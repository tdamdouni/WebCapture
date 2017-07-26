# Five Steps to Determine Whether an App Can Be Containerized

_Captured: 2017-05-23 at 03:47 from [dzone.com](https://dzone.com/articles/five-steps-to-determine-whether-an-app-can-be-containerized?edition=299094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-22)_

Deploy and scale data-rich applications in minutes and with [ease](https://dzone.com/go?i=207139&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dcloud%26utm_term%3Dpre-article%26utm_content%3D1003). [Mesosphere DC/OS](https://dzone.com/go?i=207139&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dcloud%26utm_term%3Dpre-article%26utm_content%3D1003%2522) includes everything you need to elastically run [containerized apps](https://dzone.com/go?i=207139&u=https%3A%2F%2Fmesosphere.com%2Fsolutions%2Fcontainer-orchestration%2F%3Futm_source%3Ddzone%26utm_medium%3Dcloud%26utm_term%3Dpre-article%26utm_content%3D1003) and [data services](https://dzone.com/go?i=207139&u=https%3A%2F%2Fmesosphere.com%2Fsolutions%2Fdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dcloud%26utm_term%3Dpre-article%26utm_content%3D1003) in production.

Containers have become an incredibly popular technology in recent years. The portability and simplicity of deployment they introduced, combined with their natural fit for microservice applications, have made containers the logical foundation for net new applications. But did you know that containers can provide even more benefits to your legacy applications?

Containers provide significant resource efficiencies compared to running applications directly on servers. Switching to a container-based deployment allows you to consolidate more applications onto a server compared to VMs by removing the need for the OS along with the cost of the OS license. Using bare metal servers or VMs instead of containers for a single app is like paying for a large house for a single person -- including all of the mortgage, maintenance, and real estate tax expenses -- when you could be just as happy living in a studio apartment at a fraction of the cost.

If you are looking to unlock greater efficiencies and reduce the cost of operating your existing infrastructure, evaluate which applications can be migrated to container-based deployments. To assist you, below are [five steps](https://mesosphere.com/blog/2017/04/17/five-steps-you-can-use-to-determine-if-an-existing-app-can-be-containerized/) you can use to see if they are good candidates for containerization.

## 1\. Is the App Pre-Packaged as a Single Binary or JAR File?

Take a look at the application and check if it's already a single binary or a JAR file. If it is, it's easy to containerize it. Java apps and JAR files are especially flexible and can be easily converted. Plus, containerized Java has a further advantage of carrying their specific JRE environment inside the container, which makes for simpler deployment. It also means many different versions of Java runtimes can be run side-by-side on the same servers because of the isolation containers provide.

## 2\. Is the Platform on Which Your App Is Built Available in a Containerized Version or Package Yet?

Platforms like Tomcat, Node.js, Drupal, Joomla, and many others are already available as Docker containers. Many vendors or open source communities have already done the work for you to convert your app to a containerized environment. Take an inventory of internally developed applications and check if they are using software that are already available in this way. If so, extract the application configuration, download a containerized version of the platform, and tune the same configuration to run in that version. Once it works, you can re-deploy it in a much less expensive configuration in a shared cluster.

## 3\. Are Any of Your Third-Party Apps Available in a Container Version Yet?

Vendors see the benefits of developing their software on containers, and many are starting to offer containerized versions of their commercial software. Many infrastructure servers in datacenters fall into this category, such as vendors Hitachi providing their SAN management software on containers in addition to full-server versions. Just ask your vendors to see if they offer one and make use of it if they do.

## 4\. Is the App Stateless?

Applications are stateless if they merely store configuration information locally besides a temporary cache on the server, rather than having a local data store of persistent data. Many web applications that use a backend for persistence and have tiers that just perform processing are good targets, especially ones based on Tomcat or other web frontends. If stateless tiers of an application can be peeled off, they are good candidates for containerization because they gain a lot of flexibility beyond being able to run them at higher density.

Among the benefits are simpler backups and easier config changes to the app, since they can be rolled out as new instances replacing the old ones as they are pushed out. Note that stateful apps are still within reach since storage tools like [ceph](http://ceph.com/), [Portworx](https://portworx.com/), and [Rex-Ray](https://github.com/codedellemc/rexray) can also give state to containers; they simply take a few more steps to containerize and are better targets for a later phase.

## 5\. Is Your Application Already Part of Continuous Integration/Continuous Deployment Pipeline?

If you already have applications that are part of a DevOps and CI/CD process, it might be easier for you to migrate to containers. You can start packaging your applications in containers and deploying them into existing servers. Once you are confident that your application is working correctly, you can start introducing container orchestration platforms and start realizing other benefits such as resilience and efficiency.

Your internal developers might already be developing applications on containers but deploying them on full servers instead. If you work with your developers to modify their existing CI/CD pipeline, you can achieve a much more efficient infrastructure. The benefits include a more resilient application and a CI/CD pipeline that extends all the way to the production environment. Also, containers make it easy to automate the testing and deployment of new code, and even roll back code that isn't working properly. This is especially useful for agile development shops that want to put code out faster, and with less friction.

Discover new technologies simplifying running containers and data services in production with this [free eBook by O'Reilly](https://dzone.com/go?i=213224&u=https%3A%2F%2Fmesosphere.com%2Fresources%2Fguide-build-run-modern-data-driven-apps%2F%3Futm_source%3Ddzone%26utm_medium%3Dcloud%26utm_campaign%3Dmodern_data_driven_apps%26utm_term%3Dpost-article%26utm_content%3D2004). Courtesy of [Mesosphere](https://dzone.com/go?i=213224&u=https%3A%2F%2Fmesosphere.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dcloud%26utm_term%3Dpost-article%26utm_content%3D2004).
