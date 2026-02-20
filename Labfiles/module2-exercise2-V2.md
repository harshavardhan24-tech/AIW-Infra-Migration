# HOL 2: Exercise 2: Set up your environment on Azure to Migrate Servers (Optional)

### Estimated duration: 40 Minutes

## Overview
In this exercise, you will learn how to migrate machines as physical servers to Azure, using the Azure Migrate: Server Migration tool. Migrating machines by treating them as physical servers is useful in several scenarios, such as migrating on-premises physical servers, migrating Hyper-V VMs, and much more.

## Objectives

In this exercise, you will complete the following task:

- Task 1: Configure dependency visualization

### Task 1: Configure dependency visualization

When migrating a workload to Azure, it is important to understand all workload dependencies. A broken dependency could mean that the application doesn't run properly in Azure, perhaps in hard-to-detect ways. Some dependencies, such as those between application tiers, are obvious. Other dependencies, such as DNS lookups, Kerberos ticket validation, or certificate revocation checks, are not.

In this task, you will configure the Azure Migrate dependency visualization feature. This requires you to first create a Log Analytics workspace and then deploy agents on the to-be-migrated VMs.

1. Return to the **Azure portal**, and navigate to **Azure Migrate | Servers, databases and web apps** page in the Azure Portal, expand **Migration goals (1)** on the left menu and select **Servers, databases and web apps (2)**. Under **Azure Migrate: Discovery and assessment** select **Groups (3)**.

    ![](Images/15-7-25-l6-1.png)   

1. On the **Azure Migrate: Discovery and assessment | Groups** page, expand **Manage (1)**, select **Groups (2)** from the left menu. Then click on the **SmartHotel VMs (3)** group to view the group details. 

    ![](Images/15-7-25-l6-2.png)  

1. On **SmartHotel VMs**. Note that each VM has its **Dependencies** status as **Requires agent installation**. Select **Requires agent installation** for the **redhat** VM.

    ![Screenshot showing the SmartHotel VMs group. Each VM has dependency status 'Requires agent installation'.](Images/upd-hol2-e2-s3.png "SmartHotel VMs server group")

1. On the **Dependencies** page of the **SmartHotel VMs** group, scroll down and copy the **Workspace ID (1)** and **Primary Key (2)** by clicking on the copy icon next to each field.

    ![](Images/L1E2T2S6-3012.png)

1. You will now deploy the Linux versions of the Microsoft Monitoring Agent and Dependency Agent on the **redhat** VM. To do so, you will first connect to the Red Hat VM remotely using an SSH session.

1. On the LabVM desktop, double-click the Command Prompt shortcut to open a terminal window
    
      ![](Images/15-7-25-l2-27.png)
  
1. Enter the following command to connect to the **redhat** VM running in Hyper-V on the SmartHotelHost:

    ```bash
    ssh administrator@192.168.1.19
    ```

1. Enter 'yes' when prompted **Are you sure you want to continue connecting** and enter the password **<inject key="SmartHotel Admin Password" />**.

    ![Screenshot showing the command prompt with an SSH session to UbuntuWAF.](Images/infra-l7-1.png "SSH session with UbuntuWAF")

1. Enter the following command, followed by the password **<inject key="SmartHotel Admin Password" />** when prompted:
  
    ```
    su
    ```

    > This gives the terminal session elevated privileges.

1. Enter the following command, substituting **\<Workspace ID\> and \<Primary Key\>** with the values copied previously. Answer **Yes** when prompted to restart services during package upgrades without asking.  

    ```
    wget https://raw.githubusercontent.com/Microsoft/OMS-Agent-for-Linux/master/installer/scripts/onboard_agent.sh && sh onboard_agent.sh -w <Workspace ID> -s <Primary Key>
    ```
    > **Note:** Be sure to replace `<Workspace ID>` and `<Primary Key>` with the actual values you copied from the Log Analytics workspace.

1. Enter the following command, substituting **\<Workspace ID\>** with the value copied earlier:

    ```s
    /opt/microsoft/omsagent/bin/service_control restart <Workspace ID>
    ```
    > **Note:** If the above command fails with the error **"ERROR FOUND: file /etc/opt/microsoft/omsagent/conf/omsadmin.conf doesn't exist,"** run the command below, replacing `<WorkspaceID>` and `<PrimaryKey>`, and then repeat the steps starting from Step 11.
    
    ```
    sudo /opt/microsoft/omsagent/bin/omsadmin.sh -w <WorkspaceID> -s <PrimaryKey>
    ```
    
1. Enter the following command. This downloads a script that will install the Dependency Agent.

    ```s
    wget --content-disposition https://aka.ms/dependencyagentlinux -O InstallDependencyAgent-Linux64.bin
    ```

1. Install the dependency agent by running the script downloaded in the previous step.

    ```s
    sh InstallDependencyAgent-Linux64.bin -s
    ```

    ![Screenshot showing that the Dependency Agent install on Linux was successful.](Images/infra-l7-2.png "Dependency Agent installation was successful")
    

1. Return to the Azure Portal and refresh the Azure Migrate **SmartHotel VMs** VM group blade. The Red Hat VM on which the dependency agent was installed should now show its status as **Installed**. (If not, refresh the page **using the browser refresh button**, not the refresh button in the blade.  It may take up to **5 minutes** after installation for the status to be updated.)

    ![](Images/15-7-25-l6-l6.png "Dependency agent installed")
   
    >**Note**: If you notice that the dependency agent status is showing as **Requires Agent Installation** instead of Installed even after installing dependency agents in all three VMs, please follow the steps from [here](https://github.com/CloudLabsAI-Azure/Know-Before-You-Go/blob/main/AIW-KBYG/AIW-Infrastructure-Migration.md#4-exercise1---task6---step1) to confirm dependency agent installation in VMs using Log Analytics workspace.
 
1. On the **SmartHotel VMs** group page, click **View dependencies** to visualize VM interconnections and traffic flows.

    ![Screenshot showing the view dependencies button in the Azure Migrate VM group blade.](Images/upd-view-dependencies.png "View dependencies")
   
1. Take a few minutes to explore the dependencies view. Expand each server to show the processes running on that server. Select a process to see the process information. See which connections each server makes.

    ![Screenshot showing the dependencies view in Azure Migrate.](Images/upd-dependencies1.png "Dependency map")
 
## Summary 

In this exercise, you configured the Azure Migrate dependency visualization feature by creating a Log Analytics workspace and deploying the Azure Monitoring Agent and Dependency Agent on a Linux on-premises machine.

Click on **Next** from the lower right corner to move on to the next page.

![](Images/infra-s7.png)
