# Low Tech: Social Engineering and Physical Security

### <u>Social Engineering</u>

- The art of manipulating a person or group into providing information or a service they would otherwise not have given
- **Phases**
  1. Research (dumpster dive, visit websites, tour the company, etc.)
  2. Select the victim (identify frustrated employee or other target)
  3. Develop a relationship
  4. Exploit the relationship (collect sensitive information)
- **Reasons This Works**
  - Human nature (trusting others)
  - Ignorance of social engineering efforts
  - Fear (of consequences of not providing the information)
  - Greed (promised gain for providing requested information)
  - A sense of moral obligation

### <u>Human-Based Attacks</u>

- **Dumpster Diving** - looking for sensitive information in the trash
  - Shredded papers can sometimes indicate sensitive info
- **Impersonation** - pretending to be someone you're not
  - Can be anything from a help desk person up to an authoritative figure (FBI agent)
  - Posing as a tech support professional can really quickly gain trust with a person
- **Shoulder Surfing** - looking over someone's shoulder to get info
  - Can be done long distance with binoculars, etc.
- **Eavesdropping** - listening in on conversations about sensitive information
- **Tailgating** - attacker has a fake badge and walks in behind someone who has a valid one
- **Piggybacking** - attacker pretends they lost their badge and asks someone to hold the door
- **RFID Identity Theft** (RFID skimming) - stealing an RFID card signature with a specialized device
- **Reverse Social Engineering** - getting someone to call you and give information
  - Often happens with tech support - an email is sent to user stating they need them to call back (due to technical issue) and the user calls back
  - Can also be combined with a DoS attack to cause a problem that the user would need to call about
- Always be pleasant - it gets more information
- **Rebecca** or **Jessica** - targets for social engineering
- **Insider Attack** - an attack from an employee, generally disgruntled
  - Sometimes subclassified (negligent insider, professional insider)

### <u>Computer-Based Attacks</u>

- Can begin with sites like Facebook where information about a person is available
- For instance - if you know Bob is working on a project, an email crafted to him about that project would seem quite normal if you spoof it from a person on his project
- **Phishing** - crafting an email that appears legitimate but contains links to fake websites or to download malicious content
- **Ways to Avoid Phishing**
  - Beware unknown, unexpected or suspicious originators
  - Beware of who the email is addressed to
  - Verify phone numbers
  - Beware bad spelling or grammar
  - Always check links
- **Spear Phishing** - targeting a person or a group with a phishing attack
  - Can be more useful because attack can be targeted
- **Whaling** - going after CEOs or other C-level executives
- **Pharming** - use of malicious code that redirects a user's traffic
- **Spimming** - sending spam over instant message
- **Tools** - Netcraft Toolbar and PhishTank Toolbar
- **Fave Antivirus** - very prevalent attack; pretends to be an anti-virus but is a malicious tool

### <u>Mobile-Based Attacks</u>

- **ZitMo** (ZeuS-in-the-Mobile) - banking malware that was ported to Android
- SMS messages can be sent to request premium services
- **Attacks**
  - Publishing malicious apps
  - Repackaging legitimate apps
  - Fake security applications
  - SMS (**smishing**)

### <u>Physical Security Basics</u>

- **Physical measures** - everything you can touch, taste, smell or get shocked by
  - Includes things like air quality, power concerns, humidity-control systems
- **Technical measures** - smartcards and biometrics
- **Operational measures** - policies and procedures you set up to enforce a security-minded operation
- **Access controls** - physical measures designed to prevent access to controlled areas
  - **Biometrics** - measures taken for authentication that come from the "something you are" concept
    - **False rejection rate** (FRR) - when a biometric rejects a valid user
    - **False acceptance rate** (FAR) - when a biometric accepts an invalid user
    - **Crossover error rate** (CER) - combination of the two; determines how good a system is
- Even though hackers normally don't worry about environmental disasters, this is something to think of from a pen test standpoint (hurricanes, tornadoes, floods, etc.)
