## PENETRATION TESTING REPORT
## FOOTPRINTING & NETWORK SCANNING PHASES
 
**Pentester name**: Eric Aboagye

**Program**: BO82- Networkwalks

**Date**: 12 November 2026

**Client**:1. Networkwalks (secured written permission already)
2. My own local LAN Network

**Phases covered**:Phase 1: Reconnaissance & Footprinting
Phase 2: Scanning & Network Discovery
Phase 3–5: In Progress
   
**Operating environments**:Kali Linux (footprinting)
Windows PC with Zenmap (network scanning)

##  Liability Disclaimer
I have performed these activities only on the systems and devices where I had secured written permission or on devices and systems that I own myself. All these materials are for educational and research purposes only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries, unauthorised access is a crime even when nothing is damaged.

## Introduction
This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1) and scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks.
All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). The activities and observations are documented below, together with the evidence screenshots to be inserted for each practical step and a note on why each finding matters from an attacker's point of view.

## Tools Used
**Kali Linux & Windows**: Operating systems used for reconnaissance activities.

**WHOIS**: Find domain registration details (owner, dates and name servers).

**WhatWeb**: Fingerprint web technologies (server, CMS, plugins and IP).

**Nslookup**: Resolve the domain name to its IP address using DNS.

**curl -I**: Read the HTTP response headers of the website.

**Wafw00f**: Detect whether a Web Application Firewall protects the site.

**DNSRecon**: Enumerate DNS records (NS, MX, SPF, TXT and SRV).

**Zenmap (Nmap GUI)**: Scan the local subnet to find live hosts, IPs and MAC addresses.

**Windows CMD**: Identify local IP and MAC address information

## Activities Performed
## Footprinting & Reconnaissance
I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each tool was used to collect a different type of information about the target.
First, I used WHOIS to obtain publicly available domain registration information and identify the domain's name servers. The results provided information about the domain registration and hosting infrastructure, identifying the registrar as GoDaddy and the name servers as HostGator.
I then used WhatWeb to identify technologies used by the website. The results identified WordPress 7.1.4 and WP Download Manager 3.3.76, along with the Apache server and PHP backend.
Using Nslookup, I resolved the domain name to its IP address. The provided result identified 192.232.216.135.
I used Curl with the -I option to inspect the HTTP response headers. This provided additional information about the web application, exposed the WordPress REST API endpoint /wp-json/, and revealed specific cookie settings and caching headers.
Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website. The result identified ModSecurity (SpiderLabs).
Finally, I used DNSRecon to enumerate DNS records. The results provided information relating to name servers, mail servers (MX), service records (SRV for _autodiscover), and DNS software information (Bind Version 9.16.23-RH).

## Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
I first used the Windows ipconfig command to identify my local IP address and LAN subnet. My local IP was identified as 192.168.14.28 with a subnet mask of 255.255.255.0 and default gateway 192.168.14.158.
I then entered the subnet into Zenmap and selected Ping Scan to identify active hosts. The scan identified two live hosts:

•	192.168.14.28 (My Local Machine)

•	192.168.14.158 (Gateway/Router)

The scan also identified the MAC address of the gateway as 2E:CC:AC:42:47:5E.
After completing the scan, I opened the Topology section in Zenmap, enabled the legend, and saved the network topology in PDF format as required by the practical task.

## Risk Analysis
![alt text](<Screenshot 2026-11-12 235300.png>)
Risk level key: Critical | Medium | Low
The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities. The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules. Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability

 ## Recommendations
Based on the observations from these activities, I recommend the following security improvements:
1.	Review publicly exposed technology information
Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.
2.	Keep software updated
CMS platforms (WordPress), plugins (WP Download Manager), and other web technologies should be regularly updated and reviewed against current security advisories.
3.	Review HTTP headers
HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.
4.	Review DNS records regularly
DNS records should be checked periodically to ensure that only required information and services are publicly exposed.
5.	Properly configure and monitor the WAF
Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.
6.	Perform regular internal network discovery
Organizations should periodically scan their own networks to identify active devices.
7.	Investigate unknown devices
Any unexpected device discovered during network scanning should be investigated and verified.
8.	Maintain network documentation
Network topology and device information should be documented and updated regularly.
9.	Perform security testing with authorization
Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

## Conclusion
During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.
In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information.
In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.
The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.
I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.
Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab.

## Evidence Collected
![alt text](<Screenshot (205).png>)
![alt text](<Screenshot (207).png>)
![alt text](<Screenshot (210).png>)
![alt text](<Screenshot (211).png>)
![alt text](<Screenshot (212).png>)
![alt text](<Screenshot (213).png>)
![alt text](<Screenshot (222).png>)
![alt text](<Screenshot (224).png>)
![alt text](<Screenshot (225).png>)
![alt text](<Screenshot (226).png>)![alt text](<Screenshot (227).png>)