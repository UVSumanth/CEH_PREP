
## 🔍 Ping Sweep Countermeasures
**What It Does:** Prevents attackers from identifying live hosts via ICMP echo requests.

**How It Works:**
- Detects abnormal ICMP traffic patterns (e.g., >10 echo requests).
- Uses IDS/IPS like Snort to detect ping sweeps.
- Limits ICMP via ACLs and allows only specific ICMP types in DMZ.

**Why It's Used:**
- ✅ Real World: Prevent network mapping by unauthorized users.
- ⚔️ Attacker Use: Used to identify live systems before launching attacks.

---

## 🔓 Port Scanning Countermeasures
**What It Does:** Blocks unauthorized access attempts through open ports.

**How It Works:**
- IDS/IPS and firewalls detect & block port scans (e.g., SYN scans).
- Use TCP wrappers and test against scanning tools like Nmap.
- Close unnecessary ports and block dangerous ones (135–159, 445, etc.).

**Why It's Used:**
- ✅ Real World: Protect systems from unauthorized access.
- ⚔️ Attacker Use: Scans for open ports to exploit vulnerable services.

---

## 🪪 Banner Grabbing Countermeasures
**What It Does:** Prevents attackers from gathering system info via banners.

**How It Works:**
- Disable or fake banners using server config (Apache, IIS).
- Use server masking tools to modify or hide service/version details.
- Remove HTTP headers (e.g., X-Powered-By) and hide file extensions.

**Why It's Used:**
- ✅ Real World: Reduces attack surface by hiding tech stack.
- ⚔️ Attacker Use: Banners reveal exploitable service/OS versions.

---

## 🧠 IP Spoofing Countermeasures
**What It Does:** Blocks forged IP traffic used in spoofing and DoS attacks.

**How It Works:**
- Avoid IP trust relationships.
- Use ACLs, ingress/egress filtering, firewalls, and random ISNs.
- Enable encryption (e.g., IPSec) and router hardening.

**Why It's Used:**
- ✅ Real World: Protects against impersonation and session hijacking.
- ⚔️ Attacker Use: Spoofs IP to bypass IP filters or overwhelm systems.

---

## 🛑 Scanning Detection & Prevention Tools
**Tools:**
- ExtraHop
- Splunk Enterprise Security
- Scanlogd
- Vectra Cognito Detect
- IBM QRadar XDR
- Cynet 360

**Why Used:**
- ✅ Real World: Monitor for network scans and block suspicious activity.
- ⚔️ Attacker Use: Avoid detection by staying under alert thresholds.
