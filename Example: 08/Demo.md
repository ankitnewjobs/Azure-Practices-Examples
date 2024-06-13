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
- Username	local admin
- Password	Provide a complex password
- Public inbound ports	None

- 
