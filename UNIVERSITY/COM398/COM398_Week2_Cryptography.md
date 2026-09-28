## Definitions

---

| Term | Definition |
|---|---|
| Plaintext | This is the original message or data that is to be secured. |
| Encryption algorithm | This is the mechanism of securing the message and data. The encryption algorithm performs various substitutions and transformations on the plaintext. |
| Secret key | The secret key is also input to the algorithm. The exact substitutions and transformations performed by the algorithm depend on the key. |
| Ciphertext | This is the scrambled message produced as output. It depends on the plaintext and the secret key. For a given message, two different keys will produce two different ciphertexts. |
| Decryption algorithm | This is essentially the encryption algorithm run in reverse. It takes the ciphertext and the same secret key and produces the original plaintext. |
| Cryptographer | Invents clever algorithms. |
| Cryptanalyst | Breaks clever algorithms. 

---
## Computational Issues

- Algorithm should be reasonably efficient
- Security depends on how hard it is to break
- **Combination lock**
  - 3 number sequence (2R, 1L, 0R), #s between 1-40
  - Possible combinations: 40³ = 64,000
  - 10 seconds per sequence: 178 hours (/ 2 = 89)
  - 4 number sequence, 13 seconds per sequence
  - 40⁴ = 2,560,000
  - 9,244 hours

---

# Symmetric Encryption

## Caesar Cipher

- Replace every ‘A’ in the message with a ‘D’
- Replace every ‘B’ in the message with a ‘E’
- Replace every ‘C’ in the message with an ‘F’, etc.
- Algorithms are public (Kerchoff’s Principle)
- Encrypt/decrypt depends on a key
- The only secret is the key
- For Caesar cipher, key is n, since shift forward n to encrypt, shift backward n to decrypt
- Encryption: Ci = (Pi + n) mod 26
- Decryption: Pi = (Ci - n) mod 26

## Vigenere Cipher

- Developed in 1553.
- It is a method of encrypting alphabetic text by using a series of interwoven Caesar ciphers, based on the letters of a keyword.
- Key: A word W of Length M.
- Plain text P of length N.
- Repeat the Key until it matches the length of the plain text.
- For each letter Pj of the plain text, apply a Caesar Cipher of length Wj
- Example:
  - Key: RPI
  - Plain Text: HELLO
  - Expanded key: RPIRP
  - Cipher Text: YTTCD

![[HillCipherTable.png]]

## Hill Cipher

- Developed by the mathematician Lester Hill in 1929
- Strength is that it completely hides single-letter frequencies
- The use of a larger matrix hides more frequency information
- A 3 x 3 Hill cipher hides not only single-letter but also two-letter frequency information
- Strong against a ciphertext-only attack but easily broken with a known plaintext attack
- Example:
  - Plaintext: ACT
  - Key: GYBNQKURP
  - Ciphertext: POH
  - P = 15, O = 14, H = 7

![[HillCipher.png]]

## ROT13

- Poor Encryption: ROT13
- No “key”
- Susceptible to frequency analysis
- Susceptible to brute forcing

![[ROT13.png]]

---

## One Time Pad

- Invented by Gilbert Vernam in the 1920s
- The message is a bitstring m ∈ {0,1}ⁿ
- The key is a bitstring as long as the message k ∈ {0,1}ⁿ
- Encryption is similar to shift cipher
- The ciphertext is obtained by XORing each bit of the plaintext with each bit of the key
- Encryption: c = m ⊕ k
- Key is a random bit sequence as long as the plaintext
- Encrypt by bitwise XOR of plaintext and key
  - ciphertext = plaintext ⊕ key
- Decrypt by bitwise XOR of ciphertext and key
  - ciphertext ⊕ key = plaintext

### Advantages

- Easy to compute
- Encryption and decryption are the same operation
- Bitwise XOR is very cheap to compute
- As secure as theoretically possible
- Given a ciphertext, all plaintexts are equally likely, regardless of attacker’s computational resources
- If and only if the key sequence is truly random
- True randomness is expensive to obtain in large quantities

### Disadvantages

- Key must be as long as the plaintext
  - Impractical in most realistic scenarios
  - Still used for diplomatic and intelligence traffic
- Does not guarantee integrity
  - One-time pad only guarantees confidentiality
  - Attacker cannot recover plaintext, but can easily change it to something else
- Insecure if keys are reused
  - Attacker can obtain XOR of plaintexts

![[Pasted image 20260928164519.png]]

---

## Stream Cipher

- Plain text is encrypted bit by bit
- Plain text and key are XORed
- Each bit of plaintext is encrypted one by one, with the corresponding bit of the keystream
- To describe a stream cipher, it is enough to describe the key stream generator
- Once the key stream is obtained, it works like the one-time pad
- The key stream must be generated from a random seed
  
![[StreamCipher.png]]

---

## Block Cipher

- Plaintext is encrypted block by block
- The whole block is encrypted with a key
- Block ciphers operate on blocks of plaintext one at a time to produce blocks of ciphertext
- The encryption of a bit in a plaintext will depend on the other bits in the block
- Block sizes are usually reasonably large
  - DES: 64 bits
  - AES: 128 bits
- The most famous block cipher is DES
  - Data Encryption Standard
- DES is the most studied scheme
- The design principles DES is based on have inspired a lot of ciphers used nowadays

![[BlockCipher.png]]

---

## Block Cipher Modes

### Electronic Codebook (ECB)

- Each block of 64 plaintext bits is encoded independently using the same key
- Typical application:
  - Secure transmission of single values
  - Example: an encryption key

### Cipher Block Chaining (CBC)

- The input to the encryption algorithm is the XOR of:
  - The next 64 bits of plaintext
  - The preceding 64 bits of ciphertext
- Typical applications:
  - General-purpose block-oriented transmission
  - Authentication

### Cipher Feedback (CFB)

- Input is processed s bits at a time
- Preceding ciphertext is used as input to the encryption algorithm
- Produces pseudorandom output
- Output is XORed with plaintext to produce the next unit of ciphertext
- Typical applications:
  - General-purpose stream-oriented transmission
  - Authentication

### Output Feedback (OFB)

- Similar to CFB
- The input to the encryption algorithm is the preceding DES output
- Typical application:
  - Stream-oriented transmission over noisy channel
  - Example: satellite communication

### Counter (CTR)

- Each block of plaintext is XORed with an encrypted counter
- The counter is incremented for each subsequent block
- Typical applications:
  - General-purpose block-oriented transmission
  - Useful for high-speed requirements

![[Block Cipher Modes.png]]

---

## Block Cipher Mode Characteristics

| Mode | Type | Parallelizable | Error Propagation | Notes |
|---|---|---|---|---|
| ECB | Block-by-block | Yes | None | Not secure — leaks patterns |
| CBC | Block-by-block | No | Current + next block | Very common, but slower |
| CFB | Stream-like | No | Limited (few bits) | Self-synchronizing stream |
| OFB | Stream-like | Yes | Minimal (1 bit) | Precomputable keystream |
| CTR | Stream-like | Yes | Minimal (1 block) | Most secure & efficient |

---

## Block Cipher

- Processes the input one block of elements at a time
- Produces an output block for each input block

### Block Size

- Larger block sizes mean greater security, all other things being equal
- Reduced encryption/decryption speed
- A block size of 128 bits is a reasonable trade-off
- Nearly universal among recent block cipher designs

### Key Size

- Larger key size means greater security
- May decrease encryption/decryption speed
- Most common key length in modern algorithms is 128 bits

### Number of Rounds

- A single round offers inadequate security
- Multiple rounds offer increasing security
- A typical size is 16 rounds

### Subkey Generation Algorithm

- Greater complexity in this algorithm should lead to greater difficulty of cryptanalysis

### Round Function

- Greater complexity generally means greater resistance to cryptanalysis

---

## Practical Security Issues

- Symmetric encryption is typically applied to a unit of data larger than a single 64-bit or 128-bit block
- Electronic Codebook (ECB) mode is the simplest approach to multiple-block encryption
- Each block of plaintext is encrypted using the same key
- Cryptanalysts may be able to exploit regularities in the plaintext
- Alternative techniques developed to:
  - Increase the security of symmetric block encryption for large sequences
  - Overcome the weaknesses of ECB

---

# Asymmetric Encryption

- Public Key
- Private Key
- RSA
- Diffie Hellman

---

# Cryptanalytic Attacks

- Rely on:
  - Nature of the algorithm
  - Some knowledge of the general characteristics of the plaintext
  - Some sample plaintext-ciphertext pairs
- Exploits the characteristics of the algorithm to attempt to deduce:
  - A specific plaintext
  - The key being used
- If successful:
  - All future and past messages encrypted with that key are compromised

## Brute-Force Attacks

- Try all possible keys on some ciphertext until an intelligible translation into plaintext is obtained
- On average half of all possible keys must be tried to achieve success
- Number of keys are dictated by the key size