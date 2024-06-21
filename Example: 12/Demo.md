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

2. Search for and select Storage accounts, and then click + Create.

3. On the Basics tab of the Create a storage account blade, specify the following settings (leave others with their default values):

- Setting	Value

- Subscription	the name of your Azure subscription

- Resource group	az104-rg12 (create new)

- Storage account name	any globally unique name between 3 and 24 in length consisting of letters and digits

- Region	(US) East US

- Performance	Standard (notice the Premium option)

- Redundancy	Geo-redundant storage (notice the other options)

- Make read access to data in the event of regional availability	Check the box

1. On the Advanced tab, use the informational icons to learn more about the choices. Take the defaults.

2. On the Networking tab, review the available options, select Disable public access, and use private access.

3. Review the Data Protection tab. Notice that 7 days is the default soft delete retention policy. Note you can enable blob versioning. Accept the defaults.

4. Review the Encryption tab. Notice the additional security options. Accept the defaults.

5. Select Review, wait for the validation process to complete, and then click Create.

6. Once the storage account is deployed, select Go to the resource.

7. Review the Overview blade and the additional configurations that can be changed. These are global settings for the storage account. Notice the storage account can be used for Blob containers, File shares, Queues, and Tables.

8. In the Security + networking section, select Networking. Notice public network access is disabled.

- Change the public access level to Enabled from selected virtual networks and IP addresses.

- In the Firewall section, check the box for Add your client IP address.

- Be sure to Save your changes.

9. In the Data management section, view the Redundancy blade. Notice the information about your primary and secondary data center locations.

10. In the Data Management section, select Lifecycle Management, and then select Add a rule.

- Name the rule Movetocool. Notice your options for limiting the scope of the rule.

- On the Base blobs tab, if based blobs were last modified more than 30 days ago then move to cool storage. Notice your other choices.

- Notice you can configure other conditions. Select Add when you are done exploring.

# Task 2: Create and configure secure blob storage

- In this task, you will create a blob container and upload an image. Blob containers are directory-like structures that store unstructured data.

# Create a blob container and a time-based retention policy

1. Continue in the Azure portal, working with your storage account.

2. In the Data storage section, click Containers.

3. Click + Container and Create a container with the following settings:

- Setting	Value

- Name	data

- Public access level	Notice the access level is set to private

4. On your container, scroll to the ellipsis (…) on the far right, select Access Policy.

5. In the Immutable blob storage area, select Add policy.

- Setting	Value

- Policy type	Time-based retention

- Set retention period for	180 days

8. Select Save.

# Manage blob uploads

1. Return to the containers page, select your data container and then click Upload.

2. On the Upload blob blade, expand the Advanced section.


- Setting	Value

- Browse for files	add the file you have selected to upload

- Select Advanced	 

- Blob type	Block blob

- Block size	4 MiB

- Access tier	Hot (notice the other options)

- Upload to folder	security test

- Encryption scope	Use existing default container scope

3. Click Upload.

4. Confirm you have a new folder, and that your file was uploaded.

5. Select your upload file and review the options including Download, Delete, Change tier, and Acquire lease.

6. Copy the file URL and paste it into a new In private browsing window.

7. You should be presented with an XML-formatted message stating ResourceNotFound or PublicAccessNotPermitted.


# Configure limited access to the blob storage

1. Select your uploaded file and then on the Generate SAS tab. You can also use the ellipsis (…) to the far right. Specify the following settings (leave others with their default values):

- Setting	Value

- Signing key	Key 1

- Permissions	Read (notice your other choices)

- Start date	yesterday’s date

- Start time	current time

- Expiry date	tomorrow’s date

- Expiry time	current time

- Allowed IP addresses	to be left blank

2. Click Generate SAS token and URL.

3. Copy the Blob SAS URL entry to the clipboard.

4. Open another InPrivate browser window and navigate to the Blob SAS URL you copied in the previous step.

# Task 3: Create and configure an Azure File storage

- In this task, you will create and configure Azure File shares. You will use Storage Browser to manage the file share.

# Create the file share and upload a file

1. In the Azure portal, navigate back to your storage account, in the Data storage section, click File Shares.

2. Click + File share and on the Basics tab give the file share a name, share1.

3. Notice the Access tier options. Keep the default Transaction optimized.

4. Move to the Backup tab and ensure Enable backup is not checked. We are disabling backup to simplify the lab configuration.

5. Click Review + Create, and then Create. Wait for the file share to deploy.

# Explore Storage Browser and upload a file

1. Return to your storage account and select Storage Browser. The Azure Storage Browser is a portal tool that lets you quickly view all the storage services under your account.

2. Select File shares and verify your share1 directory is present.

3. Select your share1 directory and notice you can + Add directory. This lets you create a folder structure.

4. Select Upload. Browse to a file of your choice, and then click Upload.

# Restrict network access to the storage account

1. In the portal, search for and select Virtual Networks.

2. Select + Create. Select your resource group. and give the virtual network a name, vnet1.

3. Take the defaults for other parameters, select Review + Create, and then Create.

4. Wait for the virtual network to deploy, and then select Go to the resource.

5. In the Settings section, select the Service endpoints blade.

- Select Add.

- In the Services drop-down select Microsoft.Storage.

- In the Subnets drop-down check the Default subnet.

- Click Add to save your changes.

6. Return to your storage account.

7. In the Security + networking section, select the Networking blade.

8. Select Add existing virtual network and select vnet1 and default subnet, select Add.

9. In the Firewall section, Delete your machine IP address. Allowed traffic should only come from the virtual network.

10. Be sure to Save your changes.

11. Select the Storage browser and Refresh the page. Navigate to your file share or blob content.

