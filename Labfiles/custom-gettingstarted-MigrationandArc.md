# Building The Business Migration Case With Windows Server And SQL Server

### Estimated Duration: 4 Hours

## Overview

Azure Migrate is Microsoft's centralized platform designed to assist organizations in planning, assessing, and executing their migration journey to Azure. It provides a suite of tools and features to simplify the process of moving on-premises workloads, applications, databases, and virtual machines to the Azure cloud.

Azure Data Studio helps you upgrade to a modern data platform by detecting compatibility issues that can impact database functionality in your new version of SQL Server or Azure SQL Database. Azure Data Studio recommends performance and reliability improvements for your target environment and allows you to move your schema, data, and uncontained objects from your source server to your target server.

In this Hands-On Lab, you will use Azure Migrate: Server Assessment to evaluate the on-premises environment. This process includes selecting Azure Migrate tools, deploying the Azure Migrate appliance into the on-premises environment, creating a migration assessment, and using Azure Migrate dependency visualization. 
 
## Objective

- **Discover your Windows Server:** Leverage the Azure Migrate Appliance to comprehensively discover and assess your Windows Server environment with Hyper-V, enabling detailed analysis and readiness evaluation for a seamless migration to Azure.

- **Set up your environment on Azure to migrate servers:** Develop a migration assessment and configure dependency visualization to facilitate seamless system transition and dependency analysis for seamless server migration. This includes preparing the discovered on-premises servers, configuring necessary permissions, deploying tools, and ensuring connectivity between the on-premises infrastructure and Azure.

- **Perform database assessments:** Use the Azure SQL Migration extension in Azure Data Studio to assess the on-premises database named WideWorldImporters for Azure readiness. Evaluate performance metrics, compatibility issues, and dependencies to create a comprehensive migration strategy that ensures a smooth transition to the Azure platform.

## Prerequisites

Participants should have:

- Familiarity with Azure services, including Azure Migrate, Azure Data Studio, and Azure SQL solutions.
- Experience with network configuration and enabling outbound connectivity for tools like Azure Migrate Appliance.
- Basic knowledge of database management, SQL Server architecture, and backup processes.
- Understanding of assessment and migration workflows for servers and databases to Azure environments.

## Architecture

The lab architecture involves integrating on-premises infrastructure with Azure to enable the discovery and assessment of Windows Servers and SQL Server databases. The Azure Migrate Appliance, deployed on-premises, acts as the key component for discovering and collecting metadata about servers and databases. This data is securely transmitted to an Azure Migrate project, which facilitates assessments to evaluate migration readiness. The architecture also includes Azure Data Studio for database assessments, leveraging its SQL Server Migration extension to analyze database compatibility with Azure SQL solutions. Azure resources, such as resource groups and Azure SQL databases, are set up to act as the target environment, ensuring a seamless workflow from discovery to assessment while maintaining data integrity and security.

## Architecture Diagram

![](./Images/architecture.png)

## Explanation of Components

- **Azure Migrate Appliance:** A virtual appliance deployed in the on-premises environment. It connects to on-premises servers, collects metadata (such as server configurations, performance metrics, and database details), and securely sends this data to Azure for analysis.

- **Azure Migrate Project:** A centralized service in the Azure portal that organizes and manages the discovery, assessment, and migration workflows. It processes data from the Azure Migrate Appliance to generate readiness reports and migration plans.

- **Windows Servers (On-Premises):** These are the source servers where applications and workloads run. They are the primary targets for discovery, assessment, and eventual migration to Azure.

- **SQL Server Instances (On-Premises):** On-premises SQL databases that store business-critical data. They are analyzed for compatibility, performance, and potential issues before being migrated to Azure SQL solutions.

- **Azure Data Studio:** A lightweight, cross-platform database tool used for managing SQL databases. It provides features for assessing database compatibility with Azure SQL solutions and assists in schema and data migration.

- **SQL Server Migration Extension (in Azure Data Studio):** An extension in Azure Data Studio specifically designed for assessing SQL Server instances. It generates compatibility reports, identifies potential migration blockers, and facilitates schema and data migration to Azure SQL.

## Getting started with the lab

 We've prepared a seamless environment for you to explore and learn about Azure services. Let's begin by making the most of this experience:

## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.

![](./Images/lab-guide(1).png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.

![](./Images/env1-2009.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
![](./Images/split-2009.png)
 
## Managing Your Virtual Machine
 
Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
![](./Images/resources-2009.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![Manage Your Virtual Machine](./Images/labzoom-1.png)
   
## Login to Azure Portal
 
1. On your virtual machine, click on the Azure Portal icon as shown below:
 
   ![](./Images/GS1.png)
 
2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
     ![](./Images/GS2.png)
 
3. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
     ![](./Images/GS3.png)
 
4. If you see the pop-up **Stay Signed in?**, click **No**.

   ![](./Images/stay-signedin-2009.png)

5. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

6. If a **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.
 
## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:
- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

![](./Images/next-page-2009.png)

### Happy Learning!!
