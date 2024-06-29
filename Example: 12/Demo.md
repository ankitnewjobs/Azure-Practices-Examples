# Manage Azure Storage

# Lab introduction

- In this lab, you learn to create storage accounts for Azure blobs and Azure files. You learn to configure and secure blob containers. You also learn to use Storage Browser to configure and secure Azure file shares.

# Lab scenario

- Your organization is currently storing data in on-premises data stores. Most of these files are not accessed frequently. You would like to minimize the cost of storage by placing infrequently accessed files in lower-priced storage tiers. You also plan to explore different protection mechanisms that Azure Storage offers, including network access, authentication, authorization, and replication. Finally, you want to determine to what extent Azure Files is suitable for hosting your on-premises file shares.

# Architecture diagram

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e7ed2e9b-639d-4075-9d08-64c2ace6a7d5)

# Job skills

- Task 1: Create and configure a storage account.

- Task 2: Create and configure secure blob storage.

- Task 3: Create and configure secure Azure file storage.

# Task 1: Create and configure a storage account.

- In this task, you will create and configure a storage account. The storage account will use geo-redundant storage and will not have public access.

1. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/003f76ab-7a4d-4507-abd4-22d3412931a2)

2. Search for and select Storage accounts, and then click + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c0bd04c5-52bc-4e0f-8565-a4c0bcd1153d)

3. On the Basics tab of the Create a storage account blade, specify the following settings (leave others with their default values):

- Setting	Value

- Subscription	the name of your Azure subscription

- Resource group	az104-rg12 (create new)

- Storage account name	any globally unique name between 3 and 24 in length consisting of letters and digits

- Region	(US) East US

- Performance	Standard (notice the Premium option)

- Redundancy	Geo-redundant storage (notice the other options)

- Make read access to data in the event of regional availability	Check the box

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d1d440da-36b5-4b07-ac8b-91ece4a82f39)

1. On the Advanced tab, use the informational icons to learn more about the choices. Take the defaults.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0ce207a9-9a92-4e26-88ae-72e582fcbd00)

2. On the Networking tab, review the available options, select Disable public access, and use private access.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b1fc821c-5d53-44e9-8c09-8f7775d4c5df)

3. Review the Data Protection tab. Notice that 7 days is the default soft delete retention policy. Note you can enable blob versioning. Accept the defaults.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0657a8d7-5cd4-4be6-99c1-a3f200613c68)

4. Review the Encryption tab. Notice the additional security options. Accept the defaults.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/646d45a2-cac2-4094-ae03-1b2fdd2714e5)

5. Select Review, wait for the validation process to complete, and then click Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/72aae666-cdb0-4959-a427-de4fcc258371)

6. Once the storage account is deployed, select Go to the resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f2cee69b-95af-4a7a-aad8-9c7805df892a)

7. Review the Overview blade and the additional configurations that can be changed. These are global settings for the storage account. Notice the storage account can be used for Blob containers, File shares, Queues, and Tables.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4fca4eed-29a0-42d3-ba52-5ab10a7886ae)

8. In the Security + networking section, select Networking. Notice public network access is disabled.

- Change the public access level to Enabled from selected virtual networks and IP addresses.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/21dad183-ec3d-4dba-b781-5c82c0811009)

- In the Firewall section, check the box for Add your client IP address.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/96d7ba40-ad94-4c1a-99c6-8b94dc8466fb)

- Be sure to Save your changes.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e508f45e-d6ef-4a7d-ba95-4a095045d792)

9. In the Data management section, view the Redundancy blade. Notice the information about your primary and secondary data center locations.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6115b3c7-e4b8-4828-97e6-15757344e5d1)

10. In the Data Management section, select Lifecycle Management, and then select Add a rule.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/076d4c7c-b37a-464f-87fe-71107ec4cd2b)

- Name the rule Movetocool. Notice your options for limiting the scope of the rule.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e005e824-4041-4a6e-901e-ed843ea92d5a)

- On the Base blobs tab, if based blobs were last modified more than 30 days ago then move to cool storage. Notice your other choices.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f522979f-b00f-44b1-8d7c-087e7936b747)

- Notice you can configure other conditions. Select Add when you are done exploring.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f5e91737-63f9-4582-9dab-370615eca7d1)

# Task 2: Create and configure secure blob storage

- In this task, you will create a blob container and upload an image. Blob containers are directory-like structures that store unstructured data.

# Create a blob container and a time-based retention policy

1. Continue in the Azure portal, working with your storage account.

2. In the Data storage section, click Containers.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/190809f4-b73e-4666-ab33-12dda0dd83a6)

3. Click + Container and Create a container with the following settings:

- Setting	Value

- Name	data

- Public access level	Notice the access level is set to private

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/53f1916a-01a7-47e8-b5e8-91094aec31b6)

4. On your container, scroll to the ellipsis (…) on the far right, and select Access Policy.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/77878697-f4e9-4a34-9c62-f1d537e740de)

5. In the Immutable Blob storage area, select Add Policy.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/666c3d83-025f-4f74-b70e-9565af2fbd8e)

- Setting	Value

- Policy type	Time-based retention

- Set retention period for	180 days

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/cefc1f57-fa8c-4f4f-8db5-13a26658c8d6)

6. Select Save.

# Manage blob uploads

1. Return to the containers page, select your data container, and then click Upload.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f20fc8b8-59a8-45cb-961f-681c1df598b4)

2. On the Upload blob blade, expand the Advanced section.

- Setting	Value

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7bde5590-6ee5-4420-a358-1af40a9577db)

- Browse for files	and add the file you have selected to upload

- Select Advanced	 

- Blob type	Block blob

- Block size	4 MiB

- Access tier	Hot (notice the other options)

- Upload to folder	security test

- Encryption scope	Use existing default container scope

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c5e65662-9290-4d15-b69b-35ebe11aac76)

3. Click Upload.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9995b669-f562-43e6-a613-0608555017bc)

4. Confirm you have a new folder, and that your file was uploaded.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/90e8e05b-6ab9-4ee7-aecd-da6d67901e2f)

5. Select your upload file and review the options including Download, Delete, Change tier, and Acquire lease.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/84861262-2ac6-457a-ae5f-06635186f9d7)

6. Copy the file URL and paste it into a new private browsing window.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f34f3a31-d78e-4e1f-95a3-0ccdab601f75)

7. You should be presented with an XML-formatted message stating ResourceNotFound or PublicAccessNotPermitted.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/460cf835-ac7b-4ffd-99d7-8718f4bfc140)

# Configure limited access to the blob storage

1. Select your uploaded file and then on the **Generate SAS tab**. You can also use the ellipsis (…) to the far right. Specify the following settings (leave others with their default values):

- Setting	Value

- Signing key	Key 1

- Permissions	Read (notice your other choices)

- Start date	yesterday’s date

- Start time	current time

- Expiry date	tomorrow’s date

- Expiry time	current time

- Allowed IP addresses	to be left blank

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/268d0a48-1e02-4b3c-9836-c80f10394c71)

2. Click Generate SAS token and URL.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f793396a-1d94-42bd-a46b-7f68ac2a97d2)

3. Copy the Blob SAS URL entry to the clipboard.

4. Open another InPrivate browser window and navigate to the Blob SAS URL you copied in the previous step.

# Task 3: Create and configure an Azure File storage

- In this task, you will create and configure Azure File shares. You will use Storage Browser to manage the file share.

# Create the file share and upload a file

1. In the Azure portal, navigate back to your storage account, in the Data storage section, click File Shares.


![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/cd4ec769-8eb6-44bb-902e-65ae73b4dd5e)

2. Click + File share and on the Basics tab give the file share a name, share1.

3. Notice the Access tier options. Keep the default Transaction optimized.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9986b182-eed5-49a0-a69f-9e9fe7cc8dd2)

4. Move to the Backup tab and ensure Enable backup is not checked. We are disabling backup to simplify the lab configuration.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7c7d1776-3352-4854-bd67-34c51f74ffa0)

5. Click Review + Create, and then Create. Wait for the file share to deploy.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9a0c39c9-9420-48ff-9842-e41e0724f444)


![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/76bdb496-ffbc-4f50-95a0-507b5d2fbd47)

# Explore Storage Browser and upload a file

1. Return to your storage account and select Storage Browser. The Azure Storage Browser is a portal tool that lets you quickly view all the storage services under your account.

2. Select File shares and verify your share1 directory is present.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/65cee8c2-eb6a-43fd-b0df-7d4b72a2e115)

3. Select your share1 directory and notice you can + Add directory. This lets you create a folder structure.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d470f8e5-257b-4c47-af67-b6cc6ccf73a2)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/aca4069e-d0f4-4635-ae62-e741ece600a9)

4. Select Upload. Browse to a file of your choice, and then click Upload.


![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a0bd5f84-2c7a-46c2-be90-142933c09d92)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1959895a-62fd-4656-8159-d7149d4ae97e)

# Restrict network access to the storage account

1. In the portal, search for and select Virtual Networks.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7e26d4dc-c98b-40aa-ab5e-ed65fa3fecca)

2. Select + Create. Select your resource group. and give the virtual network a name, vnet1.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b42a65bd-aec8-4fea-bbc4-81d3bcb7701e)

3. Take the defaults for other parameters, select Review + Create, and then Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a9546678-a2ba-481c-a0d7-4f2da916ce0f)

4. Wait for the virtual network to deploy, and then select Go to the resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/319a6bf8-9d56-4cfb-ac8e-79aefab451d0)

5. In the Settings section, select the Service endpoints blade.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b30fb287-f82b-40d9-bda4-3aa47107a990)

- Select Add.

- In the Services drop-down select Microsoft.Storage.

- In the Subnets drop-down check the Default subnet.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/5be5ddbd-260e-41ca-9670-384bf8e80b47)

- Click Add to save your changes.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2bd3c9be-c74f-4389-8364-0afd19df773a)

6. Return to your storage account.

7. In the Security + networking section, select the Networking blade.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/be24ad3c-db25-4398-bb2b-6f146564018f)

8. Select Add existing virtual network and select vnet1 and default subnet, select Add.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/623b2a4c-98c1-4166-a179-d8b5a3ce9df8)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0f95a0d7-55c1-47d0-a5fc-39db3d623535)

9. In the Firewall section, Delete your machine IP address. Allowed traffic should only come from the virtual network.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/adbfd37e-a77d-449a-9848-8e0606fa5a86)

10. Be sure to Save your changes.

11. Select the Storage browser and Refresh the page. Navigate to your file share or blob content.

- **File Share**

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4a87065c-d691-47be-925b-e5f927275996)

- **Blob**

  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f6db2b28-7485-4570-b7f7-0ba20cfb4fd9)


