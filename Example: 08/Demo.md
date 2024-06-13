# Implement Intersite Connectivity

# Lab introduction

- In this lab, you explore communication between virtual networks. You implement virtual network peering and test connections. You will also create a custom route.

# Lab scenario

- - Your organization segments core IT apps and services (such as DNS and security services) from other parts of the business, including your manufacturing department.
- However, in some scenarios, apps and services in the core area need to communicate with apps and services in the manufacturing area. In this lab, you configure connectivity between the segmented areas.
- This is a common scenario for separating production from development or separating one subsidiary from another.

- ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8cfceae0-b6cd-4aed-8b76-623f7ab8e3bb)

# Job skills

Task 1: Create a virtual machine in a virtual network.
Task 2: Create a virtual machine in a different virtual network.
Task 3: Use Network Watcher to test the connection between virtual machines.
Task 4: Configure virtual network peerings between different virtual networks.
Task 5: Use Azure PowerShell to test the connection between virtual machines.
Task 6: Create a custom route.

# Task 1: Create a core services virtual machine and virtual network

- You create a core services virtual network with a virtual machine in this task.

1. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f7a74202-da4b-4415-881d-1f3707fa80ca)

2. Search for and select Virtual Machines.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/fed9801e-8d8e-498b-8d07-f9c409ecaca3)

3. Select Create from the virtual machines page then select Azure Virtual Machine.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/aa3b451a-7a8d-4794-a6ac-e0b671218b49)

4. On the Basics tab, use the following information to complete the form, and then select Next: Disks >. For any setting not specified, leave the default value.

- Setting	Value

- Subscription	your subscription
- Resource group	az104-rg5 (If necessary, Create new. )
- Virtual machine name	CoreServicesVM
- Region	(US) East US
- Availability options	No infrastructure redundancy is required
- Security type	Standard
- Image	Windows Server 2019 Datacenter: x64 Gen2 (notice your other choices)
- Size	Standard_DS2_v3
- Username	ankit
- Password	Provide a complex password
- Public inbound ports	None
- Username	local admin
- Password	Provide a complex password
- Public inbound ports	None

  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6786a924-eaa1-4ee7-b826-5adc7e4af273)

5. On the Disks tab take the defaults and then select Next: Networking >.

6. On the Networking tab, for Virtual network, select Create new.

7. Use the following information to configure the virtual network, and then select Ok. If necessary, remove or replace the existing information.

- Setting	Value

Name	CoreServicesVnet (Create new)
Address Range	10.0.0.0/16
Subnet Name	Core
Subnet address range	10.0.0.0/24

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/44fd3e1c-8aed-4388-b347-f57adf59469f)

8. Select the Monitoring tab. For Boot Diagnostics, select Disable.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/bd75fac8-ec76-499b-8fdb-b3b898a40410)

9. Select Review + Create, and then select Create.

10. You do not need to wait for the resources to be created. Continue to the next task.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6b334aaa-6b03-4337-8fbf-d522a8feddb6)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/bcfe03dd-3ca6-40a4-a817-06874081363c)

# Task 2: Create a virtual machine in a different virtual network

- In this task, you create a manufacturing services virtual network with a virtual machine.

1. From the Azure portal, search for and navigate to Virtual Machines.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/45baab44-5fee-45e1-b19f-233fd3683486)

2. Select Create from the virtual machines page then select Azure Virtual Machine.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/849cd0a1-ec3f-4552-b2dd-ef8366e13b2d)
3. On the Basics tab, use the following information to complete the form, and then select Next: Disks >. For any setting not specified, leave the default value.

- Setting	Value

Subscription	your subscription
Resource group	az104-rg5
Virtual machine name	ManufacturingVM
Region	(US) East US
Security type	Standard
Availability options	No infrastructure redundancy is required
Image	Windows Server 2019 Datacenter: x64 Gen2
Size	Standard_DS2_v3
Username	ankit
Password	Provide a complex password
Public inbound ports	None

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c571e90a-c1d4-4ec8-88e2-0a2ef9739971)

4. On the Disks tab take the defaults and then select Next: Networking >.

5. On the Networking tab, for Virtual network, select Create new.

6. Use the following information to configure the virtual network, and then select Ok. If necessary, remove or replace the existing address range.

Setting	Value
Name	ManufacturingVnet
Address Range	172.16.0.0/16
Subnet Name	Manufacturing
Subnet address range	172.16.0.0/24

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/366deccc-db12-4ee6-89aa-98efa1ed1672)

7. Select the Monitoring tab. For Boot Diagnostics, select Disable.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/bd75fac8-ec76-499b-8fdb-b3b898a40410)

8. Select Review + Create, and then select Create

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/871f5a4b-89e3-4063-bae2-ae6b746da677)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a4f7688c-60cc-40b5-8a5d-766edea973ab)
 
# Task 3: Use Network Watcher to test the connection between virtual machines

-In this task, you verify that resources in peered virtual networks can communicate with each other. Network Watcher will be used to test the connection. Before continuing, ensure both virtual machines have been deployed and are running.

1. From the Azure portal, search for and select Network Watcher.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/547f66bd-5e1a-4f66-b746-e0e6c29ce64d)

2. From Network Watcher, in the Network diagnostic tools menu, select Connection Troubleshoot.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1704cbe2-5897-41e1-90e3-4dbeff38620b)

3. Use the following information to complete the fields on the Connection troubleshooting page.

- Field	Value

Source type	Virtual machine
Virtual machine	CoreServicesVM
Destination-type	Virtual machine
Virtual machine	ManufacturingVM
Preferred IP Version	Both
Protocol	TCP
Destination port	3389
Source port	Blank
Diagnostic tests Default

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/759d3bdf-ec3b-47b7-9dbb-88bcd46b5ca3)

4. Select Run diagnostic tests.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3204dc31-ac12-426c-963a-daae5537b28f)


# Task 4: Configure virtual network peerings between virtual networks

- In this task, you create a virtual network peering to enable communications between resources in the virtual networks.

1. In the Azure portal, select the CoreServicesVnet virtual network.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f2881fb4-48d7-4273-99f8-e6feb60ffd4b)

2. In CoreServicesVnet, under Settings, select Peerings.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/53eae71f-2195-4625-974e-cfdaa1ef2aa1)

- On CoreServicesVnet	Peerings, select + Add.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/da69a331-ccf5-44a9-80ab-eb40fcb9e1cb)

4. Use the information in the following table to create the peering.

**Parameter	Value**

**This virtual network**	 

- Peering link name	CoreServicesVnet-to-ManufacturingVnet
- Allow CoreServicesVnet to access the peered virtual network	selected (default)
- Allow CoreServicesVnet to receive forwarded traffic from the peered virtual network	selected
- Allow gateway in CoreServicesVnet to forward traffic to the peered virtual network	Not selected (default)
- Enable CoreServicesVnt to use the peered virtual networks’ remote gateway	Not selected (default)

  **Remote virtual network**	 

- Peering link name	ManufacturingVnet-to-CoreServicesVnet
- Virtual network deployment model	Resource manager
- I know my resource ID	Not selected
- Subscription	your subscription
- Virtual network	ManufacturingVnet
- Allow ManufacturingVnet to access CoreServicesVnet	selected (default)
- Allow ManufacturingVnet to receive forwarded traffic from CoreServicesVnet	selected
- Allow gateway in CoreServicesVnet to forward traffic to the peered virtual network	Not selected (default)
- Enable ManufacturingVnet to use CoreServicesVnet’s remote gateway	Not selected (default)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/405ce6f9-2bfd-49f8-ab28-82f650c4876c)

1. Review your settings and select Add.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8c77f2bd-9e4f-413f-9174-ab6b94cc8c60)

2. In CoreServicesVnet	Peerings, verify that the CoreServicesVnet-to-ManufacturingVnet peering is listed. Refresh the page to ensure the Peering status is Connected.
  
3. Switch to the ManufacturingVnet and verify the ManufacturingVnet-to-CoreServicesVnet peering is listed. Ensure the Peering status is Connected. You may need to Refresh the page.

# Task 5: Use Azure PowerShell to test the connection between virtual machines

- In this task, you retest the connection between the virtual machines in different virtual networks.

- **Verify the private IP address of the CoreServicesVM**
  
1. From the Azure portal, search for and select the CoreServicesVM virtual machine.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/962fd96c-a8e0-4903-b0d0-f480f8f7de61)

2. On the Overview blade, in the Networking section, record the Private IP address of the machine. You need this information to test the connection.

**Test the connection to the CoreServicesVM from the ManufacturingVM.**

1. Switch to the ManufacturingVM virtual machine.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b3c84e06-ce16-41f8-94b4-9db51556cda4)

2. In the Operations blade, select the Run command blade.

3. Select RunPowerShellScript and run the Test-NetConnection command. Be sure to use the private IP address of the CoreServicesVM.

 **Test-NetConnection <CoreServicesVM private IP address> -port 3389**
 
4. It may take a couple of minutes for the script to time out. The top of the page shows an informational message Script execution in progress.

5. The test connection should succeed because peering has been configured. Your computer name and remote address in this graphic may be different.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/536b1040-08b2-4cff-9d2e-3cfcd195427d)
