# USB-Reset-Button
A button to reset a webcam when its microphone goes haywire

___

My friend in Canada, whom I video call a lot, has a recurring issue with her webcam: her laughter is fairly high-pitched and sharp, which causes the microphone in her webcam to start resonating at a *very* annoying frequency... and it won't stop unless she unplugs it, and plugs it back in again!

Of course, she doesn't know when this issue occurs unless I tell her about it, at which point she has to go digging at the back of her PC to find the right plug... which can take a couple tries! Understandably, she gets pretty aggravated at the webcam every time this happens, now.

I decided that, since this issue happens somewhat frequently, I'm going to do something about it. My vision: a physical button she can press that momentarily interrupts the power going to the webcam, causing it to reboot.

[Rough Sketch]

Alright, this looks good! Time to go to Ax-Man Surplus to find supplies. I decided to hit up their Fridley location for the first time, since I was in the neighborhood. From what I can tell, Fridley's got the best selection of switches and buttons. I found this fantastic pinball flipper button; very durable, perfect for my friend to smack the next time her webcam acts up. This was a good "interface", but it's purely mechanical. I still need a momentary switch to do the electrical work. Preferably, one that is "normally closed" so the webcam gets power when the button *isn't* pressed. Eventually, browsing the aisles, I stumbled upon the *perfect* momentary switch for the job. Plenty of travel, but the "click" happens almost instantly with the slightest bit of pressure applied. Only one problem - the switch has two terminals, and it's "normally open", meaning it'll only deliver power when pressed. No worries! This should be an easy fix, we just need a transistor to invert the switch. Luckily, Ax-Man has plenty of those!
