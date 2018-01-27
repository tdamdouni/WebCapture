# Build Your Node.js Application in a Modular Way

_Captured: 2017-11-09 at 14:47 from [dzone.com](https://dzone.com/articles/build-your-nodejs-application-in-a-modular-way?edition=334897&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202017-11-09)_

Tips, tricks and tools for creating your own [data-driven app](https://dzone.com/go?i=247321&u=http%3A%2F%2Fplayground.qlik.com%2Flearn%2Fnoobs%2Fintro%3Futm_source%3Ddzone_web_dev_zone%26utm_medium%3Dbumper_text_1%26utm_campaign%3Ddzone), brought to you in partnership with Qlik.

Nowadays, almost all web services or integrations are done on top of Node.js run-time. Node.js is a flexible platform with a lot of community support. It is even possible to create documents like xlsx, docx, or pdf directly from Node.js. All major cloud platforms use Node.js as their level 1 language.

### Modularity

Node.js, by design, achieves modularity by using the node_modules structure. All the required modules are stored in a node_modules directory and we can invoke the modules anywhere in our code.

But are we using this modularity in our application code. Most of the applications I see contain a lib folder, in which we store all JS files. These js files are imported into the required areas using relative paths.
    
    
    const logging = require ("../../logging")

The main problem with this kind of approach is that when we change the path of a service file the path to the DB should change. Also, the format is not readable. We will be confused with the file's authenticity.

### **The Solution**

A much better approach is to design our application as modules, such as DB, logging, error, etc. Let's say your application name is cms, then it is much easier to represent the module using scope.

You can develop the modules separately and publish them to any NPM server (public/private) and use it as like any other module.

If your application needs the logging module:

If you don't want to split your application into bits and pieces, there is another approach.

### A Better Way

Keep the modules that you want inside a separate folder. Let's say "@cms." Use a separate folder for each module and let the modules have a separate package.json. This way it will become a valid Node module.

![](http://vinodsr.com/myblog/wp-content/uploads/2017/10/1.png)

![](http://vinodsr.com/myblog/wp-content/uploads/2017/10/2.png)

![](http://vinodsr.com/myblog/wp-content/uploads/2017/10/3.png)

> _The package.json for the modules will look like this_

Once the modules are ready now its time to do some scripting. Add the install.js in the "scripts" folder.
    
    
        fs.symlinkSync(source, 'node_modules/@cms', 'junction')

Add this script to your main package.json.

The script will be executed every time you do npm install. So once all other node modules are defined and the dependencies are installed, it will create a link from the @cms folder outside to the @cms folder inside node_modules. So any changes you make to the outer @cms folder will be reflected to the folder inside node_modules.

![](http://vinodsr.com/myblog/wp-content/uploads/2017/10/install.png)

You can see that the symlinks are installed for @cms. This is not a shortcut file rather than hard links created using "ln" in Linux.

Inside @cms you can see our modules which are defined in the outer @cms folder.

This way you can achieve modularity. The "@cms" folder is part of your source code. You can then import the required modules in the normal way.

When you want your application to execute, run " **npm install**" followed by **"npm start**."

This approach helps me in making the application more modular and extensible. Let me know your thoughts on this.

Explore [data-driven apps](https://dzone.com/go?i=247322&u=http%3A%2F%2Fplayground.qlik.com%2F%3Futm_source%3Ddzone_web_dev_zone%26utm_medium%3Dbumper_text_2%26utm_campaign%3Ddzone) with less coding and query writing, brought to you in partnership with Qlik.
