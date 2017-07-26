# Object-Oriented Solutions: Avoiding Getters

_Captured: 2017-03-28 at 20:41 from [dzone.com](https://dzone.com/articles/object-oriented-solutions-avoiding-getters?edition=286932&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-28)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

Alice and Bob were both working in a small team for an international broker, creating an application to react to certain events in the market. The application's architecture centered around Trades, that represent transactions between buyers and sellers exchanging something of value on an exchange.

The initial implementation of a Trade was committed by Alice, who designed the Trade according to Object-Oriented principles, concentrating on features the Trade must have, instead of the data it must contain. It looked like this:
    
    
        public Trade(Date timestamp, Symbol symbol, BigDecimal price, int volume) {

It had no getter or setter (accessor) methods. Instead, it offered methods that closely followed business requirements, something that was part of the language the traders also used.

## Remembering The Latest Trade

Bob was working on a different part of the system, calculating differences, rises, and drops in prices, the breadth of changes occurring on certain symbols (like Google (GOOG), Apple (APPL), etc.).

To calculate how the price moved for a single symbol, Bob used a Map to remember the latest Trade for every Symbol. His initial implementation looked liked this:
    
    
    private final Map < Symbol, Trade > lastTrades = new HashMap < > ();
    
    
        Trade lastTrade = lastTrades.get(trade.getSymbol());

Unfortunately, this code did not compile, because there was no `getSymbol()` method in the `Trade` object, therefore there was no way to get the Symbol of the Trade.

Bob opened the Trade class and to his relief noticed that the Trade _does_ actually have the Symbol as a private field, so Bob did the following:

He added the "missing" getter accessor method to publish the symbol of the trade, so his code could compile. Fortunately, Alice noticed the change in a code review and approached Bob to speak about this change:

## Discussing the Change

**Alice**: Hi Bob, I've noticed your change to Trade, you introduced a getter for the Symbol.  
**Bob**: Yes, was there a conflict?  
**Alice**: No, I was just curious what you need the Symbol for, and whether there was maybe something else in the Trade you could use…  
**Bob**: I need the Symbol of the Trade to create a Map with the Symbol as key.  
**Alice**: What are you using that Map for?  
**Bob**: I need to remember the latest Trade for a given Symbol to calculate differences.  
**Alice**: Ok, the difference calculation is already in the Trade. Could we move this "latest Trade" functionality into the Trade somehow?  
**Bob**: I guess we could, but why would we?  
**Alice**: Well, the Symbol is internal to the Trade, we shouldn't just expose that for everybody.  
**Bob**: Hm, but Symbol is a basic property of the Trade, I think exposing that does no harm, does it?  
**Alice**: I'm not sure. I know there are features coming to change the Symbol, introducing Options and Option Chains. I'm pretty sure our Symbol concept will change eventually, and that shouldn't impact our code elsewhere.  
**Bob**: Ok, how could we include this in the Trade? The Trade has no concept of previous Trades.  
**Alice**: Maybe the Trade can give you something new that can help, that does not expose the Symbol?  
**Bob**: Well, it could give me the Map directly, I actually only need the Map.  
**Alice**: That sounds good. Maybe we can call it a Cache, because it caches the latest Trades?  
**Bob**: Sounds good, let's define the interface for that…

## Implementing the Trade Cache

Alice and Bob agreed to avoid exposing the Symbol property of the Trade to avoid maintenance problems later. Instead, they created the Cache in the Trade, with the explicit functionality Bob needed:
    
    
            void withNewTrade(Trade newTrade, BiConsumer < Trade, Trade > logic);
    
    
            private final Map < Symbol, Trade > latestTrades = new HashMap < > ();
    
    
            public void withNewTrade(Trade newTrade, BiConsumer < Trade, Trade > logic) {
    
    
                Trade latestTrade = latestTrades.get(newTrade.symbol);

With this new feature from Trade, Bob's code became simpler, but more importantly, it became independent of the internal structure of Trade:

## Conclusion

Object-Orientation is a way to isolate objects to protect against changes that can propagate through code unchecked. The main tool to reach this isolation is encapsulation and data hiding. Following these principles requires objects to take on real responsibilities, and avoid exposing the details of these responsibilities, like the "properties" or other objects that are needed for them.

This article shows one possible way to avoid exposing properties by moving a functionally closed, meaningful feature into the object best suitable for it. Although these kinds of solutions might be unfamiliar to developers trained or experienced in other paradigms, they are absolutely necessary for creating an Object-Oriented Design.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
