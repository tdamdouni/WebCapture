# Node.js Design Patterns

_Captured: 2017-08-08 at 18:49 from [thejackalofjavascript.com](http://thejackalofjavascript.com/node-js-design-patterns/)_

Javascript on the server? How is this going to be different from Javascript on the client? We are going to cover the way Node does things and understand it to develop efficient Node code.

### Contents

## Asynchronous code & Synchronous code

As we have seen in an earlier post ([here](http://thejackalofjavascript.com/nodejs/)), how node does things Asynchronously. For a "Traditional programmer", this can be a tough pill to swallow. So lets take a look at how things can be done async.

Tradition programming

1234567 
var result = db.query("select * from someTable");// use the result here and do somethingvar doSomething = function(){// doing something totally unrelated to the db call.};doSomething(); // This will be blocked till the db response has arrived.

Here the doSomething() executes a set of statements that are not dependent on the response of the db call. But it has to wait till the db operation is completed. This is why we have a server like Node to take care of all the I/O threads separately.

So in an async world, the same will be written like this

123456789 
var result = db.query("select * from someTable", function(){// use the result here and do something});var doSomething = function(){// doing something totally unrelated to the db call.};doSomething(); // The DB request gets fired and doSomething() will get executed after that.

Here, the DB request gets fired and doSomething() will get executed immediately after that. All the actions happen async. Its Node's event loop's responsibility to take care of I/O operations and fire the registered callback.

Now, life is always not that simple is it? (_tell me about it!.._) Take a look at this example

123456 
var result = db.query("select * from someTable", function(data){var userId = data.get(1).id;var subQResult = db.query("select * from someOtherTable where id="+userId+";", function(userData){// some more info.. and the fire another db call! });});

or

1234567 
var file = fs.readFile("/usr/bin", function(data){var listOfFiles = data.getContents();var anotherFile = fs.readFile(listOfFiles[0], function(userIDs){var user = userIds[0];// Call db and get the data for this user});});

Very nested and convoluted? So can we fix this whole nested thing? Yes, you can use any of the following modules

So our code will turn into

12345678910111213 
flow.exec(function() {readFile("/usr/bin", this);// process data},function(url) {// get some other file },function(userIDs) {var user = userIds[0];// and so on },function() {completedAll()});

Now, lets take a look at Node's Modules.

## Node Modules

If you have interacted with programming languages like C, C++, Java, .Net or PHP, you would have seen statements like import using #include include or require to get external files/libraries to your current file. Since the code is isolated in these programming languages, we need to explicitly include the required libraries.

But, Javascript runs everything in the global scope and does not have a partition between variables/functions or variables/functions of a file. In simple, there is no namespacing!.

If you have 3 files, fileOne.js , fileTwo.js & fileThree.js and you loaded them in your browser in the same order, The function definition or variable values of the prior will be overridden by the later without any warnings.

Lets say fileOne has a method called add(num1,num2); which adds two numbers & fileTwo has a method called add(str1, str2); which concats' two strings. And fileThree is calling the add(5,4); expecting the method to return the sum. But instead, it receives a concatenated string.

This phenomenon in the programming world is called as the _"spaghetti code". _Unless you are careful about your variables names, you might override someone else's code or some one might override yours!

So we need to use a dependency management system, that will take care of things like these. Node uses **_CommonJs Modules_** for handling dependency.

CommonJS dependency management revolves around two methods exports & require.

Let's reconsider the above example, and implement the same via CommonJs modules.

fileOne.js

123456 
exports.add = function(a,b){if(!isNaN(a) && !isNaN(b))return parseInt(a) + parseInt(b);elsereturn "Invalid data";};

fileTwo.js

and now in fileThree.js

var moduleOne = require("./fileOne");var moduleTwo = require("./fileTwo");console.log(moduleOne.add(5,4)); // This will be the sum for sure!!

Neat right? Node uses this for its dependency management & name-spacing and you need to when you are developing code around Node.

## Javascript's Callback

_A call back basically is a function that will get invoked after the initiated task is completed. _

That means, I want do something after some other thing is completed. Like, after 5 seconds fire an alert.

Or in Node, since everything is async, the callback gets fired on completion of an I/O operation.

var results = db.query("select * from someTable", function(data){});

Callback function can be named or anonymous.

As we have seen earlier, nesting callbacks can be a nightmare for code readability. We have also seen libraries like async would help clean the code for us. Another way to implement the same without any external module is

1234567891011 
var result = db.query("select * from someTable", processData);var processData = function(data){var userId = data.get(1).id;var subQResult = db.query("select * from someOtherTable where id="+userId+";", processSomeMoreData);};var processSomeMoreData = function(userData){// some more info.. and the fire another db call! };

**_Any async function in node accepts a callback as it's last parameter._**

So, this is what you can expect from Node.

myNodeFunction(arg1, arg2, callback);myOtherNodeFunction(arg1, arg2, arg3, callback);function callback(err, result) { ... }

And the callback function's first argument is always an error object (if there an error, else null) and the second argument is the results from the parent Function.

## The Event Emitter Pattern

Let's take a look at some sample code first

12345678910111213141516 
var net = require('net');var port = 1235;net.createServer(function(socket) {console.log('A new client connected');socket.on('data', function(data) {console.log('Data received from client : '+data);});socket.on('close', function(data) {console.log('A client disconnected');});}).listen(port, "localhost");console.log("Server Running on "+port+".\nLaunch http://localhost:"+port);

The above code is a simple TCP server. Lines 4,7 & 10 register events. And the server gets created. When a client navigates to http://localhost:1235 the server starts to listen to the new client. And registers events when a data comes in & when a client disconnects from the server.

So when a client connects, we see a console log about the connection. We wait.. wait.. wait.. and then the client emits a data event, the server logs it & finally the client disconnects.

This model is also called as the "_PubSub" -_ A publisher-subscriber. For all you jQuery devs out there, you know this!! (You register an event on a button click and write some code and wait for the button click). Some call this as _Observable _pattern. You can figure this out [here](http://stackoverflow.com/a/15596131/1015046).

So, In simple, our server code will get executed only if there is an action.This is a simple example of event driven development in Node.

Node provides an option to write & trigger custom event too. Take an example of a baseball

12345678910111213 
var events = require('events'); // require eventsvar eventEmitter = new events.EventEmitter(); // create a new instancevar homeRun = function(){console.log('Home Run!!');}// Register an event for 'swing'eventEmitter.on('swing',homeRun); // yay!!// Ball pitched.. So lets emit a 'swing' event eventEmitter.emit('swing');

What happened here?

  * We created a response ( homeRun())
  * We registered an event (' swing') passing the callback ( homeRun())

Apart from the above way of implementing the eventEmitter, we can inherit the same too. What do I mean? Take a look at this

123456789101112131415161718 
var events = require('events');function Batter(name) {this.name = name;events.EventEmitter.call(this); // making the Batter class a event emitter. //Invoking the EventEmitter's constructor with Batter.this.swing = function(){this.emit('swing');}}Batter.prototype = events.EventEmitter; // Inheriting EventEmitters methods into Batter. ex: 'on', as user belowvar batter = new Batter('Babe Ruth');batter.on('swing', function() {console.log('It is a Strrikkkeee!!!!');});batter.swing();

Pretty neat right? Now you can have your own class that is invisible.

So these are some of the ways, in which node _should_ be implemented. Depending on our requirement, you can pick from above.

Thanks for reading! Do comment.  
@arvindr21
