# Blogging with Dropbox and Pelican

_Captured: 2015-11-02 at 15:25 from [technivore.org](http://technivore.org/posts/2014/01/03/blogging-with-dropbox-and-pelican.html)_

I was recently given a new iPad Air at work and in order to not feel like I use the device only for the Kindle app and the _occasional_ game, I have been looking for a productive use for it. My boss mentioned to me not long ago the he uses a text editor with Dropbox sync capabilities on the iPad for all of his note taking these days (in place of an app like Evernote) and I thought that was a great idea. I found a brilliant and beautiful app called [Editorial](http://omz-software.com/editorial) that handles text and Markdown documents and syncs with Dropbox, and since I had resurrected my blog last week I immediately began to think of a way to use it for blogging.

My blog had been in [Pelican](http://blog.getpelican.com/) already, after having migrated from blogofile when I originally began it, and I was using S3 to host it, with a workflow built around keeping the blog in a mercurial repository and manually publishing to S3 using the included make target. My first thoughts were to automate this on the iPad by building a web service for myself that would publish the blog and writing a custom workflow step in Editorial that would find all the posts in the Dropbox folder and push them to the web service.

Then I realized that was a ridiculous hack and why write a web service when the answer was already staring me in the face with Dropbox itself?

The first step was choosing a hosting provider and I went with [Webfaction](http://webfaction.com), a wonderful halfway point between the power of a full virtual server and the low cost of shared hosting. From there it was just setting up a few pieces of software, stealing ideas from [others](http://thepoch.com/2013/migrating-to-pelican-configurations-makefile-my-workflow.html) that have gone down [this](http://joehewitt.com/2011/10/03/dropbox-is-my-publish-button) [path](https://github.com/marcoarment/secondcrack), and adding some twists of my own.

## Dropbox CLI

This one is pretty well covered by other folks but the main trick is one I picked up from from [Joe Hewitt's post](http://joehewitt.com/2011/10/03/dropbox-is-my-publish-button), setting up a separate Dropbox account for the blog and then sharing a folder in that account with your main Dropbox account, so that only the files necessary for the blog end up on the server.

## Pelican

There was only one issue with installing Pelican in my Webfaction account, which was that I did it the very day that pip 1.5 was released and pip now prefers wheels where possible, but the required version of setuptools(>= 0.8) for wheel support is not present (yet) on Webfaction machines.
    
    
    easy_install-2.7 pip
    pip install --upgrade distribute
    

fixes that however. Note that that will install pip into your own ~/bin directory and that pip will keep your installed libraries in ~/lib/pythonX.Y for whatever version of python you are using, a nice feature of Webfaction.

Anyway, `pip install pelican markdown` is all you need here.

## inotify-tools

Now at this point you are basically done: you can write a shell script to run via cron and rebuild your site periodically with the latest set of posts in your Dropbox folder. But where is the fun in that? We want to rebuild the site _immediately_ whenever a post changes, and for that, on Linux anyway, we can use [inotify-tools](https://github.com/rvoicilas/inotify-tools/wiki).
    
    
    wget http://github.com/downloads/rvoicilas/inotify-tools/inotify-tools-3.14.tar.gz
    tar xvfz inotify-tools-3.14.tar.gz
    cd inotify-tools-3.14
    ./configure --prefix=$HOME
    make
    make install
    

## Custom configuration

And here is where I put my twist on the standard Dropbox/Pelican formula. I wanted to keep all of the files needed to continuously rebuild the blog in the blog folder itself so I could redeploy it easily if need be, and also because it just seemed cooler that way. So in `blog/etc` I have a shell script to rebuild the blog via pelican, the `pelicanconf.py`, a script to monitor the directory via `inotifywait`, my crontab, and the `logrotate.conf` for the log that my monitor script produces.

`pelicanconf.py` is only of interest to me but the others are reproduced below.

update-blog.sh (rebuilds the blog)
    
    
    #!/bin/bash
    source $HOME/.virtualenvs/technivore-blog/bin/activate && $HOME/bin/pelican -q -s $HOME/Dropbox/textfiles/blog/pelicanconf.py
    

monitor-blog.sh
    
    
    #!/bin/bash
    # Shamelessly stolen from Marco Arment's Second Crack project:
    # https://github.com/marcoarment/secondcrack
    
    if [ "$1" == "" ] ; then
        echo ""
        echo "Usage: monitor-blog.sh SOURCE_PATH"
        echo "  where SOURCE_PATH contains your blog posts."
        echo ""
        exit 1
    fi
    
    SOURCE_PATH="$1"
    FORCE_CHECK_EVERY_SECONDS=30
    UPDATE_LOG="${HOME}/tmp/blog-update.log"
    
    BASH_LOCK_DIR="${HOME}/tmp/update.sh.lock"
    
    if mkdir "$BASH_LOCK_DIR" ; then
        trap "rmdir '$BASH_LOCK_DIR' 2>/dev/null ; exit" INT TERM EXIT
    
        echo "`date` -- updating blog" >> $UPDATE_LOG
        $SOURCE_PATH/etc/update-blog.sh
    
        while true ; do
            $HOME/bin/inotifywait -q -q -r -t $FORCE_CHECK_EVERY_SECONDS -e close_write -e create -e delete -e moved_from "$SOURCE_PATH"
            if [ $? -eq 0 ] ; then
                echo "`date` -- updating blog, a source file changed" >> $UPDATE_LOG
            else
                echo "`date` -- updating blog, $FORCE_CHECK_EVERY_SECONDS seconds elapsed" >> $UPDATE_LOG
            fi
    
            $SOURCE_PATH/etc/update-blog.sh
        done
    
        rmdir "$BASH_LOCK_DIR" 2>/dev/null
        trap - INT TERM EXIT
    else
         echo "Already running!"
    fi
    

crontab. Note that we start the dropbox daemon at system boot, and also once per day check to make sure that it is still running and restart if necessary. Also the monitor-blog.sh script will run indefinitely, but cron runs it every minute anyway, just in case -- it will exit immediately if another copy is still running. Also, since it creates a log, let's be a good citizen and rotate that log. Normally I don't like putting things in crontabs -- _especially_ user crontabs -- but in this case since I'm keeping the crontab file itself with the project I think it's ok.
    
    
    @reboot /home/technivore/bin/dropbox.py start
    @daily  /home/technivore/bin/dropbox.py running && /home/technivore/bin/dropbox.py start
    * * * * * /home/technivore/Dropbox/textfiles/blog/etc/monitor-blog.sh /home/technivore/Dropbox/textfiles/blog
    @daily  /usr/sbin/logrotate -s /home/technivore/tmp/logrotate.status /home/technivore/Dropbox/textfiles/blog/etc/logrotate.conf
    

logrotate.conf
    
    
    /home/technivore/tmp/blog-update.log {
        rotate 5
        copytruncate
        compress
        daily
        mail blog@technivore.org
    }
    

## Conclusion

Being able to blog on the iPad is flat out awesome. I'm sure there are plenty of blogging apps for it already but this setup works for me and it's fun to see the posts go up instantly without having to do anything. There are still some impedances to work through, the biggest one of which is that, as great as the extended keyboard in Editorial is, it's not match for a hardware keyboard. I did have to go back to vim on my MacBook a couple times to paste in the source code of the scripts, and I suspect that that will continue in the future in code-heavy posts. But for quick and dirty blogging, which I need to do more of, this is a wonderfully fun and responsive setup.
