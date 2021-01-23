Configure Route Rule and Security List for Data Guard Cross Region

After creating your VCN and DRG on both regions.  You will need to set the route rules and security lists so that the primary and standby databases can communicate.

From your VCN hosting your standby database, select Route Tables.

![image-20210122202020691](C:\Users\mwan.ORADEV\AppData\Roaming\Typora\typora-user-images\image-20210122202020691.png)

Select the private subnet route table or click Create Route Table if the private subnet route table is not there.

Click Add Route Rules 

Select the Target Type as Dynamic Routing Gateways

Enter the Destination CIDR Block.  You can enter the CIDR block for the standby VCN or the standby private subnet CIDR block.  



![image-20210122200451778](C:\Users\mwan.ORADEV\AppData\Roaming\Typora\typora-user-images\image-20210122200451778.png)



Now configure the security list.  

Click Create Security List and name it something like Sec-List-Private-Subnet. 

Ensure you are in the correct compartment.

Click Add Ingress Rule with the following:

Stateless is unchecked.

Source Type is CIDR

Source CIDR is from your primary VCN or private subnet.  ie: 11.0.0.0/16

IP Protocol is TCP

Source Port Range is All

Destination Port Range is 1521 for the database.

Add a description

![image-20210122200918911](C:\Users\mwan.ORADEV\AppData\Roaming\Typora\typora-user-images\image-20210122200918911.png)



Add an Egress Rule for outbound communication to the standby.

Stateless is unchecked.

Destination Type is CIDR.

Destination CIDR is your primary VCN or private subnet CIDR Block.  ie: 11.0.0.0/16

IP Protocol is TCP

Source Port Range is All

Destination Port Range is 1521

Click Create Security List

![image-20210122201351067](C:\Users\mwan.ORADEV\AppData\Roaming\Typora\typora-user-images\image-20210122201351067.png)



Now do the same steps for the primary side.  This time the CIDR should be different since they can not overlap with the standby.

!(C:\Users\mwan.ORADEV\AppData\Roaming\Typora\typora-user-images\image-20210122200330950.png)

![image-20210121222653541](C:\Users\mwan.ORADEV\AppData\Roaming\Typora\typora-user-images\image-20210121222653541.png)