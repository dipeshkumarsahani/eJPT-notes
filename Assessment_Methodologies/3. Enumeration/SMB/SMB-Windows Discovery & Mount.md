# 📁 Enumeration – SMB (Windows Discovery & Mounting)

---

## 🎯 Purpose

To identify and access shared resources (like drives or folders) on a Windows machine through the **SMB (Server Message Block)** protocol.  
This helps in:
- Discovering shared folders or drives
- Accessing sensitive data
- Performing privilege escalation or lateral movement

---

## 🔢 SMB Default Ports

| Protocol | Port  |
|----------|-------|
| SMB over NetBIOS | 139 |
| SMB over TCP     | 445 |

---

## 🛠️ Tools Used

| Tool / Command       | Description                          |
|----------------------|--------------------------------------|
| `nmap`               | Scans for open SMB ports & services  |
| `net use` (Windows)  | Mount/unmount shared network drives  |
| **Map Network Drive** (GUI) | Windows file share mounting    |

---

## 🔎 Step-by-Step Process

---

### ✅ 1. Identify Active Hosts with SMB Open

Use `nmap` to scan the subnet and list only hosts with open ports:

```bash
nmap -T4 IP/Subnet --open
````

* `-T4`: Faster scan timing
* `--open`: Show only hosts with open ports
* Replace `IP/Subnet` with your actual target range

---

### ✅ 2. Scan Specific Host for SMB Services

After identifying a target `IP`, run:

```bash
nmap IP -sV -O
```

* `-sV`: Detects service versions (e.g., SMB version)
* `-O`: OS fingerprinting

Then:

```bash
nmap IP -sV -sC
```

* `-sC`: Runs default scripts (includes SMB share check)

These scans usually reveal:

* SMB version (e.g., SMBv1, SMBv2)
* Accessible shares
* Authentication type

---

## 💻 GUI Method (Windows)

### 🧩 Map Network Drive (e.g., C Drive)

1. Open **This PC** → Click **Map Network Drive**
2. Choose any drive letter (e.g., `Z:`)
3. Enter network path:

   ```
   \\IP\c$
   ```
4. Enter credentials if prompted

✅ You now have access to the target's shared C drive.

---

## 💻 Command-Line Method (PowerShell / CMD)

### 🚫 Remove Previous Mapped Drives

```powershell
net use * /delete
```

* Clears all existing mapped drives

### 🔁 Map the C Drive Remotely

```powershell
net use z: \\IP\c$ password /user:administrator
```

* `z:` = drive letter to assign
* `\\IP\c$` = default administrative share
* `password` = actual password
* `administrator` = target username

---

## 📌 Notes

* `c$`, `admin$`, `IPC$` are **default hidden shares** in Windows
* **Requires admin credentials**
* If accessible, it’s a **critical finding** for pentesters


📌 **Pro Tip:** Always check if anonymous access is allowed. Misconfigured shares can leak sensitive information without credentials.

---
