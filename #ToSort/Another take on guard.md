# Another take on guard

_Captured: 2016-01-01 at 19:28 from [ericasadun.com](http://ericasadun.com/2016/01/01/another-take-on-guard/)_

Today, iOS Dev Weekly pointed to [this writeup](https://medium.com/swift-programming/why-swift-guard-should-be-avoided-484cfc2603c5) by Alexei Kuznetsov about eliminating guard from your code. "Why Swift guard Should Be Avoided" posits that Robert C. Martin's rule of code parsimony (namely, "The first rule of functions is that they should be small. The second rule of functions is that _they should be smaller than that_.") should drive your Swift output.

Kuznetsov writes, "The guard statement is a handy instrument for reducing the number of nested structures in functions. The problem lies not in the instrument itself but in its usage. The guard statement promotes the creation of bigger functions that do several things and act on multiple levels of abstractions. By writing small and focused functions, one can find herself not needing the guard statement at all."

I'm sharing this article because I courteously disagree with this philosophy and I want to explain the factors that motivate my disagreement.

## The Code

In the following snippet, Apple's original example from the Swift Programming Language book designs a virtual Vending Machine. Its `vend `function enables the machine, on successful payment, to dispense an item to a consumer. If my math is right, the original function included 17 lines of code (lines 25-42). This count includes three original guard statements, and four action statements, along with surrounding whitespace:

```swift
struct Item {

var price: Int

var count: Int

}

enum VendingMachineError: ErrorType {

case InvalidSelection

case InsufficientFunds(coinsNeeded: Int)

case OutOfStock

}

class VendingMachine {

var inventory = [

"Candy Bar": Item(price: 12, count: 7),

"Chips": Item(price: 10, count: 4),

"Pretzels": Item(price: 7, count: 11)

]

var coinsDeposited = 0

func dispense(snack: String) {

print("Dispensing \\(snack)")

}

func vend(itemNamed name: String) throws {

guard var item = inventory[name] else {

throw VendingMachineError.InvalidSelection

}

guard item.count > 0 else {

throw VendingMachineError.OutOfStock

}

guard item.price <= coinsDeposited else {

throw VendingMachineError.InsufficientFunds(coinsNeeded: item.price - coinsDeposited)

}

coinsDeposited -= item.price

\--item.count

inventory[name] = item

dispense(name)

}

}
```

Kuznetsov refactors Apple's tutorial vending machine code to eliminate guard statements and minimize each function's statement count. With respect, I'm not a fan of this refactor. And I want to explain why.

```swift
func vend(itemNamed name: String) throws {

let item = try validatedItemNamed(name)

reduceDepositedCoinsBy(item.price)

removeFromInventory(item, name: name)

dispense(name)

}

private func validatedItemNamed(name: String) throws -> Item {

let item = try itemNamed(name)

try validate(item)

return item

}

private func reduceDepositedCoinsBy(price: Int) {

coinsDeposited -= price

}

private func removeFromInventory(var item: Item, name: String) {

\--item.count

inventory[name] = item

}

private func itemNamed(name: String) throws -> Item {

if let item = inventory[name] {

return item

} else {

throw VendingMachineError.InvalidSelection

}

}

private func validate(item: Item) throws {

try validateCount(item.count)

try validatePrice(item.price)

}

private func validateCount(count: Int) throws {

if count == 0 {

throw VendingMachineError.OutOfStock

}

}

private func validatePrice(price: Int) throws {

if coinsDeposited < price {

throw VendingMachineError.InsufficientFunds(coinsNeeded: price - coinsDeposited)

}

}
```

## The refactor is too long and complicated.

Kuznetsov primary goal is to promote small function size. However, the refactor has replaced those 17 lines with 46, splintering the logic around no fewer than eight separate functions. In doing so, the update introduced a high cognitive overhead. A simple linear story became a tangled collection without clear task progression.

In the rewrite, seven dependent calls follow the new `vend` function. They must be read by moving your eyes and attention down and then up and then down again in order to comprehend the flow as you imagine a user pressing the vend button.

Kuznetsov took one unified function and splintered it. I'm going to quickly throw out a reference to George Miller's "[Magical Number Seven](https://en.wikipedia.org/wiki/The_Magical_Number_Seven,_Plus_or_Minus_Two)" here not just because eight is significantly larger than one but also because Martin's rule of functional simplicity attempts to achieve a similar kind of focus, and I think this refactor misses the mark on addressing both concerns.

## The refactor treats preconditions as separate tasks

This is the more substantial criticism, which is the misunderstanding of the role of guard. In Kuznetsov's write-up, guard acts only to reduce nesting. I disagree, and as I pointed out [in my write-up the other day](http://ericasadun.com/2015/12/29/migrating-ifs-to-guards-in-swift/), it is an important member of the assert/precondition family: "A general guard statement establishes requirements for execution. It also provides a safe path for transferring control if and when those requirements fail."

In Kuznetsov's redesign the assertions are subsumed into a validation tree. A primary function `validateItemNamed` calls `validate`. In turn, `validate` collects calls to each validation step, namely `validateCount` and `validatePrice`. I propose that this tree-based layout is hard to read, hard to maintain, and introduces unnecessary complexity.

You must trace the progression of the point of error back to the original `try vend` call. Insufficient funds that fail in `validatePrice` travel back to `validate`, back to `validatedItemNamed`, and from there fail in `vend`. It's a long path for an extremely simple error and it inappropriately separates the validation tasks from the usage tasks.

In Apple's version, the three guard statements limit access to core functionality by performing sanity checks on input and state before proceeding. Importantly, they act as formal specifications about code prerequisites. By including guard statements with the code they annotate, Apple established a direct relationship between the assertions and actions. The code says, in essence, "if these tests pass, perform these actions."

Their co-location is vital. At some future code review, these tests can be inspected in the context of the actions and if needed, updated, modified, or removed with ease. Their proximity provides a vital connection to the code they're guarding.

I would recommend using guard for essential code safety checks. I believe they're being presented this in Apple's version of the vending machine code. You may be able to write your way around guard but your code will not benefit from doing so.
