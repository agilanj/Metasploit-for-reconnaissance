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

![ifconfig](img/01_ifcon.png)


Invoke msfconsole

## OUTPUT:

![msfconsole](img/02_msfconsole.png)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole

## OUTPUT:

![help](img/03_help.png)


Port Scanning:

msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![nmap](img/04_nmap.png)


scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24

# OUTPUT:

![db_nmap](img/05_db_nmap.png)


cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l

## OUTPUT:

![ls-l](img/06_ls-l.png)


msf >search name:Microsoft type:exploit

## OUTPUT:

![searchname](img/07_searchname.png)
![searchname](img/08_searchname2.png)

The info command provides information regarding a module or platform,

## OUTPUT:

![info](img/09_info.png)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.

db_nmap -sV -sC -p 3306<metasploitable_ip_address>

## OUTPUT:

![dbnmap](img/10_dbnmap.png)



Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.

search type:auxiliary mysql

## OUTPUT:

![seachtye](img/11_searchtype.png)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.

use 11


## OUTPUT:

![use11](img/11_use11.png)


Use the set rhosts command to set the parameter and run the module, as follows:


## OUTPUT:

![set_rhosts](img/12_set_rhosts.png)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.


## OUTPUT:

![use_mysql_login](img/13_use_mysqllogin.png)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

## OUTPUT:

![set_PASSFILE](img/14_set_PASSFILE.png)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
