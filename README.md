# Network-Traffic-Analysis---Cybersecurity-Incident-Response

# Table of contents

1. [Introduction](#introduction)
2. [Scenario](#scenario)
3. [Analysis](#analysis)
4. [Conclusion](#conclusion)

-------

# Introduction <a name="introduction">

A mock network traffic analysis and incident response assignment done on yummyrecipiesforme.com website as part of Google's <a href='https://www.coursera.org/google-certificates/cybersecurity-certificate'>Cybersecurity Professional Certificate</a> on Coursera. It provides an in-depth analysis of a network traffic incident related to DNS service failures, where customers were unable to access the website.

The goal of this activity is to demonstrate the process of analyzing network traffic, identifying the cause of service disruption, and providing recommendations for resolving the issue.

------

# Scenario  <a name="scenario">

Several customers reported that they were unable to access the website www.yummyrecipesforme.com and encountered the error message “destination port unreachable.” As a cybersecurity analyst working for a company that provides IT services to clients, you were tasked with investigating the issue.

Upon visiting the website, you also received the same error. To troubleshoot the issue, you utilized a network analyzer tool, tcpdump, to capture network traffic data. During the analysis, it was revealed that your browser sent a DNS query via UDP protocol to retrieve the IP address of the website. However, the DNS server responded with ICMP packets containing the error message: "udp port 53 unreachable," indicating that the DNS server could not be reached.

![alt text](https://github.com/TalhaZafeer/Network-Traffic-Analysis---Cybersecurity-Incident-Response/blob/main/tcp_dum.png?raw=true)


The captured tcpdump log provides key insights into the interaction between your computer and the DNS server, showing multiple attempts to query the DNS server and the subsequent ICMP error responses.

# Analysis  <a name="analysis">

**Problem Found in the tcpdump Log**

The tcpdump log reveals that the UDP protocol was used as part of the DNS query process to contact the DNS server. However, the server responded with ICMP error messages, indicating issues in reaching the DNS server. The error "udp port 53 unreachable" points to a failure in DNS services, as port 53 is reserved for DNS protocol traffic.

This issue was evident across multiple attempts, as each time the browser attempted to resolve the domain name, the DNS server returned the same ICMP error message, preventing the browser from retrieving the necessary IP address to load the website.

**Cause of the Incident**

The incident occurred around 1:24 PM. Customers reported the "destination port unreachable" error, which led to an investigation using tcpdump. The log data indicates that DNS port 53 was unreachable. This could be caused by several factors, including:

**DNS Server Down:** The DNS server might be offline, possibly due to a misconfiguration or a successful Denial of Service (DoS) attack.
**Firewall Blocking:** Traffic to port 53 may be blocked by a firewall, either intentionally or due to misconfiguration.
**Service Misconfiguration:** The DNS service on the server might not be running or may be incorrectly configured, leading to the port being unreachable.

The analysis shows that the DNS server at IP 203.0.113.2 is not responding to DNS queries, resulting in the failure to resolve the domain www.yummyrecipesforme.com. The next steps involve verifying the DNS server's status, checking firewall configurations, and investigating any potential server misconfiguration.

# Conclusion  <a name="conclusion">
This concludes my network traffic analysis for the DNS service disruption. I hope this writeup provides valuable insights into the process of diagnosing network-related issues and highlights the importance of thorough traffic analysis in cybersecurity.

**Self-Evaluation:**
I feel confident in my ability to identify and interpret key network traffic indicators that point to service disruptions. Successfully pinpointing the DNS issue and understanding its impact on accessibility gave me a strong sense of accomplishment. This assignment tested my knowledge and reinforced my hands-on skills in network troubleshooting.

**Lessons Learned:**
While I was able to diagnose the issue effectively, I realized the importance of diving deeper into the underlying causes of DNS failures, particularly in the context of broader network infrastructure. I also learned to balance technical detail with clarity, ensuring that the findings are both precise and understandable for stakeholders. Going forward, I aim to improve my documentation skills to better communicate technical findings to non-technical audiences.


