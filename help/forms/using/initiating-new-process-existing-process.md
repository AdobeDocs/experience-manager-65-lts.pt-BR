---
title: Iniciar um novo processo com dados de processo existentes no espaço de trabalho do AEM Forms
description: Veja como iniciar um novo processo com dados de processo existentes no espaço de trabalho do AEM Forms.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Iniciar um novo processo com dados de processo existentes no espaço de trabalho do AEM Forms{#initiating-a-new-process-with-existing-process-data-in-aem-forms-workspace}

É possível iniciar um novo processo usando os dados de um processo existente. A necessidade de iniciar um novo processo a partir dos dados de processo existentes surge quando precisamos usar o mesmo formulário frequentemente com poucas alterações no conteúdo, como o dos formulários de tempo livre pago. Esse recurso economiza tempo e esforço dos usuários, especialmente quando o processo tem um longo formulário para preencher.

Veja a seguir as etapas para iniciar um novo processo a partir dos dados existentes do processo:-

1. Execute uma das seguintes ações:

   * Em Tracking, clique na instância do processo cujos dados você deseja usar. Na exibição Histórico do processo no painel direito, clique na linha de tarefa que corresponde ao ponto inicial.
   * Em Rastreamento, selecione um modelo de pesquisa para exibir uma lista de instâncias de processo. Selecione a instância cujos dados você deseja usar.
   * Na guia **[!UICONTROL Tarefa Pendente]**, selecione a tarefa. Clique na guia **[!UICONTROL Histórico]** e selecione a tarefa que iniciou a instância do processo.

   ![Selecionar a tarefa](assets/start3_new.png) ![Selecionar a tarefa](assets/start1_new.png)

1. Na barra de ferramentas da ação Tarefa, clique em **[!UICONTROL Iniciar]**. Um formulário adaptável para a nova instância do processo é exibido com dados preenchidos previamente.

1. Atualize os dados conforme necessário e clique em **[!UICONTROL Concluir]** ou em um botão apropriado no formulário.
