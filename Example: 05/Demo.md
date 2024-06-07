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

- In this task, you create the ManufacturingVnet virtual network and associated subnets. The organization anticipates growth for the manufacturing offices so the subnets are sized for the expected growth. For this task, you use a template to create the resources.

1. Locate the template.json file exported in the previous task. It should be in your Downloads folder.

2. Edit the file using the editor of your choice. Many editors have a change all occurrences feature. If you are using Visual Studio Code be sure you are working in a trusted window and not in the restricted mode. Consult the architecture diagram to verify the details


# Make changes to the ManufacturingVnet virtual network

1. Replace all occurrences of CoreServicesVnet with ManufacturingVnet.
   
 ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d8f8762a-dc6a-47dd-a892-904af9306d4f)

2. Replace all occurrences of 10.20.0.0 with 10.30.0.0.

   ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/555ad5f6-05c8-4f31-a074-6f6b400fd78f)

# Make changes for the ManufacturingVnet subnets

1. Change all occurrences of SharedServicesSubnet to SensorSubnet1.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4dcec292-3607-4e9f-a051-8a52a3e52563)

2. Change all occurrences of 10.20.10.0/24 to 10.30.20.0/24.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1d04aeb4-56ac-4f53-8e50-0b3e52b5dca4)

3. Change all occurrences of DatabaseSubnet to SensorSubnet2.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/5952275c-035a-45e7-ac9f-b744d6327ecb)

4. Change all occurrences of 10.20.20.0/24 to 10.30.21.0/24.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1c3e3fad-24e0-4cea-b30f-b8ec32666807)

5. Read back through the file and ensure everything looks correct.

6. Be sure to Save your changes.

# Make changes to the parameters file

1. Locate the parameters.json file exported in the previous task. It should be in your Downloads folder.

2. Edit the file using the editor of your choice.

3. Replace the one occurrence of CoreServicesVnet with ManufacturingVnet.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/18e1d140-6fba-4d63-9d9b-341d9de9bb7e)

4. Save your changes.

# Deploy the custom template

1. In the portal, search for and select Deploy a custom template.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f7eece6e-08ff-4041-885e-138be794a4e0)

2. Select Build your template in the editor and then Load file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e24d4c1b-c0bb-4161-81cb-bddf00eea2bf)

3. Select the templates.json file with your Manufacturing changes, then select Save.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ed278f80-490f-4a1e-8adb-fda99e1639a7)

4. Select Review + Create and then Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/bb07cc35-0f1b-483a-866c-529cdb1fc013)

5. Wait for the template to deploy, then confirm (in the portal) that the Manufacturing virtual network and subnets were created.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b19b2d1f-c8b8-4797-86b4-52a0f63a833a)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/57d2b8d3-f248-4b09-86d1-3ef683521ac5)

# Task 3: Create and configure communication between an Application Security Group and a Network Security Group
