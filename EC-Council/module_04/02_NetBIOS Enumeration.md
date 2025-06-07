## 🔍 NetBIOS Enumeration

### What It Does
NetBIOS Enumeration allows attackers (or ethical hackers) to extract detailed info from Windows systems:
- Usernames
- Shared folders/printers
- Computer and domain names
- Services (Messenger, Server)

### How It Works
- NetBIOS uses ports:
  - 137 (UDP)
  - 138 (UDP)
  - 139 (TCP)
- Tools:
  - `nbtstat -A <IP>` – shows remote NetBIOS name table
  - `nbtstat -c` – shows local name cache
- NetBIOS name = 16 characters
  - First 15: device name
  - 16th: service code

### Why It’s Used
#### ✅ Ethical Hackers:
- Assess shares and configs
- Identify devices
- Understand domain layout

#### ❌ Attackers:
- Exploit unprotected shares
- Null Session attacks
- Gather usernames
- DoS and brute-force prep

### NetBIOS Codes
| Code | Type   | Meaning                         |
|------|--------|---------------------------------|
| <00> | Unique | Hostname                        |
| <03> | Unique | Messenger service               |
| <20> | Unique | Server service (file sharing)   |
| <1B> | Unique | Domain Master Browser           |
| <1D> | Group  | Master browser for subnet       |
| <1E> | Group  | Browser service elections        |

---

## 🧪 NetBIOS Enumeration Tools

### What It Does
Scans for:
- Computer/domain names
- Shares
- Users
- MAC addresses

### Tools
| Tool                   | Use Description                                 |
|------------------------|--------------------------------------------------|
| NetBIOS Enumerator     | Lists NetBIOS names, users, MACs                |
| Nmap + nbstat.nse      | Fetch NetBIOS info, MAC address                 |
| Hyena                  | GUI-based Windows info enumeration              |
| Advanced IP Scanner    | Quick scan with NetBIOS & port info             |
| Global Network Inventory | Lists OS, shares, services                    |
| Nsauditor              | Combines enumeration with vulnerability scan    |

#### 🔧 Command Example:
```
nmap -sV -v --script nbstat.nse <target IP>
```

---

## 👤 Enumerating User Accounts with PsTools

### What It Does
Microsoft Sysinternals tools for:
- Gathering user/session/system info
- Remote execution and control
- Password reset

### How It Works
- Connects remotely with admin credentials
- Executes commands across systems

### Tools Overview

| Tool         | Function                                             |
|--------------|------------------------------------------------------|
| PsExec       | Run remote commands                                  |
| PsFile       | View/close remote files                              |
| PsGetSid     | Resolve SIDs to usernames                            |
| PsKill       | Kill processes remotely                              |
| PsInfo       | Show system specs                                    |
| PsList       | Show process/thread stats                            |
| PsLoggedOn   | Show logged-on users (local/remote)                  |
| PsLogList    | View event logs                                      |
| PsPasswd     | Change user passwords                                |
| PsShutdown   | Shutdown/reboot/logoff remote systems                |

#### 🔧 Command Examples
```
psexec \192.168.1.10 cmd
psloggedon \192.168.1.10
pskill \192.168.1.10 notepad.exe
pspasswd \192.168.1.10 Administrator NewPass123
```

---

## 📂 Enumerating Shared Resources using `net view`

### What It Does
Lists:
- Shared folders/printers
- Computers in a domain/workgroup

### How It Works
- Uses SMB via:
  - TCP 139
  - TCP 445

### Commands
```
net view \<computername>        # Lists shared resources
net view \<computername> /ALL   # Includes hidden shares
net view /domain                 # Lists domains/workgroups
net view /domain:<domainname>    # Lists systems in the domain
```

### Why It’s Used
#### ✅ Admins:
- Audit shares & printers
- Validate share permissions

#### ❌ Attackers:
- Find sensitive shares
- Identify lateral movement paths

