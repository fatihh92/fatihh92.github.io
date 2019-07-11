---
layout: post
---

# FUZZYİNG WİTH HTB CHALLENGE

Hi everyone again.I started to write finally.Today I will show how to use wfuzz tool and
what is it work fuzzying?So I solved a hackthebox web challenge about fuzzying .I censored 
some parts but you can understand easly.


### Tools

* [wfuzz](https://tools.kali.org/web-applications/wfuzz) 
* [dirbuster]()

### Steps 

First of all I was need to find right directory so I started work with dirbuster tool.
I used `directory-list-w.3-medium.txt` as wordlist.And I set up file extension as `.php`.
And started to find php pages.


![htb](/img/fuzzying/1.png)
-------------------------------------------------------------
I found a directory and there was has a php page .So I went to the page.

![htb](/img/fuzzying/2.png)
-------------------------------------------------------------
I faced this error when I went to the page.And Fuzzying is started in this point

![htb](/img/fuzzying/3.png)
-------------------------------------------------------------
I used wfuzz tool.it is very useful tool I absolutely recommended thi tool.
If you dont know a parameter or a page name you can use to find the unknown things.
You just put the word `FUZZ` to unknown where.In the our case not known a parameter so
I put it end of the question mark.Because we know if it is have a parameter it is come after
question mark.And I used `--hw` parameter because I knew our parameter is existing over 4 word.
In the end it found a parameter you can see in payload part.

![htb](/img/fuzzying/4.png)
-------------------------------------------------------------
When I used the paramter in the url we I got one more error.This time I need to find right id.
So I started fuzzying again.

![htb](/img/fuzzying/5.png)
-------------------------------------------------------------
This time I put it right of equal.Because We dont know a value .And I used `big.txt` wordlist .
And this word is existing over 5 word.I know that because I tried before.And I found a value .

![htb](/img/fuzzying/6.png)
-------------------------------------------------------------
End of the day I used it in url and went to there.And I got flag.

![htb](/img/fuzzying/7.png)

### Summary:
I absolutely recommended to look the challenge super easy and super fun.I had fun when I was solving
You can try to solve the challenge at least you can learn wfuzz tool how to use basicly.
Have a good hacks .See you again :)


[back](./)