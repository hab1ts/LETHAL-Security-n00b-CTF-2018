# Challenge 6

For this challenge, we were presented with a pcap file. The first step was to run tcdump on the file to look for any interesting information. Based on the information gleamed from tcpdump, we can figure out that the pcap has WPA traffic that runs on channel 11 and has a ESSID of "RockYou". Given that it's encrypted, we need to find the passkey.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c6_1.png">
</p>

The name of the access point gives us a huge clue about what the passkey might be. The RockYou wordlist comes pre-installed in Kali Linux, so let's try that first. Using aircrack-ng and the RockYou wordlist, the passkey, **linkinpark**, was discovered very quickly.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c6_3.png">
</p>

Opening the file in Wireshark again, we are now able to enter the WPA password and decrypt the contents. However, if we try to extract the object directly, we see that the file is fragmented

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c6_6.png">
</p>

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c6_7.png">
</p>


Searching by http, we see 3 attempts to obtain flag.png. Since we know that the file is incomplete, the based we can is to recover as much of the file as possible. 

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c6_8.png">
</p>


Following the TCP packet, we find the beginning spot of the PNG, magic numbers 89 50, and carve from that spot to the end of the packet.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c6_4.png">
</p>

Saving this image reveals parts of the flag. The rest can be concluded by looking at the image.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c6_5.png">
</p>

flag: **wifipackets**



