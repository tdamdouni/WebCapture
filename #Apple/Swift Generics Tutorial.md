# Swift Generics Tutorial

_Captured: 2015-11-25 at 20:48 from [www.raywenderlich.com](http://www.raywenderlich.com/82572/swift-generics-tutorial)_

![Take a deep dive into Swift Generics!](http://cdn3.raywenderlich.com/wp-content/uploads/2014/09/iOS-8-Feast-Swift-250x250.png)

> _Take a deep dive into Swift Generics!_

_Note from Ray_: Congratulations, you did it! By helping to spread the word about the [iOS 8 Feast](http://www.raywenderlich.com/?p=82230), you unlocked the first Swift tutorial in less than 1/2 hour! This is an abbreviated version of a chapter from [Swift by Tutorials](http://www.raywenderlich.com/?page_id=74805) to give you a sneak peek of what's inside the book. We hope you enjoy!

If you've been playing around with Swift, you already know the basics of Swift and how to write classes and structs. But Swift is more than this--much more. The topic of this tutorial is a very powerful Swift feature already popular in several other languages: generics.

With type-safe languages, it's a common problem to want to write code that acts on one type, but is also perfectly valid acting on another type. Imagine, for example, a function to add two integers. A function to add two floats would look very similar--in fact, it would look identical. The only difference would be the type of the variables.

In a strongly-typed language, you would need to define separate functions like `addInts`, `addFloats`, `addDoubles`, etc., where each function had the correct argument and return types.

Many languages implement solutions to this problem. C++, for example, uses templates. Swift, like Java and C#, uses generic programming--hence the topic of this tutorial!

Throughout this Swift Generics tutorial, you'll tour the existing generics in the language, including some you've seen already. Then, you'll build a Flickr photo search app with a custom generic data structure to keep track of the user's search terms.

_Note:_ This Swift functional programming tutorial assumes you already know the basics of Swift development. If you are new to Swift, we recommend you check out some of our [other Swift tutorials](http://www.raywenderlich.com/?page_id=2519) first.

## Introducing Generics

You might not know it, but you've probably already seen generics at work in Swift. Arrays and dictionaries are classic examples of the type safety of generics in action.

Objective-C developers are accustomed to arrays and dictionaries holding objects of many types in the same collection. This provides for great flexibility, but how do you know what an array returned from an API is meant to hold? You can only be sure by looking at documentation or at variable names, another form of documentation. Even with documentation, there is nothing (other than bug-free code!) to prevent something unexpected in the collection at runtime.

Swift, on the other hand, has typed arrays and dictionaries. An array of `Ints` can only hold Ints and can never (for example) contain a `String`. This means you can document code by writing code, allowing the compiler to do the type checking for you.

For example, in Objective-C UIKit, the method that handles touches in a custom view is as follows:

The set in this method is known to contain only `UITouch` instances, but only because the documentation says so. Nothing is stopping the objects in there from being anything else, and you generally need to cast the touches in the set as `UITouch` instances to effectively treat them as `UITouch` objects.

Swift doesn't have a set defined in the standard library at this time. However, if you used an array in place of a set, then you could write the above method like this:
    
    
    func touchesBegan(touches: [UITouch]!, withEvent event: UIEvent!)

This tells you that the touches array only contains `UITouch` instances, and the compiler will throw an error if the code calling this method tries to pass anything else. Not only does the compiler control types placed into the touches array, but you no longer need to cast elements to instances of `UITouch`!

Overall, generics provide types as a parameter to the class. All arrays act the same way, storing values in a list, but generic arrays parameterize value type. You might find it helpful to think of it like this: The algorithms you'll use on arrays are non-type-specific, so all arrays, with all types of values, can share them.

Now that you have a basic sense of generics and their utility, you're ready to apply them to a concrete scenario.

## Generics in Action

To put generics to the test, you're going to build an app that searches Flickr for images.

Start by downloading the [starter project](http://cdn3.raywenderlich.com/wp-content/uploads/2014/09/FlickrSearch-Starter2.zip) for this tutorial. Open it and quickly familiarize yourself with the main classes. The `Flickr` class handles talking to the Flickr API. Notice the API key is located with this class--one has been provided, but you may want to use your own in case you want to expand on the app. You can sign up for one [here](https://www.flickr.com/services/apps/by/).

Build and run the app. You'll see this:

![001_StarterProject](http://cdn4.raywenderlich.com/wp-content/uploads/2014/09/001_StarterPrject.png)

Not much yet! Never fear, you'll soon have this thing pulling in pictures of cats! (What else?)

## Ordered Dictionaries

Your app is going to download pictures for each user query. It will display them in a list with the most recent search at the top.

But what if your user searches for the same term twice? It would be nice if the app brought the old results back up to the top of the most recent list and replaced it with new results.

You might use an array for the data structure to back this, but for the purpose of learning generics, you're going to create a new collection: an _ordered dictionary_.

In many languages and frameworks (including Swift) sets and dictionaries do not guarantee any kind of order, in contrast to arrays. An ordered dictionary is like a normal dictionary, but the keys are in a defined order. You'll use this functionality to store search results keyed by search term, making it quick to find results and also to maintain the order for the table view.

If you were being hasty, you might create a custom data structure to handle the ordered dictionary. But you are forward thinking! You want to create something that you can use in apps for years to come! This is a perfect use case for generics.

## The Initial Data Structure

Add a new file by clicking _File\New\File…_ and selecting _iOS\Source\Swift File_. Click _Next_ and call the file _OrderedDictionary_. Finally, click _Create_.

You will have an empty Swift file. Add the following code to it:

So far this should be no surprise. The object is going to be a struct because it should have value semantics.

Now you need to make it generic so it can hold whatever type of values you want. Change the struct definition to the following:

The elements inside the angled brackets are the type parameters of the generic. `KeyType` and `ValueType` are not types themselves, but rather become parameters that you can use in place of types within the struct's definition. All will become clear shortly.

The simplest way to implement an ordered dictionary is to maintain both an array and a dictionary. The dictionary will hold the mapping, and the array will hold the order of the keys.

Add the following code inside the struct's definition:

This declares two properties, as described, and also two _type aliases_, which are a way to give a new name to an existing type. Here, you give aliases to the array and dictionary types for the backing array and dictionary, respectively. Type aliases are a great way to take a complex type and give it a much shorter name.

Notice how you can use the type parameters `KeyType` and `ValueType` from the struct definition in place of types. The array is an array of `KeyTypes`. Of course, there is no such type as `KeyType`; instead Swift treats it as whatever type the consumer of `OrderedDictionary` passes during instantiation of the generic.

At this point, you'll notice a compiler error:
    
    
    Type 'Keytype' does not conform to protocol 'Hashable'
    

This might come as a surprise. Take a look at the implementation of `Dictionary`:

This is awfully similar to the definition of `OrderedDictionary`, except for one thing--the "`: Hashable`" after `KeyType`. The `Hashable` after the semicolon declares that the type passed for `KeyType` must conform to the `Hashable` protocol. This is because `Dictionary` needs to be able to hash keys for its implementation.

It's very common to constrain generic type parameters in this way. For example, you might want to constrain the value type to conform to the `Equatable` or `Printable` protocols depending on what your app needs to do with those values.

Open _OrderedDictionary.swift_ and replace your struct definition with the following:

This declares that the `KeyType` for `OrderedDictionary` must conform to `Hashable`. This means that whatever type `KeyType` becomes, it will be acceptable as a key for the underlying dictionary as well.

The file will now compile again without any errors!

## Keys, Values and All That Jazz

What use is a dictionary if you can't add values to it? Open _OrderedDictionary.swift_ and add the following function inside your struct definition:
    
    
    // 1
    mutating func insert(value: ValueType, forKey key: KeyType, atIndex index: Int) -> ValueType?
    {
      var adjustedIndex = index
     
      // 2
      let existingValue = self.dictionary[key]
      if existingValue != nil {
        // 3
        let existingIndex = find(self.array, key)!
     
        // 4
        if existingIndex < index {
          adjustedIndex--
        }
        self.array.removeAtIndex(existingIndex)
      }
     
      // 5
      self.array.insert(key, atIndex:adjustedIndex)
      self.dictionary[key] = value
     
      // 6
      return existingValue
    }

This introduces a couple of new things. Let's take it step by step:

  1. The method to insert a new object, `insert(_:forKey:atIndex)`, needs to take three parameters: the _value_ for a particular _key_ and the _index_ at which to insert the key-value pair. There is a keyword here that you might not have seen before: `mutating`. 

Structs are designed to be immutable by default, meaning you ordinarily can't mutate struct member variables in an instance method. Since that is quite limiting, you can add the mutating keyword to tell the compiler that the method is allowed to mutate state in the struct. This helps the compiler make decisions about when to take copies of structs (they are copy-on-write) and also helps document the API.

  2. You pass the key to the indexer of the `Dictionary`, which returns the existing value if one already exists for that key. This `insert` method emulates the same behavior as the `Dictionary`'s `updateValue` and therefore saves the existing value for the key.
  3. If there is an existing value, then and only then does the method find the index into the array for that key.
  4. If the existing key is before the insertion index, then you need to adjust the insertion index because you're about to remove the existing key.
  5. You update the array and dictionary, as appropriate.
  6. Finally, you return the existing value. Since there might not be an existing value, the function returns an optional value.

Now that you have the ability to add values to the dictionary, what about removing values?

Add the following function to the `OrderedDictionary` struct definition:
    
    
    // 1
    mutating func removeAtIndex(index: Int) -> (KeyType, ValueType)
    {
      // 2
      precondition(index < self.array.count, "Index out-of-bounds")
     
      // 3
      let key = self.array.removeAtIndex(index)
     
      // 4
      let value = self.dictionary.removeValueForKey(key)!
     
      // 5
      return (key, value)
    }

Let's take it step by step again:

  1. Once more, this is a function that mutates the internal state of the struct, and you therefore mark it as such. The name `removeAtIndex` matches the method on `Array`. It's a good idea to consider mirroring the APIs of the system library when appropriate. It helps make developers using your API feel at home on the platform.
  2. First, you check the index to see if it's within the bounds of the array. Trying to remove an out-of-bounds element from the underlying array will trigger a runtime error, so the check here will catch that condition a bit earlier. You may have used assertions in Objective-C with the assert function; `assert` is available in Swift too, but `precondition` is active in release builds so your shipped apps will terminate if the preconditions fails. 
  3. Next, you obtain the key from the array for the given index while at the same time removing the value from the array.
  4. Then, you remove the value for that key from the dictionary, which also returns the value that was present. The dictionary might not contain a value for the given key, so `removeValueForKey` returns an optional. In this case, you know that the dictionary will contain a value for the given key, because the only method that can add to the dictionary is your own `insert(_:forKey:atIndex:)`, which you wrote. Thus you can immediately unwrap the optional with ! knowing there will be a value there.
  5. Finally, you return the key and value in a tuple. This parallels the behavior of Array `removeAtIndex` and Dictionary `removeValueForKey`, which return the existing values.

## Accessing Values

You can now write to the dictionary but you can't read from it--that's no good for a data structure! You're now going to add the methods that will allow you to retrieve values from the dictionary.

Open _OrderedDictionary.swift_ and add the following code to the struct definition, just underneath the `array` and `dictionary` variable declarations:

This is a computed property for the count of the ordered dictionary, a commonly needed piece of information for such a data structure. The count of the array will always match the count of the ordered dictionary, so this is an easy one!

Next, you need a way to access elements of the dictionary. In Swift, you access a dictionary using the subscript syntax, as follows:

You're familiar with this syntax by now, but have likely only seen it used on arrays and dictionaries. How would you achieve this using your own classes and structs? Swift, fortunately, makes it simple to add subscript behavior to custom classes.

Add the following code to the bottom of the struct definition:
    
    
    // 1
    subscript(key: KeyType) -> ValueType? {
      // 2(a)
      get {
        // 3
        return self.dictionary[key]
      }
      // 2(b)
      set {
        // 4
        if let index = find(self.array, key) {
        } else {
          self.array.append(key)
        }
     
        // 5
        self.dictionary[key] = newValue
      }
    }

Here's what this code does:

  * This is how you add subscript behavior. Instead of `func` or `var`, you use the `subscript` keyword. The parameter, in this case key, defines the object that you expect to appear inside the square brackets.
  * Subscripts can comprise setters and getters, just like computed properties can. Notice that this one has both (a) a `get` and (b) a `set` closure, defining the getter and setter, respectively.
  * The getter is simple: It needs to ask the dictionary for the value for the given key. The dictionary's subscript already returns an optional to allow for indicating that no value exists for that key.
  * The setter is more complex. First, it checks if the key already exists in the ordered dictionary. If it doesn't exist, then you need to add it to the array. It makes sense are for the new key to go at the end of the array, so you add the value to the array using append.
  * Finally, you add the new value to the dictionary for the given key, passing in the new value via the implicitly named variable newValue.

Now you can index into the ordered dictionary as if it were a normal dictionary. You can get the value for a certain key, but what about accessing by index, as with an array? Seeing as how this is an ordered dictionary, it would be useful to access an element by index too.

Classes and structs can have multiple subscript definitions for different argument types. Add the following function to the bottom of your struct definition:
    
    
    subscript(index: Int) -> (KeyType, ValueType) {
      // 1
      get {
        // 2
        precondition(index < self.array.count, 
                     "Index out-of-bounds")
     
        // 3
        let key = self.array[index]
     
        // 4
        let value = self.dictionary[key]!
     
        // 5
        return (key, value)
      }
    }

This is similar to the subscript you added previously, except that the type of the parameter is now `Int`, because that is what you use to reference the index of an array. This time, however, the return type is a tuple of key and value, because that is what your `OrderedDictionary` stores at a given index.

Here's what this code does:

  1. This subscript only has a getter. You could implement a setter for it as well, first checking that indexes that are within the size range of the ordered dictionary.
  2. The index must be within the bounds of the array, which defines the length of the ordered dictionary. You use a precondition to alert programmers who try to access beyond the bounds of the ordered dictionary.
  3. You find the key by obtaining it from the array.
  4. You find the value by obtaining it from the dictionary for the given key. Notice, again, the use of the unwrapped optional, because you know that the dictionary must contain a value for any key that's in the array.
  5. Finally, you return a tuple containing the key and value.

_Challenge_: Implement a setter for this subscript. Add set followed by a closure, just as in your previous subscript definition.

At this point, you may wonder what happens if `KeyType` is `Int`. The benefit of generics is to allow any hashable type as the key, including `Int`. In that case, how does the subscript know which subscript code to use?

That's where you would need to give more type information to the compiler to let it know your intentions. Notice that each of the subscripts has a different return type. Therefore, if you tried to set a key-value tuple, the compiler would know that it should use the array-style subscript.

## Playground Testing

Let's start a playground so that you can experiment with how the compile infers which subscript method to use, and how your `OrderedDictionary` works in general.

Create a new playground by clicking _File\New\File…_, selecting _iOS\Source\Playground_ and clicking _Next_. Call it _ODPlayground_ and then click _Create_.

Copy and paste the entirety of _OrderedDictionary.swift_ into the new playground. You have to do this because, sadly, at the time of writing this tutorial the playground cannot "see" code in your app module.

Now add the following to the bottom of your playground:
    
    
    var dict = OrderedDictionary<Int, String>()
    dict.insert("dog", forKey: 1, atIndex: 0)
    dict.insert("cat", forKey: 2, atIndex: 1)
    println(dict.array.description 
            + " : " 
            + dict.dictionary.description)
     
    var byIndex: (Int, String) = dict[0]
    println(byIndex)
     
    var byKey: String? = dict[2]
    println(byKey)

In the sidebar (or via _View\Assistant Editor\Show Assistant Editor_) you can see the output of the `println()`:

![002_Console](http://cdn1.raywenderlich.com/wp-content/uploads/2014/09/002_Console.png)

In this example, the dictionary has an Int key, so the compiler will look at the type of the variable being assigned to determine which subscript to use. Since `byIndex` is an `(Int, String)` tuple, the compiler knows to use the array style index version of the subscript which matches the expected return type.

Try removing the type definition from one of the `byIndex` or `byKey` variables. You'll see a compiler error, indicating that the compiler doesn't implicitly know which subscript to use.

Experiment with the ordered dictionary in the playground to get a feel for how it works. Try adding to it, removing from it and changing the key and value types, before returning to the app.

You can now read and write into your ordered dictionary! That takes care of your data structure. Now you can get cracking with the app!

## Adding Image Search

It's time to shift your attention back to the app in hand. Open _MasterViewController.swift_ and add the following variable definition, just below the two `@IBOutlets`:

This is going to be the ordered dictionary that holds the searches the user submits to Flickr. As you can see, it maps String, the search term, to an array of `Flickr.Photo`, or the photos returned from the Flickr API. Notice you give the key and value in angle brackets just as you would for a normal dictionary. These become the type parameters `KeyType` and `ValueType` in the implementation.

You may wonder why the type `Flickr.Photo` has a period in it. It's because `Photo` is a class defined inside the `Flickr` class. This hierarchy is a rather useful feature of Swift, helping to contain namespace while keeping class names short. Inside the `Flickr` class, you can use `Photo` alone to refer to the photo class, because the context tells the compiler what it is.

Next, find the table view data source method called `tableView(_:numberOfRowsInSection:)` and change it to look like this:

This method now uses the ordered dictionary to tell the table view how many rows it has.

Next, find the table view data source method `tableView(_:cellForRowAtIndexPath:)` and change it to look like this:
    
    
    func tableView(tableView: UITableView, 
                   cellForRowAtIndexPath indexPath: NSIndexPath)
                  -> UITableViewCell
    {
      // 1
      let cell = 
        tableView.dequeueReusableCellWithIdentifier("Cell", 
          forIndexPath: indexPath) as UITableViewCell
     
      // 2
      let (term, photos) = self.searches[indexPath.row]
     
      // 3
      cell.textLabel.text = "\(term) (\(photos.count))"
     
      return cell
    }

Here's what you are doing in this method:

  1. First, you dequeue a cell from the `UITableView`. You need to cast it directly to a `UITableViewCell` because `dequeueReusableCellWithIdentifier` still returns `AnyObject` (`id` in Objective-C) and not a `UITableViewCell`. Perhaps in the future, Apple will rewrite its APIs to take advantage of generics as well!
  2. Then, you obtain the key and value for the given row, using the subscript by index that you wrote.
  3. Finally, you set the cell's text label appropriately and return the cell.

Now for the meat in the pie. Find the `UISearchBarDelegate` extension and change the single method in there to look like this:
    
    
    func searchBarSearchButtonClicked(searchBar: UISearchBar!) {
      // 1
      searchBar.resignFirstResponder()
     
      // 2
      let searchTerm = searchBar.text
      Flickr.search(searchTerm) {
        switch ($0) {
        case .Error:
          // 3
          break
        case .Results(let results):
          // 4
          self.searches.insert(results, 
                               forKey: searchTerm, 
                               atIndex: 0)
     
          // 5
          self.tableView.reloadData()
        }
      }
    }

This method is called when the user taps on the search button. Here's what you are doing in this method:

  1. You resign the search bar as first responder, dismissing the keyboard.
  2. Then, you take the search term as the text in the search bar right now, and use the `Flickr` class to search for that term. The search method of `Flickr` takes both a search term and a closure to execute on success or failure of the search. The closure takes one parameter: an enumeration of either `Error` or `Results`.
  3. In the case of Error, nothing happens. You could make it show an alert here if you wanted, but let's keep this simple for now. The code requires a break here to tell Swift's compiler of your intention that the error case do nothing.
  4. If the search works, search returns the results as the associated value in the SearchResults enum type. You add the results to the top of the ordered dictionary, with the search term as the key. If the search term already exists in the dictionary, this will bring the search term to the top of the list and update it with the latest results.
  5. Finally, you reload the table view because you now have new data.

Woo! Your app will now search for images!

Build and run the app, and make a couple of searches. You'll see something like this:

![003_Search](http://cdn1.raywenderlich.com/wp-content/uploads/2014/09/003_Search.png)

Now repeat one of the searches that's not at the top of the list. You'll see it pop back to the top:

![004_Search2](http://cdn2.raywenderlich.com/wp-content/uploads/2014/09/004_Search2.png)

Tap into one of the searches and notice it doesn't show the photos. It's time to fix that!

## Show Me the Photos!

Open _MasterViewController.swift_ and find `prepareForSegue`. Change it to look like this:
    
    
    override func prepareForSegue(segue: UIStoryboardSegue, 
                                  sender: AnyObject?)
    {
      if segue.identifier == "showDetail" {
        if let indexPath = self.tableView.indexPathForSelectedRow()
        {
          let (_, photos) = self.searches[indexPath.row]
          (segue.destinationViewController
             as DetailViewController).photos = photos
        }
      }
    }

This uses the same method of accessing the `searches` ordered dictionary as when creating the cells. It doesn't use the key (search term), though, so you indicate with the underscore that this part of the tuple doesn't need to be bound to a local variable.

Build and run the app, make a search and then tap into it. You'll see something like this:

![005_Cats](http://cdn1.raywenderlich.com/wp-content/uploads/2014/09/005_Cats.png)

Hello, cats! Doesn't this make you want to just purr with pleasure? :]

## Where To Go From Here?

Here is the [finished sample project](http://cdn5.raywenderlich.com/wp-content/uploads/2014/09/FlickrSearch-Final1.zip) from this Swift Generics tutorial.

Congratulations, you have learned a lot about generics! In addition, you have learned about other interesting things like subscripting, structs and mutability, preconditions, and more.

If you want to learn more about Generics, check out the full chapter in [Swift by Tutorials](http://www.raywenderlich.com/?page_id=74805), where I take this example a bit further and cover generic functions and protocols as well.

I hope to see you make use of the power of Generics in your future apps to help avoid code duplication and make your code more reusable. If you have any questions or comments in your journey, please join the forum discussion below!
