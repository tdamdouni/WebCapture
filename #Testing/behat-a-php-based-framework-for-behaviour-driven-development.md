# Behat: A PHP-Based Framework for Behaviour-Driven Development

_Captured: 2017-06-01 at 00:42 from [dzone.com](https://dzone.com/articles/behat-a-php-based-framework-for-behaviour-driven-d?edition=304109&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-31)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190137&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190137&u=https%3A%2F%2Fwww.wakanda.io%2F).

## Introduction

Before getting into how Behat functions, let's get into the question of **_what is Behat? _**Behat is a PHP based framework for **_Behavior-Driven Development _**or **_BDD_**. The simplicity of **_Behat_** lies in the fact that it can define all possible scenarios and behaviors in simple English steps of when and then. This is also known as the**_ Gherkin_** format.

## Prerequisites and Installation

### Prerequisite

Now, let us start with setting up **_Behat_** on our machine. To set up Behat on your machine we will need to have the following prerequisites:

  1. **_PHP_** installed on your machine. If you are using Behat version 3.0, then it is preferable if you use PHP version 7.0. I have been using the **_Ubuntu 16.04 LTS_** version. For Ubuntu 16.04, it comes pre-installed on the system.
  2. **_Composer_** installed on your machine. Composer is a PHP dependency management tool that helps in managing the required libraries for PHP related to a project. The dependencies are installed within a directory named Vendor.

### Installation

To install Composer, follow the steps below:

a) First, update the package manager cache by running the following:

b) Second, install the dependencies for installing Composer. We will need curl in order to download composer and **_php-cli_** for installing and running it. The **_php-mbstring_** package is necessary to provide functions for the library we will be using. Git is used by Composer for downloading project dependencies, and unzip is used for extracting zipped packages. Everything can be installed using the following command:

c) Composer provides an installer, written in PHP. Make sure you are in the home directory and retrieve the installer using curl.

d) To install Composer globally, use the following:
    
    
    $ sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

This will install and download Composer as a system-wide command named Composer, under /usr/local/bin.

e) To test your installation, run:

## What Is Composer? How Do You Install It?

In order to use Composer in your project, you will need a **_composer.json_** file. The **_composer.json_** file basically tells the Composer which dependency it needs to download for your project and which versions of each package are allowed to be installed. This is extremely important to keep your project consistent and avoid installing unstable versions that could potentially cause backward compatibility issues.

You don't need to create this file manually - it's easy to run into syntax errors when you do so. Composer auto-generates the **_composer.json_** file when you add a dependency to your project using the **_require_** command. Additional dependencies can also be added in the same way, without the need to manually edit this file.

The process of using Composer to install a package as a dependency in a project usually involves the following steps:

  * Identify what kind of library the application needs.
  * Research a suitable open-source library on [packagist.org](https://packagist.org/), the official package repository for Composer.
  * Choose the package you want to depend on.
  * Run **_composer require_** to include the dependency in the **_composer.json_** file and install the package.

Now let us start off with adding the dependency for Behat in the **_composer.json_** file. Here are the dependencies that are required for installing Behat onto the system:

Now Behat is installed in the **_bin_** directory. Next, you have to execute the following command:

The init command initializes the current working directory with the **_'features'_** directory. The features directory consists of the feature files. These feature files contain the pre-defined Gherkin steps to replicate user behaviors or carry out acceptance tests.

Once the basic set up is done the folder structure looks something like this.

![folderstruct1](https://soumyajit2016.files.wordpress.com/2016/11/folderstruct1.png)

Now if we check the **_'bootstrap'_** directory inside the **_'Features'_** directory, we have the **_'Feature_Context.php'_**. This file plays a crucial role in the processing of the Behat steps. The **_Feature_Context_** file consists of the **_FeatureContext_** class.

## Context Class

The Context class is a simple **_POPO (Plain Old PHP Object)_** used by Behat to represent testing part of your features suite. If *.feature files are all about describing how your application behaves, then the context class is all about how to test your application, and that it actually behaves as expected.

## Prerequisites for Context Class

In order to be used by Behat, your context class should follow 3 simple rules:

  1. Context classes should implement **Behat\Behat\Context\ContextInterface** or extend base class **Behat\Behat\Context\BehatContext** (as in the previous example).
  2. Context classes should be called **FeatureContext**. It's a simple convention inside the Behat infrastructure.
  3. Context classes should be findable and loadable by Behat. That means you should somehow tell Behat about your class file. The easiest way to do this is to put your class file inside the **features/bootstrap/**directory. All *.php files in this directory are auto-loaded by Behat before any feature is run.

## Contexts Lifetime

Your context class is initialized before each scenario runs, and every scenario has its very own context instance. This means 2 things:

  1. Every scenario is isolated from each other scenario's context. You can do almost anything inside your scenario context instance without the fear of affecting other scenarios - every scenario gets its own context instance.
  2. Every step in a single scenario is executed inside a common context instance. This means you can set private instance variables inside your @Given steps and you'll be able to read their new values inside your @When and @Then steps.

By default, Behat provides a set of Step definitions which you can see by just typing in the following command in the console:

This will enlist all the default step definitions available with Behat.

## Setting Up the Configuration for Behat

Let's talk about how to set the configuration of your entire test suit in Behat. For that, we have a file named _**'behat.yml'**._

All configuration happens inside a single configuration file in the **YAML** format. Behat tries to load **behat.yml **or **config/behat.yml** by default or you can tell Behat where your config file is with the **\--config** option, as seen below:

Few of the important features of the Behat configuration file that should be kept in mind

All configuration parameters in that file are defined under a profile name root (default: for example). A profile is just a custom name you can use to quickly switch testing configuration by using the --profile option when executing your feature suite.

The default profile is always default. All other profiles inherit parameters from the default profile. If you only need one profile, define all of your parameters under the ` default: root:` .

## Context in the Behat Configuration File

Sometimes you may want to use a different default context class or provide useful parameters for the context constructor from your behat.yml. Use the context block to set these options:

## Profiles

Profiles help you define different configurations for running your feature suite. Let's say we need 2 different configurations that share common options, but use different formatters. Our behat.yml might look like this:

For example, in the above snippet for the behat.yml, I have mentioned in two profiles **_staging_** and **_production. _**The profile for staging defines the tests to be run on the staging URL, where as the profile for production runs the required tests in the production URL. To run the tests on the specific profile we can use the following command:

## Extensions

The extensions block allows you to activate extensions for your suite or for a specific profile of the suite:

## Writing Behat Scenarios Using the Gherkin Format

Gherkin is a line-oriented language that uses indentation to define the structure. Line endings terminate statements (called steps) and either spaces or tabs may be used for indentation (we suggest you use spaces for portability). Finally, most lines in Gherkin start with a special keyword:

The parser divides the input into features, scenarios, and steps. Let's walk through the above example:

  1. Feature: 'Test the requires xyz feature' starts the feature and gives it a title.
  2. Scenario: 'Some determinable business situation' starts the scenario, and contains a description of the scenario.
  3. The next few lines after **_Scenario_** are the scenario steps, each of which is matched to a regular expression defined elsewhere.
  4. Scenario: 'A different situation' starts the next scenario, and so on.

When you're executing the feature, the trailing portion of each step (after keywords like Given, And, When, etc.) is matched to a regular expression, which executes a PHP callback function.

## Features

Every *.feature file conventionally consists of a single feature. A feature usually contains a list of scenarios. You can write whatever you want up until the first scenario, which starts with Scenario: (or the localized equivalent) on a new line. You can use tags to group features and scenarios together, independent of your file and directory structure.

Every scenario consists of a list of steps, which must start with one of the keywords Given, When, Then, But, or And (or the localized one). Behat treats them all the same. Here is an example:

## Tags

Tags are a great way to organize your features and scenarios. Consider the above example. In the above example, if you check, I have used two scenarios _**@blackbox@1**_. The tag **_@blackbox_** signifies that any Scenario with this tag will be executed on _**goutte driver**_, a headless driver which is used to execute the desired tests. Using the tag **_@1_** helps me in telling Behat which specific scenario I need to execute from a feature file.

A Scenario or Feature can have as many tags as you like, just separate them with spaces. To understand tags from the system's point of view, they are basically metadata that help Behat in identifying separate executions. It also reduces excess effort when it comes to executing identical scenarios for the developer.

## Steps

Features consist of steps, also known as **_'Givens'_**, **_'Whens'_** and **_'Thens.'_**

Behat doesn't technically distinguish between these three kinds of steps. These words have been carefully selected for their purpose in order to make the steps user readable and identically distinguishable.

## Givens

The purpose of **Given** steps is to **put the system in a known state** before the user (or external system). Avoid talking about user interaction in Givens. Givens are your preconditions. For example:

## Whens

The purpose of **When** steps are to **describe the key action** the user performs or defining the state transitions. For example:

## Thens

The purpose of **Then** steps is to **observe outcomes**. The observations should be related to the business value/benefit in your feature description. The observations should inspect the output of the system. For example:

## And, But

**And** or **But** steps can be used to allow your Scenario to be read more fluently. For example:

## Executing Behat Test Scenarios or Feature Files

Here are some specific ways by which you can execute Behat test scenarios

1\. Execute the entire Behat test suite:

2\. Execute entire test scenarios for a specific feature file:

3\. Execute scenarios specific to an entire test suite:

4\. Execute scenarios specific to a feature file:

5\. Execute test scenarios specific to a profile:

Where **_staging_** is the profile name defined in the**_ behat.yml _**configuration file.

## Drivers Available to Execute Behat Tests

  * _**Selenium WebDriver**_
  * _**Goutte Driver**_
  * _**PhantomJS + Selenium**_

Note: To run your tests headless on **_phantomjs, _**you have to start the **_phantomjs-selenium _**server at port **_8643_**. To start your phantom webdriver on port 8643, use the following command:

**_Phantomjs_** and **_Goutte_** are used to run all the scenarios headlessly, i.e you have to rely on your CLI to view the output.

## Generating Reports in Behat

Well, this part has been pretty rough when dealing with Behat version 3.0. The pretty HTML formatter has been deprecated in this version of Behat. But there is a very good plugin for generating HTML reports in Behat known by the name [behat-html-formatter](https://packagist.org/packages/emuse/behat-html-formatter). The configuration is pretty easy. All you need is to include the dependency in your composer.json file. Once that is done, make configurational changes for the Behat-html-formatter plugin in the configuration file of Behat, which is behat.yml. All you need to include is:

and

Here are few of the screenshots for steps required to start with using Behat.

## Installing Dependencies Using Composer

![pic2_composer](https://soumyajit2016.files.wordpress.com/2016/11/pic2_composer.png)

## Initializing the Feature Folder Within the Directory

![pic3_init](https://soumyajit2016.files.wordpress.com/2016/11/pic3_init.png)

## Execution of Behat Test Scenarios

![testscenarioran](https://soumyajit2016.files.wordpress.com/2016/11/testscenarioran.png)

## Generating Test Reports for Behat

![reports](https://soumyajit2016.files.wordpress.com/2016/11/reports.png)

To know more and explore more on Behat you can check on my GitHub [link](https://github.com/Corefinder89/Behat-Demo).

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190138&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190138&u=https%3A%2F%2Fwww.wakanda.io%2F).
