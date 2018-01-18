# Challenge 3

Running file on this file revealed it to be a PE file. Thus, it seemed best to attack it using a windows VM.

Looking at the file in hex showed it was written using .NET 4.5. Thus, it might be possible
to disassemble it using a .NET/C# disassembler.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c3_1.png">
</p>

Decomposing the PE showed two interesting strings, a passphrase in clear text and the encyrpted flag
<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c3_2.png">
</p>
<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c3_3.png">
</p>

I iniitally tried different methods to try and crack the AES encryption. However, it became obvious that
the salt would make it very difficult.

Eventually, I entered the passphrase into the box and the flag popped out

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c3_4.png">
</p>

** FLAG: thatwasntthekonamicode **
