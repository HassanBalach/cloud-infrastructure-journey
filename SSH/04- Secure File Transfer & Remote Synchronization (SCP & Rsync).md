# Lesson 04- Secure File Transfer & Remote Synchronization (SCP & Rsync)

## 1. Overview
If I talk about Secure File Transfer ( SCP ) & Remote Synchronization (Rsync). the only reason to learn SCP and Rsync is to copy and download files from the server. It is the way you interact with servers directly from your local machine. You can transfer your files to the server, download files from the server, and vice versa—sending files to the server or downloading them locally. That is the core purpose to focus on, but in this section, we will discuss how to accomplish this specifically using AWS.

---

## 2. SCP (Secure Copy Protocol)
SCP transfers files securely over SSH using standard remote path syntax (`user@host:path`).

Before moving on, let's see what SCP does. SCP basically helps you to download or push a single file to your server. That is the whole game of SCP.

### Commands (Using SSH Config Alias `aws`) -- if not getting aws than see lesson 3 automation 
* **Upload a File to EC2:**
  ```bash
  scp local_file.txt aws:/home/ubuntu/
  ```

  Download a File from EC2:

  ```bash
  scp aws:/home/ubuntu/remote_file.txt .
  ```

  Upload a Directory Recursively (-r):

  ```bash
  scp -r ./my_folder aws:/home/ubuntu/
  ```

### Task :
Just go and make a folder or directory and try to push that directory to the server using SCP. Then you will get an error. This is because SCP only handles individual files by default. For folders or directories, we need to move to rsync.

## 3. Rsync (Remote Synchronization)
For large projects, backups, or repeated file transfers, rsync is significantly faster than scp. It compares timestamps and file sizes to send only modified delta files across the network.

 Optimized Sync Command
 ```bash
 rsync -avz local_directory/ aws:/home/ubuntu/remote_directory/
 ```
 Core Options Breakdown
    -a (Archive mode): Preserves file permissions, ownership, timestamps, and copies recursively.
    -v (Verbose): Displays detailed transfer logs in the terminal.
    -z (Compress): Compresses data packets in transit to minimize bandwidth and speed up transfers.

## ⚠️ The Trailing Slash Rule

### The trailing slash on the source directory determines how files are copied

```bash

:my_website/ (with slash) : Copies the contents inside my_website directly into the target folder.
```

```bash
my_website (without slash) : Copies the entire directory itself into the target folder.
```

# 4. Real-World AWS EC2 Deployment Workflow

Upload Assets to Remote Web Server:

```bash
rsync -avz ./dist/ aws:/home/ubuntu/
```

Connect to Instance via SSH Alias:

```bash
ssh aws
```
Verify Uploaded Files:

```bash
ls -la /home/ubuntu/
```

```bash
To play with these two commands, open two terminals. One should connect to the SSH AWS Ubuntu server, and the second terminal should be your local Linux command line. Now, try to use these commands to play the game: make directories and files, try to use SCP and rsync, and see what happens in your terminal. You will also see the game of the trailing slash—don't forget it—so you will understand this core concept completely.
```