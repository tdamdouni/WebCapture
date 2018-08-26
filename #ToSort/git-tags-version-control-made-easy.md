# Git Tags: Version Control Made Easy

_Captured: 2018-06-14 at 13:19 from [dzone.com](https://dzone.com/articles/git-tags-version-control-made-easy?edition=384193&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-13)_

DON'T STRESS! Assess your OSS. [Get your free code scanner from Flexera](https://dzone.com/go?i=294429&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018). [FlexNet Code Aware](https://dzone.com/go?i=294429&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018) scans Java, NuGet, and NPM packages.

Tags are a simple aspect of Git: they allow you to identify specific release versions of your code. You can think of a tag as a branch that doesn't change. Once it is created, it loses the ability to change the history of commits.

There are two types of [tags in Git](https://kolosek.com/git-commands-tutorial-part2/): annotated and lightweight. Both of them will allow you to refer to a specific commit in a repository, but they differ in the amount of metadata they can store.

Annotated tags store extra metadata such as author name, release notes, tag-message, and date as full objects in the Git database. All this data is important for a public release of your project.

Tags can also include a more descriptive tag-message or annotation much like a [commit message when you are about to merge](https://kolosek.com/git-merge/). Usually, this is achieved by using (`-a` for annotation):

Executing this command you will create a new annotated tag identified with version v1.0.0. The command will then open up your commit editor so that you can fill up the metadata.

In case you wanted to add a **tag-message** you can pass the `-m` option, this is a method similar to `git commit -m`.

**Lightweight tags **are the simplest way to add a tag to your Git repository because they store only the hash of the commit they refer to. They are created with the absence of the -a, -s, or -m options and _do not_ contain any extra information.

> Lightweight tags are essentially "bookmarks" to a commit, they are just a name and a pointer to a commit, useful for creating quick links to relevant commits. [By Bitbucket tutorials](https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag)

To create a new lightweight tag execute the following command:

## Additional Commands

**Listing tags** \- `git tag`  
Use the command whenever you want to list all the existing tags, or you could filter the list with `git tag -l 'v1.1.*'`, where `*` acts as a wildcard. It will return a list of tags marked with `v1.1`.

You will notice that when you call you do not get to see the contents of your annotations. To preview them you must add `-n` to your command: `git tag -n3`.
    
    
    $ git tag -l -n3 v1.0 Release version 1.0 v1.1 Release version 1.1 v1.2 Release version 1.2

The command lists all existing tags with maximum 3 lines of their tag message. By default `-n` only shows the first line.

**Tag details** \- `git show <tag_identifier>`  
This command presents you with tag details and information from the commit that was tagged.
    
    
    $ git show v1.0 tag v1.0 Tagger: Kolosek Date: Fri May 11 10:45:33 2018 +0100 Release version 1.0 -----BEGIN PGP SIGNATURE----- Version: GnuPG v1 iMTvhAA... -----END PGP SIGNATURE----- commit 7d44b6bb8abb96dee33f32610f56441496d77e8a Author: Kolosek Date: Fri May 11 9:50:13 2018 +0100 Edited the Login form ...

It prints the author's name, creation date, message, GnuPG signature if present and the information about the referenced commit. If the tag is lightweight, the output will be limited to the information about the referenced commit.

**Editing tags** \- `git tag -a -f <tag_identifier> <commit_id>`  
If you try to create a tag with the same identifier as an existing tag, Git will throw an error: `fatal: tag 'v1.0' already exists`.

Instead of having to delete it and re-add the tag you can simply replace it while keeping the existing description. Choose the place in your commit history with `<commit_id>` where you want the tag moved to and add `-f` or `-force` to your command.

> Remember to alert your team members when you "force" a change like this. If they still have an "old" version of the tag, it may cause conflicts when they try to push to the server!

If you have already **pushed the tag** to the server and want to fix that, first make sure your local version of the tag is correct before you run the [following command](https://kolosek.com/git-commands-tutorial-part2/): `git push origin -f --tags`.

**Deleting tags** \- `git tag -d <tag_identifier>`  
Generally, there is no reason to **delete the tags** because they are inexpensive and don't use any resources unless you have mistakenly created a tag pointing to the wrong commit.

In case the tag has been already **pushed** and you need to remove it from remote repository run: `$ git push origin :v1.0`.

**Publishing tags** \- `git push <location> <tag_identifier>`  
A tag is just a reference to your local repository and it is _not_ automatically [pushed to the remote repository](https://kolosek.com/git-merge/) with the rest of the code. Instead, you can `git push` the tag individually, or you can run `git push --tags` which will push all the tags at once. It can be done similarly to pushing the branches:

**Sorting tags** \- `git tag --sort=<type>`  
When looking at a project with lots of tags, using the [sort option](https://stackoverflow.com/questions/14273531/how-to-sort-git-tags-by-version-string-order-of-form-rc-x-y-z-w#answer-22634649) can come in handy. Supported types are:

  * `refname` (sorts in a lexicographic order),
  * `version:refname` or `v:refname` (here tag names are treated as versions).

Here we are listing all tags which name starts with "v" by their versions.

Isn't _git tag_ the same as _#tag_ in social media, but in its own way? It helps us return and list all our previous release!

**Subscribe to our future article releases! We will make it sure to _git tag_ them for you!**

[Try FlexNet Code Aware Today](https://dzone.com/go?i=294430&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018)! A [free scan tool](https://dzone.com/go?i=294430&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018) for developers. Scan Java, NuGet, and NPM packages for open source security and license compliance issues.
