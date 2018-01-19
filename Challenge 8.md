# Challenge 8 - Incident Response: Dead Malware

Running file on the file showed it to be stripped binary. This means that any debugging symbols have been removed. Still, using a disassembler can reveal useful bits of information.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c8_1.png">
</p>

Using radare2, a few interesting strings popped up. First, a string for **c2.lethalsecurity.com**. This might be the domain for a command and control server. Second a string for admin and what might appear to be a flag. Unfortunately, this appeared to be a false flag.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c8_2.png">
</p>

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c8_3.png">
</p>

The next step was to do a dynamic analysis of the program. The program was ran with wireshark capturing traffic. What was seen is a clear attempt to resolve where **c2.lethalsecurity.com** was located. If no response was given, the program would terminate.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c8_4.png">
</p>

With this knowledge, I setup some virtual infrastructure to resolve the DNS query and respond to any http requests. Through some trial and error, the general workflow acted as such:
* When run, file8 reached out to a DNS server to resolve the ip for c2.lethalsecurity.com
* Once the IP is found, the file attempts to connect to port 8822. If no connection can be established, the program quits
* If the connection is established with a web server, hardcoded credentials are then transmitted to /login.php
* By faking the DNS, we can redirect to an address and server of our choosing and intercept the traffic along the way.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/Challenge8.jpg">
</p>

After looking through several GETS between the infected machine and the webserver, we can find the flag

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c8_5.png">
</p>

flag: **dynamic0**
