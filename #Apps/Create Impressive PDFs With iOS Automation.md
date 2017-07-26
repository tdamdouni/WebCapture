# Create Impressive PDFs With iOS Automation

_Captured: 2015-11-20 at 12:35 from [techstreams.github.io](http://techstreams.github.io/2015/11/13/create-impressive-pdfs-with-ios-automation/)_

I love iOS automation. There are so many amazing possiblities.

In a [previous post](http://techstreams.github.io/2015/10/01/create-impressive-google-docs-on-the-go/), I detailed an **_Impressive Google Docs_** workflow I created using [Drafts](http://agiletortoise.com/drafts/), [Markdown](https://daringfireball.net/projects/markdown/) and [Google Fonts](https://www.google.com/fonts#AboutPlace:about).

> Clever, flexible Google Doc action (with good write up) from [@techstreams](https://twitter.com/techstreams): <http://t.co/b42FNKIgvP>
> 
> -- Drafts (@draftsapp) [October 2, 2015](https://twitter.com/draftsapp/status/649912882247827456)

Combining a modified version of this [original Drafts action](http://drafts4-actions.agiletortoise.com/a/19v) with an _action extention workflow_ developed with the [Workflow](https://workflow.is/) app, I'm now able to create **Impressive PDFs**.

Interested? Read on.

### How To Create Impressive PDFs

> ... _with Drafts, Markdown, Google Fonts and Workflow_

![](http://techstreams.github.io/images/2015-11-13-impressive-pdf.png)

**STEP 1**

Install the following apps on your iOS mobile device:

_For more on **Drafts** see [iOS Automation with Drafts](http://techstreams.github.io/2015/09/03/ios-automation-with-drafts/)._

_For more on **Workflow** see [iOS Automation with Workflow](http://techstreams.github.io/2015/04/06/ios-automation-with-workflow/)._

`~~~`

**STEP 2**

After app installation:

  * Install the **[Impressive PDFs Drafts Action](https://drafts4-actions.agiletortoise.com/a/1a2)** from the _[Drafts Action Directory](https://drafts4-actions.agiletortoise.com)_

  * Install the **[HTML to PDF](https://workflow.is/workflows/35d87231e09f4a6f9d11bdca0a2510b7)** workflow

_Ensure that there are no other workflows with the name **HTML to PDF** resident within the [Workflow](https://workflow.is/) app or you may encounter an issue._

`~~~`

**STEP 3**

Enter document content into **Drafts** using markdown.

Looking for an example? Try this markdown:
    
    
    # Test PDF
    
    ---
    
    It's easy to create ***Impressive PDFs*** with:
    
    * Drafts
    * Markdown
    * Google Fonts
    * Workflow
    
    ---
    
    ### Try A Table
    
    | Column 1 | Column 2 |
    | :------: | :------: |
    | One      | Two      |
    | Three    | Four     |
    

_For an introductory markdown tutorial, see [Simplify Writing with Markdown](http://techstreams.github.io/2015/09/21/simplify-writing-with-markdown/)._

_For more on editing in Drafts, see the [Basics of Navigating Drafts](https://agiletortoise.zendesk.com/hc/en-us/articles/203530077-Basics-Navigating-Drafts)._

_If you need better document element separation/spacing, use the `<br>` line break tag between elements when creating your markdown content. To assist, I've created a convenient `<br>` [Drafts Key](https://agiletortoise.zendesk.com/hc/en-us/articles/202865034-Using-the-Enhanced-Keyboard) which can be installed from **[here](http://drafts4-actions.agiletortoise.com/k/19h)**._

`~~~`

**STEP 4**

In **Drafts**, run the installed **[Impressive PDFs Drafts Action](https://drafts4-actions.agiletortoise.com/a/1a2)** on the completed markdown content.

_See the [Basics of Navigating Drafts](https://agiletortoise.zendesk.com/hc/en-us/articles/203530077-Basics-Navigating-Drafts) for more information on running Drafts Actions._

![](http://techstreams.github.io/images/2015-11-13-drafts-action.png)

When the action runs, you'll be prompted for **_three_** items:

**1) [Google Font](https://www.google.com/fonts) to use for document styling**

> Enter the desired [Google Font](https://www.google.com/fonts) name or leave the default _[Roboto](https://www.google.com/fonts/specimen/Roboto)_ font.
> 
> In addition to _[Roboto](https://www.google.com/fonts/specimen/Roboto)_, here are a few of my other favorite fonts:
> 
> _Not all Google Fonts may be supported._
> 
> _Google Font thickness, slant and width are not supported by this action._

**2) Document headings color**

> Enter the name of a color _(e.g., red)_ or an [html color hex code](http://www.w3schools.com/html/html_colors.asp) _(e.g., #FF0000 for red)_. **_Leave #000000 for the default color black._**
> 
> _Document headings are created with markdown. See the [Simplify Writing with Markdown](http://techstreams.github.io/2015/09/21/simplify-writing-with-markdown/) post for additional information._

**3) Document body text color**

> Enter the name of a color _(e.g., red)_ or an [html color hex code](http://www.w3schools.com/html/html_colors.asp) _(e.g., #FF0000 for red)_. **_Leave #000000 for the default color black._**

After completing each prompt:

  * Press the **OK** button to continue  

  * Press the **Cancel** button to exit and return to **Drafts**

`~~~`

**STEP 5**

The **[Impressive PDFs Drafts Action](https://drafts4-actions.agiletortoise.com/a/1a2)** will now **_automatically_** pass the document content to the **[HTML to PDF](https://workflow.is/workflows/35d87231e09f4a6f9d11bdca0a2510b7)** workflow to create the PDF.

![](http://techstreams.github.io/images/2015-11-13-workflow.png)

When the workflow runs:

**1) A _Preview_ will display once PDF generation is complete**

> Click the **Done** link in the top left corner to continue.

**2) You will be prompted for a name for the generated PDF**

> Enter a new name or leave the _default_ value.
> 
> Press **OK** to continue. Press **Cancel** to exit the workflow and return to **Drafts**.

**3) An _Action_ prompt will display**

>   * _**Share:** select to share PDF (e.g., email, message, ...)_
>   * _**Open In App:** select to open PDF in another app (e.g., [Google Drive](https://itunes.apple.com/us/app/google-drive-free-online-storage/id507874739?mt=8), [Evernote](https://itunes.apple.com/us/app/evernote/id281796108?mt=8), [Dropbox](https://itunes.apple.com/us/app/dropbox/id327630330?mt=8), [iBooks](http://www.apple.com/ibooks/), ...)_
>   * _**Cancel:** cancel workflow_

You will be returned to **Drafts** once the workflow is complete.
