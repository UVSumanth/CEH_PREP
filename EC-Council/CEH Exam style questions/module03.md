## 📝 CEH-Style Multiple Choice Questions

### Network Scanning Concepts   
**Q1.** What is the purpose of the SYN flag in a TCP communication?  
A. Terminate a connection  
B. Confirm data receipt  
C. Initiate a connection  
D. Restart the communication  

✅ Correct Answer: C. Initiate a connection

___

**Q2.** Which of the following best describes the TCP termination process?  
A. SYN → ACK → RST  
B. FIN → FIN → SYN  
C. RST → ACK  
D. FIN → ACK → FIN → ACK  

✅ Correct Answer: D. FIN → ACK → FIN → ACK

___

**Q3.** In a network scan, which TCP flag combination is typically used in a stealth SYN scan?  
A. SYN only  
B. SYN + ACK  
C. FIN + PSH  
D. ACK + RST  

✅ Correct Answer: A. SYN only

***

### Network Scanning Tools
**Q1.** You are performing a stealth port scan using hping3 to avoid detection by IDS. Which type of scan is best suited for this purpose?  
A. UDP Scan  
B. TCP Connect Scan  
C. SYN Scan  
D. ACK Scan    

Answer: ✅ C. SYN Scan    
Reason: SYN scan is half-open and does not complete the TCP handshake, making it stealthy.

---

**Q2.** Which of the following hping3 commands is used to check if a host is online by sending ICMP echo requests?  
A. hping3 -8 <Target IP>  
B. hping3 -A <Target IP>  
C. hping3 -1 <Target IP>  
D. hping3 -2 <Target IP>  

Answer: ✅ C. hping3 -1 <Target IP>  
Reason: -1 switch sends ICMP echo requests, similar to ping.

---

**Q3.** A CEH professional wants to gather the Initial Sequence Number (ISN) of a target host to prepare for a TCP session hijacking attack. Which command should they use?  
A. hping3 -8 <Target IP> -S  
B. hping3 <Target IP> -Q -p 139  
C. hping3 -F -P -U <Target IP>  
D. hping3 -S <Target IP> -p 22 --flood  

Answer: ✅ B. hping3 <Target IP> -Q -p 139  
Reason: The -Q flag tells hping3 to collect ISNs, useful in hijacking.

----

**Q4.** Which hping3 command would you use to simulate a TCP SYN flood DoS attack on port 22 of a target?  
A. hping3 -A -p 22 --flood  
B. hping3 -S <target> -p 22 --flood  
C. hping3 -2 <target> -p 22  
D. hping3 -9 http -I eth0  

✅ Correct Answer: B

---

**Q5.** Which result from a UDP scan indicates a closed port on the target system?  
A. No reply from the target  
B. ICMP Port Unreachable message received  
C. RST packet received  
D. SYN-ACK response  

✅ Correct Answer: B

---

**Q6**. What is the primary benefit of using a SYN scan over a full TCP connect scan in a penetration test?  
A. Higher packet payload  
B. Guaranteed port enumeration  
C. Lower chance of detection by security systems  
D. Better for scanning mobile networks  

✅ Correct Answer: C

---

**Q7.** What information can be obtained using the hping3 -Q -p 139 <target> command?  
A. Firewall rules  
B. HTTP traffic  
C. Initial Sequence Number (ISN)  
D. UDP service banner    

✅ Correct Answer: C

---

### Host Discovery
**Q1.** What type of scan sends packets that ask for MAC addresses to discover live hosts, bypassing ICMP restrictions?  
A. TCP Connect Scan  
B. ARP Ping Scan  
C. SYN Stealth Scan  
D. ACK Scan  

✅ Correct Answer: B. ARP Ping Scan

---

**Q2.** Q: What scan sends packets to port 40125 by default to check host availability using the UDP protocol?  
A. ICMP Echo Scan  
B. TCP ACK Scan  
C. UDP Ping Scan  
D. SYN Stealth Scan  

✅ Correct Answer: C. UDP Ping Scan 

---

**Q3:** What scan type uses Echo Request/Reply to check if a host is live, commonly blocked by firewalls?  
A. TCP SYN Scan  
B. ICMP Echo Ping Scan  
C. UDP Ping Scan  
D. ACK Scan  

✅ Correct Answer: B. ICMP Echo Ping Scan

---

**Q4:** Which technique sends ICMP Echo Requests to a range of IPs to identify live hosts on a network?  
A. TCP Connect Scan  
B. ARP Ping Scan  
C. ICMP Echo Ping Sweep  
D. UDP Port Scan  

✅ Correct Answer: C. ICMP Echo Ping Sweep

---
**Q5:** Which ICMP-based scan requests the subnet mask from a host to determine if it is alive?  
A. ICMP Echo Ping  
B. ICMP Timestamp Ping  
C. ICMP Address Mask Ping  
D. TCP Null Scan  

✅ Correct Answer: C. ICMP Address Mask Ping 

---

**Q6:** Which scan sends a TCP SYN packet to check if a host is alive and ends with an RST to avoid full connection?  
A. TCP Connect Scan  
B. TCP SYN Ping Scan  
C. ICMP Echo Scan  
D. UDP Ping Scan  

✅ Correct Answer: B. TCP SYN Ping Scan

---

**Q7:** Which scan sends an ACK packet and considers a host alive if an RST is received in response?  
A. TCP SYN Ping  
B. TCP ACK Ping   
C. UDP Ping  
D. ICMP Echo Ping  

✅ Correct Answer: B. TCP ACK Ping 

---

### Port and Service Discovery
**Q1:** Which scan completes a full TCP handshake and is easily logged by the target system?  
A. TCP SYN Scan  
B. TCP Connect Scan  
C. TCP ACK Scan  
D. UDP Scan  

✅ Correct Answer: B. TCP Connect Scan 

---

**Q2:** Which scan sends a SYN, waits for SYN-ACK, then sends RST instead of completing the handshake?  
A. TCP Connect Scan  
B. TCP ACK Scan  
C. Stealth Scan (SYN Scan)  
D. UDP Ping Scan  

✅ Correct Answer: C. Stealth Scan (SYN Scan) 

---

**Q3:** Which scanning method uses TCP packets with unusual or no flags to avoid detection by IDS?  
A. Stealth Scan  
B. Inverse TCP Flag Scan  
C. TCP ACK Scan  
D. UDP Ping Scan  

✅ Correct Answer: B. Inverse TCP Flag Scan

---
**Q4:** Which scan sets FIN, URG, and PSH flags and relies on no response to detect open ports?  
A. NULL Scan  
B. Xmas Scan  
C. TCP Connect Scan  
D. ACK Scan  

✅ Correct Answer: B. Xmas Scan

---

**Q5:** Which scan analyzes RST responses (TTL or Window values) to infer port status and bypass IDS?  
A. TCP Connect Scan  
B. FIN Scan  
C. ACK Flag Probe Scan  
D. UDP Ping Scan  

✅ Correct Answer: C. ACK Flag Probe Scan

---


