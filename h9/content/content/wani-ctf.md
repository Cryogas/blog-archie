+++
title = 'Wani Ctf 2024 Writeup'
date = 2024-06-24T23:15:36+08:00
draft = false
description = "Writeup for Wani-CTF 2024"
tags = ["Writeup"]
+++

This is my writeup for Wani CTF, an event organized by Osaka University CTF Club, Wani Hackase (Rank 304th)


# Forensics

## Surveillance of sus 

A binary file is given, and after some investigation, it has a RDP8BMP Header.

![Image](/content/wani/hex.png)
<figcaption>This is the capti for the image.</figcaption>

To get the BMP images, I have referred to this [article](https://medium.com/@yashkumarnavadiya/htb-no-place-to-hide-easy-forensics-challenge-b025c864607a) and use a Python Script (bmc-tools).

After all the bmp files are recovered, the flag can be readed in plain sight if the view is changed to "Large icons".

![Image](/content/wani/large-icon.png)

Flag : FLAG{RDP_is_useful_yipeee}

---

## Tiny USB

A disk image file is given. 

FTK Imager is used to read and analyze the disc file. After some digging, the flag is found!

![Image](/content/wani/usb.png)

Flag: FLAG{hey_i_just_bought_a_usb}

---

## Tiny-10px

A small image is given.

![Image](/content/wani/chal_tiny_10px.jpg)

Based on my instincts, this could be one of those image steganography where the author resized the image of a large image. 

So I followed the instructions of this [article](https://cyberhacktics.com/hiding-information-by-changing-an-images-height/) to recover the image by changing the hex values of height and width (multiple times).

![Image](/content/wani/hex-small.png)


After some effort, a message is visible from the image. (although reading it may take some time).

![Image](/content/wani/new.jpg)

Flag: FLAG{b1g_en0ugh}

---

# Conclusion

This is my 6th CTF event participation, and I am happy that I can solve some easy to medium level challenges now! 

Thank you for reading.






