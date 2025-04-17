# Footprinting & Google Dorking Notes

## 🧭 Footprinting Overview

Footprinting involves gathering information about a target system, network, or organization to identify ways to infiltrate it.

### 🎯 Key Information Types Collected:

- **System Information**  
  *Operating system, services (e.g., Active Directory, LDAP), usernames, and passwords.*

- **Network Information**  
  *DNS records, domain/subdomains, registries, firewall types and rules.*

- **Organizational Information**  
  *Email addresses, department details, employee names and roles.*

> **Why it matters**: Helps in crafting social engineering attacks and discovering vulnerabilities before active exploitation.

---

## 🔎 Google Dorking

**Google Dorking** uses advanced search queries to extract hidden or sensitive data indexed by search engines.

### Common Operators:

| Operator      | Purpose                                           |
|---------------|---------------------------------------------------|
| `inurl:`      | Search within the URL                            |
| `intitle:`    | Search within page titles                         |
| `intext:`     | Search within page content                        |
| `site:`       | Limit results to specific domain                  |
| `filetype:`   | Find specific file types (e.g., `.pdf`, `.xls`)   |
| `link:`       | Search sites linking to a URL                     |
| `related:`    | Find similar websites                             |

### Tools & Resources:
- **Google Hacking Database (GHDB)** on ExploitDB – a repository of effective dorks.
- Use with caution and ethical responsibility.

---

## 🌐 Notes from TryHackMe: Google Dorking Room

### How Search Engines Work:

- **Search Engines**: Index massive web content.
- **Crawlers/Spiders**: Automated bots that scan pages.
- **Indexing**: Metadata like keywords, structure, and links stored for fast retrieval.

### Crawler Methods:

1. **Pure Discovery (Direct Access)**  
   - Crawls specific URLs directly.

2. **Link Traversal**  
   - Crawls pages found through links on already visited pages.

**What Crawlers Collect:**
- Keywords
- Page structure
- Metadata
- Outbound and internal links

---

## 📈 Search Engine Optimization (SEO)

SEO improves a website's visibility in search results.

| Concept           | Details                                               |
|-------------------|--------------------------------------------------------|
| **Definition**    | Optimizing content for search engine ranking          |
| **Priority Sites**| Fast, mobile-friendly, keyword-rich                   |
| **Ranking Factors**| Performance, structure, and metadata                 |
| **Robots.txt**    | File that controls crawler access                     |
| **Sitemaps**      | XML maps that guide crawlers to important pages       |

### Sitemap Benefits:
- Helps crawlers index efficiently.
- Reduces guesswork and improves visibility.
- Analogy: Like using a map instead of wandering aimlessly.

---

## 🔍 Shodan.io Summary

**Shodan** is a search engine for internet-connected devices.

### Capabilities:
- Discover exposed IoT devices, webcams, databases, etc.
- Indexes metadata like IP, OS, ports, services.

### Example Use:
1. Use `ping` to find IP → Input IP into Shodan.
2. Use filters to narrow searches:
   - `product:MySQL`
   - `asn:AS14061 product:MySQL`
   - `vuln:ms17-010` *(Only for legal, authorized assessments)*

### Banners:
- Contain metadata about services (e.g., port, OS, organization).

### Popular Filters:
- `asn`, `product`, `city`, `geo`, `hostname`, `net`, `os`, `port`, `before`, `after`

> **Legal Note**: Viewing public info = legal. Unauthorized access = illegal.

### Shodan API:
- Used to automate IP monitoring (e.g., for company-owned infrastructure).
- Useful for tasks like detecting exposed Pi-Hole instances.

---

## 🌐 Subdomain Enumeration

| Tool/Service       | Purpose                                    |
|--------------------|--------------------------------------------|
| **Netcraft**       | Web search for DNS and subdomain listings |
| **Sublist3r** (Linux) | CLI tool to enumerate subdomains       |

---

### ✅ Summary

This file includes:
- Core concepts of footprinting and enumeration
- Google Dorking syntax and responsible use
- Technical breakdowns from TryHackMe and Shodan
- SEO and crawling insights
- Practical tools and examples for reconnaissance
