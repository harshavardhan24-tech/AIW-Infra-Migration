
# Infrastructure Migration 

### Overall Estimated Duration: 8 Hours

In this hands-on lab, you will migrate and modernize workloads to Azure. You will start by evaluating and migrating Windows and SQL Server workloads using Azure Migrate and Azure Site Recovery. Next, you will replicate and migrate a Red Hat VM and OSS DB workloads, enable Entra ID-based authentication, and connect to Azure Automanage. 

Finally, you will manage a Windows machine with Azure Arc,strengthened monitoring and security by enabling Microsoft Defender for Cloud, Microsoft Sentinel, Azure Monitor, and a Log Analytics workspace for centralized visibility.

### Key Features of Infrastructure Migration to Azure

- **Seamless Workload Migration:** Migrate Windows, SQL Server, Linux, and open-source database workloads using Azure Migrate and Azure Site Recovery (ASR). This ensures efficient and secure movement of applications and data from on-premises or other clouds to Azure.

- **Comprehensive Pre-Migration Setup:** Set up your Azure environment with appropriate networking, resource groups, and migration tools. Leverage built-in guidance to ensure your infrastructure is ready for server migration and modernization.

- **Holistic Application and Data Migration:** Use Azure Migrate: Server Migration and tools like the Azure Hybrid Benefit to transition apps and databases with minimal downtime. This includes end-to-end support for migrating application configurations, databases, and dependencies.

- **Optimization of Migrated Workloads:** Post-migration, optimize workloads for performance, cost, and security. Azure tools identify inefficiencies and enable scaling, resource rightsizing, and implementation of best practices across all stacks.

- **Modernization of Linux and OSS Databases:** Leverage Azure's tailored solutions to modernize Linux workloads and open-source databases. Azure ensures compatibility and provides support for scaling and optimizing these environments.

- **Hybrid Cloud Enablement with Azure Arc:** Extend Azure management capabilities to on-premises servers using Azure Arc-enabled server. This enables centralized monitoring, policy enforcement, and management for hybrid environments.

- **Integrated Security and Monitoring:** Enable Microsoft Defender for Cloud, Microsoft Sentinel, and Azure Monitor to safeguard workloads post-migration. Integrate with Log Analytics for real-time insights and threat detection across your environment.

- **Unified Management and Automation:** Use Azure's centralized platform to manage all migrated workloads, automate processes, and apply consistent governance, security, and compliance across your infrastructure.

## Overview

The following lab provide you with a quick and easy way to get started with Azure Migrate through on-premises environments that do not require any complex setup or installations. 

For the purposes of these Hands-on Labs (HOLs), let’s consider that SmartHotel is a large hotel company. 

Their IT systems run Windows, Linux, SQL Servers, and MySQL across on-premises data centers, distribution centers, and multiple public clouds. This poses operational challenges for SmartHotel. They’d like a consistent way to govern and operate across these disparate environments, ensure security across the entire organization, and enable innovation and developer agility, all while meeting regulatory and compliance requirements and being able to leverage the latest innovations of database technologies.

## Objectives

- **Evaluate and Plan Migration:** Assess your current environment using Azure Migrate, create migration assessments, and configure dependency visualization to ensure a smooth transition.

- **Set Up Azure Environment:** Prepare Azure for migration by creating storage accounts, registering Hyper-V hosts, enabling replication, and configuring networking.

- **Migrate Workloads:** Use Azure Migrate and Azure Site Recovery to migrate Windows, SQL Server, Linux, and OSS DB workloads, ensuring minimal downtime and leveraging Azure's scalability.

- **Security:** Enhance security with Microsoft Defender for Cloud, Microsoft Sentinel, and Azure Monitor. 

## Pre-requisites

- **Access to Azure Environment:** An active Azure subscription with necessary permissions to deploy and configure resources, including enabling Azure Migrate and Azure Site Recovery (ASR).  

- **Familiarity with Azure Services and Migration Tools:** Basic understanding of Azure concepts, resource management, and migration tools like Azure Migrate, Azure Hybrid Benefit, and ASR to ensure seamless migration.  

- **Technical Environment Preparation:** Prepared on-premises environment with necessary agents installed, server discovery enabled, and application compatibility assessed for migration readiness.  

## Architecture

The architecture diagram outlines a series of labs focused on migrating workloads to Azure, configuring Azure services, and leveraging Microsoft tools for optimization and monitoring. The labs begin with migrating Windows, SQL Server, Linux, and OSS database workloads, setting up environments for migration, and utilizing tools like Azure Migrate and the Azure Hybrid Benefit to transition applications and data. Users then onboard on-premises servers to Azure Arc-enabled, migrate infrastructure to Azure. The sequence continues with enabling Microsoft Defender for Cloud, Sentinel, and Azure Monitor while setting up log analytics for security and monitoring, offering a comprehensive understanding of Azure migration, optimization, and security operations.

## Architecture Diagram

![A slide shows the on-premises SmartHotel application architecture.](Images/gettingstartedarch.png)

## Explanation of Components  

- **Azure Migrate:** A centralized hub for discovering, assessing, and migrating on-premises servers, applications, and databases to Azure. It simplifies migration planning and execution by providing tools for workload analysis, cost estimation, and seamless migration.  

- **Azure Arc:** Enables on-premises servers and other non-Azure resources to integrate with Azure's management tools, allowing organizations to manage, secure, and govern resources across hybrid environments through a unified Azure interface.  

- **Microsoft Defender for Cloud:** A security management tool that provides visibility and protection for workloads running in Azure, on-premises, and other cloud platforms. It helps detect threats, manage security posture, and ensure compliance.  

- **Microsoft Sentinel:** A cloud-native security information and event management (SIEM) and security orchestration, automated response (SOAR) solution that aggregates security data, detects threats, and enables incident response through playbooks and analytics.  

- **Azure Monitor:** A service that collects, analyzes, and acts on telemetry data from Azure resources, on-premises environments, and other clouds, providing insights into the performance and health of applications and infrastructure.  

- **Log Analytics:** A tool within Azure Monitor that enables querying and analyzing log data from Azure resources to gain insights, troubleshoot issues, and improve operational efficiency.  

- **Azure Hybrid Benefit:** A licensing benefit that helps organizations reduce costs when migrating workloads to Azure by allowing them to use existing on-premises licenses for Windows Server and SQL Server in the cloud.  

## Getting Started with the Lab

We've prepared a seamless environment for you to explore and learn about Azure services. Let's begin by making the most of this experience!

## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.

![](./Images/Infra-g2.png)

## Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment Details** tab.

   ![](./Images/14-7-25-g2.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
   ![](./Images/14-7-25-g3.png)
 
## Managing Your Virtual Machine
 
Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
  ![](./Images/14-7-25-g4.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![](./Images/14-7-25-g5.png) 

## **Let's Get Started with Azure Portal**
 
1. On your virtual machine, click on the **Azure Portal** icon as shown below:
 
    ![](./Images/infra-new1.png)
 
2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
      ![](Images/AIM-image1.png)
 
3. Next, provide your password:
 
   - **Temporary Access Pass:** <inject key="AzureAdUserPassword"></inject>
 
      ![](Images/AIM-image2.png)
 
4. If you see the pop-up **Stay Signed in?**, click **No**.

   ![](Images/AIM-image3.png)

5. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

     ![](Images/Infra-g4.png)

6. From the **Azure Portal** Dashboard, under the Navigate section, click **Resource groups** to view all the resource groups.

   ![](Images/Infra-g1.png)

   >**Note:** If you see pop-up notification to **Restore pages**, please close it.
   
7. On the **Resource groups** page in the Azure portal, confirm you have all resource groups present as shown below.

   ![](Images/Infra-g3.png)

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

![](Images/infra-s7.png)

## Happy Learning!!
