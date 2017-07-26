# Update to My Simple Dropbox Blogging System

_Captured: 2015-06-09 at 07:34 from [www.macdrifter.com](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html)_

Yes, I am blogging about blogging. What follows is both boring and tedious. There must be something better for both of us to do. Skimming is recommended.

I made a major update to my [home-grown system for blogging](http://www.macdrifter.com/2012/01/post-to-wordpress-from-simplenote-or-dropbox.html). For a quick summary, I use Hazel in conjunction with a Python script to allow me to blog directly from a Dropbox folder. When I began the project, I used Simplenote to post from my iPad and iPhone. NVAlt kept Simplenote in sync with Dropbox. I no longer use Simplenote but the system works exactly the same.

### Memory Lane

Each article contains some header meta data such as:
    
    
    title: Update to My Simple Dropblog System
    category: python
        Mac
    tags:
    

Hazel processes the Dropbox folder using [a rule that reads the meta data fields](http://www.macdrifter.com/2012/04/matching-multimarkdown-meta-data-with-hazel.html). When it finds a new text file with the "tag: @post" line in the header, it starts the script for posting to Macdrifter.com

The post is titled with the file name. If there is a value for the "title:" header field, that value is used as the post title instead. The WordPress categories are set using the "category:" field. This system has worked flawlessly for many months. I post from any text editor with access to Dropbox, which are all of the text editors on my devices. I also use the amazing [TextDrop web app](http://textdropapp.com)[1](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html) for posting from a web browser.

### Son of The Abomination

This little insult to decency posts almost every single article here. It's what I call a Danny DeVito script. It's short, it's not pretty, but it works hard and is reliable.

This version of the script is very fast. Once Hazel recognizes a candidate file to use as a post, this script is complete within two seconds. I'm sure with another couple dozen hours of work, I could shave another second off.

The script is commented well, so hopefully I don't need to provide any elaboration.[2](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html)
    
    
    import markdown
    
    from wordpress_xmlrpc import Client, WordPressPost
    
    from wordpress_xmlrpc.methods.posts import GetPosts, NewPost
    
    from wordpress_xmlrpc.methods import taxonomies
    
    import gntp.notifier
    
    import os
    
    import sys
    
    #Connection details for the WordPress xmlrpc connection
    
    wpUrl = 'http://www.macdrifter.com/xmlrpc.php'
    
    wpUser = 'SuperAwesomeUserName'
    
    wpPass = 'CleverLittlePassword'
    
    # Hold the server instance. Needed to make the post and add properties
    
    wpServer = Client(wpUrl, wpUser, wpPass)
    
    # The default category
    
    postCategoryList = ['uncategorized']
    
    title = ''
    
    postLink = ''
    
    uploadCategoryList = []
    
    ## For Hazel
    
    filePath = sys.argv[1]
    
    growlMSG = ""
    
    ## This is the business end. It makes the post to the site.
    
    def postToWordPress(title, html, postCategoryList, postLink):
    
        post = WordPressPost()
    
        post.title = title
    
        post.content = html
    
        #If there is a post cagtegory, then append it as a term
    
        if postCategoryList != '':
    
            post.terms_names = {
    
                'category' : postCategoryList
    
            }
    
        #Prepare custom field for Link List type post
    
        if postLink != '':
    
            # Just seems safer to start with an empty cutom_field list
    
            post.custom_fields = []
    
            post.custom_fields.append({
    
                'key' : 'linked_list_url',
    
                'value' : postLink
    
            })
    
        # The new API requires the post_status and comment_status to be set.
    
        # Otherwise the post is added as a draft with comments disabled.
    
        post.post_status = 'publish'
    
        post.comment_status = 'open'
    
        post_id = wpServer.call(NewPost(post))
    
        return post_id
    
    # Instantiate my own Growl notification. This is totally unnecessary but nice to have
    
    def growlInitialize():
    
        growl = gntp.notifier.GrowlNotifier(
    
        applicationName = "Simple DropBlog",
    
        notifications = ["New Messages"],
    
        defaultNotifications = ["New Messages"])
    
        growl.register()
    
        return growl
    
    # The body of the script starts here. Hazel passes in the file path.
    
    # Read the file and and get the filename to use as a title.
    
    # Then get the file contentents.
    
    try:
    
        myFile = open(filePath, "r")
    
        rawText = myFile.read()
    
        myFile.close()
    
        fileName = os.path.basename(filePath)
    
        # Start off using the file name as the post title
    
        title = os.path.splitext(fileName)[0]
    
        # Handle the odd characters. Just kill them.
    
        rawText = rawText.decode('utf-8')
    
        # Process with MD Extras and meta data support
    
        md = markdown.Markdown(extensions = ['extra', 'meta'])
    
        # Get the html text
    
        html = md.convert(rawText)
    
    ## If post_id exists then already posted. We're done.
    
    ## FUTURE: USE POST ID TO UPDATE EDITED POST
    
        if 'post_id' not in md.Meta:
    
            # extract the title from the meta data if it exists.
    
            # If there is no title attribute, keep the file name as the post title
    
            if 'title' in md.Meta:
    
                title = md.Meta['title']
    
                # title is actualy a list
    
                title = title[0]
    
    ## extract the categories but keep them as a list
    
            # If no categories exist then the default is uncategorized.
    
            if 'category' in md.Meta:
    
                postCategoryList = md.Meta['category']
    
            # Extracts the url to use as the linked-list url
    
            if 'url' in md.Meta:
    
                postLink = md.Meta['url']
    
                postLink = postLink[0]
    
                # Modify the title to indicate that it is a linked article.
    
                title = title + " [Link]"
    
    ## Only post if there is a title. If there's no title, then what are you even doing?
    
            if title != '':
    
                newPost_id = postToWordPress(title, html, postCategoryList, postLink)
    
    ## Append the post_id to the beginning of the file
    
                #Get the file contents
    
                myFile = open(filePath, "r")
    
                myFileContent = myFile.read()
    
                myFile.close()
    
                # Write the post id and append the rest of the text
    
                myFile = open(filePath, "w")
    
                myFile.write('post_id: ' + newPost_id + '\n' + myFileContent)
    
                myFile.close()
    
                postGrowl = growlInitialize()
    
                postMSG = newPost_id + ": " + title + " Posted to Macdrifter"
    
                growlMSG = growlMSG + "\n"+ postMSG
    
                postGrowl.notify(
    
                    noteType = "New Messages",
    
                    title = growlMSG,
    
                    description = "The Blog Post was successful",
    
                    icon = None,
    
                    sticky = False,
    
                    priority = 1)
    
    except Exception, e:
    
        postGrowl = growlInitialize()
    
        postMSG = "Post Failed!"
    
        postGrowl.notify(
    
            noteType = "New Messages",
    
            title = postMSG,
    
            description = e,
    
            icon = None,
    
            sticky = False,
    
            priority = 2)
    

That's the script. The major changes are as follows:

It's rewritten for the new Python WordPress XMLRPC library.

The `postToWordPress(title, html, postCategoryList, postLink)` method uses the new API to create posts with custom fields.

I no longer read all of the categories and create new categories as required. The new WordPress API does that for me when I make the post with meta data using the newPost() method.

#### Python XMLRPC

The first major upgrade was switching to the latest version of [Max Cutler's Python XMLRPC library](https://github.com/maxcutler/python-wordpress-xmlrpc) (version 2.1 as of this writing). This is a major upgrade that caused some of my method calls to break. The new library is significantly more advanced than the version I was using. For example, there are now simple calls to set post meta fields as well as the _publish_ and _comment_ status. Max has done an amazing job with the project. It follows the new WordPress 3.4 XMLRPC API very closely and enables [the newPost method](http://codex.wordpress.org/XML-RPC_WordPress_API/Posts#wp.newPost) from Python.

To update my installation of the Python library, I ran:
    
    
    sudo easy_install --upgrade python-wordpress-xmlrpc
    

The instructions are [simple enough.](http://python-wordpress-xmlrpc.readthedocs.org/en/latest/overview.html#installation)

#### Categories

In the previous version of the script, I performed a check of the existing categories before posting. If the category did not already exist, I had to create it. This update does away with all of that. The new WordPress API automatically creates a category if it does not already exist. This change provided a significant boost in performance for posting new articles. More simple code and better performance. Win.

#### Linked Lists

The next major update was one that I have been tinkering with for awhile. I wanted to switch the way I create link-posts (posts that are not my original work but point to something else). Namely I wanted to create DaringFireball type linked-list posts. Titles should link to the original source and there should be a permalink at the bottom to the Macdrifter.com post.

Previously, this was not feasible with the Python XMLRPC library. It is now, using custom fields.

#### Custom WordPress Fields

I'm not a WordPress developer and I do not enjoy working in PHP. Consequently, this description is sparse and extremely narrow.

To implement DF-style linked lists, I chose to use custom fields to contain the URL for the external site. Each post will have a custom field named linked_list_url. I chose this name in case I ever want to use the extremely popular [DFLL WordPress plugin](http://yjsoon.com/dfll-plugin). I might as well prepare for a future where I'm sick of reinventing the wheel. Of course when that happens I'll just switch to SquareSpace.

### On the WordPress Side

Great. I feel like a super star that can program binary load lifters. But this rewrite had a purpose. I want to change the way link-list articles are displayed on my WordPress instance. Now comes the awkward part of my relationship with this project. After groping around with PHP and the WordPress API documentation I found a concise example to follow. [Johan Brook](http://johanbrook.com/development/wordpress/linked-list-style-posts-in-wordpress/) perfectly documents his simple solution.[3](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html) He was even kind enough to email detail sufficient for a chaste WordPress hacker like me to follow. I already spent several hours trying to understand WordPress and PHP, so this brought everything together for me. Well, it allowed me to get to first base at least. Pucker up WordPress.

I run a hacked up version of the [Cleanr theme](http://wordpress.org/extend/themes/cleanr). In my theme directory, I opened the Index.php file and edited the portion that generates the list of posts on the main page. Your future self will thank you if you backup your WordPress theme files. Trust me on this one.
    
    
    < ?php while (have_posts()) : the_post(); ?>
    
                < ?php $meta_link = get_post_meta(get_the_ID(), "linked_list_url", true); ?>
    
                <div <?php post_class() ?> id="post-< ?php the_ID(); ?>">
    
                <span class="postmetadata">< ?php the_category(' / ') ?> &mdash; < ?php edit_post_link('Edit', '', ' &mdash; '); ?>  < ?php comments_popup_link('No comments', '1 comment', '% comments'); ?></span><br />
    
                    <small><span class="date">< ?php the_time('d') ?></span><br />< ?php the_time('M y') ?> <!-- by <?php the_author() ?> --></small>
    
                    <h2>< ?php if($meta_link):?>
    
                        <a title="follow link" href="<?php echo $meta_link;?>">
    
                            < ?php the_title();?>
    
                        </a>
    
                        < ?php else: ?>
    
                        <a href="<?php the_permalink() ?>" rel="bookmark" title="Permanent Link to < ?php the_title_attribute(); ?>">< ?php the_title(); ?></a>
    
                        < ?php endif;?>
    
                    </h2>
    
                    <div class="entry">
    
                        < ?php the_content('<em>Continue reading &rarr;'); ?>
    
                    </div>
    
                    <div class="clearfix"></div>
    
                    < ?php if($meta_link):?>
    
                    <p><a href="<?php the_permalink() ?>" rel="bookmark" title="Permanent Link to < ?php the_title_attribute(); ?>">&#197;</a></p>
    
                    < ?php endif;?>
    
                </div>
    
            < ?php endwhile; ?>
    
            <div class="navigation">
    
                <div class="alignleft">< ?php next_posts_link('&larr; Older Entries') ?></div>
    
                <div class="alignright">< ?php previous_posts_link('Newer Entries &rarr;') ?></div>
    
                <div class="clearfix"></div>
    
            </div>
    

The important parts are as follows. This line determines if there is a post meta field named "linked_list_url" and assigns it to the `$meta_link` variable.
    
    
    < ?php $meta_link = get_post_meta(get_the_ID(), "linked_list_url", true); ?>
    

The title is generated between two **"h2"** tags. So this bit says that if there is a "linked_list_url" field then use the `$meta_link` variable as the permalink. If not, then use my WordPress permalink.
    
    
    <h2>< ?php if($meta_link):?>
    
                        <a title="follow link" href="<?php echo $meta_link;?>">
    
                            < ?php the_title();?>
    
                        </a>
    
                        < ?php else: ?>
    
                        <a href="<?php the_permalink() ?>" rel="bookmark" title="Permanent Link to < ?php the_title_attribute(); ?>">< ?php the_title(); ?></a>
    
                        < ?php endif;?>
    
                    </h2>
    

This line simply inserts the permalink for my post after the comment. In this case, the "Å" character as the link text.[4](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html)
    
    
    < ?php if($meta_link):?>
    
                    <p><a href="<?php the_permalink() ?>" rel="bookmark" title="Permanent Link to < ?php the_title_attribute(); ?>">&#197;</a></p>
    
                    < ?php endif;?>
    

Next, I made a similar change to the theme's single.php file. This is the code that generates the single post view when anyone follows the permalink. In this case, if it is a link-list post the title link redirects to the original source. If not, it's just plain text.
    
    
    < ?php $meta_link = get_post_meta(get_the_ID(), "linked_list_url", true); ?>
    
                <h2>
    
                < ?php if($meta_link):?>
    
                        <a title="follow link" href="<?php echo $meta_link;?>">
    
                            < ?php the_title();?>
    
                        </a>
    
                        < ?php else: ?>
    
                        < ?php the_title(); ?>
    
                        < ?php endif;?>
    
                </h2>
    

Great, the posts work as expected. RSS feeds are a bit trickier. Johan provides excellent advice. Don't edit the RSS php files directly. Instead, edit the functions.php in the theme support file. Here's the beginning of my theme's functions.php file for some context:
    
    
    < ?php
    
    // Path constants
    
    define('THEME', get_bloginfo('template_url'), true);
    
    define('THEME_JS', THEME . '/js/', true);
    
    if (function_exists('register_sidebar'))
    
        register_sidebar();
    
    function theme_load_js() {
    
        if (is_admin()) return;
    
        wp_enqueue_script('jquery');
    
        wp_enqueue_script('nav', THEME_JS .'jquery.dropdown.js', array('jquery'));
    
    }
    
    add_action('init', theme_load_js);
    
    function macdrifter_permalink_rss($content) {
    
        global $wp_query;
    
        $postid = $wp_query->post->ID;
    
        $link = get_post_meta($postid, 'linked_list_url', true);
    
        if(is_feed()) {
    
            if($link !== '') {
    
                $content = $link;
    
            }
    
            else {
    
                $content = get_permalink($postid);
    
            }
    
        }
    
        return $content;
    
    }
    
    add_filter('the_permalink_rss', 'macdrifter_permalink_rss');
    
    </code></pre>
    
    <p>The important part is this function and "add_filter" statement:</p>
    
    <pre><code lang="php" width="600" escaped="true">function macdrifter_permalink_rss($content) {
    
        global $wp_query;
    
        $postid = $wp_query->post->ID;
    
        $link = get_post_meta($postid, 'linked_list_url', true);
    
        if(is_feed()) {
    
            if($link !== '') {
    
                $content = $link;
    
            }
    
            else {
    
                $content = get_permalink($postid);
    
            }
    
        }
    
        return $content;
    
    }
    
    add_filter('the_permalink_rss', 'macdrifter_permalink_rss');
    

That's it. I make no warranties, guarantees, promises or double entendres to imply that this will work for anyone else. You're on your own.

Finally, so that I could also have access to the linked_list_url field, I turned on the meta data editor in my WordPress settings:

![](http://www.macdrifter.com/uploads/2012/06/Screen%20Shot%2020120618_184411_600px.jpg)

Now a typical link-list article contains a header like this:
    
    
    category: Link
    url: http://www.libertypages.com/clarktech/?p=3692
    tags:
    

Once I add the "@post" tag, Hazel gets to work and creates the post for me. When the deed is done, the header looks like this:
    
    
    post_id: 3329
    category: Link
    url: http://www.libertypages.com/clarktech/?p=3692
    tags: @post
    

### Conclusion

I built a blogging engine that is only suited to me. It works exactly how I like it. I can write and post from anywhere that I can get access to my Dropbox folder. On the plus side, I learned how to completely bork a WordPress installation.

This system has made blogging extremely simple for me. I would only post a fraction of what I do now, if I had not built this system. Depending on how you feel about Macdrifter.com, that's either good or bad.

Either way, it was a fun little challenge that taught me a few things about this site. Hopefully it helps someone else. If you read this far, we should exchange promise rings or at least trade some mix tapes because I think we might have something special.

  1. This app gets better almost every day. It's a full fledged text editor with Markdown support, but in the browser. Ridiculously good. [Review here](http://www.macdrifter.com/2012/05/textdrop-3-5-update.html). [↩](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html)

  2. This work is free for personal use. Just don't be a dick about it. [↩](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html)

  3. His site is beautiful. I love the layout. Checkout his [category page](http://johanbrook.com/development/) with the subtly click effects. Very nice. [↩](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html)

  4. It will probably change, but I like it well enough for now. Why? I'm a chemist. Also, the Ångstrom is the unit of measure for links between atoms. It made sense to me at the time. No, **_you_** have a problem with HTML character codes. [↩](http://www.macdrifter.com/2012/06/update-to-my-simple-dropbox-blogging-system.html)
