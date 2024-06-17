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

2. Search for and select App services.

3. Select + Create, from the drop-down menu, Web App. Notice the other choices.

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

- Click Review + Create, and then Create.

6. After the deployment, select Go to resource.
