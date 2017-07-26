# Introducing Mavo: Create Web Apps Entirely By Writing HTML!

_Captured: 2017-05-16 at 20:38 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/05/introducing-mavo/)_

  * [0 Comments](https://www.smashingmagazine.com/2017/05/introducing-mavo/)

Many companies try to create a great experience for customers. But few are willing to make the changes required to deliver on that promise. In fact most don't even realize just how bad their experience can be. This is why we made a new book called "User Experience Revolution," a **practical battle plan for placing the user at the heart of your company**. [Get the book now!](https://shop.smashingmagazine.com/products/user-experience-revolution?utm_source=magazine&utm_campaign=ux-revolution&utm_medium=html-ad-content-1)

Raise your hand if you ever wanted to:

  * Make a website that non-technical folks (clients? family members?) can edit right in the browser
  * Make a website that presents an editable collection of items (your portfolio?)
  * Upload images to a website you made, right from the browser
  * Make an app to track and/or share an aspect of your life
  * Make a website that lets other people suggest edits to your data
  * Make an app that calculates something and presents the results in a custom way.

You can put your hand down now, it will get tired up there.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/comic-opt.gif)[1](https://www.smashingmagazine.com/2017/05/introducing-mavo/)

> _Image adapted from this excellent Zen Pencils comic, used with permission. (Large preview)_

What if I told you, that you can do these things (and more!), **just with HTML and CSS**? **No programming code to write, no servers to manage.** You can make any element editable and saveable just by adding one HTML attribute to it. In fact, you can store your data locally in the browser, on Github, on Dropbox, or any other service just by changing an HTML attribute.

You can also turn any HTML element into a collection, with customizable controls for adding items, deleting items, and rearranging items via drag and drop. And your website visitors could suggest edits to your data that create Github pull requests behind the scenes, straight from your website.

What if I told you can dynamically display the results of calculations on this data anywhere in your UI with a syntax that is engineered to be easy to read and write, even by non-programmers? And that you can create dynamic, interactive websites with the same processes and hosting providers you use for static websites?

These are only some of the things you can do with [Mavo](http://mavo.io), the project I've been working on for the past two years at [MIT CSAIL](http://csail.mit.edu/) and am excited to release today. **Mavo is a language that extends HTML to describe applications that manage, store, and transform data.** All you need to do to use Mavo in any HTML page is to [include its two files](http://mavo.io/docs/primer/#using-mavo). Yup, that's it.

But how does it all work? Let's look at a few examples.

Assume we have a run-of-the-mill static homepage, with the following HTML inside `body>`:
    
    
    <main>
    <h1>
    	<img src="images/photo.jpg" alt="">
    	<span>Grumpy Cat</span>
    </h1>
    <p>
    	<strong>Tardar Sauce</strong> (born April 4, 2012), commonly known as <strong>Grumpy Cat</strong>, is a cat, Internet and media personality and actress...
    </p>
    
    <div class="links">
    	<a class="twitter" href="https://twitter.com/RealGrumpyCat" target="_blank" title="Twitter">🐦</a>
    	<a class="facebook" href="https://www.facebook.com/TheOfficialGrumpyCat" target="_blank" title="Facebook">f</a>
    	<a class="wikipedia" href="https://en.wikipedia.org/wiki/Grumpy_Cat" target="_blank" title="Wikipedia">W</a>
    </div>
    </main>
    

Photos and text taken from [Grumpy Cat's Wikipedia page](https://en.wikipedia.org/wiki/Grumpy_Cat).

Which, when styled looks like this:
    
    
    <main mv-app="todo" mv-storage="local" mv-mode="edit">
    	<header>
    		<h1>My tasks</h1>
    		<p><strong>[count(done)]</strong> done out of <strong>[count(task)]</strong> total</p>
    	</header>
    
    	<ul>
    		<li property="task" mv-multiple>
    			<label>
    				<input property="done" type="checkbox" />
    				<span property="taskTitle">Do stuff</span>
    			</label>
    		</li>
    	</ul>
    </main>
    

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/02-Introducing-Mavo-780w-opt.png)[8](https://www.smashingmagazine.com/2017/05/introducing-mavo/)

> _Large preview_

By adding a few Mavo attributes, we can make it editable, and save its data to the cloud via Github (Github is only one of the supported services):

You can see the result in the video below or play with the live demo [here](https://mavo.io/demos/homepage).

> _>_

But how did it work? What did we just do with all these attributes? Here is a breakdown:

  * `[mv-app="homepage"](http://mavo.io/docs/primer/#mv-app)` gives our app a name and tells Mavo to be active on this portion of the page.
  * `[property](http://mavo.io/docs/primer/#property)` attributes name important elements. By default, these elements will become editable and will be saved. The editing UI is generated based on the type of element, e.g. note that `img` is edited very differently from  or `span`. Of course, any generated UI is fully customizable.
  * The `[mv-storage](http://mavo.io/docs/primer/#mv-storage)` attribute tells Mavo where to store the data. Here its value is a (fuzzy) Github URL, so any data and uploads are stored on Github.
  * `mv-plugins="tinymce"` loads the [Mavo TinyMCE plugin](https://plugins.mavo.io/plugin/tinymce) for rich text editing, and `class="tinymce"` tells Mavo to edit this element via TinyMCE. Mavo is designed for extensibility, so developers that _do_ know JavaScript can write [Plugins](https://plugins.mavo.io) that extend Mavo's functionality or even completely change how it works. Using these plugins is as easy as adding an `mv-plugins` attribute to any element in your page.

Besides editability and persistence, one of Mavo's cool features when used in conjunction with Github is that you can let visitors log in to send **"edit suggestions"** to your data, entirely via the same graphical interface you use for editing said data. These "edit suggestions" create pull requests behind the scenes that you can easily approve or reject.

At this point, we have demonstrated how Mavo can help get rid of CMSes for very simple websites. However, it can do a lot more. Let's look at a very different example, a to-do app!

As before, we start with a static HTML mockup:
    
    
    <main>
    	<header>
    		<h1>My tasks</h1>
    		<p><strong>0</strong> done out of <strong>1</strong> total</p>
    	</header>
    
    	<ul>
    		<li>
    			<label>
    				<input type="checkbox" />
    				Do stuff
    			</label>
    		</li>
    	</ul>
    </main>
    

Which looks like this after some styling:

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/01-Introducing-Mavo-780w-opt.png)[16](https://www.smashingmagazine.com/2017/05/introducing-mavo/)

> _Large preview_

Can we use Mavo to turn this into a fully functional to-do list? You probably suspect what the answer is by now: Indeed we can! These are the changes we would need to make to our markup:
    
    
    <main mv-app="todo" mv-storage="local" mv-mode="edit">
    	<header>
    		<h1>My tasks</h1>
    		<p><strong>[count(done)]</strong> done out of <strong>[count(task)]</strong> total</p>
    	</header>
    
    	<ul>
    		<li property="task" mv-multiple>
    			<label>
    				<input property="done" type="checkbox" />
    				<span property="taskTitle">Do stuff</span>
    			</label>
    		</li>
    	</ul>
    </main>
    

You can see the result in the video below or play with the live demo [here](https://mavo.io/demos/todo).

> _>_

So, what did we do here?

  * `mv-storage="local"` tells Mavo to store the data locally in the browser.
  * You already know about `property` from the previous example. Note that it can also be used to group other properties.
  * `[mv-multiple](http://mavo.io/docs/primer/#mv-multiple)` is the Mavo feature that seems to excite people the most. It converts the element it's on to an editable collection of items, full with controls to add and delete items, reorder items via drag and drop, and even keyboard shortcuts for all these!
  * `mv-mode="edit"` tells Mavo that everything should be editable immediately, and does not need a separate read mode.
  * `[count(done)]` and `[count(task)]` are [expressions](http://mavo.io/docs/primer/#expressions), similar to those you may have used in spreadsheets. Expressions are written in MavoScript, an expression language designed to be readable, forviging, and easy to use even by non-programmers. Experienced developers can also use JavaScript in Mavo Expressions.

Mavo does not treat HTML as merely a shortcut to JavaScript, but as the primary language for creating web applications. We have done [actual user studies](http://dl.acm.org/citation.cfm?id=2984551) to prove that Mavo can be successfully used even by people with no programming experience, the [results](http://dl.acm.org/citation.cfm?id=2984551) of which are published at ACM UIST 2016, one of the top academic venues for Human-Computer Interaction research. Our vision is that JavaScript, server backends, and databases should become the "Assembly of the Web", mainly needed for specialized or high performance tasks. For everything else, HTML and CSS should suffice.

Want to know more? Go over to [mavo.io](https://mavo.io), look at the [Demos](https://mavo.io/demos) and read the [Docs](https://mavo.io/docs/primer) to understand more about the language.

Is Mavo perfect yet? Far from it. As with every project of this magnitude, there is much more work to be done than what has already been done, in every front. But it's at a state where it can be useful, and demonstrate our vision for the future of Web development. We hope that others share that vision too, and (why not?) want to help us get there.

_(vf, yk, il)_
