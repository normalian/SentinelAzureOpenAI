# Exercise: Send email with Azure OpenAI on Logic App
First, figure out how to use Azure OpenAI. Try Azure OpenAI with Office 365 mail triggers.

# Outcome: 
As an outcome, you will create a bot service that send your question's answer, Azure OpenAI creates, to an email address.

- **Send a mail**<BR>
  <img width="300" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/d3dbb99a-1689-455e-98ca-6372bb3477c4"><BR>
- **Receive a mail**<BR>
  <img width="560" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/024802d3-351b-478c-97d8-f6f39f2f0f6e">

# Prerequisite 
> Use a resource group in JapanEast region for this exercise
- Create a user account, can receive mail, on your Azure AD tenant.
  - We use ``openai@[tenant name].onmicrosoft.com`` in this exercise.
- Create a resource group in JapanEast region for this exercise with setting as follows.
  - Resource group name: ``rg-Sentinel-AzureOpenAI-Workshop`` 
  - Region: ``Japan East``

<img width="620" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/72c9e870-063e-45b1-9028-2f4f9d952076">


# 1. Overview of the ARM template
> We will deploy a logic app using the ARM template.
- If The Office 365 account receive an email with the title ``OpenAI question``, the logic app queries the mail to Azure OpenAI and reply an email.
- Through this exercise, you can figure out how to configure Azure OpenAI with logic app.

<img width="219" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/f4a7ec8e-84b1-4a7f-8bb4-db53ccda6b4b">


# 2. Deploy the ARM template
Deploy ARM template below on your resource group.

https://github.com/format81/AzureOpenAI-LogicApp


# 3. Setup Azure Logic Apps 
Finish configuration of Azure Logic Apps to run it.

## 3.1 Setup API Authentication of Office 365 Connector
Azure Logic Apps require API authentication for Office 365 account. From the Edit API connection, press "Authorize" and authenticate with the address you receive emails from ( we use ``openai@[tenant name].onmicrosoft.com`` in this example).
<img width="427" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/978a67e1-ee65-4780-86d5-c53e8276923a">

## 3.2 Setup the Azure Logic Apps
### 3.2.1 Register Azure OpenAI API key
Register API key for Azure OpenAI in the Azure Logic Apps.

  - Check Azure OpenAI API key
<img width="837" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/84b99d6d-8f4b-4b55-82e0-54e9272e93c0">

  - Put Azure OpenAI key in your Azure Logic Apps
! [image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/9382ed31-7de0-4f16-a606-55e65f03bfdf)

### 3.2.2 Configure REST API of Azure Logic Apps to use Azure OpenAI on your tenant 
The REST API, deployed on the Azure Logic Apps, has a sample URL, so update the endpoint for your environment.
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/91fa2cd9-0b50-4dbc-b87b-ceac609612a1)

|  Parameter  | Sample |
| ---- | ---- |
| https://your-resource-name.openai.azure.com | https://"your resource endpoint name".openai.azure.com |
| deployment-id | model deployment name |


### 3.2.3 Send a mail the email address
The last step of Azure Logic Apps is to reply a mail to the email address. The Azure Logic App returns ``text`` obtained from Azure OpenAI for the sender of the email.
<img width="525" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/42c05c55-e8b3-48c6-a996-29ba8b6e9c25">

# 4. Have a test
Let's test with Title: "OpenAI question" for the email address you set up.<BR>
After a few minutes, you should get reply from Azure OpenAI.<P>
<img width="299" alt="image" src="https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/5e1fdd8b-7095-4228-9775-b8a1ba4b3326">

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