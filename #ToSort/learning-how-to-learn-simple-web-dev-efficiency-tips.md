# Learning How to Learn: Simple Web Dev Efficiency Tips

_Captured: 2018-08-16 at 20:57 from [dzone.com](https://dzone.com/articles/learning-how-to-learn-simple-web-dev-efficiency-ti?edition=385381&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-08-16)_

[Learn how error monitoring with Sentry](https://dzone.com/go?i=299453&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) closes the gap between the product team and your customers. With Sentry, you can focus on what you do best: building and scaling software that makes your users' lives better.

What is being a developer all about? Is it about memorizing syntax? Is it about being able to refactor inefficient code? Is it about making handy little shortcuts for yourself? Learning from the wisdom of the mighty developers here at Planet Argon has better equipped me with some tools to be able to answer these questions and I have come to learn it is all of these things…and none of them.

When you are working with existing web applications that you did not originally build, each project has its own quirks and nuances. There are so many tools, languages, frameworks, libraries, etc. that you can't possibly master them all, not to mention they are always changing. Development isn't necessarily about what you already know, but rather about your fundamental ability to learn the next thing you'll need to know to move forward.

Perhaps one of the most important ways to learn is to be efficient. When I started as an intern at Planet Argon I was still scrolling through applications looking for the thing I needed in each folder. I found myself searching as if I were still working in small tutorial-sized applications. However, real-world applications, with a large backend, are a different story.

**It seems like a trivial thing to worry about tiny commands just to save a little time, but it really does add up.**

Here are a few simple commands and tips to make you more efficient:

  * **Command 'P'** will search directly for any file containing the word you're looking for such as a model, or controller. For example searching for "user" to find User.rb.

  * **Command shift 'F'** will globally search the application for any particular word you are looking for. If what you're looking for isn't in the name of the file but you aren't sure where it lives this is your best option. Editors will usually have an area to specify a particular path as well so you can do a search only within a certain directory.

  * **Command 'F'** will search locally within whatever file you are currently looking at. This is great when the file is massive but you need to find the location of something like a unique id.

So now you can save some time bouncing around the application in the editor, but what about the terminal?

Don't be a noob like I once was and type out full file names. Start typing the file name then press tab for autocomplete. For instance: if you know there is only one file that starts with a "p" in your current directory then type "p" and press tab and it will complete the file name. If there are more than one and you press tab it will show you which files exist that start with "p".

What about finding some particular returned data in the terminal from a query of some kind? Say you are looking for a particular route relating to "home_page" so you run "rake routes" but you just get a mountain of routes which you have to scroll through until you see "home_page".

Rather than putting yourself through that misery try grepping instead! Run `rake routes | grep home_page` this will make sure that your terminal only returns routes that contain "home_page".

But what if that is not efficient enough for you? Why not conserve energy and save your tired little fingers? You currently have to type out `rake routes | grep home_page` every single time you want to search for that route. Well, luckily, you can create an alias! An alias is a short name that has a direct reference to a specific syntax.

Creating one is relatively simple. You'll need to save your alias somewhere, usually in .bashrc, .bash_profile, or,, if you are using Oh My Zsh (highly recommended), its stored in your .zshrc. Start by typing `vim .bashrc` to open the file up in your terminal-based editor. Press 'i' to be able to write in the file. You can name your alias however you want, in this case I'm going to name it "grepr" so I'll remember that means "grep routes." Type out `alias grepr="rake routes | grep"`. Press esc to exit insert mode then type ":wq" to save to the file and exit the editor. When you close, reopen your terminal and navigate back to your application's directory you will be able to type `grepr home_page` and it will behave exactly the same as `rake routes | grep home_page`.

If you can find what you're looking for faster you'll have more time to investigate whatever weird issue you are trying to solve. If you are new to development hopefully some of these tips help you in your own journey. Keep learning and stay cool!

[What's the best way to boost the efficiency of your product team](https://dzone.com/go?i=299454&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) and ship with confidence? Check out this [ebook](https://dzone.com/go?i=299454&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) to learn how Sentry's real-time error monitoring helps developers stay in their workflow to fix bugs before the user even knows there's a problem.
