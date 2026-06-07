Packets - Contains all the data of the layers above, application, presentation, session, transport.
Frames - Messages that deals with layer 2, mac address etc

**Layer of OSI Model**
Application Layer - User Interacts with this layer, gateway to the next layers
Presentation Layer - Responsible for making the presentation, keywords would be dataformat (.pdf, .exe, .html etc) and encryption(keep data encryption)
Session Layer - Starts communication between client and server keeps the thing going
Transport Layer - Use protocols to transport the data the two main transport protocols are TCP (Transmission Control Protocol) and UDP(), TCP is slow but reliable method used in documents, emails etc UDP is fast but data may get lost mainly use in gaming, graphical representations etc
TCP three way handshake is used to setup the connection
Network Layer - Deals with IP addresses, router falls under this layer
Data Link Layer - Deals with mac addresses and arp tables switches falls under this layer
Physical Layer - actual wire connected to the devices, transfer data in binary

**SOME IMPORTANT NETWORKING PROTOCOL**
1. DNS (Domain Name System): Converts Domain name into IPs
2. DHCP (Dynamic Host Configuration Protocol): Assigns IPs to the devices
3. FTP (File Transfer Protocol): Transfer files between computers
4. HTTP (HyperText Transfer Protocol): Loads websites
5. SMTP (Simple Mail Transfer Protocol): Sends email
6. SMNP (Simple Network Management Protocol): Monitors and manages network devices
7. TFTP (Trivial File Transfer Protocol): Simple file transfer, often used to network device configuration

**Who do I ask when I need to convert domain name into IP or any DNS queries" - It goes first in /etc/resolve.conf - This file tells your system where to send DNS queries — it's your machine's DNS configuration file. When you type google.com anywhere, your system reads this file first to know which DNS server to ask "what's the IP for google.com?"

**COMMANDS**
1. ip a - Short form for ip address shows and manages IP addresses assigned to your network interface. Its part of iproute2 suite and replace the older ipconfig

Syntax: ip [options] a [command] [argument]
Output: 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 52:54:00:d3:92:38 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.186/24 brd 192.168.122.255 scope global dynamic noprefixroute eth0
       valid_lft 3208sec preferred_lft 3208sec
    inet6 fe80::5054:ff:fed3:9238/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


2. ip route - The routing table is the kernal's decision engine - when packets leaves you machine kernal check the table to figure out: which interface does it go out on, and who should handed to the next gateway, ip route reads and manages that table.
Syntax: ip route
Output:
default via 192.168.122.1 dev eth0 proto dhcp src 192.168.122.186 metric 100 
192.168.122.0/24 dev eth0 proto kernel scope link src 192.168.122.186 metric 100 

3. nslookup - It stand for Name Server Lookup it's job is to ask DNS server - What IP address belongs to this domain name? DNS is like internets phonebook
Syntax: nslookup *ipaddress/domainname*
Output:
Server:		192.168.122.1
Address:	192.168.122.1#53

Non-authoritative answer:
Name:	google.com
Address: 192.178.174.100
Name:	google.com
Address: 192.178.174.101
Name:	google.com
Address: 192.178.174.138
Name:	google.com
Address: 192.178.174.113
Name:	google.com
Address: 192.178.174.102
Name:	google.com
Address: 192.178.174.139
Name:	google.com
Address: 2404:6800:4009:805::200e

4. dig - dig or Domain Information Groper its more advanced DNS investigation tool than nslookup
Syntax: dig *ipaddress/domainname*
Output:
; <<>> DiG 9.20.23-1-Debian <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10932
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		259	IN	A	192.178.174.101
google.com.		259	IN	A	192.178.174.113
google.com.		259	IN	A	192.178.174.100
google.com.		259	IN	A	192.178.174.138
google.com.		259	IN	A	192.178.174.139
google.com.		259	IN	A	192.178.174.102

;; Query time: 760 msec
;; SERVER: 192.168.122.1#53(192.168.122.1) (UDP)
;; WHEN: Sat Jun 06 15:38:59 IST 2026
;; MSG SIZE  rcvd: 135

5. curl: curl or Client URL is a command line tool use for transferring data over network. It supports HTTP, HTTPS, SMTP, FTP, and 30+ other network protocols.

Syntax: curl [flags] [URL]