+++
title = "UIUCTF 2024 Writeup"
date = 2024-07-01T00:00:00Z
draft = false
description = "Writeup for UIUCTF 2024"
tags = ["Writeup"]
+++



{{< callout emoji="⚡️" text="UIUCTF2024, hosted by SIGPwny, the cybersecurity club at the University of Illinois Urbana-Champaign (UIUC)." >}}


For this CTF competition, I am only able to do some OSINT challenges, so here is my writeup for UIUCTF2024!


# OSINT


## Hip With the Youth

This challenge requires players to find the flag on the social media of Long Island Subway Authority (LISA).

From the Instagram account, there are no flags visible.


{{< figure src="content/uiuctf24/lisa-ins.png" title="Lisa's Instagram Account" >}}


After looking through the posts and followers list, nothing useful is found. However, when I checked out the Threads account, and the flag is found immediately on the first thread.

{{< figure src="content/uiuctf24/lisa-thread-flag.png" title="" >}}


FLAG: uiuctf{7W1773r_K!113r_321879}

---


## An Unlikely Partnership

This challenge requires players to find out the partnership of LISA with a surprise influencer.

The LinkedIn account of LISA transit is accessible from the Threads page.

{{< figure src="content/uiuctf24/lisa-th.png" title="" >}}

To find the influencer involved, I poked around every link and posts on the account. Then I came across this...

{{< figure src="content/uiuctf24/lisa-skills.png" title="" >}}
{{< figure src="content/uiuctf24/lisa-endorsement.png" title="" >}}

Who is UIUC Chan? Looks sus...

After clicking into UIUC Chan's LinkedIn page, the flag is found!

{{< figure src="content/uiuctf24/uiuc-chan.png" title="" >}}  

FLAG: uiuctf{0M160D_U1UCCH4N_15_MY_F4V0r173_129301}

---

## Night

A night view photo is given, requiring players to find the street name and city name of where the photo is taken.

{{< figure src="content/uiuctf24/chal.jpg" title="" >}}

At first, I tried searching by using keywords such as "building with a hemisphere roof" and "building with a dome", but I can't get a result similar with the reference image.


After using Google Images, this is the closest result I can get (pretty useful)

{{< figure src="content/uiuctf24/longfellow.png" title="" >}}

And here is a question I asked ChatGPT for a little hint...

{{< figure src="content/uiuctf24/chat-boston.png" title="Sorry Mods.." >}}

All there is left to do is to move the little yellow man in Google Maps around to get the exact same view. After throwing the little man around, this is what I got..

{{< figure src="content/uiuctf24/i90.png" title="" >}}

Tried uiuctf{I90,Boston} but it didn't work. So I asked the moderator. Here is his(her) response.

{{< figure src="content/uiuctf24/mod.png" title="hmm..." >}}

So I backed up a little, and here is what I found!

{{< figure src="content/uiuctf24/arlington.png" title="Here is the correct location." >}}
{{< figure src="content/uiuctf24/night-answer.png" title="" >}}

FLAG: uiuctf{Arlington Street, Boston}

---

In conclusion, although I still find some challenges difficult, I thoroughly enjoyed solving the OSINT puzzles and felt a great sense of satisfaction upon completing them.














