# Understanding API Design

_Captured: 2017-10-05 at 15:52 from [dzone.com](https://dzone.com/articles/understanding-api-design?edition=329519&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-10-05)_

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

## Designing APIs

**Objectives:**

  * Describe REST API architecture.

  * Describe the API development lifecycle.

  * Translate functional requirements for APIs into resources and HTTP methods.

  * Navigate Anypoint Platform.

**Types of API:**

  1. RAML

  2. SOAP

  3. RPC

![Image title](https://dzone.com/storage/temp/6693937-capture14.png)

**Objectives:**

  * Describe the common web API formats including SOAP, RPC, and REST.

  * Describe REST API architecture.

  * List the rules for retaining REST principles in APIs.

  * Describe the design-first approach for REST APIs.

### Call a SOAP API

Here, you will explore and understand a SOAP API. You will:

  1. Examine an example SOAP API.

  2. Make a call to a SOAP API endpoint to retrieve information. 

![Image title](https://dzone.com/storage/temp/6693948-capture14.png)

> _Examine the Airline Information SOAP API._

  1. Return to the course snippets.txt file.

  2. Copy the URL for the SOAP API: http://www.webservicex.net/new/Home/Index.

  3. In a web browser, navigate to that URL.

  4. In the Webservices Directory, click Standards and Lookup Data.

![Image title](https://dzone.com/storage/temp/6693949-capture15.png)

> _5. In the list of Webservices by category, click the Airport Information Webservice._

![Image title](https://dzone.com/storage/temp/6693970-capture16.png)

> _View the Airport Information Webservice endpoint WSDL._

6\. In the Airport Information Webservice Detail page, copy the link specified for the Endpoint.

![Image title](https://dzone.com/storage/temp/6693993-capture17.png)

> _7. In a new tab in the web browser, navigate to the endpoint URL._

8\. Locate the operations and HTTP methods supported by the web service.

![Image title](https://dzone.com/storage/temp/6700890-screen-shot-2017-09-25-at-120353-pm.png)

> _Make a call to retrieve data from an Airport Information Webservice operation._

9\. Go back to the Airport Information Webservice Detail page.

10\. In the list of operations under Demo, click getAirportInformationByAirportCode.

![Image title](https://dzone.com/storage/temp/6694035-capture19.png)

> _11. In the Test parameter dialog box, type the airportCode parameter value as LHR._

12\. Click Invoke.

![Image title](https://dzone.com/storage/temp/6694043-capture19.png)

13\. Verify that a new tab opens that displays the response received from the SOAP web service  
operation.

![Image title](https://dzone.com/storage/temp/6694054-capture20.png)

> _14. Copy the content after the horizontal line in the response web page._

15\. Return to the course snippets.txt file and copy the URL for the Web Toolkit Online:  
http://www.webtoolkitonline.com/xml-formatter.html.

16\. In a new tab in the web browser, navigate to that URL.

17\. Paste the content in the XML Content area.

18\. Click "format."

![Image title](https://dzone.com/storage/temp/6694071-capture21.png)

### Make a Call to an RPC API

You will examine the Slack RPC API and make a call to an RPC endpoint.

![Image title](https://dzone.com/storage/temp/6694098-capture21.png)

Examine the Slack Web API:  
1\. In a web browser, navigate to https://api.slack.com/web. Note: This URL is also located in the course snippets.txt file.

![Image title](https://dzone.com/storage/temp/6694104-capture22.png)

> _2. Click the HTTP RPC style methods link in the middle of the page._

3\. Scroll down to the list of methods that describe the actions that can be performed with the  
channels.

4\. Click the channels.list method.

![Image title](https://dzone.com/storage/temp/6694110-capture23.png)

5\. View the documentation for the channels.list method with the arguments and response  
information.

![Image title](https://dzone.com/storage/temp/6694130-capture24.png)

Make a call to an endpoint.

6\. Scroll back up and click the Tester tab.

![Image title](https://dzone.com/storage/temp/6694150-capture25.png)

7\. In the Tester, select the No token or Invalid token option for the token attribute and click the  
Test Method button.

![Image title](https://dzone.com/storage/temp/6695826-capture26.png)

8\. Verify that you see the response as not authorized or invalid authorization.

![Image title](https://dzone.com/storage/temp/6695828-capture27.png)

Note: To obtain a valid token, you need a Slack account and to belong to an organization with  
channels and members. If you do have an account, you can generate tokens by following the  
information in the link below the token attribute value in the tester.

### Make a Call to a REST API

Here, you will explore a REST API. You will:

  1. Examine the Vimeo REST API.

  2. Make a call to a REST API endpoint to retrieve information.

![Image title](https://dzone.com/storage/temp/6695831-capture28.png)

> _Examine the Vimeo REST API._

1\. In a web browser, navigate to https://developer.vimeo.com/api.

Note: This URL is also located in the course snippets.txt file.

![Image title](https://dzone.com/storage/temp/6695840-capture29.png)

> _2. In the left navigation bar, click Playground._

3\. On the API/Playground page, click (Empty…) on the left-hand side.

![Image title](https://dzone.com/storage/temp/6695850-capture30.png)

> _4. In the expanded list of resources, click categories._

5\. Click the Make Call button.

6\. Verify the response has a status code 200.

7\. Scroll the page and view the data for the Animation and Arts & Design categories.

![Image title](https://dzone.com/storage/temp/6696121-capture34.png)

### Translating Functional Requirements for APIs

**Objectives:**

  * Identify the different categories and actions for REST APIs.

  * Convert categories to resources.

  * Select HTTP methods to support the actions on categories.

  * List the categories and actions for an API.

In this walkthrough, you list out the functional requirements for an API. You will:

  * Identify the categories for a REST API.

  * Define actions for the categories to decide how users will consume the API.

List categories:

1\. Create User functionality text file, add the following categories:

  * CUSTOMERS

  * ACCOUNTS

  * TRANSACTIONS

List detailed actions:

2\. In the User functionality text file, add a detailed list of actions that developers should be  
able to perform with the API for each of the categories.

CUSTOMERS -

  1. Get a list of all customers in the bank.

  2. Get customer information for a specific customer ID.

  3. Register a new customer.

  4. Update customer information for a specific customer ID.

  5. Delete a customer with a specific customer ID.

ACCOUNTS -

  1. Get a list of all accounts for a specific customer ID.

  2. Get account information for a specific account ID.

  3. Create a new account.

  4. Update account information for a specific account ID.

  5. Delete an account with a specific account ID.

TRANSACTIONS -

  1. Get transactions for a specific account ID.

  2. Get transaction information for a specific transaction ID.

  3. Create a new transaction.

Save the file.

### **Translate Categories and Actions Into Resources and Methods**

**Specify Resources:**  
CUSTOMERS: Resource /customers

  1. Get a list of all customers - Resource /customers

  2. Register a new customer - Resource /customers

  3. Get customer information for a specific customer ID - Resource  
/customers/{customer_id}

  4. Update customer information for a customer ID - Resource  
/customers/{customer_id}

  5. Delete a customer with a specific customer ID - Resource  
/customers/{customer_id}

ACCOUNTS: Resource /accounts

  1. Get list of all accounts for a specific customer ID - Resource  
/customers/{customer_id}/accounts

  2. Create a new account - Resource /accounts

  3. Get account information for a specific account ID - Resource  
/accounts/{account_id}

  4. Delete an account with a specific account ID - Resource  
/accounts/{account_id}

  5. Update account information for a specific account ID - Resource  
/accounts/{account_id}

Specify resources for the Transactions entity.

TRANSACTIONS: Resource /transactions

  1. Create a new transaction - Resource /transactions

  2. Get transactions for a specific account ID - Resource  
/accounts/{account_id}/transactions

  3. Get transaction information for a specific transaction ID - Resource  
/transactions/{transaction_id}

Specify HTTP methods for the actions

7\. Specify methods for the identified resources.

  * Get list of all customers - Method GET

  * Register a new customer - Method POST

  * Get customer information for a specific customer ID - Method GET

  * Update customer information for a customer ID - Method PATCH

  * Delete a customer with a specific customer ID - Method DELETE

  * Get list of all accounts for a specific customer ID - Method GET

  * Create a new account - Method POST

  * Get account information for a specific account ID - Method GET

  * Delete an account with a specific account ID - Method DELETE

  * Update account information for a specific account ID - Method PUT

  * Create a new transaction - Method POST

  * Get transactions for a specific account ID - Method GET

  * Get transaction information for a specific transaction ID - Method GET

8\. Save the text file.

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Topics:

mulesoft ,soap api ,rest api ,api design ,api ,integration ,anypoint platform

Opinions expressed by DZone contributors are their own.
