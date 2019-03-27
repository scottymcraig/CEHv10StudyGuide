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
- **Executing Applications** - putting back doors into the  system so that you can maintain access
- **Hiding Files** - making sure the files you leave behind are not discoverable
- **Covering Tracks** - cleaning up everything else (log files, etc.)
  - **clearev** - meterpreter shell command to clear log  files
  - Clear MRU list in Windows
  - In Linux, append a dot in front of a file to hide it

