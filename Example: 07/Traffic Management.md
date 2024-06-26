# Implement Traffic Management

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

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8ee33d5a-0aa3-46cb-bc0b-fe526c780cec)

4. On the custom deployment page, select Build your template in the editor.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b00faea3-e4fe-45a2-8488-edac8abffc2d)

5. On the edit template page, select Load file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8c84fb25-7133-4bf9-8ad6-be728045d7e4)

6. Locate and select the \Allfiles\Lab06\az104-06-vms-template.json file and select Open.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c3af3489-1714-4801-9d49-b0bdcc52fea0)

7. Select Save.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4cb7d6d7-2035-4e71-80e3-ec1d839dc3d8)

8. Select Edit parameters and load the \Allfiles\Lab06\az104-06-vms-parameters.json file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d9326c3e-3321-4298-ae0d-50a176b3f534)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4d72f3e7-0f77-410e-9157-0f3ad304c79f)

9. Select Save.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/14d83cbf-e52e-481a-b7c2-30618b67b96e)

10. Use the following information to complete the fields on the custom deployment page, leaving all other fields with the default value.

**- Setting	Value**

- Subscription	your Azure subscription

- Resource group	az104-rg7 (If necessary, select Create new)

- Password	Provide a secure password

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d9b59f70-4441-4b61-8ac5-5e653c5d5631)

11. Select Review + Create and then select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ffeaa2ad-1027-4e72-a40b-9edff89e0fab)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d402faa2-10ff-4531-a39c-227977cf5cfa)

# Task 2: Configure an Azure Load Balancer

- In this task, you implement an Azure Load Balancer in front of the two Azure virtual machines in the virtual network. Load Balancers in Azure provide layer 4 connectivity across resources, such as virtual machines. Load Balancer configuration includes a front-end IP address to accept connections, a backend pool, and rules that define how connections should traverse the load balancer.

# Architecture diagram - Load Balancer

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/59a0875d-de1d-4e86-acc9-f5d795e6b969)

1. In the Azure portal, search for and select Load balancers and, on the Load balancers blade, click + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9ea1b2d8-2003-4310-818b-9a8738936dbe)

2. Create a load balancer with the following settings (leave others with their default values) then click Next: Frontend IP configuration:

**- Setting	Value**

- Subscription	your Azure subscription
- Resource group	az104-rg7
- Name	az104-lb
- Region	The same region in which you deployed the VMs
- SKU	Standard
- Type	Public
- Tier	Regional

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e65cbb46-2acc-4c25-972a-753c67cc91b5)

3. On the Frontend IP configuration tab, click Add a frontend IP configuration and use the following settings:

**- Setting	Value**

- Name	az104-fe
- IP type	IP address
- Gateway Load Balancer	None
- Public IP address	Select Create new (use the instructions in the next step)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/988750b4-4f33-4bdf-a554-0e304581fd5b)

4. On the Add a Public IP address popup, use the following settings before clicking OK and then Add. When completed click Next: Backend pools.

**- Setting	Value**

- Name	az104-lbpip
- SKU	Standard
- Tier	Regional
- Assignment	Static
- Routing Preference	Microsoft network

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/925ac913-4a23-4f0e-96f8-6a05216a8adc)

5. On the Backend Pools tab, click Add a Backend Pool with the following settings (leave others with their default values). Click + Add (twice) and then click Next: Inbound rules.

**- Setting	Value**

- Name	az104-be
  
- Virtual network	az104-06-vnet1
  
- Backend Pool Configuration	NIC

- Click Add to add a virtual machine	 

- az104-06-vm0	check the box

- az104-06-vm1	check the box

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/06d5743d-39e3-41f0-a171-9e87f4898d56)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4f0161d5-dbda-4fda-bab4-c97fd89e048c)

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

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3e459d13-1e52-4c11-8f09-d17e087dc6db)

- Session persistence	None

- Idle timeout (minutes)	4

- TCP reset	Disabled

- Floating IP	Disabled

- Outbound source network address translation (SNAT)	Recommended

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8012fea7-1368-4828-9b70-716e2948b5c6)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e676dbec-ecb3-4677-b5e1-612da362cff2)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6000cbf4-036f-4ed4-9093-cb57a0391c6a)

3. Select Frontend IP configuration from the Load Balancer page. Copy the public IP address.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/91689e2c-178b-4d33-9222-a23c1bd6396d)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/92e8fb3a-ae39-4672-be06-7a7ef8d2a2e2)

4. Open another browser tab and navigate to the IP address. Verify that the browser window displays the message Hello World from az104-06-vm0 or Hello World from az104-06-vm1.

5. Refresh the window to verify the message changes to the other virtual machine. This demonstrates the load balancer rotating through the virtual machines.

# Task 3: Configure an Azure Application Gateway

- In this task, you implement an Azure Application Gateway in front of two Azure virtual machines. An Application Gateway provides layer 7 load balancing, Web Application Firewall (WAF), SSL termination, and end-to-end encryption to the resources defined in the backend pool. The Application Gateway routes images to one virtual machine and videos to the other virtual machine.

# Architecture diagram - Application Gateway

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d60a01c3-a17c-4c98-9e34-61488c6e0341)

1. In the Azure portal, search and select Virtual networks.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1076d820-6eb9-4eb0-9a0c-7b6d7e198913)

2. On the Virtual networks blade, in the list of virtual networks, click az104-06-vnet1.

3. On the az104-06-vnet1 virtual network blade, in the Settings section, click Subnets, and then click + Subnet.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4545dec8-718c-4936-9256-9024ff79b328)

4. Add a subnet with the following settings (leave others with their default values).

**- Setting	Value**

- Name	subnet-appgw

- Subnet address range	10.60.3.224/27

- Click Save

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/11762ebc-327e-4673-b3fb-7e9f54449d9e)

6. In the Azure portal, search and select Application Gateways, and, on the Application Gateways blade, click + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/04f20ba3-06af-4e1b-856a-0ab5bf5e9352)

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

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a2abf39e-d9fc-4d7e-8ab6-39d676453ce9)

8. Click Next: Frontends > and specify the following settings (leave others with their default values). When complete, click OK.

**- Setting	Value**

- Frontend IP address type	Public

- Public IP address	Add new

- Name	az104-gwpip

- Availability zone	None

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4857aaa9-2751-4c7c-9fe4-e5f5a5fb562e)

9. Click Next: Backends > and then Add a backend pool. Specify the following settings (leave others with their default values). When completed click Add.

**- Setting	Value**

- Name	az104-appgwbe

- Add backend pool without targets	No

- Virtual machine	az104-rg6-nic1 (10.60.1.4)

- Virtual machine	az104-rg6-nic2 (10.60.2.4)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/68682c6c-033b-4cd2-ad0c-70342625c2c7)

10. Click Add a backend pool. This is the backend pool for images. Specify the following settings (leave others with their default values). When completed click Add.

**- Setting	Value**
- Name	az104-imagebe

-  Add backend pool without targets	No

- Virtual machine	az104-rg6-nic1 (10.60.1.4)

11. Click Add a backend pool. This is the backend pool for video. Specify the following settings (leave others with their default values). When completed click Add.

**- Setting	Value**
- Name	az104-videobe

- Add backend pool without targets	No

- Virtual machine	az104-rg6-nic2 (10.60.2.4)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e100b063-4870-4c57-9845-0919e09f8f7b)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2fc11b31-674d-42cd-ba99-088742f8bdf4)

12. Select Next: Configuration > and then Add a routing rule. Complete the information.

**- Setting	Value**

- Rule name	az104-gwrule

- Priority	10

- Listener name	az104-listener

- Frontend IP	Public IPv4

- Protocol	HTTP

- Port	80

- Listener type	Basic

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/04a3b7a6-3204-4737-ad2a-476737dcacda)

13. Move to the Backend targets tab. Select Add after completing the basic information.

**- Setting	Value**

- Backend target	az104-appgwbe

- Backend settings	az104-http (create new)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9c15ddd2-b849-4529-a4c0-54661ca7f000)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6f9165ba-b619-44e9-bcdc-3f9de92d81ca)

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

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/003ad287-7989-4243-a041-73c2ea159d5f)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4a6b2f10-6b02-4cbc-8b3a-f0337965094a)

17. After the application gateway deploys, search for and select az104-appgw.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/650d4807-1002-495e-9bd8-de626210600b)

18. In the Application Gateway resource, in the Monitoring section, select Backend Health.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/5fcafcaf-b3cc-4ed3-9b4a-b2772f20af59)

19. Ensure both servers in the backend pool display Healthy.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/90b6aa01-2fbd-4fea-b515-d557c5703877)

20. On the Overview blade, copy the value of the Frontend public IP address.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/480b9562-7fd5-4158-8e73-ba8cdebbe35a)

21. Start another browser window and test this URL - http://<frontend ip address>/image/.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/66538b4b-a275-4fc3-b285-661adf6abbc5)

22. Verify you are directed to the image server (vm1).

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/524a8dac-755e-40b9-bf8c-0a8e1eaee35b)

23. Start another browser window and test this URL - http://<frontend ip address>/video/.

24. Verify you are directed to the video server (vm2).

# Key takeaways

- Azure Load Balancer is an excellent choice for distributing network traffic across multiple virtual machines at the transport layer (OSI layer 4 - TCP and UDP).

- Public Load Balancers are used to load balance internet traffic to your VMs. An internal (or private) load balancer is used where private IPs are needed at the frontend only.

- The Basic load balancer is for small-scale applications that don’t need high availability or redundancy. The Standard load balancer is for high performance and ultra-low latency.

- Azure Application Gateway is a web traffic (OSI layer 7) load balancer that enables you to manage traffic to your web applications.

- The Application Gateway Standard tier offers all the L7 functionality, including load balancing, The WAF tier adds a firewall to check for malicious traffic.

- An Application Gateway can make routing decisions based on additional attributes of an HTTP request, for example URI path or host headers.
