# Lab 0 Enviroment Check 

## What would you expect in this lab

1.	Check access to IBM Cloud Pak for Data (CP4D) Platform Access
2.  Check access to watsonx.data UI
3.	Warmed up: Load a .csv file and test the query with Presto
4.  Generate an API key for next labs

## Detailed steps

###  Step 1: Check your access to IBM CP4D

Open the URL: https://cpd-cpd-instance.apps.itz-7xdwed.infra01-lb.wdc07.techzone.ibm.com/
In the pull down list of the "Log in with" ==> Select "Enterprise LDAP"

In the Username, select the Username, should be tw_sept_user0x (from 01 to 04)

The Password is passw0rd123

<img src="./images/cp4d_login.png" alt="alt text" width="1600">

If everthing is fine, you should see the login page as below

<img src="./images/cp4d_login_sucess.png" alt="alt text" width="1600">

<br><br><br><br>

###  Step 2: Check your access to IBM CP4D

<span style="font-size:20px;">In the CP4D platform, go to the upper right cornor and click the "9 dots".</span>

<img src="./images/tocp4d1.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">And select "IBM Cloud Pak for Data".</span>
<img src="./images/tocp4d2.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Then go to the upper left cornor and click the "Hamburger".</span>
<img src="./images/toInstance1.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">and click "Instances" under "Services".</span>
<img src="./images/toInstance2.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">In the new open "Service instances" page, hover your mouse to the lakehouse and open it.</span>

<img src="./images/openwxdata.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Then you can see another page had been opened. Go to the left side bar, click the "Infrastructure Manager" and you could have a glance of the watsonx.data</span>

<img src="./images/wxdataUI1.png" alt="alt text" width="1600">

<br><br><br><br>

###  Step 3: Warmed up: Load a .csv file and test the query with Presto

<span style="font-size:20px;">Go to the left side bar, click the "Data Manager" and then click the "Ingest Data" on the right upper corner</span>
<img src="./images/csvIngestion1.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Select "Local System"</span>
<img src="./images/csvIngestion2.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">In the right upper cornor, select "Iceberg_data", and drag the csv into the box</span>
<img src="./images/csvIngestion3.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Click "Next"</span>
<img src="./images/csvIngestion4.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Select "iceberg_data" as catalog, "test" as schema==>Create a new table with name [your_test_table_name, like xiaoyin]-test==> click "Preview"</span>
<img src="./images/csvIngestion5.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">You will see the data sample, click "Ingest"</span>
<img src="./images/csvIngestion6.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">You will see an "Finished" Ingestion Job</span>
<img src="./images/csvIngestion7.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Go to life side bar==>Click "Query workspace"==>Go to iceberg_data->test->table you created==>click "</>"==> "Generate Select" ==> "Run on presto-small", you will see the sample data</span>
<img src="./images/csvTest.png" alt="alt text" width="1600">


###  Step 4: Generate API keys for future labs

<span style="font-size:20px;">In the CP4D platform, go to the upper right cornor and click the user icon and then click "Profile and settings".</span>

<img src="./images/API_gen1.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Then "API key" ==> "Generate new key".</span>
<img src="./images/API_gen2.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Click "Gnerate".</span>
<img src="./images/API_gen3.png" alt="alt text" width="1600">

<br><br>
<span style="font-size:20px;">Copy and store your API key somewhere, you will need it later!</span>
<img src="./images/API_gen4.png" alt="alt text" width="1600">