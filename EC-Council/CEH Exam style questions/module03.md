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
