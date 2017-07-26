# Creating a Web App From Scratch Using Python Flask and MySQL

_Captured: 2017-05-24 at 08:55 from [code.tutsplus.com](https://code.tutsplus.com/tutorials/creating-a-web-app-from-scratch-using-python-flask-and-mysql--cms-22972)_

In this series, we'll be using [Python](https://www.python.org/), [Flask](http://flask.pocoo.org/) and [MySQL](http://www.mysql.com/) to create a simple web application from scratch. It will be a simple bucket list application where users can register, sign in and create their bucket list.

This tutorial assumes that you have some basic knowledge of the `Python` programming language. We'll be using `Flask`, a Python web application framework, to create our application, with `MySQL` as the back end.

If you need to brush up on your Python skills, try the [Introduction to Python](https://themeforest.net/item/introduction-to-python/15485747) course, which gives you a solid foundation in the language for just $5.

## Introduction to Python Flask

Flask is a Python framework for creating web applications. From the official site,

> Flask is a microframework for Python based on Werkzeug, Jinja 2 and good intentions.  


When we think about Python, the de facto framework that comes to our mind is the [Django](https://www.djangoproject.com/) framework. But from a Python beginner's perspective, Flask is easier to get started with, when compared to Django.

## Setting Up Flask

Setting up Flask is pretty simple and quick. With `pip` package manager, all we need to do is:

1
`pip install flask`

Once you're done with installing Flask, create a folder called `FlaskApp`. Navigate to the `FlaskApp` folder and create a file called `app.py`. Import the `flask` module and create an app using Flask as shown:

12
`from` `flask ``import` `Flask``app ``=` `Flask(__name__)`

Now define the basic route `/` and its corresponding request handler:

123
`@app``.route(``"/"``)``def` `main():``return` `"Welcome!"`

Next, check if the executed file is the main program and run the app:

12
`if` `__name__ ``=``=` `"__main__"``:``app.run()`

Save the changes and execute `app.py`:

1
`python app.py`

Point your browser to <http://localhost:5000/> and you should have the welcome message.

## Creating a Home Page

First, when the application runs we should show a home page with the latest bucket list items added by users. So let's add our home page to our application folder.

Flask looks for template files inside the `templates` folder. So navigate to the `PythonApp` folder and create a folder called `templates`. Inside `templates`, create a file called `index.html`. Open up `index.html` and add the following HTML:

01020304050607080910111213141516171819202122232425262728293031323334353637383940414243444546474849505152535455565758596061626364656667686970
`<!``DOCTYPE` `html>``<``html` `lang``=``"en"``>``<``head``>``<``title``>Python Flask Bucket List App</``title``>``<``link` `href``=``"<http://getbootstrap.com/dist/css/bootstrap.min.css>"` `rel``=``"stylesheet"``>``<``link` `href``=``"<http://getbootstrap.com/examples/jumbotron-narrow/jumbotron-narrow.css>"` `rel``=``"stylesheet"``>``</``head``>``<``body``>``<``div` `class``=``"container"``>``<``div` `class``=``"header"``>``<``nav``>``<``ul` `class``=``"nav nav-pills pull-right"``>``<``li` `role``=``"presentation"` `class``=``"active"``><``a` `href``=``"#"``>Home</``a``>``</``li``>``<``li` `role``=``"presentation"``><``a` `href``=``"#"``>Sign In</``a``>``</``li``>``<``li` `role``=``"presentation"``><``a` `href``=``"showSignUp"``>Sign Up</``a``>``</``li``>``</``ul``>``</``nav``>``<``h3` `class``=``"text-muted"``>Python Flask App</``h3``>``</``div``>``<``div` `class``=``"jumbotron"``>``<``h1``>Bucket List App</``h1``>``<``p` `class``=``"lead"``></``p``>``<``p``><``a` `class``=``"btn btn-lg btn-success"` `href``=``"showSignUp"` `role``=``"button"``>Sign up today</``a``>``</``p``>``</``div``>``<``div` `class``=``"row marketing"``>``<``div` `class``=``"col-lg-6"``>``<``h4``>Bucket List</``h4``>``<``p``>Donec id elit non mi porta gravida at eget metus. Maecenas faucibus mollis interdum.</``p``>``<``h4``>Bucket List</``h4``>``<``p``>Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Cras mattis consectetur purus sit amet fermentum.</``p``>``<``h4``>Bucket List</``h4``>``<``p``>Maecenas sed diam eget risus varius blandit sit amet non magna.</``p``>``</``div``>``<``div` `class``=``"col-lg-6"``>``<``h4``>Bucket List</``h4``>``<``p``>Donec id elit non mi porta gravida at eget metus. Maecenas faucibus mollis interdum.</``p``>``<``h4``>Bucket List</``h4``>``<``p``>Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Cras mattis consectetur purus sit amet fermentum.</``p``>``<``h4``>Bucket List</``h4``>``<``p``>Maecenas sed diam eget risus varius blandit sit amet non magna.</``p``>``</``div``>``</``div``>``<``footer` `class``=``"footer"``>``<``p``>&copy; Company 2015</``p``>``</``footer``>``</``div``>``</``body``>``</``html``>`

Open up `app.py` and import `render_template`, which we'll use to render the template files.

1
`from` `flask ``import` `Flask, render_template`

Modify the main method to return the rendered template file.

`def` `main():``return` `render_template(``'index.html'``)`

Save the changes and restart the server. Point your browser to <http://localhost:5000/> and you should have the below screen:

![Bucket List App home page](https://cms-assets.tutsplus.com/uploads/users/442/posts/22972/image/76768hghjg55.png)

## Creating a Signup Page

We'll be using `MySQL` as the back end. So log into MySQL from the command line, or if you prefer a GUI like [MySQL work bench](http://www.mysql.com/products/workbench/), you can use that too. First, create a database called `BucketList`. From the command line:

1
`mysql -u <username> -p`

Enter the required password and when logged in, execute the following command to create the database:

1
`CREATE` `DATABASE` `BucketList;`

Once the database has been created, create a table called `tbl_user` as shown:

123456
`CREATE` `TABLE` ``BucketList`.`tbl_user` (```user_id` ``BIGINT` `NULL` `AUTO_INCREMENT,```user_name` ``VARCHAR``(45) ``NULL``,```user_username` ``VARCHAR``(45) ``NULL``,```user_password` ``VARCHAR``(45) ``NULL``,``PRIMARY` `KEY` `(`user_id`));`

We'll be using `Stored procedures` for our Python application to interact with the MySQL database. So, once the table `tbl_user` has been created, create a stored procedure called `sp_createUser` to sign up a user.

When creating a stored procedure to create a user in the `tbl_user` table, first we need to check if a user with the same `username` already exists. If it exists we need to throw an error to the user, otherwise we'll create the user in the user table. Here is how the stored procedure `sp_createUser` would look:

0102030405060708091011121314151617181920212223242526272829
`DELIMITER $$``CREATE` `DEFINER=`root`@`localhost` ``PROCEDURE` ``sp_createUser`(``IN` `p_name ``VARCHAR``(20),``IN` `p_username ``VARCHAR``(20),``IN` `p_password ``VARCHAR``(20)``)``BEGIN``if ( ``select` `exists (``select` `1 ``from` `tbl_user ``where` `user_username = p_username) ) ``THEN``select` `'Username Exists !!'``;``ELSE``insert` `into` `tbl_user``(``user_name,``user_username,``user_password``)``values``(``p_name,``p_username,``p_password``);``END` `IF;``END``$$``DELIMITER ;`

Navigate to the `PythonApp/templates` directory and create an HTML file called `signup.html`. Add the following HTML code to `signup.html`:

0102030405060708091011121314151617181920212223242526272829303132333435363738394041424344454647484950
`<!``DOCTYPE` `html>``<``html` `lang``=``"en"``>``<``head``>``<``title``>Python Flask Bucket List App</``title``>``<``link` `href``=``"<http://getbootstrap.com/dist/css/bootstrap.min.css>"` `rel``=``"stylesheet"``>``<``link` `href``=``"<http://getbootstrap.com/examples/jumbotron-narrow/jumbotron-narrow.css>"` `rel``=``"stylesheet"``>``<``link` `href``=``"../static/signup.css"` `rel``=``"stylesheet"``>``</``head``>``<``body``>``<``div` `class``=``"container"``>``<``div` `class``=``"header"``>``<``nav``>``<``ul` `class``=``"nav nav-pills pull-right"``>``<``li` `role``=``"presentation"` `><``a` `href``=``"main"``>Home</``a``></``li``>``<``li` `role``=``"presentation"``><``a` `href``=``"#"``>Sign In</``a``></``li``>``<``li` `role``=``"presentation"` `class``=``"active"``><``a` `href``=``"#"``>Sign Up</``a``></``li``>``</``ul``>``</``nav``>``<``h3` `class``=``"text-muted"``>Python Flask App</``h3``>``</``div``>``<``div` `class``=``"jumbotron"``>``<``h1``>Bucket List App</``h1``>``<``form` `class``=``"form-signin"``>``<``label` `for``=``"inputName"` `class``=``"sr-only"``>Name</``label``>``<``input` `type``=``"name"` `name``=``"inputName"` `id``=``"inputName"` `class``=``"form-control"` `placeholder``=``"Name"` `required autofocus>``<``label` `for``=``"inputEmail"` `class``=``"sr-only"``>Email address</``label``>``<``input` `type``=``"email"` `name``=``"inputEmail"` `id``=``"inputEmail"` `class``=``"form-control"` `placeholder``=``"Email address"` `required autofocus>``<``label` `for``=``"inputPassword"` `class``=``"sr-only"``>Password</``label``>``<``input` `type``=``"password"` `name``=``"inputPassword"` `id``=``"inputPassword"` `class``=``"form-control"` `placeholder``=``"Password"` `required>``<``button` `id``=``"btnSignUp"` `class``=``"btn btn-lg btn-primary btn-block"` `type``=``"button"``>Sign up</``button``>``</``form``>``</``div``>``<``footer` `class``=``"footer"``>``<``p``>&copy; Company 2015</``p``>``</``footer``>``</``div``>``</``body``>``</``html``>`

Also add the following `CSS` as `signup.css` to the static folder inside `PythonApp`.

010203040506070809101112131415161718192021222324252627282930313233343536373839
`body {``padding-top``: ``40px``;``padding-bottom``: ``40px``;``}``.form-signin {``max-width``: ``330px``;``padding``: ``15px``;``margin``: ``0` `auto``;``}``.form-signin .form-signin-heading,``.form-signin .checkbox {``margin-bottom``: ``10px``;``}``.form-signin .checkbox {``font-weight``: ``normal``;``}``.form-signin .form-control {``position``: ``relative``;``height``: ``auto``;``-webkit-box-sizing: border-box;``-moz-box-sizing: border-box;``box-sizing: border-box;``padding``: ``10px``;``font-size``: ``16px``;``}``.form-signin .form-control:focus {``z-index``: ``2``;``}``.form-signin input[type=``"email"``] {``margin-bottom``: ``-1px``;``border-bottom-right-radius: ``0``;``border-bottom-left-radius: ``0``;``}``.form-signin input[type=``"password"``] {``margin-bottom``: ``10px``;``border-top-left-radius: ``0``;``border-top-right-radius: ``0``;``}`

In `app.py` add another method called `showSignUp` to render the signup page once a request comes to `/showSignUp`:

`@app``.route(``'/showSignUp'``)``def` `showSignUp():``return` `render_template(``'signup.html'``)`

Save the changes and restart the server. Click on the **Sign Up** button on the home page and you should have the signup page as shown:

![Sign Up user page](https://cms-assets.tutsplus.com/uploads/users/442/posts/22972/image/7678574hjgfjhgjhgjhg.png)

Next, we need a server-side method for the UI to interact with the MySQL database. So navigate to `PythonApp` and open `app.py`. Create a new method called `signUp` and also add a route `/signUp`. Here is how it looks:

`@app``.route(``'/signUp'``)``def` `signUp():``# create user code will be here !!`

We'll be using [jQuery AJAX](http://api.jquery.com/jquery.ajax/) to post our signup data to the `signUp` method, so we'll specify the method in the route definition.

`@app``.route(``'/signUp'``,methods``=``[``'POST'``])``def` `signUp():``# create user code will be here !!`

In order to read the posted values we need to import `request` from Flask.

1
`from` `flask ``import` `Flask, render_template, request`

Using `request` we can read the posted values as shown below:

1234567
`@app``.route(``'/signUp'``,methods``=``[``'POST'``])``def` `signUp():``# read the posted values from the UI``_name ``=` `request.form[``'inputName'``]``_email ``=` `request.form[``'inputEmail'``]``_password ``=` `request.form[``'inputPassword'``]`

Once the values are read, we'll simply check if they are valid and for the time being let's just return a simple message:

01020304050607080910111213
`@app``.route(``'/signUp'``,methods``=``[``'POST'``])``def` `signUp():``# read the posted values from the UI``_name ``=` `request.form[``'inputName'``]``_email ``=` `request.form[``'inputEmail'``]``_password ``=` `request.form[``'inputPassword'``]``# validate the received values``if` `_name ``and` `_email ``and` `_password:``return` `json.dumps({``'html'``:``'<span>All fields good !!</span>'``})``else``:``return` `json.dumps({``'html'``:``'<span>Enter the required fields</span>'``})`

Also import `json` from Flask, since we are using it in the above code to return `json` data.

1
`from` `flask ``import` `Flask, render_template, json, request`

We'll be using [jQuery](http://jquery.com/) AJAX to send the signup request to the Python method. [Download](http://jquery.com/download/) and place `jQuery` inside `PythonApp/static/js` and add a link to it from the signup page. Once jQuery has been included, we'll add a jQuery `POST` request when the user clicks the `Sign Up` button.

So, let's attach the signup button click event as shown:

01020304050607080910111213141516
`$(``function``() {``$(``'#btnSignUp'``).click(``function``() {``$.ajax({``url: ``'/signUp'``,``data: $(``'form'``).serialize(),``type: ``'POST'``,``success: ``function``(response) {``console.log(response);``},``error: ``function``(error) {``console.log(error);``}``});``});``});`

Save all the changes and restart the server. From the **Sign Up** page, fill in the details and click **Sign Up**. Check the browser console and you should have the below message:

1
`{``"html"``: ``"<span>All fields good !!</span>"``}`

Once we have the `name`, `email address` and `password`, we can simply call the MySQL stored procedure to create the new user.

To connect with MySQL, we'll be using [Flask-MySQL](https://flask-mysql.readthedocs.org/en/latest/#), which is a Flask extension. In order to get started with `Flask-MySQL`, install it using `pip` package manager:

1
`pip ``install` `flask-mysql`

Import MySQL inside `app.py`:

1
`from` `flask.ext.mysql ``import` `MySQL`

Earlier we defined our app as shown:

1
`app ``=` `Flask(__name__)`

Along with that include the following MySQL configurations:

12345678
`mysql ``=` `MySQL()``# MySQL configurations``app.config[``'MYSQL_DATABASE_USER'``] ``=` `'jay'``app.config[``'MYSQL_DATABASE_PASSWORD'``] ``=` `'jay'``app.config[``'MYSQL_DATABASE_DB'``] ``=` `'BucketList'``app.config[``'MYSQL_DATABASE_HOST'``] ``=` `'localhost'``mysql.init_app(app)`

First, let's create the MySQL connection:

1
`conn ``=` `mysql.connect()`

Once the connection is created, we'll require a `cursor` to query our stored procedure. So, using `conn` connection, create a cursor.

1
`cursor ``=` `conn.cursor()`

Before calling the create user stored procedure, let's make our password salted using a helper provided by [Werkzeug](http://flask.pocoo.org/snippets/54/). Import the module into `app.py`:

1
`from` `werkzeug ``import` `generate_password_hash, check_password_hash`

Use the salting module to create the hashed password.

1
`_hashed_password ``=` `generate_password_hash(_password)`

Now, let's call the procedure `sp_createUser`:

1
`cursor.callproc(``'sp_createUser'``,(_name,_email,_hashed_password))`

If the procedure is executed successfully, then we'll commit the changes and return the success message.

1234567
`data ``=` `cursor.fetchall()``if` `len``(data) ``is` `0``:``conn.commit()``return` `json.dumps({``'message'``:``'User created successfully !'``})``else``:``return` `json.dumps({``'error'``:``str``(data[``0``])})`

Save the changes and restart the server. Go to the signup page and enter the `name`, `email address` and `password` and click the **Sign Up** button. On successful user creation, you'll be able to see a message in your browser console.

1
`{"message": "User created successfully !"}`

In this tutorial, we saw how to get started with creating a web application using `Python Flask`, `MySQL` and the `Flask-MySQL` extension. We created and designed the database tables and stored procedure, and implemented the signup functionality. In the next tutorial, we'll take this series to the next level by implementing sign-in functionality and some other features.

Source code from this tutorial is available on [GitHub](https://github.com/jay3dec/PythonFlaskMySQLApp---Part-1).

Do let us know your thoughts in the comments below!
