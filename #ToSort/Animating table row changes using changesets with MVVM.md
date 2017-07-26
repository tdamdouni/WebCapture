# Animating table row changes using changesets with MVVM

_Captured: 2015-12-31 at 21:55 from [www.martinrichter.net](http://www.martinrichter.net/blog/2015/12/30/animating-table-row-changes-using-changesets-with-mvvm/)_

_This is the seventh post in my series on [MVVM with ReactiveCocoa 3/4 in Swift](http://www.martinrichter.net/blog/2015/08/12/mvvm-with-reactivecocoa-3-in-swift/)._

If you've ever written an iOS app that contained some kind of list, you are most certainly familiar with `UITableView`. This UIKit staple refreshes itself by pulling new data from a `UITableViewDataSource` when told so by its owner, which is usually a view controller.

In MVVM and similar architectures, the view controller is no longer in charge of retrieving and holding the data that populates our table view. This activity now occurs "deeper" in the hierarchy of architectural layers, for example in a view model. (I agree, by the way, that "view models" are [very poorly named](http://khanlou.com/2015/12/mvvm-is-not-very-good/), but do concur with [Ash Furrow's view](https://ashfurrow.com/blog/mvvm-is-exceptionally-ok/) on the matter.) But how does the view get updated? Typically, we would expose an observable signal on the view model that sends new values, such as formatted strings, for the view to display. But as mentioned above, `UITableView` doesn't want us to push content - it wants us to tell it when to pull.

## The brute-force approach

When starting to write the [SwiftGoal](https://github.com/richeterre/SwiftGoal) showcase app, I opted for a very simple refresh mechanism: Every time there was new data, the view model would emit a `Bool` of value `true` (today I realize that I should have used `Void` instead, as the actual value was discarded anyway) on a signal called `updatedContentSignal`. The table view controller could then subscribe to the signal like so:
    
    
    // MatchesViewController.swift
    
    viewModel.updatedContentSignal
        |> observeOn(UIScheduler())
        |> observe(next: { [weak self] _ in
            self?.tableView.reloadData()
        })

This would cause the table view to ask its data source for new data and completely refresh itself, without visually indicating what rows actually changed.

## Animating insertions and deletions

After the initial fetch, an application's data rarely changes in its entirety. In a logbook-style app like SwiftGoal, a few entries might have been added since the last refresh, and some others deleted, but the majority remains unchanged. Wouldn't it be nice if we could visualize the changes? And indeed, `UITableView` comes with some [handy methods](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/TableView_iPhone/ManageInsertDeleteRow/ManageInsertDeleteRow.html#//apple_ref/doc/uid/TP40007451-CH10-SW9) to insert and delete cells in batches that must be surrounded with `beginUpdates` and `endUpdates` calls. (Whether such an API design is appropriate in the year 2015 is a topic for another post.) Doing so will also give us some neat animations for free.

To build this, we have to adjust our view model's API a little. The view must not only know _when_ to refresh, but also what rows are affected. However, the actual content will still be loaded in a pull-driven fashion from the table view's data source. So our exposed signal, now renamed to reflect the new behavior, looks like this:
    
    
    // MatchesViewModel.swift
    
    let contentChangesSignal: Signal<Changeset, NoError>

The `Changeset` is a [little data structure I wrote](https://github.com/richeterre/SwiftGoal/blob/v1.0/SwiftGoal/Models/Changeset.swift) that encapsulates two arrays of `NSIndexPath` instances, one for deletions and one for insertions. Its initializer takes two arrays, `oldItems` and `newItems`, and populates its index path arrays accordingly.

How then do we generate these changesets for the signal? After all, each changeset carries information that depends on our data's _current and previous_ state. But here's the beauty of functional reactive programming: It turns out that ReactiveCocoa comes with an [operator](https://github.com/ReactiveCocoa/ReactiveCocoa/blob/master/ReactiveCocoa/Swift/Signal.swift#L655-L664) that effectively makes this a one-liner! Can you spot it?
    
    
    // MatchesViewModel.swift
    // (code adjusted for readability)
    
    refreshSignal
        .flatMap(.Latest) { _ in
            return store.fetchMatches()
                .flatMapError { error in
                    return SignalProducer(value: [])
                }
        }
        .combinePrevious([]) // Preserve history to calculate changeset
        .startWithNext({ [weak self] (oldMatches, newMatches) in
            self?.matches = newMatches
            if let observer = self?.contentChangesObserver {
                let changeset = Changeset(
                    oldItems: oldMatches,
                    newItems: newMatches
                )
                observer.sendNext(changeset)
            }
        })

Whenever a new array of matches arrives from the store and gets flattened onto the main signal chain, `combinePrevious` will combine it with the one sent right before it, returning a tuple of type `([Match], [Match])` that we can pass to the changeset initializer. (The empty array `[]` provided by us as a parameter is used for the initial value.) Finally, the resulting changeset is sent to an observer that feeds our `contentChangesSignal`. We also update the `self.matches` property with our new data to ensure that the table view can properly refresh its content:
    
    
    // MatchesViewController.swift
    
    viewModel.contentChangesSignal
        .observeOn(UIScheduler())
        .observeNext({ [weak self] changeset in
            guard let tableView = self?.tableView else { return }
    
            tableView.beginUpdates()
            tableView.deleteRowsAtIndexPaths(changeset.deletions, withRowAnimation: .Automatic)
            tableView.insertRowsAtIndexPaths(changeset.insertions, withRowAnimation: .Automatic)
            tableView.endUpdates()
        })

## A word on equality

Equality is a powerful concept that has inspired [fantastic posts](http://nshipster.com/equality/) also in the iOS community. Generating changesets means that we need to define what it _means_ that an item is present in one array, but not in another. All of SwiftGoal's models are structs, which, [unlike classes, have value semantics](http://austinzheng.com/2015/10/04/swift-equatable/). We can make them conform to the `Equatable` protocol, overriding `==`, to be able to use basic array methods like `contains` for calculating the changesets.[1](http://www.martinrichter.net/blog/2015/12/30/animating-table-row-changes-using-changesets-with-mvvm/)

Let's take the example of a match. It has a unique identifier (`String`), two `[Player]` arrays with home and away players, respectively, and two `Int` properties for home and away goals. As the view currently only handles deletions and insertions, but not modifications, two matches that have the same identifier but e.g. different home goal counts must be treated as _not equal_, or else our table view would not refresh the data correctly.
    
    
    // Match.swift
    
    extension Match: Equatable {}
    
    public func ==(lhs: Match, rhs: Match) -> Bool {
        return lhs.identifier == rhs.identifier
            && lhs.homePlayers == rhs.homePlayers
            && lhs.awayPlayers == rhs.awayPlayers
            && lhs.homeGoals == rhs.homeGoals
            && lhs.awayGoals == rhs.awayGoals
    }

So this works, but there is a UX flaw: In the aforementioned scenario where some property _within_ the same real-world match changes, the cell in question would animate out as if deleted, only to be replaced by a newly inserted cell with the updated content. This is acceptable, but not great, so let's improve the code further!

## Animating changes in content

The key point is that our model instances, being immutable, represent **real-life entities at different moments in time**. For example, two structs can both represent a Friday afternoon match between Anna and Bob, but with different scores - maybe the score was corrected after creation. We therefore need a way to distinguish between real-life entities, but also between content that might have changed over time. To choose between the two, it helps to think about the purpose of comparison. When should a list item be removed or inserted? When should it be updated in place?

In the case of SwiftGoal's match list, the answer is clear: Adding and deleting match records on the server should result in their insertion or deletion from the table view. Any change to the _content_ of the match, such as home or away goals, on the other hand, should cause the corresponding cell to be reloaded in place, e.g. with a cross-fade animation.

We can override the `==` operator to check whether two `Match` instances represent the same, "timeless" real-world entity.[2](http://www.martinrichter.net/blog/2015/12/30/animating-table-row-changes-using-changesets-with-mvvm/) The way to tell is to look at their identifier. This means that our earlier comparison function can be simplified to
    
    
    // Match.swift
    
    extension Match: Equatable {}
    
    public func ==(lhs: Match, rhs: Match) -> Bool {
        return lhs.identifier == rhs.identifier
    }

For content equality, we need a different function that looks at other fields than just the identifier. Let's call it `contentMatches` and define it like so:
    
    
    // Match.swift
    
    extension Match: Equatable {}
    
    static func contentMatches(lhs: Match, _ rhs: Match) -> Bool {
        return lhs.identifier == rhs.identifier
            && Player.contentMatches(lhs.homePlayers, rhs.homePlayers)
            && Player.contentMatches(lhs.awayPlayers, rhs.awayPlayers)
            && lhs.homeGoals == rhs.homeGoals
            && lhs.awayGoals == rhs.awayGoals
    }

Note how any nested models (in this case, the two `Player` arrays) _must be tested for matching content, too_. Suppose that a player's name has changed and then gets shown as part of an otherwise unchanged match in the table view. Merely checking player identity would result in a visible bug, as the cell would not refresh its contents. Inside the `Player` model, comparing content happens the same way as for matches.[3](http://www.martinrichter.net/blog/2015/12/30/animating-table-row-changes-using-changesets-with-mvvm/)

Equipped with these comparison tools, we can now initialize changesets with two arrays (the old and new items) and our content matching function:
    
    
    // Changeset.swift
    
    typealias ContentMatches = (T, T) -> Bool
    
    init(oldItems: [T], newItems: [T], contentMatches: ContentMatches) {
    
        deletions = oldItems.difference(newItems).map { item in
            return Changeset.indexPathForIndex(oldItems.indexOf(item)!)
        }
    
        modifications = oldItems.intersection(newItems)
            .filter({ item in
                let newItem = newItems[newItems.indexOf(item)!]
                return !contentMatches(item, newItem)
            })
            .map({ item in
                return Changeset.indexPathForIndex(oldItems.indexOf(item)!)
            })
    
        insertions = newItems.difference(oldItems).map { item in
            return NSIndexPath(forRow: newItems.indexOf(item)!, inSection: 0)
        }
    }

For deletions and insertions, we grab the indices of all items that differ. For modifications, we filter the items common to both arrays based on whether their content matches, and store their indices. (The `difference` and `intersection` array extensions are defined in a separate file and do exactly what it says on the tin )

By the way, this kind of code should rank very high on your "make sure to test this" list, as hard-to-find bugs are likely to occur. Take a look at SwiftGoal's `Changeset` [test file](https://github.com/richeterre/SwiftGoal/blob/v1.1/SwiftGoalTests/Models/ChangesetSpec.swift) for an example.

Finally, we must add one single line of code to our view controller to make sure it also reloads the index paths that are marked as modified in the changeset:
    
    
    // MatchesViewController.swift
    
    viewModel.contentChangesSignal
        .observeOn(UIScheduler())
        .observeNext({ [weak self] changeset in
            guard let tableView = self?.tableView else { return }
    
            tableView.beginUpdates()
            tableView.deleteRowsAtIndexPaths(changeset.deletions, withRowAnimation: .Automatic)
            tableView.reloadRowsAtIndexPaths(changeset.modifications, withRowAnimation: .Automatic)
            tableView.insertRowsAtIndexPaths(changeset.insertions, withRowAnimation: .Automatic)
            tableView.endUpdates()
        })

## Summary

While animating table row changes isn't strictly an MVVM topic, I consider it an excellent selling point, because the architecture introduces a nice **separation of concerns**: The view model converts subsequent item arrays into changesets using rules that live in the model layer, and all that remains for the view is to manage the visual row changes based on `NSIndexPath` arrays that it receives from its view model. And the best part is, you can apply this regardless of your exact setup. Prefer [RxSwift](https://github.com/ReactiveX/RxSwift) over ReactiveCocoa? Hate view models and want to write [presenters and interactors](https://www.objc.io/issues/13-architecture/viper/) instead? With a few adjustments, the above will still work for you.

  1. Although structs are value types and don't offer pointer equality the way classes do, overriding `==` and comparing an `identifier` property essentially introduces a similar concept of identity. The difference is that such identifiers go even further than the memory pointers of class instances, as they extend past the application to the server database. But instead of using structs, one could in principle one choose classes and create a factory that guarantees the uniqueness of instances, e.g. when fetching data from the backend. As someone eager to dig deeper into Swift, I simply made the choice to use structs instead. [↩](http://www.martinrichter.net/blog/2015/12/30/animating-table-row-changes-using-changesets-with-mvvm/)

  2. Overriding `==` for structs with identifier comparison comes with a few caveats. For example, storing such instances in a mutable collection like a `Set` or `Array` will require you to re-add them to update their content, because the collection uses `==` to check whether it already contains the instance. Many operators in FRP frameworks do the same and might thus filter out "too much" when applied to a signal that carries content changes. Fortunately, the ReactiveCocoa folks kept this in mind when designing the `skipRepeats` [operator](https://github.com/ReactiveCocoa/ReactiveCocoa/blob/v4.0.0-RC.1/ReactiveCocoa/Swift/Signal.swift#L717-L729), allowing us to pass a matcher function. [↩](http://www.martinrichter.net/blog/2015/12/30/animating-table-row-changes-using-changesets-with-mvvm/)

  3. For the `Ranking` [model](https://github.com/richeterre/SwiftGoal/blob/v1.1/SwiftGoal/Models/Ranking.swift), however, it's a bit more complicated. A ranking doesn't have a real-life counterpart in the same way matches or players do, because it is generated on the fly to combine a player and their current rating. As we don't want a deletion and insertion in the rating table when an existing player's rating changes, we decide that ranking equality (`==`) simply means that it has the same real-world player, while any changes in player content or rating cause the content matcher to return `false`. [↩](http://www.martinrichter.net/blog/2015/12/30/animating-table-row-changes-using-changesets-with-mvvm/)
