# Telnet

The **TELNET (Teletype Network)** protocol is a network protocol for remote terminal connection. In simpler words, telnet — a TELNET client — allows you to connect to and communicate with a remote system and issue text commands. Although initially it was used for remote administration, telnet can be used to connect to any server listening on a TCP port number.

## Common Servers

| Server | Default Port | Behaviour |
|---|---|---|
| Echo server | 7 | Echoes everything you send it |
| Daytime server | 13 | Replies with the current day and time |
| Web (HTTP) server | 80 | Serves web pages |

## Example: Echo Server (Port 7)

```
user@TryHackMe$ telnet 10.82.154.223 7
Trying 10.82.154.223...
Connected to 10.82.154.223.
Escape character is '^]'.
Hi
Hi
How are you?
How are you?
Bye
Bye
^]

telnet> quit
Connection closed.
```

> **To close the connection:** press `CTRL + ]` simultaneously, then type `quit`.

## Example: Web (HTTP) Server (Port 80)

After connecting to port 80:

1. Issue the command `GET / HTTP/1.1`
2. Specify the host — anything goes, such as `Host: telnet.thm`
3. Press **Enter twice**, so your last input line is a blank line

```
user@TryHackMe$ telnet 10.82.154.223 80
Trying 10.82.154.223...
Connected to 10.82.154.223.
Escape character is '^]'.
GET / HTTP/1.1
Host: telnet.thm

HTTP/1.1 200 OK
Content-Type: text/html
[...]

Connection closed by foreign host.
```
