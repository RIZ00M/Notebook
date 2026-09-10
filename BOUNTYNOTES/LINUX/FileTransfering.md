# File Transferring

## Download a File

```bash
wget https://EXAMPLE.com/additional/linux-fundamentals/myfile.txt
wget -O X.zip 'X'
```

| Command | Purpose |
|---|---|
| `wget <url>` | Downloads a file from a URL, keeping its original filename |
| `wget -O X.zip 'X'` | Downloads and saves the file as `X.zip` (`-O` sets the output filename) |

## Transfer a File (SCP)

```bash
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
```

Copies `important.txt` to the `ubuntu` user's home directory on `192.168.1.30`, saving it as `transferred.txt`.

---

> **Note:** hosting a file with `python3 -m http.server` and pulling it down with `wget` is covered separately in `PYTHON/ServingFiles.md` — that content was identical here, so it isn't duplicated in this note.
