![[Pasted image 20240219165039.png]]
acciommfb using rsa

| ip address | Status | Subdomain | Extras |
| :--- | ---- | ---- | ---- |
| 154.113.153.112 | 200 | www.accionmfb.com |  |
| 154.113.153.113 | unreachable | contact.accionmfb.com |  |
| 154.113.153.114 | 200 | dms.accionmfb.com | Glassfish Server Open Source Edition. v5.1.0 (Outdated - 7.0.12) |
| 154.113.153.115 | unreachable | digital.accionmfb.com |  |
| 154.113.153.116 | unreachable | chatbot.accionmfb.com |  |
| 52.160.106.88 | unreachable | api.accionmfb.com |  |
| 196.1.179.169 | unreachable | audit360.accionmfb.com |  |
| 52.98.23.248 | 200 | autodiscover.accionmfb.com | autod.ms-acdc-autod.office.com (Outlook login page) |
| 40.118.188.252 |  | web.accionmfb.com |  |
| 196.1.179.174 |  | webtest.accionmfb.com |  |
|  |  |  |  |
|  |  |  |  |
todo 
1. run burpsuite scan -- done
2. check the above links both port 80 and 443 -- done
3. check amass for all links
4. you might want to make all ips a new page linked to this page - fashi
5. run reconftw -- too slow
6. document each link
7. run nmap for all ips
8. try to reach each link and indicate if reachable
9. run dirb, wfuzz and the likes on each ip
10. append a POC for each
11. check daniels file again
12. Run nessus on all 
13. try this route: https://rastating.github.io/how-i-hacked-bobby/

to get first ip in subnet do subnet mask AND the ip address
to get the last ip in subnet do inverse of subnet mask OR the ip address
# Amass results
---
![[Pasted image 20240220131801.png]]
![[Pasted image 20240220131905.png]]
![[Pasted image 20240220132009.png]]
![[Pasted image 20240220132106.png]]
amass enum -d accionmfb.com --brute --active
accionmfb.com (FQDN) --> a_record --> 154.113.153.112 (IPAddress)
accionmfb.com (FQDN) --> node --> www.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> mx_record --> mx2.zoho.com (FQDN)
accionmfb.com (FQDN) --> mx_record --> mx3.zoho.com (FQDN)
accionmfb.com (FQDN) --> mx_record --> mx.zoho.com (FQDN)
www.accionmfb.com (FQDN) --> cname_record --> accionmfb.com (FQDN)
mx3.zoho.com (FQDN) --> a_record --> 204.141.43.44 (IPAddress)
mx.zoho.com (FQDN) --> a_record --> 204.141.43.44 (IPAddress)
154.113.0.0/16 (Netblock) --> contains --> 154.113.153.112 (IPAddress) --running
204.141.42.0/23 (Netblock) --> contains --> 204.141.43.44 (IPAddress)
37282 (ASN) --> managed_by --> MAINONE (RIROrganization)
37282 (ASN) --> announces --> 154.113.0.0/16 (Netblock)
2639 (ASN) --> managed_by --> ZOHO-AS - ZOHO (RIROrganization)
2639 (ASN) --> announces --> 204.141.42.0/23 (Netblock)
accionmfb.com (FQDN) --> node --> api.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> node --> test.igree.accionmfb.com (FQDN) -- done 
api.accionmfb.com (FQDN) --> a_record --> 52.160.106.88 (IPAddress) --done
test.igree.accionmfb.com (FQDN) --> a_record --> 102.216.200.246 (IPAddress) -- done
52.160.0.0/11 (Netblock) --> contains --> 52.160.106.88 (IPAddress) -- done 
102.216.200.0/24 (Netblock) --> contains --> 102.216.200.246 (IPAddress) --done
8075 (ASN) --> managed_by --> MICROSOFT-CORP-MSN-AS-BLOCK - Microsoft Corporation (RIROrganization)
8075 (ASN) --> announces --> 52.160.0.0/11 (Netblock)
36920 (ASN) --> managed_by --> KKON, NG (RIROrganization)
36920 (ASN) --> announces --> 102.216.200.0/24 (Netblock)
accionmfb.com (FQDN) --> node --> digital.accionmfb.com (FQDN) -- done 
digital.accionmfb.com (FQDN) --> a_record --> 154.113.153.115 (IPAddress) -- done
154.113.0.0/16 (Netblock) --> contains --> 154.113.153.115 (IPAddress) -- done
accionmfb.com (FQDN) --> node --> helpdesk.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> node --> audit360.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> node --> intranet.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> node --> dms.accionmfb.com (FQDN)
helpdesk.accionmfb.com (FQDN) --> cname_record --> customer-sdpondemand.manageengine.com (FQDN)
audit360.accionmfb.com (FQDN) --> a_record --> 196.1.179.169 (IPAddress)
intranet.accionmfb.com (FQDN) --> a_record --> 196.1.179.170 (IPAddress)
dms.accionmfb.com (FQDN) --> a_record --> 154.113.153.114 (IPAddress)
196.1.176.0/22 (Netblock) --> contains --> 196.1.179.169 (IPAddress)
196.1.176.0/22 (Netblock) --> contains --> 196.1.179.170 (IPAddress)
154.113.0.0/16 (Netblock) --> contains --> 154.113.153.114 (IPAddress)
37629 (ASN) --> managed_by --> eStreamNetworks-AS (RIROrganization)
37629 (ASN) --> announces --> 196.1.176.0/22 (Netblock)
accionmfb.com (FQDN) --> node --> mobile.accionmfb.com (FQDN)
mobile.accionmfb.com (FQDN) --> a_record --> 154.113.153.115 (IPAddress)
accionmfb.com (FQDN) --> node --> web.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> node --> contact.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> node --> chatbot.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> node --> autodiscover.accionmfb.com (FQDN)
web.accionmfb.com (FQDN) --> a_record --> 40.118.188.252 (IPAddress)
contact.accionmfb.com (FQDN) --> a_record --> 154.113.153.113 (IPAddress)
chatbot.accionmfb.com (FQDN) --> a_record --> 154.113.153.116 (IPAddress)
autodiscover.accionmfb.com (FQDN) --> cname_record --> autodiscover.outlook.com (FQDN)
mx2.zoho.com (FQDN) --> a_record --> 136.143.183.44 (IPAddress)
accionmfb.com (FQDN) --> node --> wakandax.accionmfb.com (FQDN)
accionmfb.com (FQDN) --> node --> test.ibank.accionmfb.com (FQDN)
wakandax.accionmfb.com (FQDN) --> a_record --> 52.160.106.88 (IPAddress)
test.ibank.accionmfb.com (FQDN) --> a_record --> 154.113.153.113 (IPAddress)
154.113.0.0/16 (Netblock) --> contains --> 154.113.153.113 (IPAddress)
154.113.0.0/16 (Netblock) --> contains --> 154.113.153.116 (IPAddress)
40.112.0.0/13 (Netblock) --> contains --> 40.118.188.252 (IPAddress)
136.143.176.0/21 (Netblock) --> contains --> 136.143.183.44 (IPAddress)
8075 (ASN) --> announces --> 40.112.0.0/13 (Netblock)
2639 (ASN) --> announces --> 136.143.176.0/21 (Netblock)
customer-sdpondemand.manageengine.com (FQDN) --> cname_record --> csdp.manageengine.com (FQDN)
autodiscover.outlook.com (FQDN) --> cname_record --> atod-g2.tm-4.office.com (FQDN)
atod-g2.tm-4.office.com (FQDN) --> cname_record --> autod.ms-acdc-autod.office.com (FQDN)
accionmfb.com (FQDN) --> ns_record --> ns05.domaincontrol.com (FQDN)
accionmfb.com (FQDN) --> ns_record --> ns06.domaincontrol.com (FQDN)
csdp.manageengine.com (FQDN) --> a_record --> 136.143.190.99 (IPAddress)
autod.ms-acdc-autod.office.com (FQDN) --> a_record --> 52.96.111.88 (IPAddress)
autod.ms-acdc-autod.office.com (FQDN) --> a_record --> 52.96.9.8 (IPAddress)
autod.ms-acdc-autod.office.com (FQDN) --> a_record --> 52.96.15.8 (IPAddress)
autod.ms-acdc-autod.office.com (FQDN) --> a_record --> 52.96.182.120 (IPAddress)
autod.ms-acdc-autod.office.com (FQDN) --> aaaa_record --> 2603:1026:204::8 (IPAddress)
autod.ms-acdc-autod.office.com (FQDN) --> aaaa_record --> 2603:1026:207:cd::8 (IPAddress)
autod.ms-acdc-autod.office.com (FQDN) --> aaaa_record --> 2603:1026:c03:3000::8 (IPAddress)
autod.ms-acdc-autod.office.com (FQDN) --> aaaa_record --> 2603:1026:c03:7079::8 (IPAddress)
ns05.domaincontrol.com (FQDN) --> a_record --> 97.74.102.3 (IPAddress)
ns05.domaincontrol.com (FQDN) --> aaaa_record --> 2603:5:2160::3 (IPAddress)
136.143.190.0/23 (Netblock) --> contains --> 136.143.190.99 (IPAddress)
2639 (ASN) --> announces --> 136.143.190.0/23 (Netblock)
ns06.domaincontrol.com (FQDN) --> a_record --> 173.201.70.3 (IPAddress)
ns06.domaincontrol.com (FQDN) --> aaaa_record --> 2603:5:2260::3 (IPAddress)
97.74.96.0/20 (Netblock) --> contains --> 97.74.102.3 (IPAddress)
52.96.0.0/14 (Netblock) --> contains --> 52.96.182.120 (IPAddress)
52.96.0.0/14 (Netblock) --> contains --> 52.96.15.8 (IPAddress)
52.96.0.0/14 (Netblock) --> contains --> 52.96.9.8 (IPAddress)
52.96.0.0/14 (Netblock) --> contains --> 52.96.111.88 (IPAddress)
2603:1000::/26 (Netblock) --> contains --> 2603:1026:c03:7079::8 (IPAddress)
2603:1000::/26 (Netblock) --> contains --> 2603:1026:c03:3000::8 (IPAddress)
2603:1000::/26 (Netblock) --> contains --> 2603:1026:207:cd::8 (IPAddress)
2603:1000::/26 (Netblock) --> contains --> 2603:1026:204::8 (IPAddress)
44273 (ASN) --> managed_by --> DYNAMICNET (RIROrganization)
44273 (ASN) --> announces --> 97.74.96.0/20 (Netblock)
44273 (ASN) --> announces --> 2603:5:2100::/40 (Netblock)
8075 (ASN) --> announces --> 52.96.0.0/14 (Netblock)
8075 (ASN) --> announces --> 2603:1000::/26 (Netblock)
173.201.64.0/20 (Netblock) --> contains --> 173.201.70.3 (IPAddress)
2603:5:2100::/40 (Netblock) --> contains --> 2603:5:2160::3 (IPAddress)
44273 (ASN) --> announces --> 173.201.64.0/20 (Netblock)
2603:5:2260::/44 (Netblock) --> contains --> 2603:5:2260::3 (IPAddress)
44273 (ASN) --> managed_by --> GODADDY-DNS, DE (RIROrganization)
44273 (ASN) --> announces --> 2603:5:2260::/44 (Netblock)


# Nikto results for 196.1.179.170
---
![[Pasted image 20240220130709.png]]

# Nmap results for 196.1.179.170
---
![[Pasted image 20240220130955.png]]

# Dirb results for 196.1.179.170
---
try another tool similar to dirb
![[Pasted image 20240220131433.png]]