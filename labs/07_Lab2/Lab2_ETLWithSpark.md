# Lab2 ETL with Spark

## <span style="font-size:26px;">What would you expect in this lab</span>

1.	Create a gold layer table: customer_risk_360 gold.
2.	Create another gold layer table: customer_campaign_360 gold.

## <span style="font-size:26px;"> Introduction</span>
For the customer_risk_360 gold table, we: <br>
1. Join the 3 tables together
2. Create some features like <br> 
    2.1 Transactions behavior risk features, like payment diversity  <br>
    2.2 Credit utilization risk features, like total spend <br>
    2.3 Monthly spending changes <br>
    2.4 Comprehensive rish score based on 2.1-2.3 <br>

For the customer_campaign_360 gold table, we: <br>
1. Join the 3 tables together
2. Create some features like <br> 
    2.1 Spending channel analyse features  <br>
    2.2 Category spending analyse features <br>
    2.3 Customer profile features <br>
    2.4 Comprehensive campaign categories assignment based on 2.1-2.3 <br>

Why do not us use the DataStage? <br>
Some complex functions, like monthly rolling features, would be easy to create in code.

## <span style="font-size:26px;"> Detailed steps</span>


### <span style="font-size:24px;"> Step 1: Open the notebook and modify the parameters</span>

<span style="font-size:20px;">In assets of the project, open the "lab2_ETLwithSpark".</span>

<img src="./images/lab2_open.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Click Edit on the right upper conner"</span>
<img src="./images/notebookEdit.png" alt="alt text" width="1600">

### <span style="font-size:24px;"> Step 2: Modify the parameters</span>
<br><br>
<span style="font-size:20px;">Modify the parameters, based on the instructions: <br> </span>
<span style="font-size:20px;">
username: your user name <br>
wxd_apikey: the apikey you created on lab0 <br>
username: your user name <br>
wxd_apikey: the apikey you created on lab0 <br>
catalog_name = "hk_aug_catalog0" ; No need to change but please confirm it align with your silver tables catalog <br> 
schema_name = "hk_aug_schema0" ## No need to change No need to change but please confirm it align with your silver tables schema <br> 
transactions_silver_table = "xy1_transactions_silver"   Need to change, the silver transactions table you just created  <br>
cards_silver_table = "xy1_creditcards_silver"   Need to change, the silver credit cards table you just created <br>
customers_silver_table = "xy1_customers_silver"   Need to change, the silver customers table you just created <br>
gold_risk_table = "xy1_customers_risk_360"   Need to change, the gold customer risk table name, should be [your name]_customers_risk_360 <br>
gold_campaign_table = "xy1_customers_campaign_360"  Need to change, the gold customer campaign table name, should be [your name]_customers_campaign_360 

</span>
<img src="./images/paramSet.png" alt="alt text" width="1600">

### <span style="font-size:24px;"> Step 3: Run the notebook</span>
<br><br>
<span style="font-size:20px;">Go to the top and under "Run" click "Run All Cells"
</span>
<img src="./images/runNotebook.png" alt="alt text" width="1600">
<br><br>
<span style="font-size:20px;">After a short while (maybe long while ^_^!!), you will find the notebook had been executed sucessfully"
</span>
<img src="./images/notebook_success.png" alt="alt text" width="1600">
<br><br>
<span style="font-size:20px;">Similarly, you can test the gold tables in watsonx.data UI"
</span>
<img src="./images/goldTest.png" alt="alt text" width="1600">