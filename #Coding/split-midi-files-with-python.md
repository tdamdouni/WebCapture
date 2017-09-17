# Split MIDI Files with Python

_Captured: 2017-09-15 at 15:53 from [codeandlife.com](http://codeandlife.com/2017/08/13/split-midi-files-with-python/)_

In my previous post I showed how to use [Raspberry Pi to automatically record MIDI](http://codeandlife.com/2017/08/04/using-raspberry-pi-as-an-automatic-midi-logger/) files from digital piano whenever you turn it on. However, if you sit down and play for an hour, and get one big MIDI file, it is not very useful. So what to do?

Pianoteq has a feature that splits your playing session based on breaks you take between playing notes. So I decided to mimick this feature with a simple Python script that:

  1. Keeps tab on keys and pedals pressed
  2. Whenever X seconds elapse without any keys or pedals down, a new MIDI file is started
  3. Additionally, if user presses and releases sustain pedal several times in the end, filename for that MIDI is altered to "highlight" that file

I first thought to learn enough of MIDI file format to do everything from scratch, but there's quite a bit of small details to handle, so in the end I decided to use an external toolkit from Craig Stuart Sapp called [midifile](https://github.com/craigsapp/midifile) to do the heavy lifting. You should be able to just clone the Git repo and make it with Raspberry Pi:
    
    
    pi@raspberrypi:~ $ git clone https://github.com/craigsapp/midifile
    pi@raspberrypi:~ $ cd midifile
    pi@raspberrypi:~/midifile $ make
    

You should now have two useful commands in `~/midifile/bin`: `toascii` to read a MIDI file and dump an ASCII (text) version of it, and `tobinary` to do the reverse. With Python's `Popen` and smart piping, we can read and write the binary MIDI files as they were in this text format. You can check out how the format looks like with some MIDI file you have:
    
    
    ~/midifile/bin/toascii somemidi.mid | less
    

Here's a sample of a MIDI file recorded by `arecordmidi` (I added the note in square brackets):
    
    
    "MThd"
    4'6
    2'0
    2'1
    2'384
    
    ;;; TRACK 0 ----------------------------------
    "MTrk"
    4'50044
    v0      ff 51 v3 t120
    v0      ff 58 v4 '4 '2 '24 '8
    v7147   90 '58 '29
    v88     b0 '64 '5
    v1      b0 '64 '7
    
    [LOTS OF MIDI EVENTS]
    
    v0      ff 2f v0
    

There's some header data in the beginning, and each MIDI event is comprised of a deltatime field starting with 'v', and then fairly standard MIDI events in straightforward syntax. I hardcoded my program to expect single track which starts with tempo and speed data (ff 51 and ff 58 lines) which I use to calculate how many deltatime units is one second. I copy this header part to start of every MIDI file, and append the final "ff 2f v0" (END TRACK) event to the end. Here's the full code:
    
    
    #!/usr/bin/python3import sys  
    from subprocess import Popen, PIPE  
      
    toascii = '/home/pi/midifile/bin/toascii'  
    tobinary = '/home/pi/midifile/bin/tobinary'def writeAsc(segNum, common, seg, highlight=False):  
        filename = '%s_%d.mid' % (sys.argv[1].rsplit('.', 1)[0], segNum)  
        if highlight: filename = filename.replace('.mid', '_HIGH.mid')  
        with Popen([tobinary, filename], stdin=PIPE) as proc:  
            f = proc.stdin  
            for line in common+seg: f.write(bytes(line, 'ASCII'))  
            f.write(b'v0\tff 2f v0\n') # End of track  
        print('Wrote', len(seg), 'items to', filename)if len(sys.argv) < 2:  
        print('Usage: splitasc.py <midifile.mid> [splitlimit]')  
        print('\nSplit limit is in seconds, default is 5')  
        exit(1)if len(sys.argv) > 2:  
        limit = int(sys.argv[2])else:  
        limit = 5with Popen([toascii, sys.argv[1]], stdout=PIPE) as proc:  
        fin = proc.stdout  
        T = 0 # current time base  
        pedals = set() # active pedals  
        keys = set() # active keys  
        silent = True # Is all silent?  
        silentT = 0 # Start of silent  
      
        common = [] # Common lines in beginning  
        seg = [] # Current segment  
        segNum = 1 # Running number  
      
        pedCount = 0 # End with double press of pedal to highlight  
      
        for line in fin:  
            line = line.decode('ASCII')  
            if len(line) == 0 or line[0] != 'v':  
                common.append(line)  
                if len(common) == 5: # Try to extract PPQ  
                    try: PPQ = int(line[2:])  
                    except: pass  
                continue  
      
            it = line.split()  
            T += int(it[0][1:])  
      
            if it[1] == 'ff':  
                if it[2] != '2f': # Skip EOF  
                    common.append(line) # Tempo and time etc. into common  
                    if it[2] == '51': # Try to extract BPM  
                        try: BPM = int(it[-1][1:])  
                        except: pass  
                continue  
      
            if it[1] == 'b0': # Controller info  
                if it[3] == "'0":  
                    pedals.discard(it[2])  
                else:  
                    if not pedals: pedCount += 1 # Increase pedal count  
                    pedals.add(it[2])  
            elif it[1] == '90': # Note on  
                keys.add(it[2])  
            elif it[1] == '80': # Note off  
                keys.discard(it[2])  
      
            if (pedals or keys) and silent: # End of silence  
                silent = False  
                if T-silentT > limit*PPQ*BPM/60: # Over specified limit  
                    line = 'v0\t%s\n' % (' '.join(it[1:])) # hack zero timedelta  
                    if seg: # Data to write  
                        writeAsc(segNum, common, seg, pedCount > 1)  
                        segNum += 1  
                    seg = [] # Clear segment  
            else: silent, silentT = True, T  
      
            seg.append(line)  
            if it[1] == '90': pedCount = 0 # Delayed reset of pedCount on notes  
      
        if seg: # Data to write  
            writeAsc(segNum, common, seg, pedCount > 1)  
            segNum += 1

The code should be possible to understand, but you don't have to if you don't want to, just save as `splitmidi.py` in your home directory, `chmod a+x splitmidi.py` and you are ready to rock:
    
    
    ./splitmidi.py somemidi.mid

You can add a number as a second command line argument and the script will use that number of seconds of silence to mark a splitting point. MIDI part files will be named `somemidi_N.mid` where N is a running number. If you double-press pedal in the end of a playing segment (without any keys down), there will be additional `somemidi_X_high.mid` postfix to "highlight" that one. Nice!

If you want, you could even modify the script in my [previous post](http://codeandlife.com/2017/08/04/using-raspberry-pi-as-an-automatic-midi-logger/) to do this splitting after the `arecordmidi` command is terminated. I'm not revisiting my recordings that often, so I've so far decided to use this tool on "need to do it basis". :)
