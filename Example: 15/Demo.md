# Implement Monitoring

# Lab introduction

- In this lab, you learn about Azure Monitor. You learn to create an alert and send it to an action group. You trigger and test the alert and check the activity log.

# Lab scenario

- Your organization has migrated their infrastructure to Azure. It is important that Administrators are notified of any significant infrastructure changes. You plan to examine the capabilities of Azure Monitor, including Log Analytics.

# Architecture diagram

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ae084bae-c413-489a-85c1-79bf25c59162)

# Job skills

Task 1: Use a template to provision an infrastructure.

Task 2: Create an alert.

Task 3: Configure action group notifications.

Task 4: Trigger an alert and confirm it is working.

Task 5: Configure an alert processing rule.

Task 6: Use Azure Monitor log queries.

# Task 1: Use a template to provision an infrastructure

- In this task, you will deploy a virtual machine that will be used to test monitoring scenarios.

1. Download the \Allfiles\Lab11\az104-11-vm-template.json lab files to your computer.

2. Sign in to the Azure portal - https://portal.azure.com.

3. From the Azure portal, search for and select Deploy a custom template.

4. On the custom deployment page, select Build you own template in the editor.

5. On the edit template page, select Load file.

6. Locate and select the \Allfiles\Labs11\az104-11-vm-template.json file and select Open.

7. Select Save.

8. Use the following information to complete the custom deployment fields, leaving all other fields with their default values:

- Setting	Value

- Subscription	Your Azure subscription

- Resource group	az104-rg15 (If necessary, select Create new)

- Region	East US

- Username	As Per Your Choice

- Password	Provide a complex password

9. Select Review + Create, then select Create.

10. Wait for the deployment to finish, then click Go to resource group.

11. Review what resources were deployed. There should be one virtual network with one virtual machine.

# Configure Azure Monitor for virtual machines (this will be used in the last task)

1. In the portal, search for and select Monitor.

2. Take a minute to review all the insights, detection, triage, and diagnosis tools that are available.

3. Select View in the VM Insights box, and then select Configure Insights.

4. Select your virtual machine, and then Enable (twice).

5. Take the defaults for subscription and data collection rules, then select Configure.

6. It will take a few minutes for the virtual machine agent to install and configure, proceed to the next step.
