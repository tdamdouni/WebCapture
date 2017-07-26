# Xcode Push to Multiple Git Remotes?

_Captured: 2017-03-28 at 20:44 from [dzone.com](https://dzone.com/articles/xcode-push-to-multiple-git-remotes-learn-ios-dev-b?edition=286932&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-28)_

### After the recent GitLab meltdown, Peter Molnar wondered if there were ways to push to multiple repositories simultaneously and proposes a couple of ideas.

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fwww.wakanda.io%2F).

The recent meltdown of [GitLab](https://techcrunch.com/2017/02/01/gitlab-suffers-major-backup-failure-after-data-deletion-incident/) made me more aware again about the remote repository and thinking about using more than one provider in git, with only one push. In a pure git based situation it is quite easy, actually, you can use hacks and official solutions. Let see quickly what are they:

## Hack #1

At the beginning, there was a small hack to modify the git config of your local working copy. The file is located under the root directory of your local repository, in the .git folder, called config. If you open the file (for example from the terminal with nano or vi) you will see a quite straightforward configuration, with sections like the following originally created config:

And here comes the hack:

The hack was quite easy here, you have just added another URL line to the remote, with the proper URL to your repository, and that's it. It is still a hack since git doesn't support multiple pulls like this! It works like a charm (until you have different states on the remote repositories and you try just pull) from the terminal.

## Hack #2 - Solution #1

Nowadays we have a command and respective configuration entries to add a push URL to our remote. I marked it as not just a hack, but an actual solution since it is supported by git. The only caveat is that when you are adding push URLs, you need to add the original URL again, otherwise, git won't push to the original remote - what a surprise. It works pretty well from the command line.

As an example I can add more push URLs with the commands below:  
`$git remote add backup git@bitbucket.org:petermolnar_hu/testformuliple`

We need to re-add the original URL:  
`$git remote set-url --add --push backup git@bitbucket.org:petermolnar_hu/testformuliple`

Now we can add extra URLs to push:  
`$git remote set-url --add --push backup git@github.com:petermolnar_hu/TestForMultiple.git`

In this case, your config file will look like this:

## Hack #3

The third one is a real hack. You have probably heard about the git-hooks. In a nutshell, git hooks give you an opportunity to run a shell script when you invoke certain git commands. Some of the hooks are pre- or post- hooks, which means that they will run before or after the command.  
And the last classification is based on which side the hooks have invoked: on the local or the remote repository (on your machine or on the git server).  
For example, pre-commit hook is a local hook, and it is invoked by the `git commit` command. `pre-receive` is a remote hook, invoked by git-receive-pack. You can find out what types of hooks supported on your system by using the `git hooks --help` command. The executable hook scripts live in your repositories `/.git/hooks` directory.

So, the hack is to start git push to different remote(s) from one of the hooks. It is a bit risky, though, since every time you start the git command, the system will push to the remotes, whether you want to push or not. I created a backup remote:  
`git remote add backup git@github.com:petermolnar-hu/TestForMultiple.git`

And then the hack goes into the local post-commit hook:

As you can see, there is also a hack in the hack, I explicitly defined the key file I wanted to use in the `GIT_SSH_COMMAND` variable.

## What About Xcode?

Believe me, I had spent almost two weeks trying to figure out if one of the hacks above could work with Xcode from the GUI. Alas, without any success. For me it seems Xcode is using a perl script as an intermediary between the GUI and the commands, but I couldn't manage to break it.

It is quite frustrating, but at the time of writing the only way to push to multiple remotes with one command is only available from the terminal.

PS: If you figured out the ultimate trick, please share with us!

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fwww.wakanda.io%2F).
