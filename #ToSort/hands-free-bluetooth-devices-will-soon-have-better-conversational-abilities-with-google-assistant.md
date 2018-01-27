# Hands-Free Bluetooth Devices will soon have Better Conversational Abilities with Google Assistant

_Captured: 2017-11-14 at 19:57 from [www.xda-developers.com](https://www.xda-developers.com/hands-free-bluetooth-google-assistant-conversation/)_

Hands-Free Bluetooth Devices will soon have Better Conversational Abilities with Google Assistant

In order to use certain Bluetooth features on certain devices, the device must support certain Bluetooth profiles depending on what it wants to do. For hands-free devices, they must meet the Bluetooth Hands-Free Profile (HFP), which is updated on occasion to include additional features in the standard. For instance, Google recently added support in Android for [volume synchronization](https://www.xda-developers.com/hands-free-profile-volume-synchronization/) and [in-band ringtone support](https://www.xda-developers.com/bluetooth-in-band-ringtone-android-o/). Now it appears they are adding support for BVRA, a voice recognition command part of the Bluetooth Hands-Free Profile. This means that you will soon be able to initiate a conversation with the Google Assistant and end it entirely with your voice on devices with HFP.

With [these commits](https://android-review.googlesource.com/#/q/topic:%22BVRA+Client%22+\(status:open+OR+status:merged\)), the new methods that are added are called startVoiceRecognition and stopVoiceRecognition. The general flow as to how this will work can be summarized as follows:

  1. The Bluetooth accessory sends an AT+BVRA=1 command to the Android device.
  2. The Android device sends an OK response.
  3. The Android device launches a Google Assistant session and creates a Synchronous Connection (SCO) for the audio.
  4. If the Google Assistant session is not finished, the accessory must send AT+BVRA=1 to continue the conversation. This  

may need to happen multiple times.

  5. When the Google Assistant session is finished, the Android device sends a +BVRA:0 result code to the accessory.  

The Android device disconnects the SCO connection.

The steps above are pretty strict and are similar to what's outlined by Apple to use Bluetooth devices to converse with Siri. Google's implementation probably won't differ too much from Apple's. This may be relevant to older Bluetooth accessories that support only the Hands-Free Profile, allowing you to converse with the Google Assistant while driving such as when asking for directions.

This addition, by and large, is a safety feature, allowing users to benefit from the Google Assistant without stopping what they're doing. Sure it's also useful in other scenarios, but these kinds of additions will always benefit drivers the most, as they will need to keep their hands on the wheel and eyes on the road. Hopefully, we see more Hands-Free Bluetooth devices with support for Google Assistant soon!


