---
title: Problemas de conexão com os serviços de saída, Forms e (documento de registro) DoR
description: Resolva os erros de conexão do AEM Forms após o SP19. Pare, instale o Microsoft Visual C++ e reinicie o servidor para obter uma solução perfeita. Solução de problemas de serviços Output, Forms, DoR.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
hide: true
removedfrom6.5.2025: 'yes'
exl-id: c84ba536-a78d-4cf9-a480-59cb18e41076
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
  - id: f19cff18-c8cc-4a4b-adad-85dd2fa3dbe2
    internal-label: Document Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%
---
# Não é possível usar os serviços de Saída, Forms ou DoR (Documento de Registro) {#unable-to-use-output-service-forms-service-or-document-of-record-service}

## Problema

Depois de instalar o AEM Forms 6.5 Service Pack 19, tentar usar o serviço de Saída, o serviço Forms ou o serviço do Documento de Registro (DoR) pode resultar em um erro `Connection to failed service`.

## Solução

Para resolver o problema:

1. Interrompa a instância do Forms do AEM 6.5.
1. Baixe e instale a versão [64 bits dos pacotes redistribuíveis do Microsoft Visual C++ para Visual Studio 2015, 2017, 2019 e 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) no computador em que o AEM 6.5 Forms está instalado.
1. Reinicie o servidor do AEM Forms.

   >[!NOTE]
   >
   > É recomendável usar o comando &#39;Ctrl + C&#39; para reiniciar o SDK. Reiniciar o AEM SDK usando métodos alternativos, por exemplo, parar processos Java, pode levar a inconsistências no ambiente de desenvolvimento do AEM.


>[!NOTE]
>
>
> Certifique-se de instalar o Redistribuível, mesmo se uma versão anterior estiver instalada.
