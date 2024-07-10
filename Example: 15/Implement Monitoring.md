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

1. Download the https://github.com/ankitnewjobs/Azure-Implement--Monitoring template.json lab files to your computer.

2. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3a04030d-dfda-48a7-b3de-5a55ced7685b)

3. From the Azure portal, search for and select Deploy a custom template.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d3b70e99-83ac-4bc9-bcb1-c576d8f853fa)

4. On the custom deployment page, select Build you own template in the editor.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d2157837-fc87-41ad-8ee3-0fef66327595)

5. On the edit template page, select Load file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9829fc7c-44fb-4f7f-929d-dd4f9ad516dc)

6. Locate and select the template.json file and select Open.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d308a335-550d-4fc8-a0d4-15dfa5121da3)

7. Select Save.

8. Use the following information to complete the custom deployment fields, leaving all other fields with their default values:

- Setting	Value

- Subscription	Your Azure subscription

- Resource group	az104-rg15 (If necessary, select Create new)

- Region	East US

- Username	As Per Your Choice

- Password	Provide a complex password

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/407033ef-ca95-4c92-a322-60562a8e4802)

9. Select Review + Create, then select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ca66a911-84f8-4ab0-9f2e-954de320aa38)

10. Wait for the deployment to finish, then click Go to resource group.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ce20a786-b382-4489-8bd4-a9e121c1b914)

11. Review what resources were deployed. There should be one virtual network with one virtual machine.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3eee96a4-4fa3-4a22-bc3c-d7fabf9dd1b5)

# Configure Azure Monitor for virtual machines (this will be used in the last task)

1. In the portal, search for and select Monitor.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/66fb34e2-33c4-4db5-8523-565e2306ed4d)

2. Take a minute to review all the insights, detection, triage, and diagnosis tools that are available.

3. Select View in the VM Insights box, and then select Configure Insights.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/91cf8577-d4b1-4d45-815f-33fb6b7dae3f)

4. Select your virtual machine, and then Enable (twice).

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d434b9e5-e36e-4b90-a5de-c357ffca2e82)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2373f560-1b97-4f3f-b0e2-7c464b88b370)

5. Take the defaults for subscription and data collection rules, then select Configure.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c88a5621-fb6d-44dd-9869-e3b5da2acb8e)

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

2. On the Basics tab, enter the following values for each setting.

- Setting	Value

- Project details	 

- Subscription	your subscription

- Resource group	az104-rg11

- Region	Global (default)

- Instance details	 

- Action group name	Alert the operations team (must be unique in the resource group)

- Display name	AlertOpsTeam

3. Select Next: Notifications and enter the following values for each setting.

- Setting	Value

- Notification type	Select Email/SMS message/Push/Voice

- Name	VM was deleted

4. Select Email, and in the Email box, enter your email address, and then select OK.

5. Once the action group is created move to the Next: Details tab and enter the following values for each setting.

- Setting	Value

- Alert rule name	VM was deleted

- Alert rule description	A VM in your resource group was deleted

6. Select Review + create to validate your input, then select Create.

 # Task 4: Trigger an alert and confirm it is working

- In this task, you trigger the alert and confirm a notification is sent.

1. In the portal, search for and select Virtual machines.

2. Check the box for the az104-vm0 virtual machine.

3. Select Delete from the menu bar.

4. Check the box for Apply force delete. Enter delete to confirm and then select Delete.

5. In the title bar, select the Notifications icon and wait until vm0 is successfully deleted.

6. You should receive a notification email that reads, Important notice: Azure Monitor alert VM was deleted was activated… If not, open your email program and look for an email from azure-noreply@microsoft.com.

7. On the Azure portal resource menu, select Monitor, and then select Alerts in the menu on the left.

8. You should have three verbose alerts that were generated by deleting vm0.

9. Select the name of one of the alerts (For example, VM was deleted). An Alert details pane appears that shows more details about the event.

# Task 5: Configure an alert processing rule

- In this task, you create an alert rule to suppress notifications during a maintenance period.

1. Continue in the Alerts blade, select Alert processing rules and then + Create.

2. Select your resource group, then select Apply.

3. Select Next: Rule settings, then select Suppress notifications.

4. Select Next: Scheduling.

5. By default, the rule works all the time, unless you disable it or configure a schedule. You are going to define a rule to suppress notifications during overnight maintenance. Enter these settings for the scheduling of the alert processing rule:

- Setting	Value

- Apply the rule	At a specific time

- Start	Enter today’s date at 10 pm.

- End	Enter tomorrow’s date at 7 am.

- Time zone	Select the local timezone.

6. Select Next: Details and enter these settings:

- Setting	Value

- Resource group	az104-rg11

- Rule name	Planned Maintenance

- Description	Suppress notifications during planned maintenance.

- Select Review + create to validate your input, then select Create.

# Task 6: Use Azure Monitor log queries

-In this task, you will use Azure Monitor to query the data captured from the virtual machine.

1. In the Azure portal, search for and select Monitor blade, click Logs.

2. If necessary close the splash screen.

3. Select a scope, your resource group. Select Apply.

4. In the Queries tab, select Virtual machines (left pane).

5. Review the queries that are available. Run (hover over the query) the Count heartbeats query.

6. You should receive a heartbeat count for when the virtual machine was running.

7. Review the query. This query uses the heartbeat table.

8. Replace the query with this one, and then click Run. Review the resulting chart.

9. As you have time, review and run other queries.

# Key takeaways

- Alerts help you detect and address issues before users notice there might be a problem with your infrastructure or application.

- You can alert on any metric or log data source in the Azure Monitor data platform.

- An alert rule monitors your data and captures a signal that indicates something is happening on the specified resource.

- An alert is triggered if the conditions of the alert rule are met. Several actions (email, SMS, push, voice) can be triggered.

- Action groups include individuals that should be notified of an alert.
