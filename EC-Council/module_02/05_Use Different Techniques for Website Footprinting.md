## ✅ What is Website Footprinting?
Website footprinting is the process of monitoring and analyzing a target’s website to collect intelligence.

### 🔍 Information Extracted from Website:
- Software used and version
- Operating system and scripting platform
- Sub-directories, parameters, filenames
- Technologies used (e.g., CMS)
- Contact info, developer info
- Comments in source code
- Cookies behavior

**Tools Used:**
- Burp Suite
- OWASP ZAP
- Wappalyzer
- CentralOps
- Website Informer

---

## 🕷️ Website Footprinting using Web Spiders

### ✅ Web Spiders
Web spiders automate browsing and extract content like emails, employee names, etc.

**Tools:**
| Tool              | Description                                                      |
|-------------------|------------------------------------------------------------------|
| Web Data Extractor| Gathers names, emails, metadata from target sites                |
| ParseHub          | Automates data extraction from complex sites                     |
| Burp Suite        | Supports user-directed spidering and manual analysis             |
| WebScarab         | Intercepts and analyzes HTTP/HTTPS traffic during spidering      |

**Note:** If the website has `robots.txt`, spiders may be restricted.

---

## 🪞 Mirroring Websites

Mirroring a website allows offline analysis without alerting the target.

**Benefits:**
- Analyze directory structures
- Avoid multiple server requests

**Tools:**
| Tool                 | Description                                                       |
|----------------------|-------------------------------------------------------------------|
| HTTrack              | Download entire site including directories and media              |
| Cyotek WebCopy        | Recursive download and directory structure preservation           |

---

## 🕰️ Archive-Based Footprinting

**Wayback Machine (https://archive.org)**
- Reveals historical versions of websites
- Useful for identifying old pages, contact details, outdated CMS, etc.
- Helps build phishing pages mimicking old versions

---

## 🧠 Other Website Footprinting Techniques

| Technique                                     | Description                                                                 | Tools Used                          | Info Gathered                                                              |
|----------------------------------------------|-----------------------------------------------------------------------------|-------------------------------------|----------------------------------------------------------------------------|
| Extracting Website Links                     | Analyze internal & external links                                           | Octoparse, Netpeak Spider           | Images, scripts, iframes, URLs                                             |
| Wordlist Collection from Target Website      | Create wordlists for brute-forcing usernames or directories                 | CeWL (cewl www.site.com)            | Target-specific words                                                      |
| Metadata Extraction from Documents           | Extract hidden details from PDFs, DOCX, PPT, etc.                           | ExifTool, Metagoofil                | Author, creation date, usernames, etc.                                    |
| Monitoring Web Pages for Updates             | Detect UI changes, login page shifts, etc.                                 | Website-Watcher, Visual Ping        | Page updates, software versions                                           |
| Contact Info & Email Scraping                | Search for phone numbers, emails, addresses                                | Web Data Extractor                  | Contact, support, press info                                              |
| Web Page Revision & Pattern Identification   | Find copyright year, revision metadata, etc.                               | Manual or web crawlers              | Copyrights, revision numbers                                              |
| Monitor Website Traffic & Reputation         | Gauge site’s popularity and customer base                                   | Web-Stat, Rank Tracker              | Visitors, bounce rate, country-based analytics                            |

---

## 💡 CEH Exam Focus:
- Understand tools like `CeWL`, `HTTrack`, `Burp Suite`, and `ExifTool`
- Be able to differentiate between spidering vs. mirroring
- Know the purpose of `robots.txt`
- Know how to extract hidden metadata and contact info from web content
- Familiarize with tools used to monitor traffic, links, and page updates

