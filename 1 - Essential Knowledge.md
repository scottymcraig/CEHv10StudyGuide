# Essential Knowledge

### <u>The OSI Reference Model</u>

| Layer | Description  | Technologies    | Data Unit |
| ----- | ------------ | --------------- | --------- |
| 1     | Physical     | USB, Bluetooth  | Bit       |
| 2     | Data Link    | ARP, PPP        | Frame     |
| 3     | Network      | IP              | Packet    |
| 4     | Transport    | TCP             | Segment   |
| 5     | Session      | X255, SCP       | Data      |
| 6     | Presentation | AFP, MIME       | Data      |
| 7     | Application  | FTP, HTTP, SMTP | Data      |

### <u>TCP/IP Model</u>

| Layer | Description    | OSI Layer Equivalent |
| ----- | -------------- | -------------------- |
| 1     | Network Access | 1, 2                 |
| 2     | Internet       | 3                    |
| 3     | Transport      | 4                    |
| 4     | Application    | 5-7                  |

### <u>TCP Handshake</u>

SYN -> SYN-ACK -> ACK

### <u>ARP</u>

- Resolves IP address to physical address

### <u>Network Security Zones</u>

- **Internet** - uncontrollable
- **Internet** DMZ - controlled buffer network
- **Production Network Zone** - very restricted; controls direct access from uncontrolled zones; has no users
- **Intranet Zone** - controlled; has little to no heavy restrictions
- **Management Network Zone** - might find VLANs and IPSEC; highly secured; strict policies

### <u>Vulnerabilities</u>

- **Common Vulnerability Scoring System** (CVSS) - places numerical score based on severity
- **National Vulnerability Database** (NVD) - US government repository of vulnerabilities

### <u>Vulnerability Categories</u>

- **Misconfiguration** - improperly configuring a service or application
- **Default installation** - failure to change settings in an application that come by default
- **Buffer overflow** - code execution flaw
- **Missing patches** -  systems that have not been patched
- **Design flaws** - flaws inherent to system design such as encryption and data validation
- **Operating System Flaws** - flaws specific to each OS
- **Default passwords** - leaving default passwords that come with system/application

### <u>Vulnerability Management Tools</u>

- Nessus
- Qualys
- GFI Languard
- Nikto
- OpenVAS
- Retina CS

### <u>Terms to Know</u>

- **Hack value** - perceived value or worth of a target as seen by the attacker
- **Zero-day attack** - attack that occurs before a vendor knows or is able to patch a flaw
- **Doxing** - searching for and publishing information about an individual usually with a malicious intent
- **Enterprise Information Security Architecture** (EISA) - process that determines how systems work within an organization
- **Incident management** - deals with specific incidents to mitigate the attack

### <u>Threat Modeling</u>

- Identify security objectives
- Application Overview
- Decompose application
- Identify threats
- Identify vulnerabilities

### <u>Risk Management</u>

- Risk identification
- Risk assessment
- Risk treatment
- Risk tracking
- Risk review

  *Uses risk analysis matrix to determine threat level

### <u>Types of  Security Controls</u>

| Description    | Examples                                      |
| -------------- | --------------------------------------------- |
| Physical       | Guards, lights, cameras                       |
| Technical      | Encryption, smart cards, access control lists |
| Administrative | Training awareness, policies                  |

| Description  | Examples                    |
| ------------ | --------------------------- |
| Preventative | authentication, alarm bells |
| Detective    | audits, backups             |
| Corrective   | restore operations          |

### <u>Business Analysis</u>

- Business Impact Analysis (BIA)

  - Maximum Tolerable Downtime (MTD)

- Business Continuity Plan (BCP)

  - Disaster Recovery Plan (DRP)

- Annualized Loss Expectancy (ALE)

  - Annual Rate of Occurrence (ARO)

  - Single Loss Expectancy (SLE)
    $$
    ALE = SLE * ARO
    $$

**User Behavior Analysis** (UBA) - tracking users and extrapolating data in light of malicious activity

### <u>CIA Triad</u>

- **Confidentiality** - passwords, encryption
- **Integrity** - hashing, digital signatures
- **Availability** - anti-dos solutions

**Bit flipping** is an example of an <u>integrity</u> attack.  The outcome is not to gain information - it is to obscure the data from the actual user.

Confidentiality != authentication - MAC address spoofing is an authentication attack

### <u>Common Criterial for Information Technology Security Evaluation</u>

- Routinely called "Common Criteria" (CC)
- **Evaluation Assurance Level** (EAL) - goes from level 1 - 7
- **Target of Evaluation** - the system that is being tested
- **Security Target** (ST) - document describing the TOE and security requirements
- **Protection Profile** (PP) - security requirements that are specific to the type of device being tested

### <u>Access Control Types</u>

- **Mandatory** (MAC) - access is set by an administrator
- **Discretionary** (DAC) - allows users to give access to resources that they own and control

### <u>Security Policies</u>

