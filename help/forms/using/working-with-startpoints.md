---
title: Trabalhar com pontos iniciais
description: Etapas para trabalhar com um processo do Adobe Experience Manager Forms no dispositivo móvel definido no Workbench.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 88a4a75f-2cd7-44b8-a9d0-9a7077173c67
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
source-wordcount: '235'
ht-degree: 0%
---
# Trabalhar com pontos iniciais{#working-with-startpoints}

Um ponto inicial invoca um processo criado no Workbench. Está associado a um formulário que chama o processo quando o formulário é enviado.

>[!NOTE]
>
>Os termos pontos de partida, processo de início e formulário são usados alternadamente ao se referirem a esse conceito.

Para iniciar um processo do aplicativo Forms do Adobe Experience Manager (AEM), você deve ter um ponto de partida do tipo **Workspace** em seu processo. Além disso, você deve selecionar a opção **[!UICONTROL Visível no Mobile Workspace]** para o ponto de partida.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Para iniciar um processo definido no Workbench**

1. Para exibir os pontos iniciais disponíveis no aplicativo AEM Forms, vá para [Tela inicial](../../forms/using/home-screen.md).
1. Na tela **[!UICONTROL Página Inicial]**, por padrão, a lista **[!UICONTROL Todas as Forms]** é exibida.

   O ponto inicial está associado a um formulário. Selecione o ponto inicial associado ao formulário na lista para abri-lo.

   O formulário associado ao ponto inicial é aberto.

1. Insira os detalhes no formulário **[!UICONTROL Startpoint]**.

   Você pode adicionar anotações a esta tarefa usando o botão [anexo](../../forms/using/add-attachments.md).

1. Depois de preencher o formulário, clique no botão **[!UICONTROL Enviar]**.

Se o aplicativo estiver offline, o formulário e seus dados serão salvos na pasta Caixa de saída.

Se o aplicativo estiver online, a tarefa será sincronizada com o AEM Forms Server e atribuída ao usuário especificado no processo.

Para trabalhar com a tarefa na sua lista de tarefas, consulte [Abrindo uma tarefa](/help/forms/using/open-task.md).
