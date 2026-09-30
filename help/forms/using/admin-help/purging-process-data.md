---
title: Limpando dados do processo
description: Os dados de processo gerados quando um processo de longa duração é chamado podem se tornar muito grandes, resultando em menor desempenho dos formulários AEM e no uso de espaço em disco desnecessário. Veja como você pode limpar dados de processo.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 53ce63a3-704a-4da6-b652-362a436f05a7
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
source-wordcount: '207'
ht-degree: 0%
---
# Limpando dados do processo {#purging-process-data}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Os dados de processo gerados quando um processo de longa duração é chamado podem se tornar muito grandes, resultando em menor desempenho dos formulários AEM e no uso de espaço em disco desnecessário. É uma boa prática limpar os dados do processo quando os registros não são mais necessários. Os formulários do AEM fornecem vários meios de limpar dados de processo:

* Você pode usar o console de administração para executar uma expurgação única de registros obsoletos relacionados a processos de longa duração ou para programar expurgações automáticas regulares. (Consulte [Limpar registros do banco de dados do Gerenciador de Trabalhos](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)
* Você pode usar a API do Java dos formulários do AEM e a API do serviço da Web para limpar programaticamente os dados do processo relacionados aos processos de longa duração. (Consulte &quot;Limpando Dados do Processo&quot; em [Programação com AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63).)
* Use a ferramenta de limpeza de processos para remover processos com base no nome do processo e em outros parâmetros. Para obter detalhes, consulte o arquivo readme da ferramenta de limpeza de processos, em *[raiz de aem_forms]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt.
