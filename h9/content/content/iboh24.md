+++
title = "IBOH 2024 Writeup"
date = '2024-09-29T15:10:12+08:00'
draft = false
description = "Writeup for APU IBOH event!"
tags = ["CTF", "Cybersecurity", "Writeup"]

+++

# Introduction
{{< figure src="/content/iboh24/iboh.png" title="" >}}

The annual main event of CTF in Asia Pacific University (APU): International Battle of Hackers, hosted by [FSEC-CC](https://www.linkedin.com/company/forensic-security-research-center-student-section-apu/posts/?feedView=all), with amazing CTF players from not only Malaysia, but other countries such as Singapore and Indonesia participating.

The challenges were difficult in my opinion, and most of them were removed after the event, therefore I did not manage to screenshot the solution for most of them. 

Therefore, here is my humble writeup for one of the crypto challenge: I'll Kill Yall. Enjoy.


{{< figure src="/content/honest.jpg" title="It's honest work">}}


# Crypto: I'll Kill Yall

The challenge provides an attachment of a hand-written message, looks like it's ciphered.

{{< figure src="/content/iboh24/s.png" title="Creepy Message" >}}

After searching in the web, the cipher is identified as the 'Zodiac Killer Cipher'. One of the biggest mystery till this day.

At first the cipher text was unreadable, however, the symbol with a circle and cross should be at the bottom, therefore the image is rotated 180 degrees.

{{< figure src="/content/iboh24/ori.png" title="Found this online" >}}

{{< figure src="/content/iboh24/s2.png" title="Readable now.." >}}

To crack the cipher, head on to this [webpage](https://www.dcode.fr/zodiac-killer-cipher) and enter the code manually.

This is the returned message, which doesn't mean a thing.
{{< figure src="/content/iboh24/fist_dec.png" title="What does it mean?" >}}

To reveal the full ciphered message, increase the height byte value using Hexeditor, and the full message is revealed.
{{< figure src="/content/iboh24/chgHex.png" title="Increase height byte" >}}
{{< figure src="/content/iboh24/test.png" title="Full encrypted message" >}}


 Note that the original image cannot be rotated before changing the height byte, else the note will not reveal.

{{< figure src="/content/iboh24/totata.png" title="Failed to reveal message" >}}

Rotate the revealed cipher and redo the deciphering process , a plaintext message will show 😨.
{{< figure src="/content/iboh24/flagstring.png" title="Deciphered Message" >}}

The flag should start after 'THIS IS THE FLAG', which is 'KILLINGPEOPLEE?AFSTOPFED'.
But the flag was rejected when entered.

After sanity checking with the challenge creator, turns out the question mark should be replaced by 'z', as there is a bug within the calculation of the deciphering process, causing the question mark to appear.

{{< figure src="/content/iboh24/message.png" title="Sanity Check Message" >}}

I was dumb enough to try the new flag 'KILLINGPEOPLEEZAFSTOPFED', which was rejected again btw. 

After reading the message a few times, it doesn't make sense to include everything after EZAF. 

FLAG: IBOH24{KILLINGPEOPLEEZAF}

---

# Conclusion

Our team have won 4th place for local category! 🥳 

Could not have done it without my teammates:
[ZD](https://www.linkedin.com/in/pua-zhen-da-31165b248/) & [Yvonne](https://www.linkedin.com/in/yvonne-chan-217862266/) 🥰🥰🥰
{{< line_break >}}
{{< line_break >}}
Till next time! 😬
{{< figure src="/content/uwma.gif" title="" >}}
{{< line_break >}}

---


