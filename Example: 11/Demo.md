# Implement Azure Container Apps

- Lab introduction

In this lab, you learn how to implement and deploy Azure Container Apps.

# Lab scenario

- Your organization has a web application that runs on a virtual machine in your on-premises data center. The organization wants to move all applications to the cloud but doesn’t want to have a large number of servers to manage. You decide to evaluate Azure Container Apps.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/75d7f565-77b2-4e7a-9434-94e3ab3702f4)

# Job skills

- Task 1: Create and configure an Azure Container App and environment.

- Task 2: Test and verify deployment of the Azure Container App.

# Task 1: Create and configure an Azure Container App and environment

- Azure Container Apps take the concept of a managed Kubernetes cluster a step further and manage the cluster environment as well as provide other managed services on top of the cluster. Unlike an Azure Kubernetes cluster, where you must still manage the cluster, an Azure Container Apps instance removes some of the complexity of setting up a Kubernetes cluster.

1. From the Azure portal, search for and select Container Apps.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8e6c6c9b-e69d-4437-99c3-ad824ad26fdf)

2. From Container Apps, select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/83e6267f-7dc7-4cf6-9bc4-f79ace8c694f)

3. Use the following information to fill out the details on the Basics tab.*.

- Setting	Action

- Subscription	Select your Azure subscription

- Resource group	az104-rg9

- Container app name	my-app

- Region	East US (Or a region available near you)

- Container Apps Environment	Leave the default

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c0fb72cc-d13c-4f30-8f97-c59fb2c20ac5)

- On the Container tab, ensure that the Use quickstart image is enabled and that the quickstart image is set to Simple hello-world container.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/87f76e83-fe1f-4166-b2e0-da43164a9ed8)

4. Select the Review Create and then Create.

# Task 2: Test and verify deployment of the Azure Container App

- By default, the Azure container app that you create will accept traffic on port 80 using the sample Hello World application. Azure Container Apps will provide a DNS name for the application. Copy and navigate to this URL to ensure that the application is up and running.

1. Select Go to Resource to view your new container app.

2. Select the link next to the Application URL to view your application.

3. Verify you receive the Your Azure Container Apps app is live message.