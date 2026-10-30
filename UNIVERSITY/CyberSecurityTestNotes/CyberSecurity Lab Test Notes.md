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

# Week 4 HASHING and Integrity Check

Here is an example of a trusted source to verify file hashes.
https://openssl-library.org/source/old/1.0.2/

1. Download another OpenSSL and its checksum file.  
	![[Pasted image 20261028192331.png]]
2. Repeat the above process and check both the checksum values are the same or not?  
	Yes, both are the same.  
3. What we learnt from the above process? The file has not been changed during the  
	download process. 
	Authentic file.  
4. Open the openssl-1.0.2u.tar.gz file in 7z or WinRAR and delete any file from its  
	contents. Then calculate the checksum again. Is it the same? No Why? Because the  
	contents have been modified now

## Keyed Hash Message Authentication Code (HMAC)

**First Create a file** with contents
echo "Secret contents" > Secretfile.txt

openssl dgst -md5 -hmac "abcdef" Secretfile.txt

![[Pasted image 20261028193430.png]]

## TASK
1. Create a text file of any length  
2. Generate the hash value H1 for the file using HMAC (try using sha256 with HMAC).  
3. Flip one bit of the input file.  
4. Generate the hash value H2 for the modified file. 
5. Observe whether H1 and H2 are similar or not? **NO**

![[Pasted image 20261028193654.png]]

## Creating and Verifying Digital Signatures

**Create private key**
openssl genpkey -algorithm RSA -out private_key.pem

**Create public key**
openssl rsa -pubout -in private_key.pem -out public_key.pem

**Sign a file**
echo "This is a sensitive document that requires signing." > document.txt
openssl dgst -sha256 -sign private_key.pem -out signature.bin document.txt

**Verify signature using public key**
openssl dgst -sha256 -verify public_key.pem -signature signature.bin document.txt

**Change it's contents**
echo "This document has been modified." > document.txt
openssl dgst -sha256 -verify public_key.pem -signature signature.bin document.txt

![[PublicSignatures.png]]

## Signing a contract example

touch contract.pdf  
echo "This is a digital contract." > contract.pdf

**Signature**
openssl dgst -sha256 -sign private_key.pem -out contract_signature.bin contract.pdf

**Verify Document's Signature**
openssl dgst -sha256 -verify public_key.pem -signature contract_signature.bin contract.pdf

![[KaliSigning.png]]

# Week 5 IPV4 Tracing

**Select the first udp packet, what is the IP address of your computer?**
192.168.86.61
![[PCAP8.png]]

**What is the value in the time-to-live (TTL) field in this IPv4 datagram’s header?**
1
![[PCAP7.png]]

**What is the value in the upper layer protocol field in this IPv4 datagram’s header?** 
UDP
![[PCAP6.png]]

**How many bytes are in the IP header?**
20
![[PCAP5.png]]

**How many bytes are in the payload of the IP datagram? Explain how you determined the number of payload bytes**
36, 56-20. Total length - Header Length
![[PCAP3.png]]

**Has this IP datagram been fragmented? Explain how you determined whether or not the data-**  
**gram has been fragmented?**
No
![[PCAP2.png]]

## Applying filter to view specific traffic

Search for packets from a source to a destination with a specific protocol
ip.src==192.168.86.61 and ip.dst==128.119.245.12 and udp and !icmp

**Which fields in the IP datagram always change from one datagram to the next within this series of UDP segments sent by your computer destined to 128.119.245.12, via traceroute? Why?**
TTL, HeaderChecksum, Identification, as the packets contain different data.
![[PCAP1.png]]

**Which fields in this sequence of IP datagrams (containing UDP segments) stay constant? Why?**
- **Version**: Stays `4` because all packets use IPv4.
- **Header Length**: Stays `20 bytes` because the header contains no optional fields.
- **Source IP Address**: Stays the same because every packet originates from your computer.
- **Destination IP Address**: Stays the same because every packet targets the exact same destination (`128.119.245.12`).
- **Differentiated Services**: Stays `0x00` because no special quality-of-service priority is applied.
- **Protocol**: Stays `UDP (17)` because all datagrams encapsulate UDP segments.
- **Total Length**: Stays `56 bytes` because the payload size does not change between probes

**What is the upper layer protocol specified in the IP datagrams returned from the routers? **
ICMP

**Are the values in the Identification fields (across the sequence of all of ICMP packets from all of the  routers) similar in behavior to your answer to question 9 above?**
No. The Identification fields in packets from different routers vary because each router generates its own sequence, unlike the incrementing sequence from a single source

**Find the first IP datagram containing the first part of the segment sent to 128.119.245.12 sent by
your computer via the traceroute command to gaia.cs.umass.edu, after you specified that the trac-eroute packet length should be 3000.**
Yes, it has been fragmented across three IP datagrams (Packets 179, 180, and 183).

**What information in the IP header for this packet indicates whether this is the first fragment versus a latter fragment?**
The **More Fragments (MF)** flag set to 1.

**How many bytes are there in is this IP datagram (header plus payload)?**
1500 bytes (20-byte IP header + 1480-byte payload)