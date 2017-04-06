---
title: How To Allow Printing Jobs From Certain Computers To A Certain Printer
layout: post
permalink: /blog/:year-:month-:day-:title.html
---

To allow printing from certain computers to a certain printer, edit the /etc/cups/cupsd.conf file and see if the <Location /printers/printer_name> is already present. 

 <Location /printers/printer_name>
 </Location>


 # Allow printing to printer MyLaserJet from 
 #    itself and computers 192.10.2.5 and 192.10.2.6
 <Location /printers/MyLaserJet>
 ...
 Order deny,allow
 Deny from all
 Allow from 127.0.0.1
 Allow from 192.10.2.5
 Allow from 192.10.2.6
 </Location>
 
 # Allow printing to printer MyLaserJet from 
 #    itself and all computers on subnet 192.10.2.x
 <Location /printers/MyLaserJet>
 ...
 Order deny,allow
 Deny from all
 Allow from 127.0.0.1
 Allow from 192.10.2.0/255.255.255.0
 </Location>
