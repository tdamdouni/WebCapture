# Full Stack Node Development

_Captured: 2017-10-19 at 19:35 from [dzone.com](https://dzone.com/articles/midwest-js-project-source-on-full-stack-node-devel?edition=334792&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-19)_

Add user login and MFA to your next project in minutes. [Create a free Okta developer account](https://dzone.com/go?i=247342&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%25253EGlobal%25253Edeveloper-trial-sep-14-FY18Q3%26utm_medium%3Dpre-text%26utm_source%3Ddzone-web-dev-zone-all-developer), drop in one of our SDKs to your application and get back to building.

Back in August, I had participated in [Midwest JS](http://midwestjs.com/) located in Minneapolis, Minnesota. As you may know, I'm a huge fan of developing full stack applications with the JavaScript stack. This is exactly what I had presented on at the conference.

My session was well attended and many developers were taught how to use Node.js with Couchbase to develop a RESTful API and Angular as the client facing layer.

![](https://blog.couchbase.com/wp-content/uploads/2017/08/midwestjs-couchbase.jpg)

As promised, I am going to revisit the material I went over during the presentation so the concepts and code can be reproduced and expanded upon.

Going forward, the assumption is that you've got [Couchbase Server](https://www.couchbase.com), [Node.js](https://nodejs.org), and the [Ionic Framework](http://ionicframework.com/) CLI installed and configured. Couchbase will be the NoSQL Database, Node.js will power our backend, and Ionic Framework will give us a web frontend powered by Angular.

The project created at Midwest JS allowed you to store information about video game consoles and video games for various consoles. This demonstrated the use of CRUD as well as relationships between NoSQL documents and how Couchbase makes it easy.

## Creating the Node.js With Couchbase NoSQL Backend

Before we can begin development, we need to create a new Node.js project. From the command line, execute the following:

The above command will create a project **package.json** file and install our project dependencies. The `cors` package will allow us to use Node and Angular locally on two different ports without getting cross-origin resource sharing errors. The `uuid` package will allow us to generate unique strings for use as document keys. The `body-parser` package will allow us to send JSON data in HTTP requests. We'll be using Express and Couchbase which explains the other two packages.

Create an **app.js** file within your project. It will contain all the source code for our Node.js application. As boilerplate, it should look like the following:
    
    
    app.use(BodyParser.json());
    
    
    var bucket = cluster.openBucket("default", "");
    
    
    app.get("/consoles", (request, response) => {});
    
    
    app.post("/console", (request, response) => {});
    
    
    app.post("/game", (request, response) => {});
    
    
    app.get("/games", (request, response) => {});
    
    
    app.get("/game/:id", (request, response) => {});
    
    
    var server = app.listen(3000, () => {
    
    
        console.log("Listening on port " + server.address().port + "...");

Notice that we've imported each of the downloaded dependencies, initialized and configured Express, and connected to a Bucket in our Couchbase cluster.

We will have five different RESTful API endpoints for this application.

The first logical thing to do would be to create a video game console so we can add games to it. Take a look at the following endpoint code:
    
    
    app.post("/console", (request, response) => {
    
    
        if(!request.body.title) {
    
    
            return response.status(401).send({ "message": "A `title` is required." });
    
    
        bucket.insert(id, request.body, (error, result) => {

In the above logic, we are validating that a `title` exists in our request. If it does, we will generate a new id, assign a `type` to the data in our request, and insert it into Couchbase. The success or failure response of the insert will be returned to the client, which will eventually be an Angular application.

To query for video game consoles, we'll need to query based on the `type` property. For this reason, we'll have to use a N1QL query rather than a lookup by id.
    
    
    app.get("/consoles", (request, response) => {
    
    
        var statement = "SELECT `" + bucket._name + "`.*, META().id FROM `" + bucket._name + "` WHERE type = 'console'";
    
    
        bucket.query(query, (error, result) => {

The N1QL query is nothing more than a simple `SELECT` statement that you'd find in SQL. After executing the query, we would return the response back to the client.

This brings us to the actual video games. Things get a little more complex, but not more difficult.
    
    
    app.post("/game", (request, response) => {
    
    
        if(!request.body.title) {
    
    
            return response.status(401).send({ "message": "A `title` is required." });
    
    
        } else if(!request.body.cid) {
    
    
            return response.status(401).send({ "message": "A `cid` is required." });
    
    
        bucket.insert(id, request.body, (error, result) => {

In the above endpoint logic, we plan to insert a new video game into the database. This is no different than what we saw when inserting a new video game console into the database. We are defining a `type` property, but we are also making sure a `cid` exists. The `cid` will be a console id which will allow us to establish a relationship with our data.

When you have relationships, you have `JOIN` operations.
    
    
    app.get("/games", (request, response) => {
    
    
        bucket.query(query, (error, result) => {

In the above endpoint, we are doing another N1QL query, but this time we have a `JOIN` operation. It isn't useful to return a `cid` when querying for video games, so we `JOIN` and replace that information with the console title of the other document.

Likewise, we have a similar query when trying to find a specific video game:
    
    
    app.get("/game/:id", (request, response) => {
    
    
        if(!request.params.id) {
    
    
            return response.status(401).send({ "message": "An `id` is required." });
    
    
        bucket.query(query, { "id": request.params.id }, (error, result) => {

The alternative to using N1QL and `JOIN` operations would be to do two lookups based on id. There is nothing wrong with this practice, but, in my opinion, it is easier to just let the database take care of a `JOIN` rather than trying to `JOIN` via the application layer.

This brings us to the client frontend.

## Creating the Ionic Framework With Angular Frontend

As previously mentioned, this time around we are using the Ionic Framework which uses a flavor of Angular. I chose this because I was feeling too lazy to create an attractive frontend with Bootstrap or Foundation.

With the Ionic Framework CLI available, execute the following:

The above command will create a project called **pwa** using the Ionic Framework `sidemenu` template.

The base template is useful, but it doesn't have everything we need. We need to add a few pages to the application.

Using the Ionic Framework generators, or manually, create a **consoles**, **games**, and **game** page. Each of these pages should have an HTML, SCSS, and TypeScript file and each page directory should be in the **pages** directory.

Open the project's **app/app.component.ts** file and make it look like the following:
    
    
      pages: Array<{title: string, component: any}>;
    
    
      constructor(public platform: Platform, public statusBar: StatusBar, public splashScreen: SplashScreen) {
    
    
        this.platform.ready().then(() => {
    
    
        this.nav.setRoot(page.component);

Notice that we've imported `GamesPage` and `ConsolesPage`, updated the `pages` array, and set the default root page as `GamesPage`. By doing this we've set up navigation and the default page when the application launches.

To complete the setup, we also need to alter the project's **app/app.module.ts** file. Make it look like the following:

Notice that we've imported each of our new pages and added them to the `declarations` and `entryComponents` arrays of the `@NgModule` block.

Now we can focus on the development of the application and connecting it to our API.

Open the project's **src/pages/games/games.ts** file and make it look like the following. We're going to break down what is happening next.
    
    
        public constructor(public navCtrl: NavController, private http: Http, private modalCtrl: ModalController) {
    
    
            this.http.get("http://localhost:3000/games")
    
    
                .map(result => result.json())
    
    
            let gameModal = this.modalCtrl.create(GamePage);
    
    
                this.http.post("http://localhost:3000/game", JSON.stringify(data), options)
    
    
                        this.games.push({ "game_title": data.title, "console_title": ""});

Within the `GamesPage` class, we have a public variable called `games`. Because it is public, it will be accessible via the HTML. It will contain all the games returned from the Node.js application.

When the page loads, we want to query our endpoint. It is never a good idea to do this in the `constructor` method, so, instead, we use the `ionViewDidEnter` method. After issuing the request, the result is transformed into JSON and then loaded into our public variable.

If we want to create a new game in our database, things are a little different. We are going to display a modal dialog and collect input.
    
    
        let gameModal = this.modalCtrl.create(GamePage);
    
    
            this.http.post("http://localhost:3000/game", JSON.stringify(data), options)
    
    
                    this.games.push({ "game_title": data.title, "console_title": ""});

The `create` method will display our `GamePage` which will be in modal format. Any data entered in the form on the modal will be returned back to the `GamesPage` and sent via an HTTP request to the API.

Before we take a look at `GamePage`, let's look at the HTML that powers `GamesPage`.
    
    
                <ion-icon name="menu"></ion-icon>
    
    
                <button ion-button icon-only (click)="create()">
    
    
                    <ion-icon name="add"></ion-icon>
    
    
    <span class="item-note">{{game.console_title}}</span>
    
    
    </button> </ion-list> </ion-content>

In the above HTML, we are looping through our public `games` array. Each object in the array is rendered to the screen within a list. Angular does all the heavy lifting for us.

Open the project's **src/pages/game/game.ts** file and include the following:
    
    
        constructor(public navCtrl: NavController, public navParams: NavParams, public viewCtrl: ViewController, private http: Http) {
    
    
            this.http.get("http://localhost:3000/consoles")
    
    
                .map(result => result.json())
    
    
                    for(let i = 0; i < result.length; i++) {
    
    
                        this.consoles.push(result[i]);
    
    
            this.viewCtrl.dismiss(this.input);

This modal logic is similar to what we've already seen. There will be a form that is bound to HTML and TypeScript. When the `ionViewDidEnter` triggers, we query for console information. This console information will eventually be used for a radio list that the user can select from.

When the user selects the `save` method, the data bound in the public form is passed to the previous `GamesPage` page.

The HTML that powers this modal, found in **src/pages/game/game.html** looks like this:
    
    
                <ion-input type="text" [(ngModel)]="input.title"></ion-input>
    
    
                    <ion-option *ngFor="let console of consoles" value="{{ console.id }}">{{ console.title }}</ion-option>
    
    
                <button ion-button full (click)="save()">Save</button>

We have a simple list that makes up our form. The form elements are bound to our TypeScript variable and the console information is looped through to populate an HTML `select` element.

This brings us to the final page of the Angular frontend.

Open the project's **src/pages/consoles/consoles.ts** file and include the following:
    
    
        public constructor(public navCtrl: NavController, private http: Http, private alertCtrl: AlertController) {
    
    
            this.http.get("http://localhost:3000/consoles")
    
    
                .map(result => result.json())
    
    
                            this.http.post("http://localhost:3000/console", JSON.stringify(data), options)

While not too different than what we've already seen, we have a new feature. We are using a popup dialog to collect input for new video game console information.

When the popup is dismissed, the following is executed:
    
    
        this.http.post("http://localhost:3000/console", JSON.stringify(data), options)

This will take the information found in the form and send it via HTTP to our API which will, in turn, save the console information to the database.

Awesome right?

The HTML found in the project's **src/pages/consoles/consoles.html** file looks like the following:
    
    
                <ion-icon name="menu"></ion-icon>
    
    
                <button ion-button icon-only (click)="create()">
    
    
                    <ion-icon name="add"></ion-icon>

Again, it is near identical to the other HTML files that we've seen.

## Conclusion

You just got a recap of everything I went over at Midwest JS 2017. We saw how to create a Node.js API that communicates with Couchbase, our NoSQL database, as well as creating a frontend using Angular and Ionic Frameworks. These are just a few components of a full stack application.

For more information on using Node.js with Couchbase, check out the [Couchbase Developer Portal](https://developer.couchbase.com). If you'd like me to come back to Midwest JS, let me know in the comments.

Launch your application faster with Okta's user management API. [Register today for the free forever developer edition!](https://dzone.com/go?i=234224&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%25253EGlobal%25253Edeveloper-trial-FY18Q3%26utm_medium%3Dpost-text%26utm_source%3Ddzone-web-dev-zone-all-developer)
