# Test First

_Captured: 2015-10-17 at 21:50 from [blog.8thlight.com](http://blog.8thlight.com/uncle-bob/2013/09/23/Test-first.html)_

I first heard the term "Test First" in 1998. Back then it was part of the phrase "Test First Design". We often shortened it to "Test First". Later, Kent Beck, the originator of the concept, changed the name to Test Driven Development; and it has gone by the acronym TDD ever since. But the words "Test First" have a connotation that the words "Test Driven Development" don't. That connotation is deeper than most people suspect. What does "Test First" really mean?

### Tests are Specs.

To answer that we need to look more deeply at our tests. What are they -- _really_?

Users of the RSpec test framework don't call them tests. They call them specs. Why? Because, in the language of RSpec, the tests read like specifications. For those of you who've never seen an RSpec test, you don't know what you are missing. Here's a simple example:
    
    
    describe Stack do
      context "Upon Creation" do
        let(:stack) {Stack.new}
        it "will be empty" do
          stack.should be_empty
        end
        it "will raise underflow if popped" do
          lambda {stack.pop}.should raise_error(Underflow)
        end
      end
    end
    

Frameworks, like RSpec, that allow you to write tests in a spec-like format are helpful, but not really necessary. We can easily write spec-like tests in JUnit.
    
    
    @Test
    public void empty_stack_will_be_empty() {
      assertTrue(stack.isEmpty());
    }
    
    @Test(expected=Stack.Underflow.class)
    public void empty_stack_will_throw_Underflow_when_popped() {
      stack.pop();
    }
    

Indeed, so long as we keep our tests short, well factored, and well named, they ought to read very nicely. They ought to read like specifications; because they _are_ specifications.

One of the goals of TDD is to be able to trust your test suite to the extent that, if it passes, you know you can ship! If you trust your tests that much, then those tests must describe everything that the system does. And if the tests describe everything; then the tests are specs.

### Rotten Tests

I'm sure you've seen tests that don't look anything like specs. Perhaps they looked like this (you don't really have to read this):
    
    
    public void testJsonResponse() throws Exception {    
      WikiPage page = WikiPageUtil.addPage(root, PathParser.parse("PageOne"));
      PageData data = page.getData();
      data.setContent("some content");
      WikiPageProperties properties = data.getProperties();
      properties.set("Test", "true");
      page.commit(data);
    
      MockRequest request = new MockRequest();
      request.setResource("PageOne");
      request.addInput("format", "json");
    
      Responder responder = new PropertiesResponder();
      SimpleResponse response = (SimpleResponse) responder.makeResponse(context, request);
      assertEquals("text/json", response.getContentType());
      String jsonText = response.getContent();
      JSONObject jsonObject = new JSONObject(jsonText);
      assertTrue(jsonObject.getBoolean("Test"));
      assertTrue(jsonObject.getBoolean("Search"));
      assertTrue(jsonObject.getBoolean("Edit"));
      assertTrue(jsonObject.getBoolean("Properties"));
      assertTrue(jsonObject.getBoolean("Versions"));
      assertTrue(jsonObject.getBoolean("Refactor"));
      assertTrue(jsonObject.getBoolean("WhereUsed"));
      assertTrue(jsonObject.getBoolean("RecentChanges"));
    
      assertFalse(jsonObject.getBoolean("Suite"));
      assertFalse(jsonObject.getBoolean("Prune"));
      assertFalse(jsonObject.getBoolean(PageData.PropertySECURE_READ));
      assertFalse(jsonObject.getBoolean(PageData.PropertySECURE_WRITE));
      assertFalse(jsonObject.getBoolean(PageData.PropertySECURE_TEST));
    }
    

Now that's a mess. I'm sure you can figure it out if you try; but why should you have to try when a little refactoring changes that test to this:
    
    
    public void testJsonResponseForProperties() throws Exception {
      createTestPage();
      SimpleResponse jsonResponse = requestPagePropertiesInJason();
      assertJsonResponseHasDefaultProperties(jsonResponse);
    }
    

Now _that's_ a spec!

It doesn't take much to get tests to read well; just a little refactoring. And yet we often forget to refactor our tests. We treat them as some kind of second-class citizen in our systems. We let them rot because we think our effort is better spent on the production code. We think that time spent cleaning tests is wasted.

But, of course, that's nonsense.

### Tests are part of the system.

We all know that bad code slows us down. So why do we write it? Sometimes we write it because we're in a hurry. We say to ourselves we'll go back and clean it later; but we know that's a lie. We know we won't go back and clean the bad code because we know we'll be afraid of breaking it. So we simply allow it to persist and grow. The more it grows, the more it slows us down. The more it slows us down the more we rush, and the more bad code we write, and the slower we go.

This is the never ending downward spiral that so many systems are trapped in.

The key to breaking this spiral, is to clean the code. The key to cleaning the code is to have a test suite that you trust with your life; because then you won't be afraid to clean the code. You'll clean a bit of it, and that'll make you, and the team, go a little bit faster. With that extra time you'll clean more, and you'll go faster still. This is the upward spiral of cleaning code. That upward spiral is enabled by tests.

What this means is that your ability to quickly clean, maintain, and modify your system depends critically upon having a good test suite. Without that test suite your system rots, and the team slows down to near zero. With that test suite the team can quickly repair and eliminate bad code, and therefore continue to make rapid and regular process. With that test suite, they won't slow down!

The tests enable the team to go fast and the system to stay healthy. Therefore those tests are an integral, and critical, part of the system. As such, they deserve to be maintained to the same level of quality as the production code. Indeed, perhaps the tests deserve even more attention than the production code since the quality of the production code depends on the tests; but the quality of the tests does not depend on the production code.

### Asymmetry

That last statement was asymmetrical. The quality of the production code depends on the tests; but the quality of the tests is _independent_ of the production code. The reason for this is that there is an asymmetry in the way the two execute. The tests are a program that verifies that the system works as specified. But the system is _not_ a program that verifies that the tests execute correctly. You run the tests in order to refactor the system; but you _don't_ run the system in order to refactor the tests. You refactor the tests by _running the tests!_

There's another asymmetry that's even more interesting. You can (and do) create the system from the tests, _but you can't create the tests from the system_.

Consider a comprehensive suite of tests that fully describes a system. Those tests are individual units that don't depend upon each other. Each one is a statement of behavior that is independent of the other behaviors in the system, and of the other tests in the system. If I gave you such a comprehensive suite of tests you could make those tests pass, one test at a time. When you were done, you'd've written the whole system. The tests specify the system.

However, if I give you a system without tests, it's virtually impossible to create the test suite that fully specifies that system. The production code is a set of interdependent components that have complex and emergent behaviors. Trying to understand and specify all the implications of those interdependencies, and those behaviors, is very difficult indeed.

So TDD is a trap-door function. It's easy to go from tests to production code, but hard to go the other direction. And that implies something fascinating about the tests: _The tests are the most important component in the system._ They are more important than the production code.

### The Choice

I know this sounds ridiculous; but consider. If somehow all your production code got deleted, but you had a backup of your tests, then you'd be able to recreate the production system with a little work. Indeed, you'd also enjoy the benefit of _The Second System Effect_. The code would be better because it was the second time you'd've written it. So, in the end, you'd wind up with a fully functional and better designed system.

If, however, it was your tests that got deleted, then you'd have no tests to keep the production code clean. The production code would inevitably rot, slowing you down. The quality of the code, and the productivity of the team would be caught in the downward spiral towards zero -- and there's nothing they could do to stop it other than trying recreate the test suite. And, as we noted, recreating the test suite is very hard indeed.

If we lose the production code, we end up with a better designed system that stays clean because it has tests. If we lose the tests, then the production code rots and the team slows down in a never ending spiral of lost productivity.

So we can conclude that if it became a choice between the tests or the production code, we'd rather preserve the tests. And this means that the tests are a more important component of the system than the production code is. Because the tests are the specs.

### Simple Design

Years ago Ron Jeffries codified Kent Beck's rules of simple design. They are, in order of priority:

  1. All the tests pass.
  2. There is no duplication
  3. The code expresses the intent of the programmer.
  4. Classes, and methods are minimized.

Over the years we have used this as a guide for writing our code. Indeed, Kent would often say:

> First make it work, then make it right, then make it small and fast.

Given these guidelines we'd write a failing test and then focus on getting that test to pass. Then we'd refactor to remove duplication and clean up the code. Indeed, we felt the license to make a mess in the production code as we strove to get it to work. Then we'd immediately clean that mess once the tests passed.

I've used Ron's rules for a long time, and I've grown to trust them. In the production code it is always better to first make it work, and then clean it up. However, I think this order is dead wrong for the tests.

### Tests are first in all things.

We have no need to write messy tests. Indeed, tests can be written cleanly at first. To prove this to yourself, simply say the three magic words: _Given_, _When_, and _Then_. Before you write a test, you should be able to describe the test you are about to write using those three words.
    
    
    Given that I have an empty stack
    When I push something on it.
    Then it will have a size of 1.
    

And once you've got those three words, you can turn them into three statements. It might be as simple as this:
    
    
    Stack stack = makeEmptyStack();
    stack.push(0);
    assertThat(stack.size(), equalTo(1));
    

Or consider that test we refactored earlier:
    
    
    createTestPage();
    SimpleResponse jsonResponse = requestPagePropertiesInJason();
    assertJsonResponseHasDefaultProperties(jsonResponse);
    

It turns out that you can _always_ reduce a test down to three statements. _No test ever needs to have more than three lines!_ What's more, you know what those three lines are before you begin writing the test!

Oh, that doesn't mean that some tests don't have complicated setups and assertions; many do. It just means that all that complexity can be extracted from the test into utility functions, leaving behind the three critical statements: Given, When, and Then. And we can do this extraction before we get the production code to work.

So, when we are writing tests, we can invert Kent's advice.

> First make the test right. Then make the test work.

We can change Ron's rules for Simple Design, into rules for Simple Tests:

  1. The test expresses the intent of the programmer
  2. The test passes.
  3. The test has no duplication.
  4. The test has a minimum of classes and methods.

In the TDD cycle, this means that we first write a portion of a test; and before we make it pass, we clean it up to ensure that it says what we mean it to say. We get that tiny portion of the test to express our intent; and _then_ we make it pass.

The red-green-refactor cycle becomes Red -> Clean Test -> Green -> Refactor.

### Being First.

The bottom line of all this is that we should consider our tests as _being_ first. We already know we should write them first; but we should also clean them first, maintain them first, think of them first, and keep them first. We should give our tests the highest priority.

_That_ is what "Test First" really means. The Tests Come First!

Robert Martin (Uncle Bob) is a Master Craftsman. He's an award-winning author, renowned speaker, and has been an uber software geek since 1970.

[Follow @"unclebobmartin"](https://twitter.com/unclebobmartin)

#### More Posts by This Author
