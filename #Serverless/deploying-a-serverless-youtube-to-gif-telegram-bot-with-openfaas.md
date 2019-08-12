# Deploying a Serverless Youtube-To-Gif Telegram bot with OpenFaaS

_Captured: 2017-10-04 at 15:08 from [medium.com](https://medium.com/@ericstoekl/deploying-a-serverless-youtube-to-gif-telegram-bot-with-openfaas-2b78d1e9ae6?__s=hptnwhjskozdsnzhgxe6)_

# Deploying a Serverless Youtube-To-Gif Telegram bot with OpenFaaS

Today we'll create a [Telegram](https://telegram.org/) bot which will accept a YouTube URL and send you a gif. To accomplish this, we will deploy this bot with the [OpenFaaS Framework](https://github.com/alexellis/faas). The architecture is as follows:

![](https://cdn-images-1.medium.com/max/1600/1*dxAmvqL8fGuok1oNrby9MQ.png)

> _Because it's running OpenFaaS, you can replace the EC2 instance with any other kind of server imaginable. Raspberry Pi, bare-metal, etc._

When you're done, you'll have this functionality:

![](https://cdn-images-1.medium.com/max/1600/1*P2_Ug5Z5cB4K69blnGKqlg.gif)

> _Create a GIF from any YouTube video_

Let's get started.

### 1\. Create the Telegram Bot

Open a chat with the [BotFather](https://telegram.me/botfather) and send him the `/newbot` message to initiate the bot creation process. After you have created the bot, you will get a token that looks like `110201543:AAHdqTcvCH1vGWJxfSeofSAs0K5PALDsaw` .

### 2\. Deploy OpenFaaS on EC2

It is very simple to deploy the full OpenFaaS platform to an EC2 instance. We will walk through the process step by step.

First, go to the AWS EC2 console and click 'Launch Instance'. On the next page, choose the [Ubuntu AMI](https://aws.amazon.com/marketplace/pp/B01JBL2M0O).

![](https://cdn-images-1.medium.com/max/1600/1*psWAFd3CtIY6TkY8mjnmag.png)

> _Select the 'Ubuntu Server 16.04' AMI_

The default instance type is `t2.micro`, which will work. On the 'Configure Instance' page, open the 'Advanced Details' dropdown. We'll paste the following block of text into the 'User data' text area:
    
    
    #cloud-config  
    repo_update: true  
    repo_upgrade: all  
      
    runcmd:  
     - curl -sSL https://get.docker.com/ | sudo sh  
     - sudo usermod -a -G docker ubuntu  
     - docker swarm init  
     - cd /tmp  
     - git clone -b higherTimeout https://github.com/ericstoekl/faas/  
     - cd ./faas  
     - ./deploy_stack.sh  
     - cd /tmp  
     - curl -sSL https://cli.openfaas.com | sudo sh

Once that's done, it should look like this:

![](https://cdn-images-1.medium.com/max/1600/1*5rOdwnYt62AquUebj_eoTg.png)

Click the 'Next' button until you get the the security groups page. Create a security group that has TCP port 8080 open. Open port 22 as well, because SSH is needed.

![](https://cdn-images-1.medium.com/max/1600/1*5kpMY-3IgIWgOuQBcymh4g.png)

> _OpenFaaS listens on port 8080, so keeping this port open is essential._

Launch the instance and make sure you have the private key that is needed to log in.

Now ssh into the machine with the following command:
    
    
    $ ssh -i <your-key-pair.pem> ubuntu@<your-ec2-public-dns>

The cloud-config file will run each of the commands listed one by one, which may take a few minutes. When it's all done, you should be able to run `faas-cli version` and see the following output:

![](https://cdn-images-1.medium.com/max/1600/1*B0OEkAHipTc780fRuXxbsg.png)

At this point, your OpenFaaS deployment should be up and running. Make sure of it by running `faas-cli list` , and you should get the following type of output:

![](https://cdn-images-1.medium.com/max/1600/1*AELnBuQT-QhflaCLZx4_eA.png)

You can also check that your deployment of OpenFaaS is good-to-go by going to `http://<your-AWS-machine-public-DNS>:8080/`in the web browser from your local machine. You should get a nice UI:

![](https://cdn-images-1.medium.com/max/1600/1*60o3ae-6CPqDSqnjOHQNMQ.png)

> _Pass some markdown to the 'func_markdown' function and hit 'Invoke' to test that your OpenFaaS deployment is up and running_

### 3\. Deploy the core functions of the Youtube-To-Gif Telegram bot on OpenFaaS

The core functions are:

  1. `youtube-dl` -- This is a function that will take a URL of a youtube video as STDIN, and put the raw data of that youtube video (MP4 format) to STDOUT.
  2. `gif-maker` -- This function will take a raw MP4 file in STDIN and send raw data of a GIF file to STDOUT
  3. `telegram-gif-bot` -- This function will receive bot commands from the API Gateway (to be set up next) and pass the commands to the `youtube-dl` and `gif-maker` functions. Essentially a dispatcher, this function uses the [Function Director pattern.](https://github.com/openfaas/faas/blob/master/guide/chaining_functions.md#function-director-pattern) You will need to edit the code of this function to add your Telegram bot API key.

Let's deploy these functions. We'll start by cloning my github repo, which contains a YAML file that `faas-cli` will use to build and deploy the 3 aforementioned functions:
    
    
    ~ $ git clone https://github.com/ericstoekl/tg-youtubegif  
    ~ $ cd tg-youtubegif

Before we deploy these functions, we will need to edit the `telegram-gif-bot` function. Open up the `telegram-gif-bot/handler.js` file, and add you API Key that you got from the BotFather in step 1 in between the quotes of the bolded line:
    
    
    "use strict"
    
    
    var TelegramBot = require('node-telegram-bot-api');
    
    
    **var telegramBotToken = ''; // Add your own here**  
    var telegramBot = new TelegramBot(telegramBotToken, {polling: false});
    
    
    var request = require('request');

Save the file. You're ready to build and deploy these functions, with the following command:
    
    
    ~/tg-youtubegif $ faas-cli build -f tg-youtubegif.yml  
    ~/tg-youtubegif $ faas-cli deploy -f tg-youtubegif.yml

Next, wait for the functions to become active. If you run `docker service ls` , you should see the `youtube-dl` , `gif-maker` , and `telegram-gif-bot` become active when their replica count goes from `0/1` to `1/1` .

Once the functions are finished deploying, test the functionality out by opening a new terminal on your local machine and running the following command:
    
    
    curl <your-AWS-public-DNS>:8080/function/youtube-dl -d "https://www.youtube.com/watch?v=NtgtMQwr3Ko" | curl -X POST <your-AWS-public-DNS>:8080/function/gif-maker --data-binary @- > yt.gif

Now check that the GIF was downloaded successfully:

![](https://cdn-images-1.medium.com/max/1600/1*byiiampNrkl-23NdbDXnGg.gif)

> _If you get a file containing this, congrats, your OpenFaaS deployment works!_

### 4\. Create the API Gateway

Next, we'll create an API Gateway on AWS to act as a reverse-proxy to our OpenFaaS platform.

First hit the "Create API" button in API Gateway:

![](https://cdn-images-1.medium.com/max/1600/1*GCTYCafs81iMqbAZcbyMOA.png)

Name your bot something like `OpenFaas-TgBot` . You don't need to provide a description. After you submit, you will end up with a screen that looks like this:

![](https://cdn-images-1.medium.com/max/1600/1*YCHX183TH4d5lIns6E0uLw.png)

Now we add a `POST` method to the API Gateway. Click the 'Actions' drop-down menu and select 'Post':

![](https://cdn-images-1.medium.com/max/1600/1*vj1D0W-NK1qy0t3HeKNN9Q.png)

> _The Telegram bot will send messages to this gateway through HTTP POST requests_

Then hit the checkmark next to the drop-down, and you will get to the Setup screen. For the 'Endpoint URL' we'll enter in `http://<public-DNS-to-instance>:8080/function/telegram-gif-bot` .

![](https://cdn-images-1.medium.com/max/1600/1*tlbz-KTt0lsh4frHbQ7YMQ.png)

Leave the 'Content Handling' box as 'Passthrough'. Hit 'Save'. Next, click the drop-down menu again (titled 'Actions') and select 'Deploy API'. We'll create a new stage:

![](https://cdn-images-1.medium.com/max/1600/1*Qa4wGBsS_pA315FnC85-YQ.png)

Click 'Deploy', then click on your 'prod' stage. You will be given a URL (note that it is HTTPS, which Telegram requires) which you can use to accept Telegram bot messages.

![](https://cdn-images-1.medium.com/max/1600/1*mFFPGU4CNqCCvhbADqPpBg.png)

Finally, on your local machine, set your Telegram bot to post messages to this API Gateway endpoint:
    
    
    $ curl -XPOST <https://api.telegram.org/bot><YOUR_BOT_API_KEY>/setWebhook\?url\=<YOUR_API_GATEWAY_ENDPOINT>

If all goes well, you will get the following response:
    
    
    {"ok":true,"result":true,"description":"Webhook was set"}

Now, you are ready to test your telegram bot. Open a new chat in Telegram with the bot you created in Step 1, and send it the following URL: <https://www.youtube.com/watch?v=ojvTSRA-O-Y>

![](https://cdn-images-1.medium.com/max/1600/1*VfrUsfQqAbXgNPPjYhzPbA.gif)

> _If you see this result when you paste a YouTube video to your Telegram bot, congratulations!_

### Conclusion

Today we deployed a Telegram bot with the OpenFaaS platform running on a simple AWS deployment. Keep in mind that this is just a simple proof-of-concept, and a real deployment would not use just a single EC2 instance, but rather have auto-scaling functionality so that more instances would automatically be launched with increased load on the service. Something like [faas-rancher](https://github.com/kenfdev/faas-rancher) could be used for this purpose, and there is a blog post with detailed instructions on how to deploy it [here](https://medium.com/cloud-academy-inc/openfaas-on-rancher-684650cc078e).

In any case, if you liked this tutorial, please leave a comment with any and all feedback. Thanks!
