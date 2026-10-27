# Block Ciphers

## 1. What is a Block Cipher?

- A **block cipher** is a symmetric-key encryption algorithm that encrypts plaintext in fixed-size blocks, producing ciphertext blocks of the same size.
    
- The same secret key is used for encryption and decryption.
    
- Each block contains multiple bits. For example:
    
    - **DES (Data Encryption Standard):** 64-bit block size and 56-bit effective key.
        
    - **AES (Advanced Encryption Standard):** 128-bit block size, with key sizes of 128, 192 or 256 bits.
        
- Unlike a basic substitution cipher, the encryption of a bit depends on the other bits in the block and the secret key.
    
- Block ciphers aim to provide **confusion and diffusion**:
    
    - **Confusion:** Makes the relationship between the key and ciphertext difficult to understand.
        
    - **Diffusion:** Spreads the influence of each plaintext bit across many ciphertext bits.
        
- A block cipher is a mathematical transformation that operates on one block at a time. To encrypt longer messages securely, it is normally used with a **mode of operation**.
    

### Key Terms

- **Plaintext:** The original, readable message.
    
- **Ciphertext:** The encrypted message.
    
- **Encryption key:** The secret value used to encrypt and decrypt data.
    
- **Block size:** The number of bits processed by the block cipher at once.
    
- **Mode of operation:** A method that specifies how a block cipher processes messages longer than one block.
    
- **Initialization Vector (IV):** A value used by certain modes to initialize encryption. It is not normally secret, but it must satisfy the mode's requirements for uniqueness or unpredictability.
    
- **Padding:** Extra bits or bytes added to a message so that its length is a multiple of the block size, when required by the mode.
    

## 2. DES (Data Encryption Standard)

- DES is one of the most historically important block ciphers.
    
- It operates on **64-bit blocks** and uses a **56-bit effective key**. The key is commonly represented as 64 bits, including 8 parity bits.
    
- DES uses a 16-round Feistel structure.
    
- During each round, the data is divided into two halves and processed using a round key.
    
- Decryption uses the same overall structure as encryption, but applies the round keys in reverse order.
    
- DES helped establish many principles used in the study and design of modern block ciphers.
    

### Why is DES no longer secure?

- Its 56-bit effective key is too short to resist modern brute-force attacks.
    
- An attacker can systematically try possible keys until the correct one is found.
    
- DES has been superseded by more secure algorithms, particularly AES.
    
- **Triple DES (3DES)** applies DES multiple times to improve security, but it is now deprecated for most modern applications.
    

**Exam point:** DES is historically significant, but AES is the preferred modern block cipher for most new applications.

## 3. Modes of Operation

A block cipher such as DES or AES encrypts a single fixed-size block. A mode of operation determines how to encrypt a longer message containing several blocks.

The main modes covered here are:

1. Electronic Codebook (ECB)
    
2. Cipher Block Chaining (CBC)
    
3. Cipher Feedback (CFB)
    
4. Output Feedback (OFB)
    
5. Counter (CTR)
    

### Comparison Table

|Mode|Main mechanism|IV/nonce requirement|Parallel encryption|Error behaviour|
|---|---|---|---|---|
|ECB|Encrypts each block independently|None|Yes|Error affects one block|
|CBC|XORs plaintext with previous ciphertext|Unpredictable IV|No|Affects parts of two blocks|
|CFB|Encrypts previous ciphertext to generate a mask|Unique/unpredictable IV, depending on specification|No|Propagates to subsequent segments|
|OFB|Repeatedly encrypts the previous cipher output|Unique IV|No|Typically affects only corresponding bits|
|CTR|Encrypts successive counter values|Unique nonce/counter inputs|Yes|Typically affects only corresponding bits|

_These are confidentiality modes. None of these five modes, by itself, provides reliable message authentication or integrity._

---

## 4. Electronic Codebook (ECB)

### Definition

- ECB encrypts each plaintext block independently using the same secret key.
    
- Every block is encrypted separately, without using the previous plaintext or ciphertext blocks.
    

### How it works

For each block:

`C_i = E_K(P_i)`

Where:

- `P_i` = plaintext block.
    
- `C_i` = ciphertext block.
    
- `E_K` = encryption using key `K`.
    

Decryption:

`P_i = D_K(C_i)`

### Example

If a message contains three blocks:

- Block 1 → Encrypt with key K → Ciphertext 1
    
- Block 2 → Encrypt with key K → Ciphertext 2
    
- Block 3 → Encrypt with key K → Ciphertext 3
    

Each block is processed independently.

### Advantages

- Simple to implement.
    
- Encryption and decryption can be performed in parallel.
    
- Errors in one ciphertext block do not affect other blocks during decryption.
    
- Suitable for encrypting a single independent block, such as a cryptographic key, provided the surrounding protocol is designed appropriately.
    

### Disadvantages

- Identical plaintext blocks produce identical ciphertext blocks when encrypted with the same key.
    
- Repeated patterns in plaintext remain visible in the ciphertext.
    
- An attacker may identify patterns or infer information about the message.
    
- Blocks can be rearranged, removed or duplicated without the mode itself detecting the change.
    
- It does not provide authentication or integrity.
    

### Uses

- Limited applications involving a single independent block.
    
- Not recommended for encrypting ordinary multi-block messages.
    

**Exam point:** ECB is generally unsuitable for messages containing multiple blocks because it reveals patterns.

---

## 5. Cipher Block Chaining (CBC)

### Definition

- CBC combines each plaintext block with the previous ciphertext block using XOR before encryption.
    
- The first plaintext block is combined with an Initialization Vector (IV).
    
- This creates a dependency between consecutive blocks.
    

### How it works

For the first block:

`C_1 = E_K(P_1 XOR IV)`

For subsequent blocks:

`C_i = E_K(P_i XOR C_(i-1))`

Decryption:

`P_i = D_K(C_i) XOR C_(i-1)`

For the first block, the previous ciphertext is replaced by the IV.

### Key characteristics

- The IV should be unpredictable for standard CBC encryption and must be communicated to the receiver.
    
- The IV does not need to be secret.
    
- Identical plaintext blocks can produce different ciphertext blocks because the previous ciphertext changes.
    
- Padding is normally required if the message length is not a multiple of the block size.
    

### Advantages

- Hides repeated plaintext patterns more effectively than ECB.
    
- Provides confidentiality when implemented correctly.
    
- Has been widely used for general-purpose block-oriented encryption.
    

### Disadvantages

- Encryption is sequential because each block depends on the previous ciphertext.
    
- A corrupted ciphertext block affects the decrypted block and flips corresponding bits in the next plaintext block.
    
- Padding and padding-validation errors can create security vulnerabilities.
    
- CBC alone does not provide authentication or integrity.
    
- An attacker may modify ciphertext and cause controlled changes in decrypted data.
    

### Uses

- Historically used for general-purpose block-oriented data transmission and file encryption.
    
- Often encountered in legacy cryptographic systems.
    

**Exam point:** CBC uses XOR with the previous ciphertext block. The first block uses an IV.

---

## 6. Cipher Feedback (CFB)

### Definition

- CFB converts a block cipher into a stream-like encryption mode.
    
- The block cipher encrypts the IV or previous ciphertext to generate output that is XORed with the plaintext.
    
- It can process data in segments of `s` bits at a time, where `s` is the segment size.
    

### How it works

For full-block CFB:

`C_1 = P_1 XOR E_K(IV)`

`C_i = P_i XOR E_K(C_(i-1))`

The ciphertext is fed back into the encryption algorithm to generate the next output.

### Key characteristics

- Uses the block cipher's encryption function for both encryption and decryption.
    
- Can operate on smaller segments rather than requiring a complete block of plaintext at once.
    
- The IV must meet the mode's security requirements.
    
- Padding is not normally required because data can be processed in segments.
    

### Advantages

- Suitable for stream-oriented transmission.
    
- Can encrypt data as it becomes available.
    
- Does not require padding.
    
- Can be useful in systems where data is transmitted in small units.
    

### Disadvantages

- Encryption is sequential because the next stage depends on previous ciphertext.
    
- Transmission errors can affect the current segment and subsequent segments.
    
- A corrupted ciphertext segment may corrupt the corresponding plaintext segment and introduce errors in the next segment or block, depending on the configuration.
    
- Does not provide authentication or integrity by itself.
    

### Uses

- General-purpose stream-oriented transmission.
    
- Legacy communication systems where data arrives in small units.
    

**Exam point:** CFB feeds back the previous ciphertext, whereas OFB feeds back the previous cipher output.

---

## 7. Output Feedback (OFB)

### Definition

- OFB converts a block cipher into a synchronous stream cipher.
    
- Instead of feeding ciphertext back into the encryption algorithm, OFB feeds back the previous output of the block cipher.
    
- The generated output is XORed with plaintext to create ciphertext.
    

### How it works

First, generate the initial output:

`O_1 = E_K(IV)`

Then generate subsequent outputs:

`O_i = E_K(O_(i-1))`

Encrypt plaintext:

`C_i = P_i XOR O_i`

Decrypt ciphertext:

`P_i = C_i XOR O_i`

The same generated output sequence is used for encryption and decryption.

### Key characteristics

- The output sequence depends on the key and IV, not on the plaintext or ciphertext.
    
- The same key and IV must never be reused for different messages.
    
- The output sequence can be generated before the plaintext is available.
    
- Padding is not required when the stream can be truncated to the message length.
    

### Advantages

- Transmission errors do not propagate through the output-generation process.
    
- A flipped ciphertext bit causes the corresponding plaintext bit to flip, without corrupting the remaining bits.
    
- Suitable for noisy communication channels.
    
- Encryption and decryption use XOR with a generated output sequence.
    

### Disadvantages

- The IV must not be reused with the same key.
    
- The output sequence must be generated sequentially.
    
- It does not provide authentication or integrity.
    
- Synchronisation problems can cause the receiver to use the wrong part of the output sequence.
    

### Uses

- Stream-oriented communication.
    
- Historically useful for noisy channels, including certain satellite communication applications.
    

**Exam point:** OFB feeds back the previous encryption output, not the previous ciphertext.

---

## 8. Counter Mode (CTR)

### Definition

- CTR converts a block cipher into a stream-like mode by encrypting a sequence of counter values.
    
- Each encrypted counter value produces a block of pseudorandom output, which is XORed with a plaintext block.
    
- The counter is incremented for each subsequent block.
    

### How it works

For each block:

`O_i = E_K(Counter_i)`

`C_i = P_i XOR O_i`

Decryption:

`P_i = C_i XOR E_K(Counter_i)`

The counter values must be unique for each block encrypted under the same key.

### Key characteristics

- The counter inputs are generated independently of the plaintext and ciphertext.
    
- Different blocks can be encrypted and decrypted in parallel.
    
- The output can be generated before the plaintext arrives.
    
- Padding is not required.
    
- The counter must be designed to avoid repeating counter inputs under the same key.
    

### Advantages

- High-speed encryption and decryption.
    
- Supports parallel processing.
    
- Efficient for hardware and software implementations.
    
- Allows random access to individual blocks.
    
- Bit errors do not propagate to other plaintext blocks.
    
- Suitable for applications requiring high throughput.
    

### Disadvantages

- Reusing the same nonce/counter inputs with the same key can seriously compromise confidentiality.
    
- Counter management must prevent repeated inputs and counter overflow.
    
- Does not provide authentication or integrity.
    
- Ciphertext modification can flip corresponding plaintext bits.
    

### Uses

- High-speed data transmission.
    
- Storage encryption designs.
    
- Network protocols and other applications requiring parallel processing.
    

**Exam point:** CTR encrypts counter values, not plaintext blocks directly. The resulting output is XORed with the plaintext.

---

## 9. Important Differences Between CFB, OFB and CTR

These modes can all make a block cipher behave like a stream cipher, but they generate their output differently.

|Feature|CFB|OFB|CTR|
|---|---|---|---|
|Input to encryption function|Previous ciphertext (or IV initially)|Previous cipher output (or IV initially)|Counter value|
|Feedback mechanism|Ciphertext feedback|Output feedback|No feedback from message data|
|Parallel encryption|No|No|Yes|
|Padding required|No|No|No|
|Effect of a ciphertext bit error|Can propagate to later segments|Only corresponding plaintext bit|Only corresponding plaintext bit|
|Repeated input danger|IV reuse can compromise security|IV reuse can repeat output sequence|Repeated nonce/counter inputs compromise security|

### Memory aid

- **ECB:** Every block is independent.
    
- **CBC:** Ciphertext is chained.
    
- **CFB:** Ciphertext is fed back.
    
- **OFB:** Output is fed back.
    
- **CTR:** Counter is encrypted.
    

---

## 10. XOR in Block Cipher Modes

XOR means exclusive OR. It produces `1` when the two input bits differ and `0` when they are the same.

|A|B|A XOR B|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

Important properties:

- `A XOR 0 = A`
    
- `A XOR A = 0`
    
- `A XOR B XOR B = A`
    

These properties explain why stream-like modes can use XOR for both encryption and decryption.

For example:

- Encryption: `C = P XOR O`
    
- Decryption: `P = C XOR O`
    

Because XORing with the same value twice restores the original plaintext.

---

## 11. Security Considerations

- **Confidentiality:** Prevents unauthorised parties from learning the message.
    
- **Integrity:** Detects whether data has been modified.
    
- **Authentication:** Verifies the source or authenticity of a message.
    
- **Nonce/IV reuse:** Reusing values where uniqueness is required can expose relationships between plaintexts or otherwise undermine security.
    
- **Unauthenticated encryption:** ECB, CBC, CFB, OFB and CTR do not independently authenticate ciphertext.
    
- **Authenticated encryption:** Modern applications should generally prefer an authenticated-encryption mode, such as AES-GCM or ChaCha20-Poly1305, when supported by the protocol.
    

### Why is CTR nonce reuse dangerous?

If the same key and counter inputs are reused, the same output sequence is generated:

`C_1 = P_1 XOR O`

`C_2 = P_2 XOR O`

Therefore:

`C_1 XOR C_2 = P_1 XOR P_2`

The output sequence cancels out, revealing a relationship between the two plaintexts. If an attacker knows or guesses one plaintext, information about the other may be recovered.

---

## 12. Padding

- Block ciphers have a fixed block size.
    
- If a mode requires complete blocks and the message is too short or its length is not a multiple of the block size, padding may be necessary.
    
- **ECB and CBC** commonly use padding schemes such as PKCS#7.
    
- **CFB, OFB and CTR** can process partial final blocks and normally do not require padding.
    
- Padding must be handled securely because incorrect padding validation can expose vulnerabilities.
    

---

## 13. Test Yourself

### Short-answer questions

1. What is a block cipher?
    
2. What are the block size and effective key size of DES?
    
3. Why is DES considered insecure today?
    
4. Why does ECB reveal patterns in plaintext?
    
5. What is the purpose of the IV in CBC?
    
6. Explain how CBC combines plaintext and ciphertext.
    
7. What is the difference between CFB and OFB?
    
8. How does CTR generate ciphertext?
    
9. Which modes support parallel encryption?
    
10. Which modes normally require padding?
    
11. Why is nonce reuse dangerous in CTR?
    
12. Why do these modes not guarantee message integrity?
    

### Model answers

1. A symmetric-key algorithm that encrypts fixed-size plaintext blocks into ciphertext blocks.
    
2. DES uses 64-bit blocks and a 56-bit effective key.
    
3. Its key is too short to resist modern brute-force attacks.
    
4. Identical plaintext blocks produce identical ciphertext blocks under the same key.
    
5. CBC uses an unpredictable IV to initialise encryption of the first block.
    
6. CBC XORs each plaintext block with the previous ciphertext block before encryption; the first block uses the IV.
    
7. CFB feeds back ciphertext, while OFB feeds back the previous encryption output.
    
8. CTR encrypts successive counter values and XORs the results with plaintext.
    
9. ECB and CTR support parallel encryption; CBC, CFB and OFB have sequential dependencies.
    
10. ECB and CBC commonly require padding when complete blocks are required; CFB, OFB and CTR do not normally require it.
    
11. Reuse repeats the output sequence, allowing attackers to obtain relationships between plaintexts.
    
12. They provide confidentiality but do not independently detect malicious modification or authenticate the sender.
    

### Exam tip

When asked to compare modes, explain **what is fed into the encryption function, how blocks depend on each other, whether parallel processing is possible, how errors propagate, and what IV/nonce requirements apply**. These points distinguish the modes more clearly than memorising their names alone.


# Diffie–Hellman (DH) Key Exchange

## 1. Definition

**Diffie–Hellman (DH) key exchange** is a cryptographic technique first published by Whitfield Diffie and Martin Hellman in **1976**.

It allows two parties to establish a **shared secret key over an insecure communication channel**, even if an attacker can observe all the messages exchanged.

The shared secret can then be used to encrypt and decrypt messages using symmetric encryption.

## 2. Important Properties

### Property 1: Both parties contribute to the shared secret

- Each party chooses their own private value.
    
- They exchange values derived from their private values.
    
- Each party combines the received value with their own private value to calculate the same shared secret.
    
- Neither party can independently calculate the shared secret from the public information alone, assuming the private values remain secret.
    

### Property 2: An eavesdropper cannot feasibly calculate the shared secret

- A third party can observe all the messages transmitted.
    
- The public parameters and exchanged values do not reveal the private values efficiently.
    
- Recovering the shared secret is computationally infeasible when suitable parameters and a secure implementation are used.
    

> **Key idea:** The parties can agree on a shared secret without transmitting the secret itself.

## 3. How Diffie–Hellman Works

Alice and Bob want to establish a shared secret.

1. They publicly agree on a base (g) and a large prime number (p).
    
2. Alice chooses a private number (a).
    
3. Bob chooses a private number (b).
    
4. Alice calculates (A=g^a\bmod p) and sends (A) to Bob.
    
5. Bob calculates (B=g^b\bmod p) and sends (B) to Alice.
    
6. Alice calculates the shared secret (S=B^a\bmod p).
    
7. Bob calculates the shared secret (S=A^b\bmod p).
    

Both arrive at the same result:

$$S=g^{ab}\bmod p$$

The private values (a) and (b) are never sent across the network.

## 4. Worked Example (Small Numbers)

For illustration, suppose the public values are:

$$p=23,\qquad g=5$$

Alice chooses private value (a=6):

$$A=5^6\bmod23=8$$

Bob chooses private value (b=15):

$$B=5^{15}\bmod23=19$$

They exchange (A=8) and (B=19).

**Alice calculates:**

$$S=19^6\bmod23=2$$

**Bob calculates:**

$$S=8^{15}\bmod23=2$$

Therefore, both parties obtain the same shared secret:

$$\boxed{S=2}$$

_Note: These tiny numbers are insecure and are used only to demonstrate the mathematics._

## 5. Security Limitation

Diffie–Hellman by itself does **not authenticate the parties**. Without authentication, an attacker could perform a _man-in-the-middle attack_, establishing separate shared secrets with Alice and Bob.

Real-world protocols use authentication alongside key exchange to protect against this attack.

## 6. Exam Summary

- **Introduced:** 1976, by Diffie and Hellman.
    
- **Purpose:** Establish a shared secret over an insecure channel.
    
- **Private values:** Kept secret by each party.
    
- **Public values:** Can be exchanged openly.
    
- **Security basis:** The computational difficulty of reversing the relevant modular exponentiation.
    
- **Main limitation:** Basic Diffie–Hellman does not authenticate the participants.
    

**Exam-ready answer:** Diffie–Hellman allows two parties to establish a shared secret over an insecure channel without transmitting the secret itself. An eavesdropper can observe the exchanged public values but cannot feasibly calculate the shared secret when secure parameters are used.