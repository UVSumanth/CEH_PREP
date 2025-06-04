# 🔍 CEH Footprinting Tools

This document lists the most relevant tools used in **Footprinting & Reconnaissance** with a clear focus on CEH exam context — tool purpose, type (passive/active), and why each is important.

---

## 🛠️ General Reconnaissance Tools

| Tool         | Purpose                                                                                 | Type         | CEH Relevance                                                                 |
|--------------|------------------------------------------------------------------------------------------|--------------|--------------------------------------------------------------------------------|
| **theHarvester** | Collects emails, names, subdomains from public sources like Google, LinkedIn          | Passive      | Quick enumeration of organizational data for social engineering or email spam |
| **Sublist3r** | Enumerates subdomains using public engines                                               | Passive      | Essential for domain mapping                                                   |
| **Recon-ng** | Modular framework to automate OSINT tasks (email, domains, IPs)                           | Mixed        | Automates footprinting for advanced recon workflows                            |
| **Maltego**  | Graph-based visualizer for relationships between people, domains, orgs                    | Passive      | Powerful visual footprint mapping                                              |
| **Whois**    | Gets domain ownership, registrar info, creation/expiry dates                              | Passive      | Identifies owner/contact for social engineering or DNS-based attacks          |
| **nslookup** | DNS resolver that reveals domain/IP address mappings                                      | Passive      | Used to identify name servers, mail servers, A records                         |
| **dig**      | Advanced DNS query tool                                                                   | Passive      | Preferred for deeper DNS zone analysis                                         |
| **traceroute** | Discovers route/hops between attacker and target                                       | Active       | Maps intermediate devices/firewalls for further recon                          |

---

## 🔎 Google Hacking & Search Engine Tools

| Tool            | Purpose                                                                | Type     | CEH Use |
|-----------------|------------------------------------------------------------------------|----------|---------|
| **Google Search Operators** | `site:`, `inurl:`, `intitle:`, `filetype:` to find exposed data        | Passive  | Fast discovery of sensitive docs, cameras, passwords                          |
| **GHDB**        | Google Hacking Database - curated list of dorks                         | Passive  | Saves time, uses known vulnerable search queries                              |
| **Hunter.io**   | Finds email addresses for domains                                       | Passive  | Used to launch phishing campaigns or social engineering                       |
| **Email Spider**| Scrapes websites for publicly posted emails                             | Passive  | Used to build target email lists                                              |

---

## 📱 Social Media Footprinting Tools

| Tool              | Purpose                                                               | Platform       | CEH Use |
|-------------------|------------------------------------------------------------------------|----------------|---------|
| **Sherlock**      | Checks 300+ platforms for a target username                            | Multi-platform | Tracks social identities and user footprints                                 |
| **Social Searcher** | Searches social media posts + analytics                              | Social Content | Tracks shared posts, brand mentions                                          |
| **BuzzSumo**      | Tracks viral/shared content by keyword or hashtag                      | Trend Research | Finds what employees/brands are posting                                      |
| **Followerwonk**  | Analyzes Twitter followers & locations                                 | Twitter        | Tracks influence and social links                                            |
| **Meltwater**     | Monitors geotagged or brand mentions                                   | Enterprise     | Used for PR-based intel                                                       |
| **Gephi / SocNetV / NodeXL** | Create social graphs from relationships                    | Graphing       | Visualize social connections, influencer clusters                             |

---

## 🧠 Advanced & Multi-Function Tools

| Tool            | Description                                                                                           | CEH Utility                                 |
|------------------|-------------------------------------------------------------------------------------------------------|---------------------------------------------|
| **Recon-Dog**    | All-in-one recon tool using APIs to gather DNS, Whois, GeoIP                                          | Streamlines multiple passive footprinting   |
| **BillCipher**   | Web-based info gathering tool for website/IP including WHOIS, DNS, GeoIP                             | Website recon at a glance                   |
| **Spyse**        | Cybersecurity search engine for domains, subdomains, certificates, and ports                          | Deep footprinting of company’s web surface  |
| **FOCA**         | Extracts metadata from docs (PDF, Word, etc.), DNS discovery, port scanning                           | Highly useful in document & DNS recon       |
| **OSRFramework** | Multiple modules to enumerate usernames, emails, phone numbers, domains                              | Modular identity profiling for social engg  |
| **OSINT Framework** | Curated toolset and links for OSINT categorized by target (email, domain, etc.)                   | Research shortcut and tool directory        |

---

## 🌐 Website Footprinting Tools

| Tool                  | Purpose                                                                 | CEH Use                                      |
|-----------------------|-------------------------------------------------------------------------|----------------------------------------------|
| **Wappalyzer**        | Detects technologies used on a website (CMS, server, frameworks)         | Understand backend stack                     |
| **Burp Suite / Zaproxy** | Intercepts HTTP traffic, maps web app structure                      | Active footprinting, manual browsing         |
| **HTTrack / Cyotek WebCopy** | Clone entire websites locally                                      | Analyze site structure, avoid online trace   |
| **Website Informer**  | Provides site’s tech stack, contact info                                 | Lightweight recon alternative                 |

---

## 📂 Document & Metadata Recon

| Tool            | Description                                                    | CEH Use                                             |
|------------------|----------------------------------------------------------------|------------------------------------------------------|
| **Metagoofil**   | Extracts metadata from public docs (PDF/DOC)                  | Finds usernames, emails, software versions          |
| **ExifTool**     | Reads file metadata                                           | Pulls out creation timestamps, authors, GPS info     |
| **CeWL**         | Custom wordlist generator from web page content              | Helps in password cracking with targeted dictionaries|

---

## 🌍 IP & Network Recon Tools

| Tool             | Purpose                                                                | CEH Use                     |
|------------------|------------------------------------------------------------------------|-----------------------------|
| **IP2Location**  | Provides IP geolocation information                                     | Track target location       |
| **Shodan**       | Search engine for Internet-connected devices (IoT, routers, servers)    | Exposed services scanning   |
| **Censys**       | Another OSINT engine for SSL certs, open ports, device discovery        | Compare w/ Shodan output    |
| **Path Analyzer Pro / VisualRoute / PingPlotter** | Visualize network routes to target                | Detect hops, bottlenecks    |

---

## 📈 Web Traffic & Company Recon

| Tool                      | Description                                                       | CEH Use                                |
|---------------------------|-------------------------------------------------------------------|----------------------------------------|
| **Web-Stat, SimilarWeb**  | Monitor traffic, bounce rate, page views                          | Competitor and traffic analysis        |
| **opencorporates**        | Company ownership and legal structure info                        | Social engineering + B2B link mapping  |
| **Google Finance, Yahoo Finance** | Financial snapshot of org                              | Used in financial recon and fraud cases|

---

## 📌 CEH Tips for Tool Usage

- Understand the **distinction between Passive vs. Active** tools
- Be able to **explain use cases** of recon tools during interviews or scenario-based CEH questions
- Always ask: **“What can I extract from this tool and how can that be used in an attack chain?”**
- CEH tests ability to **choose the right tool** for email, DNS, web, network, or social recon tasks

---

> ✅ Stay ready to explain: “If you were given a target domain, what tools would you use to perform passive recon and why?”
