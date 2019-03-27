# Sniffing and Evasion

### <u>Basic Knowledge</u>

 - Sniffing is capturing packets as they pass on the wire to review for interesting information
 - **MAC**  (Media Access Control) - physical or burned-in address - assigned to NIC for communications at the Data Link layer
    - 48 bits long
    - Displayed as 12 hex characters separated by colons
 - NICs normally only process signals meant for it
 - **Promiscuous mode** - NIC must be in this setting to look at all frames passing on the wire
 - **CSMA/CD** - Carrier Sense Multiple Access/Collision Detection - used over Ethernet to decide who can talk
 - **Collision Domains**
    - Traffic from your NIC (regardless of mode) can only be seen within the same collision domain
    - Hubs by default have one collision domain
    - Switches have a collision domain for each port

### <u>Protocols Susceptible</u>

- SMTP is sent in plain text and is viewable over the wire.  SMTP v3 limits the information you can get, but you can still see it.
- FTP sends user ID and password in clear text
- TFTP passes everything in clear text
- IMAP, POP3, NNTP and HTTP all  send over clear text data
- TCP shows sequence numbers (usable in session hijacking)
- TCP and UCP show open ports
- IP shows source and destination addresses

### <u>ARP</u>

