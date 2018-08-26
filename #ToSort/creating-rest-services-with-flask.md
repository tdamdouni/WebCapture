# Creating REST Services With Flask

_Captured: 2018-06-29 at 19:42 from [dzone.com](https://dzone.com/articles/creating-rest-services-with-flask?edition=382219&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-29)_

[Learn more](https://dzone.com/go?i=289427&u=https%3A%2F%2Fwww.runscope.com%2Fapi-monitoring%3Futm_content%3Dapi-monitoring%26utm_source%3Ddzone%26utm_medium%3Dbanner) about how to Prevent Slow or Broken APIs From Affecting Your Bottom Line.

Previously, I wrote about creating web services with Node.js frameworks [Express](https://dzone.com/articles/creating-a-rest-application-in-nodejs-with-express) and [Hapi](https://dzone.com/articles/creating-a-rest-application-in-nodejs-with-hapi), and now, you will see how it is easy to create a REST API in [Python](https://www.python.org/) using the [Flask](http://flask.pocoo.org/) framework.

As you all know, Python is popular in the machine learning world, but as a general programming language, it can also be used to create web APIs. So you can create your machine learning model in Python and can serve it as a RESTful web service with Flask. In this article, we will not be talking about machine learning model creation, maybe in another article in the future.

The prerequisites for this tutorial is a basic knowledge of Python, Virtual Environments, and a basic understanding of REST architecture.

We begin by creating a [virtual environment](http://virtualenvwrapper.readthedocs.io/en/latest/).
    
    
    New python executable in D:\dev\platforms\Python\workon\restinflask\Scripts\python.exe
    
    
    Installing setuptools, pip, wheel...done.
    
    
        D:\dev\platforms\Python\workon\restinflask\Lib\site-packages\virtualenv_path_extensions.pth

Now we need to install **flask** and **flask-RESTful** packages:
    
    
    Successfully installed Jinja2-2.10 MarkupSafe-1.0 Werkzeug-0.14.1 aniso8601-3.0.2 click-6.7 flask-1.0.2 flask-RESTful-0.3.6 itsdangerous-0.24 pytz-2018.4 six-1.11.0
    
    
    (restinflask) D:\dev\workspaces\python\restinflask>

Now it is time to create our entry application file app.py:
    
    
            return next(filter(lambda i: i["name"] == name, items), None)
    
    
            item = self._find_item(name)
    
    
            return {"item": item}, 200 if item is not None else 404
    
    
            existing_item = self._find_item(name)
    
    
            new_item = {"name": name, "price":data["price"]}
    
    
            existing_item = self._find_item(name)
    
    
                new_item = {"name": name, "price": data["price"]}
    
    
    api.add_resource(Item, '/item/<string:name>')

The lines 4, 5, 33, and 35 are the boilerplate codes, which bootstraps the application.  
Lines from 9 through 31 implements the API. Our Item class implements the Resource class which maps HTTP verbs to methods. The `get` , `post` , and `put` methods are to handle corresponding Http methods.

Now let's run the application and test it:

First, create a table item with price 13.57.

![Image title](https://dzone.com/storage/temp/9556164-post.png)

> _Now query it with an http-get;_

![Image title](https://dzone.com/storage/temp/9556168-get1.png)

> _Update the existing item with an http-put;_

![Image title](https://dzone.com/storage/temp/9556171-put.png)

You can find the whole project in my [GitHub repository](https://github.com/dursunkoc/restinflask).

[Learn about](https://dzone.com/go?i=289428&u=https%3A%2F%2Fwww.runscope.com%2Fapi-monitoring%3Futm_content%3Dapi-monitoring%26utm_source%3Ddzone%26utm_medium%3Dbanner) the Five Steps to API Monitoring Success with Runscope
