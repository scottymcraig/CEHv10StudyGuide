# Security in Cloud Computing

### <u>Cloud Computing Basics</u>

- **Three Types**
  - **Infrastructure as a Service** (IaaS)
    - Provides virtualized computing resources
    - Third party hosts the servers with hypervisor running the VMs as guests
    - Subscribers usually pay on a per-use basis
  - **Platform as a Service** (Paas)
    - Geared towards software development
    - Hardware and software hosted by provider
    - Provides ability to develop without having to worry about hardware or software
  - **Software as a Service** (SaaS)
    - Provider supplies on-demand applications to subscribers
    - Offloads the need for patch management, compatability and version control
- **Deployment Models**
  - **Public Cloud** - services provided over a network that is open for public to use
  - **Private Cloud** - cloud solely for use by one tenant; usually done in larger organizations
  - **Community Cloud** - cloud shared by several organizations, but not open to public
  - **Hybrid Cloud** - a composition of two or more cloud deployment models
- **NIST Cloud Architecture**
  - **Cloud Carrier** - organization with responsibility of transferring data; akin to power distributor for electric grid
  - **Cloud Consumer** - aquires and uses cloud products and services
  - **Cloud Provider** - purveyor of products and services
  - **Cloud Broker** - manages use, performance and delivery of services as well as relationships betwen providers and subscribers
  - **Cloud Auditor** - independent assor of cloud service an security controls
- **FedRAMP** - regulatory effort regarding cloud computing
- **PCI DSS** - deals with debit and credit cards, but also has a cloud SIG

### <u>Cloud Security</u>

- Problem with cloud security is what you are allowed to test and what should you test
- Another concern is with a hypervisor, if the hypervisor is compromised, all hosts on that hypervisor are as well
- **Trusted Computing Model** - attempts to resolve computer security problems through hardware enhancements
  - **Roots of Trust** (RoT) - set of functions within TCM that are always trusted by the OS
- **Tools**
  - **CloudInspect** - pen-testing application for AWS EC2 users
  - **CloudPassage Halo** - instant visibility and continuous protection for servers in any cloud
  - **Dell Cloud Manager**
  - **Qualys Cloud Suite**
  - **Trend Micro's Instant-On Cloud Security**
  - **Panda Cloud Office Protection**

### <u>Threats and Attacks</u>

- **Data Breach or Loss** - biggest threat; includes malicious theft, erasure or modification
- **Shadow IT** - IT systems or solutions that are developed to handle an issue but aren't taken through proper approval chain
- **Abuse of Cloud Resources** -  another high threat (usually applies to Iaas and PaaS)
- **Insecure Interfaces and APIs** - cloud services can't function without them, but need to make sure they are secure
- **Service Oriented Architecture** - API that makes it easier for application components to cooperate and exchange information
- Insufficient due diligence - moving an application without knowing the security differences
- Shared technology issues - multitenant environments that don't provide proper isolation
- Unknown risk profiles - subscribers simply don't know what security provisions are made int he background
- Others include malicious insiders, inadequate design and DDoS
- **Wrapping Attack** - SOAP message intercepted and data in envelope is changed and sent/replayed
- **Session riding** - CSRF under a different name; deals with cloud services instead of traditional data centers
- **Side Channel Attack** - using an existing VM on the same physical host to attack another
  - This is more broadly defined as using something other than the direct interface to attack a system
