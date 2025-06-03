## 🎯 What is Social Media Footprinting?

Social networking sites are a rich source of **personal, professional, and organizational data**. Attackers use **social engineering** combined with OSINT to gather sensitive information about targets without direct technical attacks.

---

## 🧠 Collecting Information via Social Engineering

Attackers often:
- Create **fake profiles** to befriend employees
- Use common interests, group memberships, or employee tags to connect
- Exploit **shared content, group activities, and interactions** to map the organization’s internal structure

---

### 📊 What Users & Organizations Reveal (CEH-Relevant Table)

| User Behavior                         | Information Exposed to Attacker                            |
|--------------------------------------|-------------------------------------------------------------|
| Maintain profile                     | Name, email, phone, address, DOB, location, job title      |
| Connect to friends, chat             | Friends list, relationships, insider social circle         |
| Share photos/videos                  | Family members, hobbies, routines                          |
| Play games, join groups              | Interests, affiliations                                    |
| Create or attend events              | Real-time location, activities, behavioral patterns        |

| Organization Behavior                | Attacker Insight                                            |
|--------------------------------------|-------------------------------------------------------------|
| User surveys                         | Market strategy, business direction                         |
| Product promotions                   | Product lineup, marketing strategy                          |
| Customer support                     | Service vulnerabilities, frustration points                 |
| Recruitment/job posts                | Technologies used, open roles, org hierarchy               |
| Employee background checks           | Company structure, hiring pipeline                         |

---

## 🌍 Social Media Search Tools (General Recon)

| Tool         | Purpose                                                                 |
|--------------|-------------------------------------------------------------------------|
| **BuzzSumo** | Finds most shared content using hashtags, topics, or domains           |
| **Google Trends** | Shows trending search topics, hashtags, and user interests       |
| **Hashatit** | Real-time hashtag and keyword search across social media               |

🔎 These tools allow attackers to:
- Discover frequently mentioned individuals/domains
- Track posts, trends, and hashtags related to a company
- Filter influencers or insiders for social engineering

---

## 📍 Geolocation Tracking via Social Media

Attackers search for **geotagged photos, posts, and check-ins** to identify:
- User routines and current locations
- Office locations, events, and public appearances

### 🔧 Geolocation Tools

| Tool           | Functionality                                               |
|----------------|-------------------------------------------------------------|
| **Followerwonk** | Deep dive into Twitter followers and locations            |
| **Hootsuite**   | Social media monitoring with geo-based filters             |
| **Meltwater**   | Analyzes media mentions and locations                      |

---

## 🧬 Constructing & Analyzing Social Graphs

Social network analysis allows attackers to visualize and interpret:
- Relationships between employees, teams, and departments
- Flow of communication and frequently connected individuals

### 🛠️ Tools for Graph-Based Analysis

| Tool       | Purpose                                                         |
|------------|------------------------------------------------------------------|
| **Gephi**  | Powerful social network graphing and visualization              |
| **SocNetV**| Visual social network analysis with statistical metrics         |
| **NodeXL** | Excel plugin for social graph construction                      |

---

## 🔍 Tools for Social Media Footprinting

| Tool            | Description                                                                            |
|-----------------|----------------------------------------------------------------------------------------|
| **Sherlock**     | Searches over 300 social media platforms to find accounts with the same username     |
| **Social Searcher** | Real-time search engine for public social media content + analytics                |
| **theHarvester**  | Can extract emails and usernames from LinkedIn and Twitter                          |
| **Recon-ng**      | Modular OSINT framework for social and credential harvesting                         |

---

## ✅ CEH-Exam Relevance Summary

- Understand how **user habits reveal sensitive data** (e.g., event check-ins, hashtags, job posts)
- Know tools like **Sherlock, BuzzSumo, and theHarvester** and their use cases
- Be aware of **how attackers use public profiles** for pretexting, phishing, and impersonation
- Learn how **social graphs** and **trend analytics** are weaponized in footprinting
- Emphasize the **value of geolocation, friend networks, and photo metadata** for adversaries

