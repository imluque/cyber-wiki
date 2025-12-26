##### Sherlock Scenario

Susan works at the Research Lab in Forela International Hospital. A Microsoft Defender alert was received from her computer, and she also mentioned that while extracting a document from the received file, she received tons of errors, but the document opened just fine. According to the latest threat intel feeds, WinRAR is being exploited in the wild to gain initial access into networks, and WinRAR is one of the Software programs the staff uses. You are a threat intelligence analyst with some background in DFIR. You have been provided a lightweight triage image to kick off the investigation while the SOC team sweeps the environment to find other attack indicators.

RomCom.zip

#### Task 1 
What is the CVE assigned to the WinRAR vulnerability exploited by the RomCom threat group in 2025?

==`CVE-2025-8088`==

#### Task 2
What is the nature of this vulnerability?

==`path traversal`==

#### Task 3
What is the name of the archive file under Susan's documents folder that exploits the vulnerability upon opening the archive file?


#### Task 4
When was the archive file created on the disk?



#### Task 5
When was the archive file opened?



#### Task 6
What is the name of the decoy document extracted from the archive file, meant to appear legitimate and distract the user?


#### Task 7
What is the name and path of the actual backdoor executable dropped by the archive file?



#### Task 8
The exploit also drops a file to facilitate the persistence and execution of the backdoor. What is the path and name of this file?


#### Task 9
What is the associated MITRE Technique ID discussed in the previous question?



#### Task 10
When was the decoy document opened by the end user, thinking it to be a legitimate document?