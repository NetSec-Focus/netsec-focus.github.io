---
layout: post
title:  "An Adventure to Try Harder: Tjnull's OSCP Journey"
date:   2019-01-29
categories: OSCP Review
tags: [Offensive Security, OSCP, PWK. Kali]
author: tjnull
---

### Dedication: 
Before I start discussing about my journey, I have a few people that I want to dedicate this blog post. 

First, I want to dedicate this post to my parents and my sisters. Thank you for giving me the time to focus on this and also to prepare for this journey. I know during my journey I did not get to spend much time with you since I was pretty much on the computer every single day just prepping for this. I cannot thank you enough for supporting me and to keep pushing me to follow my dream. I will always be here for you. 

Lastly, I want to thank the InfoSec community. A lot of you reached out to me in so many ways to check up on me and to support me through this journey. I know there were times where I even ranted to you about my journey and you were there to comfort me. I could list every single person that has reached out to me during this journey and this post would just be endless! Thank you for inspiring and also motivating me to learn more. I hope that I can always help someone in this field to learn something and be able to provide support when they are need. 

You know who you are and you should give your self a pat on the back :D!

We live in a crazy time and the InfoSec world is only going to continue to grow at a rapid pace. 

Now here what you all have been waiting for…

### Motivation to take OSCP:

When I was a senior in high school, my instructor for my Security+ course gave me my first hacking cd (Backtrack 5r3) and a Backtrack Cookbook. Throughout the class we would go through a chapter of the book each week and we do hands on labs/exercises to identify security issues or vulnerabilities. I fell in love with it and I knew becoming a hacker or a pentester was going to be my career for me. In high school I had my A+, Net+, and my CCNA but I was always curious about what pentesting certifications were out there which led me to OSCP. After looking at the syllabus I knew I was not ready but I was destined to get this certification on the first try for preparing for it. 

### Previous Experience:

I’ve been in the IT/Cyber Security Field since 2012 (If you count education experience really). I started working as a depot repair technician fixing broken laptops and I hated it. After working there, I was offered an opportunity to be a cyber lab technician for a community college that I graduated from. That place is where I learned so much more about cyber security because my co-worker and I had to spin up the entire program from the ground up…It was awesome! My coordinator would assign me with so many tasks which gave me the ability to learn more and to hone my skills. After two years I took another position to work for govt contractor as a SOC Analyst because the college was unable to hire me full time. I never left the college though because I was offered to be an adjunct professor and teach the Ethical Hacking class they offered. 

One thing that I enjoyed in high school and throughout college was competing in cyber competitions like Cyber Patriot and National Cyber league. These competitions really help me get more engaged in cyber security and I still enjoy competing today. In the past 5 years I have competed in 205 competitions including MACCDC, ALCCDC, Global Cyberlympics, and my favorite one of all SANS NETWARS. I won my first my time competing at SANS Netwars and was given the opportunity to compete in the SANS Tournament of Champions and it was incredible. 
With my work experience, trainings, and personal hobbies I was able to obtain a lot of exposure to the field and improve my skillsets which helped me through my journey. 

•	Operating Systems: Windows, Linux
•	Windows Server Administration
•	Virtualization: Vmware, Citrix, Proxmox
•	Networking (Cisco Routers Switches, DHCP, DNS, Wireshark, and configuring firewalls)
•	Programming: Python, Bash, Ruby 

### Trainings I took before I attempted OSCP:

2012-2015
Comptia A+ training.
CompTia Net+ and CCNA Routing and Switching.
Security+ training.
Microsoft MCSA training.

2016-2017:
CISCO CCNA Cyber Ops training. 

2017-2018:
SANS 504: Hacker Tools, Techniques, Exploits, and Incident Handling
SANS 560: Network Penetration Testing and Ethical Hacking
SANS 542: Web App Penetration Testing and Ethical Hacking
SANS 573: Automating Information Security with Python
SANS 564: Red Team Operations and Threat Emulation
Derbycon 2018 Training: Windows Attack and Defense
Elearnsecurity: Penetration Testing Professional v5 

(I have to thank my employer currently for the SANS Courses because they are very supportive for my education and helping me to continue to learn more about this field.)

### Pre-Requisites for PWK: 

From my perspective I was nervous at first reading the pre-requisites for taking the OSCP course but I will say this don’t let them throw you off really. Even when it states “Familiarity of Bash scripting with basic Python or Perl a plus” will definitely help you but it is not really a requirement. I am not saying you shouldn’t learn python, perl, or ruby. What I am trying to say is as long as you have an understanding of the programing language and you can understand the scripts, then you will be fine. 

As practice for fun I would take exploits online (Metasploit Modules for sure!) and write them in another programming language. For instance, take an exploit that is written in python and write it in ruby. Now there are many ways you can learn more about programming online! You just have to find which material or resources will work for you. Personally, being hands on writing scripts was the best way I got to learn more about python, ruby, and bash. In the SANS 573 class Mark Baggett created all of the lab assignments using pywars to make us write the proper scripts to solve the python challenges he created. 

Here are some resources that I used to help me prepare for the PWK labs and the OSCP Exam. 

### Abatchy’s noob friendly guide to prepare for OSCP:

https://www.abatchy.com/2017/03/how-to-prepare-for-pwkoscp-noob 

A good list of resources that are open source you can use to prepare for the PWK/OSCP. Abatchy is also a good friend of mine and my next post will be a guide like his but updated with more resources. Take the time to go through this material as the structure of his guide is based on the syllabus for the OSCP. 

### Vulnhub: 
The only way to prepare yourself is to get your hands dirty. Vulnhub contains a large collection of vulnerable machines that you can go through to test your skills. I posted a list on twitter a few days ago that contain OSCP-Like boxes that I used to prepare for the class. 	
 
Link to the OSCP-Like Vulnhub Boxes: https://docs.google.com/spreadsheets/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/edit#gid=0 

### Hackthebox: 

Hackthebox is a fantastic online platform allowing members to test their penetration testing skills. There are so many challenges and machines that get released on a weekly basis. The best part is that it is free to the community! You need to pass the first challenge to obtain an invite code in order to play with their challenges. If you get VIP access you can be able to go through a large amount of the retired boxes as well. 

If you cannot afford VIP access do not worry because IppSec has a fantastic YouTube channel where he does full on walkthrough’s showing you how to obtain user and root access on the system. Each week he usually tries to add some new content for each box and it really helped me when he did when I was in the PWK labs. 
 
As of January 29, 2019, here is a list of HacktheBox machines that are OSCP Like: https://docs.google.com/spreadsheets/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/edit#gid=1839402159 
Link to Ippsec youtube playlist: https://www.youtube.com/playlist?list=PLidcsTyj9JXK-fnabFLVEvHinQ14Jy5tf 

If there is anything that you should focus on while preparing to start PWK is to make sure you have enough time invest into the labs. Seriously, I managed my time in the labs and would spend at least 4-5 hours a on weekday in the lab and over 5 hours on the weekend for sure. Make sure you talk to your family, girlfriend, boyfriend, friends, or anyone else to let them know about what you are going to be doing for the next 30, 60, or 90 days! Trust me I had to remind my father a few times about what I was doing as he would yell at me to get off of the computer XD. The total amount of time I dedicated to the lab and the exam was exactly 212 hours. As long as you can dedicate 5 hours per day or 20 hours per week to study you should do fine in the labs. 

### The 90-day journey for me…PWK-Course Time!

So, you registered for the course great! You should have gotten your links for your lab material which contains the following: 
•	380-page pdf manual going through the course material
•	A set of videos to go along with the course material
•	VPN connection pack to access the PWK lab environment

For the first few days I will admit the pdf can be dry with the content provided but if you watch the videos with it can be very enjoyable. The exercises were super fun as well and when you do them document them as well. When I finished the videos and manual, I went through some of the sections that I felt weak on to hone my skills on them. For instance, I went through the buffer overflow section many times just to understand the process of it. If you are just starting out then you will certainly enjoy the exercises as much I did because they are direct walkthroughs of how to complete each exercise step by step. Seriously, I have to give my props to Offsec because they definitely put the time and energy to make it easy and clear to understand the material. If you get stuck or are having issues with your exercises remember to check the Offsec forum because there may be a chance that other students could be having the same issues as well.

As an extra bonus Offsec allows you to get extra points if you document your walkthrough of exploiting 10 systems and all of the exercises. The max score you can get for doing this is 5 points depending on how well you documented your exercises and 10 lab boxes.  
I did the documentation for this to obtain the extra 5 points since it could come in handy but also it is a great way to improve your documentation skills. This is extremely important because you will have to write a report at the end of your OSCP exam as well. The lab report took me a total of 25 hours (Over 5 Days) to document. 

### PWK Lab Network:

Now comes the lab network! This part of the course is the best part in my opinion and I got extremely addicted to it. Over 50 lab machines in 3 separate networks (Public, IT, Dev, and Admin) that you get to hack…let the fun begin! I spent a total of 127 hours in the PWK Lab network and I was able to pwn the entire lab network in 28 days. The labs are super addicting for sure because each box has its own range of difficulty that can be extremely easy to the point where you can get extremely frustrated. I remember owning 17 boxes in 14 hours for one day and then getting stuck on a system in the admin network for 3 days straight. 

Each machine will test your ability to from understanding the lessons taught from the course content but even your research ability as well. This is where you get to build your own methodology when you attack these machines and remember everyone has their own different methodology. In addition, your ability to google-fu will help you tremendously here to identify new techniques, tools, understanding services, and learning more about the operating systems itself. After you own a machine make sure you document everything you did to obtain a shell or even how you priv esc to obtain a full shell. You will realize that there is not just one way to own a machine as each machine in PWK can have multiple attack vectors. 

Things to keep in mind when you are attempting the lab network: 

•	Enumerate Enumerate Enumerate! (Port scan (UDP Scan as well!), version scan, OS scan, web scan, research, etc)
•	Understand the purpose of the system (What does it do?, Who uses it?, Why was it created?)
•	Documenting your steps will help you for sure as you can review them and they may come in handy for another machine you are working on. I used OneNote for Windows 10 for my documentation and it was fantastic to use. My notes were also synced to the cloud so I did not have to worry about losing them and I had the ability to review them from multiple devices if needed.
If you would like to use the OneNote template that I used for the labs and the exam you can find it here (Credit goes all to maik for making this): https://maikthulhu.github.io/2017-11-20-onenote-layout/ 
•	Track your hours spent to see your improvement and it will help you understand how you are using your time wisely in the lab. 

### OSCP Exam Prep: 

Sorry I will not being giving anyway spoilers about the exam but I will share my advice to you on how I prepared for it 😊. After pwning all of the machines in the lab I had two weeks to prepare for my exam! Keep in mind that the exam slots do fill up fast so make sure that you schedule your OSCP exam at least one month in advance. If you are unable to commit in that time do not worry at all because you can always re-schedule it for a later day to help better prepare yourself for it. 

One blog that I have to give credit to for helping me prep for the exam mentally was this one below: 
https://www.vortex.id.au/2017/05/oscp-exam-preparation-exam-day-report-day/ 
Definitely take some time to read it because it does help you prepare mentally before the exam. With vortex advice I thought I share with you all what I did to prepare in my final days before the exam. 

### 5 days from the OSCP exam: 

During my preparation I started gathering my cheatsheets, tools, exploits, and prepping my notes ahead of time making it easy instead of me scrambling to find them during my exam. Once you have everything prepped make sure you make a backup of your kali system and also create snapshots in case you need to revert. 

Another tip I will also mention is take some time to draft your exam report. Even if you pass or fail it is good to have it already set up since you are not wasting more time creating it during the 24 hours given from Offsec to submit the report to them. 
For the proctor part of your exam you can use your laptop for your webcam! Make sure that it works and that it is also not in the way of your desk area when you are taking the exam. Plan your attack strategy and think of how you are going to attack each target in your exam. 

### 3 days from the OSCP Exam: 

Grab your snacks, prep your meals, and make sure you have your caffenine ready for this 23 hours and 45 minute exam you are about to take. Also get a music playlist set up. I was jamming to few of my rock and roll playlists and I also started with and of course playing some dual core in the beginning of my exam! 
All the things by Dual Core: https://open.spotify.com/track/3ZzxtumoIENCi16HAKuiLU?si=XNGD5WAkTC602wjzslIiXg 

### 1 day from your OSCP Exam: 

If you have done everything that I have recommended then the the only thing you should be doing is rest. Hands off the keyboard! Go spend time with your family or friends to let your mind relax. Stressing over your exam is not going to help you when you have to take it tomorrow and make sure to have positive thoughts. Reflect on what you have achieved and what you have done. Make sure you go to bed early and also find a quiet place to sleep so you are not distracted by someone. Also do not drink to much…1 beer is okay but do not go overboard 😉

### OSCP Exam:

IT’s Time! Today is the day you take your exam. Now do not rush everything you have make sure you get up an hour or two early from your exam. During that time go make breakfast and get your stuff setup and running. Check your vm’s and have your cheat sheets ready to go on your system. 

Before the last hour till you start your OSCP exam, login into the webcam program and screen connect program to make sure that those applications are working. I logged in 30mins before my OSCP exam and they were not able to see my webcam on their end for the exam. I had to work with offsec to troubleshoot this issue until we figured out another resolution. By the time we figured out a resolution offsec sent me my exam VPN connection pack and I losted 30mins of my exam time because of it. 

My attack strategy that I planned actually failed because at certain times since I was unable to get anything working. I was worried that I was going to fail but during those times I was reminded by someone and I also had a lot of support from the infosec community rooting for me to pass. I was not ready to quit that easy. There was one person that mentioned this tip to me about the exam that I will always remember: 
“you're going to run out of ideas before you run out of time. take breaks. walk away for a bit. dont be afraid to go to sleep for a few hours, especially if youre stuck” -0xdf

With this I started taking 2-3min break and sometimes 15mins breaks as well to clear my head. When you leave your room you will also need to notify the proctor when you are leaving and when you return so that they can document it. Also stay hydrated during the exam. I had two gallons next to my desk to fill up with water to keep my brain working throughout the entire time of the exam. After 24 hours I was able to get enough points to pass the exam and offsec did not give me my extra 30mins that I lossed during the exam. I closed my webcam session and also the screenconnect program and got a cup of coffee to celebrate. 

With me having enough points the clock started for writing the exam report. I was going to try to take a nap but I could not fall asleep due to my adernaline and full of excitement that I felt for passing this exam (Coffee does it’s wonders)! So I stayed up for another 14 hours to write the exam report. I am glad that I built my Exam report ahead of time because I was able to fill the needed information in quicker then creating a whole new tempelate. Once I finalized my exam I double checked everything that I did, made sure my screenshots were correct, and validated the system information before I sent it to offsec. I also included my lab report to send to them as well. 

Once I sent it to them I had to wait for offsec to send me a “Acknowledgement of Receipt” to let me know that they got my reports. 12 hours had passed and they sent me “Acknowledgement of Receipt” letting me know that they got my reports.I submitted my report on Friday and I received my exam results on Monday at 9am giving me the wonderful news that I worked hard to receive: 


4 years of hard work paid off on my first exam attempt!

### Final Thoughts: 

I have to say my OSCP journey was one the most fun, technically challenging, and absolute amazing experience of my life. I am very glad that I started it last year and was able to start the new year with being OSCP certified. I just wish I did not put it off as much as I did even though my employer gave me a lot of SANS courses and other trainings to prep for it. As you can already tell I put an extreme amount of effort into my study time then I did in the entire course alone. I now understand why Offsec uses the motto “Try Harder” because in honesty that is what you have to do to get through the labs and the exam.

No matter what happens never give up! If you are stuck or are having issues take a step back think about what you have tried. If my journey gave you some advice and motivation to take the OSCP then I wish you the best on the journey ahead. It is not an easy exam but work hard and you will certainly be rewarded. If you do not think you are ready for the course do not worry or even stress about it. Remember to look over the resources I posted earlier to help prepare for it.

### Future Plans?

1 offsec cert down…two more to go! My plan is to go for OSCE and OSEE. I also want to start getting more into red teaming and learn more about Cobalt Strike. During that time, I am working on building an ethical hacking class and also an updated OSCP Noob Friendly guide that I hope to release soon (Thanks Abatchy for your permission 😉). 

### Conclusion: 

I certainly hope you enjoyed reading my exeperience with OSCP. I know someone is going too see some typos in here but in the end we are all not perfect so :D. Not to mention I covered a lot of things but that is what I do in general really. DETAILS DETAILS DETAILS!

If you wish to find me, I am usually attending security conference for fun to learn more about InfoSec from the community or competing in CTF’s for fun as well! You can find me on NetSecfocus and on Twitter as well. Thank you again for reading this and I certainly hope that you enjoyed it 😊. 


-Tjnull
Twitter: ([@TJ_Null](https://twitter.com/tj_null))
