# 03. Automating SSH Connections with Config Aliases

In this lesson, you will configure a local SSH host alias in `~/.ssh/config` to bypass typing IP addresses, usernames, and key parameters every time you connect.

---

I know you are also tried like me to write ssh ubuntu@16.171.250.78 again and again going to aws-console 
Let's automate it:
### ssh aws 

## 🛠️ Step-by-Step Configuration

### 1. Create or edit your SSH configuration file

Open the local SSH configuration file using `nano`:

```bash
nano ~/.ssh/config
```

nano: A lightweight, terminal-based text editor built into Linux.

~/.ssh/config: The user-level SSH configuration file used to define host shortcuts, default ports, user settings, and key paths.

### 2. Define the host alias entry
Add the following block to your ~/.ssh/config file:

```bash
Host aws
    HostName 16.171.250.78
    User ubuntu
    IdentityFile ~/.ssh/id_ed25519
```

--  `Host aws:` Sets the short alias/shortcut name (aws) used when running ssh <alias>.

--  `HostName:` Defines the remote target (Public IPv4 address or domain name).

--  `User:` Specifies the remote Linux username (ubuntu).

--  `IdentityFile:` Specifies the exact private key to authenticate the connection (~/.ssh/id_ed25519).

### 3. Set strict file permissions
Apply 600 permissions so SSH can safely read the configuration file:

```bash
chmod 600 ~/.ssh/config
```
`chmod 600:` Restricts permissions so only the file owner has read and write access `(-rw-------)`. SSH security protocols automatically reject config files with open permissions.

### 4. Connect using your new alias
Test the shortcut from your terminal:

```bash
ssh aws
```
