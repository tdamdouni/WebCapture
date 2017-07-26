# Enums with Associated Data vs. Structs

_Captured: 2015-09-14 at 09:16 from [owensd.io](http://owensd.io/2015/09/13/enums-with-associated-data-vs-structs.html)_

Maybe everyone can help me out here: I'm trying to find out what the value of enums with associated values is over structs that conform to a protocol.

Here's the context: I'm playing around with the parser code and I'm using an `enum` to describe what statements might look like in Proteus.

Let's say it looks like this:

    
    enum Statement {
    	case Import(keyword: Token, packageName: Token)
    	case Assignment(binding: Token, value: Expression)
    }
    

Ok, so here's the issue. When I'm writing the parser, I want to have a function `parseImport()` to handle the actual parsing of the `import` construct. However, Swift doesn't allow me to define the function definition that I actually want:

    
    func parseImport() throws -> Statement.Import { ... }
    

The thing is, I don't want `parseImport` to return any of the possible values for `Statement`; I only want the function to be able to return the specific case of `Import`. Furthermore, the data stored within each of the associated values isn't related.

So the question is, when is an associated value enum a better choice than structs? You see, I could define the above this way too:

    
    protocol Statement {}
    
    struct Import : Statement {
    	let keyword: Token
    	let packageName: Token
    }
    
    struct Assignment : Statement {
    	let binding: Token
    	let value: Expression
    }
    
    func parseImport() throws -> Import { ... }
    

The only clear win I see is that the `enum` version is more terse. At the end of the day, the usage code is pretty similar in the fact that each needs to determine what specific type of `Statement` is being dealt with, except I can remove the `switch` necessary to unpack the `Statement.Import` version.

There has to be some benefit right? Right now, I'm only see a downside, especially given the fact that I cannot model the desire to have a function return only a specific type of enum value.

**UPDATE Sunday, September 13th, 2015 @ 11:49 PM PDT**

I should have been a little less cavalier about the "some benefit". I understand that enums limit the potential values while protocols and structs allow this to be unbound. That's not really the problem though. The problem is about the coupling of the parts that make up the associated value of the enum with the notion of the actual type itself.

One suggestion to my dilemma was to essentially do the following:

    
    typealias ImportStatement = (keyword: Token, packageName: Token)
    typealias AssignmentStatement = (binding: Token, value: Expression)
    
    enum Statement {
        case Import(ImportStatement)
        case Assignment(AssignmentStatement)
    }
    

This allows the `parseImport` to return an `ImportStatement` instead. Of course, I then need to turn that into a `Statement` in my calling code. That kinda works; though it's much more tedious to actually do that, and it puts the construction of the actual type in the wrong location. Another problem with that approach is the assumption that I own the code. What if I was using a library that provided the enum, such as the one in Apple's Swift documentation:

    
    enum Barcode {
        case UPCA(Int, Int, Int, Int)
        case QRCode(String)
    }
    

Let's say I'm writing a parser for that and I want to write the `parseUPCA` function. What is the return type? Do I provide the loosely-typed version of `parseUPCA() -> (Int, Int, Int, Int)` and then have to pust the creation of the `Barcode.UPCA` instance at the caller (and if the `UPCA` data changes, it's more than a usage code update, I need to update all places that used the parts too, which is a potentially much more difficult search-and-replace fix)? Or return a `Barcode` and hope that I only ever get the `UPCA` version out of it?

I guess I just don't find any of the options available to us particularly good. In my code, `Barcode.UPCA` is all together a different type than `Barcode.QRCode`; I'd simply like to be able to actually model that.

So I need to ask myself: allow for the proper modelling of the type signatures or allow for the proper modelling of the closed nature of the types; I don't know how to do both in Swift today.
