# Configure Route Rule and Security List for Data Guard Cross Region

After creating your VCN and DRG on both regions.  You will need to set the route rules and security lists so that the primary and standby databases can communicate.

Let's start on the standby side.  From your VCN hosting your standby database, select Route Tables.

![image-20210122202020691](images\image-20210122202020691.png)

Select the private subnet route table or click Create Route Table if the private subnet route table is not there.

Click Add Route Rules 

Select the Target Type as Dynamic Routing Gateways and select the name of the DRG gateway you created.

Enter the Destination CIDR Block.  The destination will be the primary region.  You can enter the CIDR block for the primary VCN or the primary private subnet CIDR block.  ie: 11.0.0.0/16.

Add description if desired.

Click Add Route Rules to finish.



![image-20210122200451778](images\image-20210122200451778.png)



Now configure the security list.  

Click Create Security List and name it something like Sec-List-Private-Subnet. 

Ensure you are in the correct compartment.

Click Add Ingress Rule with the following:

Stateless is unchecked.

Source Type is CIDR

Source CIDR is from your primary VCN or private subnet.  ie: 11.0.0.0/16 or 11.0.1.0/24.

IP Protocol is TCP

Source Port Range is All

Destination Port Range is 1521 for the database.

Add a description if desired.

![image-20210122200918911](images\image-20210122200918911.png)



Add an Egress Rule for outbound communication to the standby.

Stateless is unchecked.

Destination Type is CIDR.

Destination CIDR is your primary VCN or private subnet CIDR Block.  ie: 11.0.0.0/16 or 11.0.1.0/24.

IP Protocol is TCP

Source Port Range is All

Destination Port Range is 1521

Click Create Security List

![image-20210122201351067](images\image-20210122201351067.png)



Now do the same steps for the primary side.  This time the CIDR should be different since they can not overlap with the standby.



