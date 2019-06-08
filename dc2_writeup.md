---
layout: post
---

# [VulnHub]DC:2 WriteUp

Hi you all again.I pwned dc:2 machine today.But Before start the machine
you neet to read [machine page](https://www.vulnhub.com/entry/dc-2,311/) because it is hack and
you have to see every details.

### Tools

* netdiscover 
* nmap
* cewl
* wpscan
* vi
* git


### Steps 

You can guess first two steps.Target ip detection and Enumerating running services.

![dc2](/img/dc2/1.png)

![dc2](/img/dc2/2.png)

-------------------------------------------------------------
I directly opened `wpscan` tool when I saw wordpress header.So I did same thing in here.
I started enumerate users with `wpscan --url http://dc-2 --enumerate u` .And I found 3 user.

![dc2](/img/dc2/3.png)
-------------------------------------------------------------
I created username list for brute force to login page .

![dc2](/img/dc2/4.png)
-------------------------------------------------------------
But I didnt have right password list.When I went to site I saw flag1 page and I read all of them.
I noticed `cewl` word in the page.I didnt know what is that.

![dc2](/img/dc2/5.png)
-------------------------------------------------------------
So I started googling and I saw this is a tool.Even wordlist generator.
You can more info in the [link](https://tools.kali.org/password-attacks/cewl) .
I think it gonna be work to me

![dc2](/img/dc2/6.png)
-------------------------------------------------------------
I started work with the tool and created a password list .

![dc2](/img/dc2/7.png)
-------------------------------------------------------------
And I started brute force with `wpscan --url http://dc-2 -U users.txt -P pass.txt` .
I found passwords for jerry and tom.

![dc2](/img/dc2/8.png)
-------------------------------------------------------------
I saw flag2 when I logon site .And I realized I need to continue with ssh .
Because I didnt find anything else and there is no one entrypoint except ssh .

![dc2](/img/dc2/9.png)
------------------------------------------------------------
But There is have shell restriction .So I started to search how can I pass the restriction

![dc2](/img/dc2/10.png)
-----------------------------------------------------------
I looked which commands can work here and I saw my darling `vi`.Because
You can almost pass every restriction  with it .

![dc2](/img/dc2/11.png)
----------------------------------------------------------
First I typed `set shell=/bin/bash` and `:shell` in vi .
So I passed restriction but I was need to export new path and shell envoriments.
For work truely

![dc2](/img/dc2/12.png)
---------------------------------------------------------
I exporteed them and read flag3.As I understand I need to be jerry and I did what I understood
And I started enumeration for root .I saw git command can work with root privileges.

![dc2](/img/dc2/13.png)
--------------------------------------------------------
So I started to search `linux git priv esc` in google.And I found [that](http://blog.securelayer7.net/abusing-sudo-advance-linux-privilege-escalation/) .
First I typed `sudo /usr/bin/git help status` after than typed :
`!/bin/bash` and I got root and final .

![dc2](/img/dc2/14.png)


### Summary:

I really liked the machine.I saw a tool first time again.it was be good practice for me So I recommended to solved on your own.
Have a good hacks .See you next machines :)

[back](./)