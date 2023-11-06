# Metasploit-for-reconnaissance
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

1) Install kali linux either in partition or virtual box or in live mode
2) Investigate on the various categories of tools as follows
3) Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/20bda294-8613-41d0-b892-72b3f686ab92)


Invoke msfconsole:

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/53946bb3-25e2-4886-b545-26b514f5ff55)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/47c9c3b4-71be-44e7-bfe3-8da20d0853c5)



Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/2df3e285-33ed-4502-8a95-682b35b951f2)


USE the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24


## OUTPUT:

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/1a8a103e-cab4-40e4-aaf7-0f5f3a3769e8)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/7c9cd001-0036-468f-902e-5a17885992eb)



Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,

## OUTPUT

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/421046b4-4b96-45cb-801a-91ea0e7f992d)



Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/c10cdeca-4b89-41d8-84b3-e247c6e35fe6)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/4a7f9869-48cf-467f-afd3-4d6239bbc199)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/358798e5-fe3f-40a5-be2b-dde671890c6e)



Use the set rhosts command to set the parameter and run the module, as follows:

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/0255fdae-ea6d-43bd-8e73-6a4b970bb9f2)



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/cd66b841-bd11-4b24-910f-9d0bd137eef9)



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true

![image](https://github.com/Bharath745/Metasploit-for-reconnaissance/assets/94508354/ef8720da-118d-49aa-84e3-9c6fba2df3df)




## RESULT:

The Metasploit framework for reconnaissance is  examined successfully
