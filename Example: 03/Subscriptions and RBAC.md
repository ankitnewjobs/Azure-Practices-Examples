# Manage Subscriptions and RBAC

# Lab introduction

- In this lab, you learn about role-based access control. You learn how to use permissions and scopes to control what actions identities can and cannot perform. You also learn how to make subscription management easier using management groups.

# Lab scenario

- To simplify the management of Azure resources in your organization, you have been tasked with implementing the following functionality

- Creating a management group that includes all your Azure subscriptions.

- Granting permissions to submit support requests for all subscriptions in the management group. The permissions should be limited only to Create and manage virtual machines

- Create support request tickets (do not include adding Azure providers)

  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3e2d35cf-70ab-4315-80d8-32418329cf5d)

  # Task 1: Implement Management Groups
  
- In this task, you will create and configure management groups. 

- Management groups are used to logically organize subscriptions. Subscriptions should be segmented and allow for RBAC and Azure Policy to be assigned and inherited by other management groups and subscriptions.

# Sign in to the Azure portal - https://portal.azure.com.

Search for and select Microsoft Entra ID.

In the Manage blade, select Properties.

Review the Access management for the Azure resources area. Ensure you can manage access to all Azure subscriptions and management groups in the tenant.

Search for and select Management groups.

On the Management groups blade, click + Create.

Create a management group with the following settings. Select Submit when you are done.

# Setting	Value

Management group ID	az104-mg1 (must be unique in the directory)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4a37a790-b728-439c-afe2-4b0ec4deea66)

Management group display name	az104-mg1

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/79a8a4fc-f487-471b-8066-63f18c6918c1)

Refresh the management group page to ensure your new management group displays. This may take a minute

# Task 2: Create a custom RBAC role

- In this task, you will create a custom RBAC role. Custom roles are a core part of implementing the principle of least privilege for an environment. Built-in roles might have too many permissions for your scenario. In this task, we will create a new role and remove permissions that are not necessary.

1. Continue working on your management group. In the Access Control (IAM) blade, select the Check Access tab.

2. In the Create a custom role box, select Add.

3. On the Basics tab complete the configuration.

# Setting	Value
Custom role name	Custom Support Request
Description	``A custom contributor role for support requests.`

4. For Baseline permissions, select Clone a role. In the Role to Clone drop-down menu, select Support Request Contributor.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/01cee936-90cc-46a5-b382-dcded9c9faec)

5. Select Next to move to the Permissions tab, and then select + Exclude permissions.

6. In the resource provider search field, enter . Support and select Microsoft.Support.

7. In the list of permissions, place a checkbox next to Other: Registers Support Resource Provider and then select Add. The role should be updated to include this permission as a NotAction.

8. On the Assignable scopes tab, ensure your management group is listed, then click Next.

9. Review the JSON for the Actions, NotActions, and AssignableScopes that are customized in the role.

10. Select Review + Create, and then select Create.

# Task 4: Monitor role assignments with the Activity Log
In this task, you view the activity log to determine if anyone has created a new role.

1. In the portal locate the az104-mg1 resource and select Activity log. The activity log provides insight into subscription-level events.

2. Review the activities for role assignments. The activity log can be filtered for specific operations.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0ddd1ef3-ec9f-49d9-850b-3562b415ac76)

# Key takeaways

- Management groups are used to logically organize subscriptions.

- The built-in root management group includes all the management groups and subscriptions.

- Azure has many built-in roles. You can assign these roles to control access to resources.

- You can create new roles or customize existing roles.

- Roles are defined in a JSON formatted file and include Actions, NotActions, and AssignableScopes.

- You can use the Activity Log to monitor role assignments.








