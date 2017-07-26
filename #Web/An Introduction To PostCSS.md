# An Introduction To PostCSS

_Captured: 2015-12-08 at 17:18 from [www.smashingmagazine.com](http://www.smashingmagazine.com/2015/12/introduction-to-postcss/)_

The **development of CSS**, like all languages, is an iterative process. With every major release, we get new features and syntaxes that help us write our styles. CSS Level 3 introduced features that enable us to design interactions that previously were possible only with JavaScript. With every new day, tools emerge to make styling easier and more flexible.

One of the relatively recent tools introduced for styling is [PostCSS](https://github.com/postcss/postcss). PostCSS aims to reinvent CSS with an ecosystem of custom plugins and tools. Working with the same principles of preprocessors such as Sass and LESS, it **transforms extended syntaxes and features into modern, browser-friendly CSS**.

How you ask? JavaScript.

JavaScript has the ability to transform our styles much more quickly than other processors. Using task-runner tools like Gulp and Grunt, we can **transform styles through the build process**, much like Sass and LESS compilation. Libraries and frameworks like React and AngularJS allow us to write CSS directly in our JavaScript, opening the door for JavaScript transformation of our styles.

### The History Of PostCSS

Developed by [Andrey Sitnik](http://sitnik.ru/en), creator of Autoprefixer, PostCSS was launched as a method to use JavaScript for CSS processing. PostCSS on its own is simply an API, which, when used with its vast ecosystem of plugins, offers powerful abilities. To provide helpful debugging, source maps are generated, and an abstract syntax tree (AST) exists to help us understand where and how code is being transformed.

Because PostCSS uses the Node.js framework, the abilities of the language and tools can be easily modified and customized as needed. Other tools such as Sass and LESS limit the abilities of the system to the methods available when the compiler was written.

Due to its use of an API, PostCSS allows us to **create custom plugins and tools for any features** they may need. This modular platform design makes the tool neutral, which in turn focuses features on project requirements. PostCSS is agnostic to language format and allows for the syntax style of different preprocessors, like Sass and LESS, if needed.

### The Benefits Of Thinking Modularly

Most developers rarely start a project from scratch. Many start with a Sass boilerplate that holds variables, mixins and functions to be used in a given project. We'll have a separate style sheet for functions, mixins, grid systems and general utilities to make production easier. At the end of the day, we end up with 10 or more style sheets to keep things organized.

**Maintaining a library of Sass or LESS snippets** can be an overwhelming task and can leave a project bloated. Many projects have unused mixins and functions, included as "just in case" code. PostCSS enables easily installable, plug-and-play modules, making the development process more flexible for the unique needs of a project.

PostCSS moves all of the code needed to create functions, utilities and mixins out of our production style sheets and wraps them as plugins. Now, for each project, we can pick and choose the tools needed by including plugins in our task runner.

An example of this power is the plugin [PostCSS FontPath](https://github.com/seaneking/postcss-fontpath). With Sass, we could include a mixin in our files that allows for custom web fonts; thus, we created `@font-face` tags.
    
    
    @mixin importfont($font-family, $font-filename, $font-weight : normal, $font-style :normal, $font-stretch : normal) {
      @font-face {
        font-family: '#{$font-family}';
        src: url('#{$font-filename}.eot');
        src: url('#{$font-filename}.woff') format('woff'),
        url('#{$font-filename}.ttf') format('truetype');
        font-weight: $font-weight;
        font-style: $font-style;
        font-stretch: $font-stretch;
      }
    }
    @include importfont('mission script', 'fonts/mission-script-webfont', 300);

Using the [PostCSS FontPath](https://github.com/seaneking/postcss-fontpath) plugin in our project, we no longer need to include Sass mixins like the one above. We can write the following code in our CSS, and PostCSS will transform it, via Grunt or Gulp, into the code we need.
    
    
    @font-face {
      font-family: 'My Font';
      font-path: '/path/to/font/file';
      font-weight: normal;
      font-style: normal;
    }

As of the writing of this post, over 100 community plugins are currently available that allow for such things as future CSS syntax, shortcuts, tools and extensions of the language. It is beyond a "cool tool," and it currently counts WordPress, Google and Twitter teams among its user base.

### Adding PostCSS To Your Workflow

Because PostCSS is written in JavaScript, we can use task runners like [Gulp](http://gulpjs.com/) and [Grunt](http://gruntjs.com/) to transform the CSS in our projects. The tutorial below demonstrates how to incorporate PostCSS in your workflow via either Gulp or Grunt. Using one tool over the other is not crucial and is simply a matter of personal preference or what's best for the project.

**Note:** A complete version of both the Gulp and Grunt versions of the tool is [available on GitHub](https://github.com/drewminns/postCSS-starter). Feel free to use it as a starter template and to expand on it as needed.

#### Setting Up PostCSS With Gulp

If you are unfamiliar with Gulp, I'd recommend reading "[Building With Gulp](http://www.smashingmagazine.com/2014/06/building-with-gulp/)" by Callum Macrae to get up and running with the tool.

To install the PostCSS module in your project, run the following command in your terminal: `npm i gulp-postcss -D`.

In your project's `Gulpfile.js`, we need to require our installed PostCSS module and then use it within a task. Be sure to update the paths to your development files and the directory where the transformed output will go.
    
    
    var postcss = require('gulp-postcss');
    
    gulp.task('styles', function () {
        return gulp.src('path/to/dev/style.css')
            .pipe(postcss([]))
            .pipe(gulp.dest(path/to/prod))
    });

To run the task, type `gulp styles` in the command line.

#### Setting Up PostCSS With Grunt

**Note:** If you are unfamiliar with Grunt, I'd recommend reading "[Get Up and Running With Grunt](http://www.smashingmagazine.com/2013/10/get-up-running-grunt/)" by Mike Cunsolo to get comfortable with the tool.

To install the PostCSS module in your project, run the following command in the terminal: `npm i grunt-postcss -D`.

Once the plugin is installed on your system, enable it within the Gruntfile and create a task, as below. Be sure to update the `cwd` and `dest` values to reflect the structure of your app.
    
    
    module.exports = function(grunt) {
      grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),
        styles: {
          options: {
            processors: []
          },
          dist: {
            files: [{
              expand: true,
              cwd: 'dev/',
              src: ['**/*.css'],
              dest: 'prod/'
            }]
          }
        }
      });
    
      // Load post-css.
      grunt.loadNpmTasks('grunt-postcss');
    
    };

To run the task, type `grunt styles` in the command line.

#### Installing Plugins

Using PostCSS on its own is not entirely powerful; its strength lies in the plugins. You may have noticed that in the Gulp and Grunt implementations above there were empty arrays in the task declarations. These arrays are where we can import community-developed PostCSS plugins, the features we want to include in our tool.

A list of approved PostCSS plugins can be found on [PostCSS' GitHub page](https://github.com/postcss/postcss) and, like all NPM packages, the plugins can be installed through the command line. Many plugins can be used only as extensions of PostCSS and are agnostic to the task runner you are using. For this example, we will install the [PostCSS Focus](https://github.com/postcss/postcss-focus) plugin, which will add a `:focus` to every hover state.

With all of the plugins in the following examples, we will need to use the command line and NPM to install the packages in our projects.
    
    
    npm i postcss-focus -D

The plugins can be passed into the method directly; however, for the sake of cleanliness, we can construct an array and pass it in as an argument. In the array, we can include the necessary `require` statements that return the plugins and that are then called immediately. If you would like to read more about this concept, look through "[Functions as First-Class Citizens in JavaScript](http://ryanchristiani.com/functions-as-first-class-citizens-in-javascript/)" by Ryan Christiani.
    
    
    require('postcss-focus')()

The modified code for Grunt, with our newly created `processorArray` arrays, is below:
    
    
    var processorArray = [
        require('postcss-plugin')()
    ];
    
    // Snipped for brevity
    styles: {
          options: {
            processors: processorArray
          },
          dist: {
            src: 'path/to/dev/style.css',
            dest: 'path/to/prod/style.css'
          }
        }

And here is the modified code for Gulp:
    
    
    var processorArray = [
        require('postcss-plugin')()
    ];
    
    gulp.task('styles', function () {
        gulp.src('path/to/dev/style.css')
            .pipe(postcss(processorArray))
            .pipe(gulp.dest('path/to/prod'))
    });
    

### Plugins

Once we have installed a plugin and our build tool is prepared to compile our code, we can use PostCSS and the plugin features. The first thing to do is create a file with a `.css` extension in the directory where we store our development code.

"Wait! A CSS file?" Yup, a CSS file. Because PostCSS transforms our CSS, we don't need to use a specialized syntax -- just traditional CSS. If you are familiar with preprocessors, then it might feel unnatural to leave the `.sass`, `.scss`, `.styl` or `.less` files behind and return to `.css`. But, in fact, it's not converting -- it's transforming.

To process our styles with our newly installed PostCSS plugins, we can run our task runners with `grunt styles` and `gulp styles`, respectively. Our development CSS file will be processed through the PostCSS plugin and the plugins provided, and then it will be outputted to our specified production directory.

Below are a few plugins of note that might be of benefit as you get started with PostCSS. Included are instructions on installing and using the plugin.

#### Autoprefixer

Writing styles to work on a wide gamut of browsers and devices can be a pain, and keeping up to date with which properties and values need a vendor prefix is a challenge in itself. Luckily, [Autoprefixer](https://github.com/postcss/autoprefixer) figures out where and when to provide vendor prefixes. The plugin frees us to write styles with modern features and properties in mind, while taking care of vendor prefixes on the properties and values that need them.

Here is how to install this plugin via the command line:
    
    
    npm i autoprefixer-core -D

When we add the plugin to our array, we can provide an object that contains an array of the browser scope that the project will need to support. A list of options that can be provided is found in [Browserslist's account on GitHub](https://github.com/ai/browserslist).

Let's add the Autoprefixer plugin to our processors:
    
    
    var processorsArray = [
      // Snipped for brevity
      require('autoprefixer-core')({ browsers: ['last 2 versions', 'ie 6-8', 'Firefox > 20']  })
    ];

The appropriate vendor prefixes will be outputted to any CSS properties and values in our styles that need them, according to the object provided.

Here is the development CSS:
    
    
    .item {
      display: flex;
      flex-flow: row wrap;
    }

And here is the transformed output:
    
    
    .item {
      display: -webkit-flex;
      display: -ms-flexbox;
      display: -webkit-box;
      display: flex;
      -webkit-flex-flow: row wrap;
          -ms-flex-flow: row wrap;
              flex-flow: row wrap;
    }

#### Using Future Syntaxes With CSSNext

CSS4 will soon be upon us, and with it comes features such as [native variables](http://www.w3.org/TR/css-variables/), [custom media queries](https://drafts.csswg.org/mediaqueries/#custom-mq), [custom selectors](https://drafts.csswg.org/css-extensions/#custom-selectors) and new [pseudo-links](https://drafts.csswg.org/selectors-4/#negation). While they are not yet supported in all browsers as of the writing of this article, they will be implemented in modern browsers as the specification gets approved.

[CSSNext](http://cssnext.io/) is a tool that transforms any CSS4 features and properties into CSS3 that browsers can read. The tool can be used on its own or as a plugin through PostCSS. Again, we can add it to `processorsArray`, which contains our other PostCSS plugins.

Install the CSSNext plugin via the command line, like so:
    
    
    npm i cssnext -D

Then, add the plugin to your processors:
    
    
    var processorsArray = [
      // snipped for brevity
      require('cssnext')()
    ];

Now, in your production code, you can write CSS4 features, and PostCSS will transform the syntax through the task runner, thereby supporting today's browsers. When browsers come to support the newer syntax, you can replace the transformed output with the development CSS.

Here is the development CSS:
    
    
    // Custom Variables
    :root {
      --linkColour: purple;
    }
    
    a {
      color: var(--linkColour);
    }
    
    // Custom media queries with ranges
    @custom-media --only-medium-screen (width >= 500px) and (width <= 1200px);
    
    @media (--only-medium-screen) {
      /* Medium viewport styles */
    }
    
    // Custom selectors
    @custom-selector :--enter :hover, :focus;
    @custom-selector :--input input, .input, .inputField;
    
    a:--enter {
      /* Enter styles go here */
    }
    
    :--input {
      /* Input field styles go here */
    }
    

And here is the transformed output:
    
    
    a {
      color: purple;
    }
    
    @media (min-width:500px) and (max-width:1200px){
      body{
        background:#00f;
      }
    }
    
    a:focus,a:hover{
      background:#00f;
    }
    
    .input, .inputField, input{
      background:red;
    }

If you would like to explore more CSSNext features, the website has a [playground](http://cssnext.io/playground/) where you can experiment with current CSSNext-supported CSS4 features.

#### Sass Syntax

If Sass is your go-to preprocessor language, fear not: You can use the syntax and its tools with PostCSS. While traditional CSS doesn't yet support variables, nesting and imports, plugins such as [PreCSS](https://github.com/jonathantneal/precss) allow us to use these features and to write Sass syntax in our traditional CSS files.

If we add the plugin to our build via the command line and refer to the package in our array, we can start writing in Sass syntax immediately. If you're making the switch from Sass to PostCSS, you can change the file extension to `.css` and immediately pipe it through your task runner.

Install the PreCSS plugin via the command line, like so:
    
    
    npm i precss -D

And add the plugin to your processors:
    
    
    var processorsArray = [
      // snipped for brevity
      require('precss')()
    ];

Again, here is the development CSS:
    
    
    /*Variables*/
    $blue: #0000ff;
    $green: #00ff00;
    $radius: 10px;
    
    .square {
      background: $blue;
      border-radius: $radius;
    }
    
    /*Imports*/
    @import "partials/_base.css";
    
    /*Mixins*/
    @define-mixin square $dimension {
        width: $dimension;
        height: $dimension;
    }
    
    /*Nesting, variables and mixins*/
    .button {
      @mixin square 200px;
      background: $green;
      &:hover {
        background: $blue;
      }
    }

And the transformed output:
    
    
    .square {
      background: #0000ff;
      border-radius: 10px;
    }
    
    .button {
      width: 200px;
      height: 200px;
      background: #00ff00;
    }
    
    .button:hover {
      background: #0000ff;
    }

### Extending CSS With Community Plugins

While plugins are available to help us write code more efficiently, the power of PostCSS lies in the community plugins. These plugins give us quicker ways to write styles, or at least easier ways to implement creative styling. Using the PostCSS API, these plugins allow for custom properties, selectors and values in our projects, enabling us to write styles more efficiently and with less Googling.

#### Quantity Queries

[Quantity queries](https://github.com/pascalduez/postcss-quantity-queries) are powerful. They allow us to [count elements with CSS](http://www.smashingmagazine.com/2015/07/quantity-ordering-with-css/) and apply styles based on their number of siblings. While the selectors are a bit tricky to write, because they use some advanced CSS selectors, you can [use them in your CSS today](http://www.smashingmagazine.com/2015/07/constructing-css-quantity-queries-on-the-fly/). While online tools like [QQ](http://quantityqueries.com/) exist to help us write these queries, we can use PostCSS to use custom selectors in our styles directly.

To use quantity queries, install the Quantity Queries plugin in your project like any other, via the command line:
    
    
    npm i postcss-quantity-queries -D

And add the plugin to your processors:
    
    
    var processors = [
      // Snipped for brevity
      require('postcss-quantity-queries')()
    ];

Once it's installed, you can use custom selectors, available only through the plugin, to apply styles based on matched elements.

Here is the development CSS:
    
    
    // To apply styles if 'at least' number of sibling elements present
    .container > .item:at-least(5) {
      background: blue;
    }
    
    // To apply styles if 'at most' number of sibling elements present
    .item > a:at-most(10) {
      color: green;
    }
    
    // To apply styles if number of sibling items 'between' a range is present
    .gallery > img:between(4, 7) {
      width: 25%;
    }
    
    // To apply styles if 'exactly' number of provided items is present
    .profiles:exactly(4) {
      flex: 1 0 50%;
    }

And the transformed output:
    
    
    // To apply styles if 'at least' number of sibling elements present
    .container > .item:nth-last-child(n+5), .container > .item:nth-last-child(n+5) ~ .item {
      background: blue;
    }
    
    // To apply styles if 'at most' number of sibling elements present
    .item > a:nth-last-child(-n+10):first-child, .item > a:nth-last-child(-n+10):first-child ~ a {
      color: green;
    }
    
    // To apply styles if number of sibling items 'between' a range is present
    .gallery > img:nth-last-child(n+4):nth-last-child(-n+7):first-child, .gallery > img:nth-last-child(n+4):nth-last-child(-n+7):first-child ~ img {
      width: 25%;
    }
    
    // To apply styles if 'exactly' number of provided items is present
    .profiles:nth-last-child(4):first-child, .profiles:nth-last-child(4):first-child ~ .profiles {
          flex: 1 0 50%;
    }

#### Extended Shorthand Properties With Short

When writing styles, you might encounter properties whose syntax makes you say, "That could be shorter." Luckily, the [Short](https://github.com/jonathantneal/postcss-short) plugin helps us do just that: write our styles more logically. It enables us to write shorthand properties for `position` and `size`, much like how `background` and `font` can be condensed into a single declaration.

Through the PostCSS API, the shorthand declarations are transformed into browser-digestible styles, allowing for a cleaner development style sheet and a more organized production style sheet.

Install Short via the command line:
    
    
    npm i postcss-short -D

Add the plugin to your processors:
    
    
    var processors = [
      require('postcss-short')()
    ];

The `text` property includes these typographical properties: `color`, `font-style`, `font-variant`, `font-weight`, `font-stretch`, `text-decoration`, `text-align`, `text-rendering`, `text-transform`, `white-space`, `font-size`, `line-height`, `letter-spacing`, `word-spacing` and `font-family`.

And here is the development CSS:
    
    
    p {
      text: 300 uppercase dimgrey center 1.6rem 1.7 .05em;
    }

And the transformed output:
    
    
    p {
      color: dimgrey;
      font-weight: 300;
      text-align: center;
      text-transform: uppercase;
      font-size: 25px;
      font-size: 1.6rem;
      line-height: 1.7;
      letter-spacing: .05em;
    }

The `position` property allows for `top`, `left`, `right`, `bottom` values to be included in the declaration. The [order of the values](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties#Tricky_edge_cases) is clockwise, in a syntax with values from `1` to `4`. If there is a value you care to exclude, simply pass an `*` in its place.

Here is the development CSS, then:
    
    
    section {
      position: absolute 10px * *;
    }
    
    .topNav {
      position: fixed 0 * * 0;
    }
    
    .modal {
      position: fixed 40% 25%;
    }

And the transformed output:
    
    
    section {
      position: absolute;
      top: 10px;
    }
    
    .topNav {
      position: fixed;
      top: 0;
      left: 0;
    }
    
    .modal {
      position: fixed;
      top: 40%;
      right: 25%;
      bottom: 40%;
      left: 25%;
    }

### What Does This Mean For Our Industry?

Using PostCSS today and reaping the benefits are completely possible. Much like how we compile Sass and LESS, you can incorporate it in your workflow by modifying your task runner to process PostCSS. Incorporating a plugin like PreCSS allows your existing Sass projects to be ported over to PostCSS without needing any conversion of the syntax.

As of the writing of this article, a discussion is ongoing about where is the best place to write our CSS. With libraries such as [React](http://facebook.github.io/react/) gaining popularity, the idea of writing styles [within the components](https://facebook.github.io/react/tips/inline-styles.html) themselves, which allows us to transform styles with JavaScript directly on compilation, is gaining momentum. While this is still very much a discussion, it is indeed one way to transform styles with PostCSS.

Another project making waves in the industry is [CSS Modules](https://github.com/css-modules/css-modules), which scopes styles to local files and requires them as needed. This concept is already popular in JavaScript circles. And as the lines between front-end languages such as [React and JSX](https://facebook.github.io/react/docs/jsx-in-depth.html) continue to blur, it becomes hard to ignore the combined power of CSS and JavaScript.

While PostCSS extends CSS in brand new ways through custom syntaxes and properties, it could present challenges to beginners who are trying to get comfortable with the language and its intricacies. If you use PostCSS in a project with a junior developer, try to encourage in them a deep understanding of the language and of how PostCSS, much like Sass, is simply a production tool that allows styles to be written efficiently.

### Adopting PostCSS Today

Over the next few years, the way we use CSS will change in many different ways. Every project will have different requirements, to which we will have to adapt our production methods. Working within a modular ecosystem like PostCSS allows us to pick and choose the features we want to complete a project.

I encourage you to explore the PostCSS world and all of the plugins available in it. Because it is a community project, the ecosystem will grow only if people use it and create plugins. To explore more plugins, view the [available packages](https://www.npmjs.com/browse/keyword/postcss-plugin) on NPM and test their abilities in the [PostCSS Playground](https://sneakertack.github.io/postcss-playground/).

_(rb, al, ml)_
