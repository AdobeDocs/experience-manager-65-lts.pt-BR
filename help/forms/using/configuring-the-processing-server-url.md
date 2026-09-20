---
title: Definição das configurações do AEM DS
description: Saiba como especificar a URL do servidor de processamento antes de enviar um formulário.
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 8ad3afd6-e1c6-4f21-bb0f-4d97ef50710e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%
---
# Definição das configurações do AEM DS{#configuring-aem-ds-settings}

Este artigo descreve como configurar o **Serviço de Configurações do AEM DS**. Essa configuração pode ser usada em vários cenários, por exemplo:

* No Gerenciamento de correspondência

  * Para configurar o fluxo de trabalho AEM Forms
  * Ao usar o Portal do Forms para salvar remotamente rascunhos/envios

* Em Formulários adaptáveis, para casos em que um Formulário adaptável é enviado da instância de publicação

Veja a seguir as etapas para configurar as **[!UICONTROL Configurações do AEM DS]**:

1. Abra o Configuration Manager na instância de publicação usando o URL:\
   *https://localhost:port/system/console/configMgr*.

   ![Configuração do AEM Web Console](assets/web_configuration_console_new.png)

1. Na janela **[!UICONTROL Configuração do Adobe Experience Manager Web Console]**, localize e clique na opção **[!UICONTROL Configurações do AEM DS]**.

   ![Configurações DS](assets/ds_settings_new.png)

1. A janela **[!UICONTROL Serviço de Configurações do AEM DS]** exibe as definições de configuração comuns para os Componentes do AEM DS.

   ![Serviço de Configurações DS](assets/ds_settings_service_new.png)

1. Adicione as seguintes informações nos respectivos campos:

   **[!UICONTROL URL do Servidor de Processamento]**: o Servidor de Processamento é o servidor no qual o fluxo de trabalho do Forms ou do AEM deve ser acionado. Pode ser a mesma URL da instância do autor do AEM ou a outra URL do Servidor (ou seja, https://localhost:port/).

   **[!UICONTROL Nome de Usuário do Servidor de Processamento]**: Nome de Usuário do Fluxo de Trabalho [baseado na URL do servidor sendo usada]

   **[!UICONTROL Processando a senha do servidor]**: senha do usuário do fluxo de trabalho

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Ao usar workflows do Forms ou do AEM, antes de fazer qualquer envio a partir do servidor de publicação, é necessário definir o serviço de configurações do DS. Caso contrário, o envio do Formulário não terá êxito.
   >    
   >
