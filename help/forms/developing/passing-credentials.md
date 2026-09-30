---
title: Transmitir credenciais usando cabeçalhos de segurança WS
description: Saiba como transmitir credenciais usando cabeçalhos de segurança WS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 558d9b27-8734-4da2-b498-5bb2361ac65b
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '228'
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
