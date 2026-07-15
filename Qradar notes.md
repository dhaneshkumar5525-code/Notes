Video one :
Home page 
<img width="1913" height="873" alt="image" src="https://github.com/user-attachments/assets/7624c3f5-ef14-49ba-9a62-8cfaecb8a98a" />

Ibm provides 
Default ids/ips top signature (event count)
Top sytem sourcing attack 
these are the provided tabs
<img width="1261" height="406" alt="image" src="https://github.com/user-attachments/assets/389c3790-fbcf-49e7-935a-ac2f8d3b5c28" />

Creating a new dashboard 
Click new dashboard > create new dashboard 
<img width="563" height="518" alt="image" src="https://github.com/user-attachments/assets/7db9d4d2-866e-4735-b74c-c9c950550d7d" />

Lets navigate to offence management tab we can see the queue in all offences
<img width="1915" height="875" alt="image" src="https://github.com/user-attachments/assets/3fb24547-1f07-40a0-b08b-d448f3be340f" />

Important -- If there are 100 offence mostly 95-97 are just security noise combination of harmless alerts, health and false positive ( It is a real connection  from a external malicous ip but ips blocked the connection, so there is no risk since it is a blocked attack,prevented attack or migated attack


## Investiagtion process 
1) A offence generate in the siem a automated script pulls offences for every 60 seconds and updates the in the queue in the ticketing tool  
2) Assign to yourself in both tickecting tool and the siem dashboard - change the status into in progress 
3) step 1:  Validate the Alert 
  <img width="897" height="365" alt="image" src="https://github.com/user-attachments/assets/fdf91754-881a-42f0-8101-d803ba56e8c8" />

4) step 2 : Asset and user profiling 
 ( This step comes before collection of ioc and ioa)
 -- sla service level agreement --
 <img width="846" height="263" alt="image" src="https://github.com/user-attachments/assets/202d8332-6501-449a-86de-1474e965d918" />

 However, if the user profile shows the activity was done by a Senior Domain Administrator during their regular shift, it is authorized work. If the user profile shows it was a graphic designer at 3:00 AM, it is a critical security breach.

Note : *** It prevents tunnel vision on ioc ***
<img width="883" height="325" alt="image" src="https://github.com/user-attachments/assets/d8f49705-d5e0-4ad2-90a8-0600abcd463c" />

5) determine the scope 
Find out if the attacker is isolated to one computer or if they have moved across your network.
<img width="1003" height="300" alt="image" src="https://github.com/user-attachments/assets/f1509224-294e-4b66-9748-d8e34f03c104" />

6) Collect Evidence (Gathering IoCs) and ioas 
7) containment - temporary strict firewall on os kernal and forensic package a single tunnel opens
You will access the isolated machine directly through your central EDR dashboard using remote shell
8) investigation and eradication
9) Recovery
10) reporting and lesson learnt






Ticketing tool
A tickecting tool directly integrates with siem to automatically convert security alert into actionable incident tickets for the analyst
Main uses:
1) Automated alets : Siem sends critical alerts directly to the ticketing tool
2) Tracks progress : It is used to assign ownership tract status of the ticket 
3) Audit : It tracts metric for mean time to detect (MTTD) and mean time to respond (MTTR) and provide documented proof of investigation
4) Reduces noise : Reduces alert faitque
By using SOAR as middle man. The alerts comes to the siem dashboard it triggers a automated script that sends a http post request (The name is http but it used https to send because of the sensitive data) containing data to create tickects on the jira but it is intercepted by soar.
Steps :
1) Siem doesnot send entire data to the soar. It only send the precise log entires which triggered security rule
Rule trigger > data extractions > payload packing in structured format called "JSON"
<img width="911" height="614" alt="image" src="https://github.com/user-attachments/assets/04751d44-e716-423c-8ca9-754f808060ed" />

2)Siem pushes this json data package via webhook through HTTP POST > parsing process > Playbook execution --- take attacker ip and runs a api query in virus total and checks for the usernames in active directory 
It also use run book execution
example - A multiple failed logins from a internal machine to backup server
<img width="869" height="702" alt="image" src="https://github.com/user-attachments/assets/652e0f7d-3802-4d72-8155-10b72042621a" />

The automated script was running on the old credentials triggering this failed login alerts. Instead we can use soar to apply condition that ignore multiple failed logins from this ip close the alert as false posite and add a comment saying why it is false positive
<img width="814" height="334" alt="image" src="https://github.com/user-attachments/assets/b42ddddd-5ae1-4171-a9f1-e6c5ac5218a4" />

### Note : Some compaines avoid soar due to the high expensive cost
<img width="829" height="252" alt="image" src="https://github.com/user-attachments/assets/a0032063-3003-49ec-8cc3-191471d6c833" />

### once the soar reduces the no.of incident into few then it uses "bi-directional syschronization" .It ensures that the SIEM and the ticketing tool always match perfectly.
<img width="916" height="564" alt="image" src="https://github.com/user-attachments/assets/bafd62cb-210f-4342-af03-1718ef6c277c" />

Difference between ioc and ioa :
Ioa is collected to stop the active attack and ioc are collected as evidence for passive attack
Ioc and ioa are present in both network flow and event logs - analyse both of them to find the active connection for ioa 
<img width="954" height="372" alt="image" src="https://github.com/user-attachments/assets/67f694af-165e-4f21-a6ad-74851334c12d" />












