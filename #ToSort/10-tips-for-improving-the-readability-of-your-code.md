# 10 Tips for Improving the Readability of Your Code

_Captured: 2017-10-14 at 20:34 from [dzone.com](https://dzone.com/articles/10-tips-how-to-improve-the-readability-of-your-sof?edition=333592&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-14)_

Making your code easier to read will also help you debug your own programs, making it easier on yourself.

Code readability is a universal subject in the world of computer programming. It's one of the first things we learn as developers. This article will detail the most important best practices when writing readable code.

## 1 - Commenting and Documentation

IDEs (Integrated Development Environments) have come a long way in the past few years. They've made commenting your code easier than ever. Following certain standards in your comments allows IDEs and other tools to utilize them in different ways.

Consider this example:

![](https://cdn.tutsplus.com/net/uploads/legacy/516_code/readable_code_1.png)

The comments I added at the function definition can be previewed whenever I use that function, even from other files.

Here is another example, where I call a function from a third party library:

![](https://cdn.tutsplus.com/net/uploads/legacy/516_code/readable_code_2.png)

In these particular examples, the type of commenting (or documentation) used is based on [PHPDoc](http://www.phpdoc.org/), and the IDE is [Aptana](http://aptana.org/).

## 2 - Consistent Indentation

I assume you already know that you should indent your code. However, it's also worth noting that it is a good idea to keep your indentation style consistent.

There is more than one way of indenting code. Here are two of the more common:

##### Style 1:

##### Style 2:

I used to code in style #2 but recently switched to #1. But that is only a matter of preference. There is no "best" style that everyone should be following. Actually, the best style is a consistent style. If you are part of a team or if you are contributing code to a project, you should follow the existing style that is being used in that project.

The indentation styles are not always completely distinct from one another. Sometimes, they mix different rules. For example, in [PEAR Coding Standards](http://pear.php.net/manual/en/standards.php), the opening bracket `"{"` goes on the same line as [control structures](http://pear.php.net/manual/en/standards.control.php); but, they also go to the next line after [function definitions](http://pear.php.net/manual/en/standards.funcdef.php).

#### PEAR Style:

Also, note that they are using four spaces instead of tabs for indentations.

[Here](http://en.wikipedia.org/wiki/Indent_style) is a Wikipedia article with samples of different indent styles.

## 3 - Avoid Obvious Comments

Commenting your code is fantastic; however, it can be overdone or just be plain redundant. Take this example:

When the text is that obvious, it's really not productive to repeat it within comments.

If you must comment on that code, you can simply combine it into a single line instead:

## 4 - Code Grouping

More often than not, certain tasks require a few lines of code. It is a good idea to keep these tasks within separate blocks of code, with some spaces between them.

Here is a simplified example:

Adding a comment at the beginning of each block of code also emphasize the visual separation.

## 5 - Consistent Naming Scheme

PHP itself is sometimes guilty of not following consistent naming schemes:

  * strpos() vs. str_split()
  * imagetypes() vs. image_type_to_extension()

First of all, the names should have word boundaries. There are two popular options:

  * **camelCase:** First letter of each word is capitalized, except the first word.
  * **underscores:** Underscores between words, like: mysql_real_escape_string().

Having different options creates a situation similar to the indent styles, as I mentioned earlier. If an existing project follows a certain convention, you should go with that. Also, some language platforms tend to use a certain naming scheme. For instance, in Java, most code uses camelCase names, while in PHP, the majority of coders use underscores.

These can also be mixed. Some developers prefer to use underscores for procedural functions, and class names, but use camelCase for class method names:

So again, there is no obvious "best" style. Just being consistent.

## 6 - DRY Principle

DRY stands for Don't Repeat Yourself. Also known as DIE: Duplication is Evil.

The [principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) states:

> "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system."

The purpose for most applications (or computers in general) is to automate repetitive tasks. This principle should be maintained in all code, even web applications. The same piece of code should not be repeated over and over again.

For example, most web applications consist of many pages. It's highly likely that these pages will contain common elements. Headers and footers are usually best candidates for this. It's not a good idea to keep copy-pasting these headers and footers into every page. [Here](http://screenr.com/YO7) is Jeffrey Way explaining how to create templates in CodeIgniter.

## 7 - Avoid Deep Nesting

Too many levels of nesting can make code harder to read and follow.

For the sake of readability, it is usually possible to make changes to your code to reduce the level of nesting:

## 8 - Limit Line Length

Our eyes are more comfortable when reading tall and narrow columns of text. This is precisely the reason why newspaper articles look like this:

![](https://cdn.tutsplus.com/net/uploads/legacy/516_code/newspaper.jpg)

It is a good practice to avoid writing horizontally long lines of code.

Also, if anyone intends to read the code from a terminal window, such as [Vim users](http://net.tutsplus.com/tutorials/other/venturing-into-vim-new-premium-video-series/), it is a good idea to limit the line length to around 80 characters.

## 9 - File and Folder Organization

Technically, you could write an entire application's code within a single file. But that would prove to be a nightmare to read and maintain.

During my first programming projects, I knew about the idea of creating "include files." However, I was not yet even remotely organized. I created an "inc" folder, with two files in it: `db.php` and `functions.php`. As the applications grew, the functions file also became huge and unmaintainable.

One of the best approaches is to either [use a framework](http://net.tutsplus.com/sessions/codeigniter-from-scratch/) or imitate their folder structure. Here is what CodeIgniter looks like:

![](https://cdn.tutsplus.com/net/uploads/legacy/516_code/readable_code_3.png)

## 10 - Consistent Temporary Names

Normally, the variables should be descriptive and contain one or more words. But, this doesn't necessarily apply to temporary variables. They can be as short as a single character.

It is a good practice to use consistent names for your temporary variables that have the same kind of role. Here are a few examples that I tend to use in my code:
