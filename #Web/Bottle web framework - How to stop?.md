# Bottle web framework - How to stop?

_Captured: 2016-04-05 at 00:43 from [stackoverflow.com](http://stackoverflow.com/questions/11282218/bottle-web-framework-how-to-stop)_

For the default (WSGIRef) server, this is what I do (actually it is a cleaner approach of Vikram Pudi's suggestion):
    
    
    from bottle importBottle,ServerAdapterclassMyWSGIRefServer(ServerAdapter):
        server =Nonedef run(self, handler):from wsgiref.simple_server import make_server,WSGIRequestHandlerif self.quiet:classQuietHandler(WSGIRequestHandler):def log_request(*args,**kw):pass
                self.options['handler_class']=QuietHandler
            self.server = make_server(self.host, self.port, handler,**self.options)
            self.server.serve_forever()def stop(self):# self.server.server_close() <--- alternative but causes bad fd exception
            self.server.shutdown()
    
    app =Bottle()
    server =MyWSGIRefServer(host=listen_addr, port=listen_port)try:
        app.run(server=server)exceptException,ex:print ex

When I want to stop the bottle application, from another thread, I do the following:
    
    
    server.stop()

I had trouble closing a bottle server from within a request as bottle seems to run requests in subprocesses.

I eventually found the solution was to do:
    
    
    sys.stderr.close()

inside the request (that got passed up to the bottle server and axed it).

An updated version of mike's answer.
    
    
    from bottlepy.bottle importWSGIRefServer, run
    from threading importThreadimport time
    
    classMyServer(WSGIRefServer):def run(self, app):# pragma: no coverfrom wsgiref.simple_server importWSGIRequestHandler,WSGIServerfrom wsgiref.simple_server import make_server
            import socket
    
            classFixedHandler(WSGIRequestHandler):def address_string(self):# Prevent reverse DNS lookups please.return self.client_address[0]def log_request(*args,**kw):ifnot self.quiet:returnWSGIRequestHandler.log_request(*args,**kw)
    
            handler_cls = self.options.get('handler_class',FixedHandler)
            server_cls  = self.options.get('server_class',WSGIServer)if':'in self.host:# Fix wsgiref for IPv6 addresses.if getattr(server_cls,'address_family')== socket.AF_INET:class server_cls(server_cls):
                        address_family = socket.AF_INET6
    
            srv = make_server(self.host, self.port, app, server_cls, handler_cls)
            self.srv = srv ### THIS IS THE ONLY CHANGE TO THE ORIGINAL CLASS METHOD!
            srv.serve_forever()def shutdown(self):### ADD SHUTDOWN METHOD.
            self.srv.shutdown()# self.server.server_close()def begin():
        run(server=server)
    
    server =MyServer(host="localhost", port=8088)Thread(target=begin).start()
    time.sleep(2)# Shut down server after 2 seconds
    server.shutdown()

The class WSGIRefServer is entirely copied with only 1 line added to the run() method is added. Also add a simple shutdown() method. Unfortunately, this is necessary because of the way bottle creates the run() method. 

I suppose that the bottle webserver runs forever until it terminates. There are no methonds like `stop()`.

But you can make something like this:
    
    
    from bottle import route, run
    import threading, time, os, signal, sys, operator
    
    classMyThread(threading.Thread):def __init__(self, target,*args):
            threading.Thread.__init__(self, target=target, args=args)
            self.start()classWatcher:def __init__(self):
            self.child = os.fork()if self.child ==0:returnelse:
                self.watch()def watch(self):try:
                os.wait()exceptKeyboardInterrupt:print'KeyBoardInterrupt'
                self.kill()
            sys.exit()def kill(self):try:
                os.kill(self.child, signal.SIGKILL)exceptOSError:passdef background_process():while1:print('background thread running')
            time.sleep(1)@route('/hello/:name')def index(name='World'):return'<b>Hello %s!</b>'% name
    
    def main():Watcher()MyThread(background_process)
    
        run(host='localhost', port=8080)if __name__ =="__main__":
        main()

Then you can use `Watcher.kill()` when you need to kill your server.

Here is the code of `run()` function of the bottle:

try: app = app or default_app() if isinstance(app, basestring): app = load_app(app) if not callable(app): raise ValueError("Application is not callable: %r" % app)
    
    
    for plugin in plugins or[]:
            app.install(plugin)if server in server_names:
            server = server_names.get(server)if isinstance(server, basestring):
            server = load(server)if isinstance(server, type):
            server = server(host=host, port=port,**kargs)ifnot isinstance(server,ServerAdapter):raiseValueError("Unknown or unsupported server: %r"% server)
    
        server.quiet = server.quiet or quiet
        ifnot server.quiet:
            stderr("Bottle server starting up (using %s)...\n"% repr(server))
            stderr("Listening on http://%s:%d/\n"%(server.host, server.port))
            stderr("Hit Ctrl-C to quit.\n\n")if reloader:
            lockfile = os.environ.get('BOTTLE_LOCKFILE')
            bgcheck =FileCheckerThread(lockfile, interval)with bgcheck:
                server.run(app)if bgcheck.status =='reload':
                sys.exit(3)else:
            server.run(app)exceptKeyboardInterrupt:passexcept(SyntaxError,ImportError):ifnot reloader:raiseifnot getattr(server,'quiet',False): print_exc()
        sys.exit(3)finally:ifnot getattr(server,'quiet',False): stderr('Shutdown...\n')

As you can see there are no other way to get off the `run` loop, except some exceptions. The `server.run` function depends on the server you use, but there are no universal `quit`-method anyway.

You can make your thread a daemon by setting the daemon property to True before calling start.
    
    
    mythread = threading.Thread()
    mythread.daemon =True
    mythread.start()

A deamon thread will stop whenever the main thread that it is running in is killed or dies. The only problem is that you won't be able to make the thread run any code on exit and if the thread is in the process of doing something, it will be stopped immediately without being able to finish the method it is running.

There's no way in Python to actually explicitly stop a thread. If you want to have more control over being able to stop your server you should look into Python [Processes](http://docs.python.org/library/multiprocessing.html#the-process-class) from the [multiprocesses](http://docs.python.org/library/multiprocessing.html) module.

Since bottle doesn't provide a mechanism, it requires a hack. This is perhaps the cleanest one if you are using the default WSGI server:

In bottle's code the WSGI server is started with:
    
    
    srv.serve_forever()

If you have started bottle in its own thread, you can stop it using:
    
    
    srv.shutdown()

To access the srv variable in your code, you need to edit the bottle source code and make it global. After changing the bottle code, it would look like:
    
    
    srv =None#make srv globalclassWSGIRefServer(ServerAdapter):def run(self, handler):# pragma: no coverglobal srv #make srv global...

This equally kludgy hack has the advantage that is doesn't have you copy-paste any code from bottle.py:
    
    
    # The global server instance.                                                                                             
    server =Nonedef setup_monkey_patch_for_server_shutdown():"""Setup globals to steal access to the server reference.                                                             
        This is required to initiate shutdown, unfortunately.                                                                 
        (Bottle could easily remedy that.)"""# Save the original function.                                                                                         from wsgiref.simple_server import make_server
    
        # Create a decorator that will save the server upon start.                                                            def stealing_make_server(*args,**kw):global server
            server = make_server(*args,**kw)return server
    
        # Patch up wsgiref itself with the decorated function.                                                                import wsgiref.simple_server
        wsgiref.simple_server.make_server = stealing_make_server
    
    setup_monkey_patch_for_server_shutdown()def shutdown():"""Request for the server to shutdown."""
        server.shutdown()

Here's one option: provide custom server (same as default), that records itself:
    
    
    import bottle
    
    
    class WSGI(bottle.WSGIRefServer):
        instances =[]def run(self,*args,**kw):
            self.instances.append(self)
            super(WSGI, self).run(*args,**kw)# some other thread:
    bottle.run(host=ip_address, port=12345, server=WSGI)# control thread:
    logging.warn("servers are %s", WSGI.instances)
