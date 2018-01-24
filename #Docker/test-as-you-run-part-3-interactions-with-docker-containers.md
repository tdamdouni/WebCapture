# Test as you run (Part 3) – Interactions with Docker Containers

_Captured: 2018-01-03 at 16:25 from [blogs.itemis.com](https://blogs.itemis.com/en/test-as-you-run-part-3-interactions-with-docker-containers)_

In the [previous part](https://blogs.itemis.com/en/test-as-you-run-part-2-testing-with-database-mocks) of this series about test-driven development of microservices we tested our system with mocks of different sizes. This is the third part.

The first can be found [here](https://blogs.itemis.com/en/test-as-you-run-part-1).

Let's check that interactions with a real database work.

Please checkout the next step:

`git checkout step4`

Looking into the root build.gradle, we can see that the [Docker-compose](https://medium.com/r/?url=https%3A%2F%2Fgithub.com%2Favast%2Fgradle-docker-compose-plugin) Gradle-plugin was added to the buildscript classpath:

`classpath 'com.avast.gradle:gradle-docker-compose-plugin:0.6.6'`

This plugin allows us to utilize [Docker-compose](https://medium.com/r/?url=https%3A%2F%2Fdocs.docker.com%2Fcompose%2F) for orchestration of [Docker](https://medium.com/r/?url=https%3A%2F%2Fdocs.docker.com%2F)containers. Looking into the build.gradle of the UserService we see that some things have changed:

apply from: '../service.gradle'

dependencies {

compile 'com.datastax.cassandra:cassandra-driver-core:3.3.0'

compile 'io.netty:netty-all:4.1.6.Final'

compile 'org.springframework.data:spring-data-cassandra'

compile 'org.springframework.boot:spring-boot-configuration-processor'

testCompile 'org.cassandraunit:cassandra-unit-spring:3.3.0.2'

}

task bootRunDebugWithCassandra(type: org.springframework.boot.gradle.run.BootRunTask) {

group = 'Application'

doFirst() {

main = project.mainClassName

classpath = sourceSets.main.runtimeClasspath

def serviceinfos = dockerCompose.debugWithCassandra.servicesInfos

def cassandrainfos = serviceinfos.cassandra

def cassandrahost = cassandrainfos.firstContainer.inspection.NetworkSettings.Networks.entrySet().iterator().next().getValue().IPAddress

def cassandraport = cassandrainfos.ports[9042]

environment 'cassandra.host', cassandrahost + ',' + cassandrainfos.host

environment 'cassandra.port', cassandraport

environment 'cassandra.keyspace', 'test'

}

}

apply plugin: 'docker-compose'

dockerCompose {

debugWithCassandra {

useComposeFiles = ['docker-compose-debug.yml']

isRequiredBy(this.tasks.getByName('bootRunDebugWithCassandra'))

}

}

We can see that a task is defined in lines 10-25 and we will have a look on the task in a moment, but first let's have a look at the lines 27-36.

At first the Docker-compose plugin is applied. Following this a custom dockerCompose-Task is created named "debugWithCassandra" with the docker-compose file "docker-compose-debug.yml".

The task is set as a requirement for the custom task defined above, therefore the Docker-containers will be up and running before the custom tasks get executed.

The Docker-compose file is located in the project and contains the following definitions:

`version: '3'  
`services:  
cassandra:  
image: spotify/cassandra:latest  
ports:  
\- 9042

In that file a container named "cassandra" is defined using the Spotify Cassandra image and the containers port 9042 is exposed to the host system.

Now let's have a look at the custom task "bootRunDebugWithCassandra":

This task is a special version of the [bootRun](https://docs.spring.io/spring-boot/docs/current/reference/html/build-tool-plugins-gradle-plugin.html#build-tool-plugins-gradle-running-applications) task provided by the Gradle- Spring-plugin, therefore the task will start the Spring-boot-application.

The lines 12, 14 and 15 are just default definitions necessary to start the Spring application, so let's have a look at the lines 17-24:  
We use the Docker-compose plugin to get the IP-Address of the cassandra-container as well as the port and write these information as well as a keyspacename into the environment (lines 22-24).

Since we define these lines to be executed directly before the actual task get's executed the UserService will be started with the environment variables in place.

All these things may sound a little bit confusing, therefore here's a little sum up:

  1. The bootRunDebugWithCassandra-task get's called
  2. since the Docker-compose-task is required by this task it gets executed before the actual bootRunDebugWithCassandra-task and starts all the docker-container defined in the provided docker-compose file (which in our case is just the cassandra container)
  3. the IP-Address as well as the port are read from the docker container and together with a keyspace name written into the enviroment
  4. the actual bootRunDebugWithCassandra-task is executed and the server is started with the environment variables in place

That's quite awesome right?

## **How does this help me?**

By using these settings it becomes incredibly easy to start or even debug our UserServer with a Cassandra in place.

To do so, we [add a run configuration in Intellij Idea](https://www.jetbrains.com/help/idea/creating-and-editing-run-debug-configurations.html):

  * We click on our Run/Debug configurations  
-> the green plus   
-> Gradle
  * Give it a name (for example "userServiceWithCassandra")
  * select the UserService project
  * select the bootRunDebugWithCassandra task
  * set the checkmark for "Single instance only"

The configuration should look like this:

![user-service-cassandra-configuration.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/user-service-cassandra-configuration.png?t=1514992779618&width=2172&height=1488&name=user-service-cassandra-configuration.png)

  * press apply and close the window

Know by clicking either the run or the debug button the Gradle bootRunDebugWithCassandra-task get's executed as described above therefore the UserService will be started with a Cassandra all the necessary information in place.

## **Let's give it a try!**

We run the application by just pressing the debug button and have a look into the console log in Intellij. We can see that everything described above happens:

  * The Cassandra-Docker-image get's pulled if not already available on the system
  * a Cassandra container get's created
  * the UserService is started with the database in place

Now we can play a little bit with the Service.

To do so, we use [Postman](https://www.getpostman.com/). Within the git repository you will find the Postman file **test_as_you_run.postman_collection.json** in which requests for the UserService and the CapitalizeService are defined.

Let's create the three Users bruce wayne, martha wayne, and thomas wayne by using Postman:

![Users-Postman.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/Users-Postman.png?t=1514992779618&width=2172&height=1026&name=Users-Postman.png)

This window shows how to use the createuser endpoint with the defined body values to create the User bruce wayne. By clicking the send Button the request is executed.

After adding bruce, thomas and martha, we can check the getusersbylastname endpoint to check whether the users are stored.

![getusersbylasname-postman.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/getusersbylasname-postman.png?t=1514992779618&width=2172&height=1527&name=getusersbylasname-postman.png)

So now that we tried out by ourself that the UserService works as expected, lets check the database.

So we open our shell and type:

`docker inspect userservice_cassandra_1 |grep IPAddress`

And we get a result:

`"SecondaryIPAddresses": null,  
` "IPAddress": "",  
"IPAddress": "172.19.0.2",

According to the output the IP-Address of Cassandra running on my machine is **172.19.0.2;** therefore if the IP-Address differs when you try it out change the next command.

We open cqlsh and check the user table:

`cqlsh 172.19.0.2  
`cqlsh> select * from test.users;

The output should look similar to this (ignore the ID-values)

`lastname | id                                 | firstname`

\----------+----------------------------------------------------------------------------+------------------

`   wayne | 3cdef4c0-cab7-11e7-ab08-03b9b3e91691 |     bruce`

`   wayne | 40544560-cab7-11e7-ab08-03b9b3e91691 |    martha`

`   wayne | 432c92b0-cab7-11e7-ab08-03b9b3e91691 |    thomas`

Okay, so we have a Cassandra running on our machine filled with some users by the UserService. Nice!

Let's go further and create a testdata image from this Cassandra. To do so we just create a new image from the running container by running inside of our shell

`docker commit userservice_cassandra_1 usercassandra:latest`

That's all. Now we can stop the UserService and the Cassandra container will automatically get stopped as well.

Let's use this testdata image for an integration test in [part 4](https://blogs.itemis.com/en/test-as-you-run-part-4-production-like-integration-test).
