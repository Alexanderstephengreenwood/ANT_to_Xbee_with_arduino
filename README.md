# ANT_to_Xbee_with_arduino
Interfacing an ANT+ Garmin Tempe with an Xbee using an Arduino to pull temperature data

THIS IS A WORK IN PROGRESS PROJECT

For the little anecdote, I have a few Arduino boards lying around from a previous project picking up some dust and I was wondering what I could do with them and a specially with the two Digi Xbee series 1 including their Arduino shields. So ideas started working in the back of my head without anything clear.
We went trekking a few weeks ago and I found in the bottom of my backpack an old Garmin Tempe I used to pair with my Garmin Fenix 1 and Fenix 3. The idea popped;
why not use my Garmin Tempe as an extra temperature sensor for my Adruino homemade Weatherstation.

This Git repo, provides at this stage hints and information on how to interface these modules and devices together. Currently the streams investigated are;

-	ANT and ANT+ protocols
-	Digi XBee® series 1 (802.15.4)
-	Digi XBee® XCTU
-	Arduino

> ANT protocole notes

- Emission network format: 2.4 GHz ISM
- ANT easily handles peer-to-peer, star, connected star, tree and fixed mesh topologies
- 4-bit or 8-bit Microcontroller (MCU)
  The host MCU establishes and maintains a communication session to other remote ANT-enabled devices by means of a simple,
  bidirectional, serial message protocol. This document details the protocol and provides examples of how to use ANT
  for wireless networking.
  
  https://www.thisisant.com/developer/resources/downloads/

- CHANNEL IDs
  Only devices with matching channel IDs can communicate with each other. The channel ID represents the device
  type/number and transmission type of the master device and must be specified on the master device. On a slave device,
  these fields are set to determine which master device to communicate with. They can be set to match a specific master, or
  any/all of these fields can be set to zero, representing a wildcard value, such that the slave will find the first master
  matching other channel parameters (network key, frequency).
  
- device number
  The device number should not be set to 0x0000 or 0xFFFF as these are reserved values

https://www.thisisant.com/developer/ant/ant-basics/
https://www.thisisant.com/developer/ant-plus/device-profiles#524_tab --> ANT Tempe profil

> Digi specifics
- 
https://www.digi.com/resources/documentation/digidocs/PDFs/90001458-13.pdf --> XCTU guide
