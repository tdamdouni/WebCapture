# Livecoding: Why Contributing to Big Open Source Projects Is Still Hard [Video]

_Captured: 2017-11-12 at 11:22 from [dzone.com](https://dzone.com/articles/livecoding-why-contributing-to-big-open-source-pro?edition=334864&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-10)_

Add user login and MFA to your next project in minutes. [Create a free Okta developer account](https://dzone.com/go?i=247342&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%25253EGlobal%25253Edeveloper-trial-sep-14-FY18Q3%26utm_medium%3Dpre-text%26utm_source%3Ddzone-web-dev-zone-all-developer), drop in one of our SDKs to your application and get back to building.

[GatsbyJS](https://www.gatsbyjs.org/) has a buggy feature that I don't like and I'm gonna fix it! Biggest opensource project since I poked around phpBB back in high school.

I can do this!

GatsbyJS is a React-based static site generator. The reason I'm so invested is because almost everything I build with React is a static site. Landing pages, single data visualizations, stuff like that. All static.

Gatsby has a plugin, `gatsby-transformer-remark`, that lets you write copy-focused pages in Markdown. React gets tedious when you want to focus on writing copy.

![](https://i.imgur.com/xEuspE9.gif)

This remark transformer comes with a feature I love: `tableOfContents`. Looks at your header tags and generates a table of contents. Great for making your site easier to navigate.

But there's a problem.

Table of contents uses only hash links like `#this-is-a-subheading`. This works great when it's on the same page as your content, but it's not so great when you put it on an index page.

Index pages are often at different URLs than their content pages. So when you try to link with just a hash, it doesn't go anywhere.

I decided to fix that and use absolute links.

So we looked at the `CONTRIBUTING.md` doc in Gatsby's repository, and it was wonderful. Tells you everything you need to set up a development environment so you can work on Gatsby and your test site immediately picks up on it.

  1. Fork and clone Gatsby ✅
  2. Run `yarn run bootstrap` ✅

Wait... no... that didn't work. Step 2 and we're already blocked.

We filed a [helpful issue](https://github.com/gatsbyjs/gatsby/issues/2395) complaining that nothing works and everything is broken. The command didn't run through, dependencies were missing, and everything blew up in our face.

Two hours later, we had installed some 30 missing packages and aaaaalmost got a clean `yarn test` run. Very important to have all your tests passing before you start poking around a large codebase.

A very helpful person named `m-allanson` saved our asses. They found a commit from Gatsby's head maintainer that changed something in a config - removed `yarn workspaces` whatever the hell that is - and it was just 23 hours old.

All our troubles were because of a commit from less than a day ago. Talk about timing!

_And_ it was the kind of problem only a new contributor could discover. Everything worked for people who had stuff installed from before.

So... yay? We helped?

Once we got up and running, it was almost time to stop livecoding for the day. We had just enough time to figure out where in the code we're going to have to fix those links.

A file called `gatsby-transformer-remark/srcextend-node-type.js`.

This function ��
    
    
     console.log (require( 'util' ).inspect (tocAst.map , false , null ) )

Note the `console.log`. That's where we have to hook into the toc abstract syntax tree and change the links.

Not sure how yet, but how hard can it be?

Launch your application faster with Okta's user management API. [Register today for the free forever developer edition!](https://dzone.com/go?i=234224&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%25253EGlobal%25253Edeveloper-trial-FY18Q3%26utm_medium%3Dpost-text%26utm_source%3Ddzone-web-dev-zone-all-developer)
