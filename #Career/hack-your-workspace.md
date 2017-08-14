# Hack Your Workspace

_Captured: 2017-08-05 at 07:53 from [dzone.com](https://dzone.com/articles/hack-your-workspace?oid=twitter&utm_content=buffer59fa4&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

All developers, testers, and other IT people have their workspace. Employer, specialization, it doesn't matter. You have an infinite number of files on your computer. Favorite console commands. Shortcuts. Rituals that you do every day.

But do you really often think about your actions? About what you do? How many circles of hell need to be passed by a rookie or a new member of your team to start work effectively? What do you do if your hard drive were to die? And how many times you do act in ways that may be ineffective?

With my hand on my heart, I think that only some of us do backups of our own hard drive every day. And there are few of us who can recall all the settings and configurations that are being used at any given moment. Without them, everyday actions may be broken, even local software assembling. And I will just keep silent about transferring different`xxx.properties` through a messenger.

As I see it, all of these problems are things we could find in a classic system administration. But there, they have much more influence on organizational health; or peoples' careers; or maybe their health, too. To eliminate manual work (actually, if you have hundreds of servers, it just sounds like busy work), the progressive part of humanity invents **infrastructure as code**, that in the extreme makes your infrastructure immutable. And one day you will find out that it is easier to setup a server from scratch than trying to update it to keep it fit.

The fundamental part of "infrastructure as a code," quite obviously, is code, or some files that are stored in an SCM like Git. And those files could be played by a machine for doing some work instead of human. We eliminate routine by using tools, APIs, or maybe robots, because we want to do more exciting jobs, or harder tasks that improve us as professionals.

So, let's try to apply this principle to our workspace setup.

Below, you can find a list of tasks that I needed to do before I could do my work (efficiently or not) after I changed my job:

  * Install a different kind of utility software.
  * Fetch several projects from git-repository.
  * Config my local workspace settings that are kept in `.properties`-files.
  * Make gradle-meta-wrapper to feel more comfortable while working with ant.
  * Generate certificates and put them in the right place to have access to internal sources.

All of these you could do by hand. Even more, there is a document which describes how to do that. And finally, some of them you might not do at all. So, I've read and followed through the document for rookies, but I don't want to do that again. It is a first. And second, part of these actions you need to do periodically.

My decision was to automate myself with one easy peasy command:

Don't ask me why Ansible. I like it because it has an easy learning curve and I know it. It really matters.

In `local-inv` we keep our configuration and define that we want to use a local connection when playing the playbook:

On the upper-level, our algorithm is clear and easy to understand and consists of steps that we described earlier:

Every `include` contains several steps inside that need to be done to achieve a goal. And each `include` is marked by an own tag. It is required cause sometimes we want to do only a part of the work, for example, generate config files from templates.

As a bonus, you could update code from repos every morning or on demand. And it is very simple to code:

Here, `services` is a list of services, which are described through data-structures in variables, that we could change for our needs:
    
    
      - { name: messages-service }
    
    
      - { name: discussions-service }
    
    
      - { name: attachments-service, local: true }

These settings could be reused in any other tasks, for example, for templating properties of these services:

We should not forget about **idempotency**. In the case of multiple launches of our playbook with the same config, we should get identical results. It is evident that it is not necessary to generate certificates and keys again if they already exist. Why should we heat air for no reason?
    
    
    - stat: path={ username }.key 

But what is the most important part of all of that? You should use it every working day. Keep it fit. Don't do anything by hand; improve your tools.

You should test your tools periodically with a managed disaster, like corrupting some files or cleaning up your work dir. Live like you have SLA to restore your workspace anytime.

Sometimes it is hard. Very hard.

As a reward, we get a fast start for rookies, save our (and our colleagues) personal time budget, a stable workspace, and confidence in the future.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
