# FluentCV Product Blog

_Captured: 2015-11-09 at 01:17 from [fluentcv.com](http://fluentcv.com/blog/)_

* Today I'd like to announce the release of FluentCMD, a **free, developer-friendly, open-source command line resume generator** for Windows, OS X, and Linux, now available on [GitHub](https://github.com/fluentdesk/fluentcmd) and [NPM](https://www.npmjs.com/package/fluentcmd).

To install it, just run:
    
    
    npm install fluentcmd -g
    

Or:
    
    
    sudo npm install fluentcmd -g
    

Once installed, you can generate themed resumes in HTML, PDF, Word, Markdown, and plain text format using something like:
    
    
    # Generate all formats
    fluentcmd resume.json -o out/resume.all -t modern
    

Output:
    
    
    *** FluentCMD v0.3.1 ***
    Reading JSON resume: resume.json
    Generating HTML resume: out/resume.html
    Generating TXT resume: out/resume.txt
    Generating DOC resume: out/resume.doc
    Generating PDF resume: out/resume.pdf
    Generating JSON resume: out/resume.json
    Generating MARKDOWN resume: out/resume.md
    

Check out the [official README](https://github.com/fluentdesk/fluentcmd) for more information.

FluentCMD is similar to JSONResume.org's [resume-cli](https://github.com/jsonresume/resume-cli) but with a different focus:

  1. **Local-only generation**. FluentCMD is a standalone tool, not a service.
  2. **Different theming infrastructure**. FluentCMD uses Watermark-style template-based themes, mostly because they're Jekyll ~compatible-ish.
  3. **Support for resume merging/inheritance**. FCMD can merge multiple source JSON resumes prior to exporting for use in targeted resume or resume inheritance scenarios. More on this shortly.

We use FluentCMD internally to tear off new updated versions (HTML, PDF, Word, Markdown, etc.) of our own resumes, mostly because it's simple and quick and works well in conjunction with versioning tools like [git](https://git-scm.com/). It's also used, under the hood, by [FluentCV Desktop](http://fluentcv.com/download).

* Welcome to the inaugural entry of the FluentCV blog.

FluentCV is a hackable, data-driven **resume authoring and career management tool** for the 21st century, currently in development and slated for release later this month (October, 2015). 

This will be the official channel for FluentCV updates and announcements. It will also be a venue for us to talk about software-assisted career analysis, job hunting, resume authoring, and identity management.

In the end, a resume is just a piece of paper. But a CV--a [curriculum Vitae](https://en.wikipedia.org/wiki/Curriculum_vitae)--is the story of your life. In 2015, with the prevalence of open data formats and standards like [JSON Resume](http://jsonresume.org), we believe that story is best told with the help of software.

We have an [RSS feed](http://fluentcv.com/feed.xml), if that's your thing. You can also find us on [Twitter](https://twitter.com/fluentdesk) and [GitHub](https://github.com/fluentdesk).

Thanks for stopping by and happy (job) hunting!
