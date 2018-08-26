# Performing Zero Downtime Releases

_Captured: 2018-06-01 at 19:51 from [dzone.com](https://dzone.com/articles/performing-zero-downtime-releases?edition=379218&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-06-01)_

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

You've spent months working on a project, and it's finally time to show it to the world. You're proud of what you've achieved, but you aren't quite sure how to release it for others to see.

If that sounds familiar, read on, and together we will cover how to perform a release of your code, with minimal interruption and difficulty.

Handling releases is often a tricky hurdle for any developers first transitioning from being a hobbyist to a full-time role, especially if you're building a startup and may not have people with much experience handling releases. This little guide should help you out.

We will be covering a fictional PHP application, but the process is transferable to any language.

## Common Mistakes

There are many mistakes that can be made when getting started with deploying your code. Some of these mistakes will make things a little simpler for you in the short term, but in the long term, you will encounter issues and have to change how you release your code. That may not necessarily be a simple thing to do. We may as well get it right the first time.

### Building Your Release on Your Production Server

The largest issue with building your release on your production server is that it indicates there isn't necessarily a staging or testing environment where you can ensure that you haven't inadvertently broken anything.

Having a staging server, while adding cost, has huge benefits, even for a small team, and is well worth the additional cost for the peace of mind it gives you.

### Building Your Release on a Non-Similar Environment

If your code is going to end up on Ubuntu with PHP 7.2, then building it in a Windows environment on PHP 5.3 wouldn't make sense, would it? Even a minor change in the environment could potentially cause unforeseen and untested bugs to occur.

The best way for this to be handled is to use a consistent environment throughout the entire process, from your development machines through the use of Docker or Vagrant to staging and production.

### Building Your Release on a Per-Server Basis

You may have your environments set up properly, with development, staging, and production all synchronized and identical. You may run your entire process on staging, fully test the entire setup, and prove your system works. You may then start your release process on production, and something goes wrong.

How could it be that something that worked both in development and staging suddenly no longer works in production?

If you started the entire build process over again for each of those stages, then any number of things could go wrong. Not to mention it takes drastically longer to build and compile multiple times than it does to upload the pre-built code.

## Building Like a Boss

A proper way to do a build would be in an identical environment, and only once.

For example, in a dedicated build environment, you could set up your script to tag your repositories, clone the correct tag into the correct folder, pull in any dependencies via your package manager of choice, run any compilation scripts, and then tar up the result.

This tar can then be uploaded to any environment, and you can guarantee that all the files will be there, in the correct location, and that if it worked in one environment, it will work in another identically built environment.

And best of all, it's fast.

## Releasing Your Build

Once you have that build produced, you have to get it onto all of your servers and actually used by your customers.

The setup we use at Shopblocks allows for a zero-downtime release to occur.

Our folder setup looks something like this:

We upload the code onto each of our servers. You can use Ansible, SCP, FTP, whatever you desire. We upload to our `/tmp` directory using Ansible and then untar the file while still in `/tmp`.

Then we create a new directory in the `/var/www/sites/versions` for the version we are releasing; for example, `mkdir 0.0.11`.

Then you can move the code you have extracted into that directory. While this is going on, your `current` directory, and your system, has no idea that a new release is occurring and will continue as it was.

Once you have copied all of the code over and you have a new version ready for release, simply verify that the change has occurred on all the servers you are releasing to, and then change the symlink that `current` points to.

`ln -s /var/www/sites/current /var/www/sites/versions/0.0.11`

and your new release is live, without any downtime.

For your development environment, have all of your working files in the current directory. Then any references, relative or absolute, will be identical since you should always reference the current directory and not a specific version.

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
