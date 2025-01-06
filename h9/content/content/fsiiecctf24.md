+++
title = " FSIIEC CTF Writeup"
date = '2024-09-08T21:50:02+08:00'
draft = false
description = ""
tags = ["CTF", "Cybersecurity", "Writeup"]

+++

# Introduction
This is my writeup for FSIIEC CTF. 

{{< figure src="/content/honest.jpg" title="" >}}

# Boss Password

An obfuscated passage is given.

To deobfuscate the passage, look at the hint closely...
{{< figure src="/content/fsiiectf24/bosshint.png" title="Hint" >}}

The hint obviosuly states the key is "to be as sneaky as possible"

Just take the message literally and use it as a key to decode the message and convert the message to MD5 hash.
{{< figure src="/content/fsiiectf24/bosspassword.png" title="Solved!" >}}

---

# Kagegakure

To solve this challenge, I used curl -L command on Linux (Ubuntu) to read all the contents on the website.

The flag.php looks suspicious, so I change the path to query the 'flag' page, and the flag is discovered!


{{< figure src="/content/fsiiectf24/kagegakure.png" title="The flag" >}}

---

# usbchall

A image file was given, containing an image and a PDF

To solve the challenge, I used Aperi Solve to analyze the image. And the flag is found in the 'Strings' section.
{{< figure src="/content/fsiiectf24/usbchall.png" title="Flag" >}}

# Conclusion


While there are some other challenges I solved, they are not posted as they were too easy for everyone. 

(Almost solved a hard OSINT challenge but... )

Until then! 