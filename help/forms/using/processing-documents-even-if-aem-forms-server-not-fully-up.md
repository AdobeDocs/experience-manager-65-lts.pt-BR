---
title: O AEM Forms Server inicia o processamento dos documentos mesmo antes de todos os serviços estarem em execução.
description: O AEM Forms Server inicia o processamento dos documentos mesmo antes de todos os serviços estarem em execução no JEE Server e no OSGi Server.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 22dd8daa-b8c6-4e7d-bca3-3958a79fb4b5
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
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 3%
---
# O AEM Forms Server inicia o processamento dos documentos antes mesmo que todos os serviços estejam em execução{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Problema {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Antes que o servidor do AEM Forms esteja totalmente ativo e todos os aplicativos estejam em execução, o servidor do AEM Forms inicia o processamento dos documentos.


## Aplica-se a {#applies-to}

A solução se aplica ao AEM Forms no servidor JEE e ao AEM Forms no servidor OSGi.

## Solução {#solution}

Para resolver o problema, adicione um argumento `Dcom.adobe.livecycle.dsc.deferServiceStart=true` ao [arquivo de lote](/help/sites-deploying/command-line-start-and-stop.md#windows-platform-start-bat-script-example) durante a inicialização do servidor.
