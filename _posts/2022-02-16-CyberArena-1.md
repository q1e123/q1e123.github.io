---
layout: post
title:  CyberArena-2021
categories: [write-up]
tag: [write-up]
where: CTFs
permalink: /:categories/:title
desc: Write-up for some problems from  CyberArena-2021
---

## Restaurant
Maybe you can get a free menu!!

Flag format: CTF{sha256}

### Solution

We get an application that seems to create orders for a restaurant. At first I've used strings to see if I can get some useful information, but I didn't see anything that is useful.
![](/assets/img/cyberarena-1/restaurant-strings.png)

It's time to see what this program actually does so I've opened Ghidra to see the code.
![](/assets/img/cyberarena-1/restaurant-main.png)
![](/assets/img/cyberarena-1/restaurant-custom.png)

The main function dosen't look very interesting, but the custom one is using **gets** before return, so I thought that maybe I can do a return to libc attack to get a reverse shell. To be sure of that I've run **checksec** and I found that there is no canery, so this kind of attack is possible.
![](/assets/img/cyberarena-1/restaurant-checksec.png).

At first, I've tried to do it manually (get the offset using a pattern, get gadgets, find a block of memory, find libc version etc), but I've failed. I've started to researh some other ways of doing this attack and I found this video that is using pwntools. The script that I've used to solve this can be found here.

## inject

Hello,

We have received the attached file from a colleague. He told us that the file may be malicious and it was found on the work computer after the night shift was over. Due to low resources in our company, some employees are sharing the same computer.

## Solution

It took some time to find out what this file actually was. At first I've tried volatility but with no luck. After I've used binwalk, but again, no luck. I've started to search on the Internet about security releated stuff that contain the word **inject** and I've found that it the file could be the keystrokes that were recorded using a Rubber Ducky, so I've tried to decode it.
![](/assets/img/cyberarena-1/inject-ducky-decode.png)

And it seems that the hypothesis was right, but those spaces made the file quite ugly so I've used this site to make it easier to read.
![](/assets/img/cyberarena-1/inject-log.png)
![](/assets/img/cyberarena-1/inject-nospace.png)

The pastebin link gave all the information we needed.
![](/assets/img/cyberarena-1/inject-ip.png)

## flash
Hi everyone, I heard that you can calculate quite large numbers at a very high speed.

Flag format: CTF{sha256(number)}

### Solution
At first I used strings to see if I find anything useful, but nothing useful was found.
![](/assets/img/cyberarena-1/flash-strings.png)

So I opened Ghidra and started to analyse the code.
![](/assets/img/cyberarena-1/flash-guessing.png)
![](/assets/img/cyberarena-1/flash-nothing-here.png)

It seems that the program is using a seed to generate four numbers and after it is using addition and xor to compute the password. We have the seed so we can use that to generate the same numbers and addition and xor operations are reversable. The program used to compute the password can be found here.
At first I've compiled it using Visual Studio, but the flag wasn't accepted, so I thought there was something regarding the compiler. I've compiled it after on Linux using **gcc** and **g++** and I've got the correct password.
![](/assets/img/cyberarena-1/flash-running.png)

## yo-admin
Can you use our own ticketing system?

Flag format: CTF{sha256}

### Solution
The website seemes to be a ticketing system where you can put a title and a description to a ticket. At first I've tried the basic **alert(1)** but no luck.

![](/assets/img/cyberarena-1/yo-admin-alert.png)

I've view the code and it seemed quite interesting how the platform is putting the title inside the text box, since it looked like it just puts it inside the value attribute. So what if we would put " at the beginning to inject some code into the page? Well it could work but there is a problem: how can we make sure that the code would execute? What if we would use onfocus so when somebody sees the ticket, the page would make the textbox focused so the code would execute?
![](/assets/img/cyberarena-1/yo-admin-xss-code.png)
![](/assets/img/cyberarena-1/yo-admin-xss-source.png)
![](/assets/img/cyberarena-1/yo-admin-works.png)

And it works!
Now we only need to find where the flag is. We can use webhook.site to send us what the admin sees when the page is loaded but nothing interesting, so I've tried to look at other pages but no luck. This page was having some basic info pages, but there was one more feature of the site that I haven't looked for: the posts. Every post was having an id, that could be seen in the url. What if the admin put some interesting information in one of the posts?
![](/assets/img/cyberarena-1/yo-admin-webhook.png)
![](/assets/img/cyberarena-1/yo-admin-flag.png)

And it worked!

## you-can-run-but-you-cant-hide
A group of robbers managed to steal 2 rings that belonged to Elisabeth II. This happened two weeks ago at the National Museum of History in London. The police didn’t manage to determine yet who the robbers are, but the criminals are posting pictures on the Internet claiming that they will never be caught.

Can you please obtain the answers to the following questions?

### Solution

This challange... was something xD. I've only managed to get 2/4 flags.

We've got an archive containing some images. I've used binwalk to extract the files from each image, since I was quite sure that there is something inside them.

![](/assets/img/cyberarena-1/you-can-run-but-you-cant-hide-binwalk-extract.png)

The wanted PIN was inside one image:
![](/assets/img/cyberarena-1/you-can-run-but-you-cant-hide-binwalk-pin.png)

Now the fun began: where could the other flags be? I've used strings and I found some interesting strings. I used the **exiftool** to see if those strings were metadata and they were. The output was quite big so I've put it into a txt file so I would be able to analyse it easier. Inside one of them I found the desired location:
![](/assets/img/cyberarena-1/you-can-run-but-you-cant-hide-binwalk-location.png)

## undercover-scripts
We are very confused how an attacker managed to bypass Windows Defender on our systems.

Please help us solve this problem by answering the following questions:

### Solution

At first I've tried using volatility2 but I couldn't find the profile, so I've tried finding the profile using volatility3. From chalange description, I've deduced that it was a Microsoft Windows machine (since Windows Defender only works on Windows).
![](/assets/img/cyberarena-1/undercover-scripts-imageinfo.png)

Volatility3 dosen't give the profile, but it gives the Windows version and the system date. We can use that to deduce how the name for that profile would look like.
For the Windows Defender PID I've used pslist. I didn't see any WinDefend so I've searched on Google what is the name of the Windows Defender process.
![](/assets/img/cyberarena-1/undercover-scripts-pslist.png)
![](/assets/img/cyberarena-1/undercover-scripts-SID.png)
