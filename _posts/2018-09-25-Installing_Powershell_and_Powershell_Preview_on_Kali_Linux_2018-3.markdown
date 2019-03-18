---
layout: post
title:  "Installing Powershell and Powershell Preview on Kali Linux 2018.3"
date:   2018-09-25
categories: Infosec Tools
tags: [powershell, posh, kali]
author: tjnull
---

A few months ago, Kali Linux released an article about how you can now install PowerShell on Kali Linux. Here is the link and instructions:

[https://www.kali.org/tutorials/installing-PowerShell-on-kali-linux](/https://www.kali.org/tutorials/installing-PowerShell-on-kali-linux/)

If you follow the instructions you will notice that we need another package to install PowerShell: 

```bash
root@kali:~# apt -y install PowerShell
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
PowerShell: Depends: libcurl3 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Currently Kali Linux 2018.3 already contains libcurl4 and if we try to install libcurl3 you should see something like this: 

```bash
root@kali:~# apt-get install libcurl3
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
curl libcurl4 Metasploit-framework
The following NEW packages will be installed:
libcurl3
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 260 kB of archives.
After this operation, 250 MB disk space will be freed.
```

There are also other packages that use libcurl4 but it surprised me that Metasploit would be removed if I reverted back to libcurl3.

With this issue I wanted to investigate further and see if I can find a resolution. PowerShell offers two package versions for Debian (Jessie and Stretch)

You can find them here:

```
Jessie: https://packages.microsoft.com/repos/microsoft-debian-jessie-prod/pool/main/p/

Stretch: https://packages.microsoft.com/repos/microsoft-debian-stretch-prod/pool/main/p/
```

I tested the installation for all of the PowerShell packages in stretch and jessie and all of them required libcurl3

```
Stretch and Jessie packages that requires libcurl3: 
PowerShell_6.0.0-1.deb                             10-Jan-2018 17:47            51924632
PowerShell_6.0.1-1.deb                             25-Jan-2018 18:31            52137558
PowerShell_6.0.2-1.deb                             15-Mar-2018 17:32            52192714
PowerShell_6.0.3-1.deb                             19-Jul-2018 21:29            52503432
PowerShell_6.0.4-1.deb                             10-Aug-2018 00:11            52557832
```

This made no sense to me that both Stretch and Jessie need libcurl3 to run. [I submitted an issue to PowerShell on GitHub](https://github.com/PowerShell/PowerShell/issues/7719) to get a better understanding
on why PowerShell needed libcurl3. Turns out I got the answer I was looking for: 

"PowerShell Core and CoreFX no longer has a dependency on libcurl [See GitHub issue #6964](https://github.com/PowerShell/PowerShell/issues/6964)."

So why does the PowerShell package for Debian need libcurl3 if it is no longer a dependency? Since PowerShell for Kali is only supported by the community, 
I wanted to raise the issue to Kali Linux team about this. When I spoke with them they were aware that PowerShell for Kali was not working and were looking into it as well. A few days later I finally figured out that the PowerShell Debian repositories have not been updated properly for Kali Linux. The PowerShell team told me that they would fix this in the new release which was going to be released very soon. 

The reason why they were going to push this in the new release is because "PSCore6.0.x depends on .NET Core 2.0.x which DOES depend on libcurl. PSCore6.1 depends on .NET Core 2.1.x which does NOT depend on libcurl."

As the PowerShell team was working on updating the new release I found a workaround that you could use PowerShell preview on Kali Linux 2018.3. These packages do not require the libcurl3 dependency and you can install the following packages below: 

```
Stretch: 
PowerShell-preview_6.1.0~preview.3-1.deb           13-Jun-2018 00:12            59438156
PowerShell-preview_6.1.0~preview.4-1.deb           19-Jul-2018 21:13            57913672
PowerShell-preview_6.1.0~rc.1-1.deb                22-Aug-2018 01:09            56712364

Jessie: 
PowerShell-preview_6.1.0~preview.3-1.deb           13-Jun-2018 00:12            59438156
PowerShell-preview_6.1.0~preview.4-1.deb           19-Jul-2018 21:13            57913672
PowerShell-preview_6.1.0~rc.1-1.deb                22-Aug-2018 01:09            56712364  

```

### Installing PowerShell: 

First, we need to download and add the public repository GPG key so APT will trust the packages and alert you to any issues with package signatures:

```bash
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
```

Second, Once the GPG key has been added, we need to add the Microsoft package repository to its own package list file under /etc/apt/sources.list.d/ 
This will allow us to also pull any updated packages that the PowerShell team will release in the future:

```bash
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/PowerShell.list
apt update
```
Third we will need to install the following dependency packages below to continue the installation. You can download the package here: 

```bash
libicu57: https://packages.debian.org/stretch/amd64/libicu57/download
icu-devtools: https://packages.debian.org/stretch/amd64/icu-devtools/download
liblttng-ust0: https://packages.debian.org/stretch/amd64/liblttng-ust0/download
liburcu4: https://packages.debian.org/stretch/amd64/liburcu4/download
liblttng-ust-ctl2: https://packages.debian.org/stretch/amd64/liblttng-ust-ctl2/download
```

Install the packages in the following order here:

```bash
root@kali:~# dpkg -i liburcu4_0.9.3-1_amd64.deb 
Selecting previously unselected package liburcu4:amd64.
(Reading database ... 341730 files and directories currently installed.)
Preparing to unpack liburcu4_0.9.3-1_amd64.deb ...
Unpacking liburcu4:amd64 (0.9.3-1) ...
Setting up liburcu4:amd64 (0.9.3-1) ...
Processing triggers for libc-bin (2.27-5) ...

root@kali:~# dpkg -i liblttng-ust-ctl2_2.9.0-2+deb9u1_amd64.deb 
(Reading database ... 341748 files and directories currently installed.)
Preparing to unpack liblttng-ust-ctl2_2.9.0-2+deb9u1_amd64.deb ...
Unpacking liblttng-ust-ctl2:amd64 (2.9.0-2+deb9u1) over (2.9.0-2+deb9u1) ...
Setting up liblttng-ust-ctl2:amd64 (2.9.0-2+deb9u1) ...
Processing triggers for libc-bin (2.27-5) ...

root@kali:~# dpkg -i liblttng-ust0_2.9.0-2+deb9u1_amd64.deb 
(Reading database ... 341748 files and directories currently installed.)
Preparing to unpack liblttng-ust0_2.9.0-2+deb9u1_amd64.deb ...
Unpacking liblttng-ust0:amd64 (2.9.0-2+deb9u1) over (2.9.0-2+deb9u1) ...
Setting up liblttng-ust0:amd64 (2.9.0-2+deb9u1) ...
Processing triggers for libc-bin (2.27-5) ...

root@kali:~# dpkg -i libicu57_57.1-6+deb9u2_amd64.deb 
(Reading database ... 429929 files and directories currently installed.)
Preparing to unpack libicu57_57.1-6+deb9u2_amd64.deb ...
Unpacking libicu57:amd64 (57.1-6+deb9u2) over (57.1-6+deb9u2) ...
Setting up libicu57:amd64 (57.1-6+deb9u2) ...
Processing triggers for libc-bin (2.28-8) ...

root@kali:~# dpkg -i icu-devtools_57.1-6+deb9u2_amd64.deb 
Selecting previously unselected package icu-devtools.
(Reading database ... 341748 files and directories currently installed.)
Preparing to unpack icu-devtools_57.1-6+deb9u2_amd64.deb ...
Unpacking icu-devtools (57.1-6+deb9u2) ...
Setting up icu-devtools (57.1-6+deb9u2) ...
Processing triggers for man-db (2.8.3-2) ...

```

Once you have installed the following packages you can now install PowerShell preview on your system: 

```bash
root@kali:~# apt-get install PowerShell-preview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  PowerShell-preview
0 upgraded, 1 newly installed, 0 to remove and 843 not upgraded.
Need to get 56.7 MB of archives.
After this operation, 153 MB of additional disk space will be used.
Get:1 https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch/main amd64 PowerShell-preview amd64 6.1.0~rc.1-1.debian.9 [56.7 MB]
Fetched 56.7 MB in 4s (15.7 MB/s)             
Selecting previously unselected package PowerShell-preview.
(Reading database ... 341785 files and directories currently installed.)
Preparing to unpack .../PowerShell-preview_6.1.0~rc.1-1.debian.9_amd64.deb ...
Unpacking PowerShell-preview (6.1.0~rc.1-1.debian.9) ...
Setting up PowerShell-preview (6.1.0~rc.1-1.debian.9) ...
Processing triggers for man-db (2.8.3-2) ...
```

To run PowerShell preview in your console, type the following command pwsh-preview. You should see a new prompt that starts with "PS". If you see this prompt then you have successfully installed PowerShell! 

```bash
root@kali:~# pwsh-preview
PowerShell 6.1.0-rc.1
Copyright (c) Microsoft Corporation. All rights reserved.

https://aka.ms/pscore6-docs
Type 'help' to get help.

PS /root> 
```


### Update September 16 2018: 

 
The PowerShell team on GitHub was able to release a new version of PowerShell. Below are the versions that currently work in Kali Linux: 

```
Stretch: PowerShell_6.1.0-1.deb 13-Sep-2018 00:34 58286110
Jessie:  PowerShell_6.1.0-1.deb 13-Sep-2018 00:33 58287274  
```

If you have installed PowerShell preview on your Kali system, all you need to do is run apt-get install PowerShell: 
Note: If you did not install PowerShell preview, please refer to the installation guidelines. You will need to have the following depended packages that were used in PowerShell-preview to run PowerShell on kali:

```bash
root@kali:~# apt-get install PowerShell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  PowerShell
0 upgraded, 1 newly installed, 0 to remove and 843 not upgraded.
Need to get 0 B/58.3 MB of archives.
After this operation, 158 MB of additional disk space will be used.
Selecting previously unselected package PowerShell.
(Reading database ... 342275 files and directories currently installed.)
Preparing to unpack .../PowerShell_6.1.0-1.debian.9_amd64.deb ...
Unpacking PowerShell (6.1.0-1.debian.9) ...
Setting up PowerShell (6.1.0-1.debian.9) ...
Processing triggers for man-db (2.8.3-2) ...
```

To run PowerShell, make sure you type the following command: pwsh
You should see a new prompt appear with "PS"

```bash
root@kali:~# pwsh
PowerShell 6.1.0
Copyright (c) Microsoft Corporation. All rights reserved.

https://aka.ms/pscore6-docs
Type 'help' to get help.

PS /root> exit
root@kali:~# pwsh-preview
PowerShell 6.1.0-rc.1
Copyright (c) Microsoft Corporation. All rights reserved.

https://aka.ms/pscore6-docs
Type 'help' to get help.

PS /root>    
```

What I also found interesting is you can have PowerShell and PowerShell-preview running on the system :D


### Conclusion:

I really want to thank the PowerShell team and the guys at Kali for getting this issue fixed in a quick manner. I hope you have enjoyed this post and will enjoy testing PowerShell on Kali Linux :)

If you have any questions or issues trying to install PowerShell on Kali please let me know. You can find me on twitter ([@TJ_Null](https://twitter.com/tj_null)) and in the NetSec Focus community platform at [https://mm.netsecfocus.com/join/](https://mm.netsecfocus.com/join/)


### References

GitHub Issue: [https://github.com/PowerShell/PowerShell/issues/7719](https://github.com/PowerShell/PowerShell/issues/7719)

Kali: [https://bugs.kali.org/view.php?id=4958](https://bugs.kali.org/view.php?id=4958)
