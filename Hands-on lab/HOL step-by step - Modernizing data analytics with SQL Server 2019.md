![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
Modernizing data analytics with SQL Server 2019
</div>

<div class="MCWHeader2">
Hands-on lab step-by-step
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

- [Modernizing data analytics with SQL Server 2019 hands-on lab step-by-step](#Modernizing-data-analytics-with-SQL-Server-2019-hands-on-lab-step-by-step)
  - [Abstract and learning objectives](#Abstract-and-learning-objectives)
  - [Overview](#Overview)
  - [Solution architecture](#Solution-architecture)
  - [Requirements](#Requirements)
  - [Before the hands-on lab](#Before-the-hands-on-lab)
    - [Connect with Azure Data Studio](#Connect-with-Azure-Data-Studio)
    - [Connect with SQL Server Management Studio](#Connect-with-SQL-Server-Management-Studio)
  - [Exercise 1: Using data virtualization](#Exercise-1-Using-data-virtualization)
    - [Task 1: Create external table from Azure SQL Database](#Task-1-Create-external-table-from-Azure-SQL-Database)
    - [Task 2: Create external table from CSV files](#Task-2-Create-external-table-from-CSV-files)
    - [Task 3: Query and join data from flat files, data from external database systems, and SQL Server](#Task-3-Query-and-join-data-from-flat-files-data-from-external-database-systems-and-SQL-Server)
  - [Exercise 2: Using notebooks](#Exercise-2-Using-notebooks)
    - [Task 1: Introduction to Jupyter notebooks](#Task-1-Introduction-to-Jupyter-notebooks)
    - [Task 2: Querying the SQL Server Master Instance (MI)](#Task-2-Querying-the-SQL-Server-Master-Instance-MI)
    - [Task 3: Virtualizing data with scripts](#Task-3-Virtualizing-data-with-scripts)
    - [Task 4: Creating and querying a Data Mart](#Task-4-Creating-and-querying-a-Data-Mart)
    - [Task 5: Using the powerful Spark engine for data exploration](#Task-5-Using-the-powerful-Spark-engine-for-data-exploration)
  - [Exercise 3: Machine learning](#Exercise-3-Machine-learning)
    - [Task 1: Train a machine learning model](#Task-1-Train-a-machine-learning-model)
    - [Task 2: Score and save data as an external table](#Task-2-Score-and-save-data-as-an-external-table)
  - [Task 3: Mounting an Azure Data Lake Gen2 Storage Account to SQL Server 2019 Big Data Cluster using HDFS Tiering](#Task-3-Mounting-an-Azure-Data-Lake-Gen2-Storage-Account-to-SQL-Server-2019-Big-Data-Cluster-using-HDFS-Tiering)
  - [Exercise 4: Identify PII and GDPR-related compliance issues using Data Discovery & Classification in SSMS](#Exercise-4-Identify-PII-and-GDPR-related-compliance-issues-using-Data-Discovery--Classification-in-SSMS)
    - [Task 1: Use the Data Discovery & Classification in SSMS](#Task-1-Use-the-Data-Discovery--Classification-in-SSMS)
    - [Task 2: Fix compliance issues with dynamic data masking](#Task-2-Fix-compliance-issues-with-dynamic-data-masking)
  - [Exercise 5: Exploring intelligent query processing (QP) features](#Exercise-5-Exploring-intelligent-query-processing-QP-features)
    - [Task 1: Set database compatibility level](#Task-1-Set-database-compatibility-level)
    - [Task 2: Scalar UDF inlining](#Task-2-Scalar-UDF-inlining)
    - [Task 3: Table variable deferred compilation](#Task-3-Table-variable-deferred-compilation)
    - [Task 4: Row mode memory grant feedback](#Task-4-Row-mode-memory-grant-feedback)
  - [Exercise 6: Monitoring the big data cluster](#Exercise-6-Monitoring-the-big-data-cluster)
    - [Task 1: Use the cluster administration portal](#Task-1-Use-the-cluster-administration-portal)
    - [Task 2: Monitor and troubleshoot using Kubectl commands](#Task-2-Monitor-and-troubleshoot-using-Kubectl-commands)
  - [After the hands-on lab](#After-the-hands-on-lab)
    - [Task 1: Delete the resource group](#Task-1-Delete-the-resource-group)

<!-- /TOC -->

# Modernizing data analytics with SQL Server 2019 hands-on lab step-by-step

## Abstract and learning objectives

\[Insert what is trying to be solved for by using this workshop. . . \]

## Overview

\[insert your custom workshop content here . . . \]

## Solution architecture

\[Insert your end-solution architecture here. . .\]

## Requirements

1.  Number and insert your custom workshop content here . . .

## Before the hands-on lab

Refer to the Before the hands-on lab setup guide manual before continuing to the lab exercises.

Follow the steps below to connect to your SQL Server 2019 cluster with both Azure Data Studio and SQL Server Management Studio (SSMS).

### Connect with Azure Data Studio

1. On the bottom-left corner of your Windows desktop, locate the search box next to the Start Menu. Type **Azure Data Studio**, then select the Azure Data Studio desktop app in the search results.

   ![The search box has "Azure Data Studio" entered into it and the desktop app is highlighted in the results.](media/launch-azure-data-studio.png 'Launch Azure Data Studio')

2. Within Azure Data Studio, if the Connection dialog isn't automatically displayed, select **Servers** from the top of the left-hand menu, then select **New Connection** from the top toolbar to the right of the menu.

   ![The Servers menu icon is selected, as well as the new connection icon.](media/ads-new-connection-link.png 'Azure Data Studio')

3. Within the Connection dialog, configure the following:

   - **Connection type:** Select Microsoft SQL Server.
   - **Server:** Enter the IP address, followed by port number `31433` to the SQL Server 2019 Big Data cluster. It should have a format of IP separated by a comma from the port, such as: `11.122.133.144,31433`.
   - **Authentication type:** Select SQL Login.
   - **Username:** Enter `sa`.
   - **Password:** Enter the password you used when creating the cluster. The default value is **MySQLBigData2019**.
   - **Remember password:** Checked.
   - Leave all other options at their default values.

   ![The Connection form is filled out with the previously mentioned settings entered into the appropriate fields.](media/ads-new-connection.png 'Azure Data Studio - New Connection')

4. Click **Connect**.

### Connect with SQL Server Management Studio

1. On the bottom-left corner of your Windows desktop, locate the search box next to the Start Menu. Type **SQL Server Management Studio**, then select the SQL Server Management Studio desktop app in the search results.

   ![The search box has "SQL Server Management Studio" entered into it and the desktop app is highlighted in the results.](media/launch-ssms.png 'Launch SQL Server Management Studio')

2. Within the Connection dialog that appears, configure the following:

   - **Server name:** Enter the IP address, followed by port number `31433` to the SQL Server 2019 Big Data cluster. It should have a format of IP separated by a comma from the port, such as: `11.122.133.144,31433`.
   - **Authentication:** Select SQL Server Authentication.
   - **Login:** Enter `sa`.
   - **Password:** Enter the password you used when creating the cluster. The default value is **MySQLBigData2019**.
   - **Remember password:** Checked.

   ![The Connect form is filled out with the previously mentioned settings entered into the appropriate fields.](media/ssms-connection.png 'SQL Server Management Studio - Connect')

3. Click **Connect**.

## Exercise 1: Using data virtualization

One of the key new features of SQL Server 2019 is data virtualization. What this means is that you can _virtualize_ external data in a SQL Server instance, regardless of source, location, and format, so that it can be queried like any other table, or sets of tables, within your SQL Server instance. In essence, data virtualization helps you create a single "virtual" layer of data from these disparate sources, providing unified data services to support multiple applications and users. A more familiar term we could use is data lake, or perhaps data hub. Unlike a typical data lake, however, you do not have to move data out from where it lives, yet you can still query that data through a consistent interface. This is a huge advantage over traditional ETL (extract-transform-load) processes where data must be moved from its original source to a new destination, oftentimes with some data transformation or mapping. This causes delays, extra storage, additional security, and a fair amount of engineering in most cases. With data virtualization, no data movement is required, which means the data sets are up-to-date, and it is possible to query and join these different data sources through these new capabilities, thanks to the use of new [PolyBase](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide?view=sql-server-ver15) connectors. The data sources you can connect to include Cosmos DB, SQL Server (including Azure SQL Database), Oracle, HDFS (for flat files), and DB2.

![Data Virtualization compared to traditional ETL.](media/data-virtualization-vs-etl.png 'ETL vs. Data Virtualization')

The image to the left represents traditional data movement using ETL. Compare that to data virtualization, which does not require data movement and provides a unified layer over top of existing data sources.

In this task, you will experience how to configure data virtualization in SQL Server 2019 by joining data in a single query from a SQL Server 2019 table, an external file stored in HDFS (Hadoop Filesystem), and an external database.

Learn more about using data virtualization with [relational data sources](https://docs.microsoft.com/sql/relational-databases/polybase/data-virtualization?toc=%2fsql%2fbig-data-cluster%2ftoc.json&view=sql-server-ver15) and [CSV files](https://docs.microsoft.com/sql/relational-databases/polybase/data-virtualization-csv?view=sql-server-ver15), using the External Table Wizard.

<!-- ### Task 1: Query and join data from flat files, data from external database systems, and SQL Server -->

### Task 1: Create external table from Azure SQL Database

To start, we will use the External Table Wizard in Azure Data Studio to connect to an external Azure SQL Database.

1. Open Azure Data Studio and connect to your SQL Server 2019 cluster, following the [connection steps](#connect-with-azure-data-studio) above.

2. Expand the Databases folder, right-click on the **sales** database, then select **Create External Table**.

   ![The sales database and the Create External Table sub-menu item are highlighted.](media/ads-create-external-table-sales.png 'Create External Table')

3. Select the **SQL Server** data source type, then click **Next**.

   ![The SQL Server data source type is selected.](media/ads-external-table-wizard-data-source-type.png 'Select data source type')

4. The next step is to create a database master key, if it does not already exist. This secures the credentials used by an external data source. Enter `MySecure@MasterKey1` in the **Password** and **Confirm Password** fields. If you see a message stating that a master key already exists, you may skip this step. Click **Next**.

   ![The Master Key step is displayed.](media/ads-external-table-wizard-master-key.png 'Master Key')

5. Now, enter the credentials provided to you for the **CA_Commerce** Azure SQL Database within the following fields:

   - **External Data Source Name:** Enter the string "SQLReviews".
   - **Server Name:** Enter the value of the Azure SQL Server name for the server you created when you provisioned the Azure SQL Database. The name should end with `.database.windows.net`.
   - **Database Name:** Enter "WWI_Commerce".
   - **Choose Credential:** Select "-- Create New Credential --".
   - **New Credential Name:** Enter "SQLCred".
   - **Username:** Enter the Azure SQL Server username (such as **ServerAdmin**).
   - **Password:** Enter the Azure SQL Server password (such as **MySQLBigData2019**).

   ![The external data source connection form is filled out with the previously mentioned settings entered into the appropriate fields.](media/ads-external-table-wizard-data-source.png 'Create a connection to your Data Source')

6. Click **Next**. This process will take a few moments while the External Table Wizard attempts to connect to your data source.

7. The next screen allows you to configure external table mapping and select the tables for which you want to create external views. Expand the **WWI_Commerce** database node, then expand Tables, and check the box next to the **dbo.Reviews** table. Click on the table name to highlight it as well. It is here where you can rename the external table if you wish. For now, just click **Next**.

   ![The external tables are listed and the Reviews table is checked and selected.](media/ads-external-table-wizard-table-mapping.png 'External tables')

8. In the Summary page that follows, you can see the name of the database scoped credential and external data source objects to be created in the destination database. Here you can click Generate Script to view the SQL script that will run to create the external table. Instead, click **Create**.

   ![A screenshot of the summary is displayed.](media/ads-external-table-wizard-summary.png 'Summary')

9. After a few moments, a "Create External Table succeeded" message will display.

   ![The Create External Table succeeded message is displayed.](media/ads-external-table-wizard-succeeded.png 'Create External Table succeeded message')

10. Select the Servers link (Ctrl+G) on the left-hand menu, then expand the Tables list underneath your **sales** database and find the **dbo.Reviews (External)** table. If you do not see it, right-click on the Tables folder, then select Refresh. The "(External)" portion of the table name denotes that it is a virtual data object that was added as an external table.

    ![The Reviews external table is displayed in the sales tables list.](media/ads-reviews-table-in-list.png 'Reviews external table')

11. Right-click the **dbo.Reviews (External)** table, then select the **Select Top 1000** menu option to display the table contents.

    ![The Select Top 1000 rows menu item is highlighted.](media/ads-reviews-select-top-1000.png 'Select Top 1000')

12. You should see a SQL query selecting the top 1000 records from the Reviews table and its results. The interesting thing to note is that the query selects the table and fields using the same syntax you would use to select from any other table in the sales database. The fact that the Reviews table is external is completely seamless and transparent to the user. This is the power of data virtualization in SQL Server 2019.

    ![The Reviews query and results are displayed.](media/ads-reviews-query-results.png 'Reviews query results')

    ```sql
    SELECT TOP (1000) [product_id]
        ,[customer_id]
        ,[review]
        ,[date_added]
    FROM [sales].[dbo].[Reviews]
    ```

### Task 2: Create external table from CSV files

The next data source we will be virtualizing is a CSV file that you will upload to HDFS.

1. Within Azure Data Studio, scroll down below the list of SQL Server 2019 databases to find the **Data Services** folder. Expand that folder, then **right-click** on the **HDFS** folder. Select **New Directory**.

   ![The HDFS foler is highlighted and the context menu is displayed.](media/ads-hdfs-new-directory.png 'New directory')

2. In the dialog that appears, type **data** then press 'Enter' to confirm.

3. **Right-click** on the new **data** folder, then select **Upload files**.

   ![The new data folder is highlighted and the context menu is displayed.](media/ads-data-upload-files-link.png 'Upload files')

4. In the folder browser dialog, navigate to the `C:\MCW-Modernizing-data-analytics-with-SQL-Server-2019-master\Hands-on lab\Resources` folder and select **stockitemholdings.csv**.

   ![The file browser is displayed.](media/ads-open-stockitemholdings.png 'Open')

5. Click **Upload**.

6. Expand the **data** subfolder you created, then right-click on the `stockitemholdings.csv` file and select **Create External Table From CSV Files**.

   ![The CSV file and the Create External Table From CSV Files menu item are highlighted.](media/ads-create-external-table-csv.png 'Create External Table From CSV Files')

7. In the Create External Table from CSV dialog, confirm that the **sales** database is selected and that the name of the external table is **stockitemholdings**.

   ![The previously mentioned form is displayed.](media/ads-external-table-csv-wizard-active-connection.png 'Active SQL Server connections')

8. Click **Next**.

9. The next step displays a preview of the first 50 rows CSV data for validation. Click **Next** to continue.

   ![A preview of the CSV data is displayed.](media/ads-external-table-csv-preview.png 'Preview Data')

10. In the next step, you will be able to modify the columns of the external table you intend to create. You are able to alter the column name, change the data type, and allow for Nullable rows. For now, leave everything as-is and click **Next**.

    ![The Modify Columns step is displayed.](media/ads-external-table-csv-modify.png 'Modify Columns')

11. Verify that everything looks correct in the Summary step, then click **Create Table**.

    ![The Summary step is displayed.](media/ads-external-table-csv-create.png 'Summary')

12. As with the previous external table you created, a "Create External Table succeeded" dialog will appear under your task history in a few moments. Select the Servers link (Ctrl+G) on the left-hand menu, then expand the Tables list underneath your **sales** database and find the **dbo.stockitemholdings (External)** table. If you do not see it, right-click on the Tables folder, then select Refresh. **Right-click** the **dbo.stockitemholdings (External)** table, then select **Select Top 1000** from the context menu.

    ![The Select Top 1000 rows menu item is highlighted.](media/ads-stockitemholdings-select-top-1000.png 'Select Top 1000')

13. Just as before, you should see a SQL query selecting the top 1000 rows and its query results, this time from the `stockitemholdings` table. Again, the SQL query is the same type of query you would write to select from a table internal to the sales database.

    ![The stockitemholdings query and results are displayed.](media/ads-stockitemholdings-results.png 'Stockitemholdings results')

    ```sql
    SELECT TOP (1000) [StockItemID]
        ,[QuantityOnHand]
        ,[BinLocation]
        ,[LastStocktakeQuantity]
        ,[LastCostPrice]
        ,[ReorderLevel]
        ,[TargetStockLevel]
        ,[LastEditedBy]
        ,[LastEditedWhen]
    FROM [sales].[dbo].[stockitemholdings]
    ```

### Task 3: Query and join data from flat files, data from external database systems, and SQL Server

Now that we have our two external tables added, we will now join those two external tables and two internal tables with a new SQL query to demonstrate how you can seamlessly combine all these data sources without having to copy any files or with separate queries or additional processing of that data.

1. **Right-click** the **sales** database, then select **New Query**.

   ![The sales database and New Query menu item are highlighted.](media/ads-new-query.png 'New Query')

2. Paste the following into the new query window:

   ```sql
   SELECT i.i_item_sk AS ItemID, i.i_item_desc AS Item, c.c_first_name AS FirstName,
     c.c_last_name AS LastName, s.QuantityOnHand, r.review AS Review, r.date_added AS DateReviewed
   FROM dbo.item as i
   JOIN dbo.Reviews AS r ON i.i_item_sk = r.product_id
   JOIN dbo.customer AS c ON c.c_customer_sk = r.customer_id
   JOIN dbo.stockitemholdings AS s ON i.i_item_sk = s.StockItemID
   ```

3. Click the **Run** button above the query window to execute.

   ![The Run button above the query window is highlighted.](media/ads-run.png 'Run')

4. At the bottom of the query window, you will see results that include columns from the four data sources.

   ![Query results from the four data sets.](media/ads-query-results.png 'Query results')

## Exercise 2: Using notebooks

Executable, or interactive, notebooks have a long history in science and academia. Notebooks were traditionally provided by applications such as [MATLAB](https://www.mathworks.com/products/matlab.html) and [Wolfram Mathematica](https://www.wolfram.com/mathematica/) to help scientists, students, professors, and mathematicians create self-documenting notebooks that others can use to reproduce experiments. To accomplish this, notebooks contain a combination of runnable code, output, formatted text, and visualizations. Over the past several years, web-based interactive notebooks have gained popularity with data scientists and data engineers to conduct exploratory data analysis and model training using a number of languages, such as Python, Scala, SQL, R, and others.

One of the most popular notebooks in use today are [Jupyter](http://jupyter.org/) notebooks. This is what SQL Server 2019 Big Data clusters use, and what you will be using in the exercises below.

Notebooks are made up of one or more of cells that allow for the execution of the code snippets or commands within those cells. They store commands and the results of running those commands. If you are used to developing software and applications using your favorite IDE, then you will realize that there are some disadvantages to using notebooks in place of a more traditional development platform. For example, you cannot set breakpoints and run in debug mode, allowing you to step through the code and inspect object and environment states during execution. However, there are many advantages notebooks do provide. They offer an environment that allows for exploration, documentation, collaboration, and visualization. When a data scientist creates and shares it with a colleague, they are sharing notes and insights about the data with access to all of the queries, formulas, visualizations, and models. This enables interactive conversations and further exploration, with simple reproducibility by anyone running the notebook in the same or similar environment, without others needing to know a sequence of shell commands and environment variables known only to the original author. This collaborative knowledge exchange within an easy to share self-contained package is far more valuable than simply sharing a static, final report.

### Task 1: Introduction to Jupyter notebooks

1. In Azure Data Studio, click **File**, then **Open File...**.

2. In the folder browser dialog, navigate to the `C:\MCW-Modernizing-data-analytics-with-SQL-Server-2019-master\Hands-on lab\Resources` folder and select **notebook_00.ipynb**.

   ![The Open File dialog is displayed.](media/ads-open-notebook0.png 'Open File')

3. When the notebook opens, you need to select the **Kernel** you would like to use to run the notebook. Located the **Kernel** dropdown in the toolbar above the notebook, then select **Python 3**.

   ![The Python 3 kernel is selected.](media/ads-notebook-select-kernel.png 'Kernel dropdown')

4. After selecting the Kernel, you may be prompted to install Python for Notebooks components. If you see this, either select **New Python installation** or select **Use existing Python installation**. Select the existing option first and make sure it automatically locates the Python Install Location. If not, then select the first option for a new installation. Click **Install**. This may take **several minutes to complete**.

   ![The dialog is displayed.](media/ads-configure-python-for-notebooks.png 'Configure Python for Notebooks')

   While it is running, you will see the install progress in the **Tasks** tab, and the **Kernel** will display "Changing kernel..." in the dropdown.

   ![The installation status is displayed.](media/ads-configure-python-for-notebooks-running.png 'Tasks')

5. After the Python components are installed, make sure that **Python 3** is your selected **Kernel**, then follow the instructions within the notebook.

### Task 2: Querying the SQL Server Master Instance (MI)

### Task 3: Virtualizing data with scripts

### Task 4: Creating and querying a Data Mart

### Task 5: Using the powerful Spark engine for data exploration

## Exercise 3: Machine learning

In this exercise, you will use Azure Data Studio to execute a notebook that will enable you to train a model to predict the battery lifetime, apply the model to make batch predictions against a set of vehicle telemetry and save the scored telemetry to an external table that you can query using SQL.

<!-- ## Task 2: Train a machine learning model, score and save data as external table -->

### Task 1: Train a machine learning model

1. Open Azure Data Studio and select Servers.

2. Right click your Big Data Cluster node select `Manage`.

   ![Manage cluster](media/task02-manage-cluster.png 'Manage cluster')

3. In the window, select the `SQL Big Data Cluster` tab and then select the `Open Notebook` tile.

   ![Open notebook](media/task02-sql-bdc-manage.png 'Open notebook')

4. Browse to **C:\lab-files\data\1**, select **predict-battery-life-with-sqlbdc.ipynb** and select `Open`.

5. Follow the instructions in the notebook and return to the next step after you have completed the notebook.

   > There may be a kernel error pertaining to there not being a valid SQL connection when you open the notebook. If this happens, close the notebook and Azure Data Studio, then re-launch, reconnect, then re-open the notebook.

### Task 2: Score and save data as an external table

1.  In Azure Data Studio, under Servers, expand your Big Data Cluster, `Data Services`, `HDFS`, `data`.

2.  Right click the `data` folder and select `Refresh` to see the newly created folder.

    ![Refresh data](media/task02-refresh-data.png 'Refresh data')

3.  You should see `battery-life.csv` as a folder, expand it and then right click on the CSV file whose name starts with `part-00000-` and select `Create External Table From CSV Files`.

    ![Create External Table](media/task02-create-external-menu.png 'Create External Table')

4.  In Step 1 of the wizard, select your Active SQL Server connection to connect to your Big Data Cluster endpoint and select `Next`.

    ![Select endpoint](media/task02-ext-step1.png 'Select endpoint')

5.  In Step 2, select the `sales` database and for the `Name for new external table` field provide `battery-life-predictions`. Select Next.

    ![Step 2](media/task02-ext-step2.png 'Step 2')

6.  On Step 3, select `Next`.

7.  On Step 4, for the column `Car_Has_EcoStart` set the Data Type to `char(10)`. Select `Next`.

    ![Step 4](media/task02-ext-step4.png 'Step 4')

8.  On Step 5, select `Create Table`. Your predictions are now available for SQL querying in the battery-life-predictions table in the sales database.

9.  In Azure Data Studio, Servers, expand your Big Data Cluster, `Databases`, `sales_YOUR-UNIQUE-IDENTIFIER`, right click `Tables` and then select `Refresh`.

    ![Refresh sales](media/task02-refresh-sales.png 'Refresh sales')

10. Expand `tables`, right click `battery-life-prediction` and select `query` to view the data contained by the external table.

    ![Select Top 1000](media/task02-select-top.png 'Select Top 1000')

11. The vehicle telemetry along with predictions will appear. These are queried from the external table which is sourced from the CSV you created using the notebook.

    ![View data](media/task02-view-data.png 'View data')

## Task 3: Mounting an Azure Data Lake Gen2 Storage Account to SQL Server 2019 Big Data Cluster using HDFS Tiering

With tiering, applications can seamlessly access data in a variety of external stores as though the data resides in the local HDFS. This allows you to interact with the files in Azure Data Lake Store Gen2 as if they were local files. You can either use an Azure Storage access key or an Azure Active Directory User Account to gain permission to the files. For this lab, we will use the access key.

1. In Windows, open PowerShell.

![Search for PowerShell .](media/powershell.png 'SQL Server Management Studio - Connect')

2. In PowerShell, install the mssqlstl package using pip:

   ```powershell
     pip3 install -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

3. Once mssqlctl installs, connect to your Microsoft SQL Server 2019 Big Data Cluster:

   ```python
     mssqlctl login -e https://<SQL SERVER Controller IP ADDRESS>:30080
   ```

   a. You will be prompted for your big data cluster name.
   b. The user name is admin
   c. The password is MySQLBigData2019

4. Create an empty text file named filename.creds in your temp folder on the c:\ drive. Add this line as the contents:

fs.azure.abfs.account.name=ikedatabricks.dfs.core.windows.net
fs.azure.account.key.ikedatabricks.dfs.core.windows.net=HUYPk/VUjdYzkCvrKXTgFBObt5VQcp5DCY7C9KiSHX42lv65mjmBFmKFVTLy7Z7suQ0WV44mncuUOvnE8NkxGg==

5. In PowerShell, type the following command to mount the drive

   ```powershell
       mssqlctl cluster storage-pool mount create --remote-uri abfs://databricksfiles@ikedatabricks.dfs.core.windows.net/ --mount-path   /mounts/dbfiles --credential-file c:\temp\filename.creds
   ```

6. Once the storage account has been mounted, you can check the status:

```powershell
  mssqlctl cluster storage-pool mount status
```

7. Now you can use Azure Data Studio and view the files from ADLS Gen2 under your HDFS folder in your Servers pane. Look under /HDFS/mounts/dbfiles/

   ![Azure Data Studio server pane for new dbfiles folder](media/data-studio-mounts.png)

8. Now that the drive is mounted, create an external file format for CSV. Open a new query window and paste the following command:

```sql
  USE Sales;
  GO
  CREATE EXTERNAL FILE FORMAT csv_file
  WITH (
      FORMAT_TYPE = DELIMITEDTEXT,
      FORMAT_OPTIONS(
          FIELD_TERMINATOR = ',',
          STRING_DELIMITER = '"',
          FIRST_ROW = 2,
          USE_TYPE_DEFAULT = TRUE)
  );
```

9. Now create an external connection to your HDFS cluster:

```sql
  IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
  BEGIN
    CREATE EXTERNAL DATA SOURCE SqlStoragePool
    WITH (LOCATION = 'sqlhdfs://controller-svc:8080/default');
  END
```

10. Now let's create two tables to two different files that exist in the storage account:

```sql
CREATE EXTERNAL TABLE planes
("tailnum" VARCHAR(100),	"year" VARCHAR(4),	"type" VARCHAR(100)
,	"manufacturer" VARCHAR(100),	"model" VARCHAR(20),	"engines" BIGINT
,	"seats" BIGINT,	"speed" VARCHAR(20)
,	"engine" VARCHAR(20))
WITH
(
    DATA_SOURCE = SqlStoragePool,
    LOCATION = '/mounts/dbfiles/planes.csv',
    FILE_FORMAT = csv_file
);
GO

 CREATE EXTERNAL TABLE flights
("year" BIGINT, 	"month" BIGINT, 	"day" BIGINT,	"dep_time" BIGINT
    ,	"dep_delay" BIGINT,	"arr_time" BIGINT,	"arr_delay" BIGINT,	"carrier" VARCHAR(100)
    ,	"tailnum" VARCHAR(20),	"flight" VARCHAR(20),	"origin" VARCHAR(50)
    ,	"dest" VARCHAR(50),	"air_time" BIGINT,	"distance" BIGINT,
    	"hour" BIGINT,	"minute" BIGINT)
WITH
(
    DATA_SOURCE = SqlStoragePool,
    LOCATION = '/mounts/dbfiles/flights_small.csv',
    FILE_FORMAT = csv_file
);
```

11. Once the tables are created, you can interact with them like normal tables. For instance, you can run a query that joins the two tables like this:

```sql
SELECT *
  FROM planes p
  JOIN flights f
   on p.tailnum = f.tailnum
```

## Exercise 4: Identify PII and GDPR-related compliance issues using Data Discovery & Classification in SSMS

Contoso Auto has several databases that include tables containing sensitive data, such as personally identifiable information (PII) like phone numbers, social security numbers, financial data, etc. Since some of their personnel and customer data include individuals who reside within the European Union (EU), they need to adhere to the General Data Protection Regulation ([GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation)) as well. Because of this, Contoso Auto is required to provide periodic data auditing reports to identify sensitive and GDPR-related data that reside within their various databases.

With SQL Server Management Studio, they are able to identify, classify, and generate reports on sensitive and GDPR-related data by using the [SQL Data Discovery & Classification](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-ver15) tool. This tool introduces a set of advanced services, forming a new SQL Information Protection paradigm aimed at protecting the data, not just the database:

- **Discovery & recommendations** - The classification engine scans your database and identifies columns containing potentially sensitive data. It then provides you an easy way to review and apply the appropriate classification recommendations, as well as to manually classify columns.
- **Labeling** - Sensitivity classification labels can be persistently tagged on columns.
- **Visibility** - The database classification state can be viewed in a detailed report that can be printed/exported to be used for compliance & auditing purposes, as well as other needs.

### Task 1: Use the Data Discovery & Classification in SSMS

In this task, you will run the SQL Data Discovery & Classification tool against their customer database, which includes personal, demographic, and sales data.

1.  Open SQL Server Management Studio (SSMS) and connect to your SQL Server 2019 cluster.

2.  Right-click on the **sales** database, then choose **Tasks > Classify Data...**.

    ![The sales database, Tasks menu, and Classify Data items are highlighted.](media/ssms-classify-data-link.png 'Data Classification')

3.  When the tool runs, it will analyze all of the columns within all of the tables and recommend appropriate data classifications for each. What you should see is the Data Classification dashboard showing no currently classified columns, and a classification recommendations box at the top showing that there are 45 columns that the tool identified as containing sensitive (PII) or GDPR-related data. **Click** on this classification recommendations box.

    ![The data classification recommendations box is highlighted.](media/ssms-classification-recommendations-box.png 'Data classification recommendations box')

4.  The list of recommendations displays the schema, table, column, type of information, and recommended sensitivity label for each identified column. You can change the information type and sensitivity labels for each if desired. In this case, accept all recommendations by **checking the checkbox** in the recommendations table header.

    ![The recommendations are shown with each checkbox checked.](media/ssms-recommendations.png 'Classification recommendations')

5.  Click **Accept selected recommendations**.

    ![The Accept selected recommendations button is highlighted.](media/ssms-accept-selected-recommendations.png 'Accept selected recommendations')

6.  Click **Save** in the toolbar above to apply your changes.

    ![The Save button is highlighted.](media/ssms-save-classification-changes.png 'Save classification changes')

7.  After the changes are saved, click **View Report**.

    ![The View Report button is highlighted.](media/ssms-view-report.png 'View Report')

8.  What you should see is a report with a full summary of the database classification state. When you right-click on the report, you can see options to print or export the report in different formats.

    ![The report is displayed, as well as the context menu showing export options after right-clicking on the report.](media/ssms-report.png 'SQL Data Classification Report')

### Task 2: Fix compliance issues with dynamic data masking

Some of the columns identified by the Data Discovery & Classification tool as containing sensitive (PII/GDPR) information include phone numbers, email addresses, billing addresses, and credit card numbers. One way to ensure compliance with various rules and regulations that enforce policies to protect such sensitive data is to prevent those who are not authorized from seeing it. An example would be displaying `XXX-XXX-XX95` instead of `123-555-2695` when outputting a phone number within a SQL query result, report, web page, etc. This is commonly called data masking. Traditionally, modifying systems and applications to implement data masking can be challenging. This is especially true when the masking has to apply all the way down to the data source level. Fortunately, SQL Server and its cloud-related product, Azure SQL Database, provides a feature named [dynamic data masking](https://docs.microsoft.com/sql/relational-databases/security/dynamic-data-masking?view=sql-server-ver15) (DDM) to automatically protect this sensitive data from non-privileged users.

Dynamic data masking helps prevent unauthorized access to sensitive data by enabling customers to designate how much of the sensitive data to reveal with minimal impact on the application layer. DDM can be configured on the database to hide sensitive data in the result sets of queries over designated database fields, while the data in the database is not changed. Dynamic data masking is easy to use with existing applications, since masking rules are applied in the query results. Many applications can mask sensitive data without modifying existing queries.

In this task, you will apply dynamic data masking to one of the database fields so you can see how to address the reported compliance issues. To test the data mask, you will create a test user and query the field as that user.

1. Open SQL Server Management Studio (SSMS) and connect to your SQL Server 2019 cluster.

2. Expand the databases list, right-click on **sales**, then select **New Query**.

   ![The sales database and New Query menu item are highlighted.](media/ssms-sales-new-query.png 'New Query')

3. Add a dynamic data mask to the existing `dbo.customer.c_last_name` field by pasting the below query into the new query window:

   ```sql
   ALTER TABLE dbo.customer
   ALTER COLUMN c_last_name ADD MASKED WITH (FUNCTION = 'partial(2,"XXX",0)');
   ```

   > The `partial` custom string masking method above exposes the first two characters and adds a custom padding string after for the remaining characters. The parameters are: `prefix,[padding],suffix`

4. Execute the query by clicking the **Execute** button above the query window, or enter _F5_.

   ![The dynamic data mask query is shown and the Execute button is highlighted above.](media/ssms-execute-ddm-query.png 'Execute query')

5. Clear the query window and replace the previous query with the following to add a dynamic data mask to the `dbo.customer.c_email_address` field:

   ```sql
   ALTER TABLE dbo.customer
   ALTER COLUMN c_email_address ADD MASKED WITH (FUNCTION = 'email()');
   ```

   > The `email` masking method exposes the first letter of an email address and the constant suffix ".com", in the form of an email address: `aXXX@XXXX.com`.

6. Clear the query window and replace the previous query with the following, selecting all rows from the customer table:

   ```sql
   SELECT * FROM dbo.customer
   ```

   ![The query results are shown with no mask applied to the Postal Code field.](media/ssms-ddm-results-no-mask.png 'Query results')

7. Notice that the full last name and email address values are visible. That is because the user you are logged in as a privileged user. Let's create a new user and execute the query again:

   ```sql
   CREATE USER TestUser WITHOUT LOGIN;
   GRANT SELECT ON dbo.customer TO TestUser;

   EXECUTE AS USER = 'TestUser';
   SELECT * FROM dbo.customer;
   REVERT;
   ```

8. Execute the query by clicking the **Execute** button. Notice this time that the Postal Code values are masked (`90XXX`).

   ![The query results are shown with the mask applied to the Postal Code field.](media/ssms-ddm-results-mask.png 'Query results')

## Exercise 5: Exploring intelligent query processing (QP) features

In this exercise, you will execute a series of SQL scripts in SQL Server Management Studio (SSMS) to explore the improvements to the family of intelligent query processing (QP) features in SQL Server 2019. These features improve the performance of existing workloads with minimal work on your part to implement. The key to enabling these features in SQL Server 2019 is to set the [database compatibility level](https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-database-transact-sql-compatibility-level?view=sql-server-ver15) to `150`. You will be executing these queries against the `sales_XXXXX` database (where XXXXX is the unique identifier assigned to you for this workshop).

To learn more, read [intelligent query processing](https://docs.microsoft.com/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-ver15) in SQL databases.

### Task 1: Set database compatibility level

1. To get started, expand databases in the SQL Server Management Studio (SSMS) Object Explorer, right-click the `sales_XXXXX` database (where XXXXX is the unique identifier assigned to you for this workshop), and then select **New Query**.

   ![The sales database and New Query menu item are highlighted.](media/ssms-sales-new-query.png 'New Query')

2. The first query you will run is to set the database compatibility level to `150`, which is the new compatibility level for SQL Server 2019, enabling the most recent intelligent QP features. Copy the SQL script below and paste it into the new query window. Replace `XXXXX` with the unique identifier you have been given for this workshop in both the `USE` and `ALTER DATABASE` statements.

   ```sql
   USE sales_XXXXX;
   GO

   ALTER DATABASE sales_XXXXX
   SET COMPATIBILITY_LEVEL = 150;
   GO
   ```

3. To run the query, select **Execute** in the SSMS toolbar.

   ![The Execute button is highlighted in the SSMS toolbar.](media/ssms-execute-query.png 'Execute')

### Task 2: Scalar UDF inlining

Next, you will run a query to create a user-defined function (UDF) named `customer_category`. This UDF contains several steps to identify the discount price category for each customer. Notice that at the top of the query we run to create this UDF sets the database compatibility level to `150`, which is the new compatibility level for SQL Server 2019, enabling the most recent intelligent QP features. This UDF will be called inline from the two queries that follow in order to show QP improvements on scalar UDF inlining.

1. Paste the following SQL code into your query window, overwriting the current content, replace `XXXXX` in the `USE` statement with the unique identifier assigned to you for this workshop, and then select **Execute** on the SSMS toolbar.

   ```sql
   USE sales_XXXXX;
   GO

   ALTER DATABASE SCOPED CONFIGURATION
   CLEAR PROCEDURE_CACHE;
   GO

   CREATE OR ALTER FUNCTION
     dbo.customer_category(@CustomerKey INT)
   RETURNS CHAR(10) AS
   BEGIN
     DECLARE @total_amount DECIMAL(18,2);
     DECLARE @category CHAR(10);

     SELECT @total_amount =
     SUM([ws_net_paid_inc_ship])
     FROM [dbo].[web_sales]
     WHERE [ws_bill_customer_sk] = @CustomerKey;

     IF @total_amount < 50000
       SET @category = 'REGULAR';
     ELSE IF @total_amount < 100000
       SET @category = 'GOLD';
     ELSE
       SET @category = 'PLATINUM';

     RETURN @category;
   END
   GO
   ```

   > Scalar UDF inlining automatically transforms [scalar UDFs](https://docs.microsoft.com/sql/relational-databases/user-defined-functions/create-user-defined-functions-database-engine?view=sql-server-2017#Scalar) into relational expressions. It embeds them in the calling SQL query. This transformation improves the performance of workloads that take advantage of scalar UDFs. Scalar UDF inlining facilitates cost-based optimization of operations inside UDFs. The results are efficient, set-oriented, and parallel instead of inefficient, iterative, serial execution plans. This feature is enabled by default under database compatibility level 150. _For more information, see [Scalar UDF inlining](https://docs.microsoft.com/sql/relational-databases/user-defined-functions/scalar-udf-inlining?view=sql-server-2017)_.

2. Right-click on the `sales_XXXXX` database (where XXXXX is the unique identifier assigned to you for this workshop), then select **New Query**. This will open a new query window into which you can paste the following queries. You may wish to reuse the same query window, replacing its contents with each SQL statement blocks below, or follow these same steps to create new query windows for each.

   ![The sales database and New Query menu item are highlighted.](media/ssms-sales-new-query.png 'New Query')

3. The query below selects the top 100 rows from the `customer` table, calling the `customer_category` user-defined function (UDF) inline for each row. It uses the `DISABLE_TSQL_SCALAR_UDF_INLINING` hint to disable the new scalar UDF inlining QP feature. Paste the following query into the the empty query window. Replace `XXXXX` in the `USE` statement with the unique identifier assigned to you for this workshop. **Do not execute yet**.

   ```sql
   USE sales_XXXXX;
   GO

   -- Before (show actual query execution plan for legacy behavior)
   SELECT TOP 100
       [c_customer_sk], [c_first_name], [c_last_name],
         dbo.customer_category([c_customer_sk]) AS [Discount Category]
   FROM [dbo].[customer]
   ORDER BY [c_customer_sk]
   OPTION (RECOMPILE, USE HINT('DISABLE_TSQL_SCALAR_UDF_INLINING'));
   ```

4. Select the **Include Actual Execution Plan** (Ctrl+M) button in the toolbar above the query window. This will allow us to view the actual (not estimated) query plan after executing the query.

   ![The Actual Query Plan button is highlighted in the toolbar.](media/ssms-enable-actual-query-plan-customer.png 'Enable Actual Query Plan')

5. Execute the query by selecting **Execute** from the SSMS toolbar.

6. After the query executes, select the **Execution plan** tab. As the plan shows, SQL Server adopts a simple strategy here: for every tuple in the `customer` table, invoke the UDF and output the results (single line from the clustered index scan to compute scalar). This strategy is naïve and inefficient, especially with more complex queries.

   ![This screenshot shows the query execution plan using the legacy method.](media/ssms-udf-inlining-before.png 'Query execution plan with legacy method')

7. Clear the query window, or open a new one, then paste the following query that makes use of the scalar UDF inlining QP feature. Replace `XXXXX` in the `USE` statement with the unique identifier assigned to you for this workshop. If you opened a new query window instead of reusing this one, make sure to select the **Include Actual Execution Plan** button to enable it. **Execute** the query.

   ```sql
   USE sales_XXXXX;
   GO

   -- After (show actual query execution plan for legacy behavior)
   SELECT TOP 100
       [c_customer_sk], [c_first_name], [c_last_name],
         dbo.customer_category([c_customer_sk]) AS [Discount Category]
   FROM [dbo].[customer]
   ORDER BY [c_customer_sk]
   OPTION (RECOMPILE);
   ```

8. After the query executes, select the **Execution plan** tab once again. With scalar UDF inlining, this UDF is transformed into equivalent scalar subqueries, which are substituted in the calling query in place of the UDF.

   ![This screenshot shows the query execution plan using the new QP feature.](media/ssms-udf-inlining-after.png 'Query execution plan with new method')

   > As you can see, the query plan no longer has a user-defined function operator, but its effects are now observable in the plan, like views or inline TVFs. Here are some key observations from the above plan:

   A. SQL Server has inferred the implicit join between `dbo.customer` and `dbo.web_sales` and made that explicit via a join operator.

   B. SQL Server has also inferred the implicit `GROUP BY [Customer Key] on dbo.web_sales` and has used the IndexSpool + StreamAggregate to implement it.

   > Depending upon the complexity of the logic in the UDF, the resulting query plan might also get bigger and more complex. As we can see, the operations inside the UDF are now no longer a black box, and hence the query optimizer is able to cost and optimize those operations. Also, since the UDF is no longer in the plan, iterative UDF invocation is replaced by a plan that completely avoids function call overhead.

### Task 3: Table variable deferred compilation

1. Either highlight and delete everything in the query window, or open a new query window. Paste the following query into the query window, replacing `XXXXX` in the `USE` statement with the unique identifier assigned to you for this workshop. This query makes use of the table variable deferred compilation feature, since the database compatibility level is set to `150`. If you opened a new query window instead of reusing this one, make sure to click the **Include Actual Execution Plan** button to enable it. **Execute** the query.

   ```sql
   USE sales_XXXXX
   GO

   DECLARE @ItemClick TABLE (
     [itemKey] BIGINT NOT NULL,
     [clickDate] BIGINT NOT NULL
   );

   INSERT @ItemClick
   SELECT [wcs_item_sk], [wcs_click_date_sk]
   FROM [dbo].[web_clickstreams]

   -- Look at estimated rows, speed, join algorithm
   SELECT i.[i_item_sk], i.[i_current_price], c.[clickDate]
   FROM dbo.item AS i
   INNER JOIN @ItemClick AS c
     ON i.[i_item_sk] = c.[itemKey]
   WHERE i.[i_current_price] > 90
   ORDER BY i.[i_current_price] DESC;
   GO
   ```

   > The script above assigns a table variable, `@ItemClick`, storing the `itemKey` and `clickDate` fields from the `web_clickstreams` table to be used in an INNER JOIN below.

   **Old method**

   In prior versions of SQL Server (compatibility level of 140 or lower), the table variable deferred compilation QP feature is not used (more on this below).

   There are two plans. The one you want to observe is the second query plan. When we mouse over the INNER JOIN to view the estimated number of rows and the output list, which shows the join algorithm. The estimated number of rows is 1. Also, observe the execution time. In our case, it took 10 seconds to complete.

   ![This screenshot shows the query execution plan using the legacy method.](media/ssms-tvdc-old-method.png 'Query execution plan with old method')

   **New method**

   After the query above executes, select the **Execution plan** tab once again. Since our database compatibility level is set to 150, notice that the join algorithm is a hash match, and that the overall query execution plan looks different. When you hover over the INNER JOIN, notice that there is a high value for estimated number of rows and that the output list shows the use of hash keys and an optimized join algorithm. Once again, observe the execution time. In our case, it took 6 seconds to complete, which is approximately half the time it took to execute without the table variable deferred compilation feature.

   ![This screenshot shows the query execution plan using the new method.](media/ssms-tvdc-new-method.png 'Query execution plan with new method')

   > Table variable deferred compilation improves plan quality and overall performance for queries that reference table variables. During optimization and initial compilation, this feature propagates cardinality estimates that are based on actual table variable row counts. This accurate row count information optimizes downstream plan operations. Table variable deferred compilation defers compilation of a statement that references a table variable until the first actual run of the statement. This deferred compilation behavior is the same as that of temporary tables. This change results in the use of actual cardinality instead of the original one-row guess. _For more information, see [Table variable deferred compilation](https://docs.microsoft.com/sql/t-sql/data-types/table-transact-sql?view=sql-server-2017#table-variable-deferred-compilation)._

### Task 4: Row mode memory grant feedback

1. Either highlight and delete everything in the query window, or open a new query window. Paste the following query to simulate out-of-date statistics on the `web_sales` table, followed by a query that executes a hash match, replacing `XXXXX` in the `USE` statement with the unique identifier assigned to you for this workshop. If you opened a new query window instead of reusing this one, make sure to click the **Include Actual Execution Plan** button to enable it. **Execute** the query.

   ```sql
   USE sales_XXXXX;
   GO

   -- Simulate out-of-date stats
   UPDATE STATISTICS dbo.web_sales
   WITH ROWCOUNT = 1;
   GO

   SELECT
     ws.[ws_order_number], ws.ws_quantity,
     i.[i_current_price], i.[i_item_desc]
   FROM    dbo.web_sales AS ws
   INNER HASH JOIN dbo.[item] AS i
     ON ws.[ws_item_sk] = i.[i_item_sk]
   WHERE   i.[i_current_price] > 10
     AND ws.[ws_quantity] > 40;
   ```

2. After the query executes, select the **Execution plan** tab. Hover over the Hash Match step of the execution plan. You should see a warning toward the bottom of the Hash Match dialog showing spilled data. Also observe the execution time. In our case, this query took 16 seconds to execute.

   ![The Hash Match dialog shows spilled data warnings.](media/ssms-memory-grant-feedback-old.png 'Query execution plan showing spilled data')

3. Either highlight and delete everything in the query window, or open a new query window. Paste the following query to execute the select query that contains the hash match once more, replacing `XXXXX` in the `USE` statement with the unique identifier assigned to you for this workshop. If you opened a new query window instead of reusing this one, make sure to click the **Include Actual Execution Plan** button to enable it. **Execute** the query.

   ```sql
   USE sales_XXXXX;
   GO

   SELECT
     ws.[ws_order_number], ws.ws_quantity,
     i.[i_current_price], i.[i_item_desc]
   FROM    dbo.web_sales AS ws
   INNER HASH JOIN dbo.[item] AS i
     ON ws.[ws_item_sk] = i.[i_item_sk]
   WHERE   i.[i_current_price] > 10
     AND ws.[ws_quantity] > 40;
   ```

4. After the query executes, select the **Execution plan** tab. Hover over the Hash Match step of the execution plan. You should **no longer** see a warning about spilled data. Also observe the execution time. In our case, this query took 11 seconds to execute.

   ![The Hash Match dialog no longer contains spilled data warnings.](media/ssms-memory-grant-feedback-fix.png 'Query execution plan with no spilled data')

   > So what happened? A query's post-execution plan in SQL Server includes the minimum required memory needed for execution and the ideal memory grant size to have all rows fit in memory. Performance suffers when memory grant sizes are incorrectly sized. Excessive grants result in wasted memory and reduced concurrency. Insufficient memory grants cause expensive spills to disk. By addressing repeating workloads, batch mode memory grant feedback recalculates the actual memory required for a query and then updates the grant value for the cached plan. **When an identical query statement is executed**, the query uses the revised memory grant size, reducing excessive memory grants that impact concurrency and fixing underestimated memory grants that cause expensive spills to disk. Row mode memory grant feedback expands on the batch mode memory grant feedback feature by adjusting memory grant sizes for both batch and row mode operators. _For more information, see [Row mode memory grant feedback](https://docs.microsoft.com/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#row-mode-memory-grant-feedback)._

## Exercise 6: Monitoring the big data cluster

### Task 1: Use the cluster administration portal

### Task 2: Monitor and troubleshoot using Kubectl commands

## After the hands-on lab

Duration: 10 mins

In this exercise, you will delete any Azure resources that were created in support of the lab. You should follow all steps provided after attending the Hands-on lab to ensure your account does not continue to be charged for lab resources.

### Task 1: Delete the resource group

1. Using the [Azure portal](https://portal.azure.com), navigate to the Resource group you used throughout this hands-on lab by selecting Resource groups in the left menu.
2. Search for the name of your resource group, and select it from the list.
3. Select Delete in the command bar, and confirm the deletion by re-typing the Resource group name, and selecting Delete.

You should follow all steps provided _after_ attending the Hands-on lab.
