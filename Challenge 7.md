# Challenge 7

Like all of the challenges presented in this CTF, the file had the extension removed. Also, instead of looking for the flag, we were tasked with finding the root password. Running file on the file only gave us "data" as its type. Running **binwalk -e** on the file revealed several compressed img files with cramfs extension. A Google search showed that cramfs is commonly used in embedded Linux.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c7_1.png">
</p>

Also within the data was a LUA file called Install.lua. Thinking this might lead to the solution, I spent a lot of time correcting the data and restoring the correct offset. Unfortunately this lead to nowhere.

Eventually, I tried to mount the images directly. I found an article on reverse engineering firmware https://lfto.me/reverse-engineering-dvr-firmware

The most important step was stripping the mkimage header from the image. The command **dd bs=1 skip=64 if=romfs-x.cramfs.img of=romfs-x2.crafs.img** gave an image that should now be ready to be mounted.  Unfortunately, Kali 2.0 does not have cramfs support built into the kernel. 

However, to analyze the contens, one can simply use 7zip **(7z e romfs-x2.crafs.img)** to extract the img contents.

Looking under /etc/passwd, the password hash appeared encrypted. 

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c7_3.png">
</p>

While John the Ripper may have solved the problem eventually, a Google search for the hash revealed the password.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c7_4.png">
</p>

flag: **zlxx.**
