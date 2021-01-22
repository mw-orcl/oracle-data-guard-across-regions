Prerequisite

User policies to set up the VCN peering

In order to configure Data Guard across regions we must set up remote VCN peering.  Remote VCN peering connects VCNs in different regions together.  The peering allows resources with private IP address to communicate.

A picture of the remote VCN peering is shown below.  



![This image shows the basic layout of two VCNs that are remotely peered, each with a remote peering connection on the DRG](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/network_remote_peering_basic.png)

The DRG or Dynamic Routing Gateway must be set up on both VCNs and the RPC or Remote Peering Connection is then configured to connect the two VCNs.  

The route rule and security list must also be configured to access the resources in the VCN.

Step 1 

Create the DRGs in both VCNs.  

Select the menu Networking 

Select Dynamic Routing Gateways

Click Create Dynamic Routing Gateway

Ensure you are in the right compartment 

Name your DRG and click create

Perform the same steps in the second region.



![image-20210121224925100](C:\Users\mwan.ORADEV\AppData\Roaming\Typora\typora-user-images\image-20210121224925100.png)



Step 2 - Create the RPCs in both VCNs.

Step 3 - 







