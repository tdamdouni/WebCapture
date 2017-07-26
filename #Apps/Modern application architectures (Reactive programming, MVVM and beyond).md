# Modern application architectures (Reactive programming, MVVM and beyond)

_Captured: 2015-12-31 at 21:52 from [slack-files.com](https://slack-files.com/T051G5Y6D-F0HABHKDK-8e9141e191)_

by Florent Pillet ([@fpillet](http://twitter.com/fpillet))

I grew to become firmly convinced that the traditional MVC (_Model-View-Controller_) architecture is not the best choice you can make to develop modern applications. It all started when I got myself into reactive programming (with [ReactiveCocoa](http://github.com/ReactiveCocoa/ReactiveCocoa) at the time), which completely changed the way I think about code. This is not an introduction to reactive programming, which concepts I assume are understood.

As more and more of my applications' logic became abstracted and composed in signals (we call them `Observables` in [RxSwift](https://github.com/ReactiveX/RxSwift)) and I got rid of state and mutability, I was looking at extracting the business logic from the View Controller.

The goals were to:

  1. Reduce the size of View Controller classes, making maintenance easier,
  2. Make the business logic testable,
  3. More easily extract bits of reusable code.

This got me looking for architectures revolving around the concepts of separating application backend services, business logic, user interaction and data rendering. I first stumbled on [this post by Colin Eberhardt](http://www.raywenderlich.com/74106/mvvm-tutorial-with-reactivecocoa-part-1) which was enlightening since it fit so well in my use of ReactiveCocoa.

## Application architecture

The architecture I went for is a mix of [MVVM](https://www.objc.io/issues/13-architecture/mvvm/) (_Model-View-ViewModel_) and _[VIPER_](https://www.objc.io/issues/13-architecture/viper/)_ (View-Interactor-Presenter-Entity-Routing_) with some additional abstraction of application backend services (ideas taken from the post by Colin Eberhardt linked to above).

My apps are made of four main components:

  1. **View Controllers** (VC) which handle the rendering (through Views) and user interaction.
  2. **View Models** (VM) which are business logic units, a VM usually providing the business logic and access to data for a VC.
  3. **Backend services**, providing data storage, caching, networking services as well as service specific to each application (for example an app using Location Services will have a specialized backend service which provides a range of services to the app, like live position and geocoding `Observables` etc.)
  4. A single **Application Coordinator** (`AppCoordinator`) which is the entity responsible for instantiating the View Controllers, binding them to their associated View Model, and also giving VMs access to the backend services.

Each application screen is a _scene_ composed of a (ViewController, ViewModel) pair and gets presented upon request of the ViewModel controlling the current scene (the only exception being, obviously, the first scene displayed by the app).

The ViewModel only expresses its presentation intent (i.e. whether the scene should preferrably be displayed as a modal), while the AppCoordinator is ultimately responsible for creating the associated ViewController and performing the actual presentation work by the most appropriate mean.

In short: navigation is decided by the business logic (the ViewModel). AppCoordinator tries to meet the VM requirements and execute scene transitions as requested.

### Referencing order

One of the important ideas is that the ViewController holds a reference (is _bound to_) the ViewModel it presents, not the other way around. This is part of the idea of insulating the business logic from the presentation details, and making the logic testable.

When the ViewController initializes its ViewModel it passes through the `AppCoordinator` to it; this way the ViewModel has access to all Backend Services (via the AppController) but it's oblivious to the rest of the app architecture.

When a ViewModel wants to access actual Model data, it does so through appropriate Backend Services. Again, this allows insulating the ViewModel from the actual data storage details it shouldn't care about.

This leaves us with this general referencing structure:

  * **AppCoordinator** holds a reference to **Backend Services,** **ViewControllers**
  * **ViewModel** only references **AppCoordinator**
  * **ViewController** knows about **AppCoordinator** and is bound to a **ViewModel**

## View Controller

A ViewController is responsible for setting up views for display, handling user interaction and passing user actions back to the ViewModel. It is not supposed to perform any business logic by itself; its role in logic processing is limited to user interaction. Handling continuous gestures is part of the VC's role, triggering actions as a result is not.

Despite this limited role, VCs have a lot to handle in terms of presentation. To ease things, I use a `BaseViewController` class which provides general services to subclasses like automatic handling of autolayout constraints update on keyboard appearance, methods to present alerts during long networking tasks, customizing the navigation bar, etc. This removes a lot of duplicate code.

The `BaseViewController` class conforms to the `AppViewController` protocol which defines how the AppCoordinator can set it up and bind it to its ViewModel:
    
    
    protocol AppViewController {
    
    	var appCoordinator : AppCoordinator? { get set }
    
        var viewModel : BaseViewModel? { get set }
    	
    	func bindViewModel() -> Bool
    
    }

## View Model

A ViewModel handles the business logic for a _scene_. It uses the backend services exposed by the `AppCoordinator` to get access to the data. A clean separation helps a lot with mocking data for testing (particularly through the use of `Observable`), while limited and well defined responsibilities make each ViewModel simple and easy to maintain.

The simplest definition for a ViewModel I came up with is this:
    
    
    protocol ViewModelType {
    
    	/// the AppCoordinator that manages this view model
    	var coordinator: AppCoordinator { get }
    
    }
    
    class BaseViewModel : ViewModelType {
    
    	let coordinator: AppCoordinator
    
    	init(_ coordinator: AppCoordinator) {
            self.coordinator = coordinator
    	}
    }
    

When one ViewModel creates another ViewModel, it often passes more information in the initializer - for example during multi-scene input sequences (like ordering products), the contents of the shopping basket is passed from ViewModel to ViewModel until the purchase is finalized.

## Backend Service

A backend service provides access to well defined areas of the application data. I typically define them as protocols, along with a runtime implementation that is the one use during normal application execution. Each service can then be mocked independantly for testing, allowing any number of mix-and-match combinations between live app services and mocked services.

As much as possible, I will expose all data (including results from backend service operations) as Observable entities. This allows great flexibiity in each service, completely insulating the ViewModels from implementation details: all they ever see is Observables they subscribe to.

Backend services are application dependant. I will nearly always include a `CacheService` that provides caching for various kinds of data (nearly always image caching, but this can also be caching of geocoding results in location-intensive apps, etc). I will also often have a `DatabaseService` encapsulating access to the backend database (this way I can use whatever is needed for the projet, i.e. Realm or CoreData, etc).

Since some backend services may themselves rely on other backend services, I perform two-phase setup: first instantiate all services, then call a method of each service with a reference to the `AppCoordinator` from which they can each access other services.

Here's an example of an image cache service that produces images to a requested size and caches them to increase performance:
    
    
    protocol CacheService {
    	/// initial setup once all services have been created
    	func setupWithCoordinator(coordinator: AppCoordinator) -> Void
    
    	/// an image that will be provided with the requested size. Loading and resizing will happen on a background queue.
    	/// Delivery is guaranteed to happen on the main thread
    	/// The Observable will error if image is missing
    	func staticImage(path: String, size: CGSize) -> Observable<UIImage>
    
    	/// a remote image obtained and resized to the requested size
        /// this makes use of the NetworkService to obtain images.
    	func remoteImage(url: NSURL, size: CGSize) -> Observable<UIImage>
    }
    

## AppCoordinator

The central point of the app, it provides access to backend services and lets ViewModels drive transitions from scene to scene.
    
    
    protocol AppCoordinator {
    	/// the cache service providing image & data cache services
    	var cacheService : CacheService { get }
    
    	/// the "current" view controller (the one that is controlling the whole current screen)
    	var currentViewController : BaseViewController? { get set }
    
        init(rootViewController: RootMVVMViewController)
    
    	/// perform a transition to another scene by showing its associated view controller, executing
    	/// the transition defined by `intent`.
    	func transitionToScene(nextViewModel: BaseViewModel, intent: SceneTransitionIntent) -> Void
    
    	/// pop the current scene to go back to the previous scene
    	func popScene() -> Bool
    
        // Utilities to further insulate ViewModels
        // from the running environment and make them more testable
    
    	/// open a URL
    	func openURL(urlString: String) -> Bool
    }
    

One of the important aspects of scene-to-scene transition is that ViewModels express what's they'd like to be done by the way of a `SceneTransitionIntent`. The `AppCoordinator` will honor the request, but could take alternate paths depending on the current environment (i.e. is there a current NavigationController, etc). The `SceneTransitionIntent` is a struct that defines the expected visual transition (push, replace, modal display, custom animated or interactive transition, etc) and the actual ViewController to use (typically referenced through its identifier).

This implies that the application doesn't use automatic segues, which would prevent determining the ViewModel to associate with a just-presented ViewController.

I'm leaving out implementation details like how the AppCoordinator deals with tab controllers (_hint_: the BaseViewController class collaborates on this) and deep navigation controllers. They are not that interesting from an architectural point of view.

## Putting it all together

Here are some lightweight examples of a ViewController and a ViewModel, to better understand how they work together.

This example displays a list of items, and executes an action when the user taps one of them. I'm making use of:

  * [RxSwift](https://github.com/ReactiveX/RxSwift)
  * [Action](https://github.com/RxSwiftCommunity/Action) (an implementation of ReactiveCocoa's Action pattern written by Ash Furrow)
  * [NSObject+Rx](https://github.com/RxSwiftCommunity/NSObject-Rx), another micro-framework by Ash Furrow which provides NSObject subclasses with an automatic `rx_disposableBag` you can use to collect your disposables. 
  * [R.swift](https://github.com/mac-cain13/R.swift) to provide type-checked resources references

### ViewController code
    
    
    import UIKit
    import RxSwift
    import RxCocoa
    import NSObject_Rx
    
    class ItemsListViewController : BaseViewController {
      private var displayedItems = [Item]()
    	
      override func bindViewModel() -> Bool {
        let vm = self.viewModel as! ItemsListViewModel
      
        self.title = vm.itemsTypeName
      
        vm.items.subscribeNext {
          [weak self] items in
          self?.displayedItems = items
          self?.tableView.reloadData()
        }.addDisposableTo(self.rx_disposeBag)
      
        return true
      }
    }
    
    extension ItemsListViewController: UITableViewDataSource, UITableViewDelegate {
      func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
        let vm = self.viewModel as! ItemsListViewModel
        let cell = tableView.dequeueReusableCellWithIdentifier(R.reuseIdentifier.itemListCell, forIndexPath: indexPath)!
        cell.configure(displayedItems[indexPath.row], coordinator: vm.coordinator)
        return cell
      }
    	
      func tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return displayedItems.count
      }
    	
      func tableView(tableView: UITableView, shouldHighlightRowAtIndexPath indexPath: NSIndexPath) -> Bool {
        let vm = self.viewModel as! ItemsListViewModel
        vm.openItem.execute(displayedItems[indexPath.row])
        return false
      }
    }

### ViewModel code
    
    
    import Foundation
    import RxSwift
    
    class ItemsListViewModel : BaseViewModel {
    	
      /// the type of recipes we want to display
      let itemsType : ItemType
      let itemsTypeName : String
    	
      /// the list of recipe we want to display
      let items : Observable<[Item]>
    
      /// the action executed to open an item
      var openItem : Action<Item,Void> {
        return Action {
          [unowned self] item in
       
          // push a details view controller
          self?.coordinator.transitionToScene(
            ItemDetailsViewModel(coordinator: self!.coordinator, item: item),
            intent: SceneTransitionIntent(method: .Push, controller: .Named("ItemDetails"))
    
          return empty()
        }
      }
    
      init(coordinator: AppCoordinator, itemsType: itemsType) {
        self.itemsType = itemsType
        self.itemsTypeName = itemsType.displayString()
        self.items = coordinator.contentService.allItems(itemsType).sortedAlphabetically()
        super.init(coordinator)
      }
    }

## Conclusion

Modern applications call for modern achitectures. For all the good things the _Model-View-Controller_ model brought to developers, there are now more powerful alternatives meeting the requirements of today's apps. If you want your apps to be easily testable, split them up and test parts individually. If you want your code to be reusable, split it up in functional areas. Take advantage or Reactive Programming frameworks like RxSwift to expose data through Observables, making your code fully resilient to asynchrony and insulated from data providers (in addition to make data feeds transformable and composable).

I don't know whether the architecture I use now has been given a name. VIPER is a nice one but not 100% matching mine. I'll take suggestions.

This is just an example of what can be done to better fit with Reactive Programming. Every developer has different requirements, and I happily picked ideas from the architectures other developers use. You should do so, too.

## Thanks and Additional References

My thanks go to Mike Finney ([@finneycanhelp](https://twitter.com/finneycanhelp)) and Marin Todorov ([@icanzilb](https://twitter.com/icanzilb)) for proof-reading this post and suggesting improvements.

More references:

  * I use a single coordinator but there are interesting ideas in this post <http://khanlou.com/2015/10/coordinators-redux/>
