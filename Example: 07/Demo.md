# Lab - Implement Traffic Management

# Lab introduction

- In this lab, you learn how to configure and test a public Load Balancer and an Application Gateway.

# Lab scenario

- Your organization has a public website. You need to load and balance incoming public requests across different virtual machines. You also need to provide images and videos from different virtual machines. You plan on implementing an Azure Load Balancer and an Azure Application Gateway. All resources are in the same region.

# Job skills

- Task 1: Use a template to provision an infrastructure.

- Task 2: Configure an Azure Load Balancer.

- Task 3: Configure an Azure Application Gateway.

# Task 1: Use a template to provision an infrastructure

- In this task, you will use a template to deploy one virtual network, one network security group, and two virtual machines.

1. Download the \Allfiles\Lab06 lab files (template and parameters).

2. Sign in to the Azure portal - https://portal.azure.com.

3. Search for and select Deploy a custom template.

4. On the custom deployment page, select Build your own template in the editor.

5. On the edit template page, select Load file.

6. Locate and select the \Allfiles\Lab06\az104-06-vms-template.json file and select Open.

7. Select Save.
   
8. Select Edit parameters and load the \Allfiles\Lab06\az104-06-vms-parameters.json file.

9. Select Save.

10. Use the following information to complete the fields on the custom deployment page, leaving all other fields with the default value.

**- Setting	Value**

- Subscription	your Azure subscription

- Resource group	az104-rg6 (If necessary, select Create new)

- Password	Provide a secure password

11. Select Review + Create and then select Create.

# Task 2: Configure an Azure Load Balancer

- In this task, you implement an Azure Load Balancer in front of the two Azure virtual machines in the virtual network. Load Balancers in Azure provide layer 4 connectivity across resources, such as virtual machines. Load Balancer configuration includes a front-end IP address to accept connections, a backend pool, and rules that define how connections should traverse the load balancer.

# Architecture diagram - Load Balancer

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/59a0875d-de1d-4e86-acc9-f5d795e6b969)

1. In the Azure portal, search for and select Load balancers and, on the Load balancers blade, click + Create.

2. Create a load balancer with the following settings (leave others with their default values) then click Next: Frontend IP configuration:

**- Setting	Value**

- Subscription	your Azure subscription
- Resource group	az104-rg6
- Name	az104-lb
- Region	The same region in which you deployed the VMs
- SKU	Standard
- Type	Public
- Tier	Regional

3. On the Frontend IP configuration tab, click Add a frontend IP configuration and use the following settings:

**- Setting	Value**

- Name	az104-fe
- IP type	IP address
- Gateway Load Balancer	None
- Public IP address	Select Create new (use the instructions in the next step)

4. On the Add a Public IP address popup, use the following settings before clicking OK and then Add. When completed click Next: Backend pools.

**- Setting	Value**

- Name	az104-lbpip
- SKU	Standard
- Tier	Regional
- Assignment	Static
- Routing Preference	Microsoft network

5. On the Backend Pools tab, click Add a Backend Pool with the following settings (leave others with their default values). Click + Add (twice) and then click Next: Inbound rules.

**- Setting	Value**

- Name	az104-be
  
- Virtual network	az104-06-vnet1
  
- Backend Pool Configuration	NIC

- Click Add to add a virtual machine	 

- az104-06-vm0	check the box

- az104-06-vm1	check the box

6. As you have time, review the other tabs, then click Review + Create. Ensure there are no validation errors, then click Create.

7. Wait for the load balancer to deploy then click Go to resource.

# Add a rule to determine how incoming traffic is distributed

1. In the Settings blade, select Load balancing rules.

2. Select + Add. Add a load balancing rule with the following settings (leave others with their default values). As you configure the rule use the informational icons to learn about each setting. When finished click Save.

**- Setting	Value**

- Name	az104-lbrule

- IP Version	IPv4

- Frontend IP Address	az104-fe

- Backend pool	az104-be

- Protocol	TCP

- Port	80

- Backend port	80

- Health probe	Create new

- Name	az104-hp

- Protocol	TCP

- Port	80

- Interval	5

- Close the Create health probe window	Save

- Session persistence	None

- Idle timeout (minutes)	4

- TCP reset	Disabled

- Floating IP	Disabled

- Outbound source network address translation (SNAT)	Recommended

3. Select Frontend IP configuration from the Load Balancer page. Copy the public IP address.

4. Open another browser tab and navigate to the IP address. Verify that the browser window displays the message Hello World from az104-06-vm0 or Hello World from az104-06-vm1.

5. Refresh the window to verify the message changes to the other virtual machine. This demonstrates the load balancer rotating through the virtual machines.

# Task 3: Configure an Azure Application Gateway

- In this task, you implement an Azure Application Gateway in front of two Azure virtual machines. An Application Gateway provides layer 7 load balancing, Web Application Firewall (WAF), SSL termination, and end-to-end encryption to the resources defined in the backend pool. The Application Gateway routes images to one virtual machine and videos to the other virtual machine.

# Architecture diagram - Application Gateway

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d60a01c3-a17c-4c98-9e34-61488c6e0341)

1. In the Azure portal, search and select Virtual networks.

2. On the Virtual networks blade, in the list of virtual networks, click az104-06-vnet1.

3. On the az104-06-vnet1 virtual network blade, in the Settings section, click Subnets, and then click + Subnet.

4. Add a subnet with the following settings (leave others with their default values).

**- Setting	Value**

- Name	subnet-appgw

- Subnet address range	10.60.3.224/27

- Click Save

6. In the Azure portal, search and select Application Gateways, and, on the Application Gateways blade, click + Create.

7. On the Basics tab, specify the following settings (leave others with their default values):

**- Setting	Value**

- Subscription	your Azure subscription

- Resource group	az104-rg6

- Application gateway name	az104-appgw

- Region	The same Azure region that you used in Task 1

- Tier	Standard V2

- Enable autoscaling	No

- Minimum instance count	2

- Availability zone	Zone 1

- HTTP2	Disabled

- Virtual network	az104-06-vnet1

- Subnet	subnet-appgw (10.60.3.224/27)

8. Click Next: Frontends > and specify the following settings (leave others with their default values). When complete, click OK.

**- Setting	Value**

- Frontend IP address type	Public

- Public IP address	Add new

- Name	az104-gwpip

- Availability zone	None

9. Click Next: Backends > and then Add a backend pool. Specify the following settings (leave others with their default values). When completed click Add.

**- Setting	Value**

- Name	az104-appgwbe

- Add backend pool without targets	No

- Virtual machine	az104-rg6-nic1 (10.60.1.4)

- Virtual machine	az104-rg6-nic2 (10.60.2.4)

10. Click Add a backend pool. This is the backend pool for images. Specify the following settings (leave others with their default values). When completed click Add.

**- Setting	Value**
- Name	az104-imagebe
-
-  Add backend pool without targets	No

- Virtual machine	az104-rg6-nic1 (10.60.1.4)

11. Click Add a backend pool. This is the backend pool for video. Specify the following settings (leave others with their default values). When completed click Add.

**- Setting	Value**
- Name	az104-videobe

- Add backend pool without targets	No

- Virtual machine	az104-rg6-nic2 (10.60.2.4)

12. Select Next: Configuration > and then Add a routing rule. Complete the information.

**- Setting	Value**

- Rule name	az104-gwrule

- Priority	10

- Listener name	az104-listener

- Frontend IP	Public IPv4

- Protocol	HTTP

- Port	80

- Listener type	Basic

13. Move to the Backend targets tab. Select Add after completing the basic information.

**- Setting	Value**

- Backend target	az104-appgwbe

- Backend settings	az104-http (create new)

14. In the Path-based routing section, select Add multiple targets to create a path-based rule. You will create two rules. Click Add after the first rule and then Add after the second rule.

**Rule - routing to the image backend**

**- Setting	Value**

- Path	/image/*

- Target name	images

- Backend settings	az104-http

- Backend target	az104-imagebe

**Rule - routing to the video backend**

**- Setting	Value**

- Path	/video/*

- Target name	videos

- Backend settings	az104-http

- Backend target	az104-videobe

15. Be sure to Save and check your changes, then select Next: Tags >. No changes are needed.

16. Select Next: Review + create > and then click Create.

17. After the application gateway deploys, search for and select az104-appgw.

18. In the Application Gateway resource, in the Monitoring section, select Backend Health.

19. Ensure both servers in the backend pool display Healthy.

20. On the Overview blade, copy the value of the Frontend public IP address.

21. Start another browser window and test this URL - http://<frontend ip address>/image/.

22. Verify you are directed to the image server (vm1).

23. Start another browser window and test this URL - http://<frontend ip address>/video/.

24. Verify you are directed to the video server (vm2).
