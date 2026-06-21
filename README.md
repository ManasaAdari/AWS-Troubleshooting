<img width="1201" height="758" alt="image" src="https://github.com/user-attachments/assets/79c85953-e050-4278-981e-d8bb1192b14e" />

MGN
-------------

Today understand MGN[Migration] concept in simple way :

1. Old Server ➡️ Agent copies everything ➡️ New Server in AWS ➡️ Test it ➡️ Switch over! ✅

Lifecycle of Migration phases:

Not ready -> Ready for testing -> Test in progress -> Ready for cutover -> Cutover in progress -> Cutover complete

Steps:
----
Connect to the AWS MGN Dashboard
Click on Source servers, then click on the source server listed
Under Migration Dashboard, monitor the "Data replication status":

Wait until the "Replication initiation steps" complete
Wait until "Data replication status" shows "Healthy" and "Lifecycle" shows "Ready for testing"
Note: This may take between 15 and 20 minutes.

Once ready, launch a Test instance
Monitor the MGN job under "Launch history" — click on the job ID to track progress


Replication initiation steps:
----

1. Create security groups
2. Launch Replication Server
3. Boot Replication Server
4. Authenticate with service  
5. Download replication software
6. Create staging disks
7. Attach staging disks
8. Pair Replication Server with AWS Replication Agent
9. Connect AWS Replication Agent to Replication Server
10. Start data transfer

Network requirements for MGN :

This document clearly explains everything for network requirements related to MGN service-
[+] https://docs.aws.amazon.com/mgn/latest/ug/preparing-environments.html

Please check the architecture diagram of MGN service above.
