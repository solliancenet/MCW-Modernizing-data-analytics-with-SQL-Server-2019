![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Modernizing data analytics with SQL Server 2019
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
June 2019
</div>


Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2019 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Modernizing data analytics with SQL Server 2019 before the hands-on lab setup guide](#Modernizing-data-analytics-with-SQL-Server-2019-before-the-hands-on-lab-setup-guide)
  - [Requirements](#Requirements)
  - [Regional limitations](#Regional-limitations)
  - [Before the hands-on lab](#Before-the-hands-on-lab)
    - [Task 1: Provision lab VM](#Task-1-Provision-lab-VM)
    - [Task 2: (Optional) Install software on your own VM or system](#Task-2-Optional-Install-software-on-your-own-VM-or-system)
    - [Task 3: Download lab files](#Task-3-Download-lab-files)
    - [Task 4: Install SQL Server 2019 Big Data clusters](#Task-4-Install-SQL-Server-2019-Big-Data-clusters)

<!-- /TOC -->

# Modernizing data analytics with SQL Server 2019 before the hands-on lab setup guide

## Requirements

1. Microsoft Azure subscription must be pay-as-you-go or MSDN.
   - Trial subscriptions will not work.
2. PowerShell
3. Python3
4. Curl
5. [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)
6. [mssqlctl](https://docs.microsoft.com/en-us/sql/big-data-cluster/deploy-install-mssqlctl?view=sql-server-ver15)
7. [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery)
8. [SQL Server Management Studio](https://go.microsoft.com/fwlink/?linkid=2078638) (SSMS) v18.0 or greater
9. [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-ver15)
   - [SQL Server 2019 extension](sql-vnext-0.10.2-win-x64.vsix)

## Regional limitations

**L Series VMs** (required for SQL 2019 Big Data Clusters): East US 2, West US, West US 2, and a limited set of others worldwide

**Azure Machine Learning service**: East US, East US 2, West US 2, West Central US, South Central US, and a limited set of others worldwide

## Before the hands-on lab

Duration: 30 minutes

### Task 1: Provision lab VM

For this lab, you will use a custom lab VM that comes preconfigured with all the required software.

TODO: Add instructions to provision from custom image.

### Task 2: (Optional) Install software on your own VM or system

If you are not using the provided lab VM, follow these instructions to install the required software.

The instructions that follow are the same for either your own system (desktop or laptop), or a Virtual Machine. It's best to have at least 4MB of RAM on the management system, and these instructions assume that you are not planning to run the database server or any Containers on the workstation. It's also assumed that you are using a current version of Windows, either desktop or server.

_(You can copy and paste all of the commands that follow in a PowerShell window that you run as the system Administrator)_

1. Ensure your system updates are current. Run from an Administrator-level PowerShell session (if running on a VM, you may safely ignore errors).

    ```powershell
    write-host "Standard Install for Windows. Classroom or test system only - use at your own risk!"
    Set-ExecutionPolicy RemoteSigned

    write-host "Update Windows"
    Install-Module PSWindowsUpdate
    Import-Module PSWindowsUpdate
    Get-WindowsUpdate
    Install-WindowsUpdate
    ```

2. Install Chocolatey Windows package Manager.

    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
    choco feature enable -n allowGlobalConfirmation
    ```

3. Install Azure CLI.

    ```powershell
    choco install azure-cli
    ```

4. Install Python 3.

    ```powershell
    choco install python3
    ```

5. Install git.

    ```powershell
    choco install git
    ```

6. Install kubectl.

    ```powershell
    choco install kubernetes-cli
    ```

7. Install Azure Data Studio.

    ```powershell
    choco install azure-data-studio
    ```

8. Install curl.

    ```powershell
    choco install curl
    ```

9. Run the following commands separately in a new Command Prompt window.

    ```bash
    REM setx path "%path%;C:\Users\\AppData\Roaming\Python\Python37\Scripts"
    ```

    ```bash
    choco upgrade kubernetes-cli
    ```

    ```bash
    python -m pip install --upgrade pip
    ```

    ```bash
    pip3 install -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
    ```

10. Install [SQL Server Management Studio](https://go.microsoft.com/fwlink/?linkid=2078638) (SSMS) v18.0 or greater.

11. Install the [SQL Server 2019 extension](sql-vnext-0.10.2-win-x64.vsix).

### Task 3: Download lab files

Download a starter project that includes a payment data generator that sends real-time payment data for processing by your lab solution, as well as data files used in the lab.

1. From your LabVM, download the starter files by downloading a .zip copy of the Cosmos DB real-time advanced analytics GitHub repo.

2. In a web browser, navigate to the [Cosmos DB real-time advanced analytics MCW repo](https://github.com/solliancenet/MCW-Modernizing-data-analytics-with-SQL-Server-2019). TODO: UPDATE URL

3. On the repo page, select **Clone or download**, then select **Download ZIP**.

   ![Download .zip containing the repository](media/github-download-repo.png 'Download ZIP')

4. Unzip the contents to your root hard drive (i.e. `C:\`). This will create a folder on your root drive named `MCW-Modernizing-data-analytics-with-SQL-Server-2019-master`.

### Task 4: Install SQL Server 2019 Big Data clusters

Open PowerShell and execute the following to deploy the clusters in preparation for the lab.

1.  Before running the script, you must log in to your Azure account with Azure CLI at least once.

    ```bash
    az login
    ```

2. If you have multiple subscriptions, choose the appropriate subscription in which the resource should be billed. List all your subscriptions by entering the following into the shell:

   ```bash
   az account list
   ```

3. Select the specific subscription ID under your account using `az account set` command. Copy the `id` value from the output of the previous command for the subscription you wish to use into the `subscription id` placeholder:

   ```bash
   az account set --subscription <subscription id>
   ```

4.  Use the following steps to run the deployment script. This script will create an AKS service in Azure and then deploy a SQL Server 2019 big data cluster to AKS. The [deploy-sql-big-data-aks.py](deploy-sql-big-data-aks.py) script located in this folder is customized with environment variables that set the memory allocation for the cluster.

    > **Please note:** this script can take up to 30 minutes to complete.

    ```bash
    python deploy-sql-big-data-aks.py
    ```

5.  When prompted, enter the following information:

    | Value                     | Description                                                                                                                                                                                            |
    | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | **Azure subscription ID** | The Azure subscription ID to use for AKS. You can list all of your subscriptions and their IDs by running `az account list` from another command line.                                                 |
    | **Azure resource group**  | The Azure resource group name to create for the AKS cluster. (suggest **tech-immersion**)                                                                                                              |
    | **Docker username**       | The Docker username provided to you as part of the limited public preview.                                                                                                                             |
    | **Docker password**       | The Docker password provided to you as part of the limited public preview.                                                                                                                             |
    | **Azure region**          | The Azure region for the new AKS cluster (default **westus**).                                                                                                                                         |
    | **Machine size**          | Set to **Standard_L8s**.                                                                                                                                                                               |
    | **Worker nodes**          | Set the number of worker nodes in the AKS cluster to **3**.                                                                                                                                            |
    | **Cluster name**          | Enter a **unique name for the student**. This sets the name of both the AKS cluster and the big data cluster. The name of the cluster must be only lower case alpha-numeric characters, and no spaces. |
    | **Password**              | Password for the controller, HDFS/Spark gateway, and master instance (default **MySQLBigData2019**).                                                                                                   |
    | **Controller user**       | Username for the controller user (default: **admin**).                                                                                                                                                 |

    You can run the following at any time to get the status of the cluster:

    ```bash
    kubectl get all -n <your-cluster-name>
    ```

6.  When the cluster is done deploying, you will see an output of the various IP addresses for the cluster. **Copy the SQL Server Master Instance and HDFS/KNOX values** and save them to a text file that the students can use for reference.

    Example:

    - SQL Server master instance:
      - IP
        - 52.179.172.24
      - PORT
        - 31433
    - HDFS/KNOX:
      - IP
        - 52.167.114.239
      - PORT
        - 30443

You should follow all steps provided *before* performing the Hands-on lab.

