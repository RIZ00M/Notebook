<div align="center">

# 📓 RIZ00M's Notebook

### A personal cheat-sheet vault for cybersecurity, networking & scripting

![Markdown](https://img.shields.io/badge/docs-markdown-blue?style=for-the-badge&logo=markdown)
![TryHackMe](https://img.shields.io/badge/source-TryHackMe-red?style=for-the-badge&logo=tryhackme)
![Status](https://img.shields.io/badge/status-actively%20updated-brightgreen?style=for-the-badge)

*My Personal Notebook accessible to anyone who wants it!*

</div>

---

## 📖 Table of Contents

| # | Topic | What's Inside |
|---|---|---|
| 🎯 | [Reconnaissance](#-reconnaissance) | Enumeration & discovery |
| 🔓 | [Bruteforcing](#-bruteforcing) | Credential attacks |
| 💉 | [Injection](#-injection) | HTML / JS injection payloads |
| 🌐 | [Networking](#-networking) | OSI Model, Telnet |
| 🌍 | [HTTP](#-http) | Methods, status codes, cookies |
| 🧬 | [DNS](#-dns) | Record types & lookups |
| 🐍 | [Python](#-python) | Quick scripting & file serving |
| 📜 | [JavaScript](#-javascript) | DOM manipulation & demos |
| 🐧 | [Linux](#-linux) | Commands, cron, packages |
| 🪟 | [Windows](#-windows) | CMD, PowerShell, Active Directory |
| 🔧 | [Git](#-git) | Repo housekeeping |

---

## 🎯 Reconnaissance

Enumeration commands and directory brute-forcing.

| File | Description |
|---|---|
| [`Gobuster.md`](BOUNTYNOTES/RECONSAINCE/Gobuster.md) | Directory/file brute-forcing against a web server |

## 🔓 Bruteforcing

Credential attacks against live services.

| File | Description |
|---|---|
| [`Hydra.md`](BOUNTYNOTES/BRUTEFORCING/Hydra.md) | Brute-forcing HTTP POST login forms |

## 💉 Injection

Payloads for exploiting unsanitised user input.

| File | Description |
|---|---|
| [`HTMLPayloads.md`](BOUNTYNOTES/INJECTION/HTMLPayloads.md) | HTML injection basics + link injection payload |
| [`JavaScriptPayloads.md`](BOUNTYNOTES/INJECTION/JavaScriptPayloads.md) | JS payload to hijack page elements |

## 🌐 Networking

Core networking theory and legacy protocols.

| File | Description |
|---|---|
| [`OSIModel.md`](BOUNTYNOTES/NETWORKING/OSIModel.md) | The 7 OSI layers, MAC/IP breakdowns, port table |
| [`Telnet.md`](BOUNTYNOTES/NETWORKING/Telnet.md) | Raw TCP connections via Telnet (echo, daytime, HTTP) |

## 🌍 HTTP

The nuts and bolts of the web's core protocol.

| File | Description |
|---|---|
| [`CoreHTTPCommands.md`](BOUNTYNOTES/HTTP/CoreHTTPCommands.md) | HTTP verbs & anatomy of a request |
| [`HTTPMethods.md`](BOUNTYNOTES/HTTP/HTTPMethods.md) | GET / POST / PUT / DELETE explained |
| [`HTTPStatusCodes.md`](BOUNTYNOTES/HTTP/HTTPStatusCodes.md) | Full status code reference table |
| [`CookiesFlow.md`](BOUNTYNOTES/HTTP/CookiesFlow.md) | How cookies are set & sent, step by step |

## 🧬 DNS

Domain resolution and record types.

| File | Description |
|---|---|
| [`CNAME.md`](BOUNTYNOTES/DNS/CNAME.md) | CNAME records & `nslookup` example |

## 🐍 Python

Fast scripting for file transfer.

| File | Description |
|---|---|
| [`ServingFiles.md`](BOUNTYNOTES/PYTHON/ServingFiles.md) | Host & retrieve files with `http.server` / `wget` |

## 📜 JavaScript

DOM basics and a couple of demo scripts.

| File | Description |
|---|---|
| [`JavaScriptDemo.md`](BOUNTYNOTES/JAVASCRIPT/JavaScriptDemo.md) | Basic DOM manipulation example |
| [`JavaScriptGuesser.md`](BOUNTYNOTES/JAVASCRIPT/JavaScriptGuesser.md) | Console number-guessing game (+ source) |

## 🐧 Linux

Everyday commands, scheduling, and package management.

| File | Description |
|---|---|
| [`RootDirectories.md`](BOUNTYNOTES/LINUX/RootDirectories.md) | Filesystem layout: `/etc`, `/var`, `/root`, `/tmp` |
| [`LinuxCMDs.md`](BOUNTYNOTES/LINUX/LinuxCMDs.md) | Shells, permissions, navigation, bash scripting |
| [`CronTabs.md`](BOUNTYNOTES/LINUX/CronTabs.md) | Scheduling recurring tasks |
| [`FileTransfering.md`](BOUNTYNOTES/LINUX/FileTransfering.md) | `wget` / `scp` file transfer |
| [`PackageManaging.md`](BOUNTYNOTES/LINUX/PackageManaging.md) | `apt` repos, install/remove packages |

## 🪟 Windows

Command line tools, PowerShell, and Active Directory.

| File | Description |
|---|---|
| [`CMDs.md`](BOUNTYNOTES/WINDOWS/CMDs.md) | Command Prompt reference |
| [`Powershell.md`](BOUNTYNOTES/WINDOWS/Powershell.md) | PowerShell cmdlets, piping, comparison operators |
| [`ActiveDirectoryPowerShell.md`](BOUNTYNOTES/WINDOWS/ActiveDirectoryPowerShell.md) | Resetting AD user passwords |
| [`Tools.md`](BOUNTYNOTES/WINDOWS/Tools.md) | Built-in Windows admin tools (`msconfig`, `regedit`, etc.) |

## 🔧 Git

Repo commands.

| File | Description |
|---|---|
| [`Restructure.md`](BOUNTYNOTES/GIT/Restructure.md) | Resetting a repo's history and force-pushing `main` |

