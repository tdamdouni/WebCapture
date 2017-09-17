# Data Extraction from APIs with Python – Currency Exchange

_Captured: 2017-08-19 at 11:27 from [python.gotrained.com](http://python.gotrained.com/python-json-api-tutorial/?ref=quuu&utm_content=bufferccc9c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

There are several popular platforms that give developers access to their "web services", aka "APIs" (Application Programming Interface). So using APIs is the official way for data extraction and doing other stuff allowed by such applications. You can even benefit from some APIs to build other applications. REST APIs usually generate output in JSON or XML format because most of programming languages can handle these formats easily. In fact, JSON (JavaScript Object Notation) is very similar to data types in programming languages; for example, it is very similar to Python dictionaries. If a REST API allows you to get the data you want to retrieve, then you do not need regular web scraping.

Some APIs require authentication (API Key or Client ID and Client Secret, similar to a username and password, so to speak) to control their usage, and some do not. We will explain this later in multiple APIs. For the purpose of clarifying the basics, we will start with a very simple currency rate conversion API that does not require any authentication.

So this tutorial explains how to use Python to extract data from [Fixer.io](http://fixer.io/) which is -according to its official website- "a free JSON API for current and historical foreign exchange rates published by the European Central Bank."

## API URL

Just as most REST APIs that return JSON, Fixer API gives you a URL with a "query string" with one "parameter" or more. Here is an example URL for finding the rates of USD and GBP in EUR: <http://api.fixer.io/latest?symbols=USD,GBP>

If you click this URL, you will get this result:

123456789
{ "base": "EUR", "date": "2017-06-30", "rates": { "GBP": 0.87933, "USD": 1.1412 }}

As you can see in this example, in Python terms, it is like a dictionary that includes a smaller dictionary. This can get complicated in other APIs like having also lists and multiple dictionaries - again in Python terms.

**Note:** To preview the JSON output in a readable format, you can use Firefox. By default, Firefox has a built-in JSON viewer that shows JSON in a nice format once you open the URL. In the Firefox JSON viewer, you can also click the tab called "Raw Data" and then the sub-tab "Pretty Print" to see JSON in a view similar to how it is displayed above. Chrome can have the same with extensions. For more complicated tasks, you can download [Postman](https://www.getpostman.com/apps) free app, but for now the Firefox built-in JSON is just enough. So keep it simple for now and let's continue.

## Reading and Parsing the API Output with Python

**1- To handle the API output, you need to import two Python libraries:**

requests (or urllib2 or the like) to connect to the URL.

json to parse the JSON output and extract the data you need.

**2- Connect to the URL as if you are opening it in browser** - figuratively

If you print(response) you will get <Response [200]> which means you are successfully connected.

**3- Read the output:**

Note: At this point, you can try to find out the type of "data" using type(data) and you will get str which means "string". Actually, if you print(data), you will see how it is enclosed with quotes.

**4- Parse JSON - convert the string to JSON:**

Note: You can now try to find out the type of "parsed" using type(parsed) and you will get dict which means "dictionary". If you print(parsed) you will see the quotes is now removed. Be careful, it is "loads" not "load".

You can even have a "pretty print" to make it more readable for you. _This step is not required though._

The output will look like this:

123456789
{ "base": "EUR", "date": "2017-06-30", "rates": { "GBP": 0.87933, "USD": 1.1412 }}

So now, you can deal with it as a regular dictionary.

**5- Extract data:**

If you want to extract "date", just type:

Now you can extract the rate of GBP by accessing the main dictionary "parsed", then sub-dictionary "rates" and finally the key "GBP" to get its value. Be careful, do not forget quotes.

You can extract the rate of USD in the same way:

Then try to print them:

So here is your whole code:

123456789101112131415
import requestsimport jsonurl = "http://api.fixer.io/latest?symbols=USD,GBP"response = requests.get(url)data = response.textparsed = json.loads(data)date = parsed["date"]gbp_rate = parsed["rates"]["GBP"]usd_rate = parsed["rates"]["USD"]print("On " \+ date + " EUR equals " \+ str(gbp_rate) + " GBP")print("On " \+ date + " EUR equals " \+ str(usd_rate) + " USD")

## Get Rates of Other Currencies

You can use this URL to get rate of all the available currencies while the base is USA. Feel free to open it in your browser to see how it looks like. <http://api.fixer.io/latest?base=USD>

As you can see, it is a dictionary including the rates dictionary. So let's extract the rates dictionary:

Try to print it if you like to see how it looks like:

Here is how it looks like:

12
{'AUD': 1.2626, 'BGN': 1.68, 'BRL': 3.1116, 'CAD': 1.2596, 'CHF': 0.94924, 'CNY': 6.7684, 'CZK': 22.348, 'DKK': 6.3879, 'GBP': 0.76971, 'HKD': 7.8081, 'HRK': 6.3657, 'HUF': 262.3, 'IDR': 13312.0, 'ILS': 3.5632, 'INR': 64.339, 'JPY': 111.42, 'KRW': 1118.6, 'MXN': 17.502, 'MYR': 4.2835, 'NOK': 8.0154, 'NZD': 1.3443, 'PHP': 50.701, 'PLN': 3.6389, 'RON': 3.9257, 'RUB': 58.94, 'SEK': 8.2626, 'SGD': 1.3633, 'THB': 33.45, 'TRY': 3.5336, 'ZAR': 12.934, 'EUR': 0.85896}

So now to get the currencies and their rates, you need to iterate the keys and values of this dictionary using items() like this:

Note: In Python 3, you should use items() while in Python 2, you should use iteritems()

You can do it another way:

Our full code will be as follows:

12345678910111213141516
import requestsimport jsonurl = "http://api.fixer.io/latest?base=USD"response = requests.get(url)data = response.textparsed = json.loads(data)date = parsed["date"]print("Date:", date, "\n")rates = parsed["rates"]for currency, rate in rates.items():print(currency, "= USD", rate)

## Changing API URL Parameters

Actually, you can add the parameters in the URL you add to your code. Still, in some cases it helps to do this programmatically, which can be easily done using standard Python concatenation.

For example, instead of having USD as the only base, you can have a list of "base" currencies to iterate them like this:

123456789101112131415
bases = ["USD", "EUR", "GBP"]for base in bases:url = "http://api.fixer.io/latest?base=" \+ baseresponse = requests.get(url) data = response.text parsed = json.loads(data) rates = parsed["rates"]print("\--------------- Rates in", base, "\---------------") for currency, rate in rates.items():print(currency, "=", base, rate)

So that is it for this initial API tutorial, and we going to publish more tutorials on the topic soon.

You can learn more about **APIs and Python** by joining this course for free: [30 Days of Python | Unlock Your Python Potential](http://python.gotrained.com/recommends/30-days-python/) by Justin Mitchel.
