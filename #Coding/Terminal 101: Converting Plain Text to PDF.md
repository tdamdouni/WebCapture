# Terminal 101: Converting Plain Text to PDF

_Captured: 2015-06-14 at 16:51 from [www.maclife.com](http://www.maclife.com/article/columns/terminal_101_converting_plain_text_pdf)_

![](http://www.maclife.com/files/u12635/terminal_101_teaser_53.png)

_Every Monday, we'll show you how to do something new and simple with Apple's built-in command line application. You don't need any fancy software, or a knowledge of coding to do any of these. All you need is a keyboard to type 'em out!  
_  
Occasionally, you may need to convert plain text files to PDF to more easily share them over the Internet or email. Sure, you could use the vast majority of applications with a printing feature coupled with OS X's ability to "Print to PDF," but if you're working in a command-line interface, there's a simple way to do it, and we'll show you how with two freely available tools: enscript and ghostscript.

### 1\. Installing enscript and ghostscript

Before you begin converting your files to PDF, you first need to install two command-line tools available from [Homebrew and MacPorts](http://www.maclife.com/article/columns/terminal_101_using_macports_and_homebrew): enscript (to convert the plain text files to postscript), and then ghostscript (to convert the postscript files into a PDF document).

![](http://www.maclife.com/files/u12635/pdf_1.png)

To do this, we'll use MacPorts, but you could also use Homebrew (simply replace "port" with "brew" in the commands below). To install these tools, use the following commands (one after another, followed by the enter key after each install):

    sudo port install enscript

    sudo port install ghostscript

### 2\. Converting to PostScript

![](http://www.maclife.com/files/u12635/pdf_2.png)

> _The first step to getting a PDF out of your plain text files is to have a plain text file converted to PostScript (PostScript is a file for outputting text for printing). To do this, you'll need a text file (.rtf, .txt, etc.), then run the following command in Terminal after installing enscript:_

    enscript -p inputFile outputFile

Replace "outputFile" with the path and name of the file that you wish to save the PS file as (be sure to include the ".ps" extension to the file name). Replace inputFile with the path and name of the file that you will be converting to PostScript (the text file to be converted).

So, for example, if we had a file on our Desktop to be converted called "Sample.rtf," we could use the following command to convert to PostScript:

    enscript -p ~/Desktop/Sample.txt ~/Desktop/Sample.ps

Running this command will generate a PostScript (.ps) file at the specified file path. Remember that converting an RTF document (or other formatted document) will not keep the formatting; instead, the formatting options will be printed inside of the file.

### 3\. Converting from PS to PDF

![](http://www.maclife.com/files/u12635/pdf_3.png)

> _Now we need to convert the PostScript file to PDF to complete the conversion process. To do this, you'll need to run the following command after installing ghostscript (also known as "ps2pdf"):_

    ps2pdf inputFile outputFile 

Replace inputFile with the PostScript path and filename (be sure to include the extension of .ps); replace outputFile with the path and filename of the PDF to be outputted (be sure to include the extension of .pdf).

For example, we'll convert our Sample.ps file into a PDF using the following command:

    ps2pdf ~/Desktop/Sample.ps ~/Desktop/Sample.pdf

![](http://www.maclife.com/files/u12635/pdf_4.png)

> _This will create a PDF on the Desktop that, when opened, will display the contents of the original .txt (or .rtf, .html, etc.) file that we converted to PostScript, and then finally into the PDF format, ready for sharing. Once the PDF has been created, you can delete the intermediary ".ps" file._

_Cory Bohon is a freelance technology writer, indie Mac and iOS developer, and amateur photographer. [Follow this article's author on Twitter](http://twitter.com/coryb)._
