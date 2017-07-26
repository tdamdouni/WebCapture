# Language Design: Declarations

_Captured: 2015-09-14 at 09:28 from [owensd.io](http://owensd.io/2015/09/12/language-design-declarations.html)_

_In case you haven't caught on, the "Language Design" posts are basically me rambling about ideas during the development of the Proteus langauge._

I'm implementing the first part of the parser that actually handles declarations… The question my mind is using a simplified syntax or introducing keywords. I'm going to put this out here first so everyone can all gasp at once: I don't like the idea of `const`; I'm not even sure the concept will be in the language.

So let's look at some declarations:

    
    // With a keyword (option 1)
    var foo: i32 = 12    // declare and assign; type is explicit
    var foo = 12         // declare and assign; type is inferred
    var foo: i32         // declare; type is explicit
    
    // No keyword used (option 2)
    foo : i32 = 12    // declare and assign; type is explicit
    foo := 12         // declare and assign; type is inferred
    foo : i32         // declare; type is explicit
    foo :: i32        // declare; type is explicit (two :: for clarity)
    

#### Option 1: Using a Keyword

At first look, I'm not really sure what that keyword is worth it. For one, I'm not sure if I'm going to be having a corresponding thing like `let`. For another, it's just more typing. Is there a true benefit for it?

#### Option 2: No Keyword

There is something nice about this approach; it's clean, fewer characters, and still plays nice with type inference. Ok, so this is a clear winner, yeah? Well, I'm not so sure.

#### Defining Other Types

Ok, so what about other types, like functions, structs, and enums? Now it starts to get a bit more interesting.

    
    // With a keyword (option 1)
    func foo(i32, i32) -> i32 = (x, y) { return x + y }      // declare and assign; type is explicit
    var foo = func (x: i32, y: i32) -> i32 { return x + y }  // declare and assign; type is inferred
    var foo: func (i32, i32) -> i32                          // declare; type is explicit
    
    var foo = (x: i32, y: i32) -> i32 { return x + y }       // declare and assign; type is inferred
    var foo: (i32, i32) -> i32                               // declare; type is explicit
    
    // No keyword used (option 2)
    foo : (i32, i32) -> i32 = (x, y) { return x + y }      // declare and assign; type is explicit
    foo := (x: i32, y: i32) -> i32 { return x + y }        // declare and assign; type is inferred
    foo : (i32, i32) -> i32                                // declare; type is explicit
    foo :: (i32, i32) -> i32                               // declare; type is explicit (two :: for clarity)
    

With functions, it looks like option 2 is coming out ahead. I really like that there is explicit consistency throughout. With the keyword version, it starts to get really cumbersome. In order to fix that, special cases need to be introduced to start dropping some of the verbosity.

Also, the `var` keyword in option 1 is pretty problematic. Can `foo` really be assigned to something else? Now it seems that a `let` keyword **has** to be introduced just to support functions. Though, option 2 has this problem as well to some extent. However, the `foo` that are just declarations could be treated as a typealias instead, a and a variable that points to a function would be declared as: `foo :: *(i32, i32) -> i32`.

Again, option 2 is looking like it's pulling ahead to the cleanest choice.

    
    // With a keyword (option 1)
    struct Foo {
    	f: i32
    }
    
    // No keyword used (option 2)
    Foo :: {
    	f: i32
    	defaultValue := 32
    }
    

Ok, option 2 seems a bit strange in this scenario, but that could just be my eyes are so used to the first style.

    
    // With a keyword (option 1)
    enum Foo {
    	ChooseMe
    	SpecificValue
    }
    
    // No keyword used (option 2)
    Foo :: {
    	SomeValue
    	SpecificValue	:= 32
    }
    

Ok… that option 2 doesn't work; it's ambiguous now. Hmm… something has to change here, and while some syntatic sugar could be added, like using `|` to separate the cases, this is starting to look like a general problem of making declarations less ambiguous at a quick glance.

    
    Foo :: enum {
    	SomeValue
    	SpecificValue	:= 32
    }
    

If an approach like that is taken, then why is a function treated differently? Right, it should be `foo :: func (x: i32) -> i32`. If a keyword is going to need to be used, well, then it seems like the keyword-first approach is both the easier construct to use and easier to extend.

#### Conclusion

So where does this leave me? Well… I think I'm actually going to take the hybrid approach for now and treat variable declarations fundamentally different than type declarations. We'll see how that goes for now.

Here is a short summary of the basic decision:

    
    foo := 12
    
    func add(x: i32, y: i32) -> i32 { return x + y }
    
    // This code, for now at least, will be invalid.
    foo := (x: i32, y: i32) -> i32 { return x + y }
    
    // Instead, this would need to be used.
    foo := &add
    
    struct BigFoo {
    	littleFoo: i32
    }
    
    enum ChooseFoo {
    	DefaultChoice
    	MyChoice := 5
    }
    

As always, feel free to leave any comments in the [Proteus Discussion Group](https://groups.io/org/groupsio/proteus/threads).

_Sidebar_: Yeah, sure, technically the `let` says that the value it holds is constant, and yes, it's technically true that only requires that the pointer address cannot be changed. However, this is what I mean by "semantically incorrect". How do you say that not only is the pointer immutable, but the value that I point to is also immutable? This starts to add a bunch of complexity that I don't want to deal with at the moment.
