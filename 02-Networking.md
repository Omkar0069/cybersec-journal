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

**Who do I ask when I need to convert domain name into IP - It goes first in /etc/resolve.conf"