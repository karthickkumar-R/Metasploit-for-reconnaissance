# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
![1](https://github.com/user-attachments/assets/28f4d085-4d73-41c1-ace8-5b5f4d6d7507)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init

Invoke msfconsole:
## OUTPUT:
![2](https://github.com/user-attachments/assets/0978c85b-f238-4b56-bd2c-a583249dbf9e)





Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![3](https://github.com/user-attachments/assets/d1c0ae86-be58-44e1-9f52-89d212a7ac39)

Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![4](https://github.com/user-attachments/assets/2b0ffbe0-1345-4c67-a10a-393e7564346b)


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
![5](https://github.com/user-attachments/assets/8e2cdf76-cbfc-400f-bdd0-8c6bd2a0fe8c)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
![6](https://github.com/user-attachments/assets/fb955806-338b-49e8-a073-73836963b8d9)



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT


![7](https://github.com/user-attachments/assets/30e37b72-f237-45ab-80fb-d9a0c9f4cdc4)


The info command provides information regarding a module or platform,

![8](https://github.com/user-attachments/assets/34c5beda-b5a2-46b8-83d7-bafff7ee2d57)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![9](https://github.com/user-attachments/assets/d104f908-9e71-4035-aa7a-fda3a62218cc)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql


![10](https://github.com/user-attachments/assets/87ac4476-ea47-40b2-91c1-dc5eac104b21)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
![11](https://github.com/user-attachments/assets/4baab9fe-c6b0-4ab3-a402-c02bce5d5602)


Use the set rhosts command to set the parameter and run the module, as follows:
![12](https://github.com/user-attachments/assets/71c70e10-ea9b-4003-be89-ae5179c55958)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![13](https://github.com/user-attachments/assets/20d760aa-5aee-424b-b582-29fe81c8c501)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
> set PASS_FILE /usr/share/wordlists/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
> set RHOSTS <metasploitable-ip-address>

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

>set BLANK_PASSWORDS true
![14](https://github.com/user-attachments/assets/ba5da8d3-afcb-4485-b8b6-6ab2c8e44956)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
