# Peer the VCN Together

Prerequisite

User policies to set up the VCN peering  (if you do not have admin policies, refer to the documentation to add peering policies)

DRGs on both VCN already created



In order to configure Data Guard across regions we must first set up remote VCN peering.  Remote VCN peering connects VCNs in different regions together.  The peering allows resources such as the database with private IP address to communicate across regions.

A picture of the remote VCN peering is shown below.  



![This image shows the basic layout of two VCNs that are remotely peered, each with a remote peering connection on the DRG](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/network_remote_peering_basic.png)



If you don't have admin policies you will need to add remote peering policies.  A diagram of the policies follows.  Refer to the documentation for more information.

![This image shows the two policies for VCNs in different regions but in the same tenancy.](https://docs.oracle.com/en-us/iaas/Content/Resources/Images/network_remote_peering_policy_same_tenancy.png)





The DRG or Dynamic Routing Gateway must be set up on both VCNs and the RPC or Remote Peering Connection is then configured to connect the two VCNs.  

The route rule and security list must also be configured to access the resources in the VCN.

Create the DRGs in both VCNs.  

Pick a region to start with.  You can pick either the primary side or the standby.

Select the menu Networking 

Ensure you are in the right region and compartment 

Select Dynamic Routing Gateways

Click Create Dynamic Routing Gateway

Name your DRG and click create

Perform the same steps in the second region.

![image-20210124110913518](images\image-20210124110913518.png)



Create the RPCs in both VCNs.

Select the DRG you created.

Ensure you are in the correct region and compartment.

Select from Resources the Remote Peering Connections.

Click Create Remote Peering Connection.

Provide a name for the connection.

Create the RPC.



![image-20210124111112366](images\image-20210124111112366.png)



Now do the same on the other DRG in the other region.

Once you have both DRGs and RPCs created.  You must decide which side accepts a connection, and which side requests a connection.

For our lab, we'll use the standby side as the acceptor, and the primary side as the requestor.  

Navigate to the standby region.

Record the OCID of the RPC on the standby side.  You will provide this to the primary side later to establish the peering.

![image-20210124114804001](images\image-20210124114804001.png)



Navigate to your primary region

Select the DRG then the RPC you created.

On the right 3 dot action menu, select Establish Connection.



![image-20210124114006763](images\image-20210124114006763.png)

Enter the standby region you will establish the connection with.

Paste in the OCID of the RPC from the standby region.

Click Establish Connection.  Your connection will be established in a few minutes.



![image-20210124114207345](images\image-20210124114207345.png)



The Peering Status will show Peered if it is successful.