## 🚫 IDS/Firewall Evasion Techniques

---

### 1. 🧩 Packet Fragmentation

**What It Does:** Splits probe packets (e.g., SYN/FIN scans) into fragments to evade deep packet inspection.

**How It Works:**
- Breaks the TCP header across multiple smaller packets.
- IDS/firewalls may not reassemble or inspect all fragments.
- The target reassembles them for a valid scan.

**Tools:**
- `nmap --mtu <size>`
- `fragroute`

**Why Used:**
- ✅ Defender: Tests how well security tools handle fragmented traffic.
- ⚔️ Attacker: Avoids detection by signature-based IDS.

---

### 2. 🧭 Source Routing

**What It Does:** Forces packets to follow a specific path, bypassing filtered or monitored routes.

**How It Works:**
- Adds route in IP options field.
  - **Strict Source Routing**: Fixed path.
  - **Loose Source Routing**: Must pass through some hops, others flexible.

**Why Used:**
- ✅ Defender: Rare, used in legacy network diagnostics.
- ⚔️ Attacker: Bypasses firewalls/IDS, exploits misconfigured routers.

> 🛑 Note: Blocked on most modern routers.

---

### 3. 🎭 Source Port Manipulation

**What It Does:** Fakes source port to appear as if traffic is from a trusted service.

**How It Works:**
- Common ports like 53 (DNS), 80 (HTTP) are often allowed.
- Attacker sends scan traffic *from* those ports.

**Tools:**
- `nmap -g <port>` or `--source-port`

**Why Used:**
- ✅ Defender: Check firewall weaknesses.
- ⚔️ Attacker: Evade basic port-based filtering.

> 🔍 Note: Deep packet inspection (DPI) defeats this.

---

### 4. 🕵️ IP Address Decoy

**What It Does:** Obscures attacker’s IP by mixing with fake ones.

**How It Works:**
- Scan appears from multiple IPs in logs.
- Attacker IP blended with decoys.

**Tools:**
- `nmap -D RND:10`
- `nmap -D decoy1,decoy2,ME`

**Why Used:**
- ✅ Defender: Test SOC correlation abilities.
- ⚔️ Attacker: Makes tracebacks harder.

> ⚠️ Limitations: Response tracing tools may still detect the true source.

---

### 5. 🧠 IP Address Spoofing

**What It Does:** Changes the packet’s source IP.

**How It Works:**
- Attacker forges IP in packet header.
- Replies go to spoofed IP, not attacker.
- Useful in DoS attacks.

**Tool Example:**
- `hping3 <target> -a <fake-IP>`

**Why Used:**
- ✅ Defender: Test source IP filtering.
- ⚔️ Attacker: Bypass filtering, mask identity.

> 🔐 Note: No TCP handshake possible. Used for stateless attacks like DoS.

---

### 6. 📡 MAC Address Spoofing

**What It Does:** Fakes the device’s MAC address to bypass MAC filtering.

**How It Works:**
- Attacker sends packets with trusted MAC.

**Nmap Examples:**
- `--spoof-mac 0` → Random MAC
- `--spoof-mac Apple` → Vendor-specific
- `--spoof-mac 00:11:22:33:44:55` → Manual

**Why Used:**
- ✅ Defender: Validate MAC filter rules.
- ⚔️ Attacker: Evade detection, blend in on LAN.

> 🛑 Limitation: Only works within the same LAN.

---

### 7. 🛠️ Custom Packet Crafting

**What It Does:** Sends custom packets to avoid detection or simulate traffic.

**How It Works:**
- Customize TCP flags, TTL, ports, etc.
- Send malformed, fragmented, or disguised packets.

**Tools:**
- Colasoft Packet Builder
- NetScanTools Pro

**Why Used:**
- ✅ Defender: Test firewall rules and IDS response.
- ⚔️ Attacker: Launch evasion attacks, DoS, or fingerprinting.

---

### 8. 🌍 Proxy Servers & Anonymizers

**What It Does:** Hides the attacker’s real IP by routing traffic through other systems.

**How It Works:**
- Proxy → forwards request to destination.
- Target sees proxy’s IP.
- Chaining → multiple proxies for layered anonymity.

**Common Tools:**

| Type         | Tool Examples                                         |
|--------------|--------------------------------------------------------|
| Proxy        | Proxy Switcher, CyberGhost VPN, Shadowsocks, Burp Suite |
| Anonymizer   | Tor, Tails OS, Whonix, Orbot, Psiphon Pro              |

**Comparison:**

| Feature              | Proxy               | Anonymizer (Tor, etc.)    |
|----------------------|---------------------|----------------------------|
| Use Case             | Access control, hide IP | Deep anonymity, censorship bypass |
| Routing              | Manual / 1-hop      | Multi-hop routed           |
| Encryption           | Optional            | Strong default encryption  |
| Traceability         | Moderate            | Very low                   |

**Why Used:**
- ✅ Defender: Research, restricted access
- ⚔️ Attacker: Evade geo-blocks, perform anonymous scanning or attacks

---

## 📌 Summary Table

| Technique               | Key Use Case                                  | Tools                          |
|-------------------------|-----------------------------------------------|--------------------------------|
| Packet Fragmentation     | IDS evasion via broken TCP headers            | Nmap `--mtu`, fragroute        |
| Source Routing           | Control packet path, bypass filters           | Nmap (legacy), custom scripts  |
| Source Port Manipulation| Bypass firewalls using trusted port numbers   | Nmap `-g` or `--source-port`   |
| IP Decoy                | Hide true IP in logs                          | Nmap `-D`                      |
| IP Spoofing             | Hide origin IP, DoS                           | hping3                         |
| MAC Spoofing            | Bypass MAC filters                            | Nmap `--spoof-mac`             |
| Custom Packets          | Evade detection, simulate traffic             | Colasoft Packet Builder        |
| Proxy/Anonymizers       | Hide IP, access blocked content               | Tor, VPNs, Shadowsocks         |
