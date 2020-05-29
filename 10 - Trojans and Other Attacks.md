# Trojans and Other Attacks

### <u>Malware Basics</u>

- **Malware** - software designed to harm or secretly access a computer system without informed consent
- Most is downloaded from the Internet with or without the user's knowledge
- **Overt Channels** - legitimate communication channels used by programs
- **Covert Channels** - used to transport data in unintended ways
- **Wrappers** - programs that allow you to bind an executable to an innocent file
- **Crypters** - use a combination of encryption and code manipulation to render malware undetectable to security programs
- **Packers** - use compression to pack the executable which helps evage signature based detection
- **Exploit Kits** - help deliver exploits and payloads
  - Infinity
  - Bleeding Life
  - Crimepack
  - Blackhole Exploit Kit

### <u>Trojans</u>

- **Trojans** - software that appears to perform a desirable function but instead performs malicious activity
  - To hackers, it is a method to gain and maintain access to a system
  - Trojans are means of delivery whereas a backdoor provides the open access
- **Types**
  - **Defacement trojan**
  - **Proxy server trojan**
  - **Botnet trojan**
    - Chewbacca
    - Skynet
  - **Remote access trojans**
    - RAT
    - MoSucker
    - Optix Pro
    - Blackhole
  - **E-banking trojans**
  	- Zeus
  	- Spyeye
  - **Command Shell Trojan** - Provides a backdoor to connect to through command-line access
    - Netcat
- **Covert Channel Tunneling Trojan** (CCTT) - a RAT trojan; creates data transfer channels in previously authorized data streams
- **Netcat**
  - "Swiss army knife" of tcp/ip hacking
  - Provides all sorts of control over a remote shell on a target
  - Connects via **nc -e IPaddress Port#**
  - From attack machine **nc -l -p 5555** opens a listening port on 5555
  - Can connect over TCP or UDP, from any port
  - Offers DNS forwarding, port mapping and forwarding and proxying
- **Trojan Port Numbers**

| Trojan Name        | Port   |
|--------------------|--------|
| Death              | 2      |
| Senna Spy          | 20     |
| Hackers Paradise   | 31,456 |
| TCP Wrappers       | 421    |
| Doom, Santaz Back  | 666    |
| Silencer, WebEx    | 1001   |
| RAT                | 1095-98|
| SubSeven           | 1243   |
| Shiva-Burka        | 1600   |
| Trojan Cow         | 2001   |
| Deep Throat        | 6670-71|
| Tini               | 7777   |
| NetBus             | 12345-6|
| Whack a Mole       | 12361-3|
| Back Orifice       | 31337,8|

- **netstat -an** - shows open ports in numerical order
- **netstat -b** - displays all active connections and the processes using them
- **Process Explorer** - Microsoft tool that shows you everything about running processes
- **Registry Monitoring Tools**
  - SysAnalyzer
  - Tiny Watcher
  - Active Registry Monitor
  - Regshot
- **Msconfig** - Windows program that shows all programs set to start on startup
- **Tripwire** - integrity verifier that can act as a HIDS in protection against trojans
- **SIGVERIF** - build into Windows to verify the integrity of the system
  - Log  file can be found at c:\windows\system32\sigverif.txt
  - Look for drivers that are not signed

### <u>Viruses and Worms</u>

- **Virus** - self-replicating program that reproduces by attaching copies of itself into other executable code
  - Usually installed by user clicking on malicious file attachments or downloads
  - **Fake Antivirus** - tries to convince a user has a virus and have them download an AV that is a virus itself
- **Ransomware** - malicious software designed to deny access to a computer until a price is paid; usually spread through email
  - **WannaCry** - famous ransomware; within 24 hours had 230,000 victims; exploited unpatched SMB vulnerability
  - **Other Examples**
    - Cryptorbit
    - CryptoLocker
    - CryptoDefense
    - police-themed
- **Other Virus Types**
  - **Boot Sector Virus** - known as system virus; moves boot sector to another location and then inserts its code int he original location
  - **Shell Virus** - wraps  around an application's code, inserting itself before the application's
  - **Cluster Virus** - modifies directory table entries so every time a file or folder is opened, the virus runs
  - **Multipartite Virus** - attempts to infect both boot sector and files; generally refers to viruses with multiple infection methods
  - **Macro Virus** - written in VBA; infects template files - mostly Word and Excel
  - **Polymorphic Code Virus** - mutates its code by using a polymorphic engine; difficult to find because code is always changing
  - **Encryption Virus** - uses  encryption to hide the code from antivirus
  - **Metamorphic Virus** - rewrites itself every time it infects a new file
  - **Stealth Virus** - known as a tunneling virus; attempts to evade AVs by intercepting their requests and returning them instead of letting them pass to the OS
  - **Cavity Virus** - overwrite portions of host files as to not increase the actual size of the file; uses null content sections
  - **Sparse Infector Virus** - only infects occasionally (e.g. every 10th time)
  - **File Extension Virus** - changes the file extensions of files to take advantage of most people having them turned off (readme.txt.vbs shows as readme.txt)
- **Virus Makers**
  - Sonic Bat
  - PoisonVirus Maker
  - Sam's Virus Generator
  - JPS Virus Maker
- **Worm** - self-replicating malware that sends itself to other computers without human intervention
  - Usually doesn't infect files - just resides in active memory
  - Often used in botnets
- **Ghost Eye Worm** - hacking tool that uses random messaging on Facebook and other sites to perform a host of malicious efforts

### <u>Analyzing Malware</u>

- **Steps**
  1. Make sure you have a good test bed
     - Use a VM with NIC in host-only mode and no open shares
  2. Analyze the malware on the isolated VM in a static state
     - Tools - binText and UPX help with looking at binary
  3. Run the malware and check out processes
     - Use Process Monitor, etc. to look at processes
     - Use NetResident, TCPview or even Wireshark to look at network activity
  4. Check and see what files were added, changed, or deleted
     - Tools - IDA Pro, VirusTotal, Anubis, Threat Analyzer
- **Preventing Malware**
  - Make sure you know what is going on in your system
  - Have a good antivirus that is up to date
  - **Sheepdip** - system that is used to check things introduced into a network
    - Is airgapped

### <u>Denial of Service Attacks</u>

- Seeks to take down a system or deny access to it by authorized users
- **Botnet** - network of zombie computers a hacker uses to start a distributed attack
  - Can be controlled over HTTP, HTTPS, IRC, or ICQ
- **Basic Categories**
  - **Fragmentation attacks** - attacks take advantage of the system's ability to reconstruct fragmented packets
  - **Volumetric attacks** - bandwidth attacks; consume all bandwidth for the system or service
  - **Application attacks** - consume the resources necessary for the application to run
    - Note - application level attakcs are against weak code; application attacks are just the general term
  - **TCP state-exhaustion attacks** - go after load balancers, firewalls and application servers
  - **SYN attack** - sends thousands of SYN packets to the machine with a false source address; eventually engages all resources and exhausts the machine
  - **SYN flood** - sends thousands of SYN packets; does not spoof IP but doesn't respond to the SYN/ACK packets; eventually bogs down the computer, runs out of resources
  - **ICMP flood** - sends ICMP Echo packets with a spoofed address; eventually reaches limit of packets per second sent
  - **Smurf** - large number of pings to the broadcast address of the subnet with source IP spoofed as the target; entire subnet responds exhausting the target
  - **Fraggle** - same as smurf but with UDP packets
  - **Ping of Death** - fragments ICMP messages; after reassembled, the ICMP packet is larger than the maximum size and crashes the system
  - **Teardrop** - overlaps a large number of garbled IP fragments with oversized payloads; causes older systems to crash due to fragment reassembly
  - **Peer to peer** - clients of peer-to-peer file-sharing hub are disconnected and directed to connect to the target system
  - **Phlashing** - a DoS attack that causes permanent damage to a system; also called bricking a system
  - **LAND attack** - sends a SYN packet to the target with a spoofed IP the same as the target; if vulnerable, target loops endlessly and crashes
- **Low Orbit Ion Cannon** (LOIC) - DDoS tool that floods a target with TCP, UDP or HTTP requests
- **Other Tools**
  - Trinity - Linux based DDoS tool
  - Tribe Flood Network - uses voluntary botnet systems to launch massive flood attacks
  - R-U-Dead-Yet (RUDY) - DoS with HTTP POST via long-form field submissions

### <u>Session Hijacking</u>

- Attacker waits for a session to begin and after the victim authenticates, steals the session for himself
- **Steps**
  1. Sniff the traffic between the client and server
  2. Monitor the traffic and predict the sequence numbering
  3. Desynchronize the session with the client
  4. Predict the session token and take over the session
  5. Inject packets to the target server
- Can be done via brute force, calculation or stealing
- Predicting can be done by knowing the window size and the packet sequence number
- Sequence numbers increment on **acknowledgement**
  - For example, an acknowledgement of 105 with a window of 200 means you could expect sequence numbering from 105 to 305
- **Tools**
  - **Ettercap** - man-in-the-middel tool and packet sniffer on steroids
  - **Hunt** - sniff, hijack and reset connections
  - **T-Sight** - easily hijack sessions and monitor network connections
  - **Zaproxy**
  - **Paros**
  - **Burp Suite**
  - **Juggernaut**
  - **Hamster**
  - **Ferret**
- **Countermeasures**
  - Using unpredictable session IDs
  - Limiting incoming connections
  - Minimizing remote access
  - Regenerating the session key after authentication
  - Use IPSec to encrypt
- **IPSec**
  - **Transport Mode** - payload and ESP trailer are encrypted; IP header is not
  - **Tunnel mode** - everything is encrypted; cannot be used with NAT
  - **Architecture Protocols**
    - **Authentication Header** - guarantees the integrity and authentication of IP packet sender
    - **Encapsulating Security Payload** (ESP) - provides origin authenticity and integrity as well as confidentiality
    - **Internet Key Exchange** (IKE) - produces the keys for the encryption process
    - **Oakley** - uses Diffie-Hellman to create master and session keys
    - ** Internet Security Association Key Management Protocol** (ISAKMP) - software that facilitates encrypted communication between two endpoints
