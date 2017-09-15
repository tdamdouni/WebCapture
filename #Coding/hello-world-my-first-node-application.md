# Hello World: My First Node Application

_Captured: 2017-08-30 at 09:45 from [dzone.com](https://dzone.com/articles/hello-world-my-first-node-application?edition=320393&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-28)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

![](https://3.bp.blogspot.com/-MQK2F3XTUuY/WWMED8xK3XI/AAAAAAAAAD0/4PXziABuXzcfHwozUCixCtOgV48DlCCTgCPcBGAYYCw/s1600/download.png)

## Writing Your First Node Application:

I'm using [Sublime Text](https://www.sublimetext.com/3) as my text editor. You can also use Sublime Text for your Node application development.

Open your text editor, copy the following line in the file and save the file as helloworld.js.

`console.log("hello world");`

You can run the file using the following command :  
`node helloworld.js `  
Your output should be: hello world

**Bingo! You successfully ran your first Node code!**

**Question: Hey you didn't use npm anywhere? Why?**

npm is mainly used to maintain the dependencies of Node projects and in the above example, I didn't use any dependent module. In the following example, we will start using npm.

**Question: So it doesn't need any external JavaScript files?**

Correct, we won't need to include any external JavaScript files to use Node modules.

The above example is something similar to writing one Java class and running it using the command line. Next, we are going to see how to create a Node application.

### Create a Node Project

First, create one folder and in the command prompt go to that folder. Then run the command.

Now you will be asked series of questions. Answer all the questions and then click yes.

**Name**: This will be the name of the application, you are writing. Everything should be in lowercase letters, with no spaces between words, but you can use dashes/underscores in between.

**Version**: This denotes the version of the application. Every major and minor release version needs to be updated. The version should follow[ semantic versioning specifications](http://www.nodesimplified.com/2017/07/nodejs-npm-demystified-part-2.html).

**Description**: Description of the application.

**Entry Point: The **Starting point of the application.

**Test Command**: You can enter the test command, which in turn invokes the unit test cases.

**Git Repository**: You can mention the git repository of your project.

**Keywords: **You can mention the keywords related your application. So during a search your Node module will be displayed. This will be discussed in detail later.

**Author: **Your name and email id should be mentioned in this field.

**License: **You can mention the license details of the application.

Once the above step is completed, you can find the package.json file created in your application folder. If you want to modify the above content you can change in that file.

Otherwise, you can also modify the content you can use with the npm set command:

`npm set init.license "MIT"`

The above command sets the license value present in the package.json to MIT. You can do this for all other parameters.

You have successfully created your first node application!

We will put some code into our node application in our next article.

Please share your comments or questions in the below comment section!

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
