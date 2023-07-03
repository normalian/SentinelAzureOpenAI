# Advanced
> Let's consider leveraging Azure OpenAI to further use Microsoft Sentinel incidents.

We have practical use cases to further leverage both Microsoft Sentinel and Azure OpenAI in this exercise.

# 1. Ideas for practical use cases 
> Ideas for security operators to leverage Microsoft Sentinel incident information.

## Use Case 1 - Add overview of MITRE tactics
Add comments based on MITRE tactics included in the analysis rules as supplementary information.

- Example - prompt 
```
Describe the MITRE Tactics ###["LateralMovement", "Execution"]### up to 100 words.
```

- Example - Chat Completion API
```
[
  {
    "role": "system",
    "content": "You are a security analytist."
  },
  {
    "role": "user",
    "content": "I want you to summarize the content of MITRE tactics up to 100 words."
  },
  {
    "role": "assistant",
    "content":"["LateralMovement", "Execution"]"
  }
]
```

<img width="697" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work4-01.png">

## Use Case 2 - Summarize Incident from Incident Title and Incident Description
Send all information of the incident to ChatGPT and summarize it.

- Example - prompt
``` I am a security analyst.
I am a security analyst. I need a summary of a security incident up to 1000 characters.

### [incident title], [incident description], [incident entity] ###
```

- Example - Chat Completion API
```
[
  {
    "role": "system",
    "content": "You are a security analytist."
  },
  {
    "role": "user",
    "content": "I want you to summarize the content of the security incident up to 1000 characters."
  },
  {
    "role": "assistant",
    "content": "[incident title], [incident description], [incident entity]"
  }
]
```

## Use Case 3 - Suggest a KQL query for hunting
Suggest a KQL to identify the incident using the analysis rule name, supplemental content, and ChatGPT primary response.

- Example - prompt 
````
Suggest a KQL to investigate a threat with Microsoft Sentinel.

###
Someone has uploaded an executable file to your Azure storage account "Sample-Storage" in an unusual manner. This alert was triggered by an ADLS Gen2 transaction.
###
```

- Example - Chat Completion API
```
[
  {
    "role": "system",
    "content": "You are a security analytist."
  },
  {
    "role": "user",
    "content": "Suggest a KQL query to search the incident, up to 3000 characters."
  },
  {
    "role": "assistant",
    "content": "[incident title], [incident description], [incident entity]"
  }
]
```

<img width="698" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work4-02.png">


# 2. Leverage Azure OpenAI for Microsoft Sentinel incidents with gpt-3.5-turbo/GPT4
> Let's leverage Azure OpenAI for various use cases.

Let's Leverage ARM template template which leverages Azure OpenAI ChatGPT/GPT3 from incident information using Azure Logic App. In this section, the ARM template creates Chat Completion API using ChatGPT3.5turbo or GPT4, thus select ``GPT35-turbo`` as the model to deploy.
- Incident Summary
- Incident supplementary information in your natural language - Your Azure Logic App translates into Japanese
- Incident

![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work4-03.png)

# Prerequisite
> Deploy the ARM template a resource groups in JapanEast
- Create a resource group for other Azure resources you will create in this exercise for example Azure Logic App or others. You can use same resource group with exercise 1.
- The following are sample configurations. We assume that the region is East Japan.
  - Resource group name is ``rg-Sentinel-AzureOpenAI-Workshop``.
  - Azure region is ``Japan East``.
  - Azure OpenAI model is ``gpt-35-turbo``.
<img width="723" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work4-04.png">


# 3. Deploy the ARM template
Click a button below and deploy Azure resources with the ARM template.<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fnormalian%2FSentinelAzureOpenAI%2Fmain%2FtemplateEnrichmentGPT35.json)

# 4. Configuration
Setup [Azure Logic App](https://github.com/normalian/SentinelAzureOpenAI/blob/main/Work2.md#3-setup-azure-logic-apps) as follows.
- Update the REST API URI of Azure OpenAI.
  - ``https://{yourname}.openai.azure.com/openai/deployments/{yourmodel}/chat/completions?api-version=2023-05-15``
  - Make sure that your REST API URI is updated.
- Grant "**Sentinel Responder**" and "**Cognitive Services OpenAI User**" roles for Managed Identity of the Azure Logic App
- Create an Automation Rule of Microsoft Sentinel 

# 5. Run
> Create sample alerts and check how ChatGPT/GPT3 updates the incidents.

The ARM template allows features as follows.
 - **Translation the rule into Japanese**
  - ![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work4-05.png)
 - **Add Tag**
  - ![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work4-06.png)
 - **Add summary of the incident**
  - ![image](https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work4-07.png)
 - **Suggest KQL for the incident**
  - <img width="316" alt="image" src="https://github.com/normalian/SentinelAzureOpenAI/blob/main/img/work4-08.png">

# 6. Try another ideas!
> Change the deployed Azure resources and make some ideas to leverage Azure OpenAI in your cases.

# 7. Congratulation! You have worked out all exercise.
> You have completed, so remove deployed resources.

- Refer to [FAQ](https://github.com/normalian/SentinelAzureOpenAI/blob/main/FAQ.md). You can find popular questions.
- Give us feedback for this exercise. Send your message on via [Discussion](https://github.com/normalian/SentinelAzureOpenAI/discussions).

# 8. [Survey](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbRz9kK29SrCBLqv7mxsgrvl9UQVdETVBLTjNaQ1RJVVBPV1RWSDNSSzgxWC4u)
> Give us your comments. It motivates us.
