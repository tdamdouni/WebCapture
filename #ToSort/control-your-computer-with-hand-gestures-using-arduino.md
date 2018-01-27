# Control your Computer with Hand Gestures using Arduino

_Captured: 2017-11-06 at 23:33 from [circuitdigest.com](https://circuitdigest.com/microcontroller-projects/control-your-computer-with-hand-gestures)_

Recently **Gesture controlled Laptops or computers** are getting very famous. This technique is called [Leap motion](https://www.theverge.com/2013/9/19/4745964/hp-envy-17-leap-motion-se-notebook) which enables us to control certain functions on our computer/Laptop by simply waving our hand in front of it. It is very cool and fun to do it, but these laptops are really priced very high. So in this project let us try building our own **Gesture control Laptop/Computer by combining the Power of Arduino and Python**.

We will use two **Ultrasonic sensors** to determine the position of our hand and **control a media player (VLC) based on the position**. I have used this for demonstration, but once you have understood the project, you can do anything by just changing few lines of code and control your favorite application in your favorite way.

We have already covered few projects which combines Arduino with Python. So I assume that you have already installed Python and its serial library and have successfully tried out few basic projects like blinking LED. If not, don't worry you can fall back to this [Arduino-Python Led Controlling](https://circuitdigest.com/microcontroller-projects/arduino-python-tutorial) tutorial and get along with it. So make sure you have installed Python and pyserial library before proceeding.

The concept behind the project is very simple. We will place two Ultrasonic (US) sensors on top of our monitor and will read the distance between the monitor and our hand using Arduino, based on this value of distance we will perform certain actions. To perform actions on our computer we use Python **pyautogui** library. The commands from Arduino are sent to the computer through serial port (USB). This data will be then read by python which is running on the computer and based on the read data an action will be performed.

![Control your Computer with Hand Gestures using Arduino Circuit](https://circuitdigest.com/sites/default/files/circuitdiagram_mic/Control-your-Computer-with-Hand-Gestures-using-Arduino-circuit.png)

> _Control your Computer with Hand Gestures using Arduino Circuit_

To **control the PC with Hand Gestures**, just connect the two Ultrasonic sensors with Arduino. We know US sensor work with 5V and hence they are powered by the on board Voltage regulator of Arduino. The Arduino can be connected to the PC/Laptop for powering the module and also for Serial communication. Once the connections are done place them on your monitor as shown below. I have used a double side tape to stick it on my monitor but you can use your own creativity. After securing it in a place we can proceed with the Programming.

![gestures Controlled Computer using Arduino and ultrasonic](https://circuitdigest.com/sites/default/files/inlineimages/gestures-Controlled-Computer-using-Arduino-and-ultrasonic.jpg)

![Controlling computer with Hand Gestures using Arduino and ultrasonic](https://circuitdigest.com/sites/default/files/inlineimages/Controlling-computer-with-Hand-Gestures-using-Arduino-and-ultrasonic.jpg)

The Arduino should be programmed to read the distance of hand from the US sensor. The **complete program** is given at the end of this page; just below I have given the explanation for the program. If you are new to Ultrasonic sensor, just go through [Arduino & Ultrasonic Sensor Based Distance Measurement](https://circuitdigest.com/microcontroller-projects/arduino-ultrasonic-sensor-based-distance-measurement).

By reading the value of distance we can arrive at certain actions to be controlled with gestures, for example in this program I have programmed **5 actions** as a demo.

**Action 1: **When both the hands are placed up before the sensor at a particular far distance then the video in VLC player should Play/Pause.

**Action 2: **When right hand is placed up before the sensor at a particular far distance then the video should Fast Forward one step.

**Action 3: **When left hand is placed up before the sensor at a particular far distance then the video should Rewind one step.

**Action 4: **When right hand is placed up before the sensor at a particular near distance and then if moved towards the sensor the video should fast forward and if moved away the video should Rewind.

**Action 5: **When left hand is placed up before the sensor at a particular near distance and then if moved towards the sensor the volume of video should increase and if moved away the volume should Decrease.

Let us see how the program is written to perform the above actions. So, like all programs we **start with defining the I/O pins** as shown below. The two US sensors are connected to Digital pins 2,3,4 and 5 and are powered by +5V pin. The trigger pins are output pin and Echo pins are input pins.

The Serial communication between Arduino and python takes places at a baud rate of 9600.
    
    
    const int trigger1 = 2; //Trigger pin of 1st Sesnor
    const int echo1 = 3; //Echo pin of 1st Sesnor
    const int trigger2 = 4; //Trigger pin of 2nd Sesnor
    const int echo2 = 5;//Echo pin of 2nd Sesnor
    void setup() {
    Serial.begin(9600);
    
    pinMode(trigger1, OUTPUT);
    pinMode(echo1, INPUT);
    pinMode(trigger2, OUTPUT);
    pinMode(echo2, INPUT);
    }

We need to **calculate the distance between the Sensor and the hand** each time before concluding on any action. So we have to do it many times, which means this code should be used as a function. We have written a function named _calculate_distance()_ which will return us the distance between the sensor and the hand.
    
    
    /*###Function to calculate distance###*/
    void calculate_distance(int trigger, int echo)
    {
    digitalWrite(trigger, LOW);
    delayMicroseconds(2);
    digitalWrite(trigger, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigger, LOW);
    
    time_taken = pulseIn(echo, HIGH);
    dist= time_taken*0.034/2;
    if (dist>50)
    dist = 50;
    }
    
    

Inside our main _loop _we **check for the value of distance and perform the actions** mentioned above. Before that we use two variables _distL_ and _distR_ which gets updated with current distance value.
    
    
    calculate_distance(trigger1,echo1);
    distL =dist; //get distance of left sensor
    
    calculate_distance(trigger2,echo2);
    distR =dist; //get distance of right sensor

Since we know the distance between both the sensors, we can now compare it with predefined values and arrive at certain actions. For example if both the hands are placed at a distance of 40 mc then we play/pause the video. Here the word **"Play/Pause"** will be sent out through serial port
    
    
    if ((distL >40 && distR>40) && (distL <50 && distR<50)) //Detect both hands
    {Serial.println("Play/Pause"); delay (500);}

If the Right hand alone is placed before the module then we fast forward the video by one step and if it is left hand we rewind by one step. Based on the action, here the word **"Rewind" or "Forward"** will be sent out through serial port
    
    
    if ((distL >40 && distL<50) && (distR ==50)) //Detect Left Hand
    {Serial.println("Rewind"); delay (500);}
    
    if ((distR >40 && distR<50) && (distL ==50)) //Detect Right Hand
    {Serial.println("Forward"); delay (500);}

Foe detailed control of volume and track we use a different methodology so as to prevent false triggers. To **control the volume** we have to place the left hand approx. At a distance of 15 cm , then you can either move it towards the sensor to decrease the volume of move it away from the sensor to increase the volume. The code for the same is shown below. Based on the action, here the word "Vup" or "Vdown" will be sent out through serial port
    
    
    //Lock Left - Control Mode
    if (distL>=13 && distL<=17)
    {
      delay(100); //Hand Hold Time
      calculate_distance(trigger1,echo1);
      distL =dist;
      if (distL>=13 && distL<=17)
      {
        Serial.println("Left Locked");
        while(distL<=40)
        {
          calculate_distance(trigger1,echo1);
          distL =dist;
          if (distL<10) //Hand pushed in 
          {Serial.println ("Vup"); delay (300);}
          if (distL>20) //Hand pulled out
          {Serial.println ("Vdown"); delay (300);}
        }
      }
    }

We can use the same method for the right side sensor also, to **control the track of the video**. That is if we move the right hand towards the sensor it will fast forward the movie and if you move it away from the sensor it will rewind the movie. Based on the action, here the word "Rewind" or "Forward" will be sent out through serial port

You can now read over the **complete code for this gesture controlled PC given at the end of the page** and try understating it as an whole and then copy it to your Arduino IDE.

### **Programming your Python:**

The python program for this project is very simple. We just have to establish a serial communication with Arduino through the correct baud rate and then perform some basic keyboard actions. The first step with python would be to install the **p_yautogui_ **module. Make sure you follow this step because the **program will not work without pyautogui module**.

**Installing pyautogui module for windows:**

Follow the below steps to install_ pyautogui_ for windows. If you are using other platforms the steps will also be more or less similar. Make sure your computer/Laptop is connected to internet and proceed with steps below

**Step 1:** Open Windows Command prompt and change the directory to the folder where you have installed python. By default the command should be

**Step 2: **Inside your python directory use the command _python -m pip install -upgrade pip_ to upgrade your pip. Pip is a tool in python which helps us to install python modules easily. Once this module is upgraded (as shown in picture below) proceed to next step.

**Step 3:** Use the command "_python -m pip install pyautogui_" to install the pyautogui module. Once the process is successful you should see a screen something similar to this below.

![Python auto gui installation using command prompt](https://circuitdigest.com/sites/default/files/inlineimages/Python-auto-gui-installation-using-command-prompt.png)

Now that the _pyautogui_ module and _pyserial_ module (installed in [previous tutorial](https://circuitdigest.com/microcontroller-projects/arduino-python-tutorial)) is successful installed with the python, we can proceed with the python program. The **complete python code is given at the end of the tutorial** but the explanation for the same is as follows.

Let us import all the three required modules for this project. They are pyautogui, serial python and time.
    
    
    import serial #Serial imported for Serial communication
    import time #Required to use delay functions
    import pyautogui

Next we **establish connection with the Arduino through COM port.** In my computer the Arduino is connected to COM 18. Use device manager to find to which COM port your Arduino is connected to and correct the following line accordingly.
    
    
    ArduinoSerial = serial.Serial('com18',9600) #Create Serial port object called arduinoSerialData
    time.sleep(2) #wait for 2 seconds for the communication to get established

Inside the infinite _while_ loop, we repeatedly listen to the COM port and **compare the key words with any pre-defied works** and make key board presses accordingly.
    
    
    while 1:
        incoming = str (ArduinoSerial.readline()) #read the serial data and print it as line
        print incoming
        
        if 'Play/Pause' in incoming:
            pyautogui.typewrite(['space'], 0.2)
    
        if 'Rewind' in incoming:
            pyautogui.hotkey('ctrl', 'left')  
    
        if 'Forward' in incoming:
            pyautogui.hotkey('ctrl', 'right') 
    
        if 'Vup' in incoming:
            pyautogui.hotkey('ctrl', 'down')
            
        if 'Vdown' in incoming:
            pyautogui.hotkey('ctrl', 'up')

As you can see, to press a key we simply have to use the command _"pyautogui.typewrite(['space'], 0.2)"_ which will press the key space for 0.2sec. If you need hot keys like ctrl+S then you can use the hot key command _"pyautogui.hotkey('ctrl', 's')"._

I have used these combinations because they work on VLC media player you can tweak them in any way you like to create your own applications to **control anything in computer with gestures**.

### **Gesture Controlled Computer in Action:**

Make the connections as defined above and upload the Arduino code on your Arduino board. Then use the python script below and launch the program on your laptop/computer.

Now you can play any movie on your computer using the VLC media player and **use your hand to control the movie** as shown in the **video given** below.

![Control your Computer with Hand Gestures using Arduino](https://circuitdigest.com/sites/default/files/projectimage_mic/Control-your-Computer-with-Hand-Gestures-using-Arduino.jpg)

Hope you understood the project and enjoyed playing with it. This is just a demo and you can use your creativity to build a lot more cool gesture controlled stuff around this. Let me know if this was useful and what you will create using this in the comment section and I will be happy to know it.
