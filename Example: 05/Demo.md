# Lab scenario

- Your global organization plans to implement virtual networks. The immediate goal is to accommodate all the existing resources. However, the organization is in a growth phase and wants to ensure additional capacity for growth.

- The **CoreServicesVnet** virtual network has the largest number of resources. A large amount of growth is anticipated, so a large address space is necessary for this virtual network.

- The **ManufacturingVnet** virtual network contains systems for the operations of the manufacturing facilities. The organization anticipates many internally connected devices from which their systems can retrieve data.

Secure network traffic. Create a virtual machine, a virtual network, and a network security group. Add network security group rules to allow and disallow traffic.

Create a simple virtual network. Create a virtual network with two virtual machines. Demonstrate the virtual machines can communicate.

Design and implement a virtual network in Azure. Create a resource group and create virtual networks with subnets.

Implement virtual networking. Create and configure a virtual network, deploy virtual machines, configure network security groups, and configure Azure DNS.

# Architecture diagram

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/94919e3b-ac6e-4d95-9391-037f3c49470e)

# Task 1: Create a virtual network with subnets using the portal

1. Sign in to the Azure portal - https://portal.azure.com.

2.  Search for and select Virtual Networks.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c31baa3c-e85b-4c8f-b713-1c948628cc6e)

3. Select Create on the Virtual Networks page.

  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0f162bb1-0360-4088-9dcb-6888c86e02ca)


4. Complete the Basics tab for the CoreServicesVnet.

Option	Value

Resource Group	az104-rg4 (if necessary, create new)
Name	CoreServicesVnet
Region	(US) East US

5. Move to the IP Addresses tab.

- Option	Value

- IPv4 address space	10.20.0.0/16 (separate the entries)

6. Select + Add a subnet. Complete the name and address information for each subnet. Be sure to select Add for each new subnet.

- Subnet	Option	Value
  
- SharedServicesSubnet	Subnet name	SharedServicesSubnet
 	Starting Address	10.20.10.0
 	Size	/24
  
- DatabaseSubnet	Subnet name	DatabaseSubnet
 	Starting Address	10.20.20.0
 	Size	/24

7. To finish creating the CoreServicesVnet and its associated subnets, select Review + create.

8. Verify your configuration passed validation, and then select Create.

9. Wait for the virtual network to deploy and then select Go to resource.
    
![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6ee43707-4537-41da-85ac-82e4040d45d7)

10. Take a minute to verify the Address space and the Subnets. Notice your other choices in the Settings blade.

11. In the Automation section, select the Export template, and then wait for the template to be generated.
  
  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/08636c53-cb23-460b-af67-8b83528a1a56)

12. Download the template.
   #  template.json
   
![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6c6ac692-26c6-4c4a-bb40-d03f84b9f3ff)

# parameters.json

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/701afd30-f41c-4c06-bc99-21961bd138ba)

13. Navigate on the local machine to the Downloads folder and Extract all the files in the downloaded zip file.
  
  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3806632b-f68f-4fe6-a1a7-cba5bec20ec2)


14. Before proceeding, ensure you have the template.json file. You will use this template to create the ManufacturingVnet in the next task.

# Task 2: Create a virtual network and subnets using a template
