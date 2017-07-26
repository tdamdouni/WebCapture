# Up and running with Jekyll

_Captured: 2015-06-09 at 08:50 from [hypertext.net](http://hypertext.net/2013/01/jekyll/)_

As most of you know I've been thinking for a very long time about getting this site off of WordPress and the photoblog off of Pixelpost, and getting both away from a VPS I manage. [Once the decision to jump was made](http://hypertext.net/2012/08/wordpress-octopress-squarespace/), the problem became one of migration, and it wasn't easy: this site is over 10 years old and consists of ~3,000 posts, and the photoblog is a different animal entirely.

Add to that some anal-retentive obsessiveness and you get _many_ marathon hacking binges during which you lose sight of all that's good in the world and sometimes forget that you're human and probably should get up and pee.

This write-up is meant to be kind of an overview of certain things I had to deal with during the migration, and how I came to decide on certain aspects of the system, etc. As with most of the more technical posts on this site, it's documentation and reference for me as much as it is for anyone who might stumble across it.

### Why Jekyll and not Octopress?

[Octopress](http://octopress.org) is a framework that sits on top of [Jekyll](https://github.com/mojombo/jekyll), and so if the goal was for me to reduce complications and dependencies to a bare minimum, then it was a no-brainer that I would just have to bite the bullet and go with Jekyll-one less thing to worry about in the long run.

I knew it'd be a bit more work up front, but I figured it was probably worth it in the end, and after slogging fully through the migration I'm pretty sure I made the right decision.

(Given that Octopress is kind of just a wrapper around Jekyll, and that its underlying blog source files must conform to formats Jekyll requires, most of the earlier work I did in the [WordPress->Octopress migration](http://hypertext.net/2012/08/wordpress-octopress-squarespace/) was easily ported over to the Jekyll installation.)

### Why Jekyll and not Squarespace?

As I wrote and talked about quite a bit, I was [pretty set on moving to Squarespace](http://hypertext.net/2012/08/leaning-towards-squarespace/) at one point, especially after being given early access to their [Template Developer Kit](http://www.squarespace.com/developers), and the [CEO's ear](http://hypertext.net/2012/08/wordpress-octopress-squarespace/).

Believe or not, I got damn near everything up and running on Squarespace, designed the blog and photoblog using the TDK, and actually, for the past few months, was publishing to Squarespace (privately) everything I was publishing to Wordpress and Pixelpost. I threw _a lot_ of time at it.

All was well…until a couple of weeks ago when I logged in to my account and noticed that the permalinks for all of my posts were incorrect; the `/year/month/` structure had been stripped, and all that was left was `/slug`. I played around with various settings, but could never get it back to how it had been since I got my intial import working.

The `/year/month/title` directive used to, correctly, substitute the slug for the title if a slug was present (my import file contained slugs for every post), but now it seemed that if a slug was present, the `/year/month/title` structure was being disregarded and only the slug was used in its place.

Anyway, I'm really not sure what went wrong, and didn't spend too much time trying to figure it out-I just decided that if I was ever going to be truly happy with my setup, I needed as much control as possible, and at this point in time that meant Jekyll.

### Why Amazon S3?

Why not? It is Amazon after all. Though before this I had never used any of their AWS products, I have the utmost confidence in their services, and had been hearing good things about hosting static sites on S3. I feel very comfortable having 10 years of my work sitting on their servers.

(You might remember that I considered pushing to [Github Pages](http://pages.github.com/) at one point, but had to abandon that idea when I realized there was no way to put a repository within a sub-directory of another repository, which I'd need to do if I wanted the photoblog to reside at `/photos`.)

#### Route 53

The move to S3 static hosting necessitated moving the DNS for `hypertext.net` to Amazon's DNS service, [Route 53](https://aws.amazon.com/route53/). This mostly was a pretty simple transition: I signed up for Route 53, created a new zone for `hypertext.net`, pointed my registrar to the Route 53 nameservers, and deleted from my VPS the DNS stuff for `hypertext.net`.

The only real hang-up came when mapping the domain to the S3 bucket from which I planned to serve the site. Due to some terrible UI/UX on the Route 53 console, I wasted _five hours_ of my life trying to resolve an issue that didn't exist. If interested, you can read about the problem in [this post I made on the Route 53 forum](https://forums.aws.amazon.com/message.jspa?messageID=415101#415101).

#### Redirecting justinblanton.com

Until a few days ago I wasn't sure how I was going to handle the domain-wide redirects of `justinblanton.com` requests to corresponding `hypertext.net` requests. As [explained in this earlier post](http://hypertext.net/2012/12/301-v-canonical/), I was kind of resigned to just using the cheapest hosting provider I could find that could handle the kind of redirection I needed, but then I came across [this comment](http://aws.typepad.com/aws/2012/12/root-domain-website-hosting-for-amazon-s3.html?cid=6a00d8341c534853ef017ee6b90367970d#comment-6a00d8341c534853ef017ee6b90367970d) from the AWS team on one of their blog posts, which says that the query string is redirected together with the domain. So, it seems I may be able to handle this entirely using S3 + Route 53, which is _awesome_. I won't make that transition for a while still, but it's good to know there are options, and that one of them keeps me entirely within the AWS ecosystem.

### Syncing with S3

I'm not entirely sure how this element is going to play out. There are a number of options out there, the laziest and most inefficient of which is to just re-upload all the content each time I make the slightest change to _any_ file.

This, of course, is beyond stupid (especially since _most_ changes will affect only a small percentage of the total files during a rebuild of the blog), and something I'd never do unless there was no other option, but it's nice to know that, in a pinch, a literal upload-and-overwrite is all that's needed to update the content.

#### Jekyll-s3

When doing all the local development I'd sometimes use [Jekyll-s3](https://github.com/laurilehmijoki/jekyll-s3) to push to an accessible S3 "dev" bucket I created. This worked well and good for a couple of weeks, but in the past day or so (since I deployed the site), it's stopped working. It just hangs. Does nothing. Breaks completely. Instead of worrying too much about it, I just fell back on [s3cmd](http://s3tools.org/s3cmd) (discussed below), and it's proving to be a great option.

Before getting away from Jekyll-s3, I want to talk for a second about using it (when it works ;) to upload multiple blogs to the same S3 bucket. Jekyll-s3 won't let you specify a subdirectory to which to push the files, and so I had to come up with another solution, which ended up being stupid simple.

In the photoblog's Jekyll installation, you just have to tell Jekyll to write the files to `/sub-dir`, so that when these files are pushed to the S3 bucket they get pushed to the correct folder. To achieve this, I added these lines to the `_config.yml` file for my photoblog's Jekyll installation:
    
    
    baseurl: /photos
    destination: _site/photos

Not for nothing, but it seems modifying `pagination_dir` in `_config.yml` does nothing. I thought about digging into the code, but ultimately decided to just prepend the pagination links (between photos and between pages) with `/photos`.

#### s3cmd

As mentioned, I previously got two Octopress installations up and running (blog and photoblog)and worked out a way to [push them to the same S3 bucket](http://hypertext.net/2012/09/s3-bucket-octopress/). This was accomplished using s3md.

I ended up doing something very similar for my two Jekyll blogs. I created a `Rakefile` for both blogs, and so to sync each of them to my `hypertext.net` bucket, I simply run `rake sync` from within their respective installations. The `Rakefile` for the main blog looks like this:
    
    
    task :default => :sync
    desc "Sync with S3"
    task :sync do
        sh "s3cmd sync _site/* s3://hypertext.net/"
    end

(The photoblog's `Rakefile` is the same, except for the addition of `/photos/`, as appropriate.)

When I have time I'll probably at least look into other solutions (e.g., [S3Sync](http://www.s3sync.net/wiki), [rsync](https://rsync.samba.org/) \+ [FUSE](http://fuse.sourceforge.net/) (to mount S3 locally), etc.), but so far this s3cmd method seems to be working absolutely beautifully.

Clearly, and as usual, I was going for a very minimal look. If I feel I can get away with making it even more minimal, I probably will. There still are a ton of little design things all over the site that I want to refine and tweak, but I think the general aesthetic is mostly set at this point.

If the colors look familiar, it's because they're from [iA Writer](http://www.iawriter.com/). You might remember a post I wrote on [how to make any app look like iA Writer](http://hypertext.net/2011/06/mimic-writer-aesthetic)-I pulled the color scheme from that post.

For what it's worth I did all development locally and against the Chrome dev channel builds. After I was satisfied with that I played around in the other major WebKit browser, Safari. I figured this covered the majority of my traffic (including iOS and Android clients). I gave no mind at all to IE and Firefox; at the moment I just don't care if something breaks in those browsers. I likely will never worry about IE (life's too short), but might make some Firefox-specific changes at some point.

### RSS

I debated very seriously getting away from [FeedBurner](http://feedburner.com), but ultimately decided to stick with it, if for no reason other than that I couldn't come up with a great reason to leave it. I have quite a few subscribers that use FeedBurner's email feature, and I didn't want to disrupt that.

I can't remember exactly why now (and if I gave it any real thought I'd probably realize there's no longer a purpose for it), but for the past ~10 years(!) I've had my feed at `/syndicate`, and when I started using FeedBurner however many years ago, I set up a temporary redirect to the FeedBurner feed, like so:
    
    
    Redirect temp /syndicate http://feeds.feedburner.com/jblanton

Initially, I thought I wouldn't be able to replicate this with Amazon S3, but after futzing with their new redirect feature I came up with the following rule, which does _exactly_ what my old redirect did:
    
    
    <RoutingRules>
        <RoutingRule>
            <Condition>
                <KeyPrefixEquals>syndicate</KeyPrefixEquals>
            </Condition>
            <Redirect>
                <HostName>feeds.feedburner.com</HostName>
                <ReplaceKeyPrefixWith>jblanton</ReplaceKeyPrefixWith>
                <HttpRedirectCode>302</HttpRedirectCode>
            </Redirect>
        </RoutingRule>
    </RoutingRules>

(I do the same thing for the photoblog feed, but with the addition of `/photos`, as appropriate.)

### Photoblog

Unfortunately, there is just no practical way for me to automate the migration from Pixelpost. Accordingly, I'm having to do it manually, and I'm nowhere near done with it.

I went ahead and migrated the 10 most recent posts, and then created an [eleventh post](http://hypertext.net/photos/2004/01/migration/), which just tells the reader that the migration isn't complete; that will live as the first post (in time) until I'm done with the migration.

I used [wget](https://www.gnu.org/software/wget/) to pull down the entire photoblog and structure, and will use those files, together with accessing the database via [Sequel Pro](http://www.sequelpro.com/), to build the photoblog in Jekyll as time permits.

### What's left to do?

I'd say the migration is about 90% complete at this point. What remains mostly are things that only I know or care about.

The biggest thing probably is just getting the remainder of the photoblog posts into the new system. That's going to take some time.

#### Creating new posts

Honestly, I just haven't put much time into this just yet, but trust that when I do I'll come up with something that will automate to the extent possible the creation and publication of new posts, and I'll of course write it up here.

#### Search

Currently search of the site has been outsourced to Google. Before this switch to Jekyll I used WordPress's native search for the blog, and offered no search for the photoblog. Since farting around with Google site search I've realized (kind of accidentally) that you can limit the scope of the search via the value you use for the `q` variable in the search form. This means that I can offer search functionality on the photoblog and have the results limited to only those pages that exist within `/photos`. Pretty cool.

All of that said, I think I'll probably look into offering some sort of 'local' search, and get away from having to rely on Google. How this might work with a completely static site, I'm not entirely sure, and frankly, it might not be possible.

Relatedly, there are still some things I need to work out with `sitemap.xml` stuff given that I'm essentially running two completely seprate blogs on one domain.

#### UTF encoding issues

You're still reading?! I could go on and on about the UTF encoding issues I had when converting the XML file of my WordPress export to the individual post files, but seriously, who the hell wants to read about that? (I discussed it briefly [here](http://hypertext.net/2012/08/wordpress-octopress-squarespace/).) Anyway, this is something I'm going to have to revisit when I can catch my breath.

### OMG, go to bed!

As ever, please feel free to [email me](mailto:justin@justinblanton.com) if you've questions about anything I touched on in this post. I suspect many of you will be making a similar move soon, and I'm excited to see how far we can push this stuff.
