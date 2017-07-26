# Custom Subscripting in Swift Tutorial

_Captured: 2015-11-25 at 20:41 from [www.raywenderlich.com](http://www.raywenderlich.com/79764/custom-subscripting-swift-tutorial)_

![Create a Checkers game that takes advantage of subscripting.](http://cdn4.raywenderlich.com/wp-content/uploads/2014/09/initialCheckerBoard.png)

> _Create a Checkers game that takes advantage of subscripting._

_Update 4/9/15_: Updated for Xcode 6.3 / Swift 1.2

Subscripting first came to Objective-C in Xcode 4.4, way back in the middle of 2012. At this time, Swift was already two years into development. As with many other powerful features in Objective C, such as ARC, subscripting also became part of Swift.

Subscripts don't actually add functionality to a class, instead they're shortcuts to access members of a collection. It sounds like a trivial application, but subscripts significantly enhance the convenience factor and readability of your code.

For example, it used to be that you would write `myArray.objectAtIndex(2)` to access the third element of the array `myArray`. As of Xcode 4.4, you can access the third element with the much simpler `myArray[2]`.

Moreover, dictionary access is simpler as well; instead of `value = [myDictionary objectForKey:@"VotingAge"]`, you can now write `value = myDictionary[@"VotingAge"]`

Check out [ iOS 6 by Tutorials (Second edition)](http://www.raywenderlich.com/store/ios-6-by-tutorials) for the details on this and all the other advances in modern Objective-C.

Moreover, Objective-C supports adding subscripts to custom classes, but it requires some effort. In contrast, Swift makes adding subscripts to your own classes easier to implement than ever. Yes, that's right, your life is about to get easier, compliments of Apple.

_Note:_ This Swift tutorial assumes you already know the basics of Swift development. If you are new to Swift, we recommend you check out some of our [other Swift tutorials](http://www.raywenderlich.com/?page_id=2519) first.

## Getting Started

In this Swift tutorial, you're going to explore subscripts by building a basic checkers game in a playground. You'll see how easy moving pieces around is, illustrating the power of subscripting right on your game board.

When you're done, you'll also have a new game to keep your fingers occupied during all of your spare time.

Download the [starter project](http://cdn2.raywenderlich.com/wp-content/uploads/2014/10/StarterSubscriptPlayground.playground.zip). Look over the two types that already present in the playground:

  * `enum PlayerColor`: Represents the color of a piece on the board. Note that a piece with PlayerColor type `.None` represents a _blank space_ on the board.
  * `class GameBoard`: This is the main class you'll work with. It has a 2-dimensional array of PlayerColors that holds the board's data.

GameBoard controls all the gameplay and keeps track of the piece locations, and to make it functional you'll add subscripting to `GameBoard`.

Open the Assistant Editor by going to _View\Assistant Editor\Show Assistant Editor_ to view the console.

Enter the following lines at the bottom of the playground, after the closing brackets of the GameBoard class:
    
    
    let board = GameBoard()
    board.displayBoard()

After initializing the instance `GameBoard` of the GameBoard class, the call to `board.displayBoard()` prints the board to the console.

The board currently looks like this:
    
    
    -r-r-r-r
    r-r-r-r-
    -r-r-r-r
    --------
    --------
    b-b-b-b-
    -b-b-b-b
    b-b-b-b-

The `board` array comprises eight elements, each of which is an array of eight elements. In effect, this makes `board` a two-dimensional array. For example, `board[2][5]` refers to the sixth element of the third subarray -- remember that the first element of an array is at index 0).

Note how the board's subscripts are y-before-x. No, you're not looking through at in in one of those goofy mirrors at a carnival.

Though it seems backwards, it's actually not on this project, because you have to access it in this way because of how `board` is set up.

The following image should help clarify this concept. From the user's perspective, the square at (7,0) is at the top-right corner. However, in the image, the square (7,0) appears in the first array of `board`. The seventh element of this subarray is the piece at square (7,0).

Therefore, to locate the piece at square (7,0), you would need to access `board[0][7]`.

![CheckerboardCoords](http://cdn3.raywenderlich.com/wp-content/uploads/2014/08/CheckerboardCoords-320x320.png)

## Implementing a Simple Moving Method

An effective way to create subscripts is to write the code in functions first, then reuse it when you build the subscripts.

With that in mind, you're going to implement a simple function that moves a piece from one location to another. The coordinates of the locations consist of a tuple of two Int's: `(Int,Int)`.

Add this function to the end of the `GameBoard` class:

This is a very basic implementation for now - you'll add more game logic here later in the tutorial.

First, you store the piece you want to move in a variable. The next line replaces that piece in the `GameBoard` with a blank space. Then, you move the piece where you want it to go.

Try this out. At the bottom of the file, add the following two lines:

Here, you tell your `GameBoard` to move the piece at (2,5), which happens to be a black piece, diagonally to the right.

Look in the console, the board shows that the piece from (2,5) moved to its new position at (3,4):
    
    
    -r-r-r-r
    r-r-r-r-
    -r-r-r-r
    --------
    ---b----
    b---b-b-
    -b-b-b-b
    b-b-b-b-

## Finding Who is Where

Looking at the console, it's pretty easy for _you_ to know what piece occupies a given location, but your program doesn't have the same powers. It can't know which player is at a specified position without directly accessing `GameBoard` properties.

Add the following function at the end of `GameBoard`:

This function simply returns the color of the piece located at the given coordinates.

Often, when a function gets a value from the class, there's also one to set a value. In this case, setting the `PlayerColor` at a location can be very helpful.

If you need to set up the board, allow someone else to take over a piece, or need to remove a jumped piece, you need a method like this. Add the following function at the end of `GameBoard`.

This method replaces the color of the piece at a specific location on the board with a piece of the given color.

## Declaring Subscripts

Subscripts and computed properties have similar declarations. For a little comparison, pretend you're making a computed property, like this:
    
    
    var computedProperty: Type {
      get {
        //return someValue
      }
      set (newValue) {
        //setSomeValue()
      }
    }

Here's how that looks as a subscript:
    
    
    subscript(parameters) -> ReturnType {
      get {
        //return someValue
      }
      set (newValue) {
        //setSomeValue()
      }
    }

In the setter, there is a default parameter `newValue` with a type that equals the subscript's return value type. You use this parameter to change the underlying value within the class. You don't have to declare the `newValue` parameter.

Just like computed properties, subscripts can be _read-only_ or _read-write_.

A read-only subscript doesn't explicitly state get or set; the entire function body is a getter:

![disguise](http://cdn1.raywenderlich.com/wp-content/uploads/2014/08/disguise-177x320.png)

A common approach to subscripting is to have a normal method that works the same as the subscript, allowing it to act as a shortcut to the method.

For example, consider that `NSMutableArray` has `objectAtIndex()` and `replaceObjectAtIndex(withObject:)`. Using subscripts on an `NSMutableArray` instance would call these two methods, depending on the use.

Similarly, custom indexed subscripts on your class in Objective-C serve as shortcuts for calls to `objectAtIndexedSubscript:` and `setObject:atIndexedSubscript:`, both of which you must implement appropriately for your class.

In Swift, Apple seems to have moved away from this paradigm, because using subscripts is the only way to access elements of arrays and dictionaries. However, this paradigm is still useful.

## Creating a Subscript on GameBoard

Remember `playerAtLocation(_:)` and `setPlayer(_:atLocation:)`? A single subscript can replace both of these.

Add this empty subscript declaration into the bottom of `GameBoard`:
    
    
    subscript(coordinates: (Int,Int)) -> PlayerColor {
      get {
     
      }
      set {
     
      }
    }

Ignore the errors for now, they'll disappear when you combine `playerAtLocation()` and `setPlayer(atLocation:)` into a single read-write subscript.

Based on the pattern explained earlier, there is no need to copy the code from before into the subscript. Instead, the subscript calls these methods directly.

Add the following code to the subscript's getter:

At the bottom of the playground, add the following lines to see this subscript in action:

Since there is a black piece at the location (3,4), the console prints _Black_.

Likewise, implement the setter using `setPlayer(atLocation:)` to make your code look like this:

Now go to the bottom of the playground and enter the following lines:

Voila! The black piece located at (3,4) becomes a red piece!
    
    
    -r-r-r-r
    r-r-r-r-
    -r-r-r-r
    --------
    ---r----
    b---b-b-
    -b-b-b-b
    b-b-b-b-

## Adding a Second Subscript

One subscript down, one more to go! This time, you're adding a subscript for `movePieceFrom(_:to:)`. After this, instead of writing this old, verbose line:

You'll be able to write the more succinct:

At the bottom of `GameBoard`, create another read-write subscript like the first one, but with an externally named parameter `move` and a return type of `(Int,Int)` instead of `PlayerColor`.
    
    
    subscript (move coordinates: (Int,Int)) -> (Int,Int) {
      get {
     
      }
      set {
     
      }
    }

Just like methods, subscripts can have externally named parameters.

Add `movePieceFrom(to:)` to the setter for this subscript.

Note the above code uses the default `newValue`, but doesn't declare it.

In contrast, the getter for this subscript is not so straightforward. In fact, you don't want to return a value for this subscript; it's effectively write-only.

Instead of returning a dummy value, you'll employ the useful `assert` function, which throws an error during development to alert the developer that something's wrong, but doesn't throw an error in production code.

Replace the getter with the following:

Now, any attempt to access this subscript throws an exception.

## Gratuitous Gameplay

Right now, when you use the subscript to set the new position of a piece, the piece just goes wherever you say, even if it's an illegal or invalid move. Talk about a power trip.

You'll have a hard time finding anybody to play with you given your supreme impunity to the rules, so you need to add some simple move validations.

Before jumping to the code, think through the ways you can ensure a move is valid.

![thinkingcap](http://cdn1.raywenderlich.com/wp-content/uploads/2014/08/thinkingcap-236x320.png)

  1. _Is the new coordinate in the game board?_ If either of the coordinates are outside the range of 0-7, the move is invalid.
  2. _Is the moving piece either red or black?_ If the piece represents a blank space on the board, there's no sense in moving it.
  3. _Is there a red or black piece at the new location?_ In checkers, you cannot land on another piece.
  4. _Is the piece moving in the right direction?_ red pieces move down the board, while black pieces move up the board.
  5. _Is the new position off by one in both the X-coordinate and the Y-coordinate?_ Pieces move diagonally by one when they don't jump over the opponent's piece.
  6. _Does the piece jump over an opponent?_. If this is the case, then a blank space must replace the jumped piece on the board.

That of course doesn't cover every variable, but you have the basics covered.

To be fully functional, you also need to check for multiple jumps, declare a king, allow the king to move backwards, and check for moves that are not jumps when a jump is possible (The official rules of checkers requires a player to make a jumping move if one is possible.)

You'd also need to check that the player moving is not moving out of turn!

Now that you know what to validate, you need to add these new rules to the program. Instead of making changes directly to the subscript, you'll make the changes in `movePieceFrom(_:to:)`.

Delete the code inside `movePieceFrom(_:to:)`. One by one, you'll add the rules from your list.

After detecting an invalid move, the code prints an error message. Within the function, add this new function that prints the error message:

The first check is to make sure both locations are actually on the board, not in the hinterlands. To do this, check if the coordinates fall within the proper range of 0-7:

The `~=` operator (tilde and equals characters) tests to see if the range on the left contains the value on the right. Here, you make sure that each location's coordinate is in the range of 0-7. If not, you call the error message and `return`.

Next up is a simple check to ensure the color of the moved piece is a not a blank, and in this situation, you'll use subscripting to find the player.

Similar to the previous validation, you check if there is actually a piece (of either color) at the starting position.

Now, add this to the bottom of `movePieceFrom(_:to:)`:

In this case, you _do_ want the new location to be empty. Notice the `!=` compared to the `==` in the previous code.

Onto the next validation step, which is making sure the piece is moving in the right direction. Remember that each color can only go one way -- and that's what this next block does:

`yDifference` finds the difference between the y-coordinates of `to` and `from`.

If the piece being moved is red, then it can only move _down_ the board; when a piece moves down the board, it moves by a positive value. Since a positive value always equals its absolute value, you can use this basic math to determine if the piece is moving in the right direction.

On the other hand, black moves _up_ the board and has a negative y-coordinate. Negative numbers don't equal their absolute value so they're disallowed from moving down the board -- you check this at the end of the ternary operator.

Now for the next validation, and that is determining if the piece is moving diagonally by one. This is the only type of move you can make when you're not moving a king and there isn't a jump to make.

Diagonal movement requires that both the x- and y-coordinate change by an absolute value of 1. The following checks for this condition:

`movePieceFrom(_:to:)` is _almost_ functional at this point, but there is an issue to address.

Since the last segment throws an error whenever a piece moves more than one space, there is no way to check for legal jumps that move a piece by _2_ spaces.

In order to change this, replace the code:

with:
    
    
    if abs(to.0 - from.0) != 1 || abs(to.1 - from.1) != 1 {
      if abs(to.0 - from.0) != 2 || abs(to.1 - from.1) != 2 {
        error("Not a diagonal move")
        return
      }  
      let coordsOfJumpedPiece = ((to.0 + from.0) / 2 as Int, (to.1 + from.1) / 2 as Int)
      let pieceToBeJumped: PlayerColor = self[coordsOfJumpedPiece]
      if contains([.None, playerAtLocation(from)], pieceToBeJumped) {
        error("Illegal jump")
        return
      }
      setPlayer(.None, atLocation: coordsOfJumpedPiece)    
    }

The first if-statement is the same as the original code, but inside there's another similar if-statement that checks to see if the piece moves by 2 instead of by 1. Also, if the piece doesn't move diagonally by 1 or 2, the code prints an error message to the console.

In the instance that the piece moves two spaces in either direction, there needs to be a piece in the middle to jump over, otherwise the move is illegal. The location of this piece must be the midpoint between `from` and `to`, and you calculate that location by averaging the x and y values of both coordinates.

Also, the jumped piece needs to be the opposite color as the piece that is doing the jumping. Once the code confirms that, the jumped piece is set to `.None`.

Nice job, although you'll no longer enjoy supreme command over the board, you now have checks in place that allow for basic play and the piece moves to its new location:

Finally, test out this new functionality by entering these two lines at the bottom of the playground:

This changes the board from
    
    
    -r-r-r-r
    r-r-r-r-
    -r-r-r-r
    --------
    ---r----
    b---b-b-
    -b-b-b-b
    b-b-b-b-
    
    
    -r-r-r-r
    r-r-r-r-
    -r-r-r-r
    --b-----
    --------
    b-----b-
    -b-b-b-b
    b-b-b-b-

The black piece now jumps over the red piece, as you'd expect in a normal game of checkers.

Now test the error checking by trying other moves. Remember that each legal move you make changes the board!

Enter the moves below, one by one, in the order indicated to see the effect:
    
    
    board[move: (1,6)] = (2,5) //legal move
    board.displayBoard()
     
    board[move: (1,6)] = (1,5) //No piece to move since
    board.displayBoard() //you just moved the piece at (1,6)
     
    board[move: (7,2)] = (6,1) //(6,1) is already occupied
    board.displayBoard()
     
    board[move: (7,2)] = (5,4) //Illegal jump - no piece to jump
    board.displayBoard()
     
    board[move: (7,2)] = (8,1) //Range Error
    board.displayBoard()
     
    board[move: (0,7)] = (1,6) //legal move
    board.displayBoard()

## Where To Go From Here?

If you'd like to see the project in its fully functional form, feel free to download the [completed project](http://cdn5.raywenderlich.com/wp-content/uploads/2014/10/FinalSubscriptPlayground.playground1.zip) from this Swift tutorial.

Now that you have added subscripts to your tool kit, look for opportunities in your own code to use them. While they don't add extra functionality, they sure make your code more readable and more intuitive if used properly.

That said, you don't always want to revert to subscripts. One or two subscripts on a class can be helpful, but if the subscript feels unnatural or forced, or if you have more than a few on a single class, then you should start asking yourself if you _really_ need it.

Of course, this is just a bare bones start for a checkers game. You can still improve the game, for one, there's still several basic validations you could add. Then you could implement a "King Me!" mechanism, multiple jumps, or track of which player's turn it is.

If you want to learn more about Swift development, check out our book [Swift by Tutorials](http://www.raywenderlich.com/?page_id=74805).

If you have an questions, comments or other idea for how to use subscripts, please leave your comments below!
