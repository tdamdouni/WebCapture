# Networked RGB Wi-Fi Decorative Touch Lights

_Captured: 2017-12-08 at 09:48 from [www.hackster.io](https://www.hackster.io/team-filimin/networked-rgb-wi-fi-decorative-touch-lights-a6c9c8)_

![Networked RGB Wi-Fi Decorative Touch Lights](https://hackster.imgix.net/uploads/cover_image/file/45408/FCOB8U4I94196JE.MEDIUM.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

;

;

![](https://hackster.imgix.net/uploads/image/file/45369/FCOB8U4I94196JE.MEDIUM.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

I wanted to give my family a simple, meaningful, beautiful way to stay connected. We are spread out across two countries, and sometimes misunderstandings between us make communication even more difficult.

As holiday presents this last year I built 6 RGB Wi-FI enabled networked decorative touch lights. Each member of my family has one connected to their Wi-Fi. When one of us is thinking of the family, that person can touch their light. Everybody's light will light the same color simultaneously. All of us will know one of us is out there thinking of us. If the same person touches the light again, the color for all the lights will vary slightly. That person can find a color that speaks to them to share with all of us.

If another member of the family then touches their light, everybody's color will change more dramatically. All of us will know one of us has responded. All the lights fade to black within 2 hours of being touched.

There is no limitation to how many lights you can be synchronized; it's just a function of how many people are in your family and how many lights you want to make. You could make just a pair of lights or 500 of them all networked together if you wanted.

These lights have been received so positively that we have decided to manufacture and sell them. If you [pre-order some today](http://filimin.com/), you can have them at your home before the holiday season this year for less money than it costs to make them yourself. But for you DIYers out there, let's get started!

![](https://hackster.imgix.net/uploads/image/file/45373/FMYS5FVI94196K5.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

**Materials**

**Supplies**

  * Black spray paint 
  * Electrical tape 
  * Masking tape or painter's tape 
  * Solder 
  * Sand paper - 60 grit 
  * [Sticky glue](http://www.popularpatchwork.com/news/article/trimits-fabric-and-craft-glues/9805) (optional with bias tape)

**Electronics**

  * [Spark Core](https://store.spark.io/?product=spark-core) ($39 each. You need one for each light) 
  * One Raspberry Pi (any model) with SD card ethernet cable and power. (You can substitute any Linux server) 
  * [Conductive paint](http://www.bareconductive.com/shop/electric-paint-10ml/). (One light can use as much as 10ml of paint. I know it's expensive but I tried various DIY conductive paint recipes but could find nothing that works like the real thing.)
  * Wire. A 4-wire-strip ripped off ribbon cable from an old computer works great. 
  * 10 MOhm resistor.
  * High quality cell phone charger power supply. Cheaper off-brand power supplies do not work because the power is not clean enough for the touch sensing. Simple filtering with a capacitor does not fix this. You can buy name brand units (Samsung, Apple, LG, etc.) Alternatively, I picked up used brand-name chargers from the thrift store for $0.99 each and they work great.

**Tools**

  * Vibrating sander.
  * Table saw.
  * [Scraper](http://www.northerntool.com/images/product/2000x2000/909/9094236_2000x2000.jpg). A screwdriver would work. 
  * Soldering iron.
  * Drill press with router table, or drill press and router.
  * Multimeter.
![](https://hackster.imgix.net/uploads/image/file/45374/FEUDCMHI94190BG.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Frosted acrylic sheets are expensive and hard to find. As an alternative you can frost your own acrylic fairly easily:

  1. Fasten acrylic securely to a flat solid surface 
  2. Using a vibrating electric sander, sand acrylic with 60 grit sandpaper

Sand both sides of the acrylic so the acrylic diffuses the light fully. Many DIYers recommend finer grit sandpaper to frost acrylic, but rougher sandpapers such as 60 grit are better for diffusing.

(I loved this job because I got to use my dad's old vibrating sander. He was a great DIYer and he is no longer with us, so it's nice to have memories of him and his projects when I use his tools.)

![](https://hackster.imgix.net/uploads/image/file/45377/FF1J99XI9418YET.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Using a table saw, cut four 3.5"x7" sheets and one 3.5" square sheet of acrylic for each light. Set the saw blade at a 45 degree angle so you get a nice mitered corners. Acrylic is less forgiving than wood and hard to cut cleanly without cracking or melting. Here are some tips:

  * Use a sharp blade with very fine teeth designed for cutting acrylic.
  * Run the blade slowly.
  * Set the blade height to barely clear the acrylic.
  * Tape both sides of the acrylic with masking tape or painter's tape where you are going to cut it. This helps prevent cracking.
  * Push the acrylic through the blade with a sacrificial piece of wood on top so the acrylic will not kick up off the table.

( I used my dad's old table saw for the job. That was awesome. :-) )

![](https://hackster.imgix.net/uploads/image/file/45378/FZS6ZJXI9418YGH.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Using conductive paint, make a nice design on the inside of each side of each shade. This design serves as the touch sensor so make sure your design is nice and dense i.e. no huge gaping holes. Also, conductive paint is not **that** conductive so make your lines nice and thick. Be very generous with how much paint you use.

For each side of each shade, strip the end of a wire and sandwich it into the paint at the bottom of the side of the shade. If you need a weight to hold the wire, small change works well, as you can see in the picture. (No real elephants were harmed in the process of making these.)

Decorate the tops of the shades as well. Choose a place where the conductive paint of the top will meet the conductive paint of one of the sides so you can get conductivity to the top of your shade. You will connect the side to the top in a later step.

Allow the paint to dry overnight.

Using frosted paint, spray acrylic on both sides. This will help solidify the conductive paint, help the shades diffuse the light further, and give the shades a more polished look.

Apply multiple light coats so the spray doesn't run.

![](https://hackster.imgix.net/uploads/image/file/45390/FTBTPF3I9419W0P.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Prepare the acrylic by lightly sanding and cleaning the edges of the acrylic where you will be applying the cement.

Acrylic cement spreads easily and looks ugly when it runs. To help keep it from running, tape the edges of the acrylic. Run the cement as finely and evenly as you can. Use the top of the shade to square the shade and glue that at the same time. Tape the entire shade together and allow to dry overnight.

![](https://hackster.imgix.net/uploads/image/file/45391/FBIGGBVI94196TR.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

In an earlier step you chose a place where the conductive paint of the top would meet the conductive paint of one of the sides. Now that the shade is glued you can complete that connection electrically: Using an Exacto knife, gently scrape off the frosted paint at the two areas of contact. This will ensure a good electrical connection. Dab a bit of conductive paint to bridge across the two areas.

At this point you should have a complete shade with four wires coming out at the bottom, one for each. Solder these wires together.

If your cuts were not perfect (and mine were not), you might also want to add a black trim on the edges of your shade to cover up the irregularities. We used bias type and secured it with tacky glue.

![](https://hackster.imgix.net/uploads/image/file/45392/FPMCMHBI9418YN2.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

The base needs a channel for the power cord, a hole for the wiring to get from the bottom to the top of the base, and a recess for the Spark Core chip to live:

  1. Using a drill press and 1/8" drill bit, drill a slot for the power cord to go through. Smooth the slot with sandpaper. 
  2. Using a drill press and 1/2" drill bit, drill a hole through the base. The hole can be anywhere as long as it is on the inside part of the shade when the shade is glued to the base. 
  3. With a router and router bit, create a recess for the Spark Core. Clean the recess with a scraper and sandpaper. The last picture in this step shows how the Spark Core will sit in the recess of the base.
  4. Spray paint the base with several coat of black paint.
![](https://hackster.imgix.net/uploads/image/file/45399/FDA3JEPI95GTTC2.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

  1. If your Spark Core has header pins, snip them off with wire snips.
  2. Solder a 10MOhm resistor between pins D3 and D4 of the Spark Core.
  3. Cut the power cord to the cell phone charger. Confirm with a multimeter which wire is 5V and which is ground. Don't trust the color coding of the wires; I've found a few chargers were the colors were reversed from what I would have expected.
  4. Solder 5V and Gnd of the cell phone charger to the appropriate pins on the Spark Core
  5. Solder 4 wires to pins D2, D3, 5V and Gnd to feed through the base hole. I used part of an old floppy drive ribbon cable but any 4 wires will work.
  6. On the top side of the base, solder the wire connecting D3 to the 4 wires making up your touch sensor on your shade. Solder the 5V and Gnd wires to your Neopixel 5V and Gnd. Solder D2 to Neopixel Data in.

The picture shows the Spark Code glued into the recess of the base. Don't glue anything yet, though. Let's test and make sure everything is working first.

**Load the Code:**

  1. Set up your Spark Core as outlined on [the Spark website](http://www.spark.io/). It does not matter what you name your core but for convenience you might number it 1 through however many lights you are making. Besides recording the Spark UID you will want to make note of your access token for your Spark account. You will reference all three of these numbers later when networking them.
  2. Upload the Spark Core code (attached) to the Spark Core. The code is called FiliminPrototpe.ino. For your convenience I have included the two files which comprise the Neopixel library and which the code references. The Spark website offers several ways to upload code. I recommend using [the Spark CLI](http://docs.spark.io/cli/).
  3. At the top of the code that there are tweakable parameters and an array to put in SparkIDs. You do not need to worry about this for testing. The code works fine for testing with no changes.
  1. After visually checking your connections and confirming there are no shorts, plug in your cell phone power supply.
  2. If your connections to the Neopixel are secure, after the Spark connects to the Wi-Fi you will see the Neopixel cycle through a rainbow of colors then turn off.
  3. If your touch sensing is working, the Neopixel will light a random color when you touch the shade.

**Debug:**

  1. To help you with any problems, there are two booleans you can set at the beginning of the code: _#D_SERIAL true_ will output debugging values to the serial port._#D_WIFI true_ will output debugging values to the Spark Cloud.
  2. The two values you want to note when debugging touch sensing are tBaseline and tDelay. tBaseline is an averaged floating point value calculated as a timed rate of decay for the touch sensor when nobody is touching it. tDelay is a more current value which is compared to tBaseline to detect touch. tBaseline will typically hover between 100 and 250ish. If it is higher, you probably have a bad connection. If it is lower, that suggests a short or lower quality power supply.

**Reading Debugging Values from the Spark Cloud:**

When #D_WIFI is set to true you can see the values for tBaseline and tDelay in Linux using the Spark CLI:

  * watch -n 0.5 "curl -s -G [ https://api.spark.io/v1/devices/3/tBaseline ](https://api.spark.io/v1/devices/3/tBaseline) -d access_token={access token from Spark} | grep result"
  * watch -n 0.5 "curl -s -G [ https://api.spark.io/v1/devices/3/tDelay ](https://api.spark.io/v1/devices/3/tDelay) -d access_token={access token from Spark} | grep result"

To network the lights, you need to run a server connected to the Internet. Any server will work, including any Raspberry PI. I used a Raspberry PI Model A.

The server's job is to continually poll the lights to look for changes. If it sees any changes, it updates all of the lights to reflect the change. If you look at the Spark API you would guess that such a server would not be necessary as the lights could monitor each other through the cloud. I tried this first and under ideal conditions it works. However it is not a robust solution: flaky Internet connections and Spark's own throttling system can throw off the synchronization too easily. I have spoken with Spark about this and now expect later versions of Spark's hardware and cloud to address these problems fully in the very near future.

**Configure the server script:**

  1. The server is a simple Bash script. It keeps a log file called /var/log/lampServer. Make sure that the user running the server can write to this file.
  2. Edit the top of the server script putting in your token and the Spark IDs of all of the Spark Cores.
  3. Make the script executable: chmod 755 filiminPrototypeServer.sh

**Configure the Spark Core code:**

  1. Edit the Spark Core code from the previous step so that the Spark IDs of that code match completely with the Spark IDs listed in the server script. This includes the order in which the IDs are listed.
  2. Upload the edited Spark Core code to each of the Sparks in your lights.

Run the server. Plug in a couple of lights and touch one of them after they all find the Wi-Fi. Your lights should now be synchronized!

The server script will occasionally conk out with the message "Alarm Clock." To automatically restart it, use the attached watchdog script which runs the server script and detects if it freezes or stops. I have fully tested this solution over months now and have seen that the watchdog script successfully keeps the server script running continually without interruption.

To configure the watchdog script, edit the top lines to reflect correctly the path and filename of the server script.

Set the watchdog script to automatically run when when the server is booted. For a Raspberry Pi you can find a few techniques to do so [here](https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=7192).

![](https://hackster.imgix.net/uploads/image/file/45406/FCFXFOLI94196NK.LARGE.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

At this point, your lights are fully functional and you just need to complete assembly:

  * Glue Neopixel to the center of the base. Allow to dry 
  * Glue shade to base. I used tacky glue so it wouldn't hold too strongly. It dries clear and holds tight but not too tight so I can break the shade off the base for any maintenance. 
  * Glue or tape Spark Core to recess of the base. 
  * Staple cell phone power cord to the channel in the base.

**_Enjoy your networked RGB decorative touch lights!_**

**Acknowledgements: **

  * I was originally introduced to the Spark Core at [MakeICT](http://makeict.org). I also used MakeICT's facilities for some of the building of this project.
  * I got help building from my great friend Finn and my fiance Vanessa.
