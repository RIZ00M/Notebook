## Example Usage

`john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`

`john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt`

`john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt`

Single Crack Mode

`john --single --format=[format] [path to file]`

In this mode, John uses only the information provided in the username to try and work out possible passwords heuristically by slightly changing the letters and numbers contained within the username.

`john --list=formats | grep -iF "md5"`

Finding Root Password

- `unshadow`: Invokes the unshadow tool
- `[path to passwd]`: The file that contains the copy of the `/etc/passwd` file you’ve taken from the lab machine
- `[path to shadow]`: The file that contains the copy of the `/etc/shadow` file you’ve taken from the lab machine

`unshadow local_passwd local_shadow > unshadowed.txt`

