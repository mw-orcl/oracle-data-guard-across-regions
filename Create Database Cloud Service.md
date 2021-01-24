# Create your primary database with the Oracle Database Cloud Service.

Select the menu Oracle Databases then Bare Metal, VM, and Exadata.

Select your compartment.

Click Create DB System.

Ensure your compartment is selected.

Enter a name for your database for the UI display.

If you have more than one availability domain, select any one.

For the lab we will use a virtual machine with only one core.  

Data Guard supports RAC databases, but we'll use a single instance database in the lab.  

Standard Edition does not support Data Guard, select the other editions.

![image-20210121184635385](images\image-20210121184635385.png)



For faster provisioning for this lab, select Logical Volume Manager.

Use the default storage size.

Add your SSH public key.



![image-20210121184848646](images\image-20210121184848646.png)



Select BYOL if you have an existing Oracle license to use.   If not, select License Included which means you are subscribing to a new database license.  If you are using a free credits account, you will not be charged.

Select your VCN you created earlier.

Select the private subnet.  Your databases should be provisioned in a private subnet for security.

Give it a hostname prefix.

Click Next



![image-20210121185143404](images\image-20210121185143404.png)

Provide a database name, must be 8 characters or less.

Provide a strong password for your database sys user.

Select OLTP or DW.

Click Create DB System.  Your Oracle Database Cloud Service will be created in a few minutes.



![image-20210121185604333](images\image-20210121185604333.png)