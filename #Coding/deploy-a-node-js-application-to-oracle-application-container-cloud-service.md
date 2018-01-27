# Deploy a Node.js Application to Oracle Application Container Cloud Service

_Captured: 2017-12-12 at 21:19 from [dzone.com](https://dzone.com/articles/deploy-a-nodejs-application-to-oracle-application?edition=342139&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-12)_

Running out of memory? [Learn how Redis Enterprise enables large dataset analysis](https://dzone.com/go?i=252321&u=https%3A%2F%2Fredislabs.com%2Flanding%2Fredis-enterprise-flash%2F%3Futm_source%3Ddzone%26utm_medium%3Dtext%252520ad) with the highest throughput and lowest latency while reducing costs over 75%!

[ACCS](https://cloud.oracle.com/en_US/application-container-cloud) provides a pre-configured platform ([Platform-as-a-Service, or PAAS](https://en.wikipedia.org/wiki/Platform_as_a_service)) where you can quickly deploy and host your applications. For many of today's applications, the hosting server is just that: a place to host the application. Most of the time, the only thing an application needs from the server is to have it support the application's programming language and to provide in-and-out connections through ports. Using a PAAS such as ACCS frees you from all of the extra work of configuring and maintaining a server and allows you to focus on perfecting your application.

ACCS supports multiple languages but for this post, I'll focus on Node.js.

## DinoDate

For the examples, I will be deploying the [DinoDate](https://github.com/oracle/dino-date) application. DinoDate was written as an open-source learning application that can be used to demonstrate database concepts with multiple programming languages. It currently has both Python and NodeJS mid-tier applications and is backed by an Oracle Database.

The following instructions show how to deploy the Node.js version of DinoDate to an Oracle ACCS instance.

If you don't have access to Oracle Cloud services, you can [try the Oracle Cloud with $300 of free credit](https://cloud.oracle.com/en_US/tryit).

Download/Clone the [DinoDate](https://github.com/oracle/dino-date) application.

## Database

First, you'll need a database.

[Create an Oracle Cloud database](https://www.youtube.com/watch?v=0CZUyhNl97Q), or if you already have an Oracle Database, make sure that you can safely create and destroy the `DD` and `DD_NON_EBR` schema.

Connect to your database as `sys` with `sysdba` and run `coreDatabase/dd_master_install.sql`. (Use your password and connect string.)

## Prepare the DinoDate Application

Download `[oraclejet.zip](http://download.oracle.com/otn/JET/400/oraclejet.zip)` (version 4.1.0 is the current version as of the time of this post).

  * Extract the Oracle JET files
  * Run `bower install`:
  * Install the NodeJS modules. ACCS assumes your deploy package will include all necessary modules.
  * Create a deploy directory.
  * Copy the front end client into the deploy directory.
  * Copy the NodeJS application into the deploy directory.
  * Change to the `deploy/nodejs` directory:
  * Create the environment variables. (Replace `YourJdbcConnecString` with your JDBC connect string.)

  * Open your browser to_ localhost:3000_.
  * Log in as _bob@example.com_ (any password will work).
  * Open the **Search** tab and execute a search. I typically search for "eat" -- it will return several members.
  * **Ctrl** \+ **C** to stop the node server then switch back to the deploy directory (`cd ../`).

## Package the Files to Deploy

Create the manifest file: `manifest.json`.

This file declares that we will use Node.js version 8 and provides the command that will be used to start the application.

Create the deployment file: `deployment.json`.

This file includes the environment variables DinoDate needs and sets the ACCS deployment to use 1G of memory and only install one instance.

Replace `YourJdbcConnecString` with the JDBC connect string for your database.

**Important note**: ACCS is pre-configured to listen on `$PORT` so we set our application to listen on that port. Do not attempt to change `$PORT`. When ACCS performs its post-deploy check, it will open the application using `$PORT`; if the application is not listening on that port and returns a 404, the deployment will fail and be removed.

Create a ZIP file with the required DinoDate deploy files:

**Another important note**: The Node.js platform in ACCS has the oracledb module pre-installed. If we were to upload the module we just installed it would cause a conflict that would cause the deployment to fail and be removed, so we exclude it from the deployment .zip file.

## Deploy to ACCS

In your browser, navigate to the Oracle Application Container Cloud Service Console.

Push the **Create Application** button to open the platform selection panel.

Push the **Node** button to open the application definition panel.

  * Populate **Name** with DinoDate.
  * Click **Choose** **File** for **Archive** and select the `DinoDateNodeACCS.zip` file.
  * Click **Choose** **File** for **Manifest** and select the `manifest.json` file.
  * Click **Choose** **File** for **Deployment Configuration** and select the `deployment.json` file.

You can change the values in the other fields as you'd like, but notice that since we defined "memory": "1G" and "instances": "1" in the `deployment.json` file those values will change automatically.

It's also possible to include the `manifest.json` file in the DinoDateNodeACCS.zip file instead of uploading it separately.

Click **Create**.

It may take several minutes for ACCS to setup the environment and deploy the application. Once it's done, click on the **URL:** link to open the application.

## Try It Out

You can log in with any of the existing users, such as:

  * Bob 
    * bob@example.com
  * Admin 
    * admin@example.com

Use any value for the password, the application doesn't check it.

Click on the **Search** tab and search for "eat" -- it should return six of the pre-loaded dinosaurs.

## Quick Review

  1. Build your application and test it.
  2. Collect the required deployment artifacts and dependencies into a .zip file. **Reminder**: Do not include the `oracledb` module.
  3. Create a `manifest.json` file that contains at least the required Node.js version and the command used to start your application.
  4. Create a `deployment.json` file that contains any needed environment variable definitions. Optionally you can include ACCS environment definitions such as required memory and number of instances. (This file is optional.) **Reminder**: ACCS will use the pre-defined environment variable `$PORT`. Make sure your application listens on `$PORT`.
  5. Use the ACCS service console to upload your three files and create your new application.

If you run into any trouble, leave a comment and I'll be happy to help!

Running out of memory? Never run out of memory with[ Redis Enterprise database](https://dzone.com/go?i=252322&u=https%3A%2F%2Fredislabs.com%2Flanding%2Fredis-enterprise-flash%2F%3Futm_source%3Ddzone%26utm_medium%3Dtext%252520ad). [Start your free trial today](https://dzone.com/go?i=252322&u=https%3A%2F%2Fredislabs.com%2Flanding%2Fredis-enterprise-flash%2F%3Futm_source%3Ddzone%26utm_medium%3Dtext%252520ad).
