# What exactly is RESTful programming?

_Captured: 2015-12-17 at 00:02 from [stackoverflow.com](http://stackoverflow.com/questions/671118/what-exactly-is-restful-programming)_

_REST_ is the underlying architectural principle of the web. The amazing thing about the web is the fact that clients (browsers) and servers can interact in complex ways without the client knowing anything beforehand about the server and the resources it hosts. The key constraint is that the server and client must both agree on the _media_ used, which in the case of the web is _HTML_.

An API that adheres to the principles of _REST_ does not require the client to know anything about the structure of the API. Rather, the server needs to provide whatever information the client needs to interact with the service. An _HTML form_ is an example of this: The server specifies the location of the resource, and the required fields. **The browser doesn't know in advance where to submit the information, and it doesn't know in advance what information to submit. Both forms of information are entirely supplied by the server.** (This principle is called _HATEOAS_.)

**So, how does this apply to _HTTP_, and how can it be implemented in practice?** HTTP is oriented around verbs and resources. The two verbs in mainstream usage are GET and POST, which I think everyone will recognize. However, the HTTP standard defines several others such as PUT and DELETE. These verbs are then applied to resources, according to the instructions provided by the server.

For example, Let's imagine that we have a user database that is managed by a web service. Our service uses a custom hypermedia based on JSON, for which we assign the mimetype _application/json+userdb_ (There might also be an _application/xml+userdb_ and _application/whatever+userdb_ \- many media types may be supported). The client and the server has both been programmed to understand this format, but they don't know anything about each other. As [Roy Fielding](http://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven) points out:

> A REST API should spend almost all of its descriptive effort in defining the media type(s) used for representing resources and driving application state, or in defining extended relation names and/or hypertext-enabled mark-up for existing standard media types.

A request for the base resource `/` might return something like this:

**Request**
    
    
    GET /
    Accept: application/json+userdb
    

**Response**
    
    
    200 OK
    Content-Type: application/json+userdb
    
    {
        "version": "1.0",
        "links": [
            {
                "href": "/user",
                "rel": "list",
                "method": "GET"
            },
            {
                "href": "/user",
                "rel": "create",
                "method": "POST"
            }
        ]
    }
    

We know from the description of our media that we can find information about related resources from sections called "links". This is called _Hypermedia controls_. In this case, we can tell from such a section that we can find a user list by making another request for `/user`:

**Request**
    
    
    GET /user
    Accept: application/json+userdb
    

**Response**
    
    
    200 OK
    Content-Type: application/json+userdb
    
    {
        "users": [
            {
                "id": 1,
                "name": "Emil",
                "country: "Sweden",
                "links": [
                    {
                        "href": "/user/1",
                        "rel": "self",
                        "method": "GET"
                    },
                    {
                        "href": "/user/1",
                        "rel": "edit",
                        "method": "PUT"
                    },
                    {
                        "href": "/user/1",
                        "rel": "delete",
                        "method": "DELETE"
                    }
                ]
            },
            {
                "id": 2,
                "name": "Adam",
                "country: "Scotland",
                "links": [
                    {
                        "href": "/user/2",
                        "rel": "self",
                        "method": "GET"
                    },
                    {
                        "href": "/user/2",
                        "rel": "edit",
                        "method": "PUT"
                    },
                    {
                        "href": "/user/2",
                        "rel": "delete",
                        "method": "DELETE"
                    }
                ]
            }
        ],
        "links": [
            {
                "href": "/user",
                "rel": "create",
                "method": "POST"
            }
        ]
    }
    

We can tell a lot from this response. For instance, we now know we can create a new user by POSTing to `/user`:

**Request**
    
    
    POST /user
    Accept: application/json+userdb
    Content-Type: application/json+userdb
    
    {
        "name": "Karl",
        "country": "Austria"
    }
    

**Response**
    
    
    201 Created
    Content-Type: application/json+userdb
    
    {
        "user": {
            "id": 3,
            "name": "Karl",
            "country": "Austria",
            "links": [
                {
                    "href": "/user/3",
                    "rel": "self",
                    "method": "GET"
                },
                {
                    "href": "/user/3",
                    "rel": "edit",
                    "method": "PUT"
                },
                {
                    "href": "/user/3",
                    "rel": "delete",
                    "method": "DELETE"
                }
            ]
        },
        "links": {
           "href": "/user",
           "rel": "list",
           "method": "GET"
        }
    }
    

We also know that we can change existing data:

**Request**
    
    
    PUT /user/1
    Accept: application/json+userdb
    Content-Type: application/json+userdb
    
    {
        "name": "Emil",
        "country": "Bhutan"
    }
    

**Response**
    
    
    200 OK
    Content-Type: application/json+userdb
    
    {
        "user": {
            "id": 1,
            "name": "Emil",
            "country": "Bhutan",
            "links": [
                {
                    "href": "/user/1",
                    "rel": "self",
                    "method": "GET"
                },
                {
                    "href": "/user/1",
                    "rel": "edit",
                    "method": "PUT"
                },
                {
                    "href": "/user/1",
                    "rel": "delete",
                    "method": "DELETE"
                }
            ]
        },
        "links": {
           "href": "/user",
           "rel": "list",
           "method": "GET"
        }
    }
    

Notice that we are using different HTTP verbs (GET, PUT, POST, DELETE etc.) to manipulate these resources, and that the only knowledge we presume on the clients part is our media definition.

Further reading:

  * The many much better answers on this very page. 

(This answer has been subject of a fair amount of criticism for missing the point. For the most part, that has been a fair critique. What I originally described was more in line with how REST was usually implemented a few years ago when I first wrote this, rather than its true meaning. I've revised the answer to better represent the real meaning.)

![Richardson Maturity Model](http://i.stack.imgur.com/FoKRB.png)

> _Richardson Maturity Model_
