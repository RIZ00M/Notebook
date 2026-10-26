#Week1
# Week 1 Concepts
### CIA Key Security Concepts

- **Confidentiality** - Protects data from unauthorised disclosure
- **Integrity** - Ensure data is accurate and unmodified
- **Availability** - Systems and data are accessible when needed

- **Authenticity** - Verifies the identity of users and data sources
- **Accountability** - Actions can be traced to a responsible entity
---
Including hardware, software, firmware and information being stored, processed and communicated.

| Resource                         | Availability                                                                                 | Confidentiality                                                                                     | Integrity                                                                                         |
| -------------------------------- | -------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Hardware                         | Equipment is stolen or disabled, thus denying service.                                       | An unencrypted CD-ROM or DVD is stolen.                                                             | —                                                                                                 |
| Software                         | Programs are deleted, denying access to users.                                               | An unauthorized copy of software is made.                                                           | A working program is modified to cause it to fail during execution or perform an unintended task. |
| Data                             | Files are deleted, denying access to users.                                                  | An unauthorized read of data is performed. An analysis of statistical data reveals underlying data. | Existing files are modified or new files are fabricated.                                          |
| Communication Lines and Networks | Messages are destroyed or deleted. Communication lines or networks are rendered unavailable. | Messages are read. The traffic pattern of messages is observed.                                     | Messages are modified, delayed, reordered, or duplicated. False messages are fabricated.          |
## Levels of Impact

**Low Impact**
A limited adverse effect on operations, assets or individuals. Systems may experience degraded performance but core functions remain. Examples: **minor data exposure, brief service disruption**

**Moderate Impact**
A serious adverse effect. Significant degradation of capabilities, financial loss or harm to individuals is likely. Examples: **breach of a departmental database, extended system downtime.**

**High Impact**
A severe or catastrophic effect. Critical functions are lost, major financial damage occurs, or individual safety is jeopardised. Examples: **National infrastructure breach, large scale exfiltration.**

## Computer Security Problems and Assets

| No. | Challenge                          | Implication                                       | Example                                                                                |
| --- | ---------------------------------- | ------------------------------------------------- | -------------------------------------------------------------------------------------- |
| 1   | Security is not simple             | Requires layered, detailed strategies             | Passwords alone are not enough; firewalls, encryption, and monitoring are also needed. |
| 2   | Must consider potential attacks    | Designs must anticipate threats                   | Strong encryption is useless if passwords are weak.                                    |
| 3   | Procedures may be counterintuitive | Security feels inconvenient but necessary         | Multi-factor authentication adds steps but helps prevent breaches.                     |
| 4   | Placement matters                  | Wrong placement weakens defenses                  | A firewall in the wrong network segment offers little protection.                      |
| 5   | Involves more than algorithms      | Managing secret information is critical           | Encryption is useless if keys are leaked.                                              |
| 6   | Attackers need only one weakness   | Defense must cover all gaps                       | One unpatched vulnerability can compromise a system.                                   |
| 7   | Often an afterthought              | Systems are weaker if security is bolted on later | Adding security after application development can create loopholes.                    |
| 8   | Requires constant monitoring       | Must adapt to evolving threats                    | Log monitoring, intrusion detection, and patch updates.                                |
| 9   | Undervalued until failure          | Organizations act only after breaches             | Companies invest in security only after a cyberattack.                                 |
| 10  | Seen as a burden                   | Strong security reduces usability                 | Users resist long passwords or frequent logins.                                        |

|Component|Description|Threats|
|---|---|---|
|Hardware|Physical components including CPUs, servers, routers, and storage devices.|Theft, vandalism, and environmental damage.|
|Software|Operating systems, applications, and utilities.|Malware infection, unauthorised modification, and software vulnerabilities.|
|Data|Files, databases, and communications in transit or at rest.|Exfiltration, corruption, and destruction.|
|Networks|Communication links and network infrastructure.|Eavesdropping, packet tampering, denial-of-service attacks, and unauthorised access.|

|Resource|Confidentiality|Integrity|Availability|Authenticity|Accountability|
|---|---|---|---|---|---|
|Hardware|Restrict physical access|Ensure devices aren't tampered with|Maintain redundant systems and backups|Verify trusted devices|Track device use and maintenance logs|
|Software|Limit unauthorised use|Prevent code modification|Patch vulnerabilities to maintain uptime|Verify legitimate software sources|Log software installations and updates|
|Data|Encrypt sensitive data|Prevent unauthorised changes|Backup and recovery processes|Verify data origin using digital signatures|Track who accessed or modified data|
|Networks|Secure transmissions (VPN, TLS)|Detect packet tampering|Keep network services online|Authenticate users and devices|Monitor network traffic and log access|
## Vulnerabilities, Threats and Attacks

|Category|Type|Description|Example|
|---|---|---|---|
|Vulnerabilities|Corrupted|Loss of integrity; data or system state is altered.|Data is modified without authorisation.|
|Vulnerabilities|Leaky|Loss of confidentiality; information is disclosed without authorisation.|Sensitive information is exposed.|
|Vulnerabilities|Unavailable or slow|Loss of availability; services cannot be accessed or respond too slowly.|A website becomes unavailable.|
|Threats|General|Capable of exploiting one or more vulnerabilities and represent potential security harm to an asset.|An attacker targets an unpatched system.|
|Attacks|Passive|Attempt to learn or use information without affecting system resources.|Eavesdropping or traffic analysis.|
|Attacks|Active|Attempt to alter system resources or affect their operation.|Replay, masquerade, or denial-of-service attacks.|
|Attacks|Insider|Initiated by an entity within the security perimeter.|An employee accesses confidential files without permission.|
|Attacks|Outsider|Initiated from outside the security perimeter.|An external hacker attempts to access a network.|

| Threat Consequence      | Definition                                                           | Threat Actions (Attacks)                                                                                                                                                                                                                                              |
| ----------------------- | -------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unauthorized Disclosure | When an entity gains access to data for which it is not authorized.  | **Exposure:** Sensitive data is directly released.  <br>**Interception:** Unauthorized access to data in transit.  <br>**Inference:** Indirect access to sensitive data (e.g., deducing from patterns).  <br>**Intrusion:** Circumventing protections to access data. |
| Deception               | An authorized entity receives false data and believes it to be true. | **Masquerade:** Attacker pretends to be an authorized entity.  <br>**Falsification:** Inserting false data.  <br>**Repudiation:** Denying responsibility for an action.                                                                                               |
| Disruption              | Interrupts or prevents the correct operation of system services.     | **Incapacitation:** Disables a system component.  <br>**Corruption:** Modifies system functions or data undesirably.  <br>**Obstruction:** Interrupts or hinders system service delivery.                                                                             |
| Usurpation              | Unauthorized control of system services or functions.                | **Misappropriation:** Unauthorized control of a resource.  <br>**Misuse:** Making the system perform harmful or unintended actions.                                                                                                                                   |

|Passive Attack|Active Attack|
|---|---|
|Attempts to learn or use information from the system without affecting system resources.|Attempts to alter system resources or affect their operation.|
|Eavesdropping on or monitoring transmissions.|Involves modifying the data stream or creating a false stream.|
|**Goal:** Obtain information that is being transmitted.|**Goal:** Change, disrupt, or manipulate system operations or data.|
|**Two types:**|**Four categories:**|
|1. Release of message contents|1. Replay|
|2. Traffic analysis|2. Masquerade|
||3. Modification of messages|
||4. Denial of service|

## Attack Surfaces
| Attack Surfaces - Examples                                                                                          |
| ------------------------------------------------------------------------------------------------------------------- |
| Open ports on outward-facing web and other servers, and code listening on those ports                               |
| Services available on the inside of a firewall                                                                      |
| Code that processes incoming data, email, XML, office documents, and industry-specific custom data exchange formats |
| Interfaces, SQL, and web forms                                                                                      |
| An employee with access to sensitive information who is vulnerable to a social engineering attack                   |

|Attack Surface Category|Description|Examples|
|---|---|---|
|Network Attack Surface|Vulnerabilities over an enterprise network, wide-area network, or the Internet.|Network protocol vulnerabilities, denial-of-service attacks, disruption of communications links, and intruder attacks.|
|Software Attack Surface|Vulnerabilities in application, utility, or operating system code.|Web server software vulnerabilities.|
|Human Attack Surface|Vulnerabilities created by personnel or outsiders.|Social engineering, human error, and trusted insiders.|

## Standards

**Standards have been developed to cover management**  
**practices and the overall architecture of security**  
**mechanisms and services**  
• The most important of these organizations are:  
• National Institute of Standards and Technology (NIST)  
• NIST is a U.S. federal agency that deals with measurement science,  
standards, and technology related to U.S. government use and to the  
promotion of U.S. private sector innovation  

**Internet Society (ISOC)**  
• ISOC is a professional membership society that provides leadership in  
addressing issues that confront the future of the Internet, and is the  
organization home for the groups responsible for Internet  
infrastructure standards  

**International Telecommunication Union (ITU-T)**  
• ITU is a United Nations agency in which governments and the private  
sector coordinate global telecom networks and services  
• International Organization for Standardization (ISO)  
• ISO is a nongovernmental organization whose work results in  
international agreements that are published as International  
Standards



# Week 2 Encryption

**Kerchoff's Principle**
"a cryptographic system must remain secure even if an adversary knows all details of the system, including the algorithm, design, and implementation"

**Plaintext** -> Encryption -> **Ciphertext** -> Decryption -> **Plaintext**

**Plaintext** This is the original message or data that is to be secured
**Secret Key** The secret key is an input to the algorithm for substitutions and transformations
**Ciphertext** The scrambled message produced as an output.

**Cryptography** The making of encryption algorithms
**Cryptanalysis** The breaking of encryption algorithms

**Encrypting data at rest** protects the data where it's stored (On a computer, phone, database)
**Encrypting data in transit** protects the data as it is being communicated
**Access control** controls who can access the data

3 Main Components: Access Control, Monitoring, Data encryption

## Computational Issues
Algorithms should be reasonably efficient while remaining secure.

**Combination lock**  
**3 number sequence (2R, 1L, 0R), between 1-40**  
Possible combinations: 403 = 64,000
10 seconds per sequence: 178 hours (/ 2 = 89 if found midway)

**4 number sequence, 13 seconds per sequence**  
• 404 = 2,560,000  
9,244 hours

## Caesar Cipher

**Encrypting**
New letter = (Original letter + n) mod 26

**Decrypting**
Original letter = (New letter - n) mod 26

Replace every A with D, B with E etc, extremely basic.

**Considerations**
- Algorithms are public (Kerchoff's Principle)
- Encrypt/Decrypt dependant on a key
- The only secret is the key

Weakness to relative character frequencies for the key and bruteforcing
Ciphertext = “GRR MGAR OY JOBOJKJ OT ZNXKK  VGXZY”  
What is the most frequent Character?   n = 6
ALL GAUL IS DIVIDED IN THREE PARTS

## Caesar Cipher — Key Table

| Key (Shift) | Letter |
| ----------- | ------ |
| 0           | A      |
| 1           | B      |
| 2           | C      |
| 3           | D      |
| 4           | E      |
| 5           | F      |
| 6           | G      |
| 7           | H      |
| 8           | I      |
| 9           | J      |
| 10          | K      |
| 11          | L      |
| 12          | M      |
| 13          | N      |
| 14          | O      |
| 15          | P      |
| 16          | Q      |
| 17          | R      |
| 18          | S      |
| 19          | T      |
| 20          | U      |
| 21          | V      |
| 22          | W      |
| 23          | X      |
| 24          | Y      |
| 25          | Z      |

## Vigenère Cipher
Developed in 1553

Method of encrypting alphabetic text by using a series of interwoven Caesar ciphers based on the letters of a keyword.

**Reequirements:**
• The key can repeat however it has to match the length of the plaintext
• Repeat the Key until it matches the length of the plain text.

**Example**
Key: RPI
Plaintext: HELLO
Expanded Key: RPIRP
Cipher Text: YTTCD

## Factor Table

|Distance|Factors|Possible Key Lengths|
|---|---|---|
|2|1, 2|2|
|3|1, 3|3|
|4|1, 2, 4|2, 4|
|5|1, 5|5|
|6|1, 2, 3, 6|2, 3, 6|
|7|1, 7|7|
|8|1, 2, 4, 8|2, 4, 8|
|9|1, 3, 9|3, 9|
|10|1, 2, 5, 10|2, 5, 10|
|12|1, 2, 3, 4, 6, 12|2, 3, 4, 6, 12|
|15|1, 3, 5, 15|3, 5, 15|
|16|1, 2, 4, 8, 16|2, 4, 8, 16|
|18|1, 2, 3, 6, 9, 18|2, 3, 6, 9, 18|
|20|1, 2, 4, 5, 10, 20|2, 4, 5, 10, 20|
|24|1, 2, 3, 4, 6, 8, 12, 24|2, 3, 4, 6, 8, 12, 24|
|30|1, 2, 3, 5, 6, 10, 15, 30|2, 3, 5, 6, 10, 15, 30|

**Step 1: Start with the ciphertext**

Ciphertext: `DPRYEVNTNBUKWIAOXBUKWWBT`

• BUK appears at positions 9 and 17 (0-indexed) → distance 8  
• UKW appears at positions 10 and 18 → distance 8  
• BUKW appears at positions 9 and 17 → distance 8

**Step 2: Use the Kasiski test to find the key length**

Look for repeated sequences of letters.

`BUK` appears twice, starting at positions 10 and 18.

Distance: (18-10=8)

Factors of 8: 1, 2, 4, 8.

Possible key lengths include **2, 4 or 8**. Further analysis suggests the key length is 4.

**Step 3: Split the ciphertext into groups**

Divide the letters into four groups, based on their positions:

|Group 1|Group 2|Group 3|Group 4|
|---|---|---|---|
|D|P|R|Y|
|E|V|N|T|
|N|B|U|K|
|W|I|A|O|
|X|B|U|K|
|W|W|B|T|

Each group uses the same Caesar shift.

**Step 4: Use frequency analysis to find the shifts**

Try shifting each group backwards by different amounts. Look for common English letters (E, T, A, O, I, N) and patterns that form English words.

**Step 5: Recover the key**

Convert each shift into a letter:

Key: `KING`

Plaintext: `THE SUN AND THE MAN IN THE MOON`

Encrypting Example
• The apple is in the corner and the pear is there too (plain)  
• cat (key) catcatcatcatcatcat....

T = 19
C = 2
19 + 2 = 21 = V

Repeat for all letters

Vhx cpine bu ig vhx eokpek cnw vhx rett il vhxte mqo (cipher)
## Hill Cipher

Hill Cipher  
Plaintext: ACT  
Key: GYBNQKURP  
Ciphertext: POH  
We have to encrypt the message ‘ACT’ (n=3).The key is  
‘GYBNQKURP’ which can be written as the nxn matrix:

![[UNIVERSITY/CyberSecurityTestNotes/Assets/HillCipher.png]]
## ROT13 
Poor Encryption, Rotates the letters 13 
• No “key”  
• Susceptible to frequency analysis  
• Susceptible to brute forcing

![[UNIVERSITY/CyberSecurityTestNotes/Assets/ROT13.png]]

## Symmetric Encryption

• The universal technique for providing confidentiality for transmitted or stored data  
• Also referred to as conventional encryption or single-key encryption

**Two Requirements**
1. Strong encryption algorithm.
2. Sender and receiver must have obtained copies of the secret key in a secure fashion.

**Two distinct modes of operation:**  
• Stream Cipher  
Plain text is encrypted bit by bit  
Plain text and key are XORed 

• Block Cipher  
Plain text is encrypted block by block  
The whole block is encrypted with a key


## Stream Ciphers
• Each bit of plaintext is encrypted one by one, with the corresponding bit of the keystream, obtaining a bit of ciphertext.  
• To describe a stream cipher, it is enough to describe the key stream generator. Once the key stream is obtained, it works like the one-time pad.  
• The key stream must be generated from a random seed

![[XORTableExtended.png]]

![[XOROperation.png]]

## Block Ciphers
• Block ciphers operate on blocks of plaintext one at a time to produce blocks of ciphertext.  
• The encryption of a bit in a plaintext will depend on the other bits in the block.  
• The block sizes are usually reasonably large. For example, blocks in DES are of 64 bits and block in AES are 128 bits.  
• The most famous block cipher is DES (Data Encryption Standard).  
• Since DES is the most studied scheme and the design principles DES is based on have inspired a lot of ciphers used nowadays, we will have a slight view of DES
## Block Cipher Modes of Operation

| Mode                            | Description                                                                                                                                                                 | Typical Application                                                                                                                                                    |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Electronic Codebook (ECB)**   | Each block of 64 plaintext bits is encrypted independently using the same key. Identical plaintext blocks produce identical ciphertext blocks.                              | • Encryption of single, independent values (e.g., an encryption key).  <br>• Not recommended for general multi-block message encryption because patterns are revealed. |
| **Cipher Block Chaining (CBC)** | Each plaintext block is XORed with the preceding ciphertext block before encryption. The first block uses an Initialization Vector (IV).                                    | • General-purpose block-oriented data encryption.  <br>• Historically used for data transmission and file encryption.                                                  |
| **Cipher Feedback (CFB)**       | Processes data in segments of _s_ bits. The previous ciphertext (or IV initially) is encrypted to produce output, which is XORed with the plaintext to generate ciphertext. | • General-purpose stream-oriented transmission.  <br>• Applications processing data in small units.                                                                    |
| **Output Feedback (OFB)**       | Similar to CFB, but the input to the encryption algorithm is the preceding encryption output rather than the preceding ciphertext. The output is XORed with plaintext.      | • Stream-oriented transmission over noisy channels (e.g., satellite communication).  <br>• Useful when error propagation should be limited.                            |
| **Counter (CTR)**               | Each plaintext block is XORed with the encryption of a counter value. The counter is incremented for each subsequent block.                                                 | • General-purpose block-oriented data encryption.  <br>• High-speed applications requiring parallel processing.                                                        |

| Mode    | Real-Life Uses                                                                                                 |
| ------- | -------------------------------------------------------------------------------------------------------------- |
| **ECB** | 1. Encrypting individual cryptographic keys  <br>2. Encrypting isolated data blocks in specialised hardware    |
| **CBC** | 1. Encrypting files in legacy systems  <br>2. Protecting sensitive data in older banking systems               |
| **CFB** | 1. Encrypting data sent over communication links  <br>2. Securing data streams in legacy communication systems |
| **OFB** | 1. Satellite communications  <br>2. Radio communication over noisy channels                                    |
| **CTR** | 1. High-speed network encryption  <br>2. Disk and storage encryption systems                                   |
![[BlockCipherVisuals.png]]

### Block Cipher Modes Comparison

Parallelizable means multiple blocks of data can be encrypted or decrypted at the same time, rather than having to process them one after another.

| Mode | Type           | Parallelizable | Error Propagation    | Notes                       |
| ---- | -------------- | -------------- | -------------------- | --------------------------- |
| ECB  | Block-by-block | Yes            | None                 | Not secure - leaks patterns |
| CBC  | Block-by-block | No             | Current + next block | Very common, but slower     |
| CFB  | Stream-like    | No             | Limited (few bits)   | Self-synchronizing stream   |
| OFB  | Stream-like    | Yes            | Minimal (1 bit)      | Precomputable keystream     |
| CTR  | Stream-like    | Yes            | Minimal (1 block)    | Most secure & efficient     |
### Analogy
- **ECB:** Like sending a letter in identical envelopes - patterns show.
- **CBC:** Like chaining envelopes together - each depends on the previous.
- **CFB/OFB:** Like using a secret radio code - streams of encrypted data.
- **CTR:** Like using a counter-based one-time pad - fast and secure.
### Key Differences 
- **ECB:** Encrypts each block independently.
- **CBC:** Uses the previous ciphertext block.
- **CFB:** Feeds back the previous ciphertext.
- **OFB:** Feeds back the previous encryption output.
- **CTR:** Encrypts counter values.

**Block Ciphers**
• Processes the input one block of elements at a time  
• Produces an output block for each input block  
• Block size: Larger block sizes mean greater security (all other things being equal)  
but reduced encryption/decryption speed. A block size of 128 bits is a reasonable trade-off and is nearly universal among recent block cipher designs

![[BlockCiphers.png]]

### Block Cipher Attributes
**Key size:** Larger key size means greater security but may decrease encryption/ decryption speed. The most common key length in modern algorithms is 128 bits.  
**Number of rounds:** The essence of a symmetric block cipher is that a single round offers inadequate security but that multiple rounds offer increasing security. A typical size is 16 rounds.  
**Subkey generation algorithm**: Greater complexity in this algorithm should lead to greater difficulty of cryptanalysis.  
**Round function:** Again, greater complexity generally means greater resistance to cryptanalysis.

### Practical Security Issues
Typically, symmetric encryption is applied to a unit of data larger than a single  
64-bit or 128-bit block.  
• Electronic codebook (ECB) mode is the simplest approach to multiple-block encryption:  
o Each block of plaintext is encrypted using the same key  
o Cryptanalysts may be able to exploit regularities in the plaintext  
**Modes of operation:**  
• Alternative techniques developed to increase the security of symmetric block encryption for large sequences  
• Overcomes the weaknesses of ECB

![[PopularAlgorithms.png]]

### Cryptanalytic Attacks
• Rely on:  
o Nature of the algorithm  
o Some knowledge of the general characteristics of the plaintext  
o Some sample plaintext-ciphertext pairs  
• Exploits the characteristics of the algorithm to attempt to deduce a specific  
plaintext or the key being used  
o If successful, all future and past messages encrypted with that key are compromised  
### Brute-force attacks  
• Try all possible keys on some ciphertext until an intelligible translation into  
plaintext is obtained  
• On average half of all possible keys must be tried to achieve success  
• Number of Keys are dictated by the key size.
## One Time Pad

• Invented by Gilbert Vernam in the 1920s  
**• The message is a bitstring 𝑚𝜖{0,1}n**  
**• The key is a bitstring as long as the message, 𝑘𝜖{0,1}n**  
• Encryption is similar to shift cipher  
• The ciphertext is obtained by XORing each bit of the plaintext with each bit of  
the key: c = m ⨁ k.

![[XORTable.png]]

![[OneTimePad.png]]

**Advantages**
-  Easy to compute  
-  Encryption and decryption are the same operation  
- Bitwise XOR is very cheap to compute  
- As secure as theoretically possible  
- Given a ciphertext, all plaintexts are equally likely, regardless of attacker’s resources  if and only if the key sequence is truly random  
 However True randomness is expensive to obtain in large quantities

**Disadvantages**
-  Key must be as long as the plaintext  
-  Impractical in most realistic scenarios  
-  Still used for diplomatic and intelligence traffic  
- Does not guarantee integrity  
- One-time pad only guarantees confidentiality  
- Attacker cannot recover plaintext, but can easily change it to something  else  
- Insecure if keys are reused  
-  Attacker can obtain XOR of plaintexts

# Week 3 Encryption

## DES
Until recently was the most widely used encryption scheme  

FIPS PUB 46  
Referred to as the Data Encryption Algorithm (DEA)  
Uses 64 bit plaintext block and 56 bit key to produce a 64 bit ciphertext   block  
DES is a Feistel Cipher.

**Strength concerns:**  
Concerns about the algorithm itself  
DES is the most studied encryption algorithm in existence  
Some detractors but no serious flaws  
Concerns about the use of a 56-bit key  
Current processors now make the key length a lot more ineffective

- DES is a symmetric encryption algorithm: the same secret key is used for encryption and decryption.
- Block size = 64 bits.
- Main key size = 64 bits, of which 56 bits are effective key bits and 8 are parity bits.
- Number of rounds = 16.
- Each half = 32 bits.
- Each round subkey = 48 bits.
- DES uses a Feistel structure.
- DES is now considered insecure for protecting sensitive data because its effective key is too short. Modern systems generally use AES instead.

## DES Key Lengths

|Key Type|Length|Explanation|
|---|---|---|
|Main key (K)|64 bits|Includes 8 parity bits|
|Effective key|56 bits|64 − 8 parity bits|
|Parity bits|8 bits|Used for error checking|
|Round subkey (Kᵢ)|48 bits|Used in each of the 16 rounds|
|Number of rounds|16|Each round uses a different subkey|
### Key facts

![[ParityBit.png]]

![[AverageKeySearch.png]]

![[DESSummary.png]]

![[DESRounds.png]]

### DES encryption step by step

1. Split the 64-bit plaintext into two halves.
2. Divide: 32-bit left half (L₀) and 32-bit right half (R₀).
3. Apply F: The 32-bit right half goes through the F function with the round key. The F function expands it to 48 bits, mixes it with the 48-bit subkey, then produces 32 bits again.
4. XOR: XOR the F function's 32-bit output with the original left half to produce the new right half.
5. Swap: The old right half becomes the new left half.
6. Repeat: Do this for 16 rounds, using a different subkey each time

![[Permutation.png]]

**Brute-force attacks**  
• Try all possible keys on some ciphertext until an intelligible translation into plaintext is obtained  
• On average half of all possible keys must be tried to achieve success  
• Number of Keys are dictated by the key size.

## **Triple DES**

• Repeats basic DES algorithm three times using either two or three unique keys  
• First standardized for use in financial applications in ANSI standard X9.17 in 1985  

**Advantages:**  
• 168-bit key length overcomes the vulnerability to brute-force attack of DES  
• Underlying encryption algorithm is the same as in DES  
**Drawbacks:**  
• Algorithm is sluggish in software  
• Uses a 64-bit block size

| Category | Details | Key Information |
|---|---|---|
| Purpose | Needed a replacement for 3DES | 3DES was not reasonable for long-term use |
| Proposal | NIST called for proposals for a new AES in 1997 | Advanced Encryption Standard (AES) |
| Security | Should have a security strength equal to or better than 3DES | Stronger or equivalent security |
| Efficiency | Significantly improved efficiency | Faster and more efficient encryption |
| Cipher Type | Symmetric block cipher | Encrypts data using the same secret key |
| Data Block Size | 128 bits | Fixed block size |
| Key Sizes | 128, 192, or 256 bits | Three supported key lengths |
| Selection | Selected Rijndael in November 2001 | Rijndael became the AES algorithm |
| Standard | Published as FIPS 197 | Federal Information Processing Standard 197 |
![[3DES.png]]
## AES
An iterative rather than Feistel cipher  
o Processes data as block of 4 columns of 4 bytes  
o Operates on entire data block in every round  
**Designed to be:**  
o Resistant against known attacks  
o Speed and code compactness on many CPUs  
o Design simplicity  
Data block viewed as 4-by-4 table of bytes  
Such a table is called the current state Key is expanded to array of words  
Has 10 rounds in which state the following transformations (called "layers")
o BS- byte substitution (1 S-box used on every byte)  
o SR- shift rows (permute bytes between groups/columns)  
o MC- mix columns (uses matrix multiplication in GF(256))  
o ARK- add round key (XOR state with round key)

## DES vs AES

## 1. Data Encryption Standard (DES)

- **Type:** Symmetric block cipher
- **Block Size:** 64 bits
- **Key Size:** 56 effective bits (64 bits including parity bits)
- **Developed by:** IBM, based on earlier work, and adopted by NIST
- **Standardized:** 1977
- **Structure:** Feistel network
- **Number of Rounds:** 16
- **Security:** Insecure for modern use because its 56-bit key is vulnerable to brute-force attacks.
- **Status:** Obsolete; replaced by stronger encryption standards.

## 2. Advanced Encryption Standard (AES)

- **Type:** Symmetric block cipher
- **Block Size:** 128 bits
- **Key Sizes:** 128, 192, or 256 bits
- **Selected:** Rijndael was selected by NIST in 2000.
- **Standardized:** Published as FIPS 197 in 2001.
- **Structure:** Substitution-Permutation Network (SPN)
- **Number of Rounds:**
  - AES-128: 10 rounds
  - AES-192: 12 rounds
  - AES-256: 14 rounds
- **Security:** Considered secure when implemented correctly with appropriate keys and modes of operation.
- **Status:** Widely used in modern encryption systems.

## 3. DES vs AES Comparison

| Feature | DES | AES |
|---|---|---|
| Full Name | Data Encryption Standard | Advanced Encryption Standard |
| Cipher Type | Symmetric block cipher | Symmetric block cipher |
| Block Size | 64 bits | 128 bits |
| Effective Key Size | 56 bits | 128, 192, or 256 bits |
| Structure | Feistel network | Substitution-Permutation Network (SPN) |
| Number of Rounds | 16 | 10, 12, or 14 |
| Standardized | 1977 | 2001 |
| Security | Insecure against brute-force attacks | Secure when properly implemented |
| Performance | Efficient for older hardware | Efficient on modern hardware |
| Current Use | Obsolete | Widely used |
| Replacement | Replaced by stronger algorithms | Successor to DES in modern applications |

## 4. Key Differences

- **Key Size:** AES supports much larger keys than DES, making brute-force attacks significantly harder.
- **Block Size:** AES encrypts 128-bit blocks, while DES encrypts 64-bit blocks.
- **Structure:** DES uses a Feistel network, whereas AES uses a Substitution-Permutation Network.
- **Security:** DES is no longer considered secure. AES remains a standard choice for modern encryption.
- **Efficiency:** AES is designed for efficient implementation in modern software and hardware.

## 5. Important Exam Notes

- DES has a **56-bit effective key** and a **64-bit block size**.
- AES has a **128-bit block size** and supports **128-, 192-, and 256-bit keys**.
- DES uses **16 rounds**.
- AES uses **10, 12, or 14 rounds**, depending on the key size.
- Both DES and AES are **symmetric encryption algorithms**.
- AES was selected to replace DES because DES no longer provided adequate security.
- AES is based on the **Rijndael algorithm**.

## 6. Quick Memory Trick

- **DES:** 64-bit block, 56-bit key, 16 rounds.
- **AES:** 128-bit block, 128/192/256-bit key, 10/12/14 rounds.

**Remember:** DES is outdated; AES is the modern standard.

![[AESDiagram.png]]

![[RoundKeySizes.png]]

**Random numbers are essential to many aspects of cryptography, including:**  
• Keys for public-key algorithms  
• Stream key for symmetric stream cipher  
• Symmetric key for use as a temporary session key or in creating a digital envelope  
• Handshaking to prevent replay attacks  
• Session key

**Independence of random numbers means that knowing one number in a sequence does not help you predict the other numbers.**

• Probably most significant advancement in the 3000 year history of cryptography  
• Uses two keys – a public & a private key  
• Asymmetric since parties are not equal  
• Uses clever application of number theoretic concepts to function  
• complements rather than replaces private key crypto  
Why Public-key  
• Developed to address two key issues:  
• key distribution – how to have secure communications in general without having  
to trust a KDC with your key  
• digital signatures – how to verify a message comes intact from the claimed  
sender  
• Public invention due to Whitfield Diffie & Martin Hellman at Stanford Uni in 1976  
• known earlier in classified community

![[Pasted image 20261026195715.png]]

# Week 5 OS & Database Security

## Worms
•Program that actively seeks out more machines to infect and each infected  
machine serves as an automated launching pad for attacks on other machines  
•Exploits software vulnerabilities in client or server programs  
•Can use network connections to spread from system to system  
•Spreads through shared media (USB drives, CD, DVD data disks)  
•E-mail worms spread in macro or script code included in attachments and instant messenger file transfers  
•Upon activation the worm may replicate and propagate again  
•Usually carries some form of payload  
•First known implementation was done in Xerox Palo Alto Labs in the early 1980s

**WannaCry**  
Ransomware attack in May  
2017 that spread extremely  
fast over a period of hours  
to days, infecting hundreds  
of thousands of systems  
belonging to both public  
and private organizations in  
more than 150 countries  

It spread as a worm by  
aggressively scanning both  
local and random remote  
networks, attempting to  
exploit a vulnerability in the  
SMB file sharing service on  
unpatched Windows  
systems  

This rapid spread was only  
slowed by the accidental  
activation of a “kill-switch”  
domain by a UK security  
researcher  

Once installed on infected  
systems, it also encrypted  
files, demanding a ransom  
payment to recover them
## Worm Technology

## Overview

A **computer worm** is a type of malware that can self-replicate and spread across computers and networks, often without direct user interaction. Worms may exploit vulnerabilities to propagate and can consume network resources, disrupt services, or deliver additional malicious payloads.

## 1. Multiplatform

**Definition:** A multiplatform worm can infect or spread across different operating systems or computing environments.

- **How it works:** It may contain different code or techniques for targeting platforms such as Windows, Linux, and macOS.
    
- **Purpose:** To reach a wider range of devices rather than being limited to one operating system.
    
- **Example:** A worm designed with separate components that can infect both Windows and Linux systems.
    

**Key point:** Multiplatform means the worm can target multiple operating systems or platforms.

## 2. Multi-exploit

**Definition:** A multi-exploit worm uses multiple vulnerabilities or exploitation techniques to spread.

- **How it works:** If one vulnerability is unavailable on a target, the worm may attempt another applicable vulnerability.
    
- **Purpose:** To increase the number of systems it can infect.
    
- **Example:** A worm that exploits a vulnerable network service and can also spread through a separate unpatched software flaw.
    

**Key point:** Multi-exploit means using more than one exploit or vulnerability to propagate.

## 3. Ultrafast Spreading

**Definition:** An ultrafast-spreading worm propagates rapidly across systems and networks.

- **How it works:** Infected machines can scan for vulnerable targets and spread copies of the worm to them, potentially creating exponential growth.
    
- **Purpose:** To infect as many vulnerable systems as possible in a short period.
    
- **Example:** A worm that rapidly spreads through a corporate network by exploiting vulnerable computers.
    

**Key point:** Ultrafast spreading refers to the speed and scale of propagation.

## 4. Polymorphic

**Definition:** A polymorphic worm changes its appearance or certain parts of its code while preserving its malicious functionality.

- **How it works:** It may encrypt or transform parts of its code and alter the associated decryption routine, making different copies look different.
    
- **Purpose:** To make signature-based antivirus detection more difficult.
    
- **Example:** Two copies of a worm that perform the same malicious actions but have different detectable code patterns.
    

**Key point:** Polymorphic malware changes its code representation to evade detection.

## 5. Metamorphic

**Definition:** A metamorphic worm rewrites or restructures its own code as it replicates, while retaining its underlying behaviour.

- **How it works:** It can rearrange instructions, substitute equivalent instructions, or restructure its code to create different versions.
    
- **Purpose:** To make each generation harder to recognise through static code signatures.
    
- **Example:** Successive copies of a worm contain substantially different instruction sequences but perform the same propagation activities.
    

**Key point:** Metamorphic malware transforms its own code structure rather than relying only on encrypting its code.

---

## Polymorphic vs Metamorphic

|Feature|Polymorphic|Metamorphic|
|---|---|---|
|Main change|Changes code appearance, often using encryption|Rewrites or restructures its code|
|Code structure|May retain a recognisable underlying structure|Can substantially change its instruction structure|
|Detection challenge|Varying code patterns and decryptors|Different code structures with similar behaviour|
|Main objective|Evade malware detection|Evade malware detection|

![[Worms.png]]

## Malvertising

- Places malware on websites without actually compromising them
- The attacker pays for advertisements that are highly likely to be placed on their intended target websites and incorporate malware in them
- Using these malicious ads, attackers can infect visitors to sites displaying them
- The malware code may be dynamically generated to either reduce the chance of detection or to only infect specific systems
- Has grown rapidly in recent years because they are easy to place on desired websites with few questions asked and are hard to track
- Attackers can place these ads for as little as a few hours, when they expect their intended victims could be browsing the targeted websites, greatly reducing their visibility

## Clickjacking

- Also known as a user-interface (UI) redress attack
- Using a similar technique, keystrokes can also be hijacked
  - A user can be led to believe they are typing in the password to their email or bank account, but are instead typing into an invisible frame controlled by the attacker
- Vulnerability used by an attacker to collect an infected user’s clicks
  - The attacker can force the user to do a variety of things from adjusting the user’s computer settings to unwittingly sending the user to Web sites that might have malicious code
  - By taking advantage of Adobe Flash or JavaScript an attacker could even place a button under or over a legitimate button making it difficult for users to detect
  - A typical attack uses multiple transparent or opaque layers to trick a user into clicking on a button or link on another page when they were intending to click on the top level page
  - The attacker is hijacking clicks meant for one page and routing them to another page

## Social Engineering

- “Tricking” users to assist in the compromise of their own systems

## Spam

- Unsolicited bulk e-mail
- Significant carrier of malware
- Used for phishing attacks

## Trojan horse

- Program or utility containing harmful hidden code
- Used to accomplish functions that the attacker could not accomplish directly

## Mobile phone Trojans

- First appeared in 2004 (Skuller)
- Target is the smartphone

## Real-world damage

- Causes damage to physical equipment
  - Chernobyl virus rewrites BIOS code
- Stuxnet worm
  - Targets specific industrial control system software
- There are concerns about using sophisticated targeted malware for industrial sabotage

## Logic bomb

- Code embedded in the malware that is set to “explode” when certain conditions are met

## Payload Attack Agents

## Bots

- Takes over another Internet attached computer and uses that computer to launch or manage attacks

## Botnet

- Collection of bots capable of acting in a coordinated manner

### Uses

- Distributed denial-of-service (DDoS) attacks
- Spamming
- Sniffing traffic
- Keylogging
- Spreading new malware
- Installing advertisement add-ons and browser helper objects (BHOs)
- Attacking IRC chat networks
- Manipulating online polls/games

## Remote Control Facility

- Distinguishes a bot from a worm
  - Worm propagates itself and activates itself
  - Bot is initially controlled from some central facility
- Typical means of implementing the remote control facility is on an IRC server
  - Bots join a specific channel on this server and treat incoming messages as commands
  - More recent botnets use covert communication channels via protocols such as HTTP
  - Distributed control mechanisms use peer-to-peer protocols to avoid a single point of failure

## Buffer Overflows

## Buffer
- Contiguous set of a given data type
- Common in C
  - All strings are buffers of `char`’s

## Overflow
- Put more into the buffer than it can hold

### Where does the extra data go?

## Definition of Buffer Overflow

A buffer overflow, is defined in the NIST Glossary of Key Information Security Terms as follows:

> “A condition at an interface under which more input can be placed into a buffer or data holding area than the capacity allocated, overwriting other information. Attackers exploit such a condition to crash a system or to insert specially crafted code that allows them to gain control of the system.”