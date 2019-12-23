# USB-Reset-Button
A button to reset a webcam when its microphone goes haywire

___

My friend in Canada, whom I video call a lot, has a recurring issue with her webcam: her laughter is fairly high-pitched and sharp, which causes the microphone in her webcam to start resonating at a *very* annoying frequency... and it won't stop unless she unplugs it, and plugs it back in again!

Of course, she doesn't know when this issue occurs unless I tell her about it, at which point she has to go digging at the back of her PC to find the right plug... which can take a couple tries! Understandably, she gets pretty aggravated at the webcam every time this happens, now.

I decided that, since this issue happens somewhat frequently, I'm going to do something about it. My vision: a physical button she can press that momentarily interrupts the power going to the webcam, causing it to reboot.

[Rough Sketch]

Alright, this looks good! Time to go to Ax-Man Surplus to find supplies. I decided to hit up their Fridley location for the first time, since I was in the neighborhood. From what I can tell, Fridley's got the best selection of switches and buttons. I found this fantastic pinball flipper button; very durable, perfect for my friend to smack the next time her webcam acts up. This was a good "interface", but it's purely mechanical. I still need a momentary switch to do the electrical work. Preferably, one that is "normally closed" so the webcam gets power when the button *isn't* pressed. Eventually, browsing the aisles, I stumbled upon the *perfect* momentary switch for the job. Plenty of travel, but the "click" happens almost instantly with the slightest bit of pressure applied. Only one problem - the switch has two terminals, and it's "normally open", meaning it'll only deliver power when pressed. No worries! This should be an easy fix, we just need a transistor to invert the switch. Luckily, Ax-Man has plenty of those!

I opted for a P-Channel Mosfet, because I wanted to switch the +5 volt supply rail of the USB bus. Implementing this transistor would be very easy if our switch had 3 pins: "closed", "open", and "common"... We could just toggle the gate between +5v and GND. But our switch only has 2 pins, which means we need a pull down resistor to keep the gate held at GND until the switch, connecting the gate and +5v, is pressed. Here's my circuit:

![Circuit](https://i.imgur.com/xUzkBll.png)

The USB data pins and GND are just passed through, but the switching happens on the high-side (as described).

Looks good! And it's simple... easy to breadboard. When I built the circuit, and plugged a USB flash drive in to test, it worked beautifully! When I connected the wires to simulate the switch being pressed, the flash drive disappeared... then re-appeared when I simulated the switch being released! Next, I tried plugging in the webcam... but that failed! I couldn't get an image, or the device itself to be recognized in Windows. It just didn't work. Why would the flash drive work, but the webcam not?!

But then, it occurred to me... What if the webcam requires a high enough data speed to necessitate a "twisted pair" data line?

Twisted Pair is what you see in cables such as telephone or ethernet (or USB). Data is transmitted via alternating current to facilitate long-distance communication, and each "pair" of data lines is twisted together to reduce noise. By taking the two jumpers on my breadboard and twisting them together, the webcam suddenly started working! A crystal-clear picture, interrupted by the connecting of the "button" jumper.

Time to design an enclosure!
