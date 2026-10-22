# Cryptography II

## Introduction

### What we have covered

| Classification | Type | Examples |
|---|---|---|
| Classical | Substitution | Caesar, Vigenère, ROT13, Hill |
| Modern | Symmetric (Private Key) | Stream, Block |
| Modern | Asymmetric (Public Key) | RSA, Diffie-Hellman |

---

# Symmetric Encryption

## Data Encryption Standard (DES)

- Until recently was the most widely used encryption scheme.
- FIPS PUB 46.
- Referred to as the Data Encryption Algorithm (DEA).
- Uses a **64-bit plaintext block** and **56-bit key** to produce a **64-bit ciphertext block**.
- It is the best studied cipher.
- DES is a **Feistel Cipher**.

### Strength Concerns

- Concerns about the algorithm itself:
  - DES is the most studied encryption algorithm in existence.
  - Some detractors but no serious flaws.
- Concerns about the use of a **56-bit key**:
  - The speed of commercial off-the-shelf processors makes this key length woefully inadequate.

### Average Time Required for Exhaustive Key Search

| Key size | Cipher     | Number of alternative keys | Time at 10⁹ decryptions/s | Time at 10¹³ decryptions/s |
| -------- | ---------- | -------------------------: | ------------------------: | -------------------------: |
| 56 bits  | DES        |               ≈ 7.2 × 10¹⁶ |               1.125 years |                     1 hour |
| 128 bits | AES        |               ≈ 3.4 × 10³⁸ |          5.3 × 10²¹ years |           5.3 × 10¹⁷ years |
| 168 bits | Triple DES |               ≈ 3.7 × 10⁵⁰ |          5.8 × 10³³ years |           5.8 × 10²⁹ years |
| 192 bits | AES        |               ≈ 6.3 × 10⁵⁷ |          9.8 × 10⁴⁰ years |           9.8 × 10³⁶ years |
| 256 bits | AES        |               ≈ 1.2 × 10⁷⁷ |          1.8 × 10⁶⁰ years |           1.8 × 10⁵⁶ years |

---

# Feistel Network

- Many encryption algorithms incorporate a structure first proposed by **Horst Feistel of IBM (1973)**; a Feistel Network.
- This includes the DES standard.

### Structure

- The inputs to the encryption algorithm are a plaintext block of length **2w bits** and a key **K**.
- The plaintext block is divided into two halves:
  - `L₀`
  - `R₀`
- The two halves of the data pass through **n rounds of processing** and then combine to produce the ciphertext block.
- Each round `i` has as inputs:
  - `Lᵢ₋₁`
  - `Rᵢ₋₁`
  - A subkey `Kᵢ`, derived from the overall `K`.
- In general, the subkeys `Kᵢ` are different from `K` and from each other.
- Subkeys are generated from the key by a **subkey generation algorithm**.

### Round Structure

- All rounds have the same structure.
- A substitution is performed on the left half of the data.
- This is done by:
  1. Applying a round function `F` to the right half of the data.
  2. Taking the **exclusive-OR (XOR)** of the output of that function and the left half of the data.
- The round function has the same general structure for each round but is parameterized by the round subkey `Kᵢ`.
- Following this substitution, a permutation is performed that consists of the interchange of the two halves of the data.

![[DESRoundsWhite.png]]

![[DesRoundsSimplified.png]]

---

# DES

- **16 rounds**.
- In each round:
  - Expansion Box.
  - Substitution Box.
  - XOR with the round key.

### DES Structure

- `L (32 bits)`
- `R (32 bits)`
- Expansion permutation.
- XOR.
- S-BOX.
- Permutation.
- XOR.
- Left and right halves are processed through the rounds.
- Key processing includes:
  - `Lk (28 bits)`
  - `Rk (28 bits)`
  - LCS
  - Permutation
- 48-bit round key.
- 32-bit data outputs.


![[DESExplained.png]]
### Variable Changes

Changing the plaintext or key produces different ciphertext.

#### Example

Plaintext:

`Hello world`

Hex:

`48656c6c6f20776f726c64`

Output:

`80508BC5A5F89985FB1DB52E8`
`1F971ED`

Key change:

`0000000000000000`

Output:

`EADE4DB3AFA20320011F38638`
`1D8E123`

![[HexKeyExample.png]]
### Encrypted Hex

- Why is the Encrypted Hex much longer?
- Why is this important?

---

# Brute-force Attacks

- Try all possible keys on some ciphertext until an intelligible translation into plaintext is obtained.
- On average half of all possible keys must be tried to achieve success.
- Number of keys are dictated by the key size.

---

# Double DES (2DES)

- Double DES is presented as a symmetric encryption approach.
![[DESBruteforceProblem.png]]

---

# Triple DES (3DES)

- Repeats the basic DES algorithm three times using either two or three unique keys.
- First standardized for use in financial applications in **ANSI standard X9.17 in 1985**.

![[DESMultiplication.png]]

### Attractions

- **168-bit key length** overcomes the vulnerability to brute-force attack of DES.
- Underlying encryption algorithm is the same as in DES.

### Drawbacks

- Algorithm is sluggish in software.
- Uses a **64-bit block size**.

### Encryption

`P → E(K1) → D(K2) → E(K3) → C`

### Decryption

`C → D(K3) → E(K2) → D(K1) → P`

---

# Advanced Encryption Standard (AES)

![[3DESProblems.png]]

- Needed a replacement for 3DES.
- 3DES was not reasonable for long-term use.
- NIST called for proposals for a new AES in **1997**.
- Should have a security strength equal to or better than 3DES.
- Significantly improved efficiency.
- Symmetric block cipher.
- **128-bit data** and **128/192/256-bit keys**.
- Selected **Rijndael** in November 2001.
- Published as **FIPS 197**.

## AES Structure

- An iterative rather than Feistel cipher.
- Processes data as a block of **4 columns of 4 bytes**.
- Operates on the entire data block in every round.

### Designed to be

- Resistant against known attacks.
- Speed and code compactness on many CPUs.
- Design simplicity.

### Current State

- Data block viewed as a **4-by-4 table of bytes**.
- Such a table is called the **current state**.
- Key is expanded to an array of words.

### AES Transformations

AES has rounds in which the state undergoes the following transformations, called **layers**:

| Layer | Transformation |
|---|---|
| BS | Byte substitution — 1 S-box used on every byte |
| SR | Shift rows — permute bytes between groups/columns |
| MC | Mix columns — uses matrix multiplication in GF(256) |
| ARK | Add round key — XOR state with round key |

- First and last round are a little different.

### AES Parameters

| AES | Key Size (bits) | Plaintext Size (bits) | Number of Rounds | Round Key Size |
|---|---:|---:|---:|---:|
| AES-128 | 128 | 128 | 10 | 128 |
| AES-192 | 192 | 128 | 12 | 128 |
| AES-256 | 256 | 128 | 14 | 128 |

---

# Random Numbers

## Uses

Random numbers are essential to many aspects of cryptography, including:

- Keys for public-key algorithms.
- Stream key for symmetric stream cipher.
- Symmetric key for use as a temporary session key or in creating a digital envelope.
- Handshaking to prevent replay attacks.
- Session key.

## Criteria for a Good Random Number Generator

### Uniform Distribution of Random Numbers

- Frequency of occurrence of each of the numbers should be approximately the same.

### Independence of Random Numbers

- No one value in the sequence can be inferred from the others.

### Unpredictability

- Each number is statistically independent of other numbers in the sequence.
- Opponent should not be able to predict future elements of the sequence on the basis of earlier elements.

---

# Random vs Pseudorandom

- Cryptographic applications typically make use of algorithmic techniques for random number generation.
- Algorithms are deterministic and therefore produce sequences of numbers that are not statistically random.

### Pseudorandom Numbers

- Sequences produced that satisfy statistical randomness tests.
- Likely to be predictable.

### True Random Number Generator (TRNG)

- Uses a nondeterministic source to produce randomness.
- Most operate by measuring unpredictable natural processes.
- Examples:
  - Radiation.
  - Gas discharge.
  - Leaky capacitors.
- Increasingly provided on modern processors.

---

# Public-Key Cryptography

- Probably most significant advancement in the **3000 year history of cryptography**.
- Uses two keys:
  - A public key.
  - A private key.
- Asymmetric since parties are not equal.
- Uses clever application of number theoretic concepts to function.
- Complements rather than replaces private key cryptography.

## Why Public-Key Cryptography?

Developed to address two key issues:

### Key Distribution

- How to have secure communications in general without having to trust a KDC with your key.

### Digital Signatures

- How to verify a message comes intact from the claimed sender.

### Development

- Public invention due to **Whitfield Diffie & Martin Hellman at Stanford University in 1976**.
- Known earlier in the classified community.