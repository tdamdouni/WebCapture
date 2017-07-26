# RescueTime for Statusboard

_Captured: 2015-10-18 at 20:57 from [onetapless.com](https://onetapless.com/rescuetime-for-statusboard)_

[RescueTime](https://www.rescuetime.com/ref/503190) is a web service that tracks what you do and calculates your productivity according to the sites you visit and applications you use. It's my own private spy that pats on my back on a good day and points out the time sinkers in my day otherwise.

Yes, it sounds risky to let any application track that kind of data from you, specially one that works on a web layer. If you prefer a local alternative on the Mac you may like [Timing](https://itunes.apple.com/app/id431511738?mt=12&ign-mpt=uo%253D4&at=10l4KL) or [TimeSink](https://itunes.apple.com/us/app/time-sink/id404363161?mt=12&at=10l4KL), but then you'd miss the Windows support

, the API we're going to use today and the price tag: RescueTime is free.

Guides you in the building of the RescueTime panel. Just follow the steps in the first action and you'll be fine.

The receiving end of our application is [Statusboard](https://geo.itunes.apple.com/us/app/status-board/id449955536?mt=8&at=10l4KL), the dashboard app for iPad from [Panic](https://panic.com/statusboard/). The app has 6 panels for free, but our workflow requires you to purchase the IAP (currently $9.99).

I built a workflow to help you set up the panel, it will [open the page](https://www.rescuetime.com/anapi/manage) to create a new API key in Safari. Look for the following form and fill the reference label (leave the _Allow queries from_ empty).

![Fill the form to create an API key.](http://img-1775.kxcdn.com/rescuetime-for-statusboard/create-api-form.png)

> _Create an API key, copy it and return to Workflow._

Tap the _Activate this key_ button and you'll go to a page stating that your key is active. Copy the key and tap the _Back to Workflow_ button that is supposed to be in your top-left corner if you're on iOS 9. You'll go to Statusboard and be asked to position the panel.

![If you see this popup in Statusboard, the action worked.](http://img-1775.kxcdn.com/rescuetime-for-statusboard/accept-panel.png)

> _Position your panel and you're done._

Place the panel wherever you like it and enjoy! The app was built on [Heroku](https://www.heroku.com) and the graph is made with [Chart.js](http://www.chartjs.org). I'm very interested in building more of these, so if you have any panel you want to implement in [Statusboard](https://geo.itunes.apple.com/us/app/status-board/id449955536?mt=8&at=10l4KL), like this one with [RescueTime](https://www.rescuetime.com/ref/503190), reach me out on [Twitter](https://twitter.com/onetapless).
