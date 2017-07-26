# A Beginners Guide to DSL Writing in Ruby

_Captured: 2017-04-23 at 23:32 from [dzone.com](https://dzone.com/articles/a-beginners-guide-to-dsl-writing-in-ruby?oid=twitter&utm_content=buffer30437&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190137&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190137&u=https%3A%2F%2Fwww.wakanda.io%2F).

Writing the Grammar and Parser in Ruby first has the advantage of interactivity. Ruby is interpreted and has a very quick startup time.

To get going I'll start writing a JSON parser. This may sound strange as there are already JSON parsers out there, but I'm not trying to replace them, but rather show the concepts along that line rather simple grammar.

At the end, I will also give you a peek at the grammar for a more complex DSL for alert trigger creation.

To get an overview of the grammar, have a look at [JSON.org](http://json.org/index.html).

## The Ruby Parser

For Ruby, I have chosen a _treetop_ parser, which is a [Parsing Expression Grammar](https://en.wikipedia.org/wiki/Parsing_expression_grammar) (PEG).

Grammars in it look like this:

Basic setup of a grammar file.

**1**
The name of the grammar determines the name of the parser. See below.

**2**
The first rule is the starting point of the grammar.

For our Json parser the top of the file `json-simple.treetop` would look like this:

**1**
Top most rule, parsing starts here.

**2**
Content of the rule used for matching.

A JSON object would thus be either an `array` or an `object`. As both are not terminal symbols in a simple character or string (like `'this'`), more rules are needed to resolve this. We will look at them below.

Before we continue with the grammar, let's have a look at how to compile the grammar and use it.

### Compiling the Grammar

Treetop brings a command line tool called `tt`, which will compile the grammar into Ruby code.

Compiling the grammar using `tt.`
    
    
    $ tt json-simple.treetop (1)

**1**
The input grammar file.

This worked well, but calling `tt `during a development cycle is a bit too heavy. Luckily, there is a way to compile grammar files on the fly when you first use them.

Here, you see how a parser driver can load the definition and instantiate the parser.

`json_parser.rb`

The key part is the following two lines:
    
    
      Treetop.load(File.join(base_path, 'json-simple.treetop'))  (1)

**1**
We are loading the `.treetop` grammar file.

**2**
The name of the parser is determined from the `grammar`

The name of our parser is determined from the `grammar` instruction by appending `Parser` to the grammar name given there.

Let's try our grammar.

Testing the Grammar with `irb`
    
    
    2.3.0 :001 > require_relative 'json_parser' (1)
    
    
    2.3.0 :002 > JsonParser.parse '{}' (2)

You see that the parsing fails with an exception about an unknown method `_nt_array`. If you look at the grammar above you can see that we have said that a JSON object is either an `array` or an `object` but did not define them anywhere.

While the compiler is not telling us where in our source file it thinks the error is, the message above (which could be less cryptic) tells us that `_nt_array` is missing from `_nt_json` or in other words the rule `json` uses a non-terminal ( `_nt` ) named `array`, which is not defined.

TIP
As the grammar is evaluated left to right, it also means that the error reporting is left to right.

In the above case, the missing `object` declaration is not reported, as the missing `array` already made the compiler fail.

###   
Continuing With the Grammar

So let's continue with the grammar.

The definition of an `array.`
    
    
        '[' space a_value? (space ',' space a_value)* space ']'

In this example, you find two new things: _terminals_ enclosed in single quotes, like the opening and  
closing brackets, `'['` and `']'`. The parser expects such a symbol or keyword literally at this place. So for the above, an `array` needs to start with a `[` character and end with `]` to be recognized.

The other new concept you see here are the quantifiers, that you probably already know from  
regular expressions:

  * `?` The item may show up zero or one time(s).
  * `+` The item must show up at least one time (not shown above).
  * `*` The item may be given any number of times (including zero).

And last, but not least, items can be grouped together with parentheses: `(` and `).`

So the array has to start with `[` has a `space` rule, zero or one `value` and then zero or many times a block, which consists of a space, a literal colon, a space, and a value.

Now let's look at the `a_value`.

The definition of `a_value.`
    
    
        object / array / string / number / true / false / null

Here you see the slash, `/`, which means _or_. A `value` can thus be an object, an array, a string, a number, or one of true, false, and null. As treetop is a PEG parser generator, it will evaluate the list from left to right.

Sometimes you want to have a rule match different options like the above, but where only a part of the matching expression is a choice. In this case, you can put a sub-expression in parentheses:

Grouping of sub-expressions.

The last excerpt from the grammar is the `space.`

The definition of a `space.`

Here you see that the `space` consists of zero or more spaces, newlines, or tab characters.

TIP
The full grammar up to this point is available in the file `json-simple.treetop`.

## Generating Values From the Input

Up to this point, we have a grammar that can parse JSON input, but for the parser to be useful we actually want to transform the input into an object that contains nested lists and objects.

You may have seen above that the parser returns the _abstract syntax tree_ (AST) it has generated:

We could now walk the tree and determine the values from the walk. But there is a better way to do this in the treetop.

Individual grammar nodes can provide methods that can be called during the parsing run. There are several options to do this - I will show two.

### Inline in the Grammar

In this case, the function is directly inside the `.treetop` file. This is nice for a very simple function but otherwise is probably more confusing than helpful. Also, even if it is Ruby code, your IDE is most likely not helping you.
    
    
            elements[1].text_value (4)

**1**
The usual matching.

**2**
The inline function definition is delimited by `{` and `}`

**3**
The name of the function can be anything with and without parameters.

**4**
Evaluation of the current node, see below.

Even if the name and signature of the function is arbitrary, it needs to be known to a  
potential calling node.

### Via Mixin

Here we externalize the functions into a `Module` and only provide a pointer to it inside the  
grammar.

**1**
The match definition gets the name of the Module passed in angle brackets.

We then have a Ruby file that contains the definition:

`parser_extensions.rb`

You see that this is the same as inside the grammar, but you get all the help from the IDE. It is now needed though to `require` that additional file from our parser driver we need `json_parser.rb`

`json_parser.rb`

## Evaluation From the Parser Driver

Now that we have the functions defined, we can start evaluating the input. This is simply done by calling a function on the generated AST:

`json_parser.rb`

As we are calling the function `value` we also need to make sure that the topmost grammar node has it defined. Otherwise, an error like this is raised:

In our case this is not needed, as our `json` rule only diverts to `array` or `object` and thus does not add any value (pun intended).

Internally the parsed result is out into a Ruby-array called `elements`. Data starts at index 0.

This is a bit tricky sometimes and I have added the element positions below the matches.

To obtain the key (a `string`) you can thus use `elements[0]` and `elements[4]` for the value. Our `value` function for `kv_pair` could thus look like this:
    
    
        parent[elements[0].value.to_sym] = elements[4].value

This works quite nicely and if you compile the grammar with `tt` as seen above, you can see that the compiled parser uses the same elements to provide some aliases:

Generated code in the parser.

It is thus possible to use the aliases in the above code for it to look like this:

The parser gets a lot less brittle this way. If your rule now prepends a matching character literal,  
the aliases stay the same while the indexes into the elements would have changed.

Now suppose you need another `string` in your input. Treetop would then name them `string1` and `string2`. A more elegant solution here is to "tag" those input rules with the desired alias as in the below code:

Now, you can access the key string as `key`:

`parser_extensions.rb`

Still, the value part of the key-value-pair uses the un-aliased `a_node`. If you ever decide to  
rename this, you also need to rename the Ruby code.

Treetop v1.6.8 seems to only provide the aliases for non-terminal symbols that are required. For cases where you have optional symbols, you still need to fall back to tags.

##   
Handling of Bad Input

Now sometimes parsing an input fails because the input does not match the defined grammar. The parser does not return an AST in this case, which we can test for and return some debugging  
information to the user:

`json_parser.rb`

Let's see how this looks in `irb` .

Parser error as seen in `irb`

While working in your own code, you can change the error handling to your liking.

## Traps

In this section, I want to point out a few traps that one can easily fall into.

### Too Much Space

Suppose you have the following grammar:

Parsing or filling of the `elements` array may fail in unexpected ways. The parser is unable to  
determine to which element the various space characters should be matched. This becomes a bit more obvious when we 'insert' the `kv_pair ` declaration into the `object` one:

At positions 1, 2 and 8, 9, each time the parser is asked to (greedily) consume white space. One could argue that positions 1 and 8 do this and 2 and 9 could be no-ops, but apparently, this is not the case.

A solution can be to remove the surrounding `space` in the `kv_pair`:

### Adjacent Things That Should Not Be

Take this grammar snippet:

Treetop will fail to compile the grammar, as there is no whitespace between `a_value?` and `']'`, so the expression makes no sense.

### Forgotten Grouping

In the next snippet, we have two `aBool` that can be tied together via `'and'` or `'or'`.

Treetop will, in this case, try to match `aBool 'and'` or `'or' aBool`, which, most of the time, is not what we intended. To fix this we need to put the alternatives into a group.

### Naming Things

Treetop will internally provide aliases for matches as we have seen before. Take this example:

It will create an alias 'value.' Now when you define a function `value` on it, you will get  
a silent clash.

The best thing to do here is to name your functions in a way that you would never name the rules or grammar elements.

## Looking at a DSL for Alert Trigger Creation

The [Hawkular](http://hawkular.org/) project also has an alerting component that can be used to inform the user when conditions are met. Those could be when certain values are larger than a threshold, when a string is matching or when the availability of a resource goes down. The definition of the alert _trigger _with its conditions etc. is done via a REST-API.

With [HawkFX](http://github.com/pilhuhn/hawkfx), a pet project of mine, I have created an explorer for Hawkular. And in this regard, I have also started to add a DSL for trigger definition. I have [blogged about it](http://www.hawkular.org/blog/2016/10/24/hawkfx-alerts.html) as well.

I will not show the full code here, but just give some excerpts to give you some ideas on how a more complex grammar would look. The full code is available in the HawkFX repo on GitHub.

### Some Examples

Trigger for availability, with high severity that is initially disabled:

**1**
We define a new trigger with the name _MyTrigger._

**2**
It is disabled by at creation time.

**3**
When it fires an alert, then the alert severity is High.

**4**
It fires when the availability of _mymetric_ is Down.

Trigger that fires when two conditions are true:

**1**
The trigger only fires if all conditions are true.

**2**
The condition is true if the counter-metric 'mycount' is less than 5.

**3**
This condition is true if the string-metric 'mymetric' contains the string 'ERROR.'

Trigger that disables itself after firing:

**1**
When this keyword is present, the Trigger will auto-disable after firing.

###   
The Grammar

Now that we have seen some examples, we can look at the grammar rules.

Start a rule to define a trigger:
    
    
         'define trigger ' space? name:string space? (1)
    
    
         id:id? space? conditions space? act:action? (2)

**1**
'define trigger' needs to be written as is.

**2**
We need conditions. Pretty much everything else is optional.

**3**
Evaluation happens in the `DefineNode` module.

The rule for disabled is pretty simple and just checks if the keyword 'disabled' is present.

The rule for disabled:

Inside the Ruby code, it is queried on the `value` method for the `DefineNode` module:

**2**
We check if `disabled` is set.

Remember from above code that `disabled` is available as a variable for us to use because we set it in the `define` rule via `disabled:disabled?`.

Rules for conditions:

Conditions can be either a single definition, or conditions joined by 'AND' or 'OR.' Next is the rule  
for the 'AND' case:

Rules for conjunctions:

Here you see a trick that is often used: we parse the first condition in `first:condition` and then define the remaining conditions as a list of any number of conditions in the `more` part.

In code this looks as follows.

The AndConditionNode evaluation in Ruby:

I am at the end of the example. Again, the full code is available in the HawkFX repository on GitHub.

## References

Treetop home page <http://treetop.rubyforge.org/index.html>

A treetop introduction tutorial <http://www.trsolutions.biz/blog/2010/03/10/treetop-introductory-tutorial-1-of-10/>

Parsing time ranges in Treetop [https://github.com/jcinnaond/treetop-time-range](https://github.com/jcinnamond/treetop-time-range)

JSON.org <http://json.org/index.html>

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190138&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190138&u=https%3A%2F%2Fwww.wakanda.io%2F).
