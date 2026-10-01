# Encrypting & Decrypting Lab

**Encrypting A File With DES**
openssl des -e -kfile des_keySS -in SystemSec.txt -out SystemSec-enc.enc  
let’s analyse this command:  
o des is the name of the cipher  
o when we pass -e switch to the cipher, it will encrypt the file.  
o -kfile is for specifying the key file  
o des_keySS is the name of the key file  
o -in is for input  
o SystemSec.txt input file name  
o -out is for output  
o SystemSec-enc.enc output file name

**Decrypting A File With DES**
openssl des -d -kfile des_keySS -in SystemSec-enc.enc -out SystemSec-dec.dec  
let’s analyse this command:  
o des is the name of the cipher  
o when we pass -d switch to the cipher, it will decrypt the file.  
o -kfile is for specifying the key file  
o des_keySS is the name of the key file  
o -in is for input  
o SystemSec-enc.enc is the input file name  
o -out is for output file  
o SystemSec-dec.dec output file name