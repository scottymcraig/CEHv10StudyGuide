# The Pen Test:  Putting It All Together

- **Security Assessment** - test performed in order to assess the level of security on a network or system
- **Security Audit** - policy and procedure focused; tests whether organization is following specific standards and policies
- **Vulnerability Assessment** - scans and tests for vulnerabilities but does not intentionally exploit them
- **Penetration Test** - looks for vulnerabilities and actively seeks to exploit them
- Need to make sure you have a great contract in place to protect you from liability
- **Types of Pen Tests**
  - **External assessment** - analyzes publicly available information; conducts network scanning, enumeration and testing from the network perimeter
  - **Internal Assessment** - performed from within the organization, from various network access points
- **Red Team** - pen test team that is doing the attacking
- **Blue Team** - pen test team that is doing the defending
- **Purple Team** - pen test team that is doing both attacking and defending
- **Automated Testing Tools**
  - **Codenomicon** - utilizes fuzz testing that learns the tested system automatically; allows for pen testers to enter new domains such as VoIP assessment, etc.
  - **Core Impact Pro** - best known, all-inclusive automated testing framework; tests everything from web applications and individual systems to network devices and wireless
  - **Metasploit** - framework for developing and executing code against a remote target machine
  - **CANVAS** - hundreds of exploits, automated exploitation system and extensive exploit development framework
- **Phases of Pen Test**
  - **Pre-Attack Phase** - reconnaissance and data-gathering
  - **Attack Phase** - attempts to penetrate the network and execute attacks
  - **Post-Attack Phase** - Cleanup to return a system to the pre-attack condition and deliver reports

### <u>Security Assessment Deliverables</u>

- Usually begins with a brief to management
  - Provides information about your team and the overview of the original agreement
  - Explain what tests were done and the results of them
- **Comprehensive Report Parts**
  - Executive summary of the organization's security posture
  - Names of all participants and dates of tests
  - List of all findings, presented in order of risk
  - Analysis of each finding and recommended mitigation steps
  - Log files and other evidence (screenshots, etc.)
- Example reports and methodology can be found in the **Open Source Testing Methodology Manual** (OSSTMM)

### <u>Terminology</u>

- **Types of Insiders**
  - **Pure Insider** - employee with all rights and access associated with being an employee
    - **Elevated Pure Insider** - employee who has admin privileges
  - **Insider Associate** - someone with limited authorized access such as a contractor, guard or cleaning service person
  - **Insider Affiliate** - spouse, friend or client of an employee who uses the employee's credentials to gain access
  - **Outside Affiliate** - someone outside the organization who uses an open access channel to gain access to an organization's resources
