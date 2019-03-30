# Cryptography 101

### <u>Cryptograph Basics</u>

- **Cryptography** - science or study of protecting information whether in transit or at rest
  - Renders the information unusable to anyone who can't decrypt it
  - Takes plain text, applies cryptographic method, turn it into cipher text
- **Crypanalysis** - study and methods used to crack cipher text
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
- **Encryption Algorithms** - methmatical formulas used to encrypt and decrypt data
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
  - **RC** (Rivest Cipher) - RC2 to RC6; block cipher; bariable key length up to 2040 bits; RC6 (lastest version) uses 128 bit blocks and 4 bit working registers; RC5 uses variable block sizes and 2 bit working registers

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
  - **RSA** - achieves strong encryption through the use of two large prime numbers; factoring thse create key sizes up to 4096 bits; modern de facto standard
- Only downside is it's slower than symmetric especially on bulk encryption and processing power

### <u>Hash Algorithms</u>

- **Hash** - one-way mathematical function that produces a fix-length string (hash) based on the arrangement of data bits in the input
- **Algorithms**
  - **MD5** (Message Digest algorithm) - produces 128 bit hash expressed as 32 digit hexadecimal number; has serious flaws; still used for file download verification
  - **SHA-1** - developed by NSA; 160 bit value output
  - **SHA-2** - four separate hash functions; produce outputs of 224, 256, 384 and 512 bits; not widely used
  - **SHA-3** - uses sponge construction
  - **RIPEMD-#** - works through 80 stages, executing 5 blcosk 16 times each; uses modulo 32 addition
- **Collision** - occurs when two or more files create the same output
  - Can happen and can be used an attack; rare, though
- **DHUK Attack** (Don't Use Hard-Coded Keys) - allows attackers to access keys in certain VPN implementations; affects devices using ANSI X9.31 with a hard-coded seed key
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

- **Steganography** - practice of concealing a message inside another medium so that only the sender and recipient know of it's existence
- **Ways to Identify**
  - Text - character positions are key - blank spaces, text patterns
  - Image - file larger in size; some may have color palete faults
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
