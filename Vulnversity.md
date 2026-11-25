
## Task : Reconnaissance

Gather information about this machine using a network scanning tool called `Nmap`. Check out the [Nmap](https://tryhackme.com/room/furthernmap) room for more on this!

## Connecting to the machine

This room recommends using the AttackBox, which can be launched by clicking the blue button on the top-right.

## Scan the box

nmap -sV 10.48.184.85.

Nmap is a free, open-source and powerful tool used to discover hosts and services on a computer network. In our example, we use Nmap to scan this machine to identify all services running on a particular port. Nmap has many capabilities; a table summarises some of its functionality below.

| Nmap flag     | Description                                                                         |
| ------------- | ----------------------------------------------------------------------------------- |
| -sV           | Attempts to determine the version of the services running                           |
| -p <x> or -p- | Port scan for port <x> or scan all ports                                            |
| -Pn           | Disable host discovery and scan for open ports                                      |
| -A            | Enables OS and version detection, executes in-build scripts for further enumeration |
| -sC           | Scan with the default Nmap scripts                                                  |
| -v            | Verbose mode                                                                        |
| -sU           | UDP port scan                                                                       |
| -sS           | TCP SYN port scan                                                                   |
```bash
Starting Nmap 7.991 ( https://nmap.org ) at 2026-11-25 05:50 -0500
Nmap scan report for 10.48.184.85
Host is up (0.054s latency).
Not shown: 994 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 3.0.5
22/tcp   open  ssh         OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 (Ubuntu Linux; protocol 2.0)
139/tcp  open  netbios-ssn Samba smbd 4
445/tcp  open  netbios-ssn Samba smbd 4
3128/tcp open  http-proxy  Squid http proxy 4.10
3333/tcp open  http        Apache httpd 2.4.41 ((Ubuntu))
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 24.13 seconds

```
---

## Task 2: Locating directories using Gobuster

Using a fast directory discovery tool called `Gobuster`, you will locate a directory to which you can use to upload a shell.

Let's first start by scanning the website to find any hidden directories. To do this, we're going to use Gobuster.

Gobuster is a tool for brute-forcing URIs (directories and files), DNS subdomains, and virtual host names. For this machine, we will focus on using it to brute-force directories.  

Download Gobuster [here](https://github.com/OJ/gobuster), or if you're on Kali Linux run `sudo apt-get install gobuster`.

To get started, you will need a wordlist for Gobuster (which will be used to quickly go through the wordlist to identify if a public directory is available. If you use [Kali Linux](https://tryhackme.com/room/kali), you can find many wordlists under `/usr/share/wordlists`. You can also use the wordlist for directories located at `/usr/share/wordlists/dirbuster/directory-list-1.0.txt` in the AttackBox.  

Now let's run Gobuster with a wordlist using `gobuster dir -u http://10.48.184.85:3333 -w` .

| **Gobuster flag** | **Description**                           |
| ----------------- | ----------------------------------------- |
| -e                | Print the full URLs in your console       |
| -u                | The target URL                            |
| -w                | Path to your wordlist                     |
| -U and -P         | Username and Password for Basic Auth      |
| -p **<x>**        | Proxy to use for requests                 |
| -c <http cookies> | Specify a cookie for simulating your auth |

```bash
gobuster dir -u http://10.48.184.45:3333 -w /usr/share/wordlists/dirbuster/filename.txt
```
