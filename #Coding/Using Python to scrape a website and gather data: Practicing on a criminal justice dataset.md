# Using Python to scrape a website and gather data: Practicing on a criminal justice dataset

_Captured: 2016-04-03 at 13:11 from [journalistsresource.org](http://journalistsresource.org/tip-sheets/research/python-scrape-website-data-criminal-justice)_

![\(cs.lbl.gov\)](http://journalistsresource.org/wp-content/uploads/2015/07/bls-2-325x195.jpg)

> _(cs.lbl.gov)_

Data can make a story. It can be the backbone of an investigation, and it can lead to new insights and new ways of thinking. Unfortunately, the data you want isn't always readily available. It's often on the web, but it isn't always packaged up and available for download. In cases like these, you might want to leverage a technique called _web scraping_ to programmatically gather the data for you.

There are many ways to scrape, many programming languages in which to do it and many tools that can aid with it. (See the _[Data Journalism Handbook](http://datajournalismhandbook.org/1.0/en/getting_data_3.html) _for more.) But here we'll go through how to use the language [Python](https://www.python.org/about/apps/) to perform this task. This will give you a strong sense of the basics and insights into how web pages work. It will challenge you a bit to think about how data is structured.

We recommend that you download the [Anaconda Python distribution](http://continuum.io/downloads) and take a [tutorial](https://wiki.python.org/moin/BeginnersGuide/Programmers) in the basics of the language. If you have no familiarity whatsoever, Codecademy can [get you started](http://www.codecademy.com/en/tracks/python).

In this tip sheet we'll be using the [Polk County [Iowa] Current Inmate Listing site](http://apps2.polkcountyiowa.gov/inmatesontheweb/) as an example. From this site, using a Python script, we'll extract a list of inmates, and for each inmate we'll get some data like race and city of residence. (The entire script we'll walk through is open and stored [here at GitHub](https://gist.github.com/phillipsm/404780e419c49a5b62a8), the most popular online platform for sharing computer code. The code has lots of commentary to help you.)

A web browser is the first tool you should reach for when scraping a website. Most browsers provide a set of HTML inspection tools that help you lift the engine-bay hatch and get a feel for how the page is structured. Access to these tools varies by browser, but the _View Page Source_ option is a mainstay and is usually available when you right click directly on a page.

![Web page source code](http://journalistsresource.org/wp-content/uploads/2015/07/links-source-2.jpg)

> _(Page source of the Polk County Current Inmate Listing page)_

When viewing a page's HTML source, you're looking for patterns in the arrangement of your desired data. You want your values to predictably appear in rows in a <table> or in a set of <div>, <p>, or other common elements. In our example we see that links to inmate details, <a href="Details.aspx?…">, are neatly listed in table rows. This will make for easy scraping.

Now that we have a rough idea of how our values are arranged in the HTML, let's write a script that will extract them. We'll rely on two common Python packages to do the heavy lifting, [Requests](http://docs.python-requests.org/en/latest/) and [Beautiful Soup](http://www.crummy.com/software/BeautifulSoup/). Both of these packages are so popular that you might already have them installed; if not, [install them](https://docs.python.org/2/install/) before you run the code below.

At a high level, our web scraping script does three things: (1) Load the [inmate listing page](http://apps2.polkcountyiowa.gov/inmatesontheweb/) and extract the links to the inmate detail pages; (2) Load each inmate detail page and extract inmate data; (3) Print extracted inmate data and aggregate on race and city of residence.

Let's start coding.

We'll set ourselves up for success by importing requests and BeautifulSoup at the top of our script.

Our first chunk of logic loads the HTML of the inmate listing page using _requests.get(url_to_scrape) _and then parses it using _BeautifulSoup(r.text)_. Once the HTML is parsed, we loop through each row of the _inmatesList_ table and extract the link to the inmate details page. We don't do anything with our link yet, we just add it to a list, _inmates_links_.

We now loop through each inmate detail link in our inmates_links list, and for each one we load its HTML and parse it using the same Requests and BeautifulSoup methods we used previously. Once the inmate details page is parsed, we extract the age, race, sex, name, booking time and city values to a [dictionary](https://docs.python.org/2/tutorial/datastructures.html#dictionaries).

BeautifulSoup's select and findAll methods did the hard work for us -- we just told it where to look in our HTML (using our browser inspection tools above). Each inmate gets a dictionary and all the dictionaries get appended to an _inmates_ list.

inmates = []

for inmate_link in inmates_links[:10]:

r = requests.get(inmate_link)

soup = BeautifulSoup(r.text)

inmate_details = {}

inmate_profile_rows = soup.select("#inmateProfile tr")

inmate_details['age'] = inmate_profile_rows[0].findAll('td')[0].text.strip()

inmate_details['race'] = inmate_profile_rows[3].findAll('td')[0].text.strip()

inmate_details['sex'] = inmate_profile_rows[4].findAll('td')[0].text.strip()

inmate_name_date_rows = soup.select("#inmateNameDate tr")

inmate_details['name'] = inmate_name_date_rows[1].findAll('td')[0].text.strip()

inmate_details['booked_at'] = inmate_name_date_rows[2].findAll('td')[0].text.strip()

inmate_address_container = soup.select("#inmateAddress")

inmate_details['city'] = inmate_address_container[0].text.split('\n')[2].strip()

inmates.append(inmate_details)

time.sleep(1)

We've ended up with a list, _inmates_links_, that contains all of the values. We can print those out, but let's first do some aggregation by looping over the city and races values.

inmate_cities = {}

for inmate in inmates:

if inmate['city'] in inmate_cities: 

inmate_cities[inmate['city']] += 1

else:

inmate_cities[inmate['city']] = 1

print inmate_cities

inmate_races = {}

for inmate in inmates:

if inmate['race'] in inmate_races:

inmate_races[inmate['race']] += 1

else:

inmate_races[inmate['race']] = 1

print inmate_races

Our printed output looks like this in our terminal:

As you can see, the logic to load and parse the HTML is simple thanks to Requests and Beautiful Soup. Most of the effort in web scraping is digging through the HTML source in your browser and figuring out how the data values are arranged. Start simple -- just grab one value and print it out. Once you figure out how to extract one value, you'll often be very close to the rest of the data. One note of caution, though: It's pretty easy to flood a web server with requests when you're scraping. If you're looping through a bunch of links that go to one website, it's polite to wait a second between each request.

The [full web scraping example script is available](https://gist.github.com/phillipsm/404780e419c49a5b62a8) and has been commented on heavily. Copy it. Paste it. Run it. Edit to fit your needs.

Should the Polk County Inmates site change or become unavailable, you can find an archived copy of the inmates list page at <http://perma.cc/2HZR-N38X> and an example of an inmate detail page at <http://perma.cc/RTU7-57DL>.
