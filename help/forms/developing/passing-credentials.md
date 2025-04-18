---
title: Transmitir credenciais usando cabeçalhos de segurança WS
description: Saiba como transmitir credenciais usando cabeçalhos de segurança WS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 558d9b27-8734-4da2-b498-5bb2361ac65b
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Transmitindo credenciais usando cabeçalhos de Segurança WS {#using-execute-script-service-aem-forms-jee-workbench}

Ao chamar um serviço AEM Forms no JEE usando serviços da Web, você pode usar cabeçalhos de segurança WS para transmitir informações de autenticação do cliente exigidas pelo AEM Forms no JEE. O WS-Security define as extensões do SOAP para implementar a autenticação de cliente, a confidencialidade da mensagem e a integridade da mensagem. Como resultado, você pode chamar os serviços do AEM Forms no JEE quando o AEM Forms no JEE for implantado como servidor independente ou em um ambiente em cluster.

A forma como você passa cabeçalhos de segurança de WS para o AEM Forms no JEE depende de você estar usando classes Java geradas pelo Axis ou um assembly cliente .NET que consome a pilha nativa do SOAP de um serviço.

>[!NOTE]
>
>Como um exemplo de chamada de um serviço usando cabeçalhos WS-Security, este tópico criptografa um documento PDF com uma senha chamando o serviço de Criptografia.

Este documento abrange os seguintes tópicos:

* Passagem da autenticação do cliente usando classes Java geradas pelo Axis

* Geração de arquivos da biblioteca do Axis necessários para chamar o serviço de criptografia

* Chamar o serviço de criptografia usando um cabeçalho WS-Security

* Passando autenticação de cliente usando um assembly de cliente .NET

* Chamar o serviço de criptografia usando um cabeçalho WS-Security


## Requisitos {#requirements}

Para aproveitar ao máximo este documento, você precisa ter uma sólida compreensão do AEM Forms no software JEE.

>[!MORELIKETHIS]
>
>* [Passando credenciais usando cabeçalhos WS-Security](assets/passing-credentials-using-ws-security-headers.pdf)
