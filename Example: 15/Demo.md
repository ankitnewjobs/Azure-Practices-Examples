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

# Task 2: Create an alert

- In this task, you create an alert for when a virtual machine is deleted.

1. Continue on the Monitor page , select Alerts.

2. Select Create + and select Alert rule.

3. Select the box for the resource group, then select Apply. This alert will apply to any virtual machines in the resource group. Alternatively, you could just specify one particular machine.

4. Select the Condition tab and then select the See all signals link.

5. Search for and select Delete Virtual Machine (Virtual Machines). Notice the other built-in signals. Select Apply

6. In the Alert logic area (scroll down), review the Event level selections. Leave the default of All selected.

7. Review the Status selections. Leave the default of All selected.

8. Leave the Create an alert rule pane open for the next task.

# Task 3: Configure action group notifications

- In this task, if the alert is triggered send an email notification to the operations team.

1. Continue working on your alert. Select Next: Actions, and then select Create action group.

