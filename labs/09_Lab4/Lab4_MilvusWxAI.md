# Lab4: Data platform for GenAI 

## <span style="font-size:26px;">What would you expect in this lab <span>
Build your own Vector Database and working with IBM watsonx.AI
1.	Ingest PDFs into Milvus on watsonx.data.
2.	"Talk" to your PDFs (vectors in the Milvus)

## <span style="font-size:26px;">Detailed steps <span>
### <span style="font-size:24px;">Step 1: Set up your watsonx.AI <span>
 <span style="font-size:20px;">
 Log in the watsonx.AI (URL, username and password would be in another file)
<span>
<img src="./images/wxailogin.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
 Click the left top corner's "Hamburger" and go to "Resource List"
<span>
<img src="./images/resourceList.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Go to "AI/Machine Learning" and click the resource with Product of watsonx.Aai Runtime, please notice the Group as well
<span>
<img src="./images/resourceList2.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
In the next page, go to "Launch in" pull down list and select "IBM watsonx"
<span>
<img src="./images/gotowxai.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
In the watsonx.AI, similar as for CP4D, go to left upper corner "Hamburger"-->"View all projects"-->"New project"
<span>
<img src="./images/creatProject1.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Give a project name and create it
<span>
<img src="./images/createProject2.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Associate the watsonx.AI service: In the project, go to "Manager" --> Associate Service
<span>
<img src="./images/associateService1.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Check the only service you could see and click "Associate"
<span>
<img src="./images/associateService2.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Go to prompt lab
<span>
<img src="./images/openPromptLab.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Then start to test the chat function <br>
You can change the LLM if you want
<span>
<img src="./images/chatTest.png" alt="alt text" width="1600">

### <span style="font-size:24px;">Step 2: Build Milvus Connection <span>
 <span style="font-size:20px;">
In the chatting UI, go to right upper corner and click "Grounding with Documents" (you might need to clear the chat)
<span>
<img src="./images/milvus1.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
New vector index
<span>
<img src="./images/milvus2.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Select Milvus and create a new connection
<span>
<img src="./images/milvus3.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
!!Note, this step is at watsonx.data UI <br>
Go to "Infrastructure manager"-->Milvus <br>
View Connection Details <br>
Copy Json Snippet <br>
Select Database as default and "Copy to clipboard" <br>

<span>
<img src="./images/milvus4.png" alt="alt text" width="1600">
<img src="./images/milvus5.png" alt="alt text" width="1600">
<img src="./images/milvus6.png" alt="alt text" width="1600">
<img src="./images/milvus7.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
!!Note, go back to watsonx.AI UI <br>
Enter Json Snippet <br>
Paste and Enter <br>
Enter username, password, test and create <br>

<span>
<img src="./images/milvus8.png" alt="alt text" width="1600">
<img src="./images/milvus9.png" alt="alt text" width="1600">
<img src="./images/milvus10.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Give an index name <br>
Select database as default <br>
Select an embedding model <br>
Next <br>
<span>
<img src="./images/milvus11.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
New collection <br>
Give a collection name-->Select Chunk Size and Overlap size-->Upload PDFs-->Create <br>
<span>
<img src="./images/milvus12.png" alt="alt text" width="1600">
<img src="./images/milvus13.png" alt="alt text" width="1600">

<br><br>
 <span style="font-size:20px;">
Waiting until the index is ready <br>
Test "talking" with Milvus<br>
<span>
<img src="./images/milvus14.png" alt="alt text" width="1600">
<img src="./images/chatWithMilvus.png" alt="alt text" width="1600">