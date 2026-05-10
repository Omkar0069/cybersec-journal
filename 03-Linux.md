***Currently I am using Linux basics for hacker (Second Edition) as my study material so I'll be using this to keep account of myself at this point I've already completed 12 chapters out of 18 I'll be writing what I learned in short***

**Chapter 13 - BECOMING SECURE AND ANONYMOUS**
There can be as many as 20 - 30 hops between the sender and destination, but usually the packet finds it way to the destination within less then 15 hops

**Chapter 14 - UNDERSTANDING AND INSPECTING WIRELESS NETWORKS**
Basic wifi terms
AP (access point): This is the wireless device user connects to for internet access.
ESSID (Extended Service Set Identifier): Basicially the names of the wifis, Extended is used in multiple APs in wireless lan
BSSID (Basic Service Set Identifier): This is the unique identifer for each AP, just like a MAC address of the devices
SSID (Service Set Identifier): The name of the Networks
Channels: Wifi can operate on any one of the 14 channels (1 to 14). In U.S. it is limited upto 11 Channels
Power: The closer you are to the Wifi AP, the greater the power, and easier the connection is to crack.
Security: This is the Wifi security protocol that is being read from,
            - Original: Wired Equivalent Privacy (WEP)
            - Later on shift to: Wifi Protected Access (WPA)
            - Finally WPA2 PSK(Preshared key) introduced
            - WPA3 PSK is used by modern industry
Modes: Wifi can Operate in one of the 3 modes: managed, master and monitor
Wireless Range: In U.S., Wifi must legally broadcast its signal at an upper limit of 0.5 watt. At this power it has a normal range from 300 feet (100 meters). High-gain antennas can extend this range to as much as 20 miles!
Frequency: Wifi is designed to operate on 2.4GHz and 5GHz, modern wifi APs and wireless network cards use both.

nmcli dev wifi - shows all the wifi aps in the radius 