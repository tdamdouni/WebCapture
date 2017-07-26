# Decouple UI from Model with View Models and Controls

_Captured: 2015-10-16 at 10:26 from [christiantietze.de](http://christiantietze.de/posts/2015/10/view-model-control/)_

Lammert Westerhoff [compared MVVM to Presentation Controls](http://blog.xebia.com/2015/10/09/simplification-of-ios-view-controllers-mvvm-or-presentation-controls/) recently. Since nobody likes massive view controllers, I had a look, too, and found a few interesting things. To write a real app with his tips in mind, we're going to need a bit more, though, and refactor things a bit.

Especially noteworthy is:

  * Lammert introduces Presentation Controls, which are like custom view containers made of various subviews, only they don't inherit from `NSView`/`UIView`.
  * This leaves room for `SomeCustomView` and `SomeCustomControl` to co-exist. A view is passive and ready to display data, while a control is, well, controlling views.

I think we can make something greater with that. Before I show you my proposal, have a look at Lammert's solution first:

## Model, View Model, and Presentation Control (or Presenter)

To get us all on the same track, let's revisit Lammert's code.

This is our domain model at the core of the app:
    
    
    class Trip {
     
        let departure: NSDate
        let arrival: NSDate
        let actualDeparture: NSDate
        let delay: NSTimeInterval
        let delayed: Bool
        let duration: NSTimeInterval
     
        init(departure: NSDate, arrival: NSDate, actualDeparture: NSDate? = nil) {
            self.departure = departure
            self.arrival = arrival
            self.actualDeparture = actualDeparture ?? departure
     
            // calculations
            duration = self.arrival.timeIntervalSinceDate(self.departure)
            delay = self.actualDeparture.timeIntervalSinceDate(self.departure)
            delayed = delay > 0
        }
    }

And this is the view model as Lammert proposed:
    
    
    class TripViewModel {
     
        let date: String
        let departure: String
        let arrival: String
        let duration: String
        let delay: String?
        let delayHidden: Bool
        let departureTimeColor: UIColor
     
        init(_ trip: Trip) {
            date = NSDateFormatter.localizedStringFromDate(trip.departure, dateStyle: .ShortStyle, timeStyle: .NoStyle)
            departure = NSDateFormatter.localizedStringFromDate(trip.departure, dateStyle: .NoStyle, timeStyle: .ShortStyle)
            arrival = NSDateFormatter.localizedStringFromDate(trip.arrival, dateStyle: .NoStyle, timeStyle: .ShortStyle)
     
            let durationFormatter = NSDateComponentsFormatter()
            durationFormatter.allowedUnits = [.Hour, .Minute]
            durationFormatter.unitsStyle = .Short
            duration = durationFormatter.stringFromTimeInterval(trip.duration)!
     
            delayHidden = !trip.delayed
            if trip.delayed {
                durationFormatter.unitsStyle = .Full
                delay = String.localizedStringWithFormat(NSLocalizedString("%@ delay", comment: "Show the delay"), durationFormatter.stringFromTimeInterval(trip.delay)!)
                departureTimeColor = .redColor()
            } else {
                self.delay = nil
                departureTimeColor = UIColor(red: 0, green: 0, blue: 0.4, alpha: 1)
            }
        }
    }

He then uses the `TripViewModel` in the controller like so:
    
    
    class ViewController: UIViewController {
     
        @IBOutlet weak var dateLabel: UILabel!
        @IBOutlet weak var departureTimeLabel: UILabel!
        @IBOutlet weak var arrivalTimeLabel: UILabel!
        @IBOutlet weak var durationLabel: UILabel!
        @IBOutlet weak var delayLabel: UILabel!
     
        // Keeping it simple for this example
        let tripModel = TripViewViewModel(Trip(departure: NSDate(timeIntervalSince1970: 1444396193), arrival: NSDate(timeIntervalSince1970: 1444397193), actualDeparture: NSDate(timeIntervalSince1970: 1444396493)))
     
        override func viewDidLoad() {
            super.viewDidLoad()
     
            dateLabel.text = tripModel.date
            departureTimeLabel.text = tripModel.departure
            arrivalTimeLabel.text = tripModel.arrival
            durationLabel.text = tripModel.duration
            delayLabel.text = tripModel.delay
            delayLabel.hidden = tripModel.delayHidden
            departureTimeLabel.textColor = tripModel.departureTimeColor
        }
     
    }

Instead of setting `tripModel` as a constant property on `ViewController`, you're probably going to pass it to the controller in `prepareForSegue(_:)` of the presenting view controller.

This is already a very fine `ViewController`. It doesn't contain any data-transformation logic thanks to its view model.

Afterwards, Lammert proposes to replace the view model with a presentation control instead:
    
    
    class TripPresentationControl: NSObject {
     
        @IBOutlet weak var dateLabel: UILabel!
        @IBOutlet weak var departureTimeLabel: UILabel!
        @IBOutlet weak var arrivalTimeLabel: UILabel!
        @IBOutlet weak var durationLabel: UILabel!
        @IBOutlet weak var delayLabel: UILabel!
     
        var trip: Trip! {
            didSet {
                dateLabel.text = NSDateFormatter.localizedStringFromDate(trip.departure, dateStyle: .ShortStyle, timeStyle: .NoStyle)
                departureTimeLabel.text = NSDateFormatter.localizedStringFromDate(trip.departure, dateStyle: .NoStyle, timeStyle: .ShortStyle)
                arrivalTimeLabel.text  = NSDateFormatter.localizedStringFromDate(trip.arrival, dateStyle: .NoStyle, timeStyle: .ShortStyle)
     
                let durationFormatter = NSDateComponentsFormatter()
                durationFormatter.allowedUnits = [.Hour, .Minute]
                durationFormatter.unitsStyle = .Short
                durationLabel.text = durationFormatter.stringFromTimeInterval(trip.duration)!
     
                delayLabel.hidden = !trip.delayed
                if trip.delayed {
                    durationFormatter.unitsStyle = .Full
                    delayLabel.text = String.localizedStringWithFormat(NSLocalizedString("%@ delay", comment: "Show the delay"), durationFormatter.stringFromTimeInterval(trip.delay)!)
                    departureTimeLabel.textColor = .redColor()
                }
            }
        }
    }
    
    class ViewController: UIViewController {
     
        @IBOutlet var tripPresentationControl: TripPresentationControl!
     
        let trip = Trip(departure: NSDate(timeIntervalSince1970: 1444396193), arrival: NSDate(timeIntervalSince1970: 1444397193), actualDeparture: NSDate(timeIntervalSince1970: 1444396493))
     
        override func viewDidLoad() {
            super.viewDidLoad()
     
            tripPresentationControl.trip = trip
        }
    }

> Pretty clean right?

Indeed, it is clean. And the `ViewController` is even smaller!

## Architecting a bit more

The problem I have with the presentation control as it stands is that a real domain model instance is known to the view. When the presenter, `TripPresentationControl`, is coupled to `Trip`, changes to the core will immediately affect or break the view. Conversely, if you want to provide additional details to the view, you're probably going to touch your core domain model object (which may be Core Data entities) just to satisfy needs of the view.

Better decouple view from model.

Traditionally, this was done through dumb data transfer objects (DTO). The kind of view model Lammert proposed is quite similar to that. There's also another kind of view model: one that's coupled more closely to the view. I've written about this [before.](http://christiantietze.de/posts/2015/01/mvvm-cocoa/)

Let's stick with Lammerts DTO-like implementation for now.

If I had to organize all the types we just created into groups, I'd end up with this:

  * Domain 
    * `Trip`
  * View 
    * `ViewController`
    * `TripViewModel`
    * `TripPresentationControl`

`TripViewModel` shouldn't know about `Trip`, either. It's made to hold data the view needs. Refactoring the view code, the following is a lot cleaner:
    
    
    // It's a value object (struct) now!
    struct TripViewModel {
     
        let date: String
        let departure: String
        let arrival: String
        let duration: String
        let delay: String?
        let delayHidden: Bool
        let departureTimeColor: UIColor // More like "departureDueSoonColor"
    
        init(date: String, departure: String, arrival: String, 
            duration: String, delay: String?, delayHidden: Bool, 
            departureTimeColor: UIColor) {
        
            self.date = date
            self.departure = departure
            self.arrival = arrival
            self.duration = duration
            self.delay = delay
            self.delayHidden = delayHidden
            self.departureTimeColor = departureTimeColor
        }
    }
    
    class TripPresentationControl: NSObject {
     
        @IBOutlet weak var dateLabel: UILabel!
        @IBOutlet weak var departureTimeLabel: UILabel!
        @IBOutlet weak var arrivalTimeLabel: UILabel!
        @IBOutlet weak var durationLabel: UILabel!
        @IBOutlet weak var delayLabel: UILabel!
     
        var tripViewModel: TripViewModel! {
            didSet {
                dateLabel.text = tripViewModel.date
                departureTimeLabel.text = tripViewModel.departure
                arrivalTimeLabel.text = tripViewModel.arrival
                durationLabel.text = tripViewModel.duration
     
                let hideDelay = tripViewModel.delayHidden
                delayLabel.hidden = hideDelay
                
                if let delayText = tripViewModel.delay where !hideDelay {
                    durationFormatter.unitsStyle = .Full
                    delayLabel.text = delayText
                    departureTimeLabel.textColor = tripViewModel.departureTimeColor
                }
            }
        }
    }
    
    class ViewController: UIViewController {
     
        @IBOutlet var tripPresentationControl: TripPresentationControl!
     
        var tripViewModel: TripViewModel!
     
        override func viewDidLoad() {
            super.viewDidLoad()
     
            tripPresentationControl.tripViewModel = tripViewModel
        }
    }

I have now decoupled the view "module" from the model completely. It's `TripViewModel`, which now is a real value object, contains everything the view expects. The `TripPresentationControl` still does a bit of conditional set-up work. That's fine, since that's its job.

Since `TripViewModel` can now be constructed with values only, how do we create it from a `Trip` entity?

Easy: through a special factory.

I'll create the factory through cheating with extensions, though!
    
    
    extension TripViewModel {
        
        init(_ trip: Trip) {
            date = NSDateFormatter.localizedStringFromDate(trip.departure, dateStyle: .ShortStyle, timeStyle: .NoStyle)
            departure = NSDateFormatter.localizedStringFromDate(trip.departure, dateStyle: .NoStyle, timeStyle: .ShortStyle)
            arrival = NSDateFormatter.localizedStringFromDate(trip.arrival, dateStyle: .NoStyle, timeStyle: .ShortStyle)
    
            let durationFormatter = NSDateComponentsFormatter()
            durationFormatter.allowedUnits = [.Hour, .Minute]
            durationFormatter.unitsStyle = .Short
            duration = durationFormatter.stringFromTimeInterval(trip.duration)!
    
            delayHidden = !trip.delayed
            if trip.delayed {
                durationFormatter.unitsStyle = .Full
                delay = String.localizedStringWithFormat(NSLocalizedString("%@ delay", comment: "Show the delay"), durationFormatter.stringFromTimeInterval(trip.delay)!)
                departureTimeColor = .redColor()
            } else {
                self.delay = nil
                departureTimeColor = UIColor(red: 0, green: 0, blue: 0.4, alpha: 1)
            }
        }
    }

This belongs into the missing glue which makes a real app tick: event handlers. I like to create use case objects for this if it's an important task:
    
    
    class ShowExistingTrip {
        
        let view: ViewController
        
        init(view: ViewController) {
            
            self.view = view
        }
        
        func showTrip() {
            
            let trip = // ... use an Interactor to hydrate stored data into a Trip
            let tripViewModel = TripViewModel(trip: trip)
            view.tripViewModel = tripViewModel
            
            // push the view to the navigation stack or similar
        }
    }

In fact, I'd put the extension on `TripViewModel` into the same file as `ShowExistingTrip`. Depending on the complexity of the transformation or mapping, I'd go as far as make the new initializer private so only this glue layer knows about it. I can still unit-test the result through a mocked `ViewController`, inspecting its changed `tripViewModel` property.

Meanwhile, the regular `TripViewModel` initializer is still useful for unit testing the `TripPresentationControl`.

## Conclusion

The resulting components are as follows, naming the layers by convention:

  * Domain 
    * `Trip`
  * Application 
    * `ShowExistingTrip`
  * View 
    * `ViewController`
    * `TripViewModel`
    * `TripPresentationControl`

There're a lot of cool patterns floating around the web. Trying them out usually involves a working application. The use case-based services helped me sort out this kind of problems a lot in the past already.

Subscribe to the Clean Cocoa Newsletter! 

I'm writing books, I publish here and on my project pages, I release software for Mac and iOS, and I write web applications. That's a lot of stuff to keep an eye on. Let me help you get the news and pre-release invitations to exciting new products! No spam, guaranteed.

E-Mail Address* 

  * Filed under: 
    * [mvvm](http://christiantietze.de/posts/tags/mvvm)
    * [software-architecture](http://christiantietze.de/posts/tags/software-architecture)
    * [presenter](http://christiantietze.de/posts/tags/presenter)
    * [ddd](http://christiantietze.de/posts/tags/ddd)
