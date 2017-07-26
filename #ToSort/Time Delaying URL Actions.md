# Time Delaying URL Actions

_Captured: 2016-08-10 at 09:41 from [unapologetic.io](http://unapologetic.io/posts/2014/01/20/time-delaying-url-actions/)_

[UN](/)

[AP](/)

[OL](/)

[OG](/)

[ET](/)

[IC](/)

(▼)(▲)  
On the off chance that you both found this area and also still enjoy playing [Letterpress](https://itunes.apple.com/us/app/letterpress-word-game/id526619424?mt=8&uo=4&at=11lpto), I'm @ajguyot on Game Center, try me.  
  

  * [Home.](/)
  * [About.](/about)
  * [Archive.](/archive)
  * [Contact.](/contact)
  * [Rss.](/rss)
* * *

[

## Time Delaying URL Actions

](/posts/2014/01/20/time-delaying-url-actions/)(▼)(▲)

  * ![](/icons/Permalink.png)Permalink
  * ![](/icons/ADN.png)App.net
  * ![](/icons/Twitter.png)Twitter
  * ![](/icons/Facebook.png)Facebook
  * ![](/icons/Google+.png)Google+
  * ![](/icons/Pocket.png)Pocket
  * ![](/icons/Instapaper.png)Instapaper
  * ![](/icons/Email.png)Email

January 20, 2014

Early last year I posted [The Due Later Action Series](http://theaxx.net/duelaterseries) on The Axx. The basic concept was to use the URL scheme of the timer app [Due](http://dueapp.com), combined with Drafts, to time delay the launching of a particular action. While the implications of such a workflow were powerful, I was never quite happy with the implementation. First off, I've never much liked the Due UI, and especially now that it has still not been updated for iOS 7, I prefer to avoid ever having to look at the app. Secondly, after the Due notification would go off, just tapping it would not launch the action. Instead, tapping it would launch Due and you had to check off the reminder as complete, then accept a modal dialogue before the URL action would be executed. Finally, while Due could parse a natural language description of the time to launch the action, you had to remember to double tap the reminder before you created it in order for that parsing to come into effect. I often forgot this double tap and ended up ruining the entire process. Overall the workflow was delicate, finicky, and unforgiving of the slightest error in the complicated steps to make it work.

That was in early 2013, and since then iOS automation has come a long, long way. Today I'm releasing a new workflow for time delaying your URL actions. This one no longer requires Due, and therefore can bypass all of the frivolous extra steps and having to look at the iOS 6 UI. I've been using the workflow myself for the past few days, and I find it is simple and straightforward enough that I actually use it and enjoy its benefits.

## Using Pythonista and Launch Center Pro to Time Delay URL Actions

[Pythonista 1.3](http://www.macstories.net/reviews/pythonista-1-3-brings-camera-roll-and-notification-center-support-new-library-view-and-more/), released in February 2013, came with a module to script notifications on iOS devices. This would probably have been a better choice to use for the original Due Later Action series back then too, but I didn't know any Python yet, Drafts didn't have any options to separate more lines than just the first and all the others, and [Launch Center Pro 2.1](http://www.macstories.net/reviews/launch-center-pro-2-1-fleksy-keyboard-lists-photo-attachments-and-share-sheets/) had not been released, either. (▼)(▲)It's also possible I just liked the pun in the title. LCP 2.1 brought a way to pop up a list of choices when running actions. Your choice in the list would change the action that was run based on the value attached to that choice. Using a combination of that list feature in LCP, along with its ability to label prompt boxes and utilize the number pad keyboard, we can remove the need to remember exactly how to format a plain text Draft to properly time delay an action. It's still possible to run the action from Drafts if you're not an LCP user, or if you're on an iPad, but the process is not quite as simple in that case. Regardless, I'll describe both methods below.

## Running Time Delayed Action from Launch Center Pro

Running the Time Delayed Action action from LCP requires only one action, but you'll need to edit it based on the actions you want to be running. The raw code for my version of the action looks like this:

`pythonista://Time_Delay?action=run&argv=[prompt:Text for Action]&argv=[list:Choose Action to Run|Cross Post|Tweet: ajguyot|Tweet: the_axx|Post to App.net]&argv=[prompt-num:Hours to Delay]`

This action will launch Pythonista and send three parameters to the "Time_Delay" script. The first parameter, as labeled by LCP, is "Text for Action", and should be self explanatory. The second parameter may be a little more confusing. It uses Launch Center Pro's list feature to allow you to choose which action to run. In this case it gives the option to run "Cross Post", "Tweet: ajguyot", "Tweet: the_axx", or "Post to App.net. Whichever choice is made will send that exact text to Pythonista. If you want to send different text than appears in the dialogue box, place an equal sign after the text, then the actual value to be sent. For example, `[list:Choose Action to Run|Tweet=Tweet: the_axx]` would display a dialogue titled "Choose Action to Run" with one option: "Tweet". Choosing this option would send the text "Tweet: the_axx" instead of "Tweet". If you don't include an equal sign, the text sent is identical to what is displayed as the option in the dialogue. Also important, make sure not to encode the titles of your actions in this list, the Python script will do that for you later.

For the final `&argv=` in the code, LCP will display a number pad prompt and ask how many hours you want to delay your action by. Pythonista can't parse natural language (or at least, I don't want to, nor would I likely be able to write a script that might allow it to do so), so we time delay based on hours instead of selecting an actual time and date. I actually like this implementation better. If it's late at night and I want to post a Tweet when I wake up in the morning, I just time delay by an hour or two, for a time when I know I'll be asleep, and the notification will be waiting for me in the morning.

When the notification does pop up, it displays in the form "Run [[action]] on [[text]]". So if I chose to Cross Post the text "Hello World", the notification that pops up would say "Run Cross Post on Hello World", and tapping it would automatically do exactly what it says. This method avoids confusion if you set up multiple time delayed actions for the same time, or at different times but you don't look at your device until multiple actions are queued up. Now you can remember exactly what each action is going to do. If the text is too long it gets cut off, but enough should still be displayed for you to remember what it was saying.

Once your action has been scheduled, the script also appends the same text, "Run [[action]] on [[text]]" to a file called "Scheduled Actions" in Pythonista. This way if you decide you want to change the text, post it early, or not post it at all between the time you schedule the action and the time it goes off, you can still retrieve your text from the file in Pythonista.

## LCP Actions

Make sure to edit the code of this action and switch out the placeholder options with your own action options. You can add more than the four placeholders by placing more pipe characters followed by more actions at the end, or you can remove actions if you don't want that many. By default the script is running a basic Drafts action of the form `drafts://x-callback-url/create?text=[[text]]&action=[[action]]`, where [[text]] is replaced by your text and [[action]] is replaced by one of the action options you write into the main Launch Center Pro action. This means that you can use any Drafts action in your library for these options, so don't feel limited to just time delaying social media posts. (▼)(▲)As an example, I'll be using this workflow to time delay posts to Unapologetic. I write a lot of my posts on weekends or at 2 or 3 in the morning, and posting at these times is not optimal, as many people don't end up seeing the tweets. The ability to time delay the posts to a better time and then post them with a single tap will be really nice. Furthermore, if you want to time delay an action for an app that is not Drafts, you can read the comments in the Python script to find the one line to change in order to use a different base URL.

[Direct Import Link for "Time Delayed Action" Action](launchpro://import?url=pythonista%3A%2F%2FTime_Delay%3Faction%3Drun%26argv%3D%5Bprompt%3AText%20for%20Action%5D%26argv%3D%5Blist%3AChoose%20Action%20to%20Run%7CFIRST%20ACTION%7CSECOND%20ACTION%7CTHIRD%20ACTION%7CFOURTH%20ACTION%5D%26argv%3D%5Bprompt-num%3AHours%20to%20Delay%5D&title=Time%20Delayed%20Action)

## Pythonista Script

Make sure to title your Pythonista script "Time_Delay", or the actions won't call the right script.

    
    
    import sys
    import notification
    import webbrowser
    import console
    import urllib
    
    # Receive parameters from Drafts or Launch Center Pro and assign them to variables.
    text = sys.argv[1]
    action = sys.argv[2]
    delay = sys.argv[3]
    
    # Convert delay time into hours.
    hours = float(delay) * 3600
    
    # Encode action and text so they can bed used in URL action.
    encoded_action = action.encode('utf-8')
    encoded_action = urllib.quote(encoded_action, safe='')
    
    encoded_text = text.encode('utf-8')
    encoded_text = urllib.quote(encoded_text, safe='')
    
    # Create URL. You can change this from a Drafts action to be something else if it better fits your needs.
    url = 'drafts://x-callback-url/create?text=' + encoded_text + '&action=' + encoded_action
    
    # Schedule notification.
    scheduled = notification.schedule('Run ' + action + ' on "' + text + '"', hours, 'default', url)
    
    # Append text for action and what action was run on it to a file called "Scheduled Actions" in Pythonista.
    scheduled_actions = open('Scheduled Actions', 'a')
    scheduled_actions.write(action + ' on "' + text + '"\n')
    scheduled_actions.close()
    
    # Return you to source app after action is scheduled. (Delete these last lines to just stay in Pythonista.)
    webbrowser.open('launchpro://')
    #webbrowser.open('drafts://')
    # Uncomment line 35 and comment line 34 to open Drafts after success instead of Launch Center Pro.
    

## Running Time Delayed Action from Drafts

If you want to time delay actions starting from Drafts instead of Launch Center Pro, things become a little more complicated. For starters, Drafts does not have the list feature that LCP does, so we have to either reserve a line to type the title of the action we want to run every time we run it (i.e., line 1 would be the actual typed title of the action to run, line 2 would be the number of hours to delay, and line 3 until the end would be the text to send for the action), or have a multitude of different actions specifically to time delay each type of action (e.g., have a "Time Delay Cross Post" action, a "Time Delay Tweet" action, a "Time Delay Post to App.net" action, etc.).

I can't choose which option is better for you, as both of them have pros and cons. If you have to manually type the action to run every time you want to schedule a time delayed action, then a single character typo would ruin the entire process. However, if you have a separate action for every single type of time delay you might want to use, then your action list quickly becomes very cluttered. Since neither option is perfect, I'll provide you with the code for both and you can pick which one you want to use yourself.

Don't forget that regardless of which way you want to run Time Delay Action, you still need to add the same Python script from above to your Pythonista library.

## Drafts Actions

First is the action in which you have to hard code which action you want to time delay into every draft before you run it. This action requires no manual changes on your end after importing, but when you run it make sure that line 1 of your draft is the action you want to run, unencoded, but with NO typos (even a mistyped capital letter or an extra space at the end will ruin the action). Line 2 should be a single number representing the number of hours for which you want to delay your action, and the remaining lines will all be used for the text of your action. (▼)(▲)An advantage over LCP here is that you can time delay actions on multi-line text. The Launch Center Pro prompt keyboard does not have a return key, to my continued annoyance, so the only way to send multi-line text with it is if you paste in line breaks.

[Direct Import Link for "Time Delayed Action" Action](drafts://x-callback-url/import_action?type=URL&name=Time%20Delayed%20Action&url=pythonista%3A%2F%2FTime_Delay%3Faction%3Drun%26argv%3D%5B%5Bline%7C3..%5D%5D%26argv%3D%5B%5Bline%7C1%5D%5D%26argv%3D%5B%5Bline%7C2%5D%5D)

If you've decided that hard coding the action into every draft to time delay is the better direction, you don't need to read the rest of this. Otherwise, the following action will be for those of you who wish to have specific time delay actions for each type of action to delay. This method _will_ require you to tweak your action's code after importing it. Below I am providing a single template action. The template will use line 1 of your draft (which should be a single digit and no more) as the number of hours to delay your action, and line 2 and further as the text for the action. After importing, you'll need to change the code after the _second_ `&argv=` to whichever action you want to run. (The words "ACTION TITLE" in all caps is in the code in the exact spot you need to change, so find those words and swap them with your chosen action title.) You will probably also want to change the title of the action to match whatever you're time delaying with it. If you want multiple actions set up, import the template code multiple times and change each one to the action you desire.

[Direct Import Link for "Time Delayed Action Template" Action](drafts://x-callback-url/import_action?type=URL&name=Time%20Delayed%20Action%20Template&url=pythonista%3A%2F%2FTime_Delay%3Faction%3Drun%26argv%3D%5B%5Bline%7C3..%5D%5D%26argv%3D%7B%7BACTION%20TITLE%7D%7D%26argv%3D%5B%5Bline%7C2%5D%5D)

* * *

Un

ap

ol

og

et

ic 

is written by Alex Guyott
