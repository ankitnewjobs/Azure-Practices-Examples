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




- 
