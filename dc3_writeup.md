---
layout: post
---

# [VulnHub]DC:3 WriteUp

I pwned [dc:3](https://www.vulnhub.com/entry/dc-3,312/) machine today.
And We will see my writeup about that.

### Tools

* netdiscover
* nmap
* joomscan
* searchsploit
* sqlmap
* john
* nc

### Steps 

I started find target ip with `netdiscover -r 192.168.1.0/24` . 
My network adapter was in bridged mode .

![dc3](/img/dc3/1.png)

And I did nmap searching for see which ports and service work .
It was just one port open and work in joomla.

![dc3](/img/dc3/2.png)

I saw the tool first time . It is usefull tool I liked.
And I used the tool `joomscan --url http://192.168.1.104` .
I detected joomla version and started search the verison for might have vulns.

![dc3](/img/dc3/3.png)

I did searchsploit searching and saw an exploit .

![dc3](/img/dc3/4.png)

I saw sqlmap query when read the txt file . I started work with sqlmap changed address .

![dc3](/img/dc3/5.png)

I found 5 databases . I selected `joomladb` database .

![dc3](/img/dc3/6.png)

And started to find tables after add `-D joomladb --tables` line in sqlmap query .
I was hope to see an user table and it happened .

![dc3](/img/dc3/7.png)

I found admin creds after that I started to crack the hash with `john` .

![dc3](/img/dc3/8.png)

I cracked the hash before take screenshot so it didnt show this time . Result is `snoopy` . 

![dc3](/img/dc3/9.png)

I went to admin panel and logon with creds .


![dc3](/img/dc3/10.png)

I went to `templates/beez3/error.php` directory for upload reverse shell.
I changed `error.php` contents .

![dc3](/img/dc3/11.png)

And I did a request use with the page for reverse connection.

![dc3](/img/dc3/12.png)

My listener already was working .I got connection .

![dc3](/img/dc3/13.png)

I started to enumerate `os` . I saw ubuntu version.

![dc3](/img/dc3/14.png)

I searched the version and found many things but I was need to select one .And 
I select `39722.txt` . And I read the file for exploit.

![dc3](/img/dc3/15.png)

I was need to download the zip file.I extracted the files for download target machine .

![dc3](/img/dc3/16.png)

I pulled the files with `wget` .I started with `compile.sh` file .And I saw new files after that .

![dc3](/img/dc3/17.png)

And in the last step `doubleput` file worked for get root and read final flag.

![dc3](/img/dc3/18.png)



### Summary:

I liked the box.I absoultly recommended to you solve on your own.
Have a good hacks .See you next machines :)

[back](./)