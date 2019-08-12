# Python 2 to 3 Migration: Now or Never?

_Captured: 2018-08-31 at 11:27 from [dzone.com](https://dzone.com/articles/python-2-to-3-migration-now-or-never?edition=387236&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-30)_

![Image title](https://www.activestate.com/sites/default/files/styles/blog_image/public/blog-field_main_image/python-2-3-upgrade-now-never-blog-hero.jpg?itok=VrZomf84)

The upcoming end-of-support deadline for Python 2 on January 1, 2020 means enterprises need to start thinking about the impact it will have on their existing Python applications.

Originally, Python 2 was used as a scripting alternative to Perl for things like configuration automation or else for creating web applications. But Python adoption didn't really take off until its data science packages started becoming popular some 5-6 years ago.

## Python 2 vs 3

Despite the fact that Python 3 was originally introduced in 2008, and was well established by the time data science projects started accelerating the popularity of Python, data scientists by and large were still working with Python 2.

In fact, Python 2 is proving to be a particularly difficult habit to kick:

  * Many popular operating systems (like Mac OS) continue to incorporate Python 2 as the default installation, or provide both Python 2 and 3 out of the box (Debian, SUSE, etc.).
  * It wasn't until June 2017 that Python 3 users started outnumbering Python 2 users, [according to PyCharm](https://hynek.me/articles/python3-2016/).

The good news is that Python 3 is (finally) starting to gain ground:

  * The three largest public cloud providers (AWS, Azure, and Google Cloud Platform) fully support Python 3.
  * Python 3.5 introduced changes that simplified code porting.

As a result, if you're creating new projects today, you should be using Python 3 unless there's a specific package you need that still doesn't support 3.

## To Migrate or Not to Migrate

The real question is whether or not you should be migrating your existing Python 2 code to Python 3. The answer depends on your use case:

**USE CASE** **MIGRATE** **WHY/WHY NOT?**

**Internal Deployments**
**No**
If it's not broken, don't fix it.  
  
Scripts and applications deployed in the secure zone behind the firewall should be fine.

**Data Science Deployments**
**YES**
The message is clear: organizations focused on data science should be planning on adopting Python 3.  
  
All of the data science package creators have announced their plans to adopt Python 3.  
  
And the data science packages are moving very quickly: new features, new functionality, and new versions are coming out all the time.

**Public-facing Applications/Packages**
**YES**
Enterprises in this boat will need to have a strategy since their deployments will become more and more vulnerable over time.  
  
Your planning should encompass at least two options: 1) spend the time and resources to perform the migration, or else 2) opt for extended support.

##   
Tips for Migration/Support

For those considering code migration, a number of Python packages exist to help you out:

  * **Six** - best for adding Python 3 compatibility to your existing Python 2 code.
  * **2to3** - best for converting Python 2 code to Python 3 code.
  * **Python-future** - best for those that want to focus on writing python 3 code going forward while ensuring backward compatibility with Python 2.

For those that are considering staying on Python 2 (at least for now), commercial vendors are likely to step up and provide extended support. ActiveState is one such vendor considering providing support for Python 2, including bug fixes for core libraries and possibly key, popular packages, as well.

ActiveState, like Python 2 has been around for more than 20 years. We're a founding member of Python.org, and have had millions of developers download our Python distributions for the past two decades.
