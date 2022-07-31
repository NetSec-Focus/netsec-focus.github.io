---
layout: post
date:   2022-07-31
categories: Home Lab
tags: [Home lab, Infosec]
author: tjnull
title:  "TJnull's guide to building a Home Lab "
---
### Table of Contents
- [Introduction](#Introduction)
- [A word of advice](#a-word-of-advice)
- [Why should you build a home lab?](#why-should-you-build-a-home-lab)
- [ Things you need to consider](#things-you-need-to-consider)
- [Hardware](#hardware)
- [Hunting for Hardware](#hunting-for-hardware)
- [Network](#network)
- [Software](#software)
- [Virtualization Software](#virtualization-software)
- [Network Virtual Devices](#network-virtual-devices)
- [Operating Systems](#operating-systems)
- [Windows](#windows)
- [Unix and *Nix](#unix-and-nix)
- [Apple Mac OS](#apple-mac-os) 
- [Daemons/Services](#daemonsservices)
- [Monitoring Services/Systems](#monitoring-servicessystems)
- [Other Resources](#other-resources)
- [Conclusion](#conclusion)

# Introduction:

When I started my infosec journey, I remember attending an awesome talk called &quot;[The AVATAR Project and You](http://www.irongeek.com/i.php?page=videos/bsidescharm2017/bsidescharm-2017-t206-the-avatar-project-and-you-da667)&quot; by da\_667 at BSIDES Charm 2017. [Da\_667](https://twitter.com/da_667?s=20) talked about a guide he was writing about building your own lab environment which would allow you to tailor it to suit your own needs. This talk and his book &quot;[building virtual machine labs a hands-on guide](https://leanpub.com/avatar)&quot; was where my journey would begin so that I could build my home lab.

In this guide I will provide a variety of tips, tools, and resources to help you get some ideas on how to build your home lab.

# A word of advice:

This guide does not contain all the answers you will need to build your home lab. You should use it as a way for getting ideas on how you want to build your home lab. In addition, you should also think about the type of environment you want to set up to practice/build your skillset. After all, this should be a fun and exciting adventure to try out!

Take the time to do your research.

# Why should you build a home lab?

This lab should be the place you want to use it to build your skills whether you are in infosec or IT. Having a home lab will allow you to try out new things and build different topologies. A home lab should be a place where you can be able to build anything you need and tear down when things go wrong.

It is important to have a separate system that does not contain any important data such as personal files, sensitive information, etc. This system/lab will be your playground.

# Things you need to consider:

Before you decide to spin up an entire datacenter in your house (you do not need to do that, trust me) there are some things you want to think about. Here are some questions you should ask yourself first:

- What are you building this lab for?
- What is your budget? How much are you willing to spend?
  - Will you have enough funds to continue to maintain and also scale it?
- Do you have the ability to set up a wired network? If not, will you be able to set up a wireless connection?
- How many virtual machines do you want to run and utilize?
  - What are the system requirements for each virtual machine?
  - Do you plan to have backups for these systems?
- Will this lab be running in your house all the time?
  - Will you have enough power to run your home lab?
  - Do you have a dedicated area that has proper cooling?
- If you are thinking of buying a server, do you have enough space in your home? Rack or tower?
- Have you mapped out what the network is going to look like?

Once you have answered these questions, you can move forward.

# Hardware

Depending on the situation, the machine you are using may not be enough to start your lab. However, you can still do a lot of things.

**Upgrading Hardware:**

It is important to look into the following parts to upgrade in your system:

RAM/memory: The more RAM you have in your system, the better performance to run the projects you need.

Storage: Depending on the project/systems you want to spin up, you are going to need some drives to store all of it. Having multiple drives will make it easier to consolidate your machines and also give you the ability to conduct backups in case something happens. In addition, you can look into getting a network attached storage (NAS) to consolidate your machines in a separate place.

If you want to find a place that reviews the different types of drives or storage solutions [https://www.storagereview.com/](https://www.storagereview.com/consumer)[consumer](https://www.storagereview.com/consumer) is a good place to find recommendations.

CPU: More cores and a better CPU clock speed will allow you to run multiple tasks on your system. Make sure that your CPU is able to run the CPU Virtualization feature if you plan to run virtual machines on your systems.

**Dedicated Machine:**

Having a dedicated machine or converting an old machine is a great way to run your virtual machines in a separate environment. Keep in mind, all three areas which are mentioned in &#39;Upgrading Hardware&#39; (CPU, RAM, hard drive) need to have highest priority when you plan to have a dedicated machine.

If you choose to get into password cracking, using [GPUs instead of CPUs](https://en.bitcoin.it/wiki/Why_a_GPU_mines_faster_than_a_CPU) increases the cracking speed by a factor of hundreds, if not thousands. However, the specifications of this machine would need to be different as power cooling and space becomes more of an issue.

**Additional Hardware:**

There are a variety of devices that you can find to expand your lab, but it depends on what you want to learn and what you would like to try out. Here are a few devices that you should look into having:

- Firewalls/routers/switches
- Raspberry Pi
- Wireless access points/wireless network cards
- IOT devices

# Hunting for Hardware:

Depending on the budget you have and the requirements for hardware that you want, there are a variety options to choose for setting up your lab:

PC Parts/Components:

[https://pcpartpicker.com/list/](https://pcpartpicker.com/list/): This site is a good start if you want to compare the parts/specs that you may be looking for. In addition, the site includes a price comparison option to show you what retailer is selling the part/component for a lower price. They also have users who share their custom builds to give other people an idea of how they want to build out their computers which you could use to figure out your lab.

Small Form Factor Builds:

Raspberry Pi ([https://www.raspberrypi.org/](https://www.raspberrypi.org/)): An affordable single-board computer that has the power to run a variety of different projects that can be added to your lab. It has the ability to run different Linux distributions that you can use for your lab projects.

Intel NUCs ([https://www.intel.com/content/www/us/en/products/boards-kits/nuc.html](https://www.intel.com/content/www/us/en/products/boards-kits/nuc.html)): Do not be fooled by the form factor of these mini PCs as they do pack a punch. This would be a good system if you are looking to save power, reduce noise, and most importantly, save space.

AMD Mini PCs ([https://www.amd.com/en/products/embedded-minipc-solutions](https://www.amd.com/en/products/embedded-minipc-solutions)): AMD also has their own set of small form computers that you can purchase as well. They can be able to run the Ryzen processor chipset as well on some of them.

Minis Forum ([https://store.minisforum.com/](https://store.minisforum.com/)): A place to buy barebone mini PC's depending on use case you need. They have custom options and you can select for your builds and they are very affordable with the selections they have.

Servers:

As technology continues to be improved, older technology needs to be decommissioned or have an end of life (EOL). As these servers get decommissioned, this is also a good chance to repurpose them for your project. Before you decide to buy a server, you need to answer the following questions:

- Do you have enough space to buy a server? What form factor will you be looking to buy (tower or rack)
- Do you have enough power and are you okay with handling the cost of running the server depending on how you have it on?
- Does your budget include also buying parts to upgrade/maintain the server?
- Are you okay if the server is noisy? (There is a reason why we have data centers!)
- Can you provide sufficient airflow or cooling?

If you have answered these questions and are okay with your answers, then you are ready to obtain a server! There are a lot of good resources to help you find a server and the hardware you need for it. Here are some resources you can use to help you find a server for your lab:

Lab Gopher ([https://labgopher.com/](https://labgopher.com/)): The best place to look for buying a server! This site allows you to parse through servers that are listed on ebay that match the criteria you are looking for. You can filter options like RAM, storage, type of server, etc to find the one that you can use for your lab.

Other places to buy servers:

- Save My Server: [https://www.savemyserver.com/](https://www.savemyserver.com/)
- Homelabtech: [https://www.homelabtech.com/](https://www.homelabtech.com/)
- Gear Grabber: [https://geargrabber.io/](https://geargrabber.io/)
- Server Monkey: [https://www.servermonkey.com/](https://www.servermonkey.com/)
- Reddit HomelabSales: [https://www.reddit.com/r/homelabsales/](https://www.reddit.com/r/homelabsales/)
- Local E-Recycling centers
- Craigslist (be careful with sellers on there!)

Other resources for buying a server/hardware:

- Reddit home lab server guide: [https://www.reddit.com/r/homelab/wiki/hardware](https://www.reddit.com/r/homelab/wiki/hardware)

# Network:

Having your own network setup can give you the ability to build your computer networking skills and to learn more about how your network is operating. Building your own network will allow you to isolate/segment your lab from your personal network, transfer files, and isolate certain systems from accessing the internet.

If you want to purchase your own network hardware, you should look for network equipment that will be able to utilize the network speed you are receiving from your ISP. However, you can also virtualize your network if you plan to virtualize your entire lab on the hardware you have. You could even use a Raspberry Pi (depending on the model) to run your network firewall or router.

Finding network hardware:

- [https://www.reddit.com/r/homelabsales](https://www.reddit.com/r/homelabsales)
- Gear Grabber: [https://geargrabber.io/](https://geargrabber.io/)
- [https://www.cablesandkits.com/](https://www.cablesandkits.com/) (Cisco Lab Equipment)

# Software:

Once you have the hardware set up, it is time to decide what software you want to use for your lab. Here are a few types of software that you should think about implementing:

- Virtualization software
- Network virtual devices
- Operating systems
- Daemons/services

# Virtualization Software:

There are different types of virtualization software that you can use to run your virtual machines in your lab. One of the main benefits of using virtualization software is you have the ability to create snapshots which allow you to revert the system to a known state. Keep in mind that each virtualization software offers their own benefits depending on the situation you are planning to utilize them in your lab.

Virtualization software that you can run on your desktop:

- VMware Workstation Player (free, but has limited uses such as running only one virtual machine)
- VMware Workstation (paid, only for Windows and Linux)
- VMware Fusion (paid, available for MAC Only)
- Virtual Box (free, but has limited performance issues)
- Hyper-V (not available for Windows 10 Home)
- QEMU (free, open source)

Virtualization software that you can run on your server:

- VMware ESXI
- Hyper-V (Windows Server)
- Proxmox
- Xen

Note: If you are planning to run your hypervisor on a wireless connection, I would recommend using Hyper-V or Proxmox because VMware-ESXI does not support the drivers for wireless devices. Make sure the wireless card that you are using can support the Infrastructure mode.

Containers:

When you are setting up a virtualized environment, containers can be a good solution that allows you to run certain applications, services, or tools in an isolated environment. In addition, these containers can be easily spun up and taken down when you are doing testing on certain programs. In order for you to run containers in your lab, you will need a host operating system and software that will run the containers. Here is a list of programs that you can use to spin up containers:

- Docker ([https://www.docker.com/](https://www.docker.com/)): free to use and easy to use.
- Vagrant ([https://www.vagrantup.com/](https://www.vagrantup.com/)): If you plan to use VMWare with it you will need to buy it.
- Kubernetes ([https://kubernetes.io/](https://kubernetes.io/))

# Network Virtual Devices:

In case you do not have the ability to purchase your own hardware network equipment, you may be able to run some of these network devices as a virtual machine to manage the network in your lab. Here is a list of certain network devices that you can virtualize for your lab.

Routers:

- GNS3 ([https://gns3.com/software/download-vm](https://gns3.com/software/download-vm)): A network software emulator that allows you to simulate the network you are trying to build. In addition, you can leverage your existing hardware and you can expand your lab with the OS.
- dd-wrt ([https://dd-wrt.com/](https://dd-wrt.com/)): Another open source router platform that can provide router functionality and additional services for virtual networks. (Note: It is commonly used on hardware devices that can support it, but it can be ran as a virtual appliance as well.)

Firewalls:

- pfSense ([https://pfsense.org](https://pfsense.org/)): An open source firewall with a variety of features that a commercial-class firewall would have. In addition, you can install packages to improve the security of your network.
- OPNSense ([https://opnsense.org/](https://opnsense.org/)): Just like pfSense, withs a higher-end graphical web interface.
- ClearOS ([https://www.clearos.com/](https://www.clearos.com/)): Another firewall you can play with. Keep in mind, only the community version is free. If you want access to the home version you will need to pay a subscription for it.

For Raspberry Pi you could also run Pi-Hole ([https://pi-hole.net/](https://pi-hole.net/)). The Pi-Hole is a Linux network-level advertisement and Internet tracker application blocker which acts as a DNS sinkhole. When the Pi-Hole is configured it will act as a DNS Server on your private network.

# Operating Systems:

In infosec it is important to learn both variants of Windows and Linux systems because you need to understand the fundamentals of these operating systems. Most corporations will have a mix of Windows or Linux systems in their environment that need to be protected. If a attack occurs you will need to assess the system and if you do not know how to analyze both of these operating systems, then you are in trouble. Having these operating systems in your home lab is where learning the fundamentals of the Linux or Windows operating system is essential.

# Windows:

Due to the license with which Microsoft Windows is distributed, a valid license needs to be purchased to cover the number of instances installed. However, the Microsoft Evaluation Center gives you the ability to run certain operating systems for a certain amount of time (90-120 days).

Here are the only systems you can get from the Microsoft Evaluation Center: [https://www.microsoft.com/en-us/evalcenter/](https://www.microsoft.com/en-us/evalcenter/)

- Windows 10 Enterprise (32 or 64 bit)
- Windows Server 2019 (32 or 64 bit)

Finding old versions of Windows can be tough but with a little help from Google we can find some shares that have them hosted publicly. Archive.org ([https://archive.org](https://archive.org/)) is another place to find older versions of Windows. Take your time to find the versions you are looking for as some of the files may not be actual the ISOs you need.

Alternatively, a Visual Studio subscription can be purchased, allowing access to a wide range of Windows versions, both currently for sale and discontinued.

If you are a college student or you have a college email address you may have the ability to access OnTheHub. OnTheHub is a discount center for students that can download products from Microsoft, Adobe, VMware and much more. If you want to know if your school is registered you can check here: [https://onthehub.com/search](https://onthehub.com/search)

# Unix and *Nix:

In the beginning there was [UNIX](http://www.unix.org/). This name is trademarked and given to systems which meet [Single UNIX Specification (SUS)](http://www.unix.org/what_is_unix/single_unix_specification.html). _(Using the term UNIX in any other manner _[_isn&#39;t technically allowed_](http://www.unix.org/questions_answers/faq.html#7a)_.)_ From UNIX grew [Berkeley Software Distribution (BSD)](http://www.bsd.org/) sometimes called Berkeley Unix or BSD UNIX and similar UNIX operating systems, which didn&#39;t fully meet the specification. (From BSD UNIX came Darwin, which is the core of Apple OS X &amp; iOS).

- BSD - FreeBSD, OpenBSD, Solaris

These similar UNIX OSs included MINIX, and various of the BSD which did not fully meet their criteria. With the growth of these UNIX clones (referred to as \*NIX) variations formed, such as Linux.

The Linux system is derived from UNIX as it is a continuation of the basis of UNIX design. Linux also refers to the kernel of the GNU/Linux Operating system, as the original code was developed by Linus Torvalds and the GNU Foundation. Each Linux distribution consists of having a Linux kernel, GNU system, GNU utilities, libraries, compiler, additional software, documentation, a window system, a window manager, and a desktop environment.

- Linux Debian-based - Example: Debian, Ubuntu, antiX
- Linux Arch-based: Manjaro, ArcoLinux, Anarchy Linux
- Linux Slackware-based - Example: Slax, SuSE
- Linux RPM-based - Example: Red Hat, CentOS, Fedora

Wikipedia has a detailed list of the family tree of Linux which can be found [here](https://en.wikipedia.org/wiki/List_of_Linux_distributions).
 Websites have been set up to track the updates of their releases; a good project is [Distro Watch](https://distrowatch.com/).

There is a wide range of operating systems which have been mentioned in the above lines, the vast majority of them free and open source. However, there are a few which are commercial.

With this in mind, you are able to freely download and try many of the OS types. Using them will help you build up UNIX and \*NIX skills, giving you a deeper computer knowledge.

# Apple Mac OS:

This OS has been designed to use Apple&#39;s hardware (using it on non-Apple hardware is breaking their EULA). Various different virtualizing solutions (VMware Fusion and Parallel Desktop - neither are free) support OS X as a guest OS, allowing for a VM to be created on which to practice.

# Daemons/Services

After you have selected a few operating systems you want to run in your home lab, you should figure out what kind of programs or services you want to run on them. Keep in mind that certain services will only run on certain operating systems, so you will need to make sure you are using the correct operating system to run that desired service.

Here are a few recommendations of services that you should learn how to set up and play with.File/Storage Services:

- Freenas ([https://www.freenas.org/](https://www.freenas.org/))
- OwnCloud ([https://owncloud.com/](https://owncloud.com/))
- NextCloud ([https://nextcloud.com/](https://nextcloud.com/))
- Rockstor ([http://rockstor.com/](http://rockstor.com/))

Web Services:

- Apache ([https://httpd.apache.org/](https://httpd.apache.org/))
- Apache Tomcat ([http://tomcat.apache.org/](http://tomcat.apache.org/))
- NGINX ([https://www.nginx.com/](https://www.nginx.com/))
- Lighttpd ([https://www.lighttpd.net/](https://www.lighttpd.net/))
- Node.js ([https://nodejs.org/en/](https://nodejs.org/en/))

Can only be installed on Windows:

- Internet Information Services (IIS) ([https://www.iis.net/](https://www.iis.net/))

Other Services:

- DHCP Server
- DNS Server
- Mail Server
- Active Directory (Must be installed through Windows Server)

# Monitoring Services/Systems:

Once you have set up all your services, you are going to need some software or systems that pack a variety of security monitoring tools into it. After all, if you want to be in infosec you need to understand how certain attacks work and how to defend against it.

Monitoring Systems:

- Security Onion ([https://securityonion.net/](https://securityonion.net/)): A Linux-based system that is packed with a variety of open source security monitoring tools that you can test out.
- TPot ([https://github.com/telekom-security/tpotce](https://github.com/telekom-security/tpotce)): A Linux-based system that contains a variety of honeypot services that you can run for monitoring and to understand how attackers are trying to access your network. Would recommend spinning this up as a research project for fun.

Monitoring Services:

Although Security Onion packs a variety of tools into one system, it can be tough to learn all of them at once. It is important to learn how to configure some of these monitoring services manually for the first time and it also might be enough for what you need. Here are some services we recommend looking into depending on what type of monitoring you want to conduct on your home lab:

Network Intrusion Detection/Prevention Services:

- Snort ([https://www.snort.org/](https://www.snort.org/))
- Zeek ([https://zeek.org/](https://zeek.org/))
- Suricata ([https://suricata-ids.org/](https://suricata-ids.org/))
- OSSEC ([https://www.ossec.net/](https://www.ossec.net/))
- Moloch ([https://github.com/aol/moloch](https://github.com/aol/moloch))

Host-Based Endpoint Detection Services:

- Velociraptor ([https://www.velocidex.com/](https://www.velocidex.com/)): An open source tool for collecting host-based state information that can be used to hunt/monitor suspicious activities on a system.
- Bluespawn ([https://github.com/ION28/BLUESPAWN](https://github.com/ION28/BLUESPAWN)): An open source endpoint detection and response tool that can be used to identify, detect, and remove malicious activity on a system.
- Wazuh ([https://github.com/wazuh/wazuh](https://github.com/wazuh/wazuh)): An open source host-based intrusion detection system that can detect threats, intrusion attempts, system anomalies, and much more. It has a server that is used to analyze the data and the agent can be installed on different systems to detect these threats.

Endpoint Log Collectors:

- Sysmon ([https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)): A Windows system service that allows you to log system activity to the Windows event log. The detailed information it collects can be passed through an event collection program or through a SIEM.
- OSQuery ([https://github.com/osquery/osquery](https://github.com/osquery/osquery)): An open source tool that allows you to query for various system information. By using SQL statements to create your own queries, you can use it to detect and analyze for various types of threats that could be on the system.

Security Information and Event Management (SIEM) Tools:

With all of the data you are going to be collecting and reviewing, you are going to need a SIEM to review it all at once. Security Onion and Tpot both use Elasticsearch, Logstash, and Kibana to help visualize the data you see. However, there are some other alternatives that people in the infosec community use as their SIEM. Here are some tools you may be interested in playing with:

- Splunk ([https://splunk.com](https://splunk.com/)): A very popular SIEM tool that enterprise companies use to correlate the data or events in their network. Although Splunk has a free tier, it has a limit to only ingest 500MB of data per day. If you want to expand that limit, you can request a developer license and it will be able to ingest 50GB of data per day. The license will need to be renewed every six months. Here is the link to request a license: [https://www.splunk.com/en\_us/resources/personalized-dev-test-licenses.html](https://www.splunk.com/en_us/resources/personalized-dev-test-licenses.html)
- Graylog ([https://www.graylog.org/](https://www.graylog.org/)): Another open source SIEM that can collect logs from almost any device. It has a nice visualization board that you can configure to display the data you want to visualize.
- HELK ([https://github.com/Cyb3rWard0g/HELK](https://github.com/Cyb3rWard0g/HELK)): An open source threat hunting platform that uses open source tools such Elasticsearch, Logstash, and Kibana with advance hunting analytics capabilities to review the data that can be ingested into it. The platform is simple and easy to deploy. This community project was founded by Cyb3rWard0g and is still being maintained.
- DetectionLab ([https://github.com/clong/DetectionLab](https://github.com/clong/DetectionLab)): A collection of packer and vagrant scripts that builds an entire Active Directory environment with a set of endpoint security tools. The scripts also have the ability to implement a variety of logging practices that you can review for testing purposes. The lab is customizable and it&#39;seasy to make modifications in the config scripts.

# Other Resources:

This section contains a variety of links I saved when I was looking to build my home lab.

**Hardware:**

- Ubiquiti: [https://www.ui.com/products/#default](https://www.ui.com/products/#default)
- Startech ([https://www.startech.com/](https://www.startech.com/)): A company to get network equipment/cables from.

Government auction sites to find servers or network equipment:

Keep in mind what you bid on – if you win the bid you only have a few days to pick it up!

- Public Surplus: [http://www.publicsurplus.com/](http://www.publicsurplus.com/)
- Govdeals: [https://www.govdeals.com/index.cfm](https://www.govdeals.com/index.cfm)

Raspberry Pi:

Building your own Raspberry Pi Cluster:

- [https://magpi.raspberrypi.org/articles/build-a-raspberry-pi-cluster-computer](https://magpi.raspberrypi.org/articles/build-a-raspberry-pi-cluster-computer)
- [https://www.howtoraspberry.com/index.php/2020/08/28/din-r-plate-raspberry-pi-rack-system/](https://www.howtoraspberry.com/index.php/2020/08/28/din-r-plate-raspberry-pi-rack-system/)

Cluster Boards:

- Turingpi: [https://turingpi.com/](https://turingpi.com/)
- Pi Dramble: [http://www.pidramble.com/](http://www.pidramble.com/)

**Networking:**

pfSense Resources:

- Documentation: [https://docs.netgate.com/pfsense/en/latest/\*](https://docs.netgate.com/pfsense/en/latest/*)
- Reddit: [https://www.reddit.com/r/PFSENSE/](https://www.reddit.com/r/PFSENSE/)
- Lawrence Systems PFsense Tutorials: [https://www.youtube.com/watch?v=fsdm5uc\_LsU&amp;list=PLjGQNuuUzvmsuXCoj6g6vm1N-ZeLJso6o](https://www.youtube.com/watch?v=fsdm5uc_LsU&amp;list=PLjGQNuuUzvmsuXCoj6g6vm1N-ZeLJso6o)

DD-WRT:

- Documentation: [https://wiki.dd-wrt.com/wiki/index.php/Installation](https://wiki.dd-wrt.com/wiki/index.php/Installation)

**Software:**

[https://github.com/awesome-selfhosted/awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)

**Tools to Draw Network Diagrams:**

**Online Tools:**

Draw.io: [https://app.diagrams.net/](https://app.diagrams.net/)

Creately: [https://app.creately.com/diagram/](https://app.creately.com/diagram/)

LucidChart: [https://www.lucidchart.com/pages/](https://www.lucidchart.com/pages/)

**Offline Tools:**

Microsoft Visio: [https://www.microsoft.com/en-us/microsoft-365/visio/flowchart-software](https://www.microsoft.com/en-us/microsoft-365/visio/flowchart-software)

Edraw: [https://www.edrawsoft.com/edraw-max/](https://www.edrawsoft.com/edraw-max/)

**Windows:**

Windows Active Directory: [https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)

- Building a Domain Lab: [https://social.technet.microsoft.com/wiki/contents/articles/36438.windows-server-2016-build-a-windows-domain-lab-at-home-for-free.aspx#Download](https://social.technet.microsoft.com/wiki/contents/articles/36438.windows-server-2016-build-a-windows-domain-lab-at-home-for-free.aspx#Download)
- Building an Effective Active Directory Environment: [https://adsecurity.org/?p=2653](https://adsecurity.org/?p=2653)
- Building an Active Directory Lab by SethSec: [https://sethsec.blogspot.com/2017/06/pentest-home-lab-0x2-building-your-ad.html](https://sethsec.blogspot.com/2017/06/pentest-home-lab-0x2-building-your-ad.html)
- Practices for Securing Active Directory: [https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory)

Tool/Scripts to automate the deployment of your Windows Lab:

- WSLab: [https://github.com/microsoft/WSLab](https://github.com/microsoft/WSLab)
- AutomatedLab: [https://github.com/AutomatedLab/AutomatedLab](https://github.com/AutomatedLab/AutomatedLab)
- Invoke-UserSimulator: [https://github.com/ubeeri/Invoke-UserSimulator](https://github.com/ubeeri/Invoke-UserSimulator)
- ADImporter: [https://github.com/curi0usJack/ADImporter\](https://github.com/curi0usJack/ADImporter%5C)

**Linux:**

Tools:

Centrify (Active Directory Integration): [https://www.centrify.com/pam/authentication-service/active-directory-bridging/integration/](https://www.centrify.com/pam/authentication-service/active-directory-bridging/integration/)

This tool allows you to integrate your linux systems into Active Directory and they can be able to easily join the domain. This allow provides the ability to do single sign-on (SSO)

Other Tools/Scripts for Lab Automation:

These tools can be used to automate some of the manual work you will have to do in your homelab. Depending on which tool you use, it will take some time to understand how they work but it can save hours from rebuilding those systems from scratch.

Terraform: [https://www.terraform.io/](https://www.terraform.io/)

Ansible: [https://www.ansible.com/resources/get-started](https://www.ansible.com/resources/get-started)

Puppet: [https://puppet.com/](https://puppet.com/)

# Conclusion:

Having a home lab is a great way to build your skills and experience. It is important to be patient when you decide to build your lab and customize it the way you like it. There are a variety of ways to build a home lab, but make sure the way you build it matches your intended purpose. Most importantly, I hope the resources and tips that I have provided in this guide will give you a good baseline to get started.
