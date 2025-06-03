## 🌐 Overview

Footprinting using search engines involves using **public search tools** and **advanced query techniques** to extract valuable information about the target organization or individual.

Attackers use search engines to:
- Discover login portals, employee info, backend systems, and document leaks
- Perform reconnaissance for phishing and social engineering
- Find sensitive infrastructure (VPNs, web servers, admin panels)

---

## 🔍 Search Engines Used in Footprinting

- Google
- Bing
- Yahoo
- Ask
- AOL
- Baidu
- WolframAlpha
- DuckDuckGo

---

## 🔎 Google Hacking (Dorking)

**Google Hacking** = Using advanced search operators to extract sensitive or hidden information.

### 📘 Popular Google Search Operators

| Operator         | Purpose                                                   | Example                             |
|------------------|-----------------------------------------------------------|--------------------------------------|
| `cache:`         | Shows cached version of a webpage                         | `cache:example.com`                  |
| `link:`          | Shows pages that link to the target page                  | `link:example.com`                   |
| `related:`       | Shows similar pages                                       | `related:example.com`                |
| `info:`          | Displays info Google has about a webpage                  | `info:example.com`                   |
| `site:`          | Limits results to specific domain                         | `site:example.com`                   |
| `allintitle:`    | Finds pages with all words in title                       | `allintitle:admin login`            |
| `intitle:`       | Finds pages with specific words in title                  | `intitle:"login"`                    |
| `allinurl:`      | Finds pages with all terms in URL                         | `allinurl:admin login`               |
| `inurl:`         | Finds pages with specific words in URL                    | `inurl:admin`                        |
| `location:`      | Searches location-specific results                        | `location:India cybersecurity`       |

---

## 💡 Example of Google Dorking

> Simple Dork: `site:example.com inurl:login intitle:login`  
This can reveal login portals within a domain.

---

## 🧰 Google Hacking Database (GHDB)

The **GHDB** helps attackers or researchers query known dorks that reveal:
- Login portals
- Sensitive directories
- Vulnerable files and devices
- Password dumps

### 🔐 Common Categories in GHDB

| Category                     | Example Insight                                 |
|-----------------------------|--------------------------------------------------|
| Footholds                   | Entry points (admin, login pages)               |
| Files Containing Usernames  | Configs, text files with usernames              |
| Files Containing Passwords  | Credential leaks                                |
| Sensitive Directories       | Hidden web folders                              |
| Web Server Detection        | Apache/IIS/Nginx banners                        |
| Vulnerable Files/Servers    | Old software, test pages                        |
| Pages Containing Logins     | Login forms across subdomains                   |
| Online Devices              | Webcams, routers, IoT                           |

---

## 🔐 VPN Footprinting via Google Dorks

| #  | Google Dork                                                                 | Description                                         |
|----|------------------------------------------------------------------------------|-----------------------------------------------------|
| 1  | `inurl:"/sslvpn_logon.shtml" intitle:"User Authentication"`                | Finds login portals for WatchGuard SSL VPN          |
| 2  | `inurl:/sslvpn/Login/Login`                                                | General SSL VPN login portals                       |
| 3  | `site:vpn.*.*/`                                                            | Lists VPN-related subdomains                        |
| 4  | `intitle:"login" inurl:weblogin intitle:(USG20|ZyWALL|ATP...)`            | Detects Zyxel hardware vulnerabilities              |
| 5  | `intext:Please Login SSL VPN inurl:remote/login intext:FortiClient`       | Fortinet VPN login pages                           |
| 6  | `site:vpn.*.*/ intext:"login" intitle:"login"`                            | VPN login pages                                    |
| 7  | `intitle:"index of" /etc/openvpn/`                                         | OpenVPN configuration folders                      |
| 8  | `"-----BEGIN OpenVPN Static key V1-----" ext:key`                         | Finds private OpenVPN static keys                  |
| 9  | `intitle:"index of" "vpn-config.*"`                                        | VPN config files                                   |
| 10 | `index of / *.ovpn`                                                       | OpenVPN config/cert files                          |
| 11 | `inurl:"/vpn/tmindex.html"`                                               | Netscaler/Citrix VPN login pages                   |
| 12 | `intitle:"SSL VPN Service" + intext:"Your system administrator..."`       | Cisco ASA VPN admin login page                     |

---

## 🛠️ Other Search-Based Footprinting Techniques

| Technique               | Description                                         | Information Gathered                                                  | Tools Used                                           |
|------------------------|-----------------------------------------------------|------------------------------------------------------------------------|------------------------------------------------------|
| Google Advanced Search | Uses operators without manually typing              | Login pages, employee lists, documents                                | Google                                               |
| Advanced Image Search  | Reverse image search                                | Profile pics, locations, photo metadata                               | TinEye, Google Images                               |
| Video Search Engines   | Search for media content                            | Corporate events, interviews, training sessions                       | YouTube, Metadata viewers                           |
| Meta Search Engines    | Combines multiple search engines                    | Aggregated data from several search engines                           | Startpage, MetaGer                                  |
| FTP Search Engines     | Searches FTP servers for public files              | Backups, credentials, HR records, tax docs                            | NAPALM, FreewareWeb FTP                             |
| IoT Search Engines     | Finds Internet-connected devices                    | Open ports, cameras, routers, SCADA devices                           | Shodan, Censys, Thingful                            |

---

## ✅ Summary

- **Google Hacking** is a major technique used during passive footprinting.
- **Advanced operators** help narrow search to find login portals, vulnerable systems, and hidden data.
- **VPN and FTP servers**, config files, and credentials can be found with **prebuilt Google Dorks**.
- Tools like **Shodan** and **Meta search engines** expand the reach for attackers.
- CEH expects you to **know the operators, usage, and the categories of data you can retrieve**.

