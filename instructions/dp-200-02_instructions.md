﻿# DP 200 - Implementing a Data Platform Solution
# Lab 2 - Working with Data Storage

**Estimated Time**: 60 minutes

**Pre-requisites**: It is assumed that the case study for this lab has already been read. It is assumed that the content and lab for module 1: Azure for the Data Engineer has also been completed

**Lab files**: The files for this lab are located in the _Allfiles\Labfiles\Starter\DP-200.2_ folder.

## Lab overview

In this lab, the students will be able to determine the appropriate storage type to implement against a given set of business and technical requirements. They will be able to create Azure storage accounts and Data Lake Storage account and explain the difference between Data Lake Storage version 1 and version 2. They will also be able to demonstrate how to perform data loads into the data storage of choice.

## Lab objectives
  
After completing this lab, you will be able to:

1. Choose a data storage approach in Azure
1. Create an Azure Storage Account
1. Explain Azure Data Lake Storage
1. Upload data into Azure Data Lake

## Scenario
  
You have been hired as a Senior Data Engineer to implement a technology solution that is part of a digital transformation project. The organization is migrating an Internet Information Services (IIS) that hosts the company website to Azure. The developers are in the process of transferring the web application and its logic to Azure Web Apps and they have asked you to prepare a data store for them that can be used to host the static images that are used on the website.

In addition, the information services department have informed you that their team is expanding and that they will soon be joined by data scientists that will start the process of building a predictive analytics solution. You have been asked to set up a solution that will be used to host the production environment of their work. In the first instance, you will asses what is the appropriate storage tier to create for the solution.

At the end of this work, you will have:

1. Choose a data storage approach in Azure
2. Create an Azure Storage Account
3. Explain Azure Data Lake Storage
4. Upload data into Azure Data Lake

> **IMPORTANT**: As you go through this lab, make a note of any issue(s) that you have encountered in any provisioning or configuration tasks and log it in the table in the document located at _\Labfiles\DP-200-Issues-Doc.docx_. Document the Lab number, note the technology, Describe the issue, and what was the resolution. Save this document as you will refer back to it in a later module.

## Exercise 1: Choose a data storage approach in Azure

Estimated Time: 15 minutes

Individual exercise
  
The main task for this exercise are as follows:

1. From the case study, identify the data storage requirements for the static images for the website, and for the predictive analytics solution.

1. The instructor will discuss the findings with the group.

### Task 1: Identify the data storage requirements and structures of AdventureWorks.

1. From the lab virtual machine, start **Microsoft Word**, and open up the file **DP-200-Lab02-Ex01.docx** from the **Allfiles\Labfiles\Starter\DP-200.2** folder.

1. Spend **10 minutes** documenting the data storage requirements as outlined in the scenario of this lab. You can also use the case study document for additional reference.

### Task 2: Discuss the findings with the Instructor

1. The instructor will stop the group to discuss the findings.

> **Result**: After you completed this exercise, you have created a Microsoft Word document that shows two tables of data storage requirements.

## Exercise 2: Create an Azure Storage Account
  
Estimated Time: 20 minutes

Individual exercise
  
The main tasks for this exercise are as follows:

1. Create Azure resource group named **awrgstudxx** in the region closest to the lab location , where **xx** are your initials.

1. Create and configure a storage account named **awsastudxx** in the region closest to the lab location within the resource group awrgstudxx, where **xx** are your initials.

1. Create a container named **images** and **data** within the awsastudxx storage account.

1. Upload some graphics to the images container of the storage account.

### Task 1: Create and configure a resource group.

1. From the lab virtual machine, start Microsoft Edge, browse to the Azure portal at [**http://portal.azure.com**](http://portal.azure.com) and sign in by using the account that has been assigned to you for the course.

1. In the Azure portal, navigate to the **Resource groups** blade.

1. From the **Resource groups** blade, create the first resource group with the following settings:

    - Resource group name: **awrgstudxx**, where **xx** are your initials.

    - Subscription: the name of the subscription you are using in this lab

    - Resource group location: the name of the Azure region which is closest to the lab location and where you can provision Azure VMs.

      > **Note**: To identify Azure regions available in your subscription, refer to [**https://azure.microsoft.com/en-us/regions/offers/**](https://azure.microsoft.com/en-us/regions/offers/)

### Task 2: Create and configure a storage account.

1. In the Azure portal, navigate to the **+ Create a resource** blade.

1. In the New blade, navigate to the **Search the Marketplace** text box, and type the word **storage**. Click **Storage account** in the list that appears.

1. In the **Storage account** blade, click **Create**.

1. From the **Create storage account*** blade, create the first storage account with the following settings:
    
    - Subscription: the name of the subscription you are using in this lab
    
    - Resource group name: **awrgstudxx**, where **xx** are your initials.

    - Storage account name: **awsastudxx**, where **xx** are your initials.

    - Location: the name of the Azure region which is closest to you.

    - Performance: **Standard**.

    - Account kind: **StorageV2 (general purpose v2)**.
    
    - Replication: **Locally-redundant storage (LRS)**.

1. In the **Create storage account*** blade, click **Review + create**.

1. After the validation of the  **Create storage account*** blade, click **Create**.

   > **Note**: The creation of the storage account will take approximately 90 seconds while it provisions the disks and the configuration of the disks as per the settings you have defined.

### Task 3: Create and configure a container within the storage account.

1. In the Azure portal, a message states that _Your deployment is complete_, click on the button **Go to resource**.

1. In the **awsastudxx** screen, where **xx** are your initials. In the left pane, under the **Blob service** click **Containers**.

1. In the **awsastudxx - Containers** screen, at the top left, click on the  **+ Container** button.

1. From the **New Container*** screen, create a container with the following settings:

    - Name: **images**.

    - Public access level: **Private (no anonymous access)**

1. In the **New Container*** screen, click **Create**.

   > **Note**: The creation of the container is immediate and will appear in the list of the **awrgstudxx - Containers** screen.

1. Repeat steps 4 -5 to create a container named **data** with the public access level of **Private (no anonymous access)**

1. Repeat steps 4 -5 to create a container named **tweets** with the public access level of **Private (no anonymous access)**

### Task 4: Upload some graphics to the images container of the storage account.

1. In the Azure portal, in the **awsastudxx - Containers** screen, click on the **images** item in the list.

1. In the **images** screen, click on the **Upload** button.

1. In the **Upload blob** screen, in the Files text box, click on the **folder** icon to the right of the text box.

1. In the **Open** dialog box, browse to  **Labfiles\Starter\DP-200.2\website graphics** folder. Highlight the following files:

    - one.png

    - two.png

    - three.png

    - No.png

1. In the **Open** dialog box, click **Open**. 

1. In the **Upload blob** screen, click on the **Upload** button.

1. Close the **Upload blob** screen, and close the **images** screen.

1. In the Azure portal, in the **awsastudxx - Containers** screen, click on the **data** item in the list.

1. In the **data** screen, click on the **Upload** button.

1. In the **Upload blob** screen, in the Files text box, click on the **folder** icon to the right of the text box.

1. In the **Open** dialog box, browse to  **Labfiles\Starter\DP-200.2\Static files** folder. Highlight the **DimDate2.txt** file.

1. In the **Open** dialog box, click **Open**. 

1. In the **Upload blob** screen, click on the **Upload** button.

1. Close the **Upload blob** screen, and in the Azure portal, navigate to the **Home** blade 

   > **Note**: The upload of the files will take approximately 5 seconds. Once completed, they will appear in a list in the upload blobs screen.

> **Result**: After you completed this exercise, you have created a Storage account named awsastudxx that has a container named images that contains four graphics files that are ready to be used on the AdventureWorks website.

## Exercise 3: Explain Azure Data Lake Storage
  
Estimated Time: 15 minutes

Individual exercise
  
The main tasks for this exercise are as follows:

1. Create and configure a storage account named **awdlsstudxx** as a Data Lake Store Gen II storage type in the region closest to the lab location, within the resource group awrgstudxx, where **xx** are your initials.

1. Create a file system named **data** within the awdlsstudxx storage account.

1. Upload some data files to the data container of the storage account.

### Task 1: Create and configure a storage account as a Data Lake Store Gen II store.

1. In the Azure portal, navigate to the **+ Create a resource** blade.

1. In the New blade, navigate to the **Search the Marketplace** text box, and type the word **storage**. Click **Storage account** in the list that appears.

1. In the **Storage account** blade, click **Create**.

1. From the **Create storage account*** blade, create the first storage account with the following settings:

    - Subscription: the name of the subscription you are using in this lab

    - Resource group name: **awrgstudxx**, where **xx** are your initials.

    - Storage account name: **awdlsstudxx**, where **xx** are your initials.

    - Location: the name of the Azure region which is closest to you.

    - Performance: **Standard**.

    - Account kind: **StorageV2 (general purpose v2)**.
    
    - Replication: **Locally-redundant storage (LRS)**.

1. In the **Advanced** tab, click **Enabled** next to **Hierarchical namespace** under Data Lake Storage Gen2.

1. Click on **Review + create**.

1. After the validation of the  **Create storage account*** blade, click **Create**.

   > **Note**: The creation of the storage account will take approximately 90 seconds while it provisions the disks and the configuration of the disks as per the settings you have defined.

### Task 2: Create and configure a file system within the storage account.

1. In the Azure portal, a message states that _Your deployment is complete_, click on the button **Go to resource**.

1. In the **awdlsstudxx** screen, where **xx** are your initials, under the **Blob service** click **Containers**.

1. In the **awrgstudxx - Containers** screen, at the top left, click on the  **+ Container** button.

1. From the **New container** screen, create a container with the following settings:

    - Name: **data**.

1. In the **New container*** screen, click **Create**.

   > **Note**: The creation of the container is immediate and will appear in the list of the **awdlsstudxx - Containers** screen.

> **Result**: After you completed this exercise, you have created a Data Lake Gen II Storage account named awdlsstudxx that has a container named data.

## Exercise 4: Upload data into Azure Data Lake.
  
Estimated Time: 10 minutes

Individual exercise
  
The main task for this exercise are as follows:

1. Install and start Microsoft Azure Storage Explorer. This is already installed on the lab VM provided through esi.learnondemand.net. If you are not working with the lab VM you can install Azure Storage Explorer from [here](https://azure.microsoft.com/en-us/features/storage-explorer/) where there is a button that states **Download Storage Explorer free**. Click on this button.

1. Upload some data files to the data container of the Data Lake Gen II Storage Account.

### Task 1: Install Storage Explorer.

1. In the lab VM, open the Azure Storage Explorer.

1. In Storage Explorer, select the icon of the person which is called **Manage Accounts** to go to the **Account Management Panel**.

1. The left pane now displays all the Azure accounts you've signed in to which will be empty. To connect to new account, select **Add an account**

1. In the pop up to connect to Azure Storaeg, select to **Add an Azure Account** and click **Next**. Sign in to your account. 

1. After you successfully sign in with an Azure account, the account and the Azure subscriptions associated with that account are added to the left pane. Select the Azure subscriptions that you want to work with, and then select **Apply**. The left pane displays the storage accounts associated with the selected Azure subscriptions.

### Task 2: Upload data files to the data container of the Data Lake Gen II Storage Account.

1. In Azure Storage Explorer, click on the arrow to expand your subscription.

1. Under **Storage Accounts**, search for the storage account **awdlsstudxx (ADLS Gen2)**, and click on the arrow to expand it.

1. Under **Blob Containers**, click on the arrow to expand it and show the **data** container. Click on the **data** container.

1. In Azure Storage Explorer, click on the arrow next to the **Upload** icon, and click on the **Upload Files..**.

1. In Upload Files dialog box, click on the ellipsis next to the **Selected files** text box.

1. In the **Choose files to upload** dialog box, browse to **Labfiles\Starter\DP-200.2\logs** folder. Highlight the following files:

    - weblogsQ1.log

    - weblogsQ2.log

    - preferences.json

1. In the **Choose files to upload** dialog box, click **Open**.

1. In the **Upload Files** screen, click on the **Upload** button.

   > **Note**: The upload of the files will take approximately 5 seconds. You will see a message in Azure Storage Explorer that states **Your view may be out of data. Do you want to refresh? Click Yes**. Once completed, all three files will appear in a list in the upload blobs screen.

1. Close down Azure Storage Explorer.

1. Return to the Azure portal, and navigate to the **Home** blade.

> **Result**: After you completed this exercise, you have created a Data Lake Gen II Storage account named awdlsstudxx that has a file system named data that contains two weblog files that are ready to be used by the Data scientists at AdventureWorks.
