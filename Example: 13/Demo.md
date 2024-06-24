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

