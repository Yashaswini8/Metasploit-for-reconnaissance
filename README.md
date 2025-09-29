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

## Architecture Diagram:
+----------------------+              +--------------------+             +-------------------------+
|    Attacker Machine  |<----------->|  Target (MySQL DB) |<----------->|       Network           |
|  (Kali Linux + MSF)  |              |    Port 3306       |             | (LAN or External)      |
+----------------------+              +--------------------+             +-------------------------+
         |
         | Metasploit Initialized (msfdb init)
         |
         |-- db_nmap: Port Scan and Service Discovery
         |
         |-- auxiliary/scanner/mysql/mysql_version
         |      --> Detects MySQL Version
         |
         |-- auxiliary/scanner/mysql/mysql_login
                --> Brute-force user login

## EXECUTION STEPS AND ITS OUTPUT:
Find out the ip address of the attackers system

## OUTPUT:
<img width="828" height="454" alt="Screenshot 2025-09-29 084140" src="https://github.com/user-attachments/assets/62c686ff-5fcb-4a56-89a2-f6e95bb52e8e" />
Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
```
sudo systemctl start postgresql
msfdb init
msfconsole
```
## OUTPUT:
<img width="823" height="453" alt="Screenshot 2025-09-29 084432" src="https://github.com/user-attachments/assets/bf044886-a81d-417b-a11b-52fdb129db18" />
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
<img width="828" height="690" alt="image" src="https://github.com/user-attachments/assets/e4efb93b-4899-488a-8f47-f511d4b1d397" />
Port Scanning: Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
```
nmap -sT 192.168.1810/24 -p1-1000
```
## OUTPUT:
<img width="836" height="896" alt="image" src="https://github.com/user-attachments/assets/859fa224-91fd-4bae-b51f-bc5891791f6e" />
step4: use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
```
db_nmap -sV -sC -p 3306 <target-ip>
```
## OUTPUT:
<img width="811" height="473" alt="image" src="https://github.com/user-attachments/assets/a680586a-8eda-4efb-880b-e1dafc0e91e8" />
Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
```
cd /usr/share /metasploit-framework/modules/auxiliary
ls -l
```

## OUTPUT:
![WhatsApp Image 2025-09-29 at 08 32 48_29026729](https://github.com/user-attachments/assets/342003b8-42ec-4691-8c87-1e4c9f748331)
Search is a powerful command in Metasploit that you can use to find what you want to locate.
```
search name:Microsoft type:exploit
```



## OUTPUT:
<img width="830" height="875" alt="Screenshot 2025-09-29 085013" src="https://github.com/user-attachments/assets/ac4ccd24-c38d-4ccd-9a71-9983fdfb24c7" />

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
```
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
```
## OUTPUT:
<img width="800" height="356" alt="Screenshot 2025-09-29 085132" src="https://github.com/user-attachments/assets/52119c8a-620e-424f-8d9a-c58fbafaf6a9" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
```
search type:auxiliary mysql
```
## OUTPUT:
<img width="820" height="679" alt="Screenshot 2025-09-29 085236" src="https://github.com/user-attachments/assets/9d37a1d8-614d-488e-9f16-3e9b2fb02d0b" />
```
use the auxiliary/scanner/mysql/mysql_version
```
## OUTPUT:
<img width="820" height="650" alt="Screenshot 2025-09-29 085356" src="https://github.com/user-attachments/assets/982ab240-8a42-41e5-9fef-4d8127d147f0" />

module by typing the module name or associated number to scan MySQL version details.
```
use 11
```
## OUTPUT:
<img width="1920" height="1055" alt="use11" src="https://github.com/user-attachments/assets/b58d676a-f8f7-4969-9472-930c83c1d696" />


Use the set rhosts command to set the parameter and run the module, as follows:

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:

set PASS_FILE /usr/share/wordlists/rockyou.txt

Then, specify the IP address of the target machine with the RHOSTS command.

set RHOSTS <metasploitable-ip-address>

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

set BLANK_PASSWORDS true
## OUTPUT:
<img width="828" height="904" alt="Screenshot 2025-09-29 085537" src="https://github.com/user-attachments/assets/907504f8-06f3-4fd6-be11-63678619daa3" />


## RESULT:
The Metasploit framework for reconnaissance is examined successfully
