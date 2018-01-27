# Rickroll Box © GPL3+

_Captured: 2017-12-15 at 19:34 from [create.arduino.cc](https://create.arduino.cc/projecthub/slagestee/rickroll-box-3c2245?ref=platform&ref_id=424_recent___&offset=2)_

This Arduino project "rickrolls" people when they open a box (see <https://en.wikipedia.org/wiki/Rickrolling>). Basically, this involves a surprise piezo rendition of the song "Never Gonna Give You Up" by Rick Astley that plays when the box is opened and pauses when the box is closed. When the box is reopened, the song picks up where it left off. While the song is playing, an LED blinks to the notes of the music, and the Serial monitor outputs the lyrics in time with the actual song. A potentiometer can be turned to adjust the volume of the music. A fun button also exists that, when pressed, makes the song get faster. It can be pressed a few more times to make the tempo get progressively faster until it loops back around to the original tempo.

Get rickrolled when you open the box!

![Note that piezo is connected in series with potentiometer in order to control sound volume.](https://hackster.imgix.net/uploads/attachments/393832/final_arduino_project_bb_ZtfDGrKozs.png?auto=compress%2Cformat&w=680&h=510&fit=max)

> _Note that piezo is connected in series with potentiometer in order to control sound volume._

Inputs:

  * Potentiometer -used as a dial to adjust volume of piezo output 
  * Photoresistor--determines whether box is open or closed (light or dark) 
  * Button - can be pressed to make song get progressively faster 

Outputs:

  * Piezo - used to create sound for song 
  * LED - blinks to notes of song 
  * Serial Output - prints out words of song 
![Circuit connections shown outside of box for clarity.](https://hackster.imgix.net/uploads/attachments/393838/img_2232_2mBokj6O90.JPG?auto=compress%2Cformat&w=680&h=510&fit=max)

> _Circuit connections shown outside of box for clarity._

In order to play music, the song first had to be transcribed into a form that could be interpreted in code. The notes were determined by listening to the song and matching them on the piano. The rhythms were determined by counting and clapping out the song to a consistent set of beats. In the code, these notes were stored in arrays as their respective frequencies, i.e. A4=440 Hz. This is how the Piezo outputs noise; it generates sound at specified frequencies to create a pitch. All frequencies required for the song were defined at the beginning of the code.

For the rhythm of the song, relative durations of notes were stored in arrays, and these durations were later multiplied by a constant beat length in order to determine the full duration of the note. A gap 30% of the length of the previous note was introduced to create space between notes. The full song was divided into the intro, first verse, and chorus, which were set to play in the following order indefinitely: chorus, first verse, chorus, intro, intro, first verse etc. Finally, these arrays of notes and rhythms could be iterated through on a step-by-step basis, which allowed for the integration of visual outputs, such as light and lyrics. To actually output the sound from the piezo, the tone function was used, which handles the tone duration with its own independent timer. This necessitated additional delay calls in order to keep the notes on time with other parts of the code.

A light threshold was generated during setup in order to determine when the box would be open (bright) and closed (dark) in order to play and pause the song. In order to take input from the button at any time, since the state change is instantaneous (as opposed to the photoresistor, which produces continuous digital input), an interrupt was attached to the button pin in order to detect when it was pressed. Interrupts, initialized in the setup, are always listening for state changes; when the specified change is detected, the program immediately switches to handling the interrupt with a specified method and then picks up where it left off. This is a good way to handle inputs because it allows them to be read at any time, even if another portion of code is executing. Interrupts just have to be handled carefully, and any variable that is changed by them should be declared as volatile.

  * Add a servo, and take a mini Rick Astley to its arm to dance to the music.
  * Replace standard LED with RGB LED, and cycle through colors during the song.
  * Add more standard LEDs to blink to the beat of the music.
  * Whenever Rick Astley sings "Never gonna give you up," play Darude "Sandstorm," and start flashing LEDs at random.
![Final arduino project bb yln5f76hta](https://halckemy.s3.amazonaws.com/uploads/attachments/393844/final_arduino_project_bb_YlN5F76hta.png)
