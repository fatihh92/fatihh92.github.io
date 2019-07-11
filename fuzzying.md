---
layout: post
---

# FUZZYİNG WİTH HTB CHALLENGE



### Tools

* [wfuzz](https://tools.kali.org/web-applications/wfuzz) 



### Steps 

You can guess first two steps.Target ip detection and Enumerating running services.

![htb](/img/fuzzying/1.png)


-------------------------------------------------------------
I directly opened `wpscan` tool when I saw wordpress header.So I did same thing in here.
I started enumerate users with `wpscan --url http://dc-2 --enumerate u` .And I found 3 user.

![htb](/img/fuzzying/2.png)
-------------------------------------------------------------

![htb](/img/fuzzying/3.png)
-------------------------------------------------------------

![htb](/img/fuzzying/4.png)
-------------------------------------------------------------

![htb](/img/fuzzying/5.png)
-------------------------------------------------------------

![htb](/img/fuzzying/6.png)
-------------------------------------------------------------

![htb](/img/fuzzying/7.png)


### Summary:



[back](./)