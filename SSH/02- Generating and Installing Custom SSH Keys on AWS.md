# 02. Generating and Installing Custom SSH Keys on AWS

In this lesson, you will learn how to set up SSH key authentication instead of relying solely on default vendor passwords or initial download files.

I highly recommand using LLMs to understand them better rather than copy and pasting them. 


---

## 💡 Overview

* **Private Key:** Kept safely on your local machine.
* **Public Key:** Copied to the remote server using `ssh-copy-id`.

---

## 🛠️ Step-by-Step Configuration

### 1. Generate a new key on your local machine
Run the following command in your terminal:

<details>
<summary>🔍 Command Breakdown & Explanations of </summary>

* **`ssh-keygen`**: The Linux utility used to generate SSH key pairs.
* **`-t ed25519`**: Specifies the algorithm. `ed25519` is universally supported across Linux, macOS, and Windows. Always stored in `~/.ssh/` (`/home/username/.ssh/`).
* **`-C "hassan-laptop"`**: Adds an identifying comment to the key so you know which device created it.

</details>

```bash
ssh-keygen -t ed25519 -C "Hassan-Laptop"
```

Note: Press Enter to accept the default location. You can optionally set a passphrase for added security. But Leave this for now just press 'Enter'.


### 2. Copy the new public key to your AWS server

For Ubuntu instances, use:

```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub -o IdentityFile=your-existing-key.pem ubuntu@YOUR_EC2_PUBLIC_IP
```


Replace the placeholders:your-existing-key.pem $\rightarrow$ Path to your original AWS key fileYOUR_EC2_PUBLIC_IP $\rightarrow$ Your EC2 instance public IP addressec2-user / ubuntu $\rightarrow$ The correct default username for your AMI3. Test key-based loginConnect using your newly generated key pair:Bashssh -i ~/.ssh/id_ed25519 ubuntu@YOUR_EC2_PUBLIC_IP

If successful, you are now authenticating with your personal ED25519 key pair rather than relying on the default .pem file.🔒 Security Best PracticesCritical Security Warning: Never share your private key files. Ensure proper restrictive file permissions (600) are applied to all private key files on your local machine:Bashchmod 600 ~/.ssh/id_ed25519

chmod 600 your-existing-key.pem

## Congratulation for your ssh-key