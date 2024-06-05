# Lab scenario
Your organization is building a new lab environment for pre-production testing of apps and services. A few engineers are being hired to manage the lab environment, including the virtual machines. To allow the engineers to authenticate by using Microsoft Entra ID, you have been tasked with provisioning users and groups. To minimize administrative overhead, membership of the groups should be updated automatically based on job titles.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c70f3c5a-b994-4e95-8166-17d2f5d31b50)


# Job skills
Task 1: Create and configure user accounts.
Task 2: Create groups and add members.

# Task 1: Create and configure user accounts.

1. Sign in to the Azure portal - https://portal.azure.com.

2. Search for and select Microsoft Entra ID. Microsoft Entra ID is Azure’s cloud-based identity and access management solution.

3. Select the Overview blade and then the Manage Tenants tab.

4. Return to the Entra ID page and select Licenses. From here you can purchase a license, manage the licenses you have, and assign licenses to users and groups. Select Licensed features to see what is available.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1177f278-af50-49de-9d7a-8fc79785525b)



# Create a new user

1. Select Users, then in the New user drop-down select Create new user.

2.  Create a new user with the following settings (leave others with their defaults). On the Properties tab notice all the different types of information that can be included in the user account.

# Setting	Value
User principal name: az104-user1
Display name:	az104-user1
Auto-generate password: Checked
Account enabled:	checked

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c1899c61-757a-4d44-9c86-8142c96e9b67)

Job title (Properties tab):	IT Lab Administrator
Department (Properties tab):	IT
Usage location (Properties tab):	Australia

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ecfd903a-7344-48c0-aa94-e762df5151a5

3. Once you have finished reviewing, select Review + Create and then Create.

4. Refresh the page and confirm your new user was created.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/df9a11f1-1b3a-4ad3-9ae3-ba0003f0ae54)


# Invite an external user
- In the New user drop-down select Invite an external user.

1. Setting	Value
2. Email	your email address
3. Display name	your name
4. Send an invite message	and check the box
5. Message	Welcome to Azure and our group project

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/874db04b-dc92-48ac-a223-ed20bb00dd3f)

- Move to the Properties tab. Complete the basic information, including these fields.

- Setting	Value
Job title:	IT Lab Administrator
Department:	IT
Usage location (Properties tab):	Australia

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d12a34c6-92bf-4e0f-9b97-b7e36dff98da)

- Select Review + Invite, and then Invite.

- Refresh the page and confirm the invited user was created. You should receive the invitation email shortly.

  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0f76d2f6-0f5e-4e25-bcae-19a88447f607)



# Task 2: Create groups and add members

In this task, you create a group account. Group accounts can include user accounts or devices. These are two basic ways members are assigned to groups: Statically and Dynamically. Static groups require administrators to add and remove members manually. Dynamic groups update automatically based on the properties of a user account or device.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d1b709e6-9500-44dd-85dd-59a46e68d2dd)

# In the Azure portal, search for and select Groups.

- Take a minute to familiarize yourself with the group settings in the left pane.

- Expiration lets you configure a group lifetime in days. After that time the group must be renewed by the owner.
- Naming policy lets you configure blocked words and add a prefix or suffix to group names.
  
![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a235e42e-a886-41ec-bb51-a632ad8713a5)

In the All Groups Blade, select + New group and create a new group.

Setting	Value
Group type	Security
Group name	IT Lab Administrators
Group description	Administrators that manage the IT lab
Membership type	Assigned

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/84b27aef-344a-44ed-b4b2-1c98f3307e5d)

- Select No owners selected.

- In the Add Owners page, search for and select yourself as the owner. Notice you can have more than one owner.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e39faf3e-e678-455f-b2e0-1cdf48c70d85)

- Select No members selected.

- In the Add members pane, search for and select the az104-user1 and the guest user you invited. Add both of the users to the group.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/32b6409b-bc02-4317-8452-264361a6df3b)


- Select Create to deploy the group.


- Refresh the page and ensure your group was created.

- Select the new group and review the Members and Owners information.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e89c3449-b96f-49b5-a89c-243270387168)


# Key takeaways

A tenant represents your organization and helps you to manage a specific instance of Microsoft Cloud services for your internal and external users.
Microsoft Entra ID has user and guest accounts. Each account has a level of access specific to the scope of work expected to be done.
Groups combine together related users or devices. There are two types of groups including Security and Microsoft 365.
Group membership can be statically or dynamically assigned.







   






