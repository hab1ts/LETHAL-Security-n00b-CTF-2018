# Challenge 9 - Badge Challenge

**TODO: add photos**

At the CTF round up, we were presented with a badge that could be used to complete Challenge 9. The file in question was an mp3 file with an embedded flag. Through adjustments to the badge, one could decipher the flag and complete all the challenges.

On the back of the badge was the first clue to deciphering the message. Based purely on the visual aspect of the clue, this appeared to be a **Base64** encoded string. Running the string through CyberChef, the output was shown to be **What is the 76th letter?**

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/IMG_3994.JPG">
</p>

Since there are not 76 letters in the English alphabet, my first instinct was to go to an ASCII table. Looking up the value for the 76th character in an ASCII table showed the letter to be **L**.  On the front of the badge was 8 switches. These 8 switches match up with 1 byte. Thus, converting L into binary, **01001100** gives us the answer for step 2. For this, we're greeted with the device turning on.

<p align="center">
<img src="https://github.com/hab1ts/LETHAL-Security-n00b-CTF-2018/blob/master/CTF%20Images/IMG_3993.JPG">
</p>

The final step of the challenge was to decipher the message in the mp3 file. The badge has a microphone input and two filters, one low pass and one high pass. One must then adjust each such that only the lower set of LEDS blink in accordance with the mp3 file. The first step was to tune the right filter such that the lower LEDS were barely dim. Next, plug in a 3.5 mm audio cable to the audio out. As the mp3 file is playing, tune the left filter such that the top 4 lights stop blinking.

What should start happening next is the bottom 4 lights blinking in morse code. A short pulse of lights indicate a dot and a long pulse of lights indicate a dash. After a few attempts at transcribing, one should get the pattern **.....--.-.-.--....--.-.-.-**.  Without any breaks, the number of combinations are in the millions. However, there are a few patterns which should help narrow down things. The first thing I noticed was that there appeared to be a pattern. **-.-** appeared evenly spaced, as did **-.-.-** and **.-**. This meant the message was **_ACK_ACK**. Trial and error and deductive reasoning led to the final answer **HACKBACK**.

flag: **HACKBACK**
