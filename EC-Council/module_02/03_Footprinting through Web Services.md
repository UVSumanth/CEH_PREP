## 🌐 Finding a Company’s TLDs and Subdomains

### 🔍 Methods
- Search company domain via search engines (Google, Bing)
- Use OSINT tools and brute-force methods to discover subdomains
- Analyze subdomains to understand company structure (e.g., `dev.company.com`, `sales.company.com`)

### 🔧 Tools for Subdomain Enumeration

| Tool/Service                     | Purpose                                |
|----------------------------------|----------------------------------------|
| Netcraft                         | Enumerates domains & subdomains        |
| Pentest-Tools: Find Subdomains   | Online recon tool                      |
| Sublist3r                        | Python script for subdomain discovery  |

### 🔢 Sublist3r Syntax Table

| Short | Long Form      | Description                                                   |
|-------|----------------|---------------------------------------------------------------|
| -d    | --domain       | Domain to enumerate subdomains                                |
| -b    | --bruteforce   | Enable brute-force module                                     |
| -p    | --ports        | Scan found subdomains on specific ports                       |
| -v    | --verbose      | Display verbose output                                        |
| -t    | --threads      | Number of threads to use                                      |
| -e    | --engines      | Comma-separated list of engines to use                        |
| -o    | --output       | Save results to output file                                   |
| -h    | --help         | Display help menu                                             |

---

## 👤 People Search via Social Networks and Services

### 🧠 Information Extracted
- Names, email addresses, location, job titles, birthdates, photos, and blogs
- Supports social engineering, spear phishing, and employee profiling

### 🔧 Tools & Platforms

| Source Type          | Examples                                                       |
|----------------------|----------------------------------------------------------------|
| Social Media         | Facebook, LinkedIn, Twitter                                    |
| People Search Sites  | Spokeo, Intelius, Pipl, BeenVerified, Whitepages, PeekYou      |

---

## 💼 Gathering Info via LinkedIn

- Use **theHarvester** to extract employee names and job titles
- Analyze for department mapping, hierarchy, and possible email formats
- Combine with spear phishing or OSINT enumeration

---

## ✉️ Harvesting Email Lists

- Publicly available emails serve as **targets for brute-force, phishing, or spoofing**
- Tools:
  - **theHarvester**
  - **Email Spider Pro**
  - **Hunter.io**

---

## 🕸️ Deep Web vs Dark Web Footprinting

| Type       | Description                                                                 |
|------------|-----------------------------------------------------------------------------|
| Deep Web   | Content not indexed by traditional search engines                          |
| Dark Web   | Anonymized part of deep web accessed via special tools (TOR, I2P, Freenet) |

### 🔧 Tools for Deep/Dark Web
- **Tor Browser** – anonymized browsing
- **ExoneraTor** – maps IPs to TOR exit nodes
- **Dark Web Search Engines** – Ahmia, OnionSearch

### 🧠 Information Gathered:
- Leaked credentials, SSNs, CC numbers, private emails, ID documents

---

## 🖥️ Determining Operating System

| Tool     | Description                                                                 |
|----------|-----------------------------------------------------------------------------|
| SHODAN   | Search engine for Internet-connected devices (shows OS, services, ports)    |
| Censys   | Advanced search for exposed servers/devices across the globe                |

---

## 🔐 VoIP and VPN Footprinting via SHODAN

### CEH-Relevant Use:
- Identify exposed VoIP servers and VPN login portals
- Discover misconfigured or outdated VPN devices
- Use SHODAN filters: `product:OpenVPN`, `port:5060`, `"Fortinet"`, `http.title:"VPN Login"`

---

## 🏁 Competitive Intelligence Gathering

| Source Type                        | Example Sources                                                         |
|-----------------------------------|--------------------------------------------------------------------------|
| Company History                   | EDGAR, D&B Hoovers, LexisNexis                                          |
| Future Plans                      | MarketWatch, Wall Street Transcript, USPTO                              |
| Public Opinions                   | SEMRush, SimilarWeb, SERanking                                          |
| Job Postings                      | LinkedIn, Glassdoor, Careers page                                       |
| Analyst Reports                   | Euromonitor, Experian                                                   |

> Competitive intelligence is **non-intrusive** and focused on gathering publicly available information about competitors, market trends, or product strategy.

---

## 🌍 Other Web Services-Based Footprinting Techniques

| Technique                            | Description                                                                 | Information Gathered                                                                                 | Tools Used                                               |
|-------------------------------------|-----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| Geolocation Mapping                 | Locate physical premises, entry points, security cameras                    | Office layouts, entry points, surrounding access points                                               | Google Maps, Wikimapia                                  |
| Financial Information Discovery     | Search for financial metrics, shareholder reports                           | Market value, stock performance, revenue trends                                                       | Google Finance, Yahoo Finance                           |
| Business Profile Lookup             | Get regional business data                                                  | Contact details, board members, company registration                                                  | OpenCorporates, Crunchbase                              |
| Alerts & Mention Tracking           | Receive notifications for brand or personnel mentions                       | Brand reputation, PR risks                                                                            | Google Alerts, Mention, Reputology                      |
| Online Reputation Monitoring        | Track reviews or media mentions                                             | Customer complaints, ratings, brand score                                                             | ReviewPush, Trustpilot                                  |
| Forums, Blogs, and Group Analysis   | Join groups to gather casual and inside information                         | Employee views, tool usage, frustrations, incidents                                                   | Google Groups, Reddit, Discord                          |
| Usenet and NNTP Archives            | Access newsgroup postings                                                   | Network logs, tool chatter, historical commentary                                                     | Newshosting, Supernews                                  |
| Public Source Code Repositories     | Analyze code submitted by employees or open-source contributors             | API keys, software architecture, credentials                                                          | GitHub, GitLab, Recon-ng                                |

---

## ✅ Final Takeaways

- **Footprinting through web services** offers both **passive and active OSINT paths**.
- Tools like **Sublist3r, theHarvester, SHODAN, and social networks** help extract sensitive insights.
- **CEH expects you to understand how to use these tools, what info to gather, and the risk associated**.

