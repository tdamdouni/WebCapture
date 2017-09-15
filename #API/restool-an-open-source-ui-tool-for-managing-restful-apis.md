# RESTool — An open source UI tool for managing RESTful APIs

_Captured: 2017-09-06 at 12:30 from [medium.com](https://medium.com/@danielsternlicht/restool-an-open-source-ui-tool-for-managing-restful-apis-32c18062502)_

# RESTool -- An open source UI tool for managing RESTful APIs

When I worked at [Outbrain](https://www.outbrain.com/), we had a very nice tradition of open source days. Once a month, we went outside of the office, and dedicated a day for contributing the open source community.

One of the outcomes of these days is an open source project my team (- [Oreli Levi](https://github.com/orelil), [Jonathan Sellam](https://github.com/backprog)) and [myself ](https://github.com/dsternlicht)developed called "**[RESTool**](https://github.com/dsternlicht/RESTool)".

![](https://cdn-images-1.medium.com/max/1600/1*EfM7on0ep_oz-ZeEvhEQpw.png)

> _RESTool sample app._

### What's RESTool?

As a front end developer, in addition to your day job of developing awesome web apps that change the world, you're frequently being asked to develop UI tools for managing the backend of those web apps. These UI tools are mostly being used internally by product managers, account managers, and other non-technical consumers, as well as the developers team.

The idea behind RESTool is simple. Given the fact that each entity in your API has a RESTful implementation, RESTool will help you to develop a tool for managing these entities **in no time **by simply edit a configuration file. **No JavaScript**. **No CSS**. **No html**. Just a pure **JSON file**.

### How is it different from Swagger UI?

[Swagger UI](https://swagger.io/swagger-ui/) is a great tool for developers, but for non-technical people it could be a bit complicated. RESTool UI is simple, and designed for everyone.

Here's a link to a sample app we created so you could be impressed by the final result (Feel free to add more game of thrones characters to the list):

<https://restool-sample-app.herokuapp.com/>

### You convinced me. How do I start?

RESTool is available in the following GitHub repository: <https://github.com/dsternlicht/RESTool>

Although it's well documented, I'll give you a quick walk through the process of installing, configuring, and deploying a RESTool app.

### Installation

  1. Start by downloading RESTool repository from GitHub:
    
    
    git clone <https://github.com/dsternlicht/RESTool.git>

2\. Enter the app's folder :
    
    
    cd RESTool

3\. Install node dependencies:
    
    
    npm install 

4\. Install Angular CLI:
    
    
    npm install -g @angular/cli

5\. Start a development server:
    
    
    ng serve

6\. Navigate to <http://localhost:4200/> in your browser to see the app.

### Configuration

Now that the app is up and running, you may start configuring your RESTful API.

  * The file we're going to work with called `config.json` and you could find an example of its structure under `src/config-sample.json` .
  * Rename the JSON file name from `config-sample.json` to `config.json` .
  * Here's an example of the configuration structure:
    
    
    {  
     "name": "RESTool app",  
     "pages": [  
     {  
     "default": true,  
     "name": "Contacts",  
     "id": "contacts",  
     "description": "An example of RESTool configuration file usage with a simple mocking server",  
     "methods": {  
     "getAll": {  
     "label": "Get Contacts",  
     "url": "<https://restool-sample-app.herokuapp.com/api/contacts>",  
     "dataPath": null,  
     "queryParams": [  
     {  
     "name": "q",  
     "value": "",  
     "label": "Query"  
     }  
     ],  
     "display": {  
     "type": "table",  
     "fields": [  
     {  
     "name": "thumbnail",  
     "type": "image",  
     "label": "Thumbnail"  
     },  
     {  
     "name": "id",  
     "type": "text",  
     "label": "ID"  
     },  
     {  
     "name": "name",  
     "type": "text",  
     "label": "Name"  
     },  
     {  
     "name": "email",  
     "type": "text",  
     "label": "Email"  
     },  
     {  
     "name": "work",  
     "type": "text",  
     "label": "Phone #",  
     "dataPath": "phone"  
     }  
     ]  
     }  
     },  
     "getSingle": {  
     "url": "<https://restool-sample-app.herokuapp.com/api/contacts/:id>",  
     "dataPath": null,  
     "queryParams": [],  
     "requestHeaders": {}  
     },  
     "put": {  
     "url": "<https://restool-sample-app.herokuapp.com/api/contacts/:id>",  
     "actualMethod": null,  
     "fields": [  
     {  
     "name": "name",  
     "label": "Name",  
     "type": "text"  
     },  
     {  
     "name": "email",  
     "label": "Email",  
     "type": "email"  
     },  
     {  
     "name": "thumbnail",  
     "label": "Thumbnail",  
     "type": "text"  
     },  
     {  
     "name": "work",  
     "label": "Work Phone",  
     "type": "text",  
     "dataPath": "phone"  
     },  
     {  
     "name": "mobile",  
     "label": "Mobile Phone",  
     "type": "text",  
     "dataPath": "phone"  
     },  
     {  
     "name": "numbers",  
     "label": "Numbers",  
     "type": "array",  
     "arrayType": "text"  
     },  
     {  
     "name": "friends",  
     "label": "Friends",  
     "type": "array",  
     "arrayType": "object"  
     }  
     ]  
     },  
     "post": {  
     "url": "<https://restool-sample-app.herokuapp.com/api/contacts>",  
     "fields": [  
     {  
     "name": "name",  
     "label": "Name",  
     "type": "text"  
     },  
     {  
     "name": "email",  
     "label": "Email",  
     "type": "email"  
     },  
     {  
     "name": "thumbnail",  
     "label": "Thumbnail",  
     "type": "text"  
     },  
     {  
     "name": "work",  
     "label": "Work Phone",  
     "type": "text",  
     "dataPath": "phone"  
     },
    
    
    {  
     "name": "mobile",  
     "label": "Mobile Phone",  
     "type": "text",  
     "dataPath": "phone"  
     },  
     {  
     "name": "numbers",  
     "label": "Numbers",  
     "type": "array",  
     "arrayType": "text"  
     },  
     {  
     "name": "friends",  
     "label": "Friends",  
     "type": "array",  
     "arrayType": "object"  
     }  
     ]  
     },  
     "delete": {  
     "url": "<https://restool-sample-app.herokuapp.com/api/contacts/:id>"  
     }  
     }  
     }  
     ]  
    }

This configuration file refers to our sample app. Let's break it down.

**name**: The name of the app. This will appear in the app's main screen.

**pages**: Array of object. Each object will define a page in the app. In our Medium app example, our pages will be: Users, publications, series, stories, etc.

Without entering each and every field in the page object (everything is covered in the [official **README.md** file](https://github.com/dsternlicht/RESTool/blob/master/README.md)), you may see that the object describe a page in the app (name, id, description, etc.) and more importantly -- the page's RESFul methods:
    
    
    {  
     "default": true,  
     "name": "Stories",  
     "id": "stories",  
     "description": "A description of the page",  
     "methods": {  
     "getAll": {...},  
     "getSingle": {...},  
     "put": {...},   
     "post": {...},  
     "delete": {...}  
     }  
    }

Think about a Medium blog for example. Which entities are we dealing with? We have users, publications, stories, series, etc. Assuming Medium API is a RESTful API, you could get, create, update, and delete each one of the entities above.

Let's use the "**Stories**" entity as an example, and break it down to REST methods.

(note: When I'm referring to a "user", I'm aiming for the product manager, account manager, etc.)

**getAll:** Is responsible for fetching an array of stories in the app. In this method you'll also define which fields will be presented in the main view on the app.

![](https://cdn-images-1.medium.com/max/1600/1*pnqwhwq-3HNgNIFVKYu8cA.png)

> _"getAll" result example._

**getSingle**: Will be called once the user will click the "Edit" button. It will be used to fetch a single story data.

**put**: Will be called once a user will update a story in the RESTool app.

![](https://cdn-images-1.medium.com/max/1600/1*WqQw0gHqAilGvbMsUalExA.png)

> _Clicking the "Submit" button will call the "put" method._

**post**: Will be called when a user will create a new story from the RESTool app.

**delete**: (You guessed right) will be called when a user will delete a story.

Again, each method has its own set of fields, and you may read more about it here:

**[dsternlicht/RESTool**  
_RESTool is an open source UI tool for managing RESTful APIs. It could save you time developing your own internal tools…_github.com](https://github.com/dsternlicht/RESTool)

### Deployment

When you feel your RESTool app is ready for deployment run the following command:
    
    
    ng build -prod

This will build the Angular project so it will be ready for release. The result of running this command will be a folder called `dist` in the root folder.

The `dist` folder includes all the files you need (all static) in order to run the app on your server.

### Shortcut

If you don't want to deal with Angular and the whole installation process, you may just download the latest version of RESTool [here](https://github.com/dsternlicht/RESTool/archive/master.zip), and work with the `dist` folder.

Feel free to add your feedback about **RESTool** in comments, contribute to the project on GitHub, and help me spread the word! :)
