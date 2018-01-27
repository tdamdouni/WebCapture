# Start/Stop Chronometer

_Captured: 2017-11-10 at 00:49 from [www.hackster.io](https://www.hackster.io/Noshirt/start-stop-chronometer-cbf206)_

![Start/Stop Chronometer ](https://hackster.imgix.net/uploads/attachments/373114/img_9439_vzbgccG9UF.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

;

;

![](https://hackster.imgix.net/uploads/attachments/374286/img_9440_s5yF7wnbw5.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

;

;

![](https://hackster.imgix.net/uploads/attachments/374294/img_9442_cIgnZXnT7O.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/374297/label_A14E3OgI0K.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

> _FOLLOW THIS TO AVOID ERRORS_

Me and my friend are always in competition for something, in every sports, from ski to run, to MTB. I decided to build this Chronometer to have a precise measurement of the time spent to complete a pre-made circuit. You just have to choose a start and an end point, and place the two module (we 3D-printed a case for it because we soldered everything on a circuit board, you can also do this if you want something definitve) to start the competition.

Hope you have fun!

Credits for the wiring label to: <https://arduino-info.wikispaces.com/Nrf24L01-2.4GHz-HowTo>

![Cattura ue7bhngton](https://halckemy.s3.amazonaws.com/uploads/attachments/374289/cattura_UE7bhNgToN.PNG)

![Cattura1 epyyo0s3x0](https://halckemy.s3.amazonaws.com/uploads/attachments/374291/cattura1_epYYO0s3x0.PNG)
    
    
    LiquidCrystal lcd(12, 11, 5, 4, 3, 10);
    
    const byte thisSlaveAddress[5] = {'R','x','A','A','A'};
    
    
    
      lcd.begin(16, 2);
    
      distance = (duration/2) / 29.1;
      if (distance <= 100 && distance >= 0) {
        while (digitalRead(greenLed) == HIGH) {
    
    
      
      lcd.setCursor(0,1);
      lcd.print(m);
      lcd.print(":");
      lcd.print(s);
      lcd.print(dc);
      
    
      if (dc == 9) {
      
      if (s == 60) {
    
        if ( radio.available() ) {
            radio.read( &dataReceived, sizeof(dataReceived) );
    
