# Implement Web Apps

# Lab introduction

- In this lab, you learn about Azure web apps. You learn to configure a web app to display a Hello World application in an external GitHub repository. You learn to create a staging slot and swap with the production slot. You also learn about autoscaling to accommodate demand changes.

# Lab scenario

- Your organization is interested in Azure Web apps for hosting your company's websites. The websites are currently hosted in an on-premises data center. The websites are running on Windows servers using the PHP runtime stack. The hardware is nearing end-of-life and will soon need to be replaced. Your organization wants to avoid new hardware costs by using Azure to host the websites.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1371e0ac-60e4-46d6-b0c2-8cf0821787bf)

# Job skills

- Task 1: Create and configure an Azure web app.

- Task 2: Create and configure a deployment slot.

- Task 3: Configure web app deployment settings.

- Task 4: Swap deployment slots.

- Task 5: Configure and test autoscaling of the Azure web app.

# Task 1: Create and configure an Azure web app

- In this task, you create an Azure web app. Azure App Services is a Platform As a Service (PAAS) solution for web, mobile, and other web-based applications. Azure web apps are part of Azure App Services hosting most runtime environments, such as PHP, Java, and . NET. The app service plan that you select determines the web app's compute, storage, and features.

1. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3984393f-fe82-458a-92aa-8a544f5c8c05)

2. Search for and select App services.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0dea2f51-ea5c-459b-aacb-97df06b5a8c2)

3. Select + Create, from the drop-down menu, Web App. Notice the other choices.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b48ee555-cb24-452b-afd8-90f1aa58c97d)

4. On the Basics tab of the Create Web App blade, specify the following settings (leave others with their default values):

- Setting	Value

- Subscription	your Azure subscription

- Resource group	az104-rg9 

- Web app name	any globally unique name

- Publish	Code

- Runtime stack	PHP 8.2

- Operating system	Linux

- Region	East US

- Pricing plans	accept the defaults

- Zone redundancy	accepts the defaults

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b58aca81-c8ae-4bef-962b-43e926dff9af)

5. Click Review + Create, and then Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9ad92765-4527-4535-acde-baa5ff089a6b)

6. After the deployment, select Go to resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a6b5dd02-40f8-424a-82ed-de7c7ea9a029)

# Task 2: Create and configure a deployment slot

- In this task, you will create a staging deployment slot. Deployment slots enable you to perform testing before making your app available to the public (or your end users). After you have performed testing, you can swap the slot from development or staging to production. Many organizations use slots to perform pre-production testing. Additionally, many organizations run multiple slots for every application (for example, development, QA, test, and production).

1. On the blade of the newly deployed Web App, click the Default Domain link to display the default web page in a new browser tab.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/fb658b99-2198-4ea0-a269-1261dec7b490)

2. Close the new browser tab and, back in the Azure portal, in the Deployment section of the Web App blade, click Deployment slots.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/199d111e-1abd-4f97-8a14-d51660b837bc)

3. Click Add slot, and add a new slot with the following settings:

- Setting	Value

- Name	staging

- Clone settings from	Do not clone settings

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e36caf82-ab11-465c-a6b3-a7ccad739dcc)

4. Select Add.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6f71a111-941d-4bc6-a6dd-0d9fe6039363)

5. Back on the Deployment slots blade of the Web App, click the entry representing the newly created staging slot.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/aac19cf0-bb52-401a-9798-8f01c7104ab7)

6. Review the staging slot blade and note that its URL differs from the one assigned to the production slot.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ae75db00-968b-4103-b44d-9c5f4e095e60)


