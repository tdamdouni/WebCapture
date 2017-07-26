# JavaScript Physics Engines Comparison

_Captured: 2015-09-28 at 01:03 from [buildnewgames.com](http://buildnewgames.com/physics-engines-comparison/)_

In this article we will take a look at three popular Javascript physics libraries and one that is currently in development: box2dweb, Ammo.js, JigLibJS, and Cannon.js. For each one, a quick introduction will be given and then the library will be rated based on ease of use, performance, and feature set.

Though it is possible to run any of these libraries without a visual representation, that isn't much fun, so we will set up a small environment to see the results as the simulation runs. I'll use Three.js and its CanvasRenderer for this due to its popularity and how simple it is to use. Besides showing how the objects are interacting, this will also demonstrate how to extract scene information from each library. The scene will consist of two ramps leading down to a floor; balls will drop down onto the ramps from random locations above the scene, roll down the ramps, and land onto the floor.

## Setup

Our base scene that will be used in each example has two ramps which lead down to the ground. Balls will be dropped from random points above the ramps, rolling down to and then off of the ground plane. This simple scene will highlight the similarities and differences between the four libraries.

    
    var viewport = document.getElementById( 'viewport' ), // The canvas element we're going to use
    renderer = new THREE.CanvasRenderer({ canvas: viewport }), // Create the renderer
    scene = new THREE.Scene, // Create the scene
    camera = new THREE.PerspectiveCamera( 35, 1, 1, 1000 );
    
    renderer.setSize( viewport.clientWidth, viewport.clientHeight );
    
    camera.position.set( -10, 30, -200 );
    camera.lookAt( scene.position ); // Look at the center of the scene
    scene.add( camera );
    
    function addLights() {
        var ambientLight = new THREE.AmbientLight( 0x555555 );
        scene.add( ambientLight );
    
        var directionalLight = new THREE.DirectionalLight( 0xffffff );
        directionalLight.position.set( -.5, .5, -1.5 ).normalize();
        scene.add( directionalLight );
    }
    
    function buildScene() {
    
        var ramp_geometry= new THREE.CubeGeometry( 50, 2, 10 ),
            material_red = new THREE.MeshLambertMaterial({ color: 0xdd0000, overdraw: true }),
            material_green = new THREE.MeshLambertMaterial({ color: 0x00bb00, overdraw: true });
        
        var ramp_1 = new THREE.Mesh( ramp_geometry, material_red );
        ramp_1.position.set( -20, 25, 0 );
        ramp_1.rotation.z = -Math.PI / 28;
        scene.add( ramp_1 );
        
        var ramp_2 = new THREE.Mesh( ramp_geometry, material_red );
        ramp_2.position.set( 25, 5, 0 );
        ramp_2.rotation.z = Math.PI / 16;
        scene.add( ramp_2 );
        
        var floor = new THREE.Mesh(
            new THREE.PlaneGeometry( 100, 50 ),
            material_red
        );
        floor.position.y = -15;
        scene.add( floor );
    }
    
    addLights();
    buildScene();
    renderer.render( scene, camera );

## box2dweb

box2dweb is a port of the C++ [box2d](http://box2d.org/) project and is unique on our list of libraries in that it is designed to only simulate two-dimensional scenes. All of its classes are namespaced which can make the code a little hard to read, so [it is recommended](http://code.google.com/p/box2dweb/wiki/BasicUsage#Importing_Classes) that you create your own local variables for any objects you commonly use. Don't be fooled into thinking box2dweb is a weak library because it only performs 2D simulations; within its simple API is a ton of power. box2dweb has a full constraint system (which it calls joints), continuous collision detection for more accurate fast-moving bodies, and lots of configuration options both for the whole scene and for individual objects.

Collision detection with box2dweb is easy to do by using the `b2ContactListener` object. You can have separate event handlers for each of the four collision states: `BeginContact`, `EndContact`, `PreSolve`, and `PostSolve`. You can also detect collisions by iterating over the world's contact list after each step.

    
    var contactListener = new Box2D.Dynamics.b2ContactListener;
    contactListener.BeginContact = function( contact_details ) {
        // `contact_details` can be used to determine which two
        // objects collided and in what way
    };
    world.SetContactListener(contactListener);
    

Joints are used to constrain objects in different manners, making objects act as though they are on hinges, slide in only one direction, move like they're attached via a rope, and many other configurations. It can take a bit of testing to get a joint working like you want it, but after a while you start to get the hang of them and adding joints becomes much a much quicker process. As an example let's create a Revolute Joint - or in normal terms, a hinge. All joints in box2dweb take two bodies and a world position, except for the friction joint which only needs one body; for more details on the available joints and the various configuration options they have check out the Box2D manual or one of the many online Box2D joint tutorials.

    
    var body_a = world.CreateBody( bodyDef_A ).CreateFixture( fixDef );
    var body_b = world.CreateBody( bodyDef_B ).CreateFixture( fixDef );
    var jointDef = new Box2D.Dynamics.Joints.b2RevoluteJointDef;
    jointDef.Initialize(
        body_a.GetBody(),           // Body A
        body_b.GetBody(),           // Body B
        body_b.GetBody().GetWorldCenter() // Anchor location in world 
                // coordinates,in this case it's the center of body B
    );
    var joint = world.CreateJoint( jointDef );
    

Finally a last piece of information before we see the box2dweb demo: how to update your scene after a step in the simulation, such as updating the graphics in a game. The `world` object has a method named `GetBodyList` which will return the first body in the scene. You can then iterate over the remaining bodies in the scene by continually calling `body.GetNext()` until the `GetNext` method returns null. As you encounter each body you can update the associated graphics object or anything else which needs to be maintained. Custom information can be attached to each body when you create them by using the body definition's `userData` property. This `userData` usually includes a reference to the geometry object which makes updating that geometry's position and rotation simple.

Overview:

  * Performance: I have never seen a box2dweb scene run slowly unless it was set up poorly. Instead, game logic and the actual graphics rendering usually have the biggest impact on FPS.
  * Features: Box2D was never meant to do 3D, so most of the "missing" features aren't actually missing, they just don't work in 2D environments. If you only need two dimensions this library should have everything you need.
  * Usability: Very simple API, although it can be somewhat hard to find objects in the different parts of the namespace. The Box2D manual isn't too thorough so you may end up looking at the [flash port's documentation](http://www.box2dflash.org/docs/2.1a/reference/) and search for specific topics online.
  * Overall: This is a very powerful engine that isn't hard to set up, and there is no steep learning curve. If all you need is two-dimensional physics you won't have to look any further than box2dweb
  * Browser Support: Chrome, FireFox, IE9, Safari, Opera

## Ammo.js

Proving that Javascript has come a very long way in terms of performance, [Ammo.js](https://github.com/kripken/ammo.js/) is an [Emscripten](https://github.com/kripken/emscripten) port of [Bullet](http://bulletphysics.org/wordpress/), a physics library written in C++. Because of how Emscripten converts libraries to Javascript there are some things in Ammo.js which are more difficult to use - pointers add an extra layer of complication, for example. Thankfully there aren't many places where Ammo.js is affected by this and few projects will need to do anything differently. Ammo.js is a very feature-rich library including many built-in shapes, user-defined convex shapes, continuous collision detection, constraints, a powerful vehicle system, and many ways to fine-tune the scene.

In order to update the scene's visual representation you need to keep track of any objects added to the world - Ammo.js won't do that for you. Each time the scene is rendered you can iterate over those objects and update their positions and rotations. The way to create the physics objects in Ammo.js can seem a big dragged out and complex, but this also allows a much more fine-tuning on a per object basis. A lot of times it will be very helpful to create a function which builds the objects for you to avoid duplicating that code. Also unlike box2dweb, Ammo.js does not support collision events. In order to find and handle collisions you need to get a list of the world's contact manifolds and loop over them. Each manifold will tell you what objects collided and at what point.

Adding object constraints can be a little difficult until you get the hang of how they are defined. Most of the constraints can bind one object to a position in the world or constrain two objects relative to each other. For example, you could add a hinge constraint to a single object, making it rotate around a single point in the world, but specifying a second object means that same constraint will act like a hinge between the two objects - such as a door attached to a wall. Each type of constraint has its own settings to limit movement or specify how an object acts when it reaches those limits.

    
    // Create a Point2Point constraint to keep two objects bound together
    // position_a is the point of constraint relative to object_a's position
    // position_b is the point of constraint relative to object_b's position
    var constraint = new Ammo.btPoint2PointConstraint(
        object_a,
        object_b,
        new Ammo.btVector3( position_a.x, position_a.y, position_a.z ),
        new Ammo.btVector3( position_b.x, position_b.y, position_b.z )
    );
    world.addConstraint( constraint );
    

Overview:

  * Performance: Ammo.js is a large library, and being an Emscripten port means there are no Javascript optimizations. There is a definite tradeoff between power and performance, but most games shouldn't have an issue staying about 50 frames per second.
  * Features: One of the most complete physics libraries available in any programming language. Bullet Physics has been used in many commercial products such as Grand Theft Auto IV and Red Dead Redemption, movies such as 2012 and Sherlock Holmes, and is available as a physics engine in many 3D authoring tools including Blender and Cinema 4D - and we now have those same resources available in Javascript!
  * Usability: The API can be confusing at times, and the auto-generated documentation isn't much help. There have been times I have had to dig through Bullet's codebase to discover how a function parameter is used and even that one had been deprecated. A lot of time can be spent tweaking settings in order to understand what impact they have and finding the right setup for your game environment.
  * Overall: If you're looking for a fully-featured physics library then Ammo.js will get the job done. After taking some time to become familiar with the stranger parts of the library you can quickly develop complex scenes with rich interactions.
  * Browser Support: Chrome, Firefox, Safari, Opera

## JigLibJS

Rounding out the popular physics libraries is [JigLibJS](http://www.jiglibjs.org/), a port of yet another C++ library. However, unlike Ammo.js, it is not an automated port, instead it has been hand-crafted into a Javascript codebase with plenty of tweaks and optimizations along the way; the project has even received financial support from two companies. This customization gives JigLibJS the extra performance compared to Ammo.js, although it is not as rich in features.

Overall the API is consistent and it easy to find things, but there are a couple of places where it's easy to trip up. For example, almost all of the methods take spatial and rotational arguments in the X,Y,Z order - as you would expect. However, when defining a new box shape the order of the box's dimensions is X,Z,Y. The documentation clearly states this as the order but it can be easy to overlook if you go too fast. Another difference between JigLibJS and the other libraries is how you include them on the page. With Ammo.js and box2dweb there is only one script to include, but when using JigLibJS you must include each class file individually. This can help you keep the page's memory usage lower by not loading unused pieces of the library, but it is a bit of a hassle to include everything separately. One other detail to pay attention to is the method names - some are simple_separated_by_underscores while others follow theCamelCaseStyle, which style a certain method follows is seemingly random, but my guess is that it is related to the original port from C++.

What surprised me the most and presented the biggest challenge with JigLibJS was getting the object rotations right. In fact the official build contains an error in the radians-to-degrees conversion calculation. It is a [very simple fix](http://www.jiglibjs.org/?p=220#comment-78) but its presence is more than a bit unsettling. One other thing to look out for with object rotations: you need to set any moving object's rotational damping to a much more reasonable value. Simply put, damping is an effect that reduces the amount of linear and rotational velocities. By default, the rotational damping is set at `[.5, .5, .5, 0]` which severely limits the amount of rotation. A more realistic amount is `[.95, .95, .95, 0]`, which matches the default linear damping. Updating the graphics with JigLibJS is closer to box2dweb than it is to Ammo.js - you can get a list of all of the physics bodies by calling `world.get_bodies()` and loop over them. Object positions can be found with a simple call to `get_positions()` but rotations must be extracted as matrices and then converted into your graphic engine's format (Euler rotation, quaternion, etc).

Constraints are almost missing in JigLibJS, as it only includes three of the basics: Point (joining two objects), WorldPoint (fix an object to the a position in the world), and MaxDistance (limit the distance between two objects). While limiting, these three should be enough to achieve most tasks.

    
    
    // Create a Point2Point constraint to keep two objects bound together
    // position_a is the point of constraint relative to object_a's position
    // position_b is the point of constraint relative to object_b's position
    var constraint = new jigLib.JConstraintPoint(
        object_a,
        object_b,
        [ postition_a.x, postition_a.y, postition_a.z ],
        [ postition_b.x, postition_b.y, postition_b.z ],
        0, // max distance
        1 // timescale
    );
    world.addConstraint( constraint );
    

Overview:

  * Performance: Customized and tuned for Javascript, there are still some occasions where you will see shaky frame rates - usually these situations involve many boxes on top of each other, which is difficult for any physics engine to handle.
  * Features: While lacking some of the more obscure and less common features that Ammo.js has, JigLibJS still has enough to cover almost everything you'll ever want to do. However, I really wish it included more constraints.
  * Usability: Having to include each piece of JigLibJS individually and the seemingly random differences in the API take away from how developer-friendly this library could be. At times development can feel a bit clunky and more complex than it needs to be, but overall it is structured well and, once you learn it and set up an environment, easy to use.
  * Overall: As the popularity of physics-enabled games on the web continues to grow so will the demand for a powerful-yet-quick physics library. I believe JigLibJS is able to fit most developer's needs without requiring users to have more powerful computers. Unfortunately the workarounds required to get functioning rotations and the lack of some more basic physics concepts limits the library quite a bit.
  * Browser Support: Chrome, Firefox, IE9, Safari, Opera

## Cannon.js

The three libraries above are ports of existing physics engines. Because they are ports and not written in Javascript, they are not optimized for the web. Javascript has its own features and quirks which make developing for it unique, and no automatic code conversion tool will ever be able to efficiently optimize Javascript code. Because of this some people have felt a need for a physics library written from the ground up in Javascript. Most notably, this has resulted in [Cannon.js](https://github.com/schteppe/cannon.js), created by Stefan Hedman, who was inspired by the power of Ammo.js and Three.js's easy-to-use API. While Cannon.js is still in its early stages, I believe it is worth introducing and demonstrating. It already supports boxes, spheres, planes, and custom convex polygons, and is fairly stable - though if you push it too hard right now you'll start to see some bugs. If you are interested in the future of physics on the web then you should definitely keep an eye on Cannon.js - and consider contributing to the project if you are familiar with physics engines.

  * Browser Support: Chrome, Firefox, Safari, Opera

## Conclusion

While a lot has improved for the world of Javascript physics there is still quite a bit to be wanted. box2dweb doesn't support 3D worlds, Ammo.js can suffer from performance issues, and JigLibJS is affected by its API design and lack of functionality. Challengers such as Cannon.js and others which are 100% written in Javascript are beginning to appear, but none are yet ready to be widely used. Thankfully this does not mean we have to throw out the idea of incorporating physics in our games - but we must weigh our choices carefully to determine what will make the best games. Although very complex and dynamic scenes may not yet be achievable, a lot of other interesting possibilities are now presenting themselves. The blending of easily accessible technologies in today's browsers makes a very interesting environment for new games and I am eager to see how physics will be used in unique and fascinating user experiences.
