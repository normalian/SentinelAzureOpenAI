# Exercise: Send email with Azure OpenAI on Logic App
First, figure out how to use Azure OpenAI. Try Azure OpenAI with Office 365 mail triggers.

# Outcome 
As an outcome, you will create a bot service that send your question's answer, Azure OpenAI creates, to an email address.

- **Send a mail**<BR>
  <img width="300" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-01.png"><BR>
- **Receive a mail**<BR>
  <img width="560" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-02.png">

# Prerequisite 
> Use a resource group in JapanEast region for this exercise
- Create a user account, can receive mail, on your Azure AD tenant.
  - We use ``openai@[tenant name].onmicrosoft.com`` in this exercise.
- Create a resource group in JapanEast region for this exercise with setting as follows.
  - Resource group name: ``rg-Sentinel-AzureOpenAI-Workshop`` 
  - Region: ``Japan East``

<img width="620" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-03.png">


# 1. Overview of the ARM template
> We will deploy a logic app using the ARM template.
- If The Office 365 account receive an email with the title ``OpenAI question``, the logic app queries the mail to Azure OpenAI and reply an email.
- Through this exercise, you can figure out how to configure Azure OpenAI with logic app.

<img width="219" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-04.png">


# 2. Deploy the ARM template
Deploy ARM template below on your resource group.

https://github.com/format81/AzureOpenAI-LogicApp


# 3. Setup Azure Logic App 
Finish configuration of Azure Logic App to run it.

## 3.1 Setup API Authentication of Office 365 Connector
Azure Logic App require API authentication for Office 365 account. From the Edit API connection, press "Authorize" and authenticate with the address you receive emails from ( we use ``openai@[tenant name].onmicrosoft.com`` in this example).
<img width="427" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-05.png">

## 3.2 Setup the Azure Logic App
### 3.2.1 Register Azure OpenAI API key
Register API key for Azure OpenAI in the Azure Logic App.

  - Check Azure OpenAI API key
<img width="837" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-06.png">

  - Put Azure OpenAI key in your Azure Logic App
![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-07.png)

### 3.2.2 Configure REST API of Azure Logic App to use Azure OpenAI on your tenant 
The REST API, deployed on the Azure Logic App, has a sample URL, so update the endpoint for your environment.
![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-08.png)

|  Parameter  | Sample |
| ---- | ---- |
| https://your-resource-name.openai.azure.com | https://"your resource endpoint name".openai.azure.com |
| deployment-id | model deployment name |


### 3.2.3 Send a mail the email address
The last step of Azure Logic App is to reply a mail to the email address. The Azure Logic App returns ``text`` obtained from Azure OpenAI for the sender of the email.

<img width="525" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-09.png">

# 4. Run test
Let's test with Title: "OpenAI question" for the email address you set up.<BR>
After a few minutes, you should get reply from Azure OpenAI.

<img width="299" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-01.png">

** Note **
 - Send a mail up to 4,000 characterss to avoid token limitation.
 - Send an email as TEXT email not an HTML email.


# 5. Check some items
Check some items as follows.
  - Check HTTP request/response contents of RESTAPI between Azure Logic App and Azure OpenAI.
  - Check content of the inquiry from Azure Logic App to Azure OpenAI.
  - Check parameters for Azure OpenAI.


# 6. Next Action
> Conguratulation! 

Move forward next exercise as follows.
[Next exercise: Leverage Azure OpenAI with Microsoft Sentinel for incidents](https://github.com/normalian/SentinelAzureOpenAI/blob/main/Work2.md)