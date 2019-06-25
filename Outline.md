![Microsoft Cloud Workshop](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
Modernizing data analytics with SQL Server 2019
</div>

<div class="MCWHeader2">
Workshop outline
</div>

<div class="MCWHeader3">
June 2019
</div>

# Modernizing data analytics with SQL Server 2019 outline

Businesses require near real-time insights from ever-larger sets of data. Large-scale data ingestion requires scale-out storage and processing in ways that allow fast response times. In addition to simply querying this data, organizations want full analysis and even predictive capabilities over their data.

While solutions for large-scale data processing exist, they are often batch-based, which has a lag in the time from query to response. Also, batch systems such as Hadoop are complicated to set up and manage. Operational data is often stored in Relational Database systems on-premises, and joining that data to larger-scale cloud systems exposes security weaknesses and brittle architectures.

## Target audience

- Database Administrator
- Data Engineer
- Data Scientist
- Database Developer
- Solution Architect

## Abstract

### Workshop

<!-- In this workshop, you will gain a better understanding of how new features of SQL Server 2019 enables more Big Data and analytics capabilities through the use of Big Data Clusters, data virtualization and orchestration, query processing enhancements, and through better scalability through distributed storage and compute.

At the end of this workshop, you will be better able to configure and manage SQL Server 2019 Big Data Clusters so you can combine, query, and transform disparate data sources for AI and advanced analytics scenarios.

#### Customer situation -->

Wide World Importers (WWI) is a traditional brick and mortar business with a long track record of success, generating profits through strong retail store sales of their unique offering of affordable products from around the world. They have a great training program for new employees, that focuses on connecting with their customers and providing great face-to-face customer service. This strong focus on customer relationships has helped set WWI apart from their competitors.

WWI's evolution of services over the years has helped them expand their reach beyond the walls of their retail stores into the web and mobile space. With this expansion, they have generated a significant amount of additional data, and data formats. These new platforms were added without integrating into the OLTP system data or Business Intelligence infrastructures. As a result, "silos" of data stores have developed.

Due to their continued growth, lending to expansion into the digital space, WWI is prepared to innovate by taking advantage of their omni-channel strategy and increased variety and amount of valuable data. They believe they can foster innovation by building upon their track record of strong customer connections, and engage with their customers through personalized, high-quality application experiences that incorporate data and intelligence.

However, as a first step, WWI's technology team has recognized they must address the fact that they have quickly outgrown their ability to handle data. They anticipate the following solutions needed to reach more customers and grow the business:

- Scale data systems to reach more consumers
- Unlock business insights from multiple sources of structured and unstructured data
- Apply deep analytics with high-performance responses
- Infuse AI into apps to actively engage with customers

Prior to expanding to their current omni-channel strategy, WWI had a simple Point of Sale (POS) application that handled customer orders at each retail store. The back-end was a series of service layers used to process orders and store them in a SQL database. They had designed their systems and tuned them to handle this level of data.

As they added new e-commerce channels to expand the customer base, consumer demand also increased. This increased demand from more customers ordering products through more channels generated more data. Now WWI has new challenges to address:

- Increased consumer demand, leading to increased app data
- They are unable to determine business trends because of siloed insights
- They have a rising data management footprint, increasing cost and complexity
- New development challenges resulting from more deployment targets and duplicated code

There are two scenarios WWI is considering using AI to help grow their business and reduce costs:

1. Sales forecasting. Based on current and historical retail data, could they predict whether retail sales will be on track this month? Being able to meet sales targets while accurately forecasting sales revenue are critical success enablers by helping drive marketing campaigns and scale logistics and staffing accordingly.
2. Reduce maintenance costs, waste, and maximize fleet availability by predicting battery lifespans. Wide World Importers relies on refrigerated trucks to deliver temperature-sensitive products. A dead or malfunctioning battery could cause the cooling systems to fail, requiring regular battery testing and replacements. WWI would like to use transmitted sensor data from these trucks to predict when a battery will most likely fail to reduce downtime and cut waste resulting from fixed battery replacement schedules.

Workshop objectives:

1. Have students consider options for accessing data that comes from multiple locations. Should they virtualize the data by pushing down the query to the source system (no data ingestion), ingest data into SQL tables via PolyBase, etc., or load data into HDFS? Should they do a combination of these things depending on requirements and constraints? What are the decision points?
2. Should we plan on installing all BDC components in Azure, or have some combination of components on-premises and in Azure?
3. Highlight query processing enhancements where possible.

### Whiteboard design session _(this will go in the readme and in the WDS document)_

In this whiteboard design session, you will work with a group to design a solution for modernizing your large-scale data processing and machine learning capabilities through the use of SQL Server Big Data Clusters. You will evaluate the customer scenario and requirements to decide the best architecture that will meet their needs, while unifying data from disparate sources into a platform that help the customer gain business insights and apply advanced analytics at scale.

At the end of this whiteboard design session, you will be better able to design a modernization plan for performing Big Data analytics centered around SQL Server 2019 capabilities.

#### Outline: Key concerns for Customer situation

Client needs:

1. Need distributed storage available to all nodes of the container: The storage can disappear when the Container is removed, and other Containers and technologies can't access storage easily within a Container.
2. Require a data lake to easily store and access disparate data.
3. Simplified programming surface to prepare data and do data science.
4. Scale data systems to reach more consumers.
5. Unlock business insights from multiple sources of structured and unstructured data.
6. Apply deep analytics with high-performance responses.
7. Enable AI into apps to actively engage with customers.
8. Identify PII and GDPR-related compliance issues for audit reports and take steps to fix these issues.

Objections:

1. How do we centrally manage and monitor the cluster once deployed?
2. Do our workloads require us to use a data warehouse, or will a data mart suffice?
3. Will moving to container-based SQL clusters be complex and too high of a operational and management cost for our IT team?

### Hands-on lab _(this will go in the readme and in the HOL document)_

In this hands-on lab, you will implement the steps to install and configure a SQL Server 2019 cluster to Linux-based containers in Azure. Using this cluster, you will use data virtualization to unify data from various sources, analyze the data, create and deploy a machine learning model, and finally detect and fix PII and GDPR compliance issues.

At the end of this hands-on lab, you will be better able to build solutions for conducting advanced data analytics at scale with scalable SQL Server 2019 Big Data clusters.

#### Lab pre-requisites

Computer or VM with the following installed:

- PowerShell
- Python3
- [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)
- [mssqlctl](https://docs.microsoft.com/en-us/sql/big-data-cluster/deploy-install-mssqlctl?view=sql-server-ver15)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery)
- [SQL Server Management Studio](https://go.microsoft.com/fwlink/?linkid=2088649) (SSMS) v18.0 or greater
- [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-ver15)
  - [SQL Server 2019 extension](https://docs.microsoft.com/en-us/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-2017)

#### Regional limitations

**L Series VMs** (required for SQL 2019 Big Data Clusters): East US 2, West US, West US 2, and a limited set of others worldwide

#### Outline: Hands-on lab exercises

- Before the hands-on lab (30 minutes)
  - Task 1: Set up Lab VM
  - Task 2: Deploy SQL Server 2019 Big Data Cluster to AKS
  - Task 3: Provision Azure SQL Database
  - Task 4: Install sample databases and upload files
- Exercise 1: Using data virtualization
  - Task 1: Create external table from Azure SQL Database
  - Task 2: Create external table from CSV files
  - Task 3: Query and join data from flat files, data from external database systems, and SQL Server
- Exercise 2: Using notebooks
  - Task 1: Introduction to Jupyter notebooks
  - Task 2: Querying the SQL Server Master Instance (MI)
  - Task 3: Virtualizing data with scripts
  - Task 4: Creating and querying a Data Mart
  - Task 5: Using the powerful Spark engine for data exploration
- Exercise 3: Machine learning
  - Task 1: Train a machine learning model
  - Task 2: Score and save data as an external table
- Exercise 4: Identify and fix PII and GDPR-related compliance issues
  - Task 1: Use the Data Discovery & Classification in SSMS
  - Task 2: Fix compliance issues with dynamic data masking
- Exercise 5: Exploring intelligent query processing (QP) features
  - Task 1: Scalar UDF inlining
  - Task 2: Table variable deferred compilation
  - Task 3: Row mode memory grant feedback
- Exercise 6: Monitoring the big data cluster
  - Task 1: Use the cluster administration portal
  - Task 2: Monitor and troubleshoot using Kubectl commands
- Exercise 7: Cleanup
  - Task 1: Delete resource group

## Azure services and related products

- SQL Server 2019
- Docker
- Linux
- Azure Kubernetes Service (AKS)
- Apache HDFS
- Apache Knox
- Apache Spark
- SQL Server Machine Learning Services
- Azure Data Studio
- SQL Server Management Studio

## Azure solutions

_This is an internal reference and will be updated by project PM._

## Related references

_This should be a list of and links to prereqs, architectural diagrams, supporting docs, or briefing decks related to the material._

- [MCW](https://github.com/Microsoft/MCW)
