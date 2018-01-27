# Flask 101: How to Add a Search Form

_Captured: 2017-12-15 at 09:52 from [dzone.com](https://dzone.com/articles/flask-101-how-to-add-a-search-form?edition=342156&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-14)_

In our last article, we added a database to our Flask web application but didn't have a way to add anything to our database. We also didn't have a way to view anything, so, basically, we ended up having a pretty useless web application. This article will take the time to teach you how to do the following:

  * Create a form to add data to our database.
  * Use a form to edit data in our database.
  * Create some kind of view of what's in the database.

Adding forms to Flask is pretty easy too, once you figure out what extension to install. I had heard good things about WTForms so I will be using that in this tutorial. To install WTForms you will need to install [Flask-WTF](https://flask-wtf.readthedocs.io/en/stable/install.html). Installing Flask-WTF is pretty easy; just open up your terminal and activate the virtual environment we set up in our [first tutorial](http://www.blog.pythonlibrary.org/2017/12/08/flask-101-getting-started/). Then run the following command using pip:

This will install WTForms and Flask-WTF (along with any dependencies) to your web app's virtual environment.

### Serving HTML Files

Originally when I started this series, all I was serving up on the index page of our web application was a string. We should probably spruce that up a bit and use an actual HTML file. Create a folder called "templates" inside the "musicdb" folder. Now create a file called "index.html" inside the "templates" folder and put the following contents in it:

Now before we update our web application code, let's go ahead and create a search form for filtering our music database's results.

### Adding a Search Form

When working with a database, you will want a way to search for items in it. Fortunately creating a search form with WTForms is really easy. Create a Python script called "forms.py" and save it to the "musicdb" folder with the following contents:

Here we just import the items we need from the **wtforms** module and then we subclass the **Form** class. In our subclass, we create a selection field (a combobox) and a string field. This allows us to filter our search to the Artist, Album, or Publisher categories and enter a string to search for.

Now we are ready to update our main application.

### Updating the Main Application

Let's rename our web application's script from "test.py" to "main.py" and update it so it looks like this:
    
    
    @app.route('/', methods=['GET', 'POST'])
    
    
        return render_template('index.html', form=search)
    
    
        if search.data['search'] == '':
    
    
            return render_template('results.html', results=results)

We changed the `index()` function so it works with both POST and GET requests and told it to load our MusicSearchForm. You will note that when you first load the index page of your web app, it will execute a GET and the `index()` function will render our **index.html** that we just created. Of course, we didn't actually add the form to our index.html yet, so that search form won't appear yet.

There is also a `search_results()` that we added to handle really basic searches. However, this function won't be called until we actually implement a way to display the results. So let's go ahead and make the search form visible to our users.

When I was learning how to create forms with WTForms, the [Flask-WTF website ](http://flask.pocoo.org/docs/0.12/patterns/wtforms/)recommended creating a template with a macro called "_formhelpers.html." Go ahead and create a file of that name and save it to your "templates" folder. Then add the following to that file:

This syntax might look a little odd since it is obviously not just HTML. This is actually [Jinja2](http://jinja.pocoo.org/) syntax, which is the templating language used by Flask. Basically, anywhere you see the squiggly braces (i.e. {} ), you are seeing Jinja syntax. Here we pass in a **field** object and access its **label** and **errors** attributes. Feel free to look up the documentation for additional information.

Now open up your "index.html" file and update it so that it has the following contents:

The new code in this example shows how you can import the macro you created into your other HTML file. Next, we set the form method to **post** and we pass the **select** widget and the **search** widget to our **render_field** macro. We also create a **submit** button with the following label: **Search**. When you press the Search button, it will post the data in the other two fields of the form to the page that it is on, which in this case is our **index.html** or "/".

When that happens, the `index()` method in our **main.py** script will execute:

You will note that we check which request method it is and if it's the POST method, then we call the `search_results()` function. If you actually press the Search button at this stage, you will receive an **Internal Server Error** because we haven't implemented "results.html" as of yet. Anyway, right now your web application should look something like this:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/12/flask_musicdb_search.png)

Let's take a moment and get the results function doing something useful.

### Updating the Results Functionality

Right now, we don't actually have any data in our database, so when we try to query it, we won't get any results back. Thus we need to make our web application indicate that no results were found. To do that we need to update the "index.html" page:

You will note that the new code is a new block of Jinja. Here we grab "flashed" messages and display them. Now we just need to run the web application and try searching for something. If all goes as planned, you should see something like this when you do a search:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/12/flask_musicdb_search_no_results.png)

### Wrapping Up

Now we have a neat little search form that we can use to search our database, although it frankly doesn't really do all that much since our database is currently empty. In our next article, we will focus on finally creating a way to add data to the database, display search results, and edit the data too!

### Download Code

Download a tarball of the code from this article: [flask_musicdv_part_iii.tar](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/12/flask_musicdv_part_iii.tar.gz)

### Other Articles in the Series
