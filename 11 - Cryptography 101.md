# Cryptography 101

### <u>Cryptograph Basics</u>

- **Cryptography** - science or study of protecting information whether in transit or at rest
  - Renders the information unusable to anyone who can't decrypt it
  - Takes plain text, applies cryptographic method, turn it into cipher text
- **Cryptanalysis** - study and methods used to crack cipher text
- **Linear Cryptanalysis** - works best on block ciphers
- **Differential Cryptanalysis** - applies to symmetric key algorithms
  - Compares differences in the inputs to how each one affects the outcome
- **Integral cryptanalysis** - input vs output comparison same as differential; however, runs multiple computations of the same block size input
- Plain text doesn't necessarily mean ASCII format - it simply means unencrypted data
- **Nonrepudiation** - means by which a recipient can ensure the identity of the sender and neither party can deny sending

### <u>Encryption Algorithms and Techniques</u>

- **Algorithm** - step-by-step method of solving a problem
- **Two General Forms of Cryptography**
  - **Substitution** - bits are replaced by other bits
  - **Transposition** - doesn't replace;  simply changes order
- **Encryption Algorithms** - mathematical formulas used to encrypt and decrypt data
- **Steam Cipher** - readable bits are encrypted one at a time in a continuous stream
  - Usually done by an XOR operation
  - Work at a high rate of speed
- **Block Cipher** - data bits are split up into blocks and fed into the cipher
  - Each block of data (usually 64 bits) encrypted with key and algorithm
  - Are simpler and slower than stream ciphers
- **XOR** - exclusive or; if inputs are the same (0,0 or 1,1), function returns 0; if inputs are not the same (0,1 or 1,0), function returns 1
- Key chosen for cipher must have a length larger than the data; if not, it is vulnerable to frequency attacks

### <u>Symmetric Encryption</u>

- **Symmetric Encryption** - known as single key or shared key
  - One key is used to encrypt and decrypt the data
  - Problems include key distribution and management
  - Suitable for large amounts of data
  - Harder for groups of people because more keys are needed as group increases
  - Does nothing for nonrepudiation; only performs confidentiality
- **Algorithms**
  - **DES** - block cipher; 56 bit key; quickly outdated and now considered not very secure
  - **3DES** - block cipher; 168 bit key; more effective than DES but much slower
  - **AES** (Advanced Encryption Standard) - block cipher; 128, 192 or 256 bit key; replaces DES; much faster than DES and 3DES
  - **IDEA** (International Data Encryption Algorithm) - block cipher; 128 bit key; originally used in PGP 2.0
  - **Twofish** - block cipher; up to 256 bit key
  - **Blowfish** - fast block cipher; replaced by AES; 64 bit block size; 32 to 448 bit key; considered public domain
  - **RC** (Rivest Cipher) - RC2 to RC6; block cipher; comparable key length up to 2040 bits; RC6 (latest version) uses 128 bit blocks and 4 bit working registers; RC5 uses variable block sizes and 2 bit working registers. RC4 is a stream cipher

### <u>Asymmetric Encryption</u>

- Uses two types of keys for encryption and decryption
- **Public Key** - generally used for encryption; can be sent to anyone
- **Private Key** - kept secret; used for decryption
- Comes down to what one key encrypts, the other decrypts
- The private key is used to digitally sign a message
- **Algorithms**
  - **Diffie-Hellman** - developed as a key exchange protocol; used in SSL and IPSec; if digital signatures are waived, vulnerable to MITM attacks
  - **Elliptic Curve Cryptosystem** (ECC) - uses points on elliptical curve along with logarithmic problems; uses less processing power; good for mobile devices
  - **El Gamal** - not based on prime number factoring; uses solving of discrete logarithm problems
  - **RSA** - achieves strong encryption through the use of two large prime numbers; factoring these create key sizes up to 4096 bits; modern de facto standard
- Only downside is it's slower than symmetric especially on bulk encryption and processing power

### <u>Hash Algorithms</u>

- **Hash** - one-way mathematical function that produces a fix-length string (hash) based on the arrangement of data bits in the input
- **Algorithms**
  - **MD5** (Message Digest algorithm) - produces 128 bit hash expressed as 32 digit hexadecimal number; has serious flaws; still used for file download verification
  - **SHA-1** - developed by NSA; 160 bit value output
  - **SHA-2** - four separate hash functions; produce outputs of 224, 256, 384 and 512 bits; not widely used
  - **SHA-3** - uses sponge construction
  - **RIPEMD-#** - works through 80 stages, executing 5 blocks 16 times each; uses modulo 32 addition
- **Collision** - occurs when two or more files create the same output
  - Can happen and can be used an attack; rare, though
- **DUHK Attack** (Don't Use Hard-Coded Keys) - allows attackers to access keys in certain VPN implementations; affects devices using ANSI X9.31 with a hard-coded seed key
- **Rainbow Tables** - contain precomputed hashes to try and find out passwords
- **Salt** - used with a hash to obscure the hash; collection of random bits
- **Things to Remember**
  - Hashes are used for integrity
  - Hashes are one-way functions
- **Tools**
  - HashCalc
  - MD5 Calculator
  - HashMyFiles

### <u>Steganography</u>

- **Steganography** - practice of concealing a message inside another medium so that only the sender and recipient know of its existence
- **Ways to Identify**
  - Text - character positions are key - blank spaces, text patterns
  - Image - file larger in size; some may have color palette faults
  - Audio & Video - require statistical analysis
- **Methods**
  - Least significant bit insertion - changes least meaningful bit
  - Masking and filtering (grayscale images) - like watermarking
  - Algorithmic transformation - hides in mathematical functions used in image compression
- **Tools**
  - QuickStego
  - gifshuffle
  - SNOW
  - Steganography Studio
  - OpenStego

### <u>PKI System</u>

- **Public Key Infrastructure** (PKI) - structure designed to verify and authenticate the identity of individuals
- **Registration Authority** - verifies user identity
- **Certificate Authority** - third party to the organization; creates and issues digital certificates
- **Certificate Revocation List** (CRL) - used to track which certificates have problems and which have been revoked
- **Validation Authority** - used to validate certificates via Online Certificate Status Protocol (OCSP)
- **Trust Model** - how entities within an enterprise deal with keys, signatures and certificates
- **Cross-Certification** - allows a CA to trust another CS in a completely different PKI; allows both CAs to validate certificates from either side
- **Single-authority system** - CA at the top
- **Hierarchical trust system** - CA at the top (root CA); makes use of one or more RAs (subordinate CAs) underneath it to issue and manage certificates

### <u>Digital Certificates</u>

- **Certificate** - electronic file that is used to verify a user's identity; provides nonrepudiation
- **X.509** - standard used for digital certificates
- **Contents of a Digital Certificate**
  - **Version** - identifies certificate format
  - **Serial Number** - used to uniquely identify certificate
  - **Subject** - who or what is being identified
  - **Algorithm ID** (Signature Algorithm) - shows the algorithm that was used to create the certificate
  - **Issuer** - shows the entity that verifies authenticity
  - **Valid From and Valid To** - dates certificate is good for
  - **Key Usage** - what purpose the certificate serves
  - **Subject's Public Key** - copy of the subject's public key
  - **Optional Fields** - Issuer Unique Identifier, Subject Alternative Name, and Extensions
- Some root CAs are automatically added to OSes that they already trust; normally are reputable companies
- **Self-Signed Certificates** - certificates that are not signed by a CA; generally not used for public; used for development purposes
  - Signed by the same entity it certifies

### <u>Digital Signatures</u>

- When signing a message, you sign it with your **private** key and the recipient decrypts the hash with your **public** key
- **Digital Signature Algorithm** (DSA) - used in generation and verification of digital signatures per FIPS 186-2

### <u>Full Disk Encryption</u>

- **Data at Rest** (DAR) - data that is in a stored state and not currently accessible
  - Usually protected by **full disk encryption** (FDE) with pre-boot authentication
  - Example of FDE is Microsoft BitLocker and McAfee Endpoint Encryption
  - FDE also gives protection against boot-n-root

### <u>Encrypted Communication</u>

- **Often-Used Encrypted Communication Methods**
  - **Secure Shell** (SSH) - secured version of telnet; uses port 22; relies on public key cryptography; SSH2 is successor and includes SFTP
  - **Secure Sockets Layer** (SSL) - encrypts data at transport layer and above; uses RSA encryption and digital certificates; has a six-step process; largely has been replaced by TLS
  - **Transport Layer Security** (TLS) - uses RSA 1024 and 2048 bits; successor to SSL; allows both client and server to authenticate to each other; TLS Record Protocol provides secured communication channel
  - **Internet Protocol Security** (IPSEC) - network layer tunneling protocol; used in tunnel and transport modes; ESP encrypts each packet
  - **PGP** - Pretty Good Privacy; used for signing, compress and encryption of emails, files and directories; known as hybrid cryptosystem - features conventional and public key cryptography
  - **S/MIME** - standard for public key encryption and signing of MIME data; only difference between this and PGP is PGP can encrypt files and drives unlike S/MIME
- **Heartbleed** - attack on OpenSSL heartbeat which verifies data was received correctly
  - Vulnerability is that a single byte of data gets 64kb from the server
  - This data is random; could include usernames, passwords, private keys, cookies; very easy to pull off
  - nmap -d --script ssl-heartbleed --script-args vulns.showall -sV [host]
  - Vulnerable versions include Open SSL 1.0.1 and 1.0.1f
  - CVE-2014-0160
- **FREAK** (Factoring Attack on RSA-EXPORT Keys) - man-in-the-middle attack that forces a downgrade of RSA key to a weaker length
- **POODLE** (Paddling Oracle On Downgraded Legacy Encryption) - downgrade attack that used the vulnerability that TLS downgrades to SSL if a connection cannot be made
  - SSl 3 uses RC4, which is easy to crack
  - CVE-2014-3566
  - Also called PoodleBleed
- **DROWN** (Decrypting RSA with Obsolete and Weakened eNcyption) - affects SSL and TLS services
  - Allows attackers to break the encryption and steal sensitive data
  - Uses flaws in SSL v2
  - Not only web servers; can be IMAP and POP servers as well

### <u>Cryptography Attacks</u>

- **Known plain-text attack** - has both plain text and cipher-text; plain-text scanned for repeatable sequences which is compared to cipher text
- **Chosen plain-text attack** - attacker encrypts multiple plain-text copies in order to gain the key
- **Adaptive chosen plain-text attack** - attacker makes a series of interactive queries choosing subsequent plaintexts based on the information from the previous encryptions; idea is to glean more and more information about the full target cipher text and key
- **Cipher-text-only attack** - gains copies of several encrypted messages with the same algorithm; statistical analysis is then used to reveal eventually repeating code
- **Replay attack**
  - Usually performed within context of MITM attack
  - Hacker repeats a portion of cryptographic exchange in hopes of fooling the system to setup a communications channel
  - Doesn't know the actual data - just has to get timing right
- **Chosen Cipher Attack**
  - Chooses a particular cipher-text message
  - Attempts to discern the key through comparative analysis
  - RSA is particularly vulnerable to this
- **Side-Channel Attack**
  - Monitors environmental factors such as power consumption, timing and delay
- **Tools**
  - Carnivore and Magic Lantern - used by law enforcement for cracking codes
  - L0phtcrack - used mainly against Windows SAM files
  - John the Ripper - UNIX/Linux tool for the same purpose
  - PGPcrack - designed to go after PGP-encrypted systems
  - CrypTool
  - Cryptobench
  - Jipher
- Keys should still change on a regular basis even though they may be "unhackable"
- Per U.S. government, an algorithm using at least a 256-bit key cannot be cracked
