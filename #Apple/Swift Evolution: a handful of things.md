# Swift Evolution: a handful of things

_Captured: 2016-03-09 at 00:55 from [ericasadun.com](http://ericasadun.com/2016/03/08/swift-evolution-a-handful-of-things/)_

I was going through my notes this morning and found an informal (and very incomplete) list of items that I'd really love to see happen in Swift. Several of these came up in discussions but for whatever reason never progressed to a formal proposal or from a proposal to a review or were discarded as something the Swift team would prefer not to pursue.

I thought I'd share a handful of them.

## Better Compiler Directives

Discussed at a variety of times under several topics, these directives include the canonical Evan Maloney suite (Apple/Non-Apple Platform, common UIKit platform, debug/release, simulator/physical, test-supporting), Darwin-support, and the classic William Dillon (big-or-little endian/32-or-64-bit/signed-or-unsigned char) collection.

These directives involve minor changes, are easy to implement, and can be extended over time as needed. It would probably be best to get a sense of which ones the dev community *really* wants and needs and push on those to avoid clutter, but I'd hate to see these languish.

## Eliminating the Weak-Strong Self Dance

Discussed quite a bit, there's a bug that (normally) lets you do
    
    
    guard self = self else {...}

but nothing that adopts this into the language as-yet. It would be such a relief to be able to convert a weak self reference to a strong one to simplify completion blocks.

## Better Option Sets

I know Swift is unlikely to adopt a fourth core type, but surely it would be better and nicer to be able to declare
    
    
    public optionset Features {case alarmSystem, cdStereo, chromeWheels, pinStripes, leatherInterior, undercoating, windowTint}

than
    
    
    public struct Features : OptionSetType {
        public let rawValue : Int
        public init(rawValue: Int) {self.rawValue = rawValue} // workaround, :(, silly Apple
        
        public static let AlarmSystem = Features(rawValue: 1 << 1)
        public static let CDStereo = Features(rawValue: 1 <<  2)
        public static let ChromeWheels = Features(rawValue: 1 <<  3)
        public static let PinStripes = Features(rawValue: 1 <<  4)
        public static let LeatherInterior = Features(rawValue: 1 <<  5)
        public static let Undercoating = Features(rawValue: 1 <<  6)
        public static let WindowTint = Features(rawValue: 1 <<  7)
    }

The current system lets you combine options together, for example:
    
    
    public struct LaundryOptions: OptionSetType {
        public static let EnergyStar: LaundryOptions = [.LowWater, .LowHeat]
        public static let LowWater = 1, LowHeat = 2
    }

but I can't imagine that it would really be that hard to expand an option set type to do the same:
    
    
    public optionset LaundryOptions {
        case lowWater, lowHeat
        compound energyStar = [.LowWater, .LowHeat]
    }

This is most likely to be implemented through some kind of Macro system, as it currently is in Rust. (Thanks, [Kevin](http://www.twitter.com/eridius))

## **Struct Inheritance**

This is one that gets brought up occasionally, discussed, and then disappears into the wind. There's probably no right way to do it and I understand the complexity, especially when you're talking about overriding methods, and keeping to a value type system.

Inheritance would enable you to have direct access to members while extending with new members, without having to wrap everything in a new type and then provide custom ways to forward embedded types to be externally visible.

I'd also settle for less "inherit-y" composition, so long as the results are more or less the same.

## Enum Case Collections

"It is a truth universally acknowledged, that a programmer in possession of an enum with many cases, must eventually be in want of dynamic enumeration over them." This [has a proposal](https://github.com/apple/swift-evolution/pull/114) but is otherwise just sitting there.

## Other Stuff

This just scratches my list. Other things like decimal types, re-imagining ranges and intervals, extended guard constructs, and cascading can probably wait for the deluge to pass.

What's on your list of stuff you'd really like to see make the Swift cut?
