# Should you take your umbrella today?

_Captured: 2015-06-11 at 23:54 from [onetapless.com](https://onetapless.com/should-you-take-your-umbrella-today)_

I rise early from monday to friday for my day job and if there's one thing I don't like right after I wake up is to think. In the mornings, I run like a clock and any surprise disrupt my workflow. After grabbing my coffee and some breakfast, there's a brief moment in the day where I must consider the weather and the quintessential question is: _Should I take my umbrella?_.

Countless times I took my umbrella, sun shone all day long and it became a burden to carry, but now and then I ignore the weather predictions and leave it home, only to get back soaking wet. So I wrote a script to tell me the answer for this unavoidable problem in life. We'll use [Forecast's API](https://developer.forecast.io/) and the first step is to register an account so you can get your API token. Unless you decide to run this script more than 1000 times a day, you don't have to worry about payment details as the first thousand requests are free.

Got your token? Right, now let's get going on [Pythonista](https://itunes.apple.com/us/app/pythonista/id528579881?mt=8&uo=4&at=10l4KL). I'll try to build this script with you, step by step, so follow me. There must be a couple of editable variables, your API token is one of them, but I also decided to leave my arrival and departure times embed into the script, you can modify these later if you want:
    
    
    # Customization here
    APItoken = 'Insert your API token here'
    
    leave_home_hour = 8
    arrive_work_hour = 10
    leave_work_hour = 19
    arrive_home_hour = 21
    
    # End of customization

I hope the variable names are self-explanatory. The next step is fulfilling the demands for a data request from Forecast, we got the token set, but what about latitude and longitude? Luckily, Pythonista got the `location` module to handle this task:
    
    
    import location
    
    location.start_updates()
    place = location.get_location()
    location.stop_updates()
    
    latitude = str(place['latitude'])
    longitude = str(place['longitude'])

This is how it rolls: `start_updates()` activates the location services, now [Pythonista](https://itunes.apple.com/us/app/pythonista/id528579881?mt=8&uo=4&at=10l4KL) is tracking you, so we set our location with `get_location()`into a variable and stop the location services right there to save some battery life with `stop_updates()`. The `get_location()` returns a dictionary of information and since we're only interested in the latitude and longitude, we set a variable to each of them

. We have everything required to create a request, so shall we?
    
    
    from json import loads
    from requests import get
    
    request_url = 'https://api.forecast.io/forecast/' + APItoken + '/' + latitude + ',' + longitude
    
    r = get(request_url)
    data = loads(r.text)
    weather = data['hourly']['data']

First we import functions from the `json` and `requests` module. These are required to make a request and quickly interpret the outcome, but, as you may notice if you tried to print the `data` or the `weather` variables, there's way too much information. We want to limit it into the range of our previously stipulated times, however, Forecast returns each hour as UNIX time, which means it is counted as seconds since the epoch, January 1st, 1970. [You can read more about this on this Wikipedia page](http://en.wikipedia.org/wiki/Epoch_\(reference_date\\\)#Notable_epoch_dates_in_computing). So the problem is: we must convert our hours to UNIX time according to the current day.
    
    
    from datetime import date
    import time
    
    # Returns the current day as in midnight.
    today = time.mktime(date.today().timetuple())
    
    # 1 hour = 3600 seconds.
    leave_home = leave_home_hour * 3600 + today
    arrive_work = arrive_work_hour * 3600 + today
    leave_work = leave_work_hour * 3600 + today
    arrive_home = arrive_home_hour * 3600 + today

Let's dig into the `today` variable, `date.today()` will return the current day as `YYYY-MM-DD` and using `timetuple()` we convert it into a `struct_time` object and then we use `mktime()` to convert it into UNIX. Afterwards, just convert our hours into seconds and sum it with `today`. You may not want to memorize this date crazy thing, but I suggest you to save this as a snippet for later reference.

We got all the info we needed, so we'll pass that into 3 list comprehensions, one for the whole day, counting from the time you leave home until the time you get back. The other two will get the specific time spans when you're on your way between home and work. We also don't need all the info provided by Forecast, for this script we'll only use `precipProbability`, which returns the chance of rain in a number between 0 and 1, for example, 0.4 would represent 40% chance of rain in that given hour. You can get the whole list of [data point properties in the Forecast API docs](https://developer.forecast.io/docs/v2).
    
    
    day_precip = [hour['precipProbability'] for hour in weather if leave_home <= hour['time'] <= arrive_home]
    leave_precip = [errands['precipProbability'] for errands in weather if leave_home <= errands['time'] <= arrive_work]
    arrive_precip = [errands['precipProbability'] for errands in weather if leave_work <= errands['time'] <= arrive_home]

If you don't know list comprehensions, these three may teach you a lot. The logic behind the `arrive_precip` is that we call every element inside the `weather` dictionary as `errands`, you can name it as you like it, doesn't matter. Each `errands` is also a dictionary with several properties and all we want is the `precipProbability`, so we get only the `precipProbability` for each `errands` in the `weather` list. That results in a list with all raining odds in the requested data, but we also have to filter each one according to the hours we calculated earlier, so that's why we have that `if` clause afterwards, it says that the loop will only the the `precipProbability` from the `errands` if the conditions are met and another properties within the `errands` dictionary is `time`, which holds the hour in UNIX. Now we must make sure that `time` is between `leave_work` and `arrive_home` for the `arrive_precip` list and your first idea may be to do:
    
    
    if errands['time'] >= leave_work and errands['time'] <= arrive_home

However, Python has a shorthand to save you from that long clause:
    
    
    if leave_work <= errands['time'] <= arrive_home

It reads: if `leave_work` is less or equal than `errands['time']`, which is less or equal than `arrive_home`, set it as `True`. Simple, right? Now let's get these lists and turn them into averages. The first idea would be to sum all elements from the list and divide them for the length of the list:
    
    
    arrive_umbrella = sum(arrive_precip)/len(arrive_precip)

It will probably work now, however, if you request information for 8 to 9 AM from Forecast at 1 PM, that list will be empty, therefore, its length will be 0 and we can't divide a number by zero without a painful headache, so we'll write a function to set the value to 1 if the len() is 0. Our averages will look like this:
    
    
    def checkDivide(precip):
        if len(precip) == 0:
            return 1
        else:
            return len(precip)
    
    maybe_umbrella = sum(day_precip)/checkDivide(day_precip)
    leave_umbrella = sum(leave_precip)/checkDivide(leave_precip)
    arrive_umbrella = sum(arrive_precip)/checkDivide(arrive_precip)

After all this, we still don't know if we should take our damn umbrella or not. We'll check it now, if it has at least 40% chance to rain

while we're on our way to work or back home, if yes, we definitely should carry our umbrella, else if the day in general has at least 40% chance to rain, maybe we want to think twice and not risk getting wet. But if none of those are true, then your umbrella will be useless and you'll look like a weirdo on the subway. We also want to display the result is a fancy alert, so we appeal to the `console` module, it looks like this:
    
    
    from console import alert
    
    if leave_umbrella >= 0.4 or arrive_umbrella >= 0.4:
        alert('YES','It\'s rainings cats and dogs out there.')
    elif maybe_umbrella >= 0.4:
        alert('MAYBE', 'You just can\'t trust the weather.')
    else:
        alert('NO', 'You\'ll only forget it somewhere.')

Hell, after this adventure, you may want to get the whole script:
    
    
    # -*- coding: utf-8 -*-
    from json import loads
    from requests import get
    import location
    from datetime import date
    import time
    from console import alert
    
    # Customization here
    APItoken = 'Insert your API token here'
    
    leave_home_hour = 8
    arrive_work_hour = 10
    leave_work_hour = 19
    arrive_home_hour = 21
    # End of customization
    
    location.start_updates()
    place = location.get_location()
    location.stop_updates()
    
    latitude = str(place['latitude'])
    longitude = str(place['longitude'])
    
    request_url = 'https://api.forecast.io/forecast/' + APItoken + '/' + latitude + ',' + longitude
    
    r = get(request_url)
    data = loads(r.text)
    weather = data['hourly']['data']
    
    # Time math
    ## 1 hour = 3600
    today = time.mktime(date.today().timetuple())
    
    leave_home = leave_home_hour * 3600 + today
    arrive_work = arrive_work_hour * 3600 + today
    leave_work = leave_work_hour * 3600 + today
    arrive_home = arrive_home_hour * 3600 + today
    
    day_precip = [hour['precipProbability'] for hour in weather if leave_home <= hour['time'] <= arrive_home]
    leave_precip = [errands['precipProbability'] for errands in weather if leave_home <= errands['time'] <= arrive_work]
    arrive_precip = [errands['precipProbability'] for errands in weather if leave_work <= errands['time'] <= arrive_home]
    
    def checkDivide(precip):
        if len(precip) == 0:
            return 1
        else:
            return len(precip)
    
    maybe_umbrella = sum(day_precip)/checkDivide(day_precip)
    leave_umbrella = sum(leave_precip)/checkDivide(leave_precip)
    arrive_umbrella = sum(arrive_precip)/checkDivide(arrive_precip)
    
    if leave_umbrella >= 0.4 or arrive_umbrella >= 0.4:
        alert('YES','It\'s rainings cats and dogs out there.')
    elif maybe_umbrella >= 0.4:
        alert('MAYBE', 'You just can\'t trust the weather.')
    else:
        alert('NO', 'You\'ll only forget it somewhere.')

And all this just to be sure not to carry that damn umbrella in a sunny day. That's how much I hate umbrellas.
