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

**Linux Filesystem**: In Linux filesystem is a hierarchical structure to organise, store and manage files and directories. It follows a tree like structure starting from a single root directory /.
In linux everything is file; regular text, images, binaries are files, directories are folders, devices are treated as file (e.g., hard disk, USB), process and sockets also appears to be a file
This is the linux's everything is file philosophy.

Directories and structures:

    /
    |----bin
    |----etc
    |----home
    |----var
    |----usr
    |----...

/ = root directory, topmost directory and contains all other directory, everything starts from here

**Important Directories**

1. /bin (binary executables): Essential command binaries, used by all users, e.g., ls, cp, mv, cat mainly used to execute commands if any binary is removed the command will not work related to that binary.
2. /home: This is the home directory of the user contains all the user's private files, documents, etc
3. /etc: This directory contains all the system configuration files, e.g., /etc/passwd /etc/shadow /etc/network etc
4. /root: Home directory for the root user
5. /var: Frequently changed data, /var/log /var/cache /var/mail
6. /usr: User Program, Secondary Hierarchy, contains: /usr/bin - user commands, /usr/lib - libraries /usr/share - shared data
7. /dev: Hardware devices are represented as files, /dev/sda - hard disk /dev/null - null device
8. /tmp: Contains temporary files, usually deleted after boot

**Types of Files in Linux**

**Types**               **Symbol**              **Description**
- Regular file        -                   Text, binary
- Directory           d                   Folder
- Link                l                   Shortcut
- Character device    c                   Keyboard, Mouse
- Block Device        b                   Hard Disk
- Socket              s                   Communication
- Pipes               p                   Inter-process communication

**Commands**
- pwd - Prints working directory or the absolute path till the current directory
- ls - Lists the files and folders in the current directory, use -a flag to show all the files and folders including hidden files and -l is used to show a detailed info like size, owner, user, permissions etc
- cd - Used to navigate from one directory to another, use cd .. to move 1 level up (We cannot navigate inside files)
- mkdir - Creates directory, mkdir *directory_name*
- rmdir - Removes directory, rmdir *directory_name* (Note: rmdir cannot remove non-empty directory)
- touch - Used to create files, touch *filename*
- rm - Used to remove files, use rm -r *directory_name* to remove non-empty directory
- cp - Used to copy, cp *source* *destination*
- mv - Used to move and rename file mv *source* *destination* | mv *oldname* *newname*
- cat - Used to display data from file, cat *filename*
- nano - Inbuild Text editor, nano *filename* if the file exist opens existing file else create a new file and opens that

**PERMISSIONS**

**chown**: Is used to change owner and/or owner and group
sudo chown owner filename
sudo chown owner:group filename
**chgrp**: Used to change group
sudo chgrp groupname filename
**chmod**: Used to change mode(Permissions)
sudo chmod (permission) filename. e.g., chmod 700 secret.txt

To switch between users use *su - username* command
To change password: sudo passwd username
To remove user: sudo userdel username
To remove group: sudo groupdel groupname

**sudo**
sudo commands means "superuser do" it lets the authorized user to run a command with elevated privileges usually admin/root without logging in as root.
Used in:
- Installing software
- edit /etc configurations
- chown
- chmod
- permissions
- modify system networking settings

Basic syntax: sudo command

**How to add a file to path**

1. create a file
2. create a folder: ~/.local/bin
3. make it executable: sudo chmod +x ~/.local/bin/file
4. move that file there: mv file ~/.local/bin
5. set the path: export PATH=$PATH:$HOME/.local/bin
6. Done!
Now you can call that file from anywhere regardless in what directory you are in, LOL!


**Hidden Files**
In linux hidden files are listed with [.] at the beginning, they are not specially encrypted or smth like that just hidden using normal listing for convention to view all the files including hidden files use ls with -a flag, i.e., ls -a
Some important hidden files:
1. .bashrc: runs shell settings for interactive bash shell.
2. .profile: login shell environment setup.
3. .ssh/: contains ssh keys, authorized_keys, config.
4. .git/: git repository metadat.
5. .config/: modern apps store per-user config here.

**What is openssl?**
A toolbox for secure communication and cryptography

To start a connection between sever use the follow command:
*openssl s_client -connect localhost:30001*
openssl: for secure communication
s_client: secure client i.e., SSL/TLS client
-connect: start connection
localhost:30001 : at localhost on port 30001

**COMMANDS**
1. ping - Ping is a network diagnostic utility to check reachability, latency and packet loss between your machine and the host on a network. It sends ICMP Echo Request packets and waits for ICMP Echo Reply responses.

Syntax: ping google.com

What a packet actually is
A packet is literally just a labelled envelope of data. It has a "from" address (source IP), a "to" address (destination IP), a TTL countdown, a type code, some dummy payload bytes, and a checksum to verify nothing got corrupted. That's it. Nothing magical — just structured bytes.

What a packet does
It carries your "Hello, are you there?" question from your machine, hop by hop through routers, until it reaches the target. The target reads the Type field (8 = echo request), flips it to Type 0 (echo reply), and sends the exact packet back to you. Your OS measures the time between send and reply — that's your RTT (round-trip time).

    1. Resolves IP address of google.com using DNS server
    2. Sends ICMP Echo Request packets to that IP (ICMP is Internet Control Message Protocol is used to send error, control and diagnostic message in an IP network, It does not contains the actual data just like bruh your message didn't make it)
    3. Waits for the reply packets
    4. Measures Round Trip Time(RTT)
    5. Repeats continuosly until stopped (Ctrl + C)

Important Options
    -c: Send fixed number of packets., ping -c 5 google.com
    -i: Intervals, seconds between packets., ping -i 2 google.com
    -w: Timeout, wait time for each reply
    -p: Custom payload size., ping -p 1000 google.com
    -4: ipv4
    -6: ipv6
    -f: flood, sends packet as fast as possible
    -a: audible, beeps when response recieved

2. curl - curl or Client URL is a command line tool use for transferring data over network. It supports HTTP, HTTPS, SMTP, FTP, and 30+ other network protocols.

Syntax: curl [flags] [URL]

Important Flags:
    -x POST: Set HTTP method(GET, PUT, POST, DELETE...)
    -H "Key: val": Add a custom header
    -d "data": Send POST body data
    -I: Fetch header only(Head request)
    -i: Show header + body together
    -v: Verbose, full http conversation
    -L: Follow redirects
    -o file.html: Save output to file

3. wget - web-get is a non-interactive download tool pre-installed in kali. Simpler version of curl, wget is used for downloading stuff, especially recursively.

Syntax: wget [flag] [URL]

Important Flags:
    -v: Verbose
    -r: Download recursively
    -q: Quiet mode(No output)
    -c: Resume interrupted download
    -o file.html: Save custom filename

4. ssh - ssh or Secure Shell is cryptographic tool used to remotely access other machines. On Kali, it's your primary access tool for remote access, pivoting, tunneling, and port forwarding during pentests.

Syntax: ssh [user]@[host] -p [port]
e.g., ssh localhost (make sure to use sudo systemctl start ssh)

Important Flags:
    -p: connect to custom port default is 22
    -i: Use private keyfile for authentication
    -L: Local port forwarding
    -R: Remote port forwarding
    -D: Dynamic port forwarding
    -f: Run in background
    -v: Verbose

5. netstat - netstat or network statistic is a CLI tool used to monitor network connections, open ports, routing tables, interface stats. It is used for recon, finding what's running locally and spoting suspicious connections.

Syntax: netstat [flags]
Important Flags:
    -t: Show TCP connections
    -u: Show UDP connections
    -a: Show all connections(listen + established)
    -p: Show PID + Process name
    -n: Show IPs numerically

6. ss: Socket Statistics is the modern replacement for netstat. Faster, more detailed and build into every linux system. On Kali it is used to inspect socket, open ports, and active connections

Syntax: ss [flag]

Important Flags:
    -t: Show TCP connections
    -u: Show UDP connections
    -l: Listening ports only
    -n: Numeric IPs
    -p: Show PID + Process name

7. ip: Modern tool replacement for ifconfig and route. It is used for managing network interface, routing ARP tables and tunnels. Part of iproute2 package - always available.

Syntax: ip [object] [command]

Important Flags:
    ip addr: Show IP addresses on all interface.
    ip link: Show network interfaces
    ip route: Show routing table
    ip neigh: Show ARP table
    ip tunnel: Manages tunnels
    ip rule: Show routing policy rules

8. ifconfig: Similar to ip but used in old school, shows and configures network interfaces

syntax: ifconfig

9. traceroute: traceroute maps the path packets take from you machine to target-every hop(router) along the way. Used for network recon, latency diagnosis, and mapping infrastructure.

Syntax: traceroute [flag] [target]

Important Flags:
    -n: Numeric IPs, no DNS lookup
    -m: 20 Max hops(default 30)
    -w 3: Wait 3 seconds per hop
    -I: Use ICMP instead of UDP
    -T: Use TCP 
    -p: Use specific port
    -i: Use specific interface