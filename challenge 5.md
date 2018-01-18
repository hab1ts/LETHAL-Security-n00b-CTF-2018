# Challenge 5

Running the executable revealed this question to be a buffer overflow question. Our job was to overwrite the buffer and fill it with the value **'0xdeadc0de'**.

After loading up the file in gdb and disassembling main, the stack initiation was revealed to be 0x20 bytes. Further code analysis shows no alteration of the buffer. Afterwards, the program adds 4 A's that indicate the value we want to overwrite.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c5_1.png">
</p>

Using this knowledge, filling the buffer and overwriting the value becomes trivial. A perl command with our desired text is redirected to a file. That file is then used as input when we run the program under gdb.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c5_3.png">
</p>

flag: **ctfsarefun!**
