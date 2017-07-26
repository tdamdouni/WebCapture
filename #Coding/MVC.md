MVC is a way of organizing an applications code base so that the data (model) and the presentation (view) layers are abstracted away from the logic (controller). Most how-to guides will typically use a web development example when explaining the MVC architecture.

Model refers to the data model and how it is updated. (Typically it is a wrapper around a database). For example, a person model would be a class with the variables first name, last name, age, etc and would include methods for getting and setting these components (as well as saving the data back to the database).

A View is how the data is displayed to the user. In Pythonista, this refers to the UI portion of the app (whether coded or build using the UI editor).

The Controllers handle event requests, contain the logic of the application, and determine how the models work together to make the application run, which in turn calls the views to display the data to the user.

I found an interesting link that tries to explain the concept of MVC using legos if that helps.