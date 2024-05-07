# Metasploit-for-reconnaissance
Metasploit for reconnaissance in pentesting
## NAME: VISHAL T
## REG.NO: 212223100060
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

Finding the ip address of the attackers system.
```
ifconfig
```
## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/1b8fa2ed-9356-4ddb-ba40-750deb2665e6)


Invoking msfconsole
```
msfconsole 
```
## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/5ff6fd93-9a74-4cf5-a0ae-cb8195c5ac95)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/fd1768e3-5b14-4ccd-bbb6-11f121e366c0)


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
```
msf >  nmap -sT 192.168.237.0/24 -p1-1000
```
## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/4400a12b-e691-44c1-a793-41cb2719fb0c)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
```
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
```

## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/010e43ef-19c3-4fe0-b9fc-9ad92c007315)


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
```
msf >search name:Microsoft type:exploit
```
## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/1c447c42-8ce9-4acf-9cbc-05917c748911)


The info command provides information regarding a module or platform.

## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/597eaa81-7192-42f3-9e92-53237fcbf9be)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
```
systemctl start postgresql
msfdb init
```
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
```
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
```
## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/ad3236ca-ee5b-4c4f-a458-eb2844bad87a)



Use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows.
```
msf > db_nmap 192.168.181.0/24
```
if the database is not connected start the service by the following commands.
```
udo service postgresql start
```
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/e322805c-7742-4c0f-bf71-544985c896c8)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
```
search type:auxiliary mysql
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/b334ac2c-ad84-4b97-b945-489ff3d08440)



use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
```
use 11
```
or 
```
use auxiliary/scanner/mysql/mysql_version
```
## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/f241b841-ddf0-4993-87c0-bc8788ba461a)



Use the set rhosts command to set the parameter and run the module, as follows:
```
set rhosts 192.168.120.142
```
## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/117b5135-0564-4a39-98b4-aed9894648db)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/a9c6e4e3-b1e1-439d-ac58-a76d1218120a)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists
```
set PASS_FILE /usr/share/wordlists/rockyou.txt
```
Then, specify the IP address of the target machine with the RHOSTS command.
```
set RHOSTS <metasploitable-ip-address>
```
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
```
set BLANK_PASSWORDS true
```
## OUTPUT:
![image](https://github.com/Saranyaaav/Metasploit-for-reconnaissance/assets/144870813/44cc62ee-986c-4386-bc7b-706c72f19860)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
