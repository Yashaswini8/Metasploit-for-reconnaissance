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
ifconifg:
<img width="1920" height="1057" alt="ifcon1" src="https://github.com/user-attachments/assets/1da0ede7-74a5-4616-bc0a-5ce97addcd79" />
msfconsole:
<img width="1920" height="1057" alt="msf2" src="https://github.com/user-attachments/assets/ce4cedd2-369b-4143-b0f7-9cbba46643eb" />
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
<img width="1920" height="1057" alt="help" src="https://github.com/user-attachments/assets/4b649600-47a4-4fb8-8a10-eba6114800b0" />
port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000
OUTPUT:
<img width="1920" height="1057" alt="nmap0" src="https://github.com/user-attachments/assets/a898c989-6c4b-421d-9f93-d7e0520144a6" />

USE the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

OUTPUT:
<img width="1271" height="548" alt="Screenshot 2025-09-25 085916" src="https://github.com/user-attachments/assets/7f43134e-add9-4715-9333-fbf4d44e15e0" />

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

OUTPUT:
<img width="1266" height="733" alt="Screenshot 2025-09-25 085851" src="https://github.com/user-attachments/assets/9ae12ef5-2d4c-45dd-8610-1727fddb3497" />

<img width="1920" height="1057" alt="searchtype" src="https://github.com/user-attachments/assets/1cb3ad29-6976-46b8-9728-1d1154a285a5" />
MYSQL ENUMERATION:
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitab
OUTPUT:
<img width="1034" height="438" alt="Screenshot 2025-09-25 092124" src="https://github.com/user-attachments/assets/5fe480fa-071e-4dca-aa9b-2e171ab0ceed" />
Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql
<img width="1920" height="1057" alt="searchtype" src="https://github.com/user-attachments/assets/a1614976-4b0a-443b-8661-cd2fee169265" />
use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version


<img width="1920" height="1055" alt="use11" src="https://github.com/user-attachments/assets/2b036642-d040-4553-84fb-9ed74d9a30c1" />
Use the set rhosts command to set the parameter and run the module, as follows:

<img width="1920" height="1055" alt="after use11" src="https://github.com/user-attachments/assets/41d2bad5-e80f-42c6-9692-2eb742fb910a" />
After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.


<img width="1920" height="1055" alt="setpass" src="https://github.com/user-attachments/assets/8434cbdf-aada-4d66-b127-f9c0df7e9014" />
set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true
<img width="1920" height="1055" alt="lastone" src="https://github.com/user-attachments/assets/9d3eeef3-e38a-474b-a80f-862aa84d2aa7" />













## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
