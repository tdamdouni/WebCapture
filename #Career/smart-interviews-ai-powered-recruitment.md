# Smart Interviews: AI-Powered Recruitment

_Captured: 2017-12-21 at 23:07 from [dzone.com](https://dzone.com/articles/smart-interview-a-new-way-for-recruiting-candidate?edition=347111&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-21)_

Many times, as a recruiter, you'll find both [active and passive candidates](https://business.linkedin.com/talent-solutions/blog/2013/12/recruiting-active-vs-passive-candidates) who fulfill a job description. Some problems arise when the candidate has to go to the office to conduct an interview with the recruiter. The main issues are related to distance and transportation. Also, if we are dealing with a passive candidate who already has a job, conducting an interview is almost impossible. If you _can_ reach them, you need to provide some facilities to proceed with the interview. We provide a solution architecture based on an interactive chatbot. As a recruiter, the chatbot begins with a welcome message using the voice of the Google Translate service and the candidate interacts with the chatbot by voice. Once the interview is finished, an email with a report including the contact data, a sentiment analysis process, a summary, and the transcription is sent to the human recruiter. This system can be developed and deployed allow candidates to take the interview anytime and anywhere.

## **Architecture Description**

In the next figure, we provide a high-level functional description overview.

![Smart Interview Architecture](https://dzone.com/storage/temp/7541309-iris1.png)

> _Smart Interview Architecture_

The idea is to automate the candidate interview process using artificial intelligence technologies. First, we develop a virtual assistant, as shown in the figure above, which is a conversational agent capable of orchestrating the whole interview process. Then, we use different machine learning techniques to build and train models which will be capable of executing the various steps in the figure above. Following is a description of each step in the process, as illustrated above:

  1. The virtual assistant presents the candidate with a web form for capturing name and contact information.

  2. The virtual assistant starts the chat, welcomes candidate to the interview, and proceeds with interview questions via voice and text.

  3. The responses received from the candidate are analyzed to detect the predominant feeling for every response and to generate a bar chart for inclusion within the final interview report.

  4. The responses are also used to build a summary of the interview to be included in the final report.

  5. Upon finishing the interview, the virtual assistant generates the report and sends it via email to the human hiring manager.

The next figure shows the technical description of our system. Next sections provide some creative ways to use and develop the several components we've implemented.

![Smart Interview Technical Description](https://dzone.com/storage/temp/7541329-iris2.png)

> _Smart Interview Technical Description_

We have designed a front-end for the user and a formatted report to be presented as a prototype to the recruiter, as the next figure shows. The next sections correspond with each of the services developed.

![Smart Interview Prototype](https://dzone.com/storage/temp/7541334-iris4.png)

> _Smart Interview Prototype_

### **Speech-to-Text**

For speech to text, we decided to use the [Web Speech API](https://developers.google.com/web/updates/2013/01/Voice-Driven-Web-Apps-Introduction-to-the-Web-Speech-API), which makes it easy to add speech recognition to your web pages. This API allows satisfactory control and flexibility for Chrome version 25 and later.

### **Bot Engine (NLP)**

For the virtual assistant engine, we decide to use [api.ai/DialogFlow](https://dialogflow.com/) to configure all our intents, entities, and so on. Before beginning, you should check out the weather virtual agent tutorial [here](https://dialogflow.com/docs/getting-started/building-your-first-agent). Once you are familiar with concepts like intents, entities, and webhooks, you can design your own bot engine but just with text capabilities. What can we do to provide speech capabilities to our bot? The idea is to use a webhook to fulfill the request and use a cloud function to manipulate each of the intent messages. We are going to explain this in the next section.

### **Text-to-Speech**

We can create a simple Node.js application using the Google's TTS API to convert text to audio and create a response that sends it to DialogFlow and then to the user front-end. The response is sent by a JSON file.
    
    
      var intent = req.body.result.action; 
    
    
      googleTTS(text, 'es', 1)   // speed normal = 1 (default), slow = 0.24, language ‘es’ 
    
    
          res.send(JSON.stringify({ "data": {"facebook": { "attachment": url.replace("https","http") }}, "speech": text}));

Once you've implemented your cloud function, you need to deploy it in order to consume it in DialogFlow. We decide to deploy over [Google Cloud platform](https://cloud.google.com/) using [Firebase ](https://firebase.google.com/)as follows:

First, we need to get the Firebase SDK using the following code into a shell.

Execute the following command to authenticate into Firebase using your Google account linked to Google Cloud.

Then, go to your project directory and execute the following command.

Once all is completed, you'll have a project directory similar to this:

![Image title](https://dzone.com/storage/temp/7542230-iris5.png)

> _Copy the previous Node.js function to the file index.js and deploy your function using:_

If all is going right, then an URL will be provided, similar to:

More information can be found [here](https://firebase.google.com/docs/functions/get-started). Sometimes, you may need to add these variables to your `index.js`:

It's important to note that you need a Google Cloud project configured in order to use this code.

### **Sentiment Analysis**

For sentiment analysis, we decide to use [Google's NLP API](https://cloud.google.com/natural-language/). Here's a [step-by-step guide on how to use the API](https://cloud.google.com/natural-language/docs/reference/rest/).

### Text Summarizer

We designed a summarizer in Python and exposed the service using Django. For the Python summarizer, we used the Python `summy` library:

### **Report Generation**

For report generation, we decided to use a JavaScript library for PDF generation called `[BytescoutPDF.js](http://cdn.bytescout.com/help/BytescoutPDFGeneratorSDKJS/index.html)`. It is a simple library that allows you to configure the report as you desire from the client side.

### **Email Generation**

For sending the email, two server-side libraries are required: `[nodemailer.js](https://nodemailer.com/about/)` and `[body-parser.js](https://www.npmjs.com/package/body-parser)`. The first library is used to configure the SMTP transport layer and send the email. The second library is used to manage attachments and `POST` requests.

And that's it! You just need to connect all components in the middleware in order to manage each task.
