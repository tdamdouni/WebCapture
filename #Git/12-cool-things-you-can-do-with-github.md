# 12 cool things you can do with GitHub

_Captured: 2017-09-20 at 18:17 from [hackernoon.com](https://hackernoon.com/12-cool-things-you-can-do-with-github-f3e0424cf2f0)_

I can't for the life of me think of an intro, so…

### #1 Edit code on GitHub.com

I'm going to start with one that I _think_ most people know (even though I didn't know until a week ago).

When you're in GitHub, looking at a file (any text file, any repository), there's a little pencil up in the top right. If you click it, you can edit the file. When you're done, hit **Propose file change** and GitHub will fork the repo for you and create a pull request.

Isn't that wild? It creates the fork for you!

No need to fork and pull and change locally and push and create a PR.

![](https://cdn-images-1.medium.com/freeze/max/60/1*w3yKOnVwomvK-gc7hlQNow.png?q=20)![](https://cdn-images-1.medium.com/max/1600/1*w3yKOnVwomvK-gc7hlQNow.png)

> _Not a real PR_

This is great for fixing typos and a somewhat terrible idea for editing code.

### #2 Pasting images

You're not just limited to text in comments and issue descriptions. Did you know you can paste an image straight from the clipboard? When you paste, you'll see it gets uploaded (to the 'cloud', no doubt) and becomes the markdown for showing an image.

Neat.

### #3 Formatting code

If you want to write a code block, you can start with three backticks -- just like you learned when you read the [Mastering Markdown](https://guides.github.com/features/mastering-markdown/) page -- and GitHub will make an attempt to guess what language you're writing.

But if you're posting a snippet of something like Vue, Typescript or JSX, you can specify that explicitly to get the right highlighting.

Note the ````jsx` on the first line here:

…which means the snippet is rendered correctly:

(This extends to gists, by the way. If you give a gist the extension of `.jsx` you'll get JSX syntax highlighting.)

### #4 Closing issues with magic words in PRs

Let's say you're creating a pull request that fixes issue #234. You can put the text "fixes #234" in the description of your PR (or indeed anywhere in any comment on the PR).

Then, merging the PR automagically closes that issue. Isn't that cool?

### #5 Linking to comments

Have you even wanted to link to a particular comment but couldn't work out how? That's because you don't know how to do it. But those days are behind you my friend, because I am here to tell you that clicking on the date/time next to the name is how you link to a comment.

> _Hey, gaearon got a picture!_

### #6 Linking to code

So you want to link to a specific line of code. I get that.

Try this: while looking at the file, click the line number next to said code.

Whoa, did you see that? The URL was updated with the line number! If you hold down shift and click another line number, SHAZAAM, the URL is updated again and now you've highlighted a range of lines.

Sharing that URL will link to this file and those lines. But hold on, that's pointing to the current branch. What if the file changes? Perhaps a permalink to the file in its current state is what you're after.

I'm lazy so I've done all of the above in one screenshot:

Speaking of URLs…

### #7 Using the GitHub URL like the command line

Navigating around GitHub using the UI is all well and fine. But sometimes the fastest way to get where you want to be is just to type it in the URL. For example, if I want to jump to a branch that I'm working on and see the diff with master, I can type `/compare/branch-name` after my repo name.

That will land me on the diff page for that branch:

That's a diff with master though, if I was working off an integration branch, I'd type `/compare/**integration-branch...**my-branch`

For you keyboard short-cutters out there, `ctrl`+`L` or `cmd`+`L` will jump the cursor up into the URL (in Chrome at least). This -- coupled with the fact that your browser is going to do auto-complete -- can make it a handy way to jump around between branches.

Pro-tip: use the arrow keys to move through Chrome's auto-complete suggestions and hit `shift`+`delete` to remove an item from history (e.g. once a branch is merged).

(I really wonder if those shortcuts would be easier to read if I did them like `shift + delete`. But technically the '+' isn't part of it, so I don't feel comfortable with that. This is what keeps _me_ up at night, Rhonda.)

### #8 Create lists, in issues

Do you want to see a list of check boxes in your issue?

And would you like that to show up as a nifty "2 of 5" bar when looking at the issue in a list?

That's great! You can create interactive check boxes with this syntax:
    
    
     - [ ] Screen width (integer)  
     - [x] Service worker support  
     - [x] Fetch support  
     - [ ] CSS flexbox support  
     - [ ] Custom elements

That's a space and a dash and a space and a left bracket and a space (or an x) and a close bracket and a space and then some words.

Then you can actually check/uncheck those boxes! For some reason this seems like technical wizardry to me. You can _check_ the boxes! And it updates the underlying text!

What will they think of next.

Oh and if you have this issue on a project board, it will show the progress there too:

If you don't know what I'm talking about when I say "on a project board" then you're in for a treat further down the page.

Like, 2cm further down the page.

### #9 Project boards in GitHub

I've always used Jira for big projects. And for solo projects I've always used Trello. I quite like both of them.

When I learned a few weeks back that GitHub has its own offering, right there on the **Projects** tab of my repo, I thought I'd replicate a set of tasks that I already had on the boil in Trello.
