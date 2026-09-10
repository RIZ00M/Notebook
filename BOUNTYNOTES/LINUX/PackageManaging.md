# Package Managing

## Core Commands

| Command | Purpose |
|---|---|
| `sudo add-apt-repository` | Adds a repository to apt's sources |
| `dpkg` | Low-level package manager (installs/manages `.deb` files directly) |

## Manual Repository Add — Example: Sublime Text 3

1. **Add the GPG key**

   ```bash
   wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
   ```

   Adds Sublime Text 3's repository key. Good practice is to keep a separate file for every different community/3rd-party repository you add.

2. **Create a sources file**

   Create a file named `sublime-text.list` in `/etc/apt/sources.list.d/` and add the repository info to it — using Nano or a text editor of your choice:

   ```
   deb https://download.sublimetext.com/ apt/stable/
   ```

3. **Update apt**

   ```bash
   apt update
   ```

   Refreshes apt so it recognises the new repository entry.

4. **Install the package**

   ```bash
   apt install sublime-text
   ```

## Removing Packages

Reverse the process:

| Method | Command |
|---|---|
| Remove a PPA | `add-apt-repository --remove ppa:PPA_Name/ppa` |
| Remove manually | Delete the file previously added to `/etc/apt/sources.list.d/` |
| Uninstall the software | `apt remove [software-name-here]` (e.g. `apt remove sublime-text`) |
