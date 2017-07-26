# Apprentice Blog of the Week: Useful Clojure Macros For The Object Oriented Programmer

_Captured: 2015-10-17 at 22:16 from [blog.8thlight.com](http://blog.8thlight.com/alex-hill/2014/07/10/useful-clojure-macros-for-the-object-oriented-programmer.html)_

One of the most difficult aspects of learning Clojure for most programmers who have been brought up in the object oriented tradition is the Lisp syntax. Over time many of us grow to love it, but it's usually rough and slow going at first. This post outlines several macros that you can use that will make your code look more familiar, and make you feel at home in Clojure Land. I will also go over how you can start using these macros, and eventually refactor them into a more terse, idiomatic, and functional style.

By far the most useful macro for me is the `loop` macro. This macro allows you to pretend as if you had some collection of objects that you'd like to iterate over and mutate, despite the fact that Clojure's data structures are immutable. Here's a simple example of using `loop` to increment each number in a collection by one:
    
    
     1 (def vals [1 2 3])
     2 
     3 (loop [output []
     4        input-left vals]
     5   (if (= 0 (count input-left))
     6     output
     7     (recur (conj output (inc (first input-left)))
     8            (rest input-left))))
     9 
    10 ; [2 3 4]

Here's how it works: you pass a vector of local variables to `loop` to modify recursively. In this case, and in most others, your two variables will represent input and output. We've set output to an empty list. We've named our list of values "input-left" because it represents the remaining input. You might think it's strange to call it input-left instead of input, but this makes it clear that we're modifying and removing one element of the input list each time we recur.

All recursive algorithms need a point at which to stop looping. This is called the base case. Our base case is very simple. We just keep looping until we've modified all of the input values. The call to recur is probably the least familiar part of this to the eyes of an OO programmer. By calling recur, we're basically instructing our code to return to the top of the loop with the modified values. The arguments to recur represent each local variable we defined in the loop--you must supply the correct number of arguments, and they must be in the correct order. As you can see, we increment the value we're currently iterating over by one, add it to the end of the output list, and recur with our new output and the rest of the remaining input.

However, you'll quickly learn that `loop` is not always the best way to express your thoughts in Clojure. When iterating over a collection, I usually start with a `loop/recur` and later refactor it into something simpler by using functions like `map` or `reduce`. In this case, achieving the same result functionally is extremely trivial:
    
    
    1 (map inc vals)
    2 
    3 ; [2 3 4]

`map` is at the heart of the Clojure language. Its first argument is a function, and its second argument is a sequence. It applies that function to each element in the sequence and returns a new sequence. In functional programming, functions are first-class citizens, which means they can be passed around as arguments to other functions. This is a huge advantage Clojure has over traditional object-oriented languages.

The solution with `map` is clearly better, given how concise it is. You might be wondering why anyone would ever use `loop/recur`. While `map` is much more concise and readable in this case, in more complicated situations, the more verbose `loop/recur` style may make complex operations more clear to others. It is also useful for fleshing out a complex algorithm that you intend to refactor later.

Another option that will be familiar to those coming from languages like Java is the `for` macro:
    
    
    1 (for [x vals]
    2   (inc x))
    3 
    4 ; 2 3 4

`for` also allows you to pass options to it. You can use `:while` to tell it when to stop iterating, or `:when` to filter out certain inputs:
    
    
     1 (for [x vals
     2       :when (even? x)]
     3   (inc x))
     4 
     5 ; (3)
     6 
     7 (for [x vals
     8       :while (not= x 2)]
     9   (inc x))
    10 
    11 ; (2)

I tend not to use `for` as often as `loop`, but that is most likely due to my first programming language being Ruby, a language where the use of `for` is frowned upon.

The last two macros I'd like to go over are Clojure's threading macros. Unlike `loop` and `for`, it's more likely that you'll refactor toward these macros instead of away from them. They make your code easier to read and feel more like object-oriented code. Let's start out by looking at a purely functional representation of an algorithm that gets the names of all the files within a specified directory:
    
    
    1 ; directory structure
    2 ; public/
    3 ;   file1.txt
    4 ;   file2.txt
    5 
    6 (drop 1 (map #(.getName %) (file-seq (as-file "public/"))))
    7 
    8 ; (file1.txt file2.txt)

Trying to understand what's going here can be frustrating. In what order are the steps of this algorithm happening? What values are being supplied as arguments to each function? That's where the (-») or `thread-last` macro comes in handy:
    
    
    1 (->> (file-seq (as-file "public/"))
    2      (map #(.getName %))
    3      (drop 1)
    4 
    5 ; (test1.txt test2.txt)

Now things are much more clear. First we're going to generate a sequence of the files inside of the public directory, including the directory itself. Next we're going to map over those files and get their name. Finally, we're going to drop the first filename, because we're not concerned with the name of the public directory that we already specified. The way this works is actually pretty simple: the `thread-last` macro evaluates each form, then inserts that form as the last element in the next form.

There is also a `thread-first` macro, which works much the same way as `thread-last`, except that it places each evaluated form second in the next form. A good example for how it's used is splitting an HTTP range header:
    
    
    1 (def request {:path "/" :method "GET" :headers {"Range" "bytes=1-100"}})
    2 
    3 (-> ((request :headers) "Range")
    4     (split #"=")
    5     second)
    6 
    7 ; 1-100

These algorithms were only three steps each. As your algorithms become more complex, Lisp-like threading becomes harder and harder to read. The other programmers on your team will thank you for getting comfortable with threading macros sooner rather than later.

`loop`, `for`, and the threading macros make Clojure much more approachable than it would be otherwise. Don't let your unfamiliarity with Lisp or functional programming scare you away from such a truly beautiful and practical language.

#### More Posts by This Author
