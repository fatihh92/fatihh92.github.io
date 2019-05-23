---
layout: post
---


# [VulnHub] Unknowndevice64:2 WriteUp For Android Pentesters
It was different experience for me.Because I did android pentesting in first time. 
It was just like introduce to android hack.This machine level is Beginner.
You should read [machine main page](https://www.vulnhub.com/entry/unknowndevice64-2,297/) before start 
because You need to set `nomodeset` to GRUB.You can do easly with video in description. 

### Tools

* netdiscover
* nmap
* adb

### Steps

If you see the screen you did settings correctly. 

![android](/img/unknowndevices2/1.png)

I started to detect target ip again with `netdiscover -r 192.168.88.1/24`. I used NAT network option by the way.

![android](/img/unknowndevices2/2.png)

I did nmap scanning for port and service couples.

![android](/img/unknowndevices2/3.png)

And finally I used adb tool.I read many thing about that but I haven't been used ever.
You can read some basic things in this [link](https://developer.android.com/studio/command-line/adb) .
I connected  to device with adb and listed devices for see we have connections which devices.
And I got shell with `adb shell`

![android](/img/unknowndevices2/4.png)

I started some basic enumeration.Honestly I didn't know How I  proceed.
But I saw system directory and decided go there.

![android](/img/unknowndevices2/5.png)

I found `flag.txt`.I tried to read the file.I couldn't be successfull.
I tried basic root command `su` and it worked I got root.

![android](/img/unknowndevices2/6.png)

I went to same directory and read .

![android](/img/unknowndevices2/7.png)

### Summary:

There is have one more way as authors' said. You can feel free share with me If you will found the way .
It was really easy but a step for mobil pentesting to me .I liked the machine.
Have a good hacks .See you next machines :)

[back](./)