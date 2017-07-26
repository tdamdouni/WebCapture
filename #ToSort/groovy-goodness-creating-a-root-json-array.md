# Groovy Goodness: Creating a Root JSON Array

_Captured: 2017-02-22 at 19:10 from [dzone.com](https://dzone.com/articles/groovy-goodness-creating-root-json-array?edition=271915&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-22)_

Check out this [8-step guide](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code! Brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431).

Creating JSON output with Groovy is easy using [JsonBuilder](http://mrhaki.blogspot.nl/2011/04/groovy-goodness-build-json-with.html) and [StreamingJsonBuilder](http://mrhaki.blogspot.nl/2011/09/groovy-goodness-streaming-json-with.html). In the samples mentioned in the links, we create a JSON object with a key and values. But what if we want to create JSON with a root JSON array using `JsonBuilder` or `StreamingJsonBuilder`? It turns out to be very simple -- by passing a list of values using the constructor or using the implicit method `call`.

In the following example, we use `JsonBuilder` to create a root JSON array:
    
    
    def list = ['The Joker', 'Penguin', 'Catwoman', 'Harley Quinn'].collect { name -> new Villain(name) }
    
    
    assert json1.toString() == '[{"name":"The Joker"},{"name":"Penguin"},{"name":"Catwoman"},{"name":"Harley Quinn"}]'
    
    
    assert json1.toString() == '[{"name":"The Joker"},{"name":"Penguin"},{"name":"Catwoman"},{"name":"Harley Quinn"}]'

In the next example, we use `StreamingJsonBuilder` to create a root JSON array:
    
    
    def list = ['The Joker', 'Penguin', 'Catwoman', 'Harley Quinn'].collect { name -> new Villain(name) }
    
    
    assert json.toString() == '[{"name":"The Joker"},{"name":"Penguin"},{"name":"Catwoman"},{"name":"Harley Quinn"}]'

There is also an implicit method `call` that takes an extra `Closure` argument. For each element in the list, the `Closure` is invoked with the element as an argument. This way, we can customize the root JSON array output using the properties of the object that is in the list. In the following example, we use both the `JsonBuilder` and `StreamingJsonBuilder` classes to transform the elements in the list:
    
    
    def list = ['The Joker', 'Penguin', 'Catwoman', 'Harley Quinn'].collect { name -> new Villain(name) }
    
    
        initials villain.name.split(' ').collect { it[0].toUpperCase() }.join()
    
    
        initials villain.name.split(' ').collect { it[0].toUpperCase() }.join()

Written with Groovy 2.4.8

The Java Zone is brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered). Check out this [8-step guide](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code!
