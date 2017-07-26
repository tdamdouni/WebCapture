# Avoid Keeping Sensitive Info in a Code Repo: How to Remove Files From Git Version History

_Captured: 2017-04-04 at 22:43 from [dzone.com](https://dzone.com/articles/avoid-keeping-sensitive-info-in-a-code-repo-how-to?edition=288881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-04)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

One of the vulnerabilities that are really easy to exploit is when people leave super-sensitive information in source code - and you get your hands on this source code. In early prototyping, a lot of people will hardcode passwords and certificate keys in their code, and remove it later when moving to production code. Sometimes it is not even removed from production. But even in the case where you do remove it, this sensitive information can linger in your version history. What if your app is an open source app where you are sharing the code on GitHub? You probably don't want to share your passwords.

Getting this sensitive info out of your repository is not as easy as deleting the file from the repo and adding it to the .gitignore file - because this does not touch your version history. What you need to do this is:

  * Merge any remote changes into your local repo, to make sure you don't remove the work of your team if they have committed after your own last merge/commit.
  * Remove the file history for your sensitive files from your local repo using the filter-branch command:
    
    
    git filter-branch –force –index-filter \
    
    
    ‘git rm –cached –ignore-unmatch \
    
    
    PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA‘ cat — –all

Although the command above looks somewhat scary it is not that hard to dig out - you can find in the Github [doc files](https://help.github.com/articles/removing-sensitive-data-from-a-repository/). When that's done, there are only a few more things to do:

  * Add the files in question to your.gitignore file.
  * Force write to the repo (**git push origin -force -all**).
  * Tell all your collaborator to clone the repo as a fresh start to avoid them merging in the sensitive files again.

Also, if you have actually pushed sensitive info to a remote repository, particularly if it is an open source publicly available one, make sure you change all passwords and certificates that were included previously - this info should be considered compromised.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
