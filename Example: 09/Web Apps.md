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

# Task 3: Configure Web App deployment settings

- In this task, you will configure Web App deployment settings. Deployment settings allow for continuous deployment. This ensures that the app service has the latest version of the application.

1. In the staging slot, select Deployment Center and then select Settings.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/64832158-3db1-483b-85ed-4abd1c436816)

2. In the Source drop-down list, select External Git. Notice the other choices.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d2a193de-f819-4795-b542-cd885ea56b42)

3. In the repository field, enter https://github.com/ankitnewjobs/Azure-Example-php-docs-hello-world

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e0e8f03f-02cf-439c-939f-20d6bdc2e845)

4. In the branch field, enter master/main.

5. Select Save.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e668cfb8-7679-4e71-a1d0-8069169edc9a)

6. From the staging slot, select Overview.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9b9995df-854a-46f9-be9a-d6ee3c762dd2)

7. Select the Default domain link, and open the URL in a new tab.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3d87e563-40c7-4dd2-9dd9-a9d9330462e0)

8. Verify that the staging slot displays Hello World.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/243b4916-9a19-4d24-8684-c2af19f971a0)

# Task 4: Swap deployment slots

- In this task, you will swap the staging slot with the production slot. Swapping a slot allows you to use the code that you have tested in your staging slot, and move it to production. The Azure portal will also prompt you if you need to move other application settings that you have customized for the slot. Swapping slots is a common task for application teams and application support teams, especially those deploying routine app updates and bug fixes.

1. Navigate back to the Deployment slots blade, and then select Swap.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3f4424a0-1458-4004-8041-a96e915acd73)

2. Review the default settings and click Swap.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3e37d219-48d2-412c-a9b1-6214017ab73b)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8cd9a6ed-81cd-4294-bf64-39084d71b0cf)

3. On the Overview blade of the Web App select the Default domain link to display the website home page.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/fe732688-10c5-4617-a713-67bef693febb)

4. Review the default settings and click Swap.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8cd9a6ed-81cd-4294-bf64-39084d71b0cf)

5. Verify the production web page displays the Hello World! page.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4486a06d-eb80-4b38-9f53-56029dabb026)

# Task 5: Configure and test autoscaling of the Azure Web App

- In this task, you will configure the autoscaling of Azure Web App. Autoscaling enables you to maintain optimal performance for your web app when traffic to the web app increases. To determine when the app should scale you can monitor metrics like CPU usage, memory, or bandwidth.

1. In the Settings section, select Scale-out (App Service plan).

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a10d2b94-572c-4aa4-ab9a-9a5fc60c2e80)

2. From the Scaling section, select Automatic. Notice the Rules-based option. Rules-based scaling can be configured for different app metrics.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/afca06ca-c4d2-4b0d-9b88-8a73af346576)

3. In the Maximum burst field, select 2.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/52a4d94e-8b33-4a85-986e-72a709942284)

4. Select Save.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/927b887d-9e77-465b-9761-1bd777c17842)

5. Select Diagnose and solve problems (left pane).

6. In the Load Test your App box, select Create Load Test.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2abd51c0-1312-4c4f-ab4a-633dcddb9249)

- Select + Create and give your load test a name. The name must be unique.

- Select Review + Create and then Create.

 ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/32bcc6d7-a500-4ec3-ad37-64b2838015d8)

7. Wait for the load test to be created, and then select Go to the resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/975fe9f3-445c-4956-bb7a-dacf6b0d8483)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1f554291-c48c-4601-b618-fc9654209de1)

8. From the Overview	Add HTTP requests, select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a6c5f233-6eaa-4d8e-b312-cf17edbad91e)

9. For the Test URL, paste in your Default domain URL. Ensure this is properly formatted and begins with https://.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9c4c5231-e339-40c7-85c1-012942a88cba)

10. Select Review + create and Create.

11. Review the test results including Virtual users, Response time, and Requests/sec.

12. Select Stop to complete the test run.

# Key takeaways

- Azure App Services lets you quickly build, deploy, and scale web apps.

- App Service includes support for many developer environments including ASP.NET, Java, PHP, and Python.

- Deployment slots allow you to create separate environments for deploying and testing your web app.

- You can manually or automatically scale a web app to handle additional demand.

- A wide variety of diagnostics and testing tools are available.
