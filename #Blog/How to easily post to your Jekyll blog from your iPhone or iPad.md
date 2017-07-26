# How to easily post to your Jekyll blog from your iPhone or iPad

_Captured: 2015-10-30 at 10:19 from [www.hardscrabble.net](http://www.hardscrabble.net/2015/how-to-jekyll-from-ios/)_

## Caveats:

  * This solution doesn't support Octopress, only Jekyll
  * This solution assumes you're hosting your blog on GitHub

## Steps

  * One-time setup 
    * Download [Editorial](http://omz-software.com/editorial/)
    * Install the [Publish Jekyll Post](http://www.editorial-workflows.com/workflow/5838419494174720/XyeFJfsyXwE) workflow I've just created
    * Tap the wrench to see the list of workflows
    * Find the newly installed "Publish Jekyll Post" workflow
    * We need to configure the workflow with your info. Try running it, and it will complain that you haven't provided a GitHub API access token. It will offer to open Safari on the page where you can create a new access token. Do that, and copy it to your clipboard. Note: the only necessary permission is "public_repo", assuming your repo is public, which it almost certainly is. You can revoke this token at any time to cut off the workflow.
    * Return to Editorial
    * Tap the "i" info button for the workflow
    * Tap "Edit Workflow"
    * Find the step called "Configure Access Token" and tap to expand it. There's a text box there where you can paste in your access token.
    * Scroll down to the "Configure Repo" step and tap to expand that one as well. There, write in your GitHub username and the name of the repo you'd like to add posts to.
  * Now that configuration is done, just create a new document in Editorial and write your post. You are responsible for providing the YAML front matter (the block at the top with the title and date)
  * Run the workflow. 
    * You will be asked what the file name should be. The workflow makes a smart guess: `_posts/2015-04-02-whatever-the-file-name-is.md`, but you can change it.
    * You will be asked what the commit message should be.
    * The workflow will then create the file in your repo and, upon success, offer to open that file on GitHub.

If you have any problems or ideas, please open an issue on the project's GitHub repo: <https://github.com/maxjacobson/github-pages-editorial>
