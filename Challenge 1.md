# Challenge 1

The only information given about this file was that it was linux-based.
Running **file** on the file revealed it to be a 32-bit executable.

![img 1](https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c1_1.png)

Executing the file wrote "First Challenge for noobCTF!" to the console

Using **hexdump -C** allowed the executable to be disassembled into human readable format.
From there, simply browsing through the dump revealed the flag

![img 2](https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c1_2.png)

**thisflagistooeasy**
