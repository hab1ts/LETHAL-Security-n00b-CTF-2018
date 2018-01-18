# Challenge 2

Running file on the file revealed it to be a zoo archive. Zoo is an archaic compression algorithm that eventually lost out to zip, rar, and other
compression types. 

Kali does not naturally have the ability to uncompress zoo archives. However, debian repos have utilities to deal with
zoo archives. Thus, I added the **debian jessie repo to /etc/apt/sources.list**, updated, than added via **apt-get install zoo**.

After uncompressing the archive, 4 .jpg files were present. Comparing hashes between all the files revealed that one file was different.
**Steghide brute force** and the rockyou wordlist was run on that different file. This revealed the first part of the flag **DONTFORGETTO**

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c2_1.png">
</p>

For the second part of the flag, searching through every file revealed a hidden PNG embedded in the zoo archive.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c2_2.png">
</p>

Carving out the PNG portion of the archive revealed the second part of the flag

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c2_3.png">
</p>

Flag: **DONTFORGETTORTFM**
