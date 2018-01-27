# [Unicorn Python] Keep led on without While True?

_Captured: 2017-11-22 at 21:03 from [forums.pimoroni.com](https://forums.pimoroni.com/t/unicorn-python-keep-led-on-without-while-true/6420/2)_

This is actually a more complex problem than it outwardly appears. This is because, while the WS2812 LEDs on Unicorn HAT and Unicorn pHAT are "smart" and will remember the last data you sent to them, they're also fairly forgiving about what they interpret as data.

Basically- if you're not actively sending them a signal telling them to "show X" they might suddenly decide to interpret some random environmental noise as "show Y", which isn't fun!

Anyway, if you're willing to overlook this detail you can fudge it by using adding:
    
    
    unicorn.atexit._exithandlers = []
    

Right after `unicorn.show()`

It looks like I need to add this as a feature into Unicorn HAT, although because it has no onboard driver chip to maintain the last state you sent (causing the problem documented above) I've so far avoided doing so.

The _correct_ way to accomplish this, would be to have the Python script running continuously, and then use some sort of interface (a fifo, pipe or otherwise) to communicate with that script and tell it to turn the lights on/off.

You could use `SIGUSR1` and `SIGUSR2` to do this, or perhaps `SIGSTOP` and `SIGCONT`. Off the top of my head:
    
    
    #!/usr/bin/env python
    
    import signal
    import unicornhat as unicorn
    
    unicorn.set_layout(unicorn.PHAT)
    unicorn.brightness(0.2)
    
    def turn_on(signum, stack):
        for x in range(8):
            unicorn.set_pixel(x, 1, 255, 0, 255)
        unicorn.show()
        signal.pause()
    
    def turn_off(signum, stack):
        unicorn.off()
        signal.pause()
    
    signal.signal(signal.SIGUSR1, turn_on)
    signal.signal(signal.SIGUSR2, turn_off)
    
    signal.pause()
    

Save this as `unincornsignal.py` and run with: `sudo unicornsignal.py &` to send it to the background.

You should see a line appear after this that says something like:
    
    
    [2] 431
    

The latter number is the script's PID, substitute this in the below commands.

Now try: `sudo kill -12 PID` to turn Unicorn HAT off  
and `sudo kill -10 PID` to turn it on.

You could make a Python script to run these commands for you:
    
    
    #!/usr/bin/env python
    
    import os
    import signal
    import argparse
    
    parser = argparse.ArgumentParser()
    
    parser.add_argument("-pid", "--pid", type=int, help="pid of Unicorn Server")
    parser.add_argument("-sw", "--show", action="store_true", help="turn on the led")
    parser.add_argument("-st", "--stop", action="store_true", help="stop the led")
    
    args = parser.parse_args()
    
    if args.show:
        os.kill(args.pid, signal.SIGUSR1)
    elif args.stop:
        os.kill(args.pid, signal.SIGUSR2)
    

And call with:
    
    
    pi@raspberrypi:~ $ sudo python unicornremote.py --pid 464 --stop
    pi@raspberrypi:~ $ sudo python unicornremote.py --pid 464 --show
    

And you could even go so far as to have `unicornsignal.py` save its pid to an external file, and have `unicornremote.py` read that in automatically.

Then set up a systemd unit to run your `unicornsignal.py` in the background:
    
    
    [Unit]
    Description=My UnicornHAT Server
    After=multiuser.target
    Requires=local-fs.target
    
    [Service]
    Restart=always
    Type=simple
    ExecStart=/usr/bin/python /home/pi/unicornsignal.py
    
    [Install]
    WantedBy=default.target
    

Which you would save as `/etc/systemd/system/unicornserver.service`

Then reload systemd:
    
    
    sudo systemctl daemon-reload
    

And start your new service:
    
    
    sudo systemctl start unicornserver
    

You can also get its status:
    
    
    sudo systemctl status unicornserver
    

And stop it:
    
    
    sudo systemctl stop unicornserver
    
