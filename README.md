# Workshop for  Microsoft Sentinel / Azure Open AI
This workshop enable you to configure Microsoft Sentinel to create incident and trigger Azure OpenAI GPT/ChatGPT.
![image](https://github.com/hisashin0728/SentinelAzureOpenAI/assets/55295601/96135a01-3aff-471a-8a37-0c373fd50db4)

# Objective 

> The purpose of this exercise is to provide training content for leveraging Microsoft Sentinel incidents with Azure OpenAI.

- Create an environment to leverage Azure OpenAI from Microsoft Sentinel
- Understand the model of Azure OpenAI Logic App through this exercise / Consider the use of Prompt

# Prerequisite
Prerequisites are as follows. You will incur Azure resources fee through this exercise.

- Create Microsoft Sentinel resource on your tenant
- Enable Azure OpenAI on your subscription **( You have to complete Request Access as follows before starting this exercise as of 31th May 2023 )**
  -   https://customervoice.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR7en2Ais5pxKtso_Pz4b1_xUOFA5Qk1UWDRBMjg0WFhPMkIzTzhKQ1dWNyQlQCN0PWcu
- Enable to launch an alert to Microsoft Sentinel based on some analysis rules.
  - Microsoft Sentinel connects to Microsoft Defender for Cloud with data connector, then you use sample alerts from Microsoft Defender for Cloud in this exercise.

# Contents
Follow steps as follows.
- [Before hands-on Create Azure OpenAI resource](https://github.com/normalian/SentinelAzureOpenAI/blob/main/preconfiguration.md)
- [Exercise 1: Make a mail response with Azure OpenAI and Logic Apps](https://github.com/normalian/SentinelAzureOpenAI/blob/main/Work1.md)
- [Exercise 2: Leverage Microsoft Sentinel trigger and translate analysis rule with Azure OpenAI using Logic Apps](https://github.com/normalian/SentinelAzureOpenAI/blob/main/Work2.md)
- [Lookback: How can we leverage Azure OpenAI prompt](https://github.com/normalian/SentinelAzureOpenAI/blob/main/Work3.md)
- [Excercise 3: Advanced - Custmize inquiry to Azure OpenAI based on incident of Microsoft Sentinel](https://github.com/normalian/SentinelAzureOpenAI/blob/main/Work4.md)

- [FAQ](https://github.com/normalian/SentinelAzureOpenAI/blob/main/FAQ.md)

# Disclaimer
> Exercises in this repository will incur charges of Azure resources.
- The user is responsible for any costs incurred by this exercise.
- The author is not responsible for outcome from this exercise.
- This repository is open source.
