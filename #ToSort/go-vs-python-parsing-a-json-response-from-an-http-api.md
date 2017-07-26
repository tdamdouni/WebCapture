# Go vs. Python: Parsing a JSON Response From an HTTP API

_Captured: 2017-02-03 at 13:55 from [dzone.com](https://dzone.com/articles/thoughts-on-software-development-go-vs-python-pars)_

As part of a _[recommendations with Neo4j talk_](https://www.meetup.com/graphdb-london/events/236256437/) that I've presented a few times over the last year, I have a set of scripts that download some data from the [meetup.com API](https://www.meetup.com/meetup_api/).

They're all written in Python but I thought it'd be a fun exercise to see what they'd look like in Go. My eventual goal is to try and parallelize the API calls.

This is the Python version of the script:
    
    
    uri ="https://api.meetup.com/2/groups?&topic={0}&lat={1}&lon={2}&key={3}".format(seed_topic , lat , lon , key )  
    
    
    all_topics =[topic ["urlkey"] for result in r. json()["results"]
    
    
    for topic in result ["topics"]] for topic in all_topics: 

We're using the [requests](http://docs.python-requests.org/en/master/) library to send a request to the meetup API to get the groups which have the topic 'nosql' in the London area. We then parse the response and print out the topics.

Now, to do the same thing in Go! The first bit of the script is almost identical:
    
    
    var httpClient = &http.Client{Timeout: 10 * time.Second}
    
    
    uri := fmt.Sprintf("https://api.meetup.com/2/groups?&topic=%s&lat=%s&lon=%s&key=%s", seedTopic, lat, lon, key)

If we run that this is the output we see:
    
    
    $ go cmd/blog/main.go
    
    
    &{200 OK 200 HTTP/2.0 2 0 map[X-Meetup-Request-Id:[2d3be3c7-a393-4127-b7aa-076f150499e6] X-Ratelimit-Reset:[10] Cf-Ray:[324093a73f1135d2-LHR] X-Oauth-Scopes:[basic] Etag:["35a941c5ea3df9df4204d8a4a2d60150"] Server:[cloudflare-nginx] Set-Cookie:[__cfduid=d54db475299a62af4bb963039787e2e3d1484894864; expires=Sat, 20-Jan-18 06:47:44 GMT; path=/; domain=.meetup.com; HttpOnly] X-Meetup-Server:[api7] X-Ratelimit-Limit:[30] X-Ratelimit-Remaining:[29] X-Accepted-Oauth-Scopes:[basic] Vary:[Accept-Encoding,User-Agent,Accept-Language] Date:[Fri, 20 Jan 2017 06:47:45 GMT] Content-Type:[application/json;charset=utf-8]] 0xc420442260 -1 [] false true map[] 0xc4200d01e0 0xc4202b2420}

So far so good. Now we need to parse the response that comes back.

Most of the examples that I came across [suggest creating a struct with all the fields](http://stackoverflow.com/questions/17156371/how-to-get-json-response-in-golang) that you want to extract from the JSON document but that feels a bit overkill for such a simple script.

Instead we can just create maps of (string -> interface{}) and then apply type conversions where appropriate. I ended up with the following code to extract the topics:
    
    
    for _, rawGroup := range target["results"].([]interface{}) {
    
    
        group := rawGroup.(map[string]interface{})
    
    
        for _, rawTopic := range group["topics"].([]interface{}) {
    
    
            topic := rawTopic.(map[string]interface{})

It's more verbose than the Python version because we have to explicitly type each thing we take out of the map at every stage, but it's not too bad. This is the full script:

Once I've got these topics, the next step is to make more API calls to get the groups for those topics.

I want to make those API calls in parallel while making sure I don't exceed the rate limit restrictions on the API and I think I can make use of Go routines, channels, and timers to do that.

But that's for another post!
