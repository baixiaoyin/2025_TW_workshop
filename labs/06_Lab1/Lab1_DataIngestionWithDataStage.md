# Lab1_DataIngestionWithDataStage

## <span style="font-size:26px;">What would you expect in this lab</span>

1.	Bronze layer creation: Data ingestion from DB2, PostgreSQL and IBM Cloud Object Storage to watsonx.data Iceberg tables with Datastage.
2.	Silver layer creation: Data cleasing and transfer with Datastage.

## <span style="font-size:26px;"> Detailed steps</span>


### <span style="font-size:24px;"> Step 1: Import Project</span>

<span style="font-size:20px;">Navigate to Projects > All Project, create on `New Project`.</span>

<img src="./images/all_projects.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Select `Local File` --> Drag and drop your project .zip file in to the "Browse"</span>

<img src="./images/local_project1.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Enter a project name --> Create <br>
Note: the project name please follow the format [your name]_hk_techexchange_project</span>

<img src="./images/create_project.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Go to your new project</span>

<img src="./images/goto_newproject.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">After successfully import project. You should see many assets that we are going to use for data ingestion.</span>
<img src="./images/project_created.png" alt="alt text" width="1600">

<br><br>
### <span style="font-size:24px;"> Step 2: Connections check</span>

<br><br>
<span style="font-size:20px;">Check 4 connections one by one, starting with "IBM_S3COS_connection" by clicking it </span>
<img src="./images/connections.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Click "Test connection"-->Waiting for the Sucessful info --> Click Cancel </span>
<img src="./images/check_cos.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Do the same for the rest 3 connections</span>
<img src="./images/check_db2.png" alt="alt text" width="1600">
<img src="./images/check_postgres.png" alt="alt text" width="1600">
<img src="./images/check_presto.png" alt="alt text" width="1600">

<br><br>
###  <span style="font-size:24px;"> Step 3: Run DataStage Flow -- Bronze Layer</span>

<span style="font-size:20px;"> The project import with several DataStage flows. Now let's start with the bronze layer data ingestion, clicking the "lab1_bronzeLayer" flow </span>
<img src="./images/lab1_click.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">
This step will read from 3 tables from the source to the watsonx.data Iceberg table:
<span>

1. Customer table from S3 (IBM Cloud Object Storage)
2. Tranction table from DB2
3. Credit card from PostgreSQL

<img src="./images/bronzeFlowIntro.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">
For 3 sources, you do not have to change anything, keep it as it is.<br>
For 3 targets, double click them one by one, starting with customer_bronze.<br>
<span>
<img src="./images/customer_bronze_click.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">
Modify the catalog, shcema and table<br>
Catalog: should be "hk_aug_catalog0", change to this if it is not<br>
Shchema: should be "hk_aug_schema0", change to this if it is not<br>
<span>
<span style="font-size:20px; color:red;">
!!Table: Change to [yourName]_customers_bronze<br>
<span>
<span style="font-size:20px;">
Click Save <br>
<span>

<img src="./images/customers_bronze_change.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">
Do the same for the rest two: transactions and credit cards<br>
<span>
<span style="font-size:20px; ; color:red;">
!!Transactions table: Change to [yourName]_transactions_bronze<br>
!!Credit cards table: Change to [yourName]_creditcards_bronze<br>
<span>
<img src="./images/transactions_bronze.png" alt="alt text" width="1600">
<img src="./images/cards_bronze.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;"> Save and Run, waiting it until Sucess</span>
<img src="./images/bronze_save_run.png" alt="alt text" width="1600">
<img src="./images/bronze_sucess.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;"> Test: In your watsonx.data UI, go to "Query Workspace"-->Catalog-->Schema-->Table-->Generate Select-->Run</span>
<img src="./images/bronze_test.png" alt="alt text" width="1600">
<span style="font-size:20px;"> You can do the same test for the rest two tables</span>

<br><br>
###  <span style="font-size:24px;"> Step 4: Run DataStage Flow -- Silver Layer</span>

<span style="font-size:20px;"> Go back to project and click the "lab2_bronzeLayer" flow </span>
<img src="./images/silver_click.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">
This step will read from 3 bronze tables we just created and:
<span>

1. Cleansing the data (for example, in the customer table, make sure the name is not None)
2. New feature creation (for example, in the transactions, we created a new feature called amount_usd, which is the amount of local currency multiply by exchange rate)

<img src="./images/silver_intro.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px; color:red;">
For 3 sources, make sure the catalog, schema and table align with what you created in the bronze layer.<br>
<img src="./images/silver_source_modify_customer.png" alt="alt text" width="1600">
<img src="./images/silver_source_trans_modify.png" alt="alt text" width="1600">
<img src="./images/silver_source_cards_modify.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">
For 3 targets:
Modify the catalog, shcema and table (taking customers for example)<br>
Catalog: should be "hk_aug_catalog0", change to this if it is not<br>
Shchema: should be "hk_aug_schema0", change to this if it is not<br>
<span>
<span style="font-size:20px; color:red;">
!!Table: Change to [yourName]_customers_silver<br>
<span>
<span style="font-size:20px;">
Click Save <br>
<span>

<img src="./images/silver_target_customers_modify.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">
Do the same for the rest two: transactions and credit cards<br>
<span>
<span style="font-size:20px; ; color:red;">
!!Transactions table: Change to [yourName]_transactions_silver<br>
!!Credit cards table: Change to [yourName]_creditcards_silver<br>
<span>
<img src="./images/silver_target_trans_modify.png" alt="alt text" width="1600">
<img src="./images/silver_target_cards_modify.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;"> Save and Run, waiting it until Sucess</span>
<img src="./images/silver_save_run.png" alt="alt text" width="1600">
<img src="./images/silver_success.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;"> Test: In your watsonx.data UI, go to "Query Workspace"-->Catalog-->Schema-->Table-->Generate Select-->Run</span>
<img src="./images/silver_test.png" alt="alt text" width="1600">
<span style="font-size:20px;"> You can do the same test for the rest two silver tables</span>



