# APIs to Control Your API Management

_Captured: 2017-12-01 at 02:33 from [dzone.com](https://dzone.com/articles/apis-to-control-your-api-management?edition=339011&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-11-30)_

In [WSO2 API Cloud](https://wso2.com/api-management/cloud/), everything you do through the web user interface can also be done programmatically via APIs. Detailed API reference can be found in the [API Cloud's Product APIs documentation](https://docs.wso2.com/display/APICloud/Product+APIs).

Today I will show you just a quick example on how you can use Publisher's RESTful APIs to get a list of APIs published (for all other operations you would use a similar approach and simply other REST resources from the API reference).

## **1\. Register Client**

### **1.1. Obtain Your Organization-Qualified ID**

The first thing we need to do is register our API client and obtain the consumer ID and consumer secret values.

The most important piece of information that you need for that is your domain-qualified ID in WSO2 Cloud. This is your email address @ your Organization Key. You can find your Organization Key by clicking **[Organization](https://cloudmgt.cloud.wso2.com/cloudmgt/site/pages/organization.jag)** on the 9-dot menu at the top right of the cloud interface.

For example, in the screenshot below, my **Organization Key** is `wso2dmitry2639`:

![](http://cloudblog.wso2.com/wp-content/files/2017/11/Locate-WSO2-Cloud-organization-key-1024x282.png)

With my email address `dmitry@wso2.com`, this gives me the qualified ID of `dmitry@wso2.com@wso2dmitry2639`.

### **1.2. Create Registration JSON**

This is just a _payload.json_ file that would have the ID that you have just obtained. In my case that would be:

Save that text file as _payload.json_.

### **1.3. Encode Your Credentials**

Now you need to take the qualified ID from step 1.1, add a colon (`:`), add your password and do [Base 64 encoding](https://www.base64encode.org/) for that string. For example, if my password was `P@ssw0rd`, I would have needed to encode `dmitry@wso2.com@wso2dmitry2639:P@ssw0rd` and that would have given me: `ZG1pdHJ5QHdzbzIuY29tQHdzbzJkbWl0cnkyNjM5OlBAc3N3MHJk`

### **1.4. Register the Client**

Now you can just run this curl command in the folder that has your _payload.json_ from step 1.2:  
`curl -X POST -H "Authorization: BasicZG1pdHJ5QHdzbzIuY29tQHdzbzJkbWl0cnkyNjM5OlBAc3N3MHJk" -H "Content-Type: application/json" -d @payload.json https://api.cloud.wso2.com/client-registration/v0.11/register/v0.11/register`

This will give you an output like this:

This response has everything we need: **clientId** is your consumer key and **clientSecret** is your consumer secret.

## 2\. Obtain OAuth Token

### 2.1 Encode Consumer Key and Consumer Secret

Now we need to take the **clientId** and **clientSecret** values, put a colon between them, and base 64 encode that string. In my case, I need to encode `O7buGR5fMVMuNBFF:A3mYNQjHDsXX_T1`.

When I do that, I get `TzdidUdSNWZNVk11TkJGRjpBM21ZTlFqSERzWFhfVDE=`

### 2.2 Find Your Scope

In the documentation page for the method you want to call, find which scope it needs. I just want to use _[Retrieve/Search API_](https://docs.wso2.com/display/APICloud/apidocs/publisher/#!/operations#APICollection#apisGet) and this method requires `apim:api_view` scope.

### 2.3 Request the Ttoken

Now you have everything you need to get the OAuth token. Simply run this (with your own ID, encoded keys, and scope):

`curl -k -d "grant_type=password&username=dmitry@wso2.com@wso2dmitry2639&password=P@ssw0rd&scope=apim:api_view" -H "Authorization: BasicTzdidUdSNWZNVk11TkJGRjpBM21ZTlFqSERzWFhfVDE=" https://gateway.api.cloud.wso2.com/token`

You then get a response like this:

`access_token` is the OAuth key you can use for your calls.

## 3\. Use the APIs

Now you can just take that access token and use it with the API call that you pick from the reference page. In my case, for the token that I got, to get a list of all APIs, I would call:

`curl -k -H "Authorization: Bearer 89c12aab-6f0e-3c3b-8409-d186670ec73c" https://api.cloud.wso2.com/api/am/publisher/v0.11/apis`

I then get a response like this:

For my tutorial, I picked just one simple call to list the APIs. Full reference has dozens of methods that you can use to completely bypass our user interfaces and perform any API management operations programmatically.

Check out [API Cloud's Product APIs documentation ](https://docs.wso2.com/display/APICloud/Product+APIs) and let us know what you think.
