# The MoSCoW Prioritization

_Captured: 2018-04-29 at 11:59 from [egkatzioura.com](https://egkatzioura.com/)_

One of the hardest part when it comes to implement new ideas and features through the lifecycle of a project is making sure that the specific feature or the new framework that will be added, will play an essential part in the project's success.

By implementing features that are hard to implement and are not as essential to the customer, or by adding tools to your stack, which require a certain expertise and time to invest in learning, but its uses are limited for this project, then we risk the project's success and our customer will be unhappy.  
For example one of your business analysts John comes with a brilliant idea which he believes it should be reordered on top of the product backlog. Also one of your top developers Jack might stumble upon a new tool which will help automate the testing process.

Is this new feature that John proposes as great and as essential as it seems for the client? Is the new tool that Jack proposes really needed, so that we will incorporate it in one of our sprint features for our next sprint?

A good and simple way to avoid waste is to use the [MoSCoW](https://en.wikipedia.org/wiki/MoSCoW_method) Prioritization.  
So here's what MoSCow prioritization stands up for

  * **M** : Must have
  * **S** : Should have
  * **C** : Could have
  * **W** : Won't have

**Must have**

Is our final solution useless if we won't ship this specific feature with our product? Are we going to have constant problems through the product's development lifecycle, which will risk its delivery, if we don't use this specific tool?

If the above cases are satisfied then the feature or the non functional requirement is a **must-have** and we should work our way out in order to include them.

**Should have**

Is the feature important but not necessary for the customer to get started? Can we have a workaround if it doesn't meet the delivery date? Is the product delivery not going to be affected if we won't use this tool although it will save us time and effort?

If the above cases are satisfied then the feature or the non functional requirement is a **should-have** and we can find workarounds for that.

**Could have**

Is this feature going to enhance the customer experience but it won't affect the project goal at all if won't get delivered? Will the development process continue to be successful although using that framework will helps us speed things up?

If the above cases are satisfied then the feature or the non functional requirement is a **could-have** and it is not of high importance to have it. However if the must-haves and the could-haves are satisfied there is some real value on implementing them.

**Won't Have**

Is the project scope not effected at all if we won't implement this feature? Is the new tool introduced through our development process not used at all?

If the above cases are satisfied then the feature or the non functional requirement is a **won't-have** and thus you don't have to bother at all.

To sum up since the beginning of the project our main focus is on the **must-have** items. By satisfying them we can move to the **should-have **items. Finally we can tackle the **could-have **items.

All in all this way can helps us avoid waste and keep being efficient on resources needed.

One of the major issues when dealing with large codebases in our teams has to do with artifact sharing and artifact storage.

There are various options out there that provide many features such as [jfrog](https://www.jfrog.com/confluence/display/RTF/Configuring+Repositories), [nexus](https://www.sonatype.com/nexus-repository-sonatype), [archiva](https://archiva.apache.org/index.cgi) etc.

I have been into using them, setting them up and configuring and they certainly provide you with many features. Also having you own repository installation gives you a lot of flexibility. Furthermore docker has made things a lot easier and thus setting them up takes almost no time.

Now if you use a cloud provider like amazon, azure etc there is a more lightweight option and pretty easy to setup. By using a cloud provider such as amazon, azure or google you have cheap and easy access to storage. The storage options that they provide can also be used in order to host your private artifacts or even your public ones.

To do so you need to use a maven wagon which is capable to communicate with the storage options that your cloud provider has and this is exactly what the CloudStorageMaven project deals with.

The [CloudStorageMaven](https://github.com/gkatzioura/CloudStorageMaven) project provides you with wagons interacting with [Amazon S3](https://aws.amazon.com/s3/), [Azure Blob Storage](https://azure.microsoft.com/en-gb/services/storage/blobs/) and [Google Cloud Storage](https://cloud.google.com/storage/).

If you already use one of these cloud services hosting your artificats on them seems like a no brainer and theese wagons make it a lot easier to do so.

I have compiled some tutorials on how to get started with each one of them

Happy coding!

If you use Google Cloud and you use Java for your projects then Google Cloud Storage is a great place to host your teams artifacts.

It is easy to setup and pretty cheap. Also it is much simpler than setting one of the existing repository options (jfrog, nexus, archiva etc) if you are not particularly interested in their features.

To get started you need to specify a maven wagon which supports google cloud storage.  
We will use the [Google storage wagon](https://github.com/gkatzioura/CloudStorageMaven/tree/master/GoogleStorageWagon).

Let's get started by creating a maven project

mvn archetype:generate -DgroupId=com.test.apps -DartifactId=GoogleWagonTest -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

We are going to add a simple service.
    
    
    package com.test.apps;
    
    public class HelloService {
    
        public String sayHello() {
    
            return "Hello";
        }
    }
    

Then we are going to add the maven wagon which will upload and fetch our binaries to the google cloud storage.
    
    
        <build>
            <extensions>
                <extension>
                    <groupId>com.gkatzioura.maven.cloud</groupId>
                    <artifactId>google-storage-wagon</artifactId>
                    <version>1.0</version>
                </extension>
            </extensions>
        </build>
    

Then we shall create the google cloud storage bucket which will host our artifacts.

![](https://cloud.google.com/storage/images/create-bucket.png)

Our bucket shall be called mavenrepository

Now that we have set up our bucket in google we shall set the distribution management on our maven project.
    
    
        <distributionManagement>
            <snapshotRepository>
                <id>my-repo-bucket-snapshot</id>
                <url>gs://mavenrepository/snapshot</url>
            </snapshotRepository>
            <repository>
                <id>my-repo-bucket-release</id>
                <url>gs://mavenrepository/release</url>
            </repository>
        </distributionManagement>
    

From the maven documentation

> Where as the repositories element specifies in the POM the location and manner in which Maven may download remote artifacts for use by the current project, distributionManagement specifies where (and how) this project will get to a remote repository when it is deployed. The repository elements will be used for snapshot distribution if the snapshotRepository is not defined.

The next step is the most crucial and this has to to do with authenticating to google cloud.

You need to have the gcloud command line setup in your system and you must issue a login  
'[gcloud auth login -brief'](https://cloud.google.com/sdk/gcloud/reference/auth/) with an account that has access to the bucket we created previously.  
The other way is to use the GOOGLE_APPLICATION_CREDENTIALS environmental variable. You can use this GOOGLE_APPLICATION_CREDENTIALS in order to set the path to your google application credentials file.  
The credentials file should also be able to access the bucket we created previously.

And now the easiest part which is deploying.

Now since your artifact has been deployed you can use it in another repo by specifying your repository and your wagon.
    
    
        <repositories>
            <repository>
                <id>my-repo-bucket-snapshot</id>
                <url>gs://mavenrepository/snapshot</url>
            </repository>
            <repository>
                <id>my-repo-bucket-release</id>
                <url>gs://mavenrepository/release</url>
            </repository>
        </repositories>
    
        <build>
            <extensions>
                <extension>
                    <groupId>com.gkatzioura.maven.cloud</groupId>
                    <artifactId>google-storage-wagon</artifactId>
                    <version>1.0</version>
                </extension>
            </extensions>
        </build>
    

That's it! Next thing you know, your artifact will be downloaded by maven through google cloud storage and used as a dependency in your new project.

![](https://egkatzioura.files.wordpress.com/2018/04/screen-shot-2018-04-05-at-08-34-31.png?w=906&h=960)

![](https://egkatzioura.files.wordpress.com/2018/04/screenshot-from-2018-04-08-19-34-022-e1523205370927.png)
