# Exercise: Leverage Azure OpenAI with Microsoft Sentinel for incidents
> Query to Azure OpenAI based onIncident Trigger of Microsoft Sentinel  

When an incident of Microsoft Sentinel occurs, query Azure OpenAI and translate the analysis rules into other natural launguage.

# Outcome
When a Sentinel incident is detected, the outcome of this excercise describes the detail of the inccident by using ChatGPT.
![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work2-01.png)

# Prerequisite 
> Deploy the templates on a resource group in Japan East 
- Create a resource group for Azure resources you will create in this exercise (e.g., Azure Logic App, etc.)
- The following is a sample configuration. You can use the same resource group as in exercise 1. We assume that the region is East Japan.
- Resource group name ``rg-Sentinel-AzureOpenAI-Workshop`` 
- Region ``Japan East``

<img width="620" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work1-03.png">

# 1. Overview of the template 
> The ARM template deploys Azure Logic App.

- Microsoft Sentinel allows you to perform various automation processes by using Azure Logic App. 
- With this ARM template, you can query Azure OpenAI when an incident occurs and use the prompt to translate the analysis rule.

<img width="1080" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work2-03.png">

# 2. Deploy the ARM template
Deploy the ARM template from the following button<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelAzureOpenAI%2Fmain%2Ftemplate.json)

# 3. Setup Azure Logic App
Setup Azure Logic App with the same settings as in exercise 1.

## 3.1 Azure Logic App - assign role to managed identity
Unlike Exercise 1, access Azure OpenAI securely by using a managed ID.<BR>
In order to enable the Azure Logic App to update Microsoft Sentinel incidents, assign the following two roles to the Managed ID of the Azure Logic App:<BR>
- **Sentinel Responder**
- **Cognitive Services OpenAI User**

Rrant roles on a subscription basis, not on a resource group as possible.
- You have to grant Sentinel Responder role to a resource group which has a Microsoft Sentinel resource.
- You have to grant Cognitive Services OpenAI role to a resource grrop which has a Azure OpenAI resource. 

[2023.5.18 Update] [We can access Azure OpenAI with managed identity assigned Cognitive Service OpenAI User privilege](https://zenn.dev/microsoft/articles/call-openai-from-logicapps-with-managedid) - This article is written in Japanese, so use translation to read the detail.

<img width="826" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work2-04.png">

## 3.2 Configure REST API on Azure Logic App
The REST API endpoint of the deployed Azure Logic App is setup with a sample URL. Update the URL for your environment. 

![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work2-05.png)

|  Parameter  | Sample |
| ---- | ---- |
| https://your-resource-name.openai.azure.com | https://"your resource endpoint name".openai.azure.com |
| deployment-id | model deployment name |



## 3.3 Sentinel - Configure "Playbook permissions"
Configure permissions to allow Microsoft Sentinel access to your Azure Logic App, so go to "Settings" and grant access permissions for the playbook.
![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work2-06.png)

## 3.4 Sentinel - Automation rule to automatically start the playbook
Finally, create an automation rule so that the playbook is activated when an incident occurs.
If you have pre-configured your playbook, such as email notifications, you can set it up before notification so that you are notified of the Japanese translated content.


## 3.4 Sentinel - Trigger the playbook with the automation rule
Create an automation rule to trigger the playbook when an incident occurs. You can get translated notification with this automation rule if you have pre-configured your playbook to notify via email.

<img width="372" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work2-07.png">

# 4. Test
> Perform the test!
Generate a sample security alert for Microsoft Sentinel.
- [Alert validation in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alert-validation#generate-sample-security-alerts)

# 5. Checklist
> Validte topics as follows.
  - How was the Sentinel analysis rules translated?
  - What prompt was sent to Azure OpenAI?
  - How was the Sentinel incident updated?
  - Were any parameters set for Azure OpenAI?

# 6. Next Action
> Congratulation!

Move to next section [Lookback](https://github.com/hisashin0728/SentinelAzureOpenAI/blob/main/Work3.md).
