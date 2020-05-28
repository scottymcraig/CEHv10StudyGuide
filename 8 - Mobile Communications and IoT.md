# Mobile Communications and IoT

### <u>Mobile Platform Hacking</u>

- **Three Main Avenues of Attack**
  - **Device Attacks** - browser based, SMS, application attacks, rooted/jailbroken devices
  - **Network Attacks** - DNS cache poisoning, rogue APs, packet sniffing
  - **Data Center (Cloud) Attacks** - databases, photos, etc.

- **OWASP Top 10 Mobile Risks**
  - **M1 - Improper Platform Usage** - misuse of features or security controls (Android intents, TouchID, Keychain)
  - **M2 - Insecure Data Storage** - improperly stored data and data leakage
  - **M3 - Insecure Communication** - poor handshaking, incorrect SSL, clear-text communication
  - **M4 - Insecure Authentication** - authenticating end user or bad session management
  - **M5 - Insufficient Cryptography** - code that applies cryptography to an asset, but is insufficient (does NOT include SSL/TLS)
  - **M6 - Insecure Authorization** - failures in authorization (access rights)
  - **M7 - Client Code Quality** - catchall for code-level implementation problems
  - **M8 - Code Tampering** - binary patching, resource modification, dynamic memory modification
  - **M9 - Reverse Engineering** - reversing core binaries to find problems and exploits
  - **M10 - Extraneous Functionality** - catchall for backdoors that were inadvertently placed by coders

### <u>Mobile Platforms</u>

- **Android** - platform built by Google
  - **Rooting** - name given to the ability to have root access on an Android device
    - **Tools**
      - KingoRoot
      - TunesGo
      - OneClickRoot
      - MTK Droid
- **iOS** - platform built by Apple
  - **Jailbreaking** - different levels of rooting an iOS device
    - **Tools**
      - evasi0n7
      - GeekSn0w
      - Pangu
      - Redsn0w
      - Absinthe
      - Cydia
    - **Techniques**
      - **Untethered** - kernel remains patched after reboot, with or without a system connection
      - **Semi-Tethered** - reboot no longer retains patch; must use installed jailbreak software to re-jailbreak
      - **Tethered** - reboot removes all jailbreaking patches; phone may get in boot loop requiring USB to repair
    - **Types**
      - **Userland exploit** - found in the system itself; gains root access; does not provide admin; can be patched by Apple
      - **iBoot exploit** - found in bootloader called iBoot; uses vulnerability to turn codesign off; semi-tethered; can be patched
      - **BootROM exploit** - allows access to file system, iBoot and custom boot logos; found in device's first bootloader; cannot be patched
- **App Store attacks** - since some App stores are not vetted, malicious apps can be placed there
- **Phishing attacks** - mobile phones have more data to be stolen and are just as vulnerable as desktops
- **Android Device Administration API** - allows for security-aware apps that may help
- **Bring Your Own Device** (BYOD) - dangerous for organizations because not all phones can be locked down by default
- **Mobile Device Management** - like group policy on Windows; helps enforce security and deploy apps from enterprise
  - MDM solutions include XenMobile, IBM, MaaS360, AirWatch and MobiControl
- **Bluetooth attacks** - if a mobile device can be connected to easily, it can fall prey to Bluetooth attacks
  - **Discovery mode** - how the device reacts to inquiries from other devices
    - **Discoverable** - answers all inquiries
    - **Limited Discoverable** - restricts the action
    - **Nondiscoverable** - ignores all inquiries
  - **Pairing mode** - how the device deals with pairing requests
    - **Pairable** - accepts all requests
    - **Nonpairable** - rejects all connection requests

### <u>Mobile Attacks</u>

- **SMS Phishing** - sending texts with malicious links
  - People tend to trust these more because they happen less
  - **Trojans Available to Send**
    - Obad
    - Fakedefender
    - TRAMPS
    - ZitMo
  - **Spyware**
    - Mobile Spy
    - Spyera
- Mobile platform features such as Find my iPhone, Android device tracking and the like can be hacked to find devices, etc.
- **Mobile Attack Platforms** - tools that allow you to attack from your phone
  - Network Spoofer
  - DroidSheep
  - Nmap
- **Bluetooth Attacks**
  - **Bluesmacking** - denial of service against device
  - **Bluejacking** - sending unsolicited messages
  - **Bluesniffing** - attempt to discover Bluetooth devices
  - **Bluebugging** - remotely using a device's features
  - **Bluesnarfing** - theft of data from a device
  - **Blueprinting** - collecting device information over Bluetooth
- **Bluetooth Attack Tools**
  - **BlueScanner** - finds devices around you
  - **BT Browser** - another tool for finding and enumerating devices
  - **Bluesniff** and **btCrawler** - sniffing programs with GUI
  - **Bloover** - can perform Bluebugging
  - **PhoneSnoop** - good spyware option for Blackberry
  - **Super Bluetooth Hack** - all-in-one package that allows you to do almost anything

### <u>IoT Architecture</u>

- **Definition** - a collection of devices using sensors, software, storage and electronics to collect, analyze, store and share data
- **Three Basic Components**
  - Sensing Technology
  - IoT gateways
  - The cloud
- **Operating Systems**
  - **RIOT OS** - embedded systems, actuator boards, sensors; is energy efficient
  - **ARM Mbed OS** - mostly used on wearables and other low-powered devices
  - **RealSense OS X** - Intel's depth sensing version; mostly found in cameras and other sensors
  - **Nucleus RTOS** - used in aerospace, medical and industrial applications
  - **Brillo** - Android-based OS; generally found in thermostats
  - **Contiki** - OS made for low-power devices; found mostly in street lighting and sound monitoring
  - **Zephyr** - option for low-power devices and devices without many resources
  - **Ubuntu Core** - used in robots and drones; known as "snappy"
  - **Integrity RTOS** - found in aerospace, medical, defense, industrial and automotive sensors
  - **Apache Mynewt** - used in devices using Bluetooth Low Energy Protocol
- **Methods of Communicating**
  - **Device to Device** - communicates directly with other IoT devices
  - **Device to Cloud** - communicates directly to a cloud service
  - **Device to Gateway** - communicates with a gateway before sending to the cloud
  - **Back-End Data Sharing** - like device to cloud but adds abilities for parties to collect and use the data
- **Architecture Levels**
  - **Edge Technology Layer** - consists of sensors, RFID tags, readers and the devices
  - **Access Gateway Layer** - first data handling, message identification and routing
  - **Internet Layer** - crucial layer which serves as main component to allow communication
  - **Middleware Layer** - sits between application and hardware; handles data and device management, data analysis and aggregation
  - **Application Layer** - responsible for delivery of services and data to the user

### <u>IoT Vulnerabilities and Attacks</u>

- **I1 - Insecure Web Interface** - problems such as account enumeration, weak credentials, and no account lockout
- **I2 - Insufficient Authentication/Authorization** - assumes interfaces will only be exposed on internal networks and thus is a flaw
- **I3 - Insecure Network Services** - may be susceptible to buffer overflow or DoS attacks
- **I4 - Lack of Transport Encryption/Integrity Verification** - data transported without encryption
- **I5 - Privacy Concerns** - due to collection of personal data
- **I6 - Insecure Cloud Interface** - easy-to-guess credentials make enumeration easy
- **I7 - Insecure Mobile Interface** - easy-to-guess credentials on mobile interface
- **I8 - Insufficient Security Configurability** - cannot change security which causes default passwords and configuration
- **I9 - Insecure Software/Firmware** - lack of a device to be updated or devices that do not check for updates
- **I10 - Poor Physical Security** - because of the nature of devices, these can easily be stolen

- **Sybil Attack** - uses multiple forged identities to create the illusion of traffic
- **HVAC Attacks** - attacks on HVAC systems
- **Rolling Code** - the ability to jam a key fob's communications, steal the code and then create a subsequent code
- **BlueBorne Attack** - attacks against Bluetooth devices

- Other attacks already enumerated in other sections still apply such as MITM, ransomware, side channel

### <u>IoT Hacking Methodology</u>

- **Steps**
  - **Information Gathering** - gathering information about the devices; useful resource is Shodan (Google for IoT devices connected to Internet)
    - **Foren6** - IoT traffic sniffer
  - **Vulnerability Scanning** - same as normal methodology - looks for vulnerabilities
    - **Tools**
      - Nmap
      - RIoT Vulnerability Scanner
      - beSTORM
      - IoTsploit
      - IoT Inspector
  - **Launching Attacks**
    - **Tools**
      - Firmalyzer
      - KillerBee
      - JTAGulator
      - Attify
  - **Gaining Access** - same objectives as normal methodology
  - **Maintaining Access** - same objectives as normal methodology
