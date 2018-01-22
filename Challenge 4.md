# Challenge 4

Running file showed the file to be a 64-bit executable. After running the program, we are prompted to enter a number that is compared to the "winning" number. Any disassembler will do, but I learned how to use **GDB** a long time ago in a low level programming class, so it's my go to tool.
Disassembling the file revealed several interesting parts:
* The number uses srand, a starting seed value, and time.
* The generated random number is compared to our input.
* Our input is saved on the stack and is retrieved during the comparsion.

The latter two points are important since reverse engineering the lottery generation algorithm is difficult and time consuming.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c4_1.png">
</p>

From the above disassembly, the important lines to look at are **main+142** and **main+150**. 

In line 142, our inputted value is saved onto the stack at an address -x24 bytes from the base pointer.

A function call then retrieves the lottery generated number and loads it into %eax. The address for our input is then read and compared to %eax.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c4_3.png">
</p>

Using gdb, the simplest way to solve this problem is to overwrite the value in %eax and enter the number we initially entered. This effectively circumvents the lottery number generation algorithm.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c4_4.png">
</p>

This technique then reveals the flag

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/c4_5.png">
</p>

flag: **Pr3DictAbleR3sult5**
