# How to Jump Ship From Evernote and Take Your Data With You

_Captured: 2017-01-07 at 02:00 from [www.google.de](https://www.google.de/amp/lifehacker.com/how-to-jump-ship-from-evernote-and-take-your-data-with-1782841075/amp?client=safari)_

[Earlier this week](http://lifehacker.com/evernote-limits-device-sharing-for-free-users-bumps-up-1782744350), Evernote announced its subscriptions are getting more expensive and free users are now limited to just two devices. For the scores of existing users, that little restriction and that price increase are a big pain. Thankfully, you have other options.

Before you jump ship from Evernote, you'll want to pick which new tool for managing your notes and clippings is best for you. You have a few solid options here: The most obvious choice for most people is [Microsoft's OneNote](https://www.onenote.com/), which goes[ toe-to-toe with Evernote in most features](http://lifehacker.com/note-taking-showdown-evernote-vs-onenote-2016-editio-1765707423). If you're a dedicated Apple user totally inside their ecosystem, [Apple Notes](https://support.apple.com/kb/PH12081?locale=en_US) is a surprisingly robust option. Alternately, you can go a completely different direction with [something like plain text](http://lifehacker.com/i-still-use-plain-text-for-everything-and-i-love-it-1758380840) if you don't use Evernote's fancy features, or [Google Drive](https://www.google.com/drive/) if you're looking to dump a lot of long-form notes in a searchable format.

### How to Export Your Data Out of Evernote

Evernote has a handy export option built into its Windows and Mac apps (it's not available on their web app). With the exception of moving your data over to OneNote, the first thing you need to do is export your notes out of Evernote before you can import them into the new notes app of your choice:

  1. Download the Evernote app for [Windows or Mac](https://evernote.com/download/) and log into your account.
  2. Right-click a notebook and select "Export Notes."
  3. Choose the Evernote ENEX format to export everything as an organized file or HTML to export it as a set of web pages. ENEX is best for the import options we'll look at below.
  4. Repeat this for every notebook in your account.

If you have a lot of notes, this is a pretty tedious process, but it's the only way to get all your notes over to a new app with any sense of organization. If you don't care about bringing the notebook structure, you can just dump every note into a single file:

  1. Click the Notes bar 
  2. Click Edit > Select All 
  3. Right-click a note and select "Export Notes."

This will export every note you have into a single file.

### How to Move Everything to Microsoft OneNote

OneNote is the closest cross-platform competitor to Evernote. [You can do a ton with OneNote](http://lifehacker.com/how-to-master-microsoft-office-onenote-1768471983) and it can handle just about everything Evernote can. Good news for Windows users too, you can import your Evernote notebooks with Microsoft's importer tool:

  1. Download the [Evernote Windows application](https://evernote.com/download/), and Microsoft's [importer tool](http://lifehacker.com/how-to-master-microsoft-office-onenote-1768471983).
  2. If you haven't used it before, open up the Evernote app on Windows and let it download all your notes.
  3. Open up the importer tool.
  4. The importer tool will scan your hard drive for Evernote notes and display the notebooks it finds. Click the checkboxes next to all the notebooks you want to import and click Next.
  5. Enter your Microsoft credentials.
  6. Click Import.

That's it, the importer tool migrates all your notebooks over to OneNote for you. Everything should import over, including tags, attachments, and formatting. Right now, Mac users are out of luck for an automated tool. If you want to use OneNote, you can use a tool like [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and a [trial version of Windows](https://www.microsoft.com/en-us/software-download/windows10/) to run [Windows on your Mac](http://lifehacker.com/5938332/how-to-run-mac-os-x-on-any-windows-pc-using-virtualbox) for long enough to import your files, or you can skip below to the IFTTT method for a hacky way to force all your notes over.

### How to Move Everything to Apple Notes

Apple's made a [lot of strides with Apple Notes](http://lifehacker.com/all-the-stock-mac-apps-that-apple-has-quietly-made-usef-1764376667), and the once boring little app is now nearly as feature-rich as Evernote. The newest version of Apple Notes (the version included in [OS X 10.11.4](https://support.apple.com/kb/DL1869?locale=en_US)) also comes with an importer for Evernote files, which makes it easier to bring all your notes over. You still have to do this manually though:

  1. Export all your Evernote notebooks.
  2. Open up Apple Notes.
  3. Flick File > Import Notes... and select a file you saved from Evernote. If you want to preserve your notebooks, it's best to do each file individually. If you select all of them, it'll import all your notes into a single folder.

You'll likely need to do a little cleaning up of your notes after they're imported in. Tags didn't seem to come over for me when I did it, but at least all your images, links, and formatting _should_ appear in Apple Notes the same way it was in Evernote.

### How to Move Everything to Nimbus Note

[Nimbus Note](https://nimbus.everhelper.me/note.php) isn't as well known as Apple Notes or OneNote, but it works pretty much the same way. The only caveat is that the free plan only allows for 100 MB of uploads a month. Still, it has a lot of similar features to Evernote, and even has a [web clipper tool](https://nimbus.everhelper.me/clipper.php). While Nimbus Note has apps for [Chrome](https://chrome.google.com/webstore/detail/nimbus-notes/haafigbapbpbpnmgcknnmilaaaimggpk), [Windows Phone](http://www.windowsphone.com/en-us/store/app/nimbus-note-web/0c5dd4ac-3c41-46cd-9ac0-cda61bac7d01), [Android](https://play.google.com/store/apps/details?id=com.bvblogic.nimbusnote), and [iOS](https://itunes.apple.com/us/app/nimbus-notes/id828918459?l=uk&ls=1&mt=8), only the [Windows application](https://nimbus.everhelper.me/nimbus-note-windows.php) can import notes from Evernote:

  1. Open up Nimbus Note for Windows.
  2. Click File > Import > Evernote. 
  3. Select the files you exported earlier and click OK.

Nimbus Note will now import your Evernote notes, images, and to-do lists.

### Migrate Your Notes to Plain Text

If you only use Evernote to store boring old text files, you can output those as [Markdown-formatted plain text files](http://lifehacker.com/5943320/what-is-markdown-and-why-is-it-better-for-my-to-do-lists-and-notes). To do this, you'll need a [little command line know-how](http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything) and a utility called [ever2simple](https://github.com/claytron/ever2simple). Ever2simple was initially created as a way to import Evernote files into [Simplenote](https://simplenote.com/), but Simplenote no longer supports importing TXT files, so it's useless for that. Still, you can use the TXT files it creates in any text editor. If you _really_ want to give Simplenote a try, you can import the TXT files ever2simple generates with a third-party utility like [nvALT on Mac](http://brettterpstra.com/projects/nvalt/) or [RosephNotes](http://www.resoph.com/ResophNotes/Welcome.html) on Windows. First, you need to install ever2simple:

  1. Make sure you have [Python installed on your computer](https://www.python.org/downloads/) (yes, we know)
  2. Open up your Terminal app. Type `pip install -U ever2simple` and wait for ever2simple to install everything it needs.

Now, you need to run a command in your Terminal application to convert the files you exported from Evernote above into plain text files. In Terminal, type this command, substituting `my_evernote.enex` for your ENEX file and `notes_dir`for directory you want your notes to export to:
    
    
    ever2simple my_evernote.enex --output notes_dir --format dir

This creates a ton of different TXT files that you can open in your [text editor of choice](http://lifehacker.com/five-best-text-editors-1564907215), and organize accordingly.

### Migrate Your Notes Over to Google Drive, Day One, Dropbox, and More Using IFTTT

If none of the above notes apps are appealing to you, you can hack together a way to send all your Evernote notes to a variety of apps using the automation tool, [If This Then That](https://ifttt.com) (IFTTT). This way, you can export your Evernote notes to any app IFTTT supports.

This is a multi-step process where you'll first create an IFTTT recipe, then go into Evernote and add a tag to all the notes you want to import. First, pick an IFTTT recipe for the notes app you want to use. Here are a few:

  * **[Evernote to Dropbox**](https://ifttt.com/recipes/415760-evernote-to-dropbox) (turns each note into a TXT file in your Dropbox folder)
  * **[Evernote to OneNote**](https://ifttt.com/recipes/419118-evernote2onenote) (this is useful if you only have access to a Mac)
  * **[Evernote to Google Drive**](https://ifttt.com/recipes/341266-if-the-note-has-a-tag-upload-it-to-gdrive) (turns each note into a Google Docs document, Google Keep does not currently have an import option)

Once you pick the recipe you want to use, it's time to set it up:

  1. On the recipe's page, click the "Advanced Settings."
  2. Under the Trigger option, look for "Specific Tag." Type in a tag here, like "movetogoogledrive."
  3. Click the Add button at the bottom of the page on IFTTT.
  4. Open up Evernote. 
  5. Select a group of notes you want to export, and add the tag you entered in step two.
  6. Head back to IFTTT's [My Recipes page](https://ifttt.com/myrecipes/personal) and click the Check Recipe Now button next to your recipe to force it to update. 

IFTTT will pull all the Evernote notes you added that tag to into your new notes app. You'll likely need to clean up and organize when you're done doing this, but at least you won't have to copy-and-paste each note manually.

Leaving Evernote might seem like a daunting task, and once you get all your notes into your new app, you'll need to spend some time getting to know how they work. Still, most of the above options are free and offer the bulk of Evernote's most popular features, so you should be able to fill that hole in your heart easily enough.

_Illustration by Sam Woolley._
