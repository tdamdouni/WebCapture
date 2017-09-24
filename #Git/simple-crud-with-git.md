# Simple CRUD With Git

_Captured: 2017-09-21 at 11:07 from [dzone.com](https://dzone.com/articles/simple-crud-with-git?edition=326502&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-20)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

In this article, I will show you how to perform basic operations with Git that will improve the productivity of a developer. Git is an essential tool to learn and master, as many projects depend on it. This article will show some of the basic operations that come handy in day to day life while dealing with Git.

## **Create a Repository**

The first thing we need to do is to create a remote repository on github.com. For that, you need to log into github.com. After a successful login, you need to create a repository called "test" using the "create a repository" button. This is the repository we are going to work with.

### **Add New Files**

By default, the repository is empty except for a README.MD file.

In order to add a new file, first you need to clone this "test" repository to your local disk. In order to do that, run the following command:

This will download and create a folder called "test" on your local disk. If there are any files in it, all of them will be downloaded into the "test" folder.

Now add a new file called "test.txt" with some contents in it under the "test" folder. Then run the following command:

The above command will add the new files to your repository.

The next command is to commit this new file.

The -m switch is the message that you want when you commit the changes.

Now we need to send this change to the remote repository. For that, run the following command.

This command will lead to authenticate the user once again and send your file to new repository.

Let us take a look at the above command in detail:

  * **push** \- Sends the files or changes to remote repository.

  * **origin** \- The default name of the repository given by Git. 

  * **master** \- The default branch name in the repository. This is where all your changes will be pushed into unless a different branch name is mentioned.

### **Update Files**

Now you are going to modify the files you created in the above step. Let us modify the "test.txt" file we created in the above step. We need to perform the following operations one by one:

Once you execute the above commands one after another, your files will be updated in the git remote repository.

### **Delete Files**

Now we want to delete either a single file or multiple files from the remote repository. In order to do this, issue the following commands:

These commands will help you in delete the file in your git repository as well as from your local file system.

In order to delete multiple files, you need to mention the files to be deleted. For example, if you want to delete 2 files, namely, file1.txt and file2.txt, then issue the following command:

## **Summary**

We have seen the minimal necessary commands while working with a Git repository. In all the CRUD operations which we have seen, the following commands are mandatory:

You can do much more with Git, but this article is just beginner level for anyone to understand the basic concepts of Git.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

Opinions expressed by DZone contributors are their own.
