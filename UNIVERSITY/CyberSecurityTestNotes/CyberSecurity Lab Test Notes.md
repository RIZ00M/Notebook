# Week 1 Lab Notes

![[Pasted image 20261028142148.png]]

**Inspecting Packets**
– Frame: General packet information, such as timestamp and packet size.  
– Ethernet: The link-layer protocol.  
– IP: The network-layer protocol, responsible for routing the packet.  
– TCP: The transport-layer protocol, ensuring reliable delivery.

![[Pasted image 20261028142622.png]]

**Calculating Overhead**
– Ethernet header  (14)
![[Pasted image 20261028143339.png]]
![[Pasted image 20261028143510.png]]![[Pasted image 20261028143519.png]]![[Pasted image 20261028143533.png]]
– IP header  (20)
![[Pasted image 20261028143402.png]]
– TCP header (20)  
![[Pasted image 20261028143426.png]]
– HTTP data (1281)
![[Pasted image 20261028143732.png]]

![[Pasted image 20261028142950.png]]

## Total Header = 14 + 20 + 20 = 54 Bytes

## 54 / 1281 x 100 = 4.2% (Header / Length * 100 = Overhead)

# Week 2 DES & AES

This lab uses OpenSSL

**Commands**
Version: openssl version
Help: openssl -h 
List Ciphers: openssl ciphers -v
Benchmarking: openssl speed

## Encrypting DES Using OpenSSL
Generate DES Key: openssl rand -out des_keySS 56
Generate AES Key: openssl rand -out aes_keySS 128

**openssl DES -e -kfile des_keySS -in SystemSec.txt -out SystemSec-enc.enc**
o des is the name of the cipher  
o when we pass -e switch to the cipher, it will encrypt the file.  
o -kfile is for specifying the key file  
o des_keySS is the name of the key file  
o -in is for input  
o SystemSec.txt input file name  
o -out is for output  
o SystemSec-enc.enc output file name

![[Pasted image 20261028144833.png]]

## Decrypting DES Using SSL
**openssl DES -d -kfile des_keySS -in SystemSec-enc.enc -out SystemSec-dec.dec**
o des is the name of the cipher  
o when we pass -d switch to the cipher, it will decrypt the file.  
o -kfile is for specifying the key file  
o des_keySS is the name of the key file  
o -in is for input  
o SystemSec-enc.enc is the input file name  
o -out is for output file  
o SystemSec-dec.dec output file name

![[Pasted image 20261028145217.png]]

## Encrypting With AES

6 Modes

**Encryption**
openssl aes-256-cbc -e -in plaintext.txt -out encrypted.enc  
openssl aes-256-ecb -e -in plaintext.txt -out encrypted.enc  
openssl aes-256-cfb -e -in plaintext.txt -out encrypted.enc  
openssl aes-256-ofb -e -in plaintext.txt -out encrypted.enc  
openssl aes-256-ctr -e -in plaintext.txt -out encrypted.enc

**Decryption**
openssl aes-256-cbc -d -in encrypted.enc -out plaintext.txt  
openssl aes-256-ecb -d -in encrypted.enc -out plaintext.txt  
openssl aes-256-cfb -d -in encrypted.enc -out plaintext.txt  
openssl aes-256-ofb -d -in encrypted.enc -out plaintext.txt
openssl aes-256-ctr -d -in encrypted.enc -out plaintext.txt

**Encryption**
openssl rand -out aes_keySS 128 
openssl aes256 -e -kfile aes_keySS -in SystemSec.txt -out SystemSec-aes.enc

Decryption
**openssl aes256 -d -kfile aes_keySS -in SystemSec-aes.enc -out SystemSec-aes.dec**

![[Pasted image 20261028150301.png]]

Task 1
(a) Generate AES Key of 256-bits: openssl rand -out aes_keySS 256
(b) Create a Sec.txt file with some text: echo "Security Test" > Sec.txt
(c) Encrypt it with AES CTR mode & Calculate MD5: aes-256-ctr -e -kfile aes_keySS -in Sec.txt -out encrypted.enc  | md5sum encrypted.enc
(d) Now delete some contents and calculate MD5: nano encrypted.enc | md5sum encrypted.enc
(e) Compare values: The file's hash changes whenever it is encrypted or contents are changed.

![[Pasted image 20261028150847.png]]

# Week 3 Private & Public Asymmetric Encryption

**1st Person Generate Private Key**
openssl genrsa -aes256 -out private.pem 1024

Prompted, Password is 123456 or anything

**1st Person Generate Public Key**
openssl rsa -in private.pem -pubout -out public.pem

**1st Person Write to file**
echo "Hello, World " > Secretfile.txt

**2nd Person will encrypt using public key**
openssl pkeyutl -encrypt -pubin -inkey public.pem -in Secretfile.txt -out encrypted.txt

**1st Person will decrypt using their private key**
openssl pkeyutl -decrypt -inkey private.pem -in encrypted.txt -out Secretfile2.txt

1. Create an RSA 1024-bit long private key  
2. Generate the public key from the private key  
![[Pasted image 20261028153302.png]]
3. Next create a file Secrets.txt, and write some text into it  
4. Encrypt the file with the public key and then decrypt it using your private key. Did you get the same text?
![[Pasted image 20261028153614.png]]

## Signing Documents

**Signing a document**
openssl dgst -sha256 -sign private.pem -out sign.sha256 Secretfile.txt
**A binary signature file named sign.sha256 is also generated alongside this command**

**Display the signature in Base64 Format**
openssl base64 -in sign.sha256 -out signature

**Verify Signature**
openssl base64 -d -in signature -out sign.sha256

**Verify Public Key**
openssl dgst -sha256 -verify public.pem -signature sign.sha256 Secretfile.txt

![[Pasted image 20261028155047.png]]

1. Generate a 1024-bit RSA private key  
2. Next generate the public key from the private key  
3. Digitally sign the document (i.e. contract.txt)  
4. Then verify the integrity of the digitally signed document (i.e. contract.txt)  
5. Next make some changes to the contract.txt and again try to verify the document
![[Pasted image 20261028160001.png|636]]
![[Pasted image 20261028155912.png]]