# Create your VCN

Oracle Data Guard provide disaster recovery for your Oracle databases.  A standby database is set up to receive redo "transaction" logs from the primary database.  In the event of a disaster on the primary database, a failover to the standby database will occur.  

For disaster recovery, it is a best practice to set up the primary and standby database in two different data centers located in different geographies.  In this guide we will be setting up Oracle Data Guard between two cloud regions.  

Prerequisites

- Oracle Cloud Account with access to more than one region

- Oracle Cloud user role to manage networks and databases

- SSH public and private keys

- Compartment to work on


Although the primary database will be in one region and the standby in another region, they must both be in the same compartment.  And they must both not have overlapping VCN IP address blocks.

1. Sign in to Oracle Cloud

2. Create an Oracle cloud network called a Virtual Cloud Network.  You will provision the Oracle Database Cloud Service on this network.

3. Select your region and compartment


![image-20210121174143796](images\image-20210121174143796.png)

4. Go to Networking/Virtual Cloud Network
5. Click Start VCN Wizard

![image-20210121173942686](images\image-20210121173942686.png)



6. Select VCN with Internet Connectivity to create your cloud network.

7. Click Start VCN Wizard.  

![image-20210121180617626](images\image-20210121180617626.png)



8. Give your VCN a name of your choice.

9. Enter a CIDR block.  The CIDR block must not be the same as your cross region CIDR block because we will need to peer them together later so they must be different.  

ie: 10.0.0.0/16 for one region and 11.0.0.0/16 for the peer region.

10. Update your subnet CIDR block accordingly.

![image-20210121181204561](images\image-20210121181204561.png)

11. Click Next and then Click Create.  Your cloud network will be created quickly. 
12. Now do the same steps and create another VCN on your peer region.  

Switch to your peer region and create your VCN.  Remember it must be in the same compartment.





