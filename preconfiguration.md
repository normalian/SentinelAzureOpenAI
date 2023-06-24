# Prerequisite
Before starting this exercise, Azure OpenAI service must be activated on your Azure subscription. Refer to following steps and set up Azure OpenAI service.

# 1: Create Azure OpenAI resource
- You can activate Azure OpenAI service on your subscription after approving your application form.
- Configure resourcegroup, region, Azure OpenAI service resource name, and pricing tier.
  - The price tier is only ``Standard S0`` as of June 2023.
  - This Azure OpenAI resource will be accessed from Azure Logic Apps in this workshop, thus select ``All networks, including the internet, can access this resource.`` option.
- It takes **about 7 minutes** to create Azure OpenAI resource. 
<img width="424" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/img/preconfiguration-01.png">

# 2: Check Endpoint and API Key
- Check endpoint and API Key of your Azure OpenAI. 
- Endpoint and API Key
  - ![image](https://github.com/normalian/SentinelAzureOpenAI/img/preconfiguration-02.png)

# 3: Deploy a model
Create a model for Azure OpenAI. First, open Azure AI Studion from "Model Deployments" -> "Manage Deployments" menus on Azure Portal. Then, create a model on Azure AI Studion.
<img width="930" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/img/preconfiguration-03.png">

- Refer to [Azure OpenAI Service models](https://learn.microsoft.com/azure/cognitive-services/openai/concepts/models) to check the detail of Azure OpenAI models 
- Use Davinci model on this exercise.
  -   ``text-davinci-003``
  -   ``gpt35-turbo``

# Next Action
Go to [Exercise: 1](https://github.com/normalian/SentinelAzureOpenAI/blob/main/Work1.md) after completing to create Azure OpenAI resource.

