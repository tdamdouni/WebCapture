# OpenCV and ESP32: Moving a Servo With My Face

_Captured: 2018-04-25 at 07:31 from [dzone.com](https://dzone.com/articles/opencv-and-esp32-moving-a-servo-with-my-face?edition=375219&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-04-24)_

One Saturday morning, I was having a breakfast when I discovered the [face_recognition](https://github.com/ageitgey/face_recognition) project. I started to play with the [OpenCV](https://opencv.org/) example -- I put my picture in, and wow, it works like a charm! It was pretty straightforward in detecting my face, and I can also obtain facial landmarks. One landmark that I can get, for example, is the nose tip. Playing with this script, I realized that with the nose tip, I can determine the position of the face. I can see if my face is aligned to the center or if it is moved to one side. Additionally, I have a new IoT device (one ESP32), and I wanted to do something with it. Let's say, for example, I wanted to control a servo (SG90) and move it from left to right depending on my face's position.

First, we have the main Python script. With this script, I detect my face, the nose tip, and the position of my face. With this position, I will emit an event to an MQTT broker (a [mosquitto](https://mosquitto.org/) server running on my laptop).
    
    
        small_frame = cv2.resize(frame, (0, 0), fx=0.25, fy=0.25)
    
    
        for face_encoding, face_landmarks in zip(face_encodings, face_landmarks_list):
    
    
    diff = math.fabs(maxLandmark[1] - minLandmark[1])
    
    
                    client.publish("/face/{}/center".format(name), "1")
    
    
                    client.publish("/face/{}/left".format(name), "1")
    
    
                    client.publish("/face/{}/right".format(name), "1")
    
    
    shape = np.array(face_landmarks['nose_bridge'], np.int32)
    
    
                cv2.polylines(frame, [shape.reshape((-1, 1, 2)) * 4], True, (0, 255, 255))
    
    
                cv2.fillPoly(frame, [shape.reshape((-1, 1, 2)) * 4], GREEN)
    
    
    face_names.append("{} {}".format(name, status))
    
    
    for (top, right, bottom, left), name in zip(face_locations, face_names):
    
    
    if 'Unknown' not in name.split(' '):
    
    
                cv2.rectangle(frame, (left, top), (right, bottom), labelColor, 2)
    
    
                cv2.rectangle(frame, (left, bottom - 35), (right, bottom), labelColor, cv2.FILLED)
    
    
                cv2.putText(frame, name, (left + 6, bottom - 6), cv2.FONT_HERSHEY_DUPLEX, 1.0, (255, 255, 255), 1)
    
    
                cv2.rectangle(frame, (left, top), (right, bottom), BLUE, 2)
    
    
    if cv2.waitKey(1) & 0xFF == ord('q'):

Now another Python script will be listening to MQTT events and will trigger one event with the position of the servo. I know that this second Python script may be unnecessary. We can move its logic to the ESP32 and main OpenCV script, but I was playing with MQTT and I wanted to decouple it a little bit.
    
    
            if event != self._state:
    
    
                self._client.publish("/servo", self._dict[event])
    
    
                print("emit /servo envent with value {} - {}".format(self._dict[event], name))
    
    
    client.on_connect = lambda self, mosq, obj, rc: self.subscribe("/face/#")
    
    
    client.on_message = lambda client, userdata, msg: on_message(msg.topic, iot)

And finally the ESP32. Here, we will connect to my Wi-Fi and my MQTT broker.

![](https://gonzalo123.files.wordpress.com/2018/02/20180224_195036_001_jpg.png?w=600&h=342)

Here is a video with the working prototype in action:

The source code is available in my [GitHub](https://github.com/gonzalo123/face.iot) account.
