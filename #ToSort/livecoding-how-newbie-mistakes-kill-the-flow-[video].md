# Livecoding: How Newbie Mistakes Kill the Flow [Video]

_Captured: 2017-12-21 at 14:01 from [dzone.com](https://dzone.com/articles/livecoding-how-newbie-mistakes-kill-the-flow-video?edition=347101&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202017-12-21)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

We continued to work on [GatsbyJS](https://github.com/gatsbyjs/gatsby). That one feature I want to add: make links in markdown tables of contents absolute.

Instead of `#some-title` the link should be `/page-slug#some-title`. That way users can put tables of contents on their index pages and link into documents directly.

The first difficulty was [using VSCode](https://swizec.com/blog/wont-be-switching-vscode/swizec/7898). I wanted to give it a fairer shot at impressing me after all the configuration advice people gave me on Friday.

I'll talk more about VSCode after I use it some more.

The other difficulty was that I have no idea what I'm doing. At first, I was editing the wrong file. My code kept vanishing every time compilation did its thing.

Turns out there's a big difference between `gatsby-transform-remark/extend-node-type.js` and `gatsby-transform-remark/src/extend-node-type.js`.

Confusing for a newbie that those two files are so close together, but it makes sense. Gatsby uses something called [Lerna](https://github.com/lerna/lerna) to create a multi-repo. Every folder inside the repository is its own package.

When I figured that out, I had the bright idea to update my local clone to the latest master.

It did not go so well.

It went so not well, in fact, that we never got to the real work. I don't know how many times I installed and reinstalled `node_modules`, but nothing worked.

This ate all the time I had, and we got nothing done.

I mean, sure, we explored how the markdown AST stuff works, where we need to add the slug (it's deep inside children of children), and made a reasonable hypothesis that we can get the slug using `markdownNode.fields.slug`.

The hypothesis stems from this: we know that each Gatsby node has a `fields.slug`. Don't know where it comes from, but docs assure us it's there. Not sure `markdownNode` is _that_ node, but what else could it be?

`markdownNode` is the node that we are extending, therefore it must be the same thing as a normal Gatsby node. It's just called `markdownNode` here because we're operating on markdown.

This is the function we're tweaking by the way:
    
    
              toc = hastToHTML(toHAST(tocAst.map))

That `tocAst` is where we inject our tweak. I think...

Oh right! The newbie mistake fix - Matthew of Gatsby fame informed me that my `yarn.lock` was probably out of date. It was.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
