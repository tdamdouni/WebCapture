# CURL Comes to N1QL: Querying External JSON Data

_Captured: 2017-05-03 at 23:42 from [dzone.com](https://dzone.com/articles/curl-comes-to-n1ql-querying-external-json-data?edition=294992&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-03)_

N1QL has many functions that allow you to perform a specific operation. One such function that has been added into the new Couchbase 5.0 DP is CURL.

CURL allows you to use N1QL to interact with external JSON endpoints; namely, Rest API's that return results and data in JSON format. Interaction primarily consists of data transfer to and from a server using the http and https protocols. In short, the CURL function in N1QL provides you, the user, a subset of standard curl functionality (<https://curl.haxx.se/docs/manpage.html>) within a query language.

In order to retrieve data from different servers (such as Google Maps, Yahoo Finance etc), we can issue either GET or HTTP POST requests using the CURL function. This is seen in the diagram below.

![](https://docs.google.com/drawings/d/s7H8C-gEWVmH1534QaEGPmg/image?w=502&h=425&rev=250&ac=1)

## Function Definition

CURL (URL, [options])

The first argument is the URL, which represents any URL that points to a JSON endpoint. Only URLs with the http:// or the https:// protocol are supported. Redirection is disabled.

Later in the article we shall see examples that query from the Google Geocode API, the Yahoo Finance API, Couchbase full text search and the Github API. The second argument is a list of options. This is a JSON object that contains a list of curl options and their corresponding values.

We support a variety of options that allow you to interact with any endpoint effectively. In general these can be categorized into security related options and general options. A table of the supported options is given at the end of the article.

## Interaction With Different Endpoints

Let us see how to query different endpoints using the CURL function in N1QL.

### Google Maps Geocoding API

The Geocoding API from Google Maps allows you to convert static addresses into coordinates and vice versa using HTTP request. (For more information refer to <https://developers.google.com/maps/documentation/geocoding/intro> )

Say you want to search for Santa Cruz in Spain using your Google Dev API key. In order to do this, you can use the following query:
    
    
    curl https://maps.googleapis.com/maps/api/geocode/json?address=santa+cruz&components=country:ES&key=<Your Developer API key>

#### Corresponding Query

This query retrieves the address and geographic location bounds of the address, Santa Cruz, ES. We use the address, components and key parameters from the Google Maps Geocoding REST API. The "data" option represents the curl data option that represents HTTP POST data. However, because this is a get request we set the "get" option to true. You can provide values to all the REST parameters within the data option.

The above query searches for Half Moon Bay.

### Yahoo Finance API

The Yahoo Finance API allows you to use the Yahoo Query Language (YQL) to fetch stock quotes (as seen in <http://meumobi.github.io/stocks%20apis/2016/03/13/get-realtime-stock-quotes-yahoo-finance-api.html> ). Below is the YQL SELECT statement to access the stock of Hortonworks Inc (HDP).

In order to get the results in JSON you can use the following URL:

[https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20yahoo.finance.quotes%20where%20symbol%20in%20(%22HDP%22)&format=json&diagnostics=true&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys&callback=](https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20yahoo.finance.quotes%20where%20symbol%20in%20\(%22HDP%22\)&format=json&diagnostics=true&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys&callback=)

For this query, the value of the data option contains the Yahoo REST parameters, q (for the YQL query), format (to return data in JSON) and some other parameters.

### Couchbase Full Text Search

Couchbase's Full Text Search allows you to apply fuzzy search to data stored in Couchbase. For more information see <https://blog.couchbase.com/2016/february/couchbase-4.5-developer-preview-couchbase-fts> .

Suppose you create a FTS index called beers on the beer-sample bucket in Couchbase. You can now search for beer type pale ale using this index, using the CURL function in N1QL. It is important to note that FTS currently accepts HTTP POST instead of GET. To explicitely specify the POST request method, use the request option.

We give multiple options in this query. The header option allows you to pass a custom header to server. Content-Type : application/json tells the server that the data is provided in JSON format. If we have a password protected bucket in Couchbase, then we need to pass its credentials with the query. The user option can be used to pass in a colon-separated username and password. The request option specifies that POST request method is used.

If you want to retrieve only those documents from beer-sample that are returned by the search above, you can write a N1QL JOIN query as follows.

This will retrieve the ids of the documents returned by the FTS query that searches for pale ale, along with the total hits and all the details from the corresponding document in beer-sample.

## Github API (Will be supported in Couchbase 5.0 DP 2)

Github's API is a bit different from the previous API's, in that it returns multiple results in the form of a JSON array of result values. This can be treated as multiple documents.Refer to the Github API docs in <https://developer.github.com/v3/> for more details on what can be queried.

Say you want to find out all the repositories linked to a Github account. The following query does this

If the account has three repositories, the query gives three results. The RAW keyword is used to return the array of documents that the query returns, without a wrapper object. One point you will notice is that the header option contains the User-Agent with a github username. This is now mandatory for all Github API requests.

Now from this list, say you would like to know, what is the clone url for each of these repos. The following query accomplishes this

## Summary

As you can see with the above examples, using the CURL function, N1QL users can now interact with any external API's that return results in JSON format. This opens up many possibilities. For example, if Couchbase contains data corresponding to different hotels, then you can use the Google Maps API to find nearby locations to each of the corresponding hotels.

The N1QL implementation of CURL uses the golang libcurl API -[ https://github.com/andelf/go-curl](https://github.com/andelf/go-curl)

## List of Available Options

### Security Options

Option

Description

value

user

Server user and password

When password is empty it is treated as an empty password string.

USERNAME[:PASSWORD] 

basic

Use HTTP Basic Authentication

BOOLEAN (TRUE/ FALSE)

insecure 

Allow connections to SSL sites without certs (H)

BOOLEAN (TRUE/ FALSE)

anyauth

curl to figure out authentication method by itself, and use the most secure one

BOOLEAN (TRUE/ FALSE)

cacert 

  
  
  
  


Specify CA signed certificate filename

Certificates should be stored on the local machine - each query node within a cluster. 

/Couchbase/var/lib/couchbase/n1qlcerts to store certificates. This is not visible to the user. 

The Filename cannot contain a path. If it is not a match to the existing contents of n1qlcerts directory, the function throws an error.

For expired and invalid certificates throw an error. 

FILENAME (This is the certificate, pem file for aws for example)

  


### Other Transfer-Related Options

Option

Description

Value

get, G

Get request for CURL

BOOLEAN (true/false)

X, request

Set the request method. This only accepts GET or POST and is case sensitive. 

For all other cases it errors out.

{"request":"POST"}

connect-timeout

  


Maximum time allowed for connection. It should contain the maximum time in seconds that you allow the connection phase to the server to take. This only limits the connection phase, it has no impact once it has connected. Set to zero to switch to the default built-in connection timeout - 300 seconds. 

If float value, we truncate it to the integer value.

For all other types (not a number) throw error.

SECONDS

max-time 

Maximum time allowed for the transfer operation.

Default timeout is 0 (zero) which means it never times out during transfer.

If float value, we truncate it to the integer value.

For all other types (not a number) throw error.

SECONDS 

data 

HTTP POST data (H)

Allows us to set all the rest api parameters for the given endpoint.

STRING

OR

[...string,string….]

header 

Pass custom header string to server (H)

STRING 

OR

[...string,string….]

show-error

Show error. 

When true show errors when they occur. 

When false suppress the errors

BOOLEAN (TRUE/ FALSE)

silent

Silent mode (don't output anything)

BOOLEAN (TRUE/ FALSE)

keepalive-time

Wait SECONDS between keepalive probes for low level TCP connectivity. (Does not affect HTTP level keep-alive)

SECONDS

user-agent

Value for the User-Agent to send to the server.

STRING

data-urlencode

Encode the data, and send to server. 

This is a test => this%20is%20a%20test 

STRING 

OR

[...string,string….]
