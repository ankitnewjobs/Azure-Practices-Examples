# Implement Azure Container Instances

# Lab introduction

- In this lab, you learn how to implement and deploy Azure Container Instances.

# Lab scenario

- Your organization has a web application that runs on a virtual machine in your on-premises data center. The organization wants to move all applications to the cloud but doesn’t want to have a large number of servers to manage. You decide to evaluate Azure Container Instances and Docker.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2bf715b2-231b-4c7b-8a18-2197b2821840)

# Job skills

- Task 1: Deploy an Azure Container Instance using a Docker image.

- Task 2: Test and verify deployment of an Azure Container Instance.

# Task 1: Deploy an Azure Container Instance using a Docker image

- In this task, you will create a simple web application using a Docker image. Docker is a platform that provides the ability to package and run applications in isolated environments called containers. Azure Container Instances provides the compute environment for the container image.

1. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4e8b86c1-6852-4751-8ec7-5a8d13fef69c)

2. In the Azure portal, search for and select Container instances and then, on the Container instances blade, click + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c2e13222-6e16-4e59-b812-15ecf511284a)

3. On the Basics tab of the Create container instance blade, specify the following settings (leave others with their default values):

- Setting	Value

- Subscription	Select your Azure subscription

- Resource group	az104-rg9 (If necessary, select Create new)

- Container name	az104-c1

- Region	East US (or a region available near you)

- Image Source	Quickstart images

- Image	mcr.microsoft.com/azuredocs/aci-helloworld:latest (Linux)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a1d422d3-f514-49e3-8052-3f381ac528fc)

4. Click Next: Networking > and specify the following settings (leave others with their default values):

- Setting	Value

- DNS name label	any valid, globally unique DNS host name

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/61b67d08-4d7c-4927-b7a1-9839a06f0f09)

4. Click Next: Advanced >, review the settings without making any changes.

5. Click Review + Create, ensure that the validation passed and then select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4e08a7ad-67e4-4349-99b3-4f3673456356)

