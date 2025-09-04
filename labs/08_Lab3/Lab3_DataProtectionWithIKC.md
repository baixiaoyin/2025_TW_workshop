# Lab 3: Data Protection with IKC

## <span style="font-size:26px;">What would you expect in this lab <span>
With proper configurations in IBM Knowledge Catalog (IKC) and its integration with watsonx.data, different user groups can have customized access to the information within the Iceberg tables in watsonx.data.
1.	Data owners and platform admin would have full access to the table
2.	Data Analytics group would see masked data (like email and data of birth would be masked)

## <span style="font-size:26px;">IBM Knowledge Catalog <span>

IBM Knowledge Catalog connects people to the data and knowledge that they need. The platform is supported by a data governance framework to ensure that data access and data quality are compliant with your business rules and standards. IBM Knowledge Catalog delivers automated enrichment of data assets with business metadata to align company policies and vocabularies to data in support of AI, analytics, and compliance use cases.

IBM Knowledge Catalog provides the methods that your enterprise needs to automate data governance so you can ensure data accessibility, trust, protection, security, and compliance. The service offers comprehensive features to manage governance artifacts, such as business terms, data classes, or classifications, that can be applied to data assets.

The following are the key components that help you understand how to build data governance framework with IBM Knowledge Catalog:

- **Governance Artifacts**: These are reusable components like business terms, data classes, and classifications that add meaning and control to your data assets.
- **Categories**: Collaborative workspaces where governance artifacts are organized and managed with proper access controls and approval workflows.
- **Metadata Enrichment**: Automated process that applies governance artifacts to data assets, adding business context and enabling intelligent data discovery.
- **Data Protection Rules**: Automated policies that enforce data privacy and security by masking or restricting access to sensitive data based on governance artifacts.
- **Catalogs**: Governed repositories where enriched data assets are published and shared across the organization with appropriate access controls.

## <span style="font-size:26px;">Detailed steps <span>
### <span style="font-size:24px;">!! [No Action] Step 1: Create your catalog <span>
 <span style="font-size:20px;">
!! [No Action] <br> 
Go to the left upper cornor "Hamburger" icon-->Catalog-->All Catalog
<span>
<img src="./images/catalog1.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
!! [No Action] <br>
Create a new catalog <br>
Make sure the "Enforce data protection rules" had been checked <br>
Add hk work shop user group as Admin of this catalog <br>
Add cpuser001 as Viewer <br>
<span>
<img src="./images/catalog2.png" alt="alt text" width="1600">
<img src="./images/catalog3.png" alt="alt text" width="1600">
<img src="./images/catalog4.png" alt="alt text" width="1600">
<img src="./images/catalog5.png" alt="alt text" width="1600">
<img src="./images/catalog6.png" alt="alt text" width="1600">
<img src="./images/catalog7.png" alt="alt text" width="1600">

<br><br>
### <span style="font-size:24px;">!! [No Action] Step 2: Create your category with business terms <span>
 <span style="font-size:20px;">
!! [No Action] <br> 
Go to the left upper cornor "Hamburger" icon-->Governanceg-->Category
Create a new category, giving a name and create <br>
Go to the left upper cornor "Hamburger" icon-->Governanceg-->Business terms <br>
Create business terms under the catagory you created, then publish <br>
Repeat business terms creation until all your terms are published (card number, customer phone, etc) <br>
<span>
<img src="./images/catagory1.png" alt="alt text" width="1600">
<img src="./images/catagory2.png" alt="alt text" width="1600">
<img src="./images/catagory3.png" alt="alt text" width="1600">
<img src="./images/catagory4.png" alt="alt text" width="1600">
<img src="./images/catagory5.png" alt="alt text" width="1600">
<img src="./images/catagory6.png" alt="alt text" width="1600">
<img src="./images/catagory7.png" alt="alt text" width="1600">
<img src="./images/catagory8.png" alt="alt text" width="1600">
<img src="./images/catagory9.png" alt="alt text" width="1600">

<br><br>
### <span style="font-size:24px;">!! [No Action] Step 3: Setup data protection rules <span>
 <span style="font-size:20px;">
!! [No Action] <br> 
Go to the left upper cornor "Hamburger" icon-->Governanceg-->Rules
Create a new rule <br>
Set the rule as redacti columns if this column contains credit card number <br>
Create and review<br>

<span>
<img src="./images/rule1.png" alt="alt text" width="1600">
<img src="./images/rule2.png" alt="alt text" width="1600">
<img src="./images/rule3.png" alt="alt text" width="1600">
<img src="./images/rule4.png" alt="alt text" width="1600">
<img src="./images/rule5.png" alt="alt text" width="1600">

<br><br>
### <span style="font-size:24px;">!! Action starts! Step 4: Enrich your data<span>
#### <span style="font-size:22px;">Step 4.1: Metadata import<span>
<span style="font-size:20px;">
Go back to your project and create a new asset <br>
New asset type: "Import metadata for data assets" <br>
Give a name (recommand [your name]_silver_import) <br>
Select "Import asset metadata" and Next<br>
Select "Connections"-->chose "presto-small"<br>
Select data scope: only select the credit cards table you created in lab 1 (should be hk_catalog0->hk_aug_schema0->[yourName]_creditcards_silver_)<br>
Follow the pictures, "Next" all the way to create the job <br>
Wait for a while you will see sucess info <br>
<span>
<img src="./images/enrich1.png" alt="alt text" width="1600">
<img src="./images/metaImport1.png" alt="alt text" width="1600">
<img src="./images/metaImport2.png" alt="alt text" width="1600">
<img src="./images/metaImport3.png" alt="alt text" width="1600">
<img src="./images/metaImport4.png" alt="alt text" width="1600">
<img src="./images/metaImport5.png" alt="alt text" width="1600">
<img src="./images/metaImport6.png" alt="alt text" width="1600">
<img src="./images/metaImport7.png" alt="alt text" width="1600">
<img src="./images/metaImport8.png" alt="alt text" width="1600">
<img src="./images/metaImport9.png" alt="alt text" width="1600">
<img src="./images/metaImport10.png" alt="alt text" width="1600">
<img src="./images/metaImport11.png" alt="alt text" width="1600">
<img src="./images/metaImport12.png" alt="alt text" width="1600">

#### <span style="font-size:22px;">Step 4.2: Enrich the Metadata you just imported<span>
<span style="font-size:20px;">
Go back to your project and create a new asset <br>
New asset type: "Enrich data assets with metadata" <br>
Give a name (recommand [your name]_silver_enrich) <br>
Select the meta data you just imported and Next<br>
Check "Profile Data", "Assign terms and classifications", "Identify data quality checks" and Run data quality analysis <br>
Select "retail_banking_category0" as the Category <br>
Follow the pictures, "Next" all the way to create the job <br>
Wait for a while you will see sucess info <br>
Click the card_number-->on the right side bar-->click the "Assign business terms"-->Assign it to "Credit Card Number" under "retail_banking_category" <br>
Mark it as reviewd and publish <br>
<span>
<span style="font-size:20px;"> !! Note, use "xiaoyinbai_catalog"<span>
<img src="./images/metaEnrich1.png" alt="alt text" width="1600">
<img src="./images/metaEnrich2.png" alt="alt text" width="1600">
<img src="./images/metaEnrich3.png" alt="alt text" width="1600">
<img src="./images/metaEnrich4.png" alt="alt text" width="1600">
<img src="./images/metaEnrich5.png" alt="alt text" width="1600">
<img src="./images/metaEnrich6.png" alt="alt text" width="1600">
<img src="./images/metaEnrich7.png" alt="alt text" width="1600">
<img src="./images/metaEnrich8.png" alt="alt text" width="1600">
<img src="./images/metaEnrich9.png" alt="alt text" width="1600">
<img src="./images/metaEnrich10.png" alt="alt text" width="1600">
<img src="./images/metaEnrich11.png" alt="alt text" width="1600">
<img src="./images/metaEnrich110.png" alt="alt text" width="1600">
<img src="./images/metaEnrich12.png" alt="alt text" width="1600">
<img src="./images/metaEnrich13.png" alt="alt text" width="1600">
<img src="./images/metaEnrich14.png" alt="alt text" width="1600">
<img src="./images/metaEnrich15.png" alt="alt text" width="1600">
<img src="./images/metaEnrich16.png" alt="alt text" width="1600">
<img src="./images/metaEnrich17.png" alt="alt text" width="1600">
<img src="./images/metaEnrich18.png" alt="alt text" width="1600">

<br><br>
### <span style="font-size:24px;">Step 4: Review in the catalog <span>
<span style="font-size:20px;">
Go back to your catalog, go to the new one you just created <br>
Go to "Profile", you can see everything would be visible for you, as you are the owner of this data <br>
Next step, open an Incognito browser page <br>
Go to the same catalog and asset <br>
You will find the credit card number is not visible for you <br>
<span>
<img src="./images/review1.png" alt="alt text" width="1600">
<img src="./images/review2.png" alt="alt text" width="1600">
<img src="./images/review3.png" alt="alt text" width="1600">
<img src="./images/review4.png" alt="alt text" width="1600">

<br><br>
### <span style="font-size:24px;">Step 5: Review in watsonx.data <span>
<span style="font-size:20px;">
Under your own account (hkaug_user0x)->watsonx.data UI->Access Control, check the IKC had been ingegrated and activated <br>
Select 10 rows for your silver crdit cards table (which had been enriched), just as normal, you can see the credit cards number <br>
Go to cpuser001 (Incognito browser)-->watsonx.data <br>
Select same and you will find the credit card number had been masked <br>
<span>
<img src="./images/ikcWxdReview1.png" alt="alt text" width="1600">
<img src="./images/ikcWxdReview2.png" alt="alt text" width="1600">
<img src="./images/ikcWxdReview3.png" alt="alt text" width="1600">





