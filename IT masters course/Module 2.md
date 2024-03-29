# Prov 3 vs 5
# Target Enumeration and Vulnerability Scanning

Learn to read and study to overcome personal issues

### Target Enumeration
---
What is in scope?
	Target specified by the organisation
What info is already on the internet?
		Graphical view of the target
Looking for all hosts or network devices
Looking for all applications and login prompts
Looking for all usernames and passwords

### Passive Reconnaissance
---
Scanning for info or deriving info without touching the target system directly.
All the places you can get info about the system without interacting with it:
1. DNS
2. Whois
3. GeoIP
4. Reverse IP: finding all websites on that ip e.g hackthetarget
5. Google Dorks
6. Bing
7. Wireless Sniffing
8. Shodan
### Active Reconnaissance
---
Interacting with the target e.g flooding with the system
Vulnerability scanning and port scanning
1. Network Scanning: nmap (look into nmap scripts to identify scripts)
2. Vulnerability Scanning: Rapid7, OpenVas, Metasploit
3. Wireless Interaction: Kismet, Airsnot and Aircrack, Evil Twin
### Application Enumeration
---
1. Browser
2. Nmap
3. Nikto
4. Dirb
### Sniffing
---
Best done on the target machine... get a shell, run tshark
1. Neighboring systems
2. Usernames and passwords
3. Keys
4. Data
### Vulnerability Scanning
Keeps a database of operating systems and applications vulnerabilities
1. Authenticated scans
2. Discovery scans
### Challenges with Vulnerability Scanning
1. Cause outages
2. Run out of hours
3. Network Segmentation
4. Bandwidth and resource considerations
5. Change windows and notifications
6. If a scan is happening when there is an outage
### Social Engineering
Trying to get someone to do something or share something they wouldn't normally do
1. Phishing: Credentials, False invoices, Ransomware, Gift card scams
2. Phishing email and website
3. Whaling
4. Spear phishing
5. Shoulder surfing
6. USB drops
### Social Engineering Tactics
1. Impersonation: Authority, IT Department, Government department
2. Urgency: Limit thought process
3. Fear: Fine, legal action