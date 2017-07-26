# The Flask Mega-Tutorial, Part I: Hello, World!

_Captured: 2017-05-24 at 08:57 from [blog.miguelgrinberg.com](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world)_

This is the first article in a series where I will be documenting my experience writing web applications in [Python](http://python.org) using the [Flask](http://flask.pocoo.org) microframework.

**NOTE**: This article was revised in September 2014 to be in sync with current versions of Python and Flask.

Here is an index of all the articles in the series that have been published to date:

  * [Part I: Hello, World!](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world) (this article)
  * [Part II: Templates](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-ii-templates)
  * [Part III: Web Forms](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iii-web-forms)
  * [Part IV: Database](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database)
  * [Part V: User Logins](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-v-user-logins)
  * [Part IX: Pagination](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-ix-pagination)
  * [Part XII: Facelift](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xii-facelift)

## My background

I'm a software engineer with double digit years of experience developing complex applications in several languages. I first learned Python as part of an effort to create bindings for a C++ library at work.

In addition to Python, I've written web apps in PHP, Ruby, Smalltalk and believe it or not, also in C++. Of all these, the Python/Flask combination is the one that I've found to be the most flexible.

**UPDATE**: I have written a book titled "Flask Web Development", published in 2014 by O'Reilly Media. The book and the tutorial complement each other, the book presents a more updated usage of Flask and is, in general, more advanced than the tutorial, but some topics are only covered in the tutorial. Visit <http://flaskbook.com> for more information.

## The application

The application I'm going to develop as part of this tutorial is a decently featured microblogging server that I decided to call _microblog_. Pretty creative, I know.

These are some of the topics I will cover as we make progress with this project:

  * User management, including managing logins, sessions, user roles, profiles and user avatars.
  * Database management, including migration handling.
  * Web form support, including field validation.
  * Pagination of long lists of items.
  * Full text search.
  * Email notifications to users.
  * HTML templates.
  * Support for multiple languages.
  * Caching and other performance optimizations.
  * Debugging techniques for development and production servers.
  * Installation on a production server.

So as you see, I'm going pretty much for the whole thing. I hope this application, when finished, will serve as a sort of template for writing other web applications.

## Requirements

If you have a computer that runs Python then you are probably good to go. The tutorial application should run just fine on Windows, OS X and Linux. Unless noted, the code presented in these articles has been tested against Python 2.7 and 3.4, though it will likely be okay if you use a newer 3.x release.

The tutorial assumes that you are familiar with the terminal window (command prompt for Windows users) and know the basic command line file management functions of your operating system. If you don't, then I recommend that you learn how to create directories, copy files, etc. using the command line before continuing.

Finally, you should be somewhat comfortable writing Python code. Familiarity with [Python modules and packages](http://docs.python.org/tutorial/modules.html) is also recommended.

## Installing Flask

Okay, let's get started!

If you haven't yet, go ahead and install [Python](http://python.org/download/).

Now we have to install Flask and several extensions that we will be using. My preferred way to do this is to create a [virtual environment](http://pypi.python.org/pypi/virtualenv) where everything gets installed, so that your main Python installation is not affected. As an added benefit, you won't need root access to do the installation in this way.

So, open up a terminal window, choose a location where you want your application to live and create a new folder there to contain it. Let's call the application folder `microblog`.

If you are using Python 3, then cd into the `microblog` folder and then create a virtual environment with the following command:
    
    
    $ python -m venv flask

Note that in some operating systems you may need to use `python3` instead of `python`. The above command creates a private version of your Python interpreter inside a folder named `flask`.

If you are using any other version of Python older than 3.4, then you need to download and install [virtualenv.py](http://virtualenv.readthedocs.org/en/latest/virtualenv.html#installation) before you can create a virtual environment. If you are on Mac OS X, then you can install it with the following command:
    
    
    $ sudo easy_install virtualenv

On Linux you likely have a package for your distribution. For example, if you use Ubuntu:
    
    
    $ sudo apt-get install python-virtualenv

Windows users have the most difficulty in installing virtualenv, so if you want to avoid the trouble then install Python 3. If you want to install `virtualenv` on Windows then the easiest way is by installing `pip` first, as explaned in [this page](https://pip.pypa.io/en/latest/installing.html). Once `pip is installed, the following command installs`virtualenv`:
    
    
    $ pip install virtualenv

We've seen above how to create a virtual environment in Python 3. For older versions of Python that have been expanded with `virtualenv`, the command that creates a virtual environment is the following:
    
    
    $ virtualenv flask

Regardless of the method you use to create the virtual environment, you will end up with a folder named `flask` that contains a complete Python environment ready to be used for this project.

Virtual environments can be activated and deactivated, if desired. An activated environment adds the location of its `bin` folder to the system path, so that for example, when you type `python` you get the environment's version and not the system's one. But activating a virtual environment is not necessary, it is equally effective to invoke the interpreter by specifying its pathname.

If you are on Linux, OS X or Cygwin, install flask and extensions by entering the following commands, one after another:
    
    
    $ flask/bin/pip install flask
    $ flask/bin/pip install flask-login
    $ flask/bin/pip install flask-openid
    $ flask/bin/pip install flask-mail
    $ flask/bin/pip install flask-sqlalchemy
    $ flask/bin/pip install sqlalchemy-migrate
    $ flask/bin/pip install flask-whooshalchemy
    $ flask/bin/pip install flask-wtf
    $ flask/bin/pip install flask-babel
    $ flask/bin/pip install guess_language
    $ flask/bin/pip install flipflop
    $ flask/bin/pip install coverage

If you are on Windows the commands are slightly different:
    
    
    $ flask\Scripts\pip install flask
    $ flask\Scripts\pip install flask-login
    $ flask\Scripts\pip install flask-openid
    $ flask\Scripts\pip install flask-mail
    $ flask\Scripts\pip install flask-sqlalchemy
    $ flask\Scripts\pip install sqlalchemy-migrate
    $ flask\Scripts\pip install flask-whooshalchemy
    $ flask\Scripts\pip install flask-wtf
    $ flask\Scripts\pip install flask-babel
    $ flask\Scripts\pip install guess_language
    $ flask\Scripts\pip install flipflop
    $ flask\Scripts\pip install coverage

These commands will download and install all the packages that we will use for our application.

## "Hello, World" in Flask

You now have a `flask` sub-folder inside your `microblog` folder that is populated with a Python interpreter and the Flask framework and extensions that we will use for this application. Now it's time to write our first web application!

After you `cd` to the `microblog` folder, let's create the basic folder structure for our application:
    
    
    $ mkdir app
    $ mkdir app/static
    $ mkdir app/templates
    $ mkdir tmp

The `app` folder will be where we will put our application package. The `static` sub-folder is where we will store static files like images, javascripts, and cascading style sheets. The `templates` sub-folder is obviously where our templates will go.

Let's start by creating a simple init script for our `app` package (file `app/__init__.py`):
    
    
    from flask import Flask
    
    app = Flask(__name__)from app import views

The script above simply creates the application object (of class `Flask`) and then imports the views module, which we haven't written yet. Do not confuse `app` the variable (which gets assigned the `Flask` instance) with `app` the package (from which we import the `views` module).

If you are wondering why the `import` statement is at the end and not at the beginning of the script as it is always done, the reason is to avoid circular references, because you are going to see that the `views` module needs to import the `app` variable defined in this script. Putting the import at the end avoids the circular import error.

The views are the handlers that respond to requests from web browsers or other clients. In Flask handlers are written as Python functions. Each view function is mapped to one or more request URLs.

Let's write our first view function (file `app/views.py`):
    
    
    from app import app
    
    @app.route('/')@app.route('/index')def index():
        return "Hello, World!"

This view is actually pretty simple, it just returns a string, to be displayed on the client's web browser. The two `route` decorators above the function create the mappings from URLs `/` and `/index` to this function.

The final step to have a fully working web application is to create a script that starts up the development web server with our application. Let's call this script `run.py`, and put it in the root folder:
    
    
    #!flask/bin/pythonfrom app import app
    app.run(debug=True)

The script simply imports the `app` variable from our app package and invokes its `run` method to start the server. Remember that the `app` variable holds the `Flask` instance that we created it above.

To start the app you just run this script. On OS X, Linux and Cygwin you have to indicate that this is an executable file before you can run it:
    
    
    $ chmod a+x run.py

Then the script can simply be executed as follows:
    
    
    ./run.py

On Windows the process is a bit different. There is no need to indicate the file is executable. Instead you have to run the script as an argument to the Python interpreter from the virtual environment:
    
    
    $ flask\Scripts\python run.py

After the server initializes it will listen on port 5000 waiting for connections. Now open up your web browser and enter the following URL in the address field:
    
    
    http://localhost:5000

Alternatively you can use the following URL:
    
    
    http://localhost:5000/index

Do you see the route mappings in action? The first URL maps to `/`, while the second maps to `/index`. Both routes are associated with our view function, so they produce the same result. If you enter any other URL you will get an error, since only these two have been defined.

When you are done playing with the server you can just hit Ctrl-C to stop it.

And with this I conclude this first installment of this tutorial.

For those of you that are lazy typists, you can download the code from this tutorial below:

Download [microblog-0.1.zip](https://github.com/miguelgrinberg/microblog/archive/version-0.1.zip).

Note that you still need to install Flask as indicated above before you can run the application.

## What's next

In the next part of the series we will modify our little application to use HTML templates.

I hope to see you in the next chapter.

Miguel
