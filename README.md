
# RapidPro Android Channel 
While it's great to have full integration with mobile operators at the SMSC level, that's not always practical (or in some cases even possible). As such, it's important to have an alternative method for enabling two-way SMS messaging.

The Android Channel for RapidPro does just that by using an inexpensive Android phone -- the purchase of which is becoming nearly ubiquitous around the world. Since Android phones are essentially little computers with redundant network and power, it makes it easy for us to leverage it's GSM modem for our needs. 

The RapidPro Android Channel is open source, licensed under [AGPL](http://www.gnu.org/licenses/agpl-3.0.html). Copyright 2014 Nyaruka, UNICEF.

## Using the Android Channel
Once you download the app from Google Play (or sideload it as necessary), opening for the first time will provide you with a claim code. It will look something like 'ABC 123 XYZ'. Once you've created your account on RapidPro, you can then enter this claim code on your account to register your Android device to your account. Once it is connected, every incoming SMS message received on the phone will be sent to your RapidPro account and every outbound message from your RapidPro account will use your Android phone to deliver the message.

## Why two projects?
The Android Channel project is split up into two projects, [client](https://github.com/rapidpro/android-channel/tree/master/client) and [packs](https://github.com/rapidpro/android-channel/tree/master/packs). The primary project is *client*. This is where you will find all the meat for the Android Channel relaying code. The companion project *packs* is used to create messaging packs to support the client. This is to allow the client to send more messages as the SMS usage on Android is rate-limited per project. Note that this project doesn't have any source code of its own. The one bit of code it needs for sending messages is linked from the client project. It doesn't even have a proper AndroidManifest.xml as this is generated by the build script for each pack it creates.

## Building
Before you build, you need to update your project properties so that ant can find your {sdk.dir}. -p requires path for your client root folder.
```
% android update project -p ./
```
Then it is easy peasy. We use ant.
```
% ant debug
```
To build the message packs, there's a shell script.
```
% ./buildpacks.sh
```
That's it!

## Developer Mode
You can put the client in developer mode by tapping on the logo 11 times. Once you've acheived this, you'll see a short toast at the bottom of the window. Once this is enabled you will see additional options in the settings menu -- chief among them is the ability to point your client to an IP Address which is useful if you are running RapidPro in your development environmnet.



