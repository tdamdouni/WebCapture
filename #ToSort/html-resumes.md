# HTML Resumes

_Captured: 2017-05-04 at 10:36 from [www.terrill.ca](http://www.terrill.ca/design/html_resume/)_

Each term thousands of co-op students at the University of Waterloo search for a new job. Every one of them must create an HTML version of their resume for use (abuse?) in Jobmine, our online job matching machine.

Most will use MS Word, or worse, and old version of Netscape Composer. Luckily HTML isn't PostScript and can be learned and written quite easily. Having helped countless students with their HTML woes it's time to be proactive and provide the proper resources to help make your own HTML resume. One to be proud of.

### 0\. Samples

### 1\. Whitespace

Your compulsion to preserve paper is noble, but it won't help you come evaluation time. If you're looking at your resume thinking - "There's a big white space, what can I put _there_?" resist the urge, and leave it blank.

Whitespace is important to the structure of a page. Try adding some vertical margin to your page headers. It will help separate sections and guide readers eyes.
    
    
        h2, h3 { margin-top:1em; }
        

Take advantage of the CSS support in new browsers. Define a max-width value to cut down the line length to something more "paper" like. Newspapers have thin columns for a reason, you know.
    
    
        body { 
        margin:1em;
        max-width: 50em;
        }
        

### 2\. Typography

Consistency is key. Choose your font wisely. Pick one that is widely adopted, one the viewer is likely to have, and specify a backup just in case they don't.

Sometimes one font just won't due. If you must use a second keep it in the family!

**Serif fonts:** Times New Roman, Georgia, Times, serif;  
**Sans-Serif fonts:** Arial, Helvetica, Verdana, Trebuchet MS, sans-serif

Increasing the line-height slightly can allow the piece to breath a little better. Use this in moderation.
    
    
        body { 
        line-height: 1.4em;
        }
        

Letter Spacing is one of the finer points, and when done properly goes completely un-noticed. Adjusting the space between letters and words can help alleviate some of the "squished" looked that bold titles often get.
    
    
        h1,h2,h3,h4{
        letter-spacing: .06em;
        }
        

Finally, make sure the default font size is sufficiently large to prevent reader eye strain. If you absolutely must prevent that line of text from wrapping then reword it! Don't decrease the font size. Remember to comb the final draft thoroughly for any sizing inconsistencies.

### 3\. Readability

Yes, there's more to readability than having the perfect font for the job. You need to make sure that the reader understands exactly what you mean.

Acronoyms and abbreviations are also a common place of fault. All too often I see an acronym such as NHMFL, and I think "sounds impressive, but I have no _clue_ what it means" (turns out it stands for "National High Magnetic Field Laboratory"). Acronyms are pronounced as a word, while abbreviations are spelled.

You have the ability to give the reader hints with HTML. Use this whenever you can!
    
    
        <acronym title="Document Object Model">DOM</acronym>
    
        <abbr title="PHP Hypertext Preprocessor">PHP</abbr>	
        

### 4\. Colour. Everything in moderation

You can't be too conservative when it comes to colour on a resume. Subtle variations from white or black work best. Stay away from colours which could elicit bad reactions from the reader. Be aware of common [moods associated with colours](http://iit.bloomu.edu/vthc/Design/psychology.htm). I would limit yourself to Black + 1 colour, if you must. Grey is useful for denoting less important or suplimental information. Doing this has the added benefit of making pure black text stand out more. Subtle gradients, or preferably none at all. No [patterns](http://terrill.ca/posts/backgrounds/). Even solids blocks of non-white are rarely a good idea.

Keep in mind that when it comes time to print, the design will likely be reduced to black and white.

Oh, and unless you're applying for a job at a morgue... it's best not to use light text on a dark background.

### 5\. Borders and Underlines

They are often used (and abused) to create structure on a page. When used correctly they can be icing on the cake, but all too often people end up with a broken box effect (or worse yet _parrallelograms!_).

Use both sparingly, and consistently (have I mentioned Consistency is key?). If one job title is underlined, then every job title better be underlined. Use the thickness of the border to denote the importance of division. Don't be affraid to use different border styles - they can have a very elegant effect.
    
    
        h2 {
        border-bottom: 1px dotted #999999;
        }
        

### 6\. Graphics, if you dare

There are a few acceptable opportunities to use a graphic in your resume.

  1. Custom bullets for lists can give it some flair. They allow you to be expressive, yet still functional. 
  2. A graphic at the end of the resume to indicate to the reader they have reached the end. The reader will also know they've not missed a page; something that can easily happen when printing out numerous resumes. 

### 7\. Check other browsers

For numerous reasons your resume is likely to be opened in a Microsoft browser. Clicking a link in most MS programs pops open IE 6 or 7. A companies IT department may restrict which browser people use. _Jobmine may restrict what browser people use._ The list goes on. Long story short; install as many of these browsers as you can, and make sure that it looks good on screen, and in the print preview. If you don't have access to one of these listed, ask a friend who does.

### 8\. Print style sheet

When you're finished creating your screen style sheet. Copy the entire thing into a new file that will be used for printing. Then you can start deleting things. Remove the max-width property you may have set earlier. Remove margins and padding on the outter most containers. Use all the available width of the page. Print is good like that - you get generous page padding by default.

Next check the length. Does it fit on two pages? If not there is probably something in there that shouldn't be. Watch the number of applicants to the job your applying. A rule of thumb is; the fewer applicants, the more time they will take to read each resume, and the longer your resume may be. If your the hundreth person to apply then shorten it up. The evaluator will be greatful you did.

### 9\. File Name

On more than one occasion I have been given a group of resumes via email. I saved them all to my computer, and then proceeded to go through the list (ordered by file name). The first resumes always get the most attention. So, if your name is Zack (starts with a Z) don't name the file zack.html, instead try naming the file something that will put you at the front of the line.

### 10\. Be Distinctive, not Unorthodox

You just _know_ that every other person applying for your job will be reading this. So it's your job to use these tips uniquely to make your resume distinctive. It may not help you get an interview, but it will help you once you've got one. **Caution:** an unorthodox resume will probably get tossed out like yestedays lunch. If you're applying to a marketing position you'll have more slack, but you math/CS'ers best be careful.
