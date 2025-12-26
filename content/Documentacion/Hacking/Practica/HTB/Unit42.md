##### Sherlock Scenario

In this Sherlock, you will familiarize yourself with Sysmon logs and various useful EventIDs for identifying and analyzing malicious activities on a Windows system. Palo Alto's Unit42 recently conducted research on an UltraVNC campaign, wherein attackers utilized a backdoored version of UltraVNC to maintain access to systems. This lab is inspired by that campaign and guides participants through the initial access stage of the campaign.

### Task 1
How many Event logs are there with Event ID 11?
![[Pasted image 20251018184117.png]]

==`56`==

### Task 2
Whenever a process is created in memory, an event with Event ID 1 is recorded with details such as command line, hashes, process path, parent process path, etc. This information is very useful for an analyst because it allows us to see all programs executed on a system, which means we can spot any malicious processes being executed. What is the malicious process that infected the victim's system?

Para saber el proceso que ejecuta normalmente es el id. del evento ==1==

==`C:\Users\CyberJunkie\Downloads\Preventivo24.02.14.exe.exe`==


### Task 3
Which Cloud drive was used to distribute the malware?

Para saber el proceso que es ejecutado desde una unidad externa (internet) es el id.del evento ==22==

==`Dropbox`==

### Task 4
For many of the files it wrote to disk, the initial malicious file used a defense evasion technique called Time Stomping, where the file creation date is changed to make it appear older and blend in with other files. What was the timestamp changed to for the PDF file?

Para saber el proceso que cambia la fecha llamado como timestomping, básicamente es la técnica que usan los atacantes para cambiar la fecha de cuando se instala para que pase desapercibido con los archivos del sistema, es el id.del evento ==2==

==`2024-01-14 08:10:06`==



### Task 5
The malicious file dropped a few files on disk. Where was "once.cmd" created on disk? Please answer with the full path along with the filename.

==`C:\Users\CyberJunkie\AppData\Roaming\Photo and Fax Vn\Photo and vn 1.1.2\install\F97891C\WindowsVolume\Games\once.cmd`==

### Task 6
The malicious file attempted to reach a dummy domain, most likely to check the internet connection status. What domain name did it try to connect to?

==`www.example.com`==


### Task 7
Which IP address did the malicious process try to reach out to?

Para identificar el proceso que intenta conexiones externas, es el id.del evento ==3==

==`93.184.216.34`==

### Task 8
The malicious process terminated itself after infecting the PC with a backdoored variant of UltraVNC. When did the process terminate itself?

El proceso ==5== sirve para identificar que un proceso existe.

==`2024-02-14 03:41:58`==