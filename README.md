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
<img width="743" height="355" alt="Screenshot 2026-02-09 133054" src="https://github.com/user-attachments/assets/70ad0203-2271-4653-bd91-3b0079eb2fc3" />
<img width="679" height="74" alt="Screenshot 2026-02-09 134359" src="https://github.com/user-attachments/assets/46ccf04a-d819-49f1-9d41-e9ef68d03101" />


Invoke msfconsole:
## OUTPUT:

<img width="657" height="404" alt="Screenshot 2026-02-09 133132" src="https://github.com/user-attachments/assets/31293ed8-398b-400b-a26c-6e4f4dccf179" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


<img width="950" height="947" alt="Screenshot 2026-02-09 133202" src="https://github.com/user-attachments/assets/f4791af6-35f9-4c1e-a447-03ccbd285ec0" />


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="581" height="370" alt="Screenshot 2026-02-09 134625" src="https://github.com/user-attachments/assets/3a6e2a90-6308-437e-8716-c9da242dbfb6" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="656" height="313" alt="Screenshot 2026-02-09 135352" src="https://github.com/user-attachments/assets/5c109af0-4696-44e2-b8db-75b5f8e9b606" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="731" height="400" alt="Screenshot 2026-02-09 135527" src="https://github.com/user-attachments/assets/28254433-32fe-4b4e-81fb-281f06a69c93" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Google type:exploit
## OUTPUT:

<img width="940" height="764" alt="Screenshot 2026-02-09 135636" src="https://github.com/user-attachments/assets/d11a622f-ebe5-4371-b1c5-f9c3201121da" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="947" height="751" alt="Screenshot 2026-02-09 135806" src="https://github.com/user-attachments/assets/1bb5cb66-62ea-40fd-ac34-1071f63e3278" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="868" height="152" alt="Screenshot 2026-02-09 140005" src="https://github.com/user-attachments/assets/1a550e67-75bd-4388-9e02-b34a0f2d4898" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="949" height="645" alt="Screenshot 2026-02-09 140045" src="https://github.com/user-attachments/assets/9b9037ba-9cbb-4be5-99d7-eba19bfb5794" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="934" height="258" alt="Screenshot 2026-02-09 140512" src="https://github.com/user-attachments/assets/dd884e7c-bc19-4b8b-9cc0-0b5e81c675e9" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="934" height="258" alt="Screenshot 2026-02-09 140512" src="https://github.com/user-attachments/assets/75eb7b2a-356e-4ff7-9cb7-e71356e6e0f7" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="947" height="361" alt="Screenshot 2026-02-09 140553" src="https://github.com/user-attachments/assets/24d5030b-ec44-4da3-b129-224085bd105a" />


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:


<img width="825" height="180" alt="image" src="https://github.com/user-attachments/assets/d822e533-0e87-4ac1-9676-a38bb0a5a7e3" />




## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
