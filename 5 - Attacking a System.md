# Attacking a System

<u>Windows Security Architecture</u>

- Authentication credentials stored in SAM file
- File is located at C:\windows\system32\config
- Older systems use LM hashing.  Current uses NTLM v2 (MD5)
- Windows network authentication uses Kerberos
- **LM Hashing**
  - Splits the password up.  If it's over 7 characters, it is encoded in two sections.
  - If one section is blank, the hash will be AAD3B435B51404EE
  - Easy to break if password  is 7 characters or under because you can split the hash
- SAM file presents as UserName:SID:LM_Hash:NTLM_Hash:::
- **Ntds.dit** - database file on a domain controller that stores passwords
  - Located in %SystemRoot%\NTDS\Ntds.dit or
  - Located in %SystemRoot%System32\Ntds.dit
  - Includes the entire Active Directory
- **Kerberos**
  - Steps of exchange
    1. Client asks **Key Distribution Center** (KDC) for a ticket.  Sent in clear text.
    2. Server responds with **Ticket Granting Ticket** (TGT).  This is a secret key which is hashed by the password copy stored  on the server.
    3. If client can decrypt it, the TGT is sent back to the server requesting a **Ticket Granting Service** (TGS) service ticket.
    4. Server sends TGS service ticket which client uses to access resources.
  - **Tools**
    - KerbSniff
    - KerbCrack
    - Both take a  long time to crack
- **Registry**
  - Collection of all settings and configurations that make the system run
  - Made up of keys and values
  - Root level keys
    - **HKEY_LOCAL_MACHINE** (HKLM) - information on hardware and software
    - **HKEY_CLASSES_ROOT** (HKCR) - information on file associates and OLE classes
    - **HKEY_CURRENT_USER** (HKCU) - profile information for the current user including preferences
    - **HKEY_USERS** (HKU) - specific user configuration information  for all currently active users
    - **HKEY_CURRENT_CONFIG** (HKCC) - pointer to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Hardware Profiles\Current
  - Type of values
    - **REG_SZ** - character string
    - **REG_EXPAND_SZ** - expandable string value
    - **REG_BINARY** - a binary value
    - **REG_DWORD** - 32-bit unsigned integer
    - **REG_LINK** - symbolic link to another key
  - Important Locations
    - HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce
    - HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServices
    - HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce
    - HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
  - Executables to edit
    - regedit.exe
    - regedt32.exe (preferred by Microsoft)
- **MMC**
  - Microsoft Management Console - used by Windows to administer system
  - Has "snap-ins" that allow you to modify sets (such as Group Policy Editor)

### <u>Linux Security Architecture</u>

- Linux root is just a slash (/)
- Important locations
  - **/** - root directory
  - **/bin** - basic Linux commands
  - **/dev** - contains pointer locations to various storage and input/output systems
  - **/etc** - all administration files and passwords.  Both password and shadow files are here
  - **/home** - holds the user home directories
  - **/mnt** - holds the access locations you've mounted
  - **/sbin** - system binaries folder which holds more administrative commands
  - **/usr** - holds almost all of the information, commands and files unique to the users
- Linux Commands

| Command  | Description                                                  |
| -------- | ------------------------------------------------------------ |
| adduser  | Adds a user to the system                                    |
| cat      | Displays contents of file                                    |
| cp       | Copies                                                       |
| ifconfig | Displays network configuration information                   |
| kill     | Kills a running process                                      |
| ls       | Displays the contents of a folder.  -l option provides most information. |
| man      | Displays the manual page for a command                       |
| passwd   | Used to change password                                      |
| ps       | Process status.  -ef option shows all processes              |
| rm       | Removes files.  -r option recursively removes all directories and subdirectories |
| su       | Allows you to perform functions as another user (super user) |

- Adding an ampersand after a process name indicates it should run in the background.
- **pwd** - displays curennt directory
- **chmod** - changes the permissions of a folder or file
  - Read is 4, write is 2 and execute is 1
  - First number is user, second is group, third is others
  - Example - 755 is everything for users, read/execute for group, and read/execute for others
- Root has UID and GID of 0
- First user has UID and GID of 500
- Passwords are stored in /etc/shadow for most current systems
- /etc/password stores passwords in hashes.
- /etc/shadow stores passwords encrypted (hashed and salted) and is only accessible by root

### <u>System Hacking Goals</u>

- **Gaining Access** - uses information gathered to exploit the system
- **Escalating Privileges** - granting the account you've hacked admin or pivoting to an admin account
- **Executing Applications** - putting back doors into the system so that you can maintain access
- **Hiding Files** - making sure the files you leave behind are not discoverable
- **Covering Tracks** - cleaning up everything else (log files, etc.)
  - **clearev** - meterpreter shell command to clear log files
  - Clear MRU list in Windows
  - In Linux, append a dot in front of a file to hide it

### <u>Authentication and Passwords</u>

- **Three Different Types**
  - **Something You Are** - uses biometrics to validate identity (retina, fingerprint, etc.)
    - Downside is there can be lots of false negatives
    - **False acceptance rate** (FAR) - rate that a system accepts access for people that shouldn't have it
    - **False rejection rate** (FRR) - rate that a system rejects access for someone who should have it
    - **Crossover error rate** (CER) - combination of the two; the lower the CER, the better the system
    - **Active** - requires interaction (retina scan or fingerprint scanner)
    - **Passive** - requires no interaction (iris scan)
  - **Something You Have** - usually consists of a token of some kind (swipe badge, ATM card, etc.)
    - This type usually requires something alongside it (such as a PIN for an ATM card)
    - Some tokens are single-factor (such as a plug-and-play authentication)
  - **Something You Know** - better known as a password
    - Most systems use this because it is universal and well-known

- **Two-Factor** - when you have two types of authentication such as something you know (password) and something you have (access card)

- **Strength of passwords** - determined by length and complexity
  - ECC says that both should be combined for the best outcome
  - Complexity is defined by number of character sets used (lower case, upper case, numbers, symbols, etc.)
- **Default passwords** - always should be changed and never left what they came with.  Databases such as cirt.net, default-password.info and open-sez.me all have databases of these

### <u>Password Attacks</u>

- **Non-electronic** - social engineering attacks - most effective.
  - Includes shoulder surfing and dumpster diving
- **Active online** - done by directly communicating with the victim's machine
  - Includes dictionary and brute-force attacks, hash injections, phishing, Trojans, spyware, keyloggers and password guessing
  - **Keylogging** - process of using a hardware device or software application to capture keystrokes of a user
  - **LLMNR/NBT-NS** - attack based off Windows technologies that caches DNS locally.  Responding to these poisons the local cache.  If an NTLM v2 hash is sent over, it can be sniffed out and then cracked
    - **Tools**
      - NBNSpoof
      - Pupy
      - Metasploit
      - Responder
    - LLMNR uses UDP 5355
    - NBT-NS uses UDP 137
  - Active online attacks are easier to detect and take a longer time
  - Can combine "net" commands with a tool such as **NetBIOS Auditing tool** or **Legion** to automate the testing of user IDs and passwords
  - **Tools**
    - Hydra
    - Metasploit
- **Passive online** - sniffing the wire in hopes of intercepting a password in clear text or attempting a replay attack or man-in-the-middle attack
  - **Tools**
    - **Cain and Abel** - can poison ARP and then monitor the victim's traffic
    - **Ettercap** - works very similar to Cain and Abel.  However, can also help against SSL encryption
    - **KerbCrack** - built-in sniffer and password cracker looking for port 88 Kerberos traffic
    - **ScoopLM** - specifically looks for Windows authentication traffic on the wire and has a password cracker
- **Offline** - when the hacker steals a copy of the password file and does the cracking on a separate system
  - **Dictionary Attack** - uses a word list to attack the password.  Fastest method of attacking
  - **Brute force attack** - tries every combination of characters to crack a password
    - Can be faster if you know parameters (such as at least 7 characters, should have a special character, etc.)
  - **Hybrid attack** - Takes a dictionary attack and replaces characters (such as a 0 for an o) or adding numbers to the end
  - **Rainbow tables** - uses pre-hashed passwords to compare against a password hash.  Is faster because the hashes are already computed.
  - **Tools**
    - Cain
    - KerbCrack
    - Legion
    - John the Ripper

### <u>Privilege Escalation and Executing Applications</u>

- **Vertical** - lower-level user executes code at a higher privilege level
- **Horizontal** - executing code at the same user level but from a location that would be protected from that access
- **Four Methods**
  - Crack the password of an admin - primary aim
  - Take advantage of an OS vulnerability
    - **DLL Hijacking** - replacing a DLL in the application directory with your own version which gives you the access you need
  - Use a tool that will provide you the access such as Metasploit
  - Social engineering a user to run an application
- ECC refers executing applications as "owning" a system
- **Executing applications** - starting things such as keyloggers, spyware, back doors and crackers

### <u>Hiding Files and Covering Tracks</u>

- In Windows, **Alternate Data Stream** (ADS) can hide files
  - Hides a file from directory listing on an NTFS file system
  - readme.txt:badfile.exe
  - Can be run by start readme.txt:badfile.exe
  - You can also create a link to this and make it look real (e.g. mklink innocent.exe readme.txt:badfile.exe)
  - Every forensic kit looks for this, however
  - To show ADS, dir /r does the trick
  - You can also blow away all ADS by copying files to a FAT partition
- You can also hide files by attributes
  - In Windows:  attrib +h filename
  - In Linux, simply add a . to the beginning of the filename
- Can hide data and files with steganography
- Also need to worry about clearing logs
  - In Windows, you need to clear application, system and security logs
  - Don't just delete; key sign that an attack has happened
  - Option is to corrupt a log file - this happens all the time
  - Best option is be selective and delete the entries pertaining to your actions.
- Can also disable auditing ahead of time to prevent logs from being captured

### <u>Rootkits</u>

- Software put in place by attacker to obscure system compromise
- Hides processes and files
- Also allows for future access
- **Examples**
  - Horsepill - Linus kernel rootkit inside initrd
  - Grayfish - Windows rootkit that injects in boot record
  - Firefef - multi-component family of malware
  - Azazel
  - Avatar
  - Necurs
  - ZeroAccess
- **Hypervisor level** - rootkits that modify the boot sequence of a host system to load a VM as the host OS
- **Hardware** - hide malware in devices or firmware
- **Boot loader level** - replace boot loader with one controlled by hacker
- **Application level** - directed to replace valid application files with Trojans
- **Kernel level** - attack boot sectors and kernel level replacing kernel code with back-door code; most dangerous
- **Library level** - use system-level calls to hide themselves
- One way to detect rootkits is to map all the files on a system and then boot a system from a clean CD version and compare the two file systems