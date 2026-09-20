---
title: Personalizando guias para uma tarefa
description: Como personalizar os nomes das guias para suas tarefas, no espaço de trabalho do LiveCycle AEM Forms.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 88f5093c-f249-4e4b-900a-5897f47e513c
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%
---
# Personalizando guias para uma tarefa {#customizing-tabs-for-a-task}

Você pode personalizar nomes de guia para o componente `Start Process` no modo de exibição Uber `Start Process` e o componente `Task Details` no modo de exibição Uber `ToDo`.

1. Siga as [etapas genéricas para personalização do espaço de trabalho do AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Alterar o valor de `tabname` no arquivo `translation.json`.

   Por exemplo, altere `/apps/ws/locales/en-US/translation.json` para inglês.

   * Para tarefas iniciadas no processo de início, use o seguinte trecho do bloco `"startprocess" : {}`.

   ```json
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Para tarefas em Tarefas Pendentes, use o seguinte trecho do bloco `"todo" : {}`.

   ```json
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Adicione o par de valor principal correspondente para todos os idiomas compatíveis.
