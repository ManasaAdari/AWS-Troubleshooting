

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
Create security groups
Launch Replication Server
Boot Replication Server
Authenticate with service  <<<<=====//
Download replication software
Create staging disks
Attach staging disks
Pair Replication Server with AWS Replication Agent
Connect AWS Replication Agent to Replication Server
Start data transfer
