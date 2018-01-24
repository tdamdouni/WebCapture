# Flask 101: Filtering Searches and Deleting Data

_Captured: 2017-12-21 at 14:00 from [dzone.com](https://dzone.com/articles/flask-101-filtering-searches-and-deleting-data?edition=347101&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202017-12-21)_

[Last time](https://dzone.com/articles/flask-101-adding-editing-and-displaying-data) we got our Flask based music database application partially functional. It could now add data to the database, edit said data, and also display everything in the database. But we didn't cover how to filter the data by using the user's filter choice (Artist, Album name, or publisher name) and search string. We also didn't cover how to delete items from the database. That is the two-fold goal of this article.

### Filtering Search Results

Filtering search results using SQLAlchemy (via Flask-SQLAlchemy) is actually quite easy. All you need to do is create some very simple query objects. Open up the **main.py** file that we were editing last time and replace the **search_results()** function with the following version of the code:
    
    
                results = [item[0] for item in qry.all()]
    
    
                qry = db_session.query(Album).filter(
    
    
                qry = db_session.query(Album).filter(

Here we added a somewhat lengthy conditional if statement. We first check to see if the user has entered a search string in the search text box. If so, then we check to see which filter the user has chosen from the combobox: Artist, Album, or Publisher. Depending on the user's choice, we create a custom SQLAlchemy query. If the user doesn't enter a search term or if our web application gets confused and doesn't recognize the user's filter choice, then we do a query against the full database. This is something that probably shouldn't be done in production as, if the database gets really large, then doing a query against your database will end up making your web application unresponsive. You can simply add some validation to your form's input to prevent this from happening (i.e. don't query the database with an empty search string). However, we won't be covering that here.

Anyway, go ahead and try this code out and see how it works. I tried several different search terms and it seemed to work fine for my use cases. You will note that I simply used the [contains method](http://docs.sqlalchemy.org/en/latest/orm/internals.html#sqlalchemy.orm.properties.RelationshipProperty.Comparator.contains) which is great for looking up a string in a table's column. You can always index your database and do other various optimizations to it including making these queries a lot more focused if you want to. Feel free to play around with this code and see how you can improve it.

Now we will move on and learn how to delete items from the database!

### Deleting Data

There are times when you enter something into the database that you just want to delete. Technically you could use our editing functionality to just edit the entry to whatever you want, but sometimes you just need to purge data permanently. So the first thing we need to do is add a **Delete** column to our results table. You will want to open up **tables.py** and add a new **LinkCol** instance to the **Results** class:
    
    
        edit = LinkCol('Edit', 'edit', url_kwargs=dict(id='id'))
    
    
        delete = LinkCol('Delete', 'delete', url_kwargs=dict(id='id'))

Just as we did when we created the link for editing our data, we add a new link for deleting the data. You will note that the second argument, which is the endpoint, points to a delete function. So the next step is to open up our **main.py** file and add said **delete()** function:
    
    
    @app.route('/delete/<int:id>', methods=['GET', 'POST'])
    
    
            form = AlbumForm(formdata=request.form, obj=album)
    
    
            if request.method == 'POST' and form.validate():
    
    
            return 'Error deleting #{id}'.format(id=id)

This code is actually pretty similar to our `edit()` function from the last article. You will note that we updated the route though. So instead of specifying **'/item/'**, we made it **'/delete/'**. This makes the URLs between the two functions different so they actually execute the correct function when the link is clicked on. The other difference is that we don't need to create a special saving function here. We just reference the **db_session** object directly and tell it to remove the album if it's found in the database and then commit our changes.

If you run the code, you should see something like the following when doing an empty string search:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/12/flask_musicdb_deleting_link.png)

The last thing we need to do is create the **delete_album.html** that we referenced above. Let's create that file and save it to our **templates** folder. Once that file is created, just add the following:

This code will render our form to show the user what they are deleting. Let's try clicking on the delete link for one of the duplicates in our table. You should see a screen like this appear:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/12/flask_musicdb_delete_album.png)

When you press the Delete button, it will redirect you to the home page where you will see a message that the item was deleted successfully:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/12/flask_musicdb_del_success.png)

To verify that the deletion worked, just do another empty string search. Your results should show one less item in the table:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/12/flask_musicdb_deleted_results.png)

### Wrapping Up

Now you should know how to do some basic filtering of search results from the database. You also have learned how to successfully delete items from the database in your Flask application. There are several places in the code that could use a refactoring and general cleanup. You could also add some CSS styling to your application to make it look prettier. Those are exercises that I will leave for the reader. Have fun playing around with the code and giving Flask a try. It's a neat little web framework and well worth a look!

### Download Code

Download a tarball of the code from this article: [flask_music_db_v.tar](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/12/flask_musicdb_v.tar.gz)

### Other Articles in the Series
