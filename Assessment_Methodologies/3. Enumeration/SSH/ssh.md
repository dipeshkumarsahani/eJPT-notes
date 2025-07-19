
# 🧠 SSH Enumeration Notes (for eJPT and Pentesting)

## 🔍 Step-by-step SSH Enumeration:

### ✅ 1. **Basic Nmap Scanning**

```bash
nmap <IP>
```

* Quickly identify open ports.

### ✅ 2. **Service & OS Detection**

```bash
nmap -sV -O <IP>
```

* `-sV`: Detects service versions (helps identify SSH version).
* `-O`: OS detection, useful to know if it's Linux, Ubuntu, etc.

---

## 🔐 SSH-Specific Enumeration

### ✅ 3. **Direct SSH Access Attempt (if creds known or default)**

```bash
ssh root@<IP>
```

* Try common usernames like `root`, `admin`, `test`, etc.
* If passwordless login enabled, it will let you in.

### ✅ 4. **Netcat Banner Grabbing**

```bash
nc <IP> 22
```

* Can show SSH banner info like OpenSSH version (may help with exploits).

---

## 🧪 Nmap NSE Scripts for SSH

### ✅ 5. **Enumerate SSH Configuration/Algorithms**

```bash
nmap <IP> -p22 --script ssh2-enum-algos
```

* Lists supported encryption, MAC, and key exchange algorithms.

### ✅ 6. **Get SSH Host Keys (Check for Weak or Reused Keys)**

```bash
nmap <IP> -p22 --script ssh-hostkey --script-args ssh-hostkey=full
```

* Helps in fingerprinting and checking for known compromised keys.

### ✅ 7. **Check Authentication Methods**

```bash
nmap <IP> -p22 --script ssh-auth-methods --script-args="ssh.user=root"
```

* Checks if user can auth using password, pubkey, keyboard-interactive, etc.

---

## 👀 Additional Useful Info

### 🔑 Username Enumeration (Manually)

If the server gives different responses for valid vs invalid usernames:

```bash
ssh validuser@<IP>       # See if it asks for password
ssh invaliduser@<IP>     # It may throw a "No such user" error
```

You can also use tools like `hydra` or `patator` to brute-force usernames (careful with rate limiting).

---

## 🎯 Summary

| Task                        | Tool/Command Example                                                     |
| --------------------------- | ------------------------------------------------------------------------ |
| Detect SSH service          | `nmap -sV <IP>`                                                          |
| Grab SSH banner             | `nc <IP> 22`                                                             |
| List supported algos        | `nmap --script ssh2-enum-algos -p22 <IP>`                                |
| Get host key fingerprint    | `nmap --script ssh-hostkey --script-args ssh-hostkey=full -p22 <IP>`     |
| Check auth methods for user | `nmap --script ssh-auth-methods --script-args="ssh.user=root" -p22 <IP>` |
| Attempt login (if creds)    | `ssh root@<IP>`                                                          |

---

💡 **Pro Tips:**

* Knowing SSH version (e.g., OpenSSH 7.4) helps check for version-specific exploits via `searchsploit`.
* If `root` is not allowed over SSH, try `admin`, `user`, or others found via `enum4linux`, `rpcclient`, etc.
* Try SSH tunneling or port forwarding after successful login.
