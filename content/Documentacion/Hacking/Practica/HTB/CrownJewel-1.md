##### Sherlock Scenario

Forela's domain controller is under attack. The Domain Administrator account is believed to be compromised, and it is suspected that the threat actor dumped the NTDS.dit database on the DC. We just received an alert of vssadmin being used on the DC, since this is not part of the routine schedule we have good reason to believe that the attacker abused this LOLBIN utility to get the Domain environment's crown jewel. Perform some analysis on provided artifacts for a quick triage and if possible kick the attacker as early as possible.

CrownJewel1.zip

10 MB

### Task 1
Attackers can abuse the vssadmin utility to create volume shadow snapshots and then extract sensitive files like NTDS.dit to bypass security mechanisms. Identify the time when the Volume Shadow Copy service entered a running state.

Identificar en en evetviewer el proceso 7036 y ver en que momento el volume shadow ha empezado a estar en el estado running. Buscamos los detalles del evento y entramos a la parte XML.

==`2024-05-14 03:42:16`==
### Task 2
When a volume shadow snapshot is created, the Volume shadow copy service validates the privileges using the Machine account and enumerates User groups. Find the two user groups the volume shadow copy process queries and the machine account that did it.


### Task 3
Identify the Process ID (in Decimal) of the volume shadow copy service process.


### Task 4
Find the assigned Volume ID/GUID value to the Shadow copy snapshot when it was mounted.


### Task 5
Identify the full path of the dumped NTDS database on disk.



### Task 6
When was newly dumped ntds.dit created on disk?


### Task 7
A registry hive was also dumped alongside the NTDS database. Which registry hive was dumped and what is its file size in bytes?