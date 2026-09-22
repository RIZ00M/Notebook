# Gobuster – Directory Bruteforcing

Gobuster is used to discover hidden directories/files on a web server by brute-forcing against a wordlist.

## Command

```bash
gobuster dir -u http://154.57.164.82:31081 -w /usr/share/wordlists/dirbuster/directory-list.txt
```

| Flag | Meaning |
|---|---|
| `dir` | Run gobuster in directory/file brute-forcing mode |
| `-u` | Target URL |
| `-w` | Path to the wordlist to use |

## Checking Available Wordlists

```bash
ls -lah /usr/share/wordlists/dirbuster/
```

Lists the wordlists available in the `dirbuster` directory (with human-readable file sizes and permissions).
