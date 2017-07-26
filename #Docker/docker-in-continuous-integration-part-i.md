# Docker in Continuous Integration: Part I

_Captured: 2017-02-23 at 19:50 from [dzone.com](https://dzone.com/articles/docker-in-continuous-integration-part-1?edition=272883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-23)_

This blog series covers three Docker in Continuous Integration (CI) scenarios. A CI process combined with immutable Docker images expedites delivering software changes. The three scenarios covered in this series are:

  1. Use an existing Docker image.
  2. Build your own Docker image.
  3. Push a Docker image to a registry of your choice.

In this blog, I'll cover the first scenario.

Use an existing Docker image in your CI process with either of the following two options. We'll look at each options, see when to use them, list out steps you should take, and give examples.

  1. Shippable's default Docker image.
  2. Your own custom Docker image.

## Shippable's Default Docker Image

Shippable [supports](http://docs.shippable.com/ci/supported/) nine languages and 14 services across three platforms with 50+ [default Docker images](https://github.com/dry-dock) to support different combinations.

### When to Use This Option

  * Your CI process doesn't use Docker.
  * Shippable's default Docker images fulfills your CI process requirements.

### **Steps**

Specify the language, the version (optional), and the service (optional) that you need in the `shippable.yml` file. Based on your input, the platform automatically chooses the best default image for your CI process.

Sample `shippable.yml`:

### Example

Use this [tutorial](http://blog.shippable.com/get-started-with-continuous-integration-for-nodejs-app) to run Continuous Integration for a simple Node.js application. This example pulls a default Node.JS Docker image for the CI process.

## Your Own Custom Docker Image

Specify your private Docker image to run your build. Shippable will start the build container from your Docker image and run the CI process.

### **When to Use This Option**

  * Override Shippable's default image with your own custom Docker image.
  * Set specific options for booting up the default build container for the CI process.

Sample `shippable.yml`:

### Example

  1. Follow along by forking this [Node.js sample application (sample_nodejs)](https://github.com/shippableSamples/sample_nodejs), available for free on GitHub. Alternatively, follow along based on your own repo. If you have never used Shippable, take 30 minutes to complete the [getting started tutorial](http://blog.shippable.com/get-started-with-continuous-integration-for-nodejs-app).
  2. [Log into Shippable](https://app.shippable.com/login.html) using your GitHub credentials.
  3. [Enable](http://docs.shippable.com/navigatingUI/subscriptions/ci/#enable-project) the `sample_nodejs` project.
  4. Create [an integration on Shippable](http://docs.shippable.com/integrations/imageRegistries/dockerHub/) to your image registry (Docker Hub used in this example).![Image title](http://blog.shippable.com/hs-fs/hubfs/Blog_images/docker-in-continuous-integration-series/Docker%20Hub%20integration.png?t=1487656187279&width=640&name=Docker%20Hub%20integration.png)

  5. Modify the `shippable.yml` file compared to the above sample. Replace the following values. 
    * **`image_name`: **Replace `abhijitkini/testimage` with your docker-hub-username/docker-hub-image-repo. For Google Container Registry or Amazon EC2 Container Registry, refer our [documentation](http://docs.shippable.com/ci/shippableyml/#pre_ci_boot).
    * **`image_tag`: **Replace `latest` with the tag of the image you want to pull.
    * **`pull`: **Set to `true` for the image to be pulled from the Docker registry.
    * **`env`: **Specify environment variables you want inside your build container.
    * **`options`: **Enter Docker options for use in the `docker run` command. You can also include Home environment variable as shown, if it isn't set in your image.
    * **`integrationName`: **Replace `docker-hub` with the name of the Docker integration you created in Step 4.
    * **`type`: **`docker` This value specifies it is a Docker registry integration.
    * `**branches**` (optional): Skip this for your integration to be applicable to all branches. In this example, it is applicable only to the `master` branch.
  6. Commit the `shippable.yml` changes, which automatically triggers a build on Shippable.
  7. Shippable pulls your Docker image from Docker hub and uses it in the CI process. A successful build is shown below:![Image title](http://blog.shippable.com/hs-fs/hubfs/Blog_images/docker-in-continuous-integration-series/Use%20your%20Docker%20Image%20in%20Continuous%20Integration.png?t=1487656187279&width=640&name=Use%20your%20Docker%20Image%20in%20Continuous%20Integration.png)

### **Important Note**

You can combine each option with _Push a Docker image to a registry of your choice_ (Scenario #3) in your CI process. We'll go over this combination of scenarios in a later post.

## **Conclusion**

You can use Shippable's default Docker images in your CI process when you don't use Docker or the default images fulfill your requirements. Use your own custom Docker image in your CI process when you want to override the default images or set specific options to boot the build container.

In the next blog, we'll go over Scenario #3: Build your own Docker image.
