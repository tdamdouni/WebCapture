# Fixing Bugs Driven By Tests in Swift

_Captured: 2015-10-30 at 10:58 from [www.mokacoding.com](http://www.mokacoding.com/blog/fixing-bugs-driven-by-tests-in-swift/)_

In the past months there have been a number of articles here on [mokacoding](http://mokacoding.com) regarding testing, like "[Enhancing XCTest test cases with Nimble matchers"](http://www.mokacoding.com/blog/xctest-nimble/), "[Xcode 7 UI testing, a first look"](http://www.mokacoding.com/blog/xcode-7-ui-testing/), and "[Better tests with Specta"](http://www.mokacoding.com/blog/better-tests-with-specta/).

It is clear that I'm a big TDD fan boy, and if we meet in person I'll probably try to _convert_ you. In this post though I will introduce another use for unit and acceptance tests that you might not have considered yet. Unit and acceptance tests can be used as a tool to fix bug.

![Fixing bugs guided by test is productive and fun](https://s3.amazonaws.com/mokacoding/2015-10-29-bug.jpg)

> _A bug is only a test that hasn't been written yet. - Unknown_

It can sometimes be difficult to find a place where to start writing tests when developing new code, but it certainly isn't when there a bug. You already know what is wrong. Speaking in [red, green, refactor](http://www.jamesshore.com/Blog/Red-Green-Refactor.html) you already have a red scenario to be made green.

Let's take [Simple Notes](https://github.com/mokacoding/SimpleNotes) a demo app build for the occasion. In its mvp form Simple Notes is a read only notes app, you can see a list of notes, and tap on one to see its details. The product owner is clearly a bit crazy.

![Simple Notes Screenshot](https://s3.amazonaws.com/mokacoding/2015-10-29-simple-notes.png)

> _Simple Notes Screenshot_

Simple Notes has two known bugs, see [this commit](https://github.com/mokacoding/SimpleNotes/commit/92b55d744751afc013bf2b0002a74c25e1c5f855), let's see how we can fix them in a TDD way.

## Fix a bug with an unit test

There is an issue in Simple Notes' main screen, the notes are not in any particular order, while the spec says that they should be ordered by updated date, with the most recent first.

Let's write a unit test that we'll have to make green in order to fix this bug. But how?

Well first of all we need to find the code responsible for providing the data to the note table view. Turns out that there is a `NotesListDataSource` object that `NotesListViewController` uses in its implementation of the `UITableViewDataSource` methods.

There are many ways to write the test for this bug, here's one:
    
    
    class NotesDataSourceTest: XCTestCase {
    
      // it sorts the notes by updated date
      func testSortsNotesByUpdatesDate() {
        let firstNote = Note(name: "any name", content: "any content", lastUpdated: NSDate().dateByAddingTimeInterval(60))
        let secondNote = Note(name: "any other name", content: "any content", lastUpdated: NSDate())
        let thirdNote = Note(name: "yet another name", content: "any content", lastUpdated: NSDate().dateByAddingTimeInterval(-60))
    
        let sut = NotesDataSource(notes: [thirdNote, firstNote, secondNote])
    
        assert(sut.noteAtIndexPath(NSIndexPath(forRow: 0, inSection: 0)), isEqualTo: firstNote)
        assert(sut.noteAtIndexPath(NSIndexPath(forRow: 1, inSection: 0)), isEqualTo: secondNote)
        assert(sut.noteAtIndexPath(NSIndexPath(forRow: 2, inSection: 0)), isEqualTo: thirdNote)
      }
    
      private func assert(note: Note, isEqualTo otherNote: Note) {
        XCTAssertEqual(note.name, otherNote.name)
      }
    }
    

Now if you run the tests, or got to [this commit](https://github.com/mokacoding/SimpleNotes/commit/a7431b2bd7363a96a54d0609c133c6b8e069b2f7), you'll see that they fail.

Making the test pass, and therefore fixing the bug is as easy as [adding a `sort` step when initializing the data source](https://github.com/mokacoding/SimpleNotes/commit/048fe2db5b6f37f1875dd21ea1c8592a89d33f94).

## Fix a bug with an acceptance test

If you run Simple Notes you'll notice that nothing happens when selecting a note. That is outrageous! The expected behaviour is for the app to transition to a screen showing the details of the note.

This kind of bug is related to the navigation of the application rather that its logic, and we can easily write an acceptance test. For example:
    
    
    func testShowsNotesDetails() {
      // From the notes list screen
      let app = XCUIApplication()
    
      XCTAssertTrue(app.anyViewWithIdentifier("notes_list_screen").exists)
    
      // When tapping on a note
      app.cells.elementBoundByIndex(1).tap()
    
      // It goes to the note details screen
      XCTAssertFalse(app.anyViewWithIdentifier("notes_list_screen").exists)
      XCTAssertTrue(app.anyViewWithIdentifier("note_screen").exists)
    
      // Go back
      app.backButton().tap()
    }
    

Note that because the app is currently broken I had to write that test manually, rather then recording it. But that's ok, after playing around with the UI testing APIs you will get familiar with them and writing acceptance test will be a smooth experience.

Also note that the approach used in that test is to assert the presence of an accessibility element with a certain identifier. That is a simple trick I use that decouples tests for the user navigation in the app from the content on UI itself. In fact, the accessibility identifier is set on the view controller's main view.

In my opinion this approach is better that, for example, asserting the presence of views containing the title and content of a note because:

  1. Those strings are present in the notes list screen as well, and
  2. The focus of the test is not on the content of the screen, but on the presence of the screen itself.
  3. Finally, it is always better to assert for the value of `accessibilityIdentifier` rather than `accessibilityLabel`.

How do we make this test pass? Looking into `NotesListViewController` you'll notice that... I forgot to implement `tableView(didSelectRowAtIndexPath:)`. So silly...

[Implementing the delegate]() makes the acceptance test pass. And now all tests are green, and SimpleNotes is working as expected. Hurray! 🎉

## Wrapping up

These two bugs in Simple Notes were just examples, but not too far from what real world development looks like. And the same goes for the way to fix them: identify what's wrong, write a failing test, write code to make the test pass.

Not only this process is great to get into the TDD mindset, but it also produces a suite of _regression tests_, that will make sure you won't ship the same bug twice.

I find that developing by writing failing tests then making them pass a very pleasurable experience, almost like a game made of little quests. Plus is a way to keep the system simple, writing long tests is a smell of a too complex design that more often than not can be simplified.

What is your opinion on this? Have you ever tried to write a test for an existing bug? I'd like to hear from you, ping me on Twitter [@mokagio](https://twitter.com/mokagio), leave a comment below, and don't forget to [subscribe to the newsletter](http://www.mokacoding.com/blog/fixing-bugs-driven-by-tests-in-swift/).

_Happy coding, and leave the codebase better than you found it._
