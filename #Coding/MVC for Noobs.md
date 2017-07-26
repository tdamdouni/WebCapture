# MVC for Noobs

_Captured: 2016-02-05 at 23:59 from [code.tutsplus.com](http://code.tutsplus.com/tutorials/mvc-for-noobs--net-10488)_

Model-View-Controller (MVC) is probably one of the most quoted patterns in the web programming world in recent years. Anyone currently working in anything related to web application development will have heard or read the acronym hundreds of times. Today, we'll clarify what MVC means, and why it has become so popular.

## Ancient History...

> MVC is not a design pattern, it is an Architectural pattern that describes a way to structure our application and the responsibilities and interactions for each part in that structure.

It was first described in 1979 and, obviously, the context was a little bit different. The concept of web application did not exist. Tim Berners Lee sowed the seeds of World Wide Web in the early nineties and changed the world forever. The pattern we use today for web development is an adaptation of the original pattern.

The wild popularization of this structure for web applications is due to its inclusion in two development frameworks that have become immensely popular: Struts and Ruby on Rails. These two environments marked the way for the hundreds of frameworks created later.

![](https://s3.amazonaws.com/nettuts/613_mvc/frameworks.jpg)

## MVC for Web Applications

The idea behind the Model-View-Controller architectural pattern is simple: we must have the following responsibilities clearly separated in our application:

![](https://s3.amazonaws.com/nettuts/613_mvc/components.jpg)

The application is divided into these three main components, each one in charge of different tasks. Let's see a detailed explanation and an example.

### Controller

The **Controller** manages the user requests (received as HTTP GET or POST requests when the user clicks on GUI elements to perform actions). Its main function is to call and coordinate the necessary resources/objects needed to perform the user action. Usually the controller will call the appropriate model for the task and then selects the proper view.

### Model

The **Model** is the data and the rules applying to that data, which represent concepts that the application manages. In any software system, everything is modeled as data that we handle in a certain way. What is a user, a message or a book for an application? Only data that must be handled according to specific rules (date can not be in the future, e-mail must have a specific format, name cannot be more than x characters long, etc).

![](https://s3.amazonaws.com/nettuts/613_mvc/ModelData.jpg)

The model gives the controller a data representation of whatever the user requested (a message, a list of books, a photo album, etc). This data model will be the same no matter how we may want to present it to the user, that's why we can choose any available view to render it.

The model contains the most important part of our application logic, the logic that applies to the problem we are dealing with (a forum, a shop, a bank, etc). The controller contains a more internal-organizational logic for the application itself (more like housekeeping).

### View

The **View** provides different ways to present the data received from the model. They may be templates where that data is filled. There may be several different views and the controller has to decide which one to use.

A web application is usually composed of a set of controllers, models and views. The controller may be structured as a main controller that receives all requests and calls specific controllers that handles actions for each case.

## Let's See an Example

Suppose we're developing an online book store. The user can perform actions such as: view books, register, buy, add items to current order, create or delete books (if he is an administrator, etc.). Let's see what happens when the user clicks on the _fantasy_ category to view the titles we have available.

We will have a particular controller to handle all books-related actions (view, edit, create, etc). Let's call it books_controller.php for this example. We will also have a model, for example book_model.php, handling data and logic related to the items in the shop. Finally we will have a series of views to present, for example, a list of books, a page to edit books, etc.

The following figure shows how the user request to view the fantasy books list is handled:

![](https://s3.amazonaws.com/nettuts/613_mvc/diagram.jpg)

The controller (books_controller.php) receives the user request [1] as an HTTP GET or POST request (we can also have a central controller, for example index.php receiving it and then calling books_controller.php).

The controller examines the request and the parameters and calls the model (book_model.php) _asking_ him to return the list of available fantasy books [2].

The model is responsible for getting that information from the database (or wherever it is stored) [3], apply filters or logic if necessary, and return the data representing the list of books [4].

The controller will use the appropriate view [5] to present these data to the user [6-7]. If the request came from a mobile phone, a view for mobile phones will be used, if the user has a particular skin selected, the corresponding view will be chosen, and so on.

## What are the Advantages?

> The most obvious advantage we gain using MVC is a clear separation of presentation (the interface with the user) and application logic. 

Support for different types of users using different types of devices is a common problem these days. The interface presented must be different if the request came from a desktop computer or from a cell phone. The model returns exactly the same data, the only difference is that the controller will choose a different view to render them (we can think of a different template).

Apart from isolating the view from the business logic, the M-V-C separation reduces the complexity when designing large applications. The code is much more structured and therefore easier maintain, test and reuse.

## Ok, but Why a Framework?

When you use a framework, the basic structure for MVC is already prepared and you just have to extend that structure, placing your files in the appropriate directory, to comply with the Model-View-Controller pattern. Also you get a lot of functionality already written and thoroughly tested.

Take cakePHP as an example MVC framework. Once you have it installed, you'll see three main directories:

  * app/
  * cake/
  * vendors/

The **app** folder is where you place your files. It is your place to develop your part of the application.

The **cake** folder is where cakePHP has its files and where they have developed their part (main framework functionality).

The **vendors** folder is for third-party PHP libraries if needed.

Your working place (app directory) has the following structure:

  * app/ 
    * config/
    * controllers/
    * locale/
    * models/
    * plugins/
    * tests/
    * tmp/
    * vendors/
    * views/
    * webroot/

Now you have to put your controllers in the **controllers** directory, your models in the **models** directory and your views in... the **views** directory!

Once you get used to your framework, you'll be able to know where to look for almost any piece of code you need to modify or create. This organization alone makes maintainability a lot easier.

## Let's Framework our Example

Since this tutorial is not intended to show you how to create an application using cakePHP, we'll use it only to show example code for the model, view and controller components and comment on the benefits of using an MVC framework. The code is oversimplified and not suitable for real applications.

Remember we had a book store and a curious user who wants to see the complete list of books in the _fantasy_ category. We said that the controller will be the one receiving the request and coordinating the necessary actions.

So, when the user clicks, the browser will be requesting this url:

1
`www.ourstore.com/books/list/fantasy`

CakePHP likes to format URLs in the form /controller/action/param1/param2 , where _action_ is the function to call within the controller. In the old classic url format it would be:

1
`www.ourstore.com/books_controller.php?action=list&category=fantasy`

### Controller

With the help of cakePHP framework, our controller will look something like this:

010203040506070809101112131415
`<?php``class` `BooksController ``extends` `AppController {``function` `list(``$category``) {``$this``->set(``'books'``, ``$this``->Book->findAllByCategory(``$category``));``}``function` `add() { ... ... }``function` `delete``() { ... ... }``... ... } ?>`

Simple, isn't it?. This controller will be saved as books_controller.php and placed in /app/controllers. It contains the list function, to perform the action in our example, but also other functions to perform other book-related actions (add a new book, delete a new book, etc).

The framework provides a lot of things for us and only one line is necessary to list the books. We have base classes with the basic controller behavior already defined, so we inherit from them (AppController which inherits from Controller).

All it has to do in the list action is call the model to get the data and then choose a view to present it to the user. Let's explain how this is done.

_this->Book_ is our Model, and this part:

1
`$this``->Book->findAllByCategory(``$category``)`

is telling the model to return the list of books in the selected category (we'll see the model later).

The _set_ method in the line:

1
`$this``->set(``'books'``, ``$this``->Book->findAllByCategory(``$category``));`

Is the controller way to pass data to the view. It sets the _books_ variable to the data returned by the model and makes it accessible to the view.

Now we just have to render the view, but this will be done automatically by cakePHP if we want the default view. If we need any other view we just have to call it explicitly using the _render_ method.

### Model

The model is even more simple:

1234567
`<?php``class` `Book ``extends` `AppModel { ``}``?>`

Why empty? Because it inherits from a base class that provides necessary functionality and we have followed the CakePHP name conventions to allow the framework to do other tasks automatically. For example, cakePHP knows, based on names, that this model is used in BooksController and that it will access a database table called books.

With this declaration only we have a book model capable of reading, deleting or saving data from the database

The code will will be saved as book.php and placed in /app/models.

### View

All we have to do now is creating a view (at least one) for the list action. The view will have the HTML code and a few (as few as possible) PHP lines to loop through the books array provided by the model.

12345
`<table> <tr> <th>Title</th> <th>Author</th> <th>Price</th> </tr>``<?php ``foreach` `(``$books` `as` `$book``): ?> <tr> <td> <?php ``echo` `$book``[``'Book'``][``'title'``]; ?> </td> <td> <?php ``echo` `$book``[``'Book'``][``'author'``]; ?> </td> <td> <?php ``echo` `$book``[``'Book'``][``'price'``]; ?> </td> </tr> <?php ``endforeach``; ?>``</table>`

As we can see, the view doesn't produce a complete page, just an HTML fragment (a table in this case). This is because CakePHP provides another way to define the layout of the page, and the views are inserted into that layout. The framework also provides us with some helper objects to make common task easy when creating these HTML excerpts (insert forms, links, Ajax or JavaScript).

We make this the default view saving it as list.ctp ( list is the name of the action and ctp means cake template) and placing it in /app/views/books (inside books because these are views for books controller actions).

And this completes the three components with the help of CakePHP framework!

## Conclusion

We have learned what is probably the most commonly used architectural pattern today. We must be aware though that when we talk about patterns in the programming world, we are talking about flexible frames, to be tailored to the particular problem at hand. We will find implementations introducing variations on the structure we have seen, but the important thing is that, in the end, the pattern helps us gain a clear division between responsibilities and better maintainability, code-reuse, and testing.

We have also seen the advantages of using an MVC framework that provides us with a basic MVC skeleton and a lot of functionality, improving our productivity and making the development process easier. Thanks for reading!
