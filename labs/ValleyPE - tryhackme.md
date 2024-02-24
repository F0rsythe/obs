## Open Ports 
---

PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
37370/tcp open  unknown

## Version
---
PORT      STATE SERVICE VERSION
37370/tcp open  ftp     vsftpd 3.0.3
Service Info: OS: Unix
## Pages from port 80
---
Target: http://10.10.198.237/FUZZ/
000000120:   200        16 L     58 W       946 Ch      "gallery"        
000000157:   200        14 L     40 W       567 Ch      "static"         
000000386:   403        9 L      28 W       278 Ch      "icons"          
000002050:   200        17 L     70 W       1140 Ch     "pricing"     


**Target: http://10.10.198.237/pricing/notes.txt**
J,
Please stop leaving notes randomly on the website
-RP

#### From url/gallery
---

000000149:   403        9 L      28 W       278 Ch      ".htaccess"      
000000371:   200        16 L     58 W       946 Ch      "."              
000000529:   403        9 L      28 W       278 Ch      ".html"          
000001299:   200        140 L    394 W      3940 Ch     "gallery.html"   
000001556:   403        9 L      28 W       278 Ch      ".htpasswd"      
000001822:   403        9 L      28 W       278 Ch      ".htm"           
000002092:   403        9 L      28 W       278 Ch      ".htpasswds"     
000004616:   403        9 L      28 W       278 Ch      ".htgroup"       
000007069:   403        9 L      28 W       278 Ch      ".htaccess.bak"  

000008678:   403        9 L      28 W       278 Ch      ".htuser"        
000011450:   403        9 L      28 W       278 Ch      ".htc"           
000011449:   403        9 L      28 W       278 Ch      ".ht"      
