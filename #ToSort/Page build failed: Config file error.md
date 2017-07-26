# Page build failed: Config file error

_Captured: 2016-04-03 at 03:21 from [help.github.com](https://help.github.com/articles/page-build-failed-config-file-error/#fixing-highlighting-errors)_

Once you've fixed any syntax errors in your __config.yml_ file, you will need to commit your changes and push to your GitHub Pages repository again to trigger another build on our servers.

###  Fixing highlighting errors

If you attempt to use a syntax highlighter other than [Rouge](https://github.com/jneen/rouge) on your GitHub Pages site with Jekyll, you'll receive a page build warning. GitHub Pages does not support other highlighters and will automatically use the default Rouge. For more information, see "[Using syntax highlighting on GitHub Pages](https://help.github.com/articles/using-syntax-highlighting-on-github-pages)."

To fix page build warnings, you must change your highlighter value to `rouge` in your __config.yml_ file.

  1. On GitHub, navigate to the main page of the repository.

  2. In your repository, browse to __config.yml_.

  3. In the upper right corner of the file view, click to open the file editor. 
  4. Find the line that starts with `highlighter:` and change the value to `rouge`. 

  5. At the bottom of the page, type a short, meaningful commit message that describes the change you made to the file. 

  6. Below the commit message fields, decide whether to add your commit to the current branch or to a new branch. If your current branch is `master`, you should choose to create a new branch for your commit and then [create a pull request](https://help.github.com/articles/creating-a-pull-request). 

  7. Click **Propose file change**. 

###  Further reading:

  * [YAML documentation](http://www.yaml.org/start.html)
