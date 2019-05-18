---
layout: post
---

# [VulnHub]DC:6 WriteUp

Today I am starting to write first blog post.I decided to write my pwned machines from vulnhub site.
I also release writeups of hackthebox machines in my github page.You can go here:[Github](https://github.com/fatihh92/HackTheBox-Writeups)

The machine level is beginner.So I pwned that in a short time.First of all I used these tools;

### Tools
* netdiscover
* nmap
* wpscan
* searchsploit

### Steps 

I need to find target machine ip So I used `netdiscover` tool.I started to scan my network.
Network adapter was in briged mode  by the way.And I detected target ip : `192.168.1.104`

![deneme](/img/DC6/1.png)

I started nmap scanning after I found target ip normally.there is open 2 common port.

![deneme](/img/DC6/2.png)

But I saw some info when I used `sC` flag.The flag everytime work for me.
You can see there is have a domain name and the site is wordpress site.

![deneme](/img/DC6/3.png)

I added the ip address to `/etc/hosts` file.

![deneme](/img/DC6/4.png)

I went to index page .Actually I went to look source codes of page ,I did but forget take screenshot :D

![deneme](/img/DC6/5.png)

I always use wpscan scanning for find users .I did again and I got some username .I got my note the usernames
Maybe it gonna work

![deneme](/img/DC6/6.png)

The clue actually was in the machine page. Its author gave us for save our time.
If read machine page You can see how many time saved.

![deneme](/img/DC6/7.png)

Honestly I new learnt that.we can do password attack with wpscan.It was very useful.
I used like that : `wpscan --url http://wordy -U user.txt -P password.txt`

![deneme](/img/DC6/8.png)

I logon with the creds.And I went to admin page.The point was that I just stuck.
Actually I had some suspicions about `activity monitor ` part but I wasn't sure.
So I looked google for be sure.

![deneme](/img/DC6/9.png)

Googling didn't work for me but I decided to try my chance on one of my favorite tools.
`Searchsploit` is very useful tool.I found some exploits and selected one of them.  

![deneme](/img/DC6/10.png)

But I was need to manage some parts of it like everytime.I run it and I got reverse shell.

![deneme](/img/DC6/11.png)


![deneme](/img/DC6/12.png)
![deneme](/img/DC6/13.png)
![deneme](/img/DC6/14.png)
![deneme](/img/DC6/15.png)
![deneme](/img/DC6/16.png)
![deneme](/img/DC6/17.png)
![deneme](/img/DC6/18.png)
![deneme](/img/DC6/19.png)

[back](./)