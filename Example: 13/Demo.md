# Manage Virtual Machines

# Lab introduction

- In this lab, you create and compare virtual machines to virtual machine scale sets. You learn how to create, configure and resize a single virtual machine. You learn how to create a virtual machine scale set and configure autoscaling.

 # Lab scenario

- Your organization wants to explore deploying and configuring Azure virtual machines. First, you implement an Azure virtual machine with manual scaling. Next, you implement a Virtual Machine Scale Set and explore autoscaling.

# Job skills

- Task 1: Deploy zone-resilient Azure virtual machines by using the Azure portal.

- Task 2: Manage compute and storage scaling for virtual machines.

- Task 3: Create and configure Azure Virtual Machine Scale Sets.

- Task 4: Scale Azure Virtual Machine Scale Sets.

- Task 5: Create a virtual machine using Azure PowerShell (optional 1).

- Task 6: Create a virtual machine using the CLI (optional 2).

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/babfb797-aee2-40bd-9ffe-05d20f5b38fc)

# Task 1: Deploy zone-resilient Azure virtual machines by using the Azure portal

- In this task, you will deploy two Azure virtual machines into different availability zones by using the Azure portal. Availability zones offer the highest level of uptime SLA for virtual machines at 99.99%. To achieve this SLA, you must deploy at least two virtual machines across different availability zones.

1. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/19de69da-1e8e-4c6f-9b73-d2592176f970)

2. Search for and select Virtual machines, on the Virtual machine's blade, click + Create, and then select in the drop-down Azure virtual machine. Notice your other choices.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/5862d73a-d00e-4f29-9371-c7316e0372ef)

3. On the Basics tab, in the Availability zone drop-down menu, place a checkmark next to Zone 2. This should select both Zone 1 and Zone 2.

4. On the Basics tab, continue completing the configuration:

- Setting	Value

- Subscription	the name of your Azure subscription

- Resource group	az104-rg13 (If necessary, click Create new)

- Virtual machine names	az104-vm1 and az104-vm2 (After selecting both availability zones, select Edit names under the VM name field.)

- Region	East US

- Availability options	Availability zone

- Availability zone	Zone 1, 2 (read the note about using virtual machine scale sets)

- Security type	Standard

- Image	Windows Server 2019 Datacenter - x64 Gen2

- Azure Spot instance	unchecked

- Size	Standard D2s v3

- Username	as per your choice

- Password	Provide a secure password

- Public inbound ports	None

- Would you like to use an existing Windows Server license?	Unchecked

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c7e922a7-447e-4087-9469-1c200eae635b)


5. Click Next: Disks >, specify the following settings (leave others with their default values):

- Setting	Value

- OS disk type	Premium SSD

- Delete with VM	checked (default)

- Enable Ultra Disk compatibility	Unchecked

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b5a36bd4-a25c-4254-92ce-cc73192d3f40)

6. Click Next: Networking > Take the defaults but do not provide a load balancer.

- Setting	Value

- Delete public IP and NIC when VM is deleted	Checked

- Load balancing options	None

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/5b5057d3-e57d-448a-b88d-2c4054ef6d52)

7. Click Next: Management > and specify the following settings (leave others with their default values):

- Setting	Value

- Patch orchestration options	Azure orchestrated

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/bc870154-fecc-403a-9c29-c6ad8bbd45ac)

8. Click Next: Monitoring > and specify the following settings (leave others with their default values):

- Setting	Value

- Boot diagnostics	Disable

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b0a87662-6ecf-4bea-83d3-e22888a52f76)

9. Click Next: Advanced >, take the defaults, then click Review + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/45308a75-4ac1-4c42-a0db-b5b20aa4b566)

10. After the validation, click Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2e6396ad-ad65-4d87-b622-0f14e0c267b0)

11. Wait for the deployment to complete, then select Go to resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9053b667-9386-40a6-ae6e-2935d2dda546)

# VM 1
![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7a331c02-70fb-47e7-baba-0021c05fd360)

# VM 2
![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ef115e87-00c8-4573-9837-7c815294a599)

# Task 2: Manage compute and storage scaling for virtual machines

- In this task, you will scale a virtual machine by adjusting its size to a different SKU. Azure provides flexibility in VM size selection so that you can adjust a VM for periods if it needs more (or less) computing and memory allocated. This concept is extended to disks, where you can modify the performance of the disk, or increase the allocated capacity.

1. On the az104-vm1 virtual machine, in the Availability + scale blade, select Size.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/61450091-e339-48ef-a377-ec0d6bd84c45)

2. Set the virtual machine size to DS1_v2 and click Resize. When prompted, confirm the change.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/57584608-cf12-4d8f-b39f-bf58ce9c3fcb)

3. In the Settings area, select Disks.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/357efdfe-5798-4fac-ac0d-0a67cd487e90)

4. Under Data disks select + Create and attach a new disk. Configure the settings (leave other settings at their default values).

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/734eabc8-c89e-40b6-b507-dd1a0cff4a20)

- Setting	Value

- Disk name	vm1-disk1

- Storage type	Standard HDD

- Size (GiB)	32

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/102a3593-e050-4b14-8dd0-f1123957c257)

5. Click Apply.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/418249df-503e-4ffe-b7e1-f03b3994e9e7)

6. After the disk has been created, click Detach (if necessary, scroll to the right to view the detach icon), and then click Apply.

7. Search for and select Disks. From the list of disks, select the vm1-disk1 object.

8. In the Settings blade, select Size + Performance.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6ce80223-c66e-4e91-aac1-1493bd004011)

9. Set the storage type to Standard SSD, and then click Save.

10. Navigate back to the az104-vm1 virtual machine and select Disks.

11. In the Data disk section, select Attach existing disks.

12. In the Disk name drop-down, select VM1-DISK1.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/53684755-cf38-4742-9c29-ca81fddd1ec7)

13. Verify the disk is now Standard SSD.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3353fc89-9762-4adf-8c51-da62a89d849e)

14. Select Apply to save your changes.

# Azure Virtual Machine Scale Sets Architecture Diagram

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f7d89801-bece-470b-90a6-5874a519f619)

# Task 3: Create and configure Azure Virtual Machine Scale Sets

- In this task, you will deploy an Azure virtual machine scale set across availability zones. VM Scale Sets reduce the administrative overhead of automation by enabling you to configure metrics or conditions that allow the scale set to horizontally scale, scale in, or scale out.

1. In the Azure portal, search for and select Virtual machine scale sets and, on the Virtual machine scale sets blade, click + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3a7e8dbf-f917-4115-b75c-fdb5295391b4)

2. On the Basics tab of the Create a virtual machine scale set blade, specify the following settings (leave others with their default values) and click Next: Spot 

- Setting	Value

- Subscription	the name of your Azure subscription

- Resource group	az104-rg13

- Virtual machine scale set name	vmss1

- Region	(US)East US

- Availability zone	Zones 1, 2, 3

- Orchestration mode	Uniform

- Security type	Standard

- Image	Windows Server 2019 Datacenter - x64 Gen2

- Run with Azure Spot discount	Unchecked

-
- Size	Standard D2s_v3

- Username	as per your choice 

- Password	Provide a secure password

- Already have a Windows Server license?	Unchecked

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/201cdfb2-614a-4328-824b-59c006ca3096)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e9a1669c-a581-4160-a1ca-23d1f3cc04bb)

3. On the Spot tab, accept the defaults and select Next: Disks >.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/49c04bbe-0d84-441d-b724-21bc8e5bb351)

4. On the Disks tab, accept the default values and click Next: Networking >.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ee79869f-1265-4540-bf9b-02069f5ab9cc)

5. On the Networking page, click the Create Virtual Network link below the Virtual Network textbox and create a new virtual network with the following settings (leave others with their default values). When finished, select OK.

- Setting	Value

- Name	vmss-vnet

- Address Range	10.82.0.0/20 (change what is there)

- Subnet name	subnet0

- Subnet range	10.82.0.0/24

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/12a45fb2-349a-4456-aa15-f6058b9fe238)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b276da14-a724-48ce-94f0-4454714c0d83)

6. In the Networking tab, click the Edit network interface icon to the right of the network interface entry.

7. For the NIC network security group section, select Advanced and then click Create new under the Configure network security group drop-down list.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/64f74419-9308-4cbc-b4ad-860e23bf52f2)

8. On the Create network security group blade, specify the following settings (leave others with their default values):

- Setting	Value

- Name	vmss1-nsg

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a9670da7-4600-4e65-a7e8-4b40850cc715)

9. Click Add an inbound rule and add an inbound security rule with the following settings (leave others with their default values):

- Setting	Value

- Source	Any

- Source port ranges	*

- Destination	Any

- Service	HTTP

- Action	Allow

- Priority	1010

- Name	allow-HTTP

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/00b65233-a80b-4344-85ae-5c22026aef8d)

10. Click Add and, back on the Create network security group blade, click OK.

11. In the Edit network interface blade, in the Public IP address section, click Enabled and click OK.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/acfc6028-b055-4ced-9b39-31d085a098ee)

12. In the Networking tab, under the Load balancing section, specify the following (leave others with their default values).

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/48d29e3a-2da8-4984-9993-9d1b01cd0650)

- Setting	Value

- Load balancing options	Azure load balancer

- Select a load balancer	Create a load balancer

13. On the Create a load balancer page, specify the load balancer name and take the defaults. Click Create when you are done then Next: Management >.

- Setting	Value

- Load balancer name	vmss-lb

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/236ebc5f-54a5-44da-b23b-79c944f34407)

14. On the Management tab, specify the following settings (leave others with their default values):

- Setting	Value

- Boot diagnostics	Disable

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/61347626-73db-4809-8064-99f133649707)

15. Click Next: Health >.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6b40b0e2-84f2-46d8-a9fd-ca42b4697bc3)

16. On the Health tab, review the default settings without making any changes and click Next: Advanced >.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d425beb0-1551-400b-8aaa-717ef1eaef0c)

17. On the Advanced tab, click Review + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4257aaec-f24d-4e1b-8270-1c4c2e81d5bc)

18. On the Review + Create tab, ensure that the validation passed and click Create
