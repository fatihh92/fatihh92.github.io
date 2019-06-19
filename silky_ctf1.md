---
layout: post
---

# [VulnHub]Silky-CTF: 0x01 WriteUp

Hi guys .I will talk about a vulnhub machine it's name is [Silky-CTF 0X01](https://www.vulnhub.com/entry/silky-ctf-0x01,306/).
It was different for me.It is easy machine but You need to think simple. Let's start 


### Tools

* nmap
* dirbuster
* python
* hydra
* basic linux commands

### Steps 

Tradational first step is  nmap :D I started to enumerate network.
And There is just open 2 port as you see.But I catched first clue.It is `robots.txt` file.
The file has always been important . Because You can see directories,files clearly.
And I saw `notes.txt` file .

![silky1](/img/silky1/1.png)

------------------------------
I saw there is have `notes.txt` . And it was disallowed for every agent.It must be valuable.

![silky1](/img/silky1/2.png)

------------------------------
I went to there and I saw germany words.I was need to translate it .

![silky1](/img/silky1/3.png)

------------------------------
I used `google translate` .

![silky1](/img/silky1/4.png)

------------------------------
I started use `dirbuster` with medium dirb list .I used the tool because faster than `dirb` .
I catched `script.js` .And I went to there .

![silky1](/img/silky1/5.png)

------------------------------
I saw the word and I remember one step ago.I thought it must be start of password .
So I need last two character. 

![silky1](/img/silky1/6.png)

------------------------------
I found the easy python script .I run it for generate wordlist.

![silky1](/img/silky1/7.png)


![silky1](/img/silky1/8.png)

------------------------------
I put passwords in `pass.txt` file .And I looked how many lines is wordlist?

![silky1](/img/silky1/9.png)

------------------------------
I started brute force with `hydra`.If you dont know the tool You must learn because
very usefull.You can attack almost every service:`ftp,smb,smtp,ssh..etc`
`-l` for username and `-P` for password list.And I found password:`s1lKy#5`.

![silky1](/img/silky1/10.png)

------------------------------
I could login with ssh

![silky1](/img/silky1/11.png)

------------------------------
I started basic enumeration.I found a file that is have root rights.I generally use [the page](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/) 
for privilege escalation

![silky1](/img/silky1/12.png)

------------------------------
And I started enumerate the file .There is have weird thing.Somethings happening in last line .
It is just like `whoami` command output .

![silky1](/img/silky1/13.png)

------------------------------
I translated the germany words but didnt understand what interest.

![silky1](/img/silky1/14.png)

------------------------------
I used `strings` command in this step beacuse I could look the file deeply.And I was right there was have
`whoami` command.

![silky1](/img/silky1/15.png)

------------------------------
I couldnt change `whoami` but I could create mine.And I did in `tmp` directory .
And I put `/bin/sh` in whoami for get root shell.I was need to manage path for run my whoami command.
I got when typed `sky` and read `flag.txt`.

![silky1](/img/silky1/16.png)


### Summary:
I really loved this box .You absoultely work in the machine .At least once try to solve on your own.
Have a good hacks .See you next machines :)


[back](./)