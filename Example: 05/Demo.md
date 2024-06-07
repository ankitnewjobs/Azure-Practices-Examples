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

In this task, we create an Application Security Group and a Network Security Group. The NSG will have an inbound security rule that allows traffic from the ASG. The NSG will also have an outbound rule that denies access to the internet.

1. In the Azure portal, search for and select Application security groups.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6f65f27b-bf56-4926-bce3-ef61a4213268)

2. Click Create and provide the basic information.

- Setting	Value
Subscription	your subscription
Resource group	az104-rg4
Name	asg-web
Region	East US

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2160caac-0669-40d5-82a9-c29bbcf39a52)

3. Click Review + Create and then after the validation click Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3d0e1c9e-4d03-44d4-b8ab-3db48198a976)

# Create the Network Security Group and associate it with the ASG subnet

1. In the Azure portal, search for and select Network security groups.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/34f84609-7baa-49c5-845d-318e59dbe1df)

2. Select + Create and provide information on the Basics tab.

- Setting	Value
- 
Subscription	your subscription
Resource group	az104-rg4
Name	myNSGSecure
Region	East US

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/834d3b46-7e96-4ae0-af4e-e23195679cf4)

3. Click Review + Create and then after the validation click Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ba0b0b2a-81ab-4480-bc0f-1433fd8b04b1)

4. After the NSG is deployed, click Go to the resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0957bed4-413c-4ecf-a5a0-9bc32a8af101)

5. Under Settings click Subnets and then Associate.

- Setting	Value

Virtual network	CoreServicesVnet (az104-rg4)
Subnet	SharedServicesSubnet
Click OK to save the association.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/bd42d827-7b2d-40f0-8a83-6c959a273767)

6. Click OK to save the association.
   
![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f489e3a3-f640-4e83-9867-7f73b5168b32)

# Configure an inbound security rule to allow ASG traffic

1. Continue working with your NSG. In the Settings area, select Inbound security rules.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ec4bcb06-245e-4996-ae37-673441ee8307)

2. Review the default inbound rules. Notice that only other virtual networks and load balancers are allowed access.

3. Select + Add.

4. On the Add inbound security rule blade, use the following information to add an inbound port rule. This rule allows ASG traffic. When you are finished, select Add.

- Setting	Value

Source	Application security group
Source application security groups	asg-web
Source port ranges	*
Destination	Any
Service	Custom (notice your other choices)
Destination port ranges	80,443
Protocol	TCP
Action	Allow
Priority	100
Name	AllowASG

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6f2c5c10-2ddb-4733-84e7-b824ee4c2d70)

# Configure an outbound NSG rule that denies Internet access

1. After creating your inbound NSG rule, select Outbound security rules.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/08afaceb-5f69-42b4-b8b7-f64c1c61eb1e)

2. Notice the AllowInternetOutboundRule rule. Also, notice the rule cannot be deleted and the priority is 65001.

3. Select + Add and then configure an outbound rule that denies access to the internet. When you are finished, select Add.

Setting	Value
Source	Any
Source port ranges	*
Destination	Service tag
Destination service tag	Internet
Service	Custom
Destination port ranges	8080
Protocol	Any
Action	Deny
Priority	4096
Name		DenyAnyCustom8080Outbound

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7431514d-8a15-4a14-a85d-674c9070d9ec)

# Task 4: Configure public and private Azure DNS zones

In this task, you will create and configure public and private DNS zones.

# Configure a public DNS zone

You can configure Azure DNS to resolve host names in your public domain. For example, if you purchased the contoso.xyz domain name from a domain name registrar, you can configure Azure DNS to host the contoso.com domain and resolve www.contoso.xyz to the IP address of your web server or web app.

1. In the portal, search for and select DNS zones.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9b6af4b8-85c4-4d37-87b8-e66a387641be)

2. Select + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/40727a29-5a76-447c-adce-b8fc783a8914)

3. Configure the Basics tab.

Property	Value
Subscription	Select your subscription
Resource group	az-104-rg4
Name	contoso2.com (if reserved adjust the name)

4. Select Review Create and then Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ce378227-93a9-4ca2-8c9c-deab1c296bb7)

5. Wait for the DNS zone to deploy and then select Go to resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d493d256-0080-4d82-96b6-aee26efd01ee)

6. On the Overview blade notice the names of the four Azure DNS name servers assigned to the zone. Copy one of the name server addresses. You will need it in a future step.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2ce9ece3-24ff-4a78-9d5d-278dd39374e5)

7. Select + Record set. You add a virtual network link record for each virtual network that needs private name-resolution support.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/eb78dcfc-304e-4d89-b1bf-88e1bb97da99)

Property	Value
Name	www
Type	A
TTL	1
IP address	10.1.1.4

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1b5a634e-ac27-48b2-9d9b-85b1b25b7977)

8. Select OK and verify that contoso2.com has an A record set named www.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/dc048ddb-0808-4a37-b9d4-263555c25138)

Open a command prompt, and run the following command:

Shell nslookup www.contoso.com <name server name>

1. Verify the hostname www.contoso.com resolves to the IP address you provided. This confirms name resolution is working correctly.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/666e6514-0222-4aa2-9fb3-195d5aed16e7)

# Configure a private DNS zone

A private DNS zone provides name resolution services within virtual networks. A private DNS zone is only accessible from the virtual networks that it is linked to and can’t be accessed from the internet.

1. In the portal, search for and select Private DNS zones.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3adc0ad5-5efc-48da-8693-019e49f5e36e)

2. Select + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/87df00e9-f9fc-462c-8644-4060bd3129a4)

3. On the Basics tab of Create private DNS zone, enter the information as listed in the table below:

- Property	Value
  
Subscription	Select your subscription
Resource group	az-104-rg4
Name	private.contoso.com (adjust if you had to rename)
Region	East US

4. Select Review Create and then Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/23b4175c-ec1c-4674-9def-f38443876c10)

5. Wait for the DNS zone to deploy and then select Go to resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0cb715c8-02f4-40b2-a035-8bba91b2a214)

6. Notice on the Overview blade there are no name server records.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1619dd5b-d6a5-4cc7-b2f6-cacd918dd9d1)

7. Select + Virtual network links and then select + Add.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8a3d9647-9a56-41ff-9807-275da97247e9)

Property	Value
Link name	manufacturing-link
Virtual network	ManufacturingVnet

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a1367791-d734-4b5a-b1af-9ad12e586a33)

8. Select OK and wait for the link to create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8041559d-5d78-4a33-ac2b-2d838d99af46)

9. From the Overview blade select + Record set. You would now add a record for each virtual machine that needs private name-resolution support.

Property	Value
Name	sensorvm
Type	A
TTL	1
IP address	10.1.1.4

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b039e558-2df6-4ac5-9974-6577e9d561aa)

# Cleanup your resources
If you are working with your subscription take a minute to delete the lab resources. This will ensure resources are freed up and cost is minimized. The easiest way to delete the lab resources is to delete the lab resource group.

- In the Azure portal, select the resource group, select Delete the resource group, Enter the resource group name, and then click Delete.
- Using Azure PowerShell, Remove-AzResourceGroup -Name resourceGroupName.
- Using the CLI, az group delete --name resourceGroupName.
