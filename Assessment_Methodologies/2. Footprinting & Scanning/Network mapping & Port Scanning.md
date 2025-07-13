<h2>
  Assessment Methodologies | Footprinting & Scanning | 
  <code>Network Mapping & Port Scanning</code>
  
</h2>

# 🗺️ Footprinting & Scanning – Mapping a Network

---

## 🎯 Purpose

The goal of network mapping is to identify:
- Active hosts within a subnet
- Host IP addresses and MACs
- Basic network layout
- Devices that can be targets for deeper assessment

---

## ⚙️ Process

1. Identify your **network interface** and **subnet**
2. Scan the subnet to detect **live hosts**
3. Use tools to **visualize or capture packets**
4. Document the discovered hosts and structure

---

## 🧰 Tools Used

| Tool       | Purpose                               |
|------------|----------------------------------------|
| `ip a`     | Show active network interfaces & IPs   |
| `arp-scan` | Perform ARP-based discovery on subnet  |
| `fping`    | Fast ping sweeping                     |
| `nmap`     | Ping scan to find live hosts           |
| `zenmap`   | GUI frontend for Nmap                  |
| `wireshark`| Network packet capture tool            |

---

## 🔧 Commands & Usage

---

### 🔍 Step 1: Check Interface and Subnet

```bash
ip a
````

* Find your interface name (e.g., `tap0`, `eth0`, `wlan0`)
* Note the IP range (e.g., `10.0.2.0/24`)

---

### ⚡ Step 2: Use `arp-scan` for Local Discovery

```bash
sudo arp-scan -I tap0 -g 10.0.2.0/24
```

* `-I tap0` = specify interface
* `-g` = use generated IP range

---

### 📶 Step 3: Use `ping` (Basic ICMP Test)

```bash
ping 10.0.2.10
```

* Check if a host responds to ICMP ping

---

### 🚀 Step 4: Use `fping` for Fast Sweeping

```bash
fping -I tap0 -g 10.0.2.0/24 2>/dev/null
```

* Faster than `ping`
* `2>/dev/null` hides unreachable host errors

---

### 🔎 Step 5: Use Nmap Ping Scan

```bash
nmap -sn 10.0.2.0/24
```

* Sends ICMP echo & ARP requests
* Detects live hosts without scanning ports

---

### 🖥️ Step 6: Use Zenmap (GUI)

* Select **ping scan**
* Enter subnet: `10.0.2.0/24`
* Interface auto-detected or set manually

---

### 📡 Bonus: Capture Packets with Wireshark

1. Open Wireshark
2. Select interface `tap0` or `eth0`
3. Start capturing
4. Observe ARP requests, ICMP replies, broadcast packets

---

## ✅ Summary

| Tool        | Description                      |
| ----------- | -------------------------------- |
| `arp-scan`  | Best for LAN/ARP-level discovery |
| `fping`     | Fast ICMP sweeps                 |
| `nmap -sn`  | Standard ping/ARP scan           |
| `wireshark` | Packet-level network monitoring  |
| `zenmap`    | Visual scanning for easy review  |

---

📌 **Tip:** Always match your scan tool with the network type (LAN/WAN) and stealth requirement.

---

