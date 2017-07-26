# Web Dev Zone

_Captured: 2017-05-13 at 08:59 from [dzone.com](https://dzone.com/articles/github-templates?edition=298091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-12)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

In today's web development world, Git is a powerful SCM ([Source Control Management](https://en.wikipedia.org/wiki/Version_control)). [GitHub](https://github.com/),\ is a web based Git SCM Provider. These guys play an important role in all open sourced projects, where you can see 95% of such projects.

[GitHub](https://github.com/)'s imporantce in ope-source projects is made evident by the soaring number of contributors. It's important to note that internet giants like [Facebook](https://github.com/facebook), [Google](https://github.com/google) and [Microsoft](https://github.com/microsoft) have created their own organizational pages and published their projects. Let's get to the point. In this post, we are going to discuss GitHub Templates.

## Why Do We Need Templates?

  1. GitHub introduces templates for their web forms (issues, pull requests, etc.), which can configure inputs to be pre-filled with data which will help maintainers to set up a [questionnaire](https://en.wikipedia.org/wiki/Questionnaire) and help contributors to do their part fast.
  2. It's hard and tough to solve a problem when important details about a contributor's project are missing in the [pull request](https://en.wikipedia.org/wiki/Distributed_version_control#Pull_requests) or in the issues folder. Both are web forms in GitHub where you can submit without an accompanying description, like below, which causes these contributions to become meaningless.
![](https://cdn-images-1.medium.com/max/1000/1*IrA43ipfi_pylAY9wDf2Fw.png)

> _Bad Request -- Pull Request with Empty Description_

Let's talk about the above **Pull Request** where the title and commit message says **Header Changes. **It's hard to fathom this code change by **Reviewers**. It may be a great contribution, but this kind of code will give only a rough idea of which issues are most imporant. It may introduce new defects because they are not very clear about the current and new behavior.

## How About With Description, Lets Have A look!

![](https://cdn-images-1.medium.com/max/1000/1*9qlzbOWNZYGXXyI4ux-4Sw.png)

> _Pull Request with Description_

Above is a good and descriptive pull request which can be easily understood. Our goal should be to value the contributions and issue requests which will be reviewed and merge faster than usual.

## So Github Templates Solve This Problem?

Yes. GitHub Templates help to configure your templates which will help to configure [questionnaires](https://en.wikipedia.org/wiki/Questionnaire). Now maintainers can add templates, but make sure your template file names are composed following proper naming conventions. Below is an example for an `ISSUE Template`.

![](https://cdn-images-1.medium.com/max/800/1*mgwHQ1NOGi8NR69GOil4RA.png)

It's always good to categorize your request as a pull request or an issue. Please read the `**Things you should know**` section for few more templates in various use cases provided by [GitHub](https://github.com/).

## Things You Should Know

  1. Add `PULL_REQUEST_TEMPLATE.md` for Pull Request Template.
  2. Add `Issue_TEMPLATE.md` for Issue Template.
  3. Add `CONTRIBUTING.md` for Contribution Guidelines.
  4. Add `CODE_OF_CONDUCT.md` for Setting Coding Standard Guidelines.
  5. Add `LICENSE` or `LICENSE.txt` for License.
  6. You can keep it in the root directory or move all of them under the directory called `.github`.
  7. A file extension is optional, but [Markdown](https://en.wikipedia.org/wiki/Markdown) files (.md) are supported.

## You Are Done, Checkout How it Looks!

![](https://cdn-images-1.medium.com/max/800/1*HXhhpOEIIfrIG5iaLJv4Cg.png)

![](https://cdn-images-1.medium.com/max/800/1*ZEV5veENVoubS2E9-2zhQw.png)

Cool, isn't it !!

Happy coding, stay tuned for the next one !

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
