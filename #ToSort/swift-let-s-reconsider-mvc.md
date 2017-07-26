# Swift: Let's Reconsider MVC

_Captured: 2017-01-15 at 20:51 from [dzone.com](https://dzone.com/articles/swift-lets-reconsider-mvc?edition=263882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-15)_

Why do developers tend to fill views in their view controllers? What about the better approach to MVC in Swift?

Most of the developers I met tend to do really strange things. Some of them avoid washing and stink like hell. Others drink coffee with salt and pepper. But the most common behavior I see is that developers don't use the views and prefer to do all the view-related actions in view controllers, like filling, creating the animations, etc.

First of all, let's pretend we have some class describing the user:

Secondly, we have a task of filling some presentation with data from that user. The code of lots of developers and even the one Apple provides in its tutorials would look like the monstrosity below:
    
    
        override func viewWillAppear(_ animated: Bool) {
    
    
            guard let user = self.user else { return }
    
    
            self.nameLabel?.text = user.name
    
    
            self.avatarImageView?.image = UIImage(named: user.imageName)

Listen to me, oh ye sinners, who could say: "Oh. Hey. That's the code I usually write. There's nothing wrong with it." It's actually really wrong on several levels:

  * The content of the view depends on when you set the model;
  * It is not extensible and maintainable;
  * It's not reusable.

And we shouldn't forget to make our _@IBOutlets_ weak, as the view controller _view_ property could change and we'd hold strong references to views, that we don't have any responsibility about.

If the model was set after the view appeared (e.g., it was downloaded from teh internets), it won't be presented on the screen, unless we go further into navigation hierarchy and then return back. There are guys out there in the wild who do that in _viewDidLoad_, but that's even worse, as the only way to update the content is to create a new view controller with a new model. And even then, if you set the model after pushing your controller into the navigation controller, it won't be shown as well, as _viewDidLoad_ was called already during the push itself.

The extensibility and maintainability are really painful in here as well. Your view controller is responsible for filling in and animating its whole view hierarchy. Right now, there are just two subviews, but imagine you had 20 of them or even more. Moreover, you had to animate them or change how they look depending on the model data. _viewWillAppear_ would quickly become a general mess.

As for the reuse, imagine a situation when you want the same view and model relation being presented on a different view controller with different logic as to when and how the model is fetched and processed. Say you want to present it as a cell in a table view or present it for a different kind of user coming from a different API endpoint.

It's really weird, in my opinion, that there were not that many sound voices around the web who proposed a much better and simpler alternative. In most of these cases, developers don't have anything against writing:

Let's think about it. UILabel has some sophisticated drawing logic and processing of strings in it. What it does is that it presents the string. But what is a string to the view? Isn't it obvious? It's a model!

So, why does our code, when we use our own views, boil down to the code I previously mocked? Some of the people would start arguing that that's the proper way of doing MVC. And MVC is a design pattern. And Apple does that in their code and we should oblige. You know what this reminds me? Enterprise Java projects with "hello world" being written using 20 classes and protocols. Of course, Java devs could simplify the thing, but they strictly abide GoF and other mainstream design patterns, forgetting that they are recommendations, not strict rules to follow.

Let's reason about our code and presentation from the POV I insist on. Each of our views is tightly coupled to some model. It's designed and presented in the way suitable only for one model. A proof? You won't be able to present the exam math problems using user-presenting screens. Its design is different, and its subviews are different. The same applies to UITableView as well, for example, but in that case, we should consider its model to be the array of models. And in that case, it fits in the same scheme of one model to one view relation.

The same applies to animations and other stuff. View controller shouldn't handle those things on the low level of implementation details. It should call appropriate methods of the view responsible for presentation. So, our view becomes a self-contained entity that only needs models for presentation. And in that case, we could drag a pair of a model and view around and present them around the app anywhere we want without writing additional code. That's high reusability for you. The only real problem is that you should decompose your views and models properly in order to make the entities self-contained without expressly bloating your code and using reusability.

One more important thing is that views shouldn't modify the models, they should just adapt to them. And models shouldn't know anything about their views, as one model could be presented in several different ways, but any view is tightly coupled to its model.

Moreover, views shouldn't start any processing based on user actions. They should either call the controller _@IBActions_ or call the closures, that the view controller passes to views.

So, my idea of responsibilities is as follows:

_View controller_:

  1. Handles user interactions;
  2. Passes models to views;
  3. Calls view methods responsible for different aspects of presentation (e.g., show loading view);
  4. Initiates the data processing logic of a model;

_View_:

  1. Fills itself in from the model and possibly reacts to model changes reactively;
  2. Provides interfaces hiding the implementation details of presentation (like animations and stuff or some specific set up);
  3. Receives its look and layout from the nib;

_Model_:

  1. Processes data;
  2. Stores data;
  3. Possibly provides means of observing the state.

Yeah, it looks, like MVVM, but it's not. You could, however, inject view models for even better decomposition in case you need them. Just pass them to views instead of raw models.

As for the models, I'll cover that in later blog posts. For now, let's take a look at the implementation of my ideas in practice. Here comes the abstract view providing the 1-to-1 relation to the model:

_DidSet_ could contain a much more interesting setup if you wanted to observe the model state somehow. But that will do for our case. It's generic without constraints, as the model could be anything and we can't make any assumptions, as we don't expect any specific model behavior.

Then, we create the root view class for our view controller and specialize its model. My naming convention is to call it by removing "Controller" word from controller name:

Please note, that I removed _weak_ from _@IBOutlets_. That's because our view is responsible for the changes to its hierarchy and removing or re-adding subviews to the view hierarchy is totally okay.

_UserView_ is self-contained. You could use it as _UIViewController_ root view or you could put it as a subview on _UITableViewCell_ and it would work the same. You want to change how it looks in the cell? No problem, just create a nib with the cell and specify the constraints to your liking. That's the reusability for you.

Next, let's solve the problems with _UIViewController_ by creating an abstract class responsible for managing models and compound views:
    
    
            didSet { self.fillView() }
    
    
            self.rootView?.model = self.model

Nothing too fancy in here. A generic class because of the same reasons as _IDPView_, as we don't know anything about the model. We only know about the view and that it should be an _IDPView_ subclass, and that its model should be the of the same type, as the model of the _IDPViewController_.

At the same time, we solved the problem I previously mentioned, that the contents of the view would differ based on when the model was set. How does it work? Simple, Watson. If the _rootView_ was not loaded yet (_viewDidLoad_ was not called), but the model was already set, we pass the model to the view, when it loads. Otherwise, we do that immediately, when the model is set.

The _UserViewController_ becomes really simple in that case, as it doesn't have to handle from what I outlined in the responsibility list above:

Both _IDPView_ and _IDPViewController_ are reusable and they both solve the problems I outlined at the start of the article. Their subclasses are also quite reusable at their core. If you tried to solve them separately for each subclass of _UIView_ and _UIViewController_, it could have resulted in a bloated and much less reusable solution with duplication.

Of course, there are exceptions. If we take reusable high-level views without the implementation details, like _UITableView_ or _UITableViewCell_ (I'm talking of those specific classes, not their subclasses), they are universal and are not tightly coupled to any specific model, so my solution doesn't fit them. We will need the view controller to work with those entities on the implementation level in that specific case. We could subclass and specialize the cells for example, but reusability and self-containment of my _UITableView_ and other collections are definitely the tale for another day.

That's all, folks. Have a great day and stay DRY, no matter, where you are.
