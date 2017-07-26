# Updating your Markdown processor to kramdown

_Captured: 2016-04-03 at 03:15 from [help.github.com](https://help.github.com/articles/updating-your-markdown-processor-to-kramdown/)_

If you are not already using [kramdown](http://kramdown.gettalong.org/), Jekyll 3.0.0's default Markdown processor, then you must update your Markdown processor in your __config.yml_ file.

**Note:** Starting May 1st, 2016, GitHub Pages will _only_ support [kramdown](http://kramdown.gettalong.org/).

[GitHub-flavored Markdown](https://help.github.com/articles/github-flavored-markdown/) is supported by kramdown by default, so you can use Markdown with GitHub Pages the [same way you use Markdown on GitHub](https://help.github.com/articles/about-writing-and-formatting-on-github/).

If you're currently using Markdown processors that support GitHub-flavored Markdown, such as [Rdiscount](https://github.com/davidfstr/rdiscount) or [Redcarpet](https://github.com/vmg/redcarpet), then you don't need to change your Markdown files for them to render properly. Instead, change the Markdown setting in your site's configuration file.

  1. On GitHub, navigate to the main page of the repository.

  2. In your repository, browse to __config.yml_.

  3. In the upper right corner of the file view, click to open the file editor. 
  4. Find the line that starts with `markdown:` and change the value to `kramdown`. 

  5. At the bottom of the page, type a short, meaningful commit message that describes the change you made to the file. 

  6. Below the commit message fields, decide whether to add your commit to the current branch or to a new branch. If your current branch is `master`, you should choose to create a new branch for your commit and then [create a pull request](https://help.github.com/articles/creating-a-pull-request). 

  7. Click **Propose file change**. 

For more information on using kramdown, see [kramdown's quick reference guide](http://kramdown.gettalong.org/quickref.html) or [kramdown's official documentation](http://kramdown.gettalong.org/documentation.html).
