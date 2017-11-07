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
  for wireless networking. https://www.thisisant.com/developer/resources/downloads/
- Network Number
  A network number is an 8-bit field that identifies the available networks on an ANT device, with acceptable values ranging
  from 0 to the maximum number defined by the ANT implementation. The host can obtain this maximum number by
  querying the ANT system using the appropriate request message (refer to section 9 for more details). The default network
  number is 0. Network number 0 is assigned to the “Public Network” by default. For AP1 devices, the remaining network
  numbers are left un-initialized; however, for non-AP1 devices all network numbers typically default to the public network
  key
- RF Frequency
  Default Frequency 2466MHz
- Device Number
  A Sample Serial Number
- Transmission Type
  byte: 0-1
            00: Reserved
            01: Independent Channel
            10: Shared Channel using 1 byte address (if supported)
            11: Shared Channel using 2 byte address
  byte 2
            Optional for non-ANT+ managed networks:
                0: Global data pages not used
                1: Global data pages used (e.g. ANT+ Common Data pages)
  byte 3
            Undefined – set to zero.
  byte 4-7
            Optional extension of the device number (MSN)
- Device Type
- Channel Type
  0x00 Bidirectional Slave Channel
  0x10 Bidirectional Master Channel
  0x20 Shared Bidirectional Slave Channel
  0x30 Shared Bidirectional Master Channel
  0x40 Slave Receive Only Channel (diagnostic)
  0x50 Master Transmit Only Channel (legacy)

- Channel Period
  16384 2Hz Message Rate
- Data Type

- CHANNEL IDs
  Only devices with matching channel IDs can communicate with each other. The channel ID represents the device
  type/number and transmission type of the master device and must be specified on the master device. On a slave device,
  these fields are set to determine which master device to communicate with. They can be set to match a specific master, or
  any/all of these fields can be set to zero, representing a wildcard value, such that the slave will find the first master
  matching other channel parameters (network key, frequency).
  
- Device number
  The device number should not be set to 0x0000 or 0xFFFF as these are reserved values

https://www.thisisant.com/developer/ant/ant-basics/
https://www.thisisant.com/developer/ant-plus/device-profiles#524_tab --> ANT Tempe profil

> Digi specifics
- 
https://www.digi.com/resources/documentation/digidocs/PDFs/90001458-13.pdf --> XCTU guide
