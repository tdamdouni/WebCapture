# Shutdown The Simple Server

_Captured: 2015-12-15 at 10:15 from [flask.pocoo.org](http://flask.pocoo.org/snippets/67/)_

The Werkzeug server that is used by the `app.run()` command can be shut down starting with Werkzeug 0.8. This can be helpful for small applications that should serve as a frontend to a simple library on a user's computer.
    
    
    from flask import request
    
    def shutdown_server():
        func = request.environ.get('werkzeug.server.shutdown')
        if func is None:
            raise RuntimeError('Not running with the Werkzeug Server')
        func()
    

Now you can shutdown the server by calling this function:
    
    
    @app.route('/shutdown', methods=['POST'])
    def shutdown():
        shutdown_server()
        return 'Server shutting down...'
    

The shutdown functionality is written in a way that the server will finish handling the current request and then stop.

This snippet by Armin Ronacher can be used freely for anything you like. Consider it public domain.

## Comments

  * Is it possible to shutdown server without request object? Why an application has a run(...) method, but hasn't stop()? Due to difficulties with reloader?
