# iOS App Design Patterns – One Interesting Pattern That Can Help

_Captured: 2017-08-04 at 19:46 from [dzone.com](https://dzone.com/articles/ios-app-design-patterns-one-interesting-pattern-th?edition=313393&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-04)_

Design patterns make programmers jobs just that little bit easier. And if you're a programmer you'll know that the easiest way to get your job done is always the best way. Design patterns are templates for creating software using a repeatable process. These templates are applied to a common problem to help reduce the risk of contraindicative bugs occurring and to separate out the core elements of the application, along with each of their interactions, making unit testing more effective.

Design patterns are best used with Object Oriented (OO) programming languages. Since Swift is the language of iOS, this means that we can apply applicable design patterns when we are developing our iOS apps.

## **The Model-View-Presenter Design Pattern**

One of the most useful design patterns that we can apply to iOS apps is the Model-View-Presenter (MVP) pattern. This pattern allows for effective sectioning of an app into its UI, the data access, and the logic behind it all.

### **The Model**

Within this pattern, our data access is the Model part of the puzzle. This is the interface to our database, server, or other data store, and what we use to populate parts of our UI.

### **The View**

Our UI element is the View part of the pattern. Here we change the UI from incoming data that is received, as well as accept user interactions, that are passed to a handler.

### **The Presenter**

The Presenter is our logic within the app, which passes along changes to both the UI (the View) as well as the Model. It handles any complex logic, you can think of the View and the Model as mainly dumb interfaces.

![presenter](https://d1xzrcop0305fv.cloudfront.net/wp-content/uploads/2017/02/14093741/presenter.png)

## **The MVP Pattern in Action**

Now that we've learned the basics of the MVP design pattern and why it is useful, let's take a look at the MVP pattern in action with a Swift basic implementation. This implementation will involve building the MVP components of a very basic app that lets a user rate movies from the UI interface.

First, we should set up our View protocol, MovieView, which will publish our movie name and movie rating to our UI. These will need to be implemented from within the actual View class:

Then we will show the MovieViewController class which will be the actual View for our app. It inherits from the UIViewController as well as our MovieView protocol. We will need to create an instance of our Presenter from within this class:

If our view loaded correctly, then we'll have to add a listener to MovieViewController for our buttons to check what the user is doing, which we can then pass to the Presenter:
    
    
     self. findMovieButton.addTarget(self, action: "didTapButton:", forControlEvents: .TouchUpInside)
    
    
     self. saveMovieRatingButton.addTarget(self, action: "didTapButton:", forControlEvents: .TouchUpInside)

These two methods would then be stipulated in our protocol to the Presenter class, MovieViewPresenter which should also stipulate an incoming View, for instantiation:

And then defined in our actual Presenter, MoviePresenter:
    
    
     required init(view: MovieView, model: MovieModel) {
    
    
     let movieRating = self.model.getMovieRating(movieName)
    
    
     The model itself is trivial to implement, but this is how we then hook it all up in the end:
    
    
     let presenter =MoviePresenter(view: view, model: model)
