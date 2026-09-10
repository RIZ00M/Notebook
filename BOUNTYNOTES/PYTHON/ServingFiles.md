# Serving & Retrieving Files with Python

A quick way to transfer files between machines using Python's built-in HTTP server.

## Host a Server

Run this in the directory containing the file(s) you want to share:

```bash
python3 -m http.server
```

## Get the File (from the other machine)

```bash
wget http://MACHINE_IP:8000/myfile
```

| Step | Command | Purpose |
|---|---|---|
| 1 | `python3 -m http.server` | Starts a simple HTTP server (default port 8000) in the current directory |
| 2 | `wget http://MACHINE_IP:8000/myfile` | Downloads `myfile` from the hosting machine |
