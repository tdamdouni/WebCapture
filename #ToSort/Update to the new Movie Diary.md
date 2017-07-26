# Update to the new Movie Diary

_Captured: 2016-03-26 at 19:49 from [onetapless.com](https://onetapless.com/update-new-movie-diary)_

It feels like yesterday when I [released](https://onetapless.com/new-movie-diary-with-airtable) the new Movie Diary using [Airtable](https://airtable.com/invite/Vnohp0jk) and [Pythonista](https://itunes.apple.com/us/app/pythonista/id528579881?mt=8&uo=4&at=10l4KL) and the feedback has been great. I recognize that plugging into Airtable is challenging even with a video, so don't be afraid to [poke me on Twitter](https://twitter.com/pgruneich) for aid. Now enjoy the new version.

This new version is almost a rewrite and has better error reporting, accepts external arguments

and brings a new setup screen where you can plug all your API keys and database IDs. In this new configuration dialog you can also request to set the date manually and to include the time of the entry in the date.

As a bonus, four new fields: **Genres**, **Cast**, **Runtime** and **IMDB URL** and you can toggle the ones you want

in the same configuration dialog. The first time you run the script after the update you'll see the new setup even if you configured the Movie Diary earlier. Don't worry, you won't need to collect keys, ids and tables again, the new version fills the fields with existing data.

> **Feb 23**: Updated once again with a couple new features: now you can customize the names of the fields, so you can name your fields as you like in Airtable, just use the same name for the fields in the script. You can configure this from the configuration panel, and now you can access it anytime: run the Movie Diary from Pythonista, when prompted to search a movie, press OK to continue with an empty field, then you'll get the configuration panel.
> 
> **Feb 22**: I forgot to mention but [Jimmy Reekes](https://twitter.com/jmreekes) reminded me to tell you that you must create these new fields in your Airtable table for them to work. _Genres_ and _Cast_ require a homonymous **Single Line Text** field each; _Runtime_ is supposed to be an eponymous **Number** field and _IMDB URL_ is an **URL** field named **IMDB**. If you don't create the fields the script will raise an "Invalid Data" exception pointing to the fields it couldn't find. In an upcoming version I plan to make these field names customizables in the setup.

After you successfully configure the Movie Diary, it won't prompt you for that data again, if you eventually desire to change a configuration, like adding your MovieDB API key or turning a field on, the following script will display the configuration panel again with your current settings.

I like how the new Movie Diary is shaping up and your pitch is indispensable. Report every error, tweet your suggestions and reach out with your opinion. Besides making the editing feature built-in

, I would if you chime in with what would you like to see in the next version of the Movie Diary.
