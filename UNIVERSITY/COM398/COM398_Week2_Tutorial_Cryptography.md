## Brute Force Attack

Try every key possible until readable text is obtained from the ciphertext.

On average, the number of guesses is half the key space.

### Breaking the Caesar Cipher

Try all 25 keys using a brute force attack, e.g. `k = 1`, `k = 2`, `k = 3`, …

If the language of the plaintext is known, it is often possible to recognise the correct plaintext.

Questions raised on the slide:
- What if you don’t know the language?
- What if it is compressed?

![[KeyBruteForceTimes.png]]

## Playfair Cipher

A 5×5 matrix is constructed based on a keyword.

The keyword starts the matrix, with duplicate letters omitted. `I/J` is treated as one letter. The remainder of the matrix is filled with the other letters in alphabetical order.

### Playfair Cipher Rules

If the plaintext has a pair of identical letters, use a filler such as `x` before encrypting.

Example: `balloon = ba lx lo xo nx`

If a pair is on the same row, the ciphertext becomes the letters to the right.

`E(be) = CN`

If a pair is on the same column, the ciphertext becomes the letters below.

`E(tv) = NT`

Otherwise, each plaintext letter is replaced by the letter in the same row as itself and the same column as the other letter.

`E(ir) = AS`  
`E(ud) = QE`

### Playfair Cipher Analysis

Playfair improves on monoalphabetic ciphers because it is much harder to use statistics about relative frequency of letters and digrams.

However, it is still relatively easy to break using language/frequency analysis.

![[EncryptionMatrix.png]]
## Vigenère Cipher

The Vigenère cipher is an example of a **polyalphabetic cipher**.

A key determines which one of a set of **monoalphabetic ciphers** to use.

It uses the **26 Caesar ciphers**.

The keyword letter determines which Caesar cipher to use:

`a → k=0`  
`b → k=1`  
`c → k=2`  
…  

The main idea is that different letters of the keyword use different Caesar shifts.

This hides information about letter frequency because there can be **multiple ciphertext letters for each plaintext letter**.

However, some information can still be used by an attacker.

## Breaking the Vigenère Cipher

The attacker makes the following guesses/assumptions:

If a monoalphabetic code was used, the relative frequency of cipher letters should match those of the English language.

If the frequency does not match, assume Vigenère.

Repeated sequences of ciphertext are generated if 2 sequences of plaintext are an integer multiple of the keyword length apart.

With long ciphertext, the analyst can detect the length of the keyword.

The analyst can then analyse the individual monoalphabetic ciphers.

### Improving on Vigenère

This depends upon the construction of the key.

Use a very long keyword.

Concatenate the keyword with the plaintext to create a new keyword.

### Ultimate Security

Use a keyword the same length as the plaintext and with no statistical relationship with the plaintext.

This is called a **One-time pad**.

