# Load Balancing Using web.xml

_Captured: 2017-04-28 at 22:09 from [dzone.com](https://dzone.com/articles/load-balancing-using-webxml?oid=twitter&utm_content=buffer1e69a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

If you are wondering how you can test the performance of your newly developed application in a production environment, then probably you have to create a replica -- which is not feasible in most of the cases. By following some simple tricks, you can create a production-like environment in your dev set-up only. A major restriction is the SSL, networking, load balancing, and clustering of the server for creating the replica of the production environment. Today, I would be telling you how to create a load balancing application in your dev environment using just `web.xml`.

[Here's my reference from the Oracle site](https://docs.oracle.com/cd/E13222_01/wls/docs61/adminguide/http_proxy_cluster.html).

Create a dynamic web project in your IDE and place the below code in `web.xml`:

Creat the WAR and deploy it into a new managed server that is not pointing to any of the clusters. Add the URLs of the managed servers for which you wish to use for the load balancing: `<param-value>localhost:7002|localhost:7003</param-value>`.

Access your application with the port number of the deployed load balancing application and you will get the required result. And you're done!
