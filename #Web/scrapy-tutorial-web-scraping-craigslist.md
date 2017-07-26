# Scrapy Tutorial: Web Scraping Craigslist

_Captured: 2017-06-13 at 18:09 from [python.gotrained.com](http://python.gotrained.com/scrapy-tutorial-web-scraping-craigslist/?ref=quuu&utm_content=bufferf0293&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

In this Scrapy tutorial, you will learn how to write a Craigslist crawler to scrape [Craigslist](https://newyork.craigslist.org/search/egr)'s "Architecture & Engineering" jobs in New York and store the data to a CSV file.

This tutorial is one lecture of our comprehensive Scrapy online course on Udemy, [Scrapy: Powerful Web Scraping & Crawling with Python](https://www.udemy.com/scrapy-tutorial-web-scraping-with-python/?couponCode=SITE-CRAIGSLIST-TOP)

## **Scrapy Tutorial Getting Started**

As you may already know, Scrapy is one of the most popular and powerful Python scraping frameworks. In this Scrapy tutorial we will explain how to use it on a real-life project, step by step.

### **Scrapy Installation**

You can simply install Scrapy using **pip** with the following command:

If you are on Linux or Mac, you might need to start the command with **sudo** as follows:

This will install all the dependencies as well.

### **Creating a Scrapy Project**

Now, you need to create a Scrapy project. In your Terminal/CMD navigate to the folder in which you want to save your project and then run the following command:

Note that for all Scrapy commands, we start with scrapy followed by the command which is here startproject for creating a new Scrapy project and here it should be followed by the project name which can be anything; we called it "craigslist" just for example.

So typically any Scrapy command will look like this:

### **Creating a Scrapy Spider**

In your Terminal, navigate to the folder of the Scrapy project we have created in the previous step. As we called it _**craigslist**_, the folder would be with the same name and the command should simply be:

After that, create the spider using the genspider command and give it any name you like; here we will call it _**jobs**_. Then, it should be followed by the URL.

### **Editing the Scrapy Spider**

Now, manually navigate to the _**craigslist**_ folder, i.e. the scrapy project. You can see that it is structured as in this screenshot.

For now, we will be concentrating on the spider file, which is here called _**jobs.py**_ - open it in any text editor and you will have the following:

1234567891011 
# -*- coding: utf-8 -*-import scrapyclass JobsSpider(scrapy.Spider):name = "jobs"allowed_domains = ["craigslist.org"]start_urls = ['https://newyork.craigslist.org/search/egr']def parse(self, response):pass

### **Understanding the Scrapy Spider File**

Let's check the parts of the main class of the file automatically generated for our jobs Scrapy spider:

1- name of the spider.

2- allowed_domains the list of the domains that the spider is allowed scrape.

3- start_urls the list of one or more URL(s) with which the spider starts crawling.

4- parse the main function of the spider. Do NOT change its name; however, you may add extra functions if needed.

Warning: Scrapy adds extra _http://_ at the beginning of the URL in start_urls and it also adds a trailing slash. As we here already added https:// while creating the spider, we must delete the extra _http://_. So double-check that the URL(s) in start_urls are correct or the spider will not work.

## **Craigslist Scrapy Spider #1 - Titles**

If you are new to Scrapy, let's start by extracting and retrieving only one element for the sake of clarification. We are just starting with this basic spider as a foundation for more sophisticated spiders in this Scrapy tutorial. This simple spider will only extract job titles.

### Editing the parse() Function

Instead of pass, add this line to the parse() function:

**What does this mean?**

titles is a of text portions extracted based on a rule.

response is simply the whole html source code retrieved from the page. Actually, "response" has a deeper meaning because if you print(response) you will get something like <200 https://newyork.craigslist.org/search/egr> which means "you have managed to connect to this web page"; however, if you print(response.body) you will get the whole source code. Anyhow, when you use XPath expressions to extract HTML nodes, you should directly use response.xpath()

xpath is how we will extract portions of text and it has rules. XPath is a detailed topic and we will dedicate a separate article for it. But generally try to notice the following:

Open the [URL](https://newyork.craigslist.org/search/egr) in your browser, move the cursor on any job title, right-click, and select "Inspect". You can see now the HTML code like this:

So, you want to extract "Chief Engineer" which is the text of an <a> tag, and as you can see this <a> tag has the class "result-title hdrlnk" which can distinguish it from other <a> tags on the web-page.

Let's explain the XPath rule we have:

// means instead of starting from the <html>, just start from the tag that I will specify after it.

/a simply refers to the <a> tag.

[@class="result-title hdrlnk"] that is directly comes after /a means the <a> tag must have this class name in it.

text() refers to the text of the <a> tag, which is"Chief Engineer".

extract() means extract every instance on the web page that follows the same XPath rule into a .

extract_first() if you use it instead of extract() it will extract only the first item in the list.

Now, you can print titles:

Your "basic Scrapy spider" code should now look like this:

123456789101112 
# -*- coding: utf-8 -*-import scrapyclass JobsSpider(scrapy.Spider):name = "jobs"allowed_domains = ["craigslist.org"]start_urls = ['https://newyork.craigslist.org/search/egr']def parse(self, response):titles = response.xpath('//a[@class="result-title hdrlnk"]/text()').extract()print(titles)

### **Running the Scrapy Spider**

Now, move to your Terminal, make sure you are in the root directory of your Scrapy project _**craigslist**_ and run the spider using the following command:

In Terminal, you will get a similar result; it is a including the job titles (the titles can vary from day to day):

[u'Junior/ Mid-Level Architect for Immediate Hire', u'SE BUSCA LLANTERO/ LOOKING FOR TIRE CAR WORKER CON EXPERIENCIA', u'Draftsperson/Detailer', u'Controls/ Instrumentation Engineer', u'Project Manager', u'Tunnel Inspectors - Must be willing to Relocate to Los Angeles', u'Senior Designer - Large Scale', u'Construction Estimator/Project Manager', u'CAD Draftsman/Estimator', u'Project Manager']

As you can see, the result is a list of Unicode strings. So you can loop on them, and yield one title per time in a form of dictionary.

Your "basic Scrapy spider" code should now look like this:

12345678910111213 
# -*- coding: utf-8 -*-import scrapyclass JobsSpider(scrapy.Spider):name = "jobs"allowed_domains = ["craigslist.org"]start_urls = ['https://newyork.craigslist.org/search/egr']def parse(self, response):titles = response.xpath('//a[@class="result-title hdrlnk"]/text()').extract()for title in titles:yield {'Title': title}

### **Storing the Scraped Data to CSV**

You can now run your spider and store the output data into CSV, JSON or XML. To store the data into CSV, run the following command in Terminal. The result will be a CSV file called result-titles.csv in your Scrapy spider directory.

Your Terminal should show you a similar result, which indicates success

'item_scraped_count' refers to the number of titles scraped from the page. 'log_count/DEBUG' and 'log_count/INFO' are okay; however, if you received 'log_count/ERROR' you should find out which errors you get during scraping are fix your code.

In Terminal, you will notice debug messages like:

The status code 200 means the request has succeeded. Also, 'downloader/response_status_count/200' tells you how many requests succeeded. There are many other [status codes](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) with different meanings; however, in web scraping they could act as a defense mechanism against web scraping.

## **Craigslist Scrapy Spider #2 - One Page**

In the second part of this Scrapy tutorial, we will scrape the details of Craigslist's "Architecture & Engineering" jobs in New York. For now, you will start by only one page. In the third part of the tutorial, you will learn how to navigate to next pages.

Before starting this Scrapy exercise, it is very important to understand the main approach:

### **The Secret: Wrapper**

In the first part of this Scrapy tutorial, we extracted titles only. However, if you want to scrape several details about each job, you will not extract them separately, and then loop on each of them. No! Actually, you scrape the whole "container" or "wrapper" of each job including all the information you need, and then extract pieces of information from each container/wrapper.

To see how this container/wrapper looks like, right-click any job on the [Craigslist's page](https://newyork.craigslist.org/search/egr) and select "Inspect"; you will see this:

As you can see, each result is inside an HTML list <li> tag.

If you expand the <li> tag, you will see this HTML code:

As you can see, the <li> tag includes all the information you need; so you can consider it your "wrapper". Actually, you can even start from the <p> tag which includes the same information you need. The <li> is distinguished by the class "result-row" while the <p> is distinguished by the class "result-info" so each of them is unique, and can be easily distinguished by your XPath expression.

Note: If you are using the same spider from the Basic Scrapy Spider, delete any code under the parse() function, and start over, or just copy the file into the same "spiders" folder and change name ="jobs" in the basic spider to anything else like name = "jobs-titles" and keep the new one name ="jobs" as is.

### **Extracting All Wrappers**

As we agreed, you first need to scrape all the wrappers from the page. So under the parse() function, write the following:

Note that here you will not use extract() because it is the wrapper from which you will extract other HTML nodes.

### **Extracting Job Titles**

You can extract the job titles from the wrappers using a for loop as follows:

The first observation is that in the for loop, you do not use "response" (which you already used to extract the wrapper). Instead, you use the wrapper selector which are referred to as "job".

Also, as you can see, we started the XPath expression of "jobs" by // meaning it starts from <html> until this <p> whose class name is "result-info".

However, we started the XPath expression of "title" without any slashes, because it complements or depends on the XPath expression of the job wrapper. If you rather want to use slashes, you will have to precede it with a dot to refer to the current node as follows:

As we explained in the first part of this Scrapy tutorial, a refers to the first <a> tag inside the <p> tag, and text() refers to the text inside the <a> tag which is the job title.

Here, we are using extract_first() because in each iteration of the loop, we are in a wrapper with only one job.

What is the difference between the above code and what we had in the first part of the tutorial? So far, this will give the same result. However, as you want to extract and yield more than one element from the wrapper, this approach is more straightforward because now, you can extract other elements like the address and URL of each job.

### **Extracting Job Addresses and URLs**

You can extract the job address and URL from the wrappers using the same for loop as follows:

To extract the job address, you refer to the <span> tag whose class name is "result-meta" and then the <span> tag whose class name is "result-hood" and then the text() in it. The address is between brackets like (Brooklyn); so if you want to delete them, you can use string slicing [2:-1]. However, this string slicing will not work if there is no address (which is the case for some jobs) because the value will be None which is not a string! So you have to add empty quotes inside extract_first("") which means if there is no result, the result is "".

To extract the job URL, you refer to the <a> tag and the value of the href attribute, which is the URL. Yes, @ means an attribute.

However, this is a relative URL, which looks like: /brk/egr/6112478644.html so, to get the absolute URL to be able to use it later, you can either use Python concatenation as follows:

Note: Concatenation is another case in which you need to add quotes to extract_first("") because concatenation works only on strings and cannot work on None values.

Otherwise, you can simply use the urljoin() method, which builds a full absolute URL:

Finally, yield your data using a dictionary:

### **Running the Spider and Storing Data**

Just as we did in the first part of this Scrapy tutorial, you can use this command to run your spider and store the scraped data to a CSV file.

## **Craigslist Scrapy Spider #3 - Multiple Pages**

To do the same for all the result pages of Craigslist's Architecture & Engineering jobs, you need to extract the "next" URLs and then apply the same parse() function on them.

### **Extracting Next URLs**

To extract the "next" URLs, right-click the one in the first page, and "Inspect" it. Here is how the HTML code looks like:

So here is the code you need. Be careful! You should now get out of the for loop.

Note that the next URL is in an <a> tag whose class name is "button next". You need to extract the value of the attribute href so that is why you should use @href

Just as you did in the previous part of this Scrapy tutorial, you need to extract the absolute next url using the urljoin() method.

Finally, yield the Request() method with the absolute_next_url and this requires a callback function, which means a function to apply on this URL; in this case, it is the same parse() function which extracts the titles, addresses and URLs of jobs from each page. Note that in the case the parse() function is the callback, you can delete this callback=self.parse because the parse() function is a callback by default, even if you do not explicitly state that.

Of course, you must import the Request method before using it:

### **Running the Spider and Storing Data**

Again, just as we did in the first and second parts of this Scrapy tutorial, you can run your spider and save the scraped data to a CSV file using this command:

## **Craigslist Scrapy Spider #4 - Job Descriptions**

In this spider, we will open the URL of each job and scrape its description. The code we wrote so far will change; so if you like, you can copy the file into the same "spiders" folder, and change the spider name of the previous one to be something like name = "jobsall" and you can keep the new file name ="jobs" as is.

### **Passing the Data to a Second Function**

In the parse() function, we had the following yield in the for loop:

We yielded the data at this stage because we were scraping the details of each job from one page, but now you need to create a new function called for example parse_page() to open the URL of each job and scrape the job description from each job dedicated page; so you have to pass the URL of the job from the parse() function to the parse_page() function in a callback using the Request() method as follows:

What about the data you have already extracted? You need to pass those values of titles and addresses from the parse() function to the parse_page() function as well, using meta in a dictionary as follows:

### **Function to Extract Job Descriptions**

So the parse_page() function will be as follows:

123456789 
def parse_page(self, response):url = response.meta.get('URL')title = response.meta.get('Title')address = response.meta.get('Address')description = "".join(line for line in response.xpath('//*[@id="postingbody"]/text()').extract())yield{'URL': url, 'Title': title, 'Address':address, 'Description':description}

Here, you should deal with meta as a dictionary and assign each value to a new variable. To get the value of each key in the dictionary, you can use the Python's dictionary get() method as usual.

Otherwise, you can use the other way around by adding the new value "description" to the meta dictionary and then simply yield meta to retrieve all the data as follows:

Note that a job description might be in more than one paragraph; so we used join() to merge them.

Now, we can also extract "compensation" and "employment type". They are in a <p> tag whose class name is "attrgroup" and then each of them is in a <span> tag, but with no class or id to distinguish them.

So we can use span[1] and span[2] to refer to the first <span> tag of "compensation" and the second <span> tag of "employment type" respectively.

Actually, this is the same as if you use list slicing. In this case, you will use extract() not extract_first() and follow the expression with [0] or [1] which can be added directly after the expression as shown below or even after extract(). Note that in the previous way, we counted the tags from [1] while in this way, we are counting from [0] just as any list.

### **Storing Scrapy Output Data to CSV, XML or JSON**

You can run the spider and save the scraped data to either CSV, XML or JSON as follows:

## **Editing Scrapy settings.py**

In the same Scrapy project folder, you can find a file called **_settings.py_** which includes several options you can use. Let's explain a couple of regularly used options. Note that sometimes the option is already in the file and you have just to uncomment it, and sometimes you have to add it yourself.

### **Arranging Scrapy Output CSV Columns**

As you might noticed by now, Scrapy does not arrange the CSV columns in the same order of your dictionary.

Open the file _settings.py_ found in the Scrapy project folder and add this line; it will give you the order you need:

Note: If your run the command of generating the CSV again, make sure you first delete the current CSV file or it will add the new output at the end of the current one.

### **Setting a User Agent**

If you are using a regular browser to navigate a website, your web browser will send what is known as a "User Agent" for every page you access. So it is recommended to use the Scrapy _**USER_AGENT**_ option while web scraping to make it look more natural. The option is already in Scrapy _settings.py_ so you can enable it by deleting the # sign.

You can find lists of user agents online; select a recent one for [Chrome](http://www.useragentstring.com/pages/useragentstring.php?name=Chrome) or [Firefox](http://www.useragentstring.com/pages/useragentstring.php?name=Firefox). You can even check [your own user agent](http://www.whoishostingthis.com/tools/user-agent/); however, it is not required to use the same one in Scrapy.

Here is an example:

### **Setting Scrapy DOWNLOAD_DELAY**

The option DOWNLOAD_DELAY is already there in Scrapy settings.py so you can just enable it by deleting the # sign. According to Scrapy documentation, "this can be used to throttle the crawling speed to avoid hitting servers too hard."

You can see that the offered number is 3 seconds; however, you can make them less or more. Still, this makes sense because there is another option that is activated by default which is RANDOMIZE_DOWNLOAD_DELAY and it is set from 0.5 to 1.5 seconds.

## Final Scrapy Tutorial Spider Code

So the whole code of this Scrapy tutorial is as follows. Try it yourself; if you have questions, feel free to send a comment.

## **Craigslist Scrapy Tutorial on GitHub**

You can also find all the spiders we explained in this Python Scrapy tutorial on GitHub ([Craigslist Scraper](https://github.com/GoTrained/Scrapy-Craigslist/)).
