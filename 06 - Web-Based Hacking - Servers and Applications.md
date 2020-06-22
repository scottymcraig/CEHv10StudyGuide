# Web-Based Hacking - Servers and Applications

### <u>Web Organizations</u>

- **Internet Engineering Task Force** (IETF) - creates engineering documents to help make the Internet work better
- **World Wide Web Consortium** (W3C) - a standards-developing community
- **Open Web Application Security Project** (OWASP) - organization focused on improving the security of software

### <u>OWASP Web Top 10</u>

- **A1 - Injection Flaws** - SQL, OS and LDAP injection
- **A2 - Broken Authentication and Session Management** - functions related to authentication and session management that aren't implemented correctly
- **A3 - Sensitive Data Exposure** - not properly protecting sensitive data (SSN, CC  numbers, etc.)
- **A4 - XML External  Entities (XXE)** - exploiting XML  processors by uploading hostile content in an XML document
- **A5 - Broken Access Control** - having improper controls on areas that should be protected
- **A6 - Security Misconfiguration** - across all parts of the server and application
- **A7 - Cross-Site Scripting (XSS)** - taking untrusted data and sending it without input validation
- **A8 - Insecure Deserialization** - improperly de-serializing data
- **A9 - Using Components with Known Vulnerabilities** - libraries and frameworks that have known security holes
- **A10 - Insufficient Logging and Monitoring** - not having enough logging to detect attacks

**WebGoat** - project maintained by OWASP which is an insecure web application meant to be tested

### <u>Web Server Attack Methodology</u>

- **Information Gathering** - Internet searches, whois, reviewing robots.txt
- **Web  Server Footprinting** - banner grabbing
  - **Tools**
    - Netcraft
    - HTTPRecon
    - ID Serve
    - HTTPrint
    - nmap
      - nmap --script http-trace -p80 localhost (detects vulnerable TRACE method)
      - nmap --script http-google-email <host> (lists email addresses)
      - nmap --script hostmap-* <host> (discovers virtual hosts on the IP address you are trying to footprint; * is replaced by online db such as  IP2Hosts)
      - nmap --script http-enum -p80 <host> (enumerates common web  apps)
      - nmap -p80 --script http-robots.txt <host> (grabs the robots.txt file)
- **Website Mirroring** - brings the site to your own machine to examine structure, etc.
  - **Tools**
    - Wget
    - BlackWidow
    - HTTrack
    - WebCopier Pro
    - Web Ripper
    - SurfOffline
- **Vulnerability Scanning** - scans web server for vulnerabilities
  - **Tools**
    - Nessus
    - Nikto - specifically suited for web servers; still very noisy like Nessus
- **Session Hijacking**
- **Web Server Password Cracking**

### <u>Web Server Architecture</u>

- **Most Popular Servers** - Apache, IIS and Nginx
- Apache runs configurations as a part of a module within special files (http.conf, etc.)
- IIS runs all applications in the context of LOCAL_SYSTEM
- IIS 5 had a ton of bugs - easy to get into
- **N-Tier Architecture** - distributes processes across multiple servers; normally as three-tier: Presentation (web), logic (application) and data (database)
- **Error Reporting** - should not be showing errors in production; easy to glean information
- **HTML** - markup language used to display web pages
- **HTTP Request Methods**
  - **GET** - retrieves whatever information is in the URL; sending data is done in URL
  - **HEAD** - identical to get except for no body return
  - **POST** - sends data via body - data not shown in URL or in history
  - **PUT** - requests data be stored at the URL
  - **DELETE** - requests origin server delete resource
  - **TRACE** - requests application layer loopback of message
  - **CONNECT** - reserved for use with proxy
  - Both POST and GET can be manipulated by a web proxy
- **HTTP Error Messages**
  - **1xx: Informational** - request received, continuing
  - **2xx: Success** - action received, understood and accepted
  - **3xx: Redirection** - further action must be taken
  - **4xx: Client Error** - request contains bad syntax or cannot be fulfilled
  - **5xx: Server Error** - server failed to fulfill an apparently valid request

### <u>Web Server Attacks</u>

- **DNS Amplification** - uses recursive DNS to DoS a target; amplifies DNS answers to target until it can't do anything
- **Directory Transversal** (../ or dot-dot-slash) - requests file that should not be accessible from web server
  - Example: http://www.example.com/../../../../etc/password
  - Can use Unicode to possibly evade IDS - %2e for dot and %sf for slash
- **Parameter Tampering** (URL Tampering) - manipulating parameters within URL to achieve escalation or other changes
- **Hidden Field Tampering** - modifying hidden form fields producing unintended results
- **Web Cache Poisoning** - replacing the cache on a box with a malicious version of it
- **WFETCH** - Microsoft tool that allows you to craft HTTP requests to see response data
- **Misconfiguration Attack** - same as before - improper configuration of a web server
- **Password Attack** - attempting to crack passwords related to web resources
- **Connection String Parameter Pollution** - injection attack that uses semicolons to take advantage of databases that use this separation method
- **Web Defacement** - simply modifying a web page to say something else
- **Tools**
  - **Brutus** - brute force web passwords of HTTP
  - **Hydra** - network login cracker
  - **Metasploit**
    - Basic working is Libraries use Interfaces and Modules to send attacks to services
    - **Exploits** hold the actual exploit
    - **Payload** contains the arbitrary code if exploit is successful
    - **Auxiliary** used for one-off actions (like a scan)
    - **NOPS** used for buffer-overflow type operations
- **Shellshock** - causes Bash to unintentionally execute commands when commands are concatenated on the end of function definitions

### <u>Web Application Attacks</u>

- Most often hacked before of inherent weaknesses built into the program
- First step is to identify entry points (POST data, URL parameters, cookies, headers, etc.)
- **Tools for Identifying Entry Points**
  - WebScarab
  - HTTPPrint
  - BurpSuite
- **Web 2.0** - dynamic applications; have a larger attack surface due to simultaneous communication
- **File Injection** - attacker injects a pointer in a web form to an exploit hosted elsewhere
- **Command Injection** - attacker gains shell access using Java or similar
- **LDAP Injection** - exploits applications that construct LDAP statements
  - Format for LDAP injection includes )(&)
- **SOAP Injection** - inject query strings in order to bypass authentication
  - SOAP uses XML to format information
  - Messages are "one way" in nature
- **Buffer Overflow** (Smashing the stack) - attempts to write data into application's buffer area to overwrite adjacent memory, execute code or crash a system
  - Inputs more data than the buffer is allowed
  - Includes stack, heap, NOP sleds and more
  - **Canaries** - systems can monitor these - if they are changed, they indicate a buffer overflow has occurred; placed between buffer and control data
- **XSS** (Cross-site scripting) - inputting JavaScript into a web form that alters what the page does
  - Can also be passed via URL (http://IPADDRESS/";!--"<XSS>=&{()}
  - Can be malicious by accessing cookies and sending them to a remote host
  - Can be mitigated by setting **HttpOnly** flag for cookies
  - **Stored XSS** (Persistent or Type-I) - stores the XSS in a forum or like for multiple people to access
- **Cross-Site Request Forgery** (CSRF) - forces an end user to execute unwanted actions on an app they're already authenticated on
  - Inherits  identity and privileges of victim to perform an undesired function on victim's behalf
  - Captures the session and sends a request based off the logged in user's credentials
  - Can be mitigated by sending **random challenge tokens**
- **Session Fixation** - attacker logs into a legitimate site and pulls a session ID; sends link with session ID to victim.  Once victim logs in, attacker can now log in and run with user's credentials
- **Cookies** - small text-based files stored that contains information like preferences, session details or shopping cart contents
  - Can be manipulated to change functionality (e.g. changing a cooking that says "ADMIN=no" to "yes")
  - Sometimes, but rarely, can also contain passwords
- **SQL Injection** - injecting SQL commands into input fields to produce output
  - Data Handling - Definition (DDL), manipulation (DML) and control (DCL)
  - Example - input "' OR 1 = 1 --" into a login field - basically tells the server if 1 = 1 (always true) to allow the login.
  - Double dash (--) tells the server to ignore the rest of the query (in this example, the password check)
  - Basic test to see if SQL injection is possible is just inserting a single quote (')
  - **Fuzzing** - inputting random data into a target to see what will happen
  - **Tautology** - using always true statements to test SQL (e.g. 1=1)
  - **In-band SQL injection** - uses same communication channel to perform attack
    - Usually is when data pulled can fit into data exported (where data goes to a web table)
    - Best for using UNION queries
  - **Out-of-band SQL injection** - uses different communication channels (e.g. export results to file on web server)
  - **Blind/inferential** - error messages and screen returns don't occur; usually have to guess whether command work or use timing to know
  - **Tools**
    - Sqlmap
    - sqlninja
    - Havij
    - SQLBrute
    - Pangolin
    - SQLExec
    - Absinthe
    - BobCat
- **HTTP Response Splitting** - adds header response data to an input field so server splits the response
  - Can be used to redirect a user to a malicious site
  - Is not an attack in and of itself - must be combined with another attack
- **Countermeasures** - input scrubbing for injection, SQL parameterization for SQL injection, keeping patched servers, turning off unnecessary services, ports and protocols
