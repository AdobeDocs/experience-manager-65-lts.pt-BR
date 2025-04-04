---
title: Aplicação de fluxos de trabalho a páginas
description: Os fluxos de trabalho podem ser iniciados no console Sites ou, ao editar uma página, no Sidekick.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 15%

---

# Aplicação de fluxos de trabalho a páginas{#applying-workflows-to-pages}

Ao aplicar o fluxo de trabalho, especifique as seguintes informações:

* O fluxo de trabalho a ser aplicado.

  É possível aplicar qualquer fluxo de trabalho (ao qual você tenha acesso, conforme atribuído pelo administrador do AEM).
* Opcionalmente:

   * Um comentário que fornece informações sobre por que você iniciou o fluxo de trabalho.
   * Um título que ajuda a identificar a instância do fluxo de trabalho na Caixa de entrada de um usuário.

>[!NOTE]
>
>Os administradores do AEM podem iniciar fluxos de trabalho usando [vários outros métodos](/help/sites-administering/workflows-starting.md).

## Aplicação de fluxos de trabalho {#applying-workflows}

Os fluxos de trabalho podem ser iniciados no console Sites ou, ao editar uma página, no Sidekick.

A coluna **Status** no console **Sites** indica se um fluxo de trabalho foi aplicado a uma página:

![status do fluxo de trabalho](assets/workflowstatus.png)

### Iniciar um fluxo de trabalho a partir do console Sites {#starting-a-workflow-from-the-websites-console}

1. Abra o console Sites. ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin))
1. Na árvore Sites, selecione a página principal à qual deseja aplicar o fluxo de trabalho.
1. Na lista da página, selecione a página e clique em Fluxo de trabalho.
1. Na caixa de diálogo Iniciar fluxo de trabalho, selecione o fluxo de trabalho a ser aplicado. Opcionalmente, insira um comentário e um título. Em seguida, clique em Start.

### Iniciar um fluxo de trabalho usando o Sidekick {#starting-a-workflow-using-sidekick}

1. Abra o console Sites.
1. Abra a página desejada.
1. Selecione a guia Fluxo de trabalho no Sidekick.
1. Expanda a caixa de diálogo **Fluxo de Trabalho**, que permite selecionar o **Fluxo de Trabalho** e, opcionalmente, inserir o **Título do Fluxo de Trabalho** e o **Comentário**.

   ![workflowstartsidekick](assets/workflowstartsidekick.png)

1. Clique em **Iniciar Fluxo de Trabalho** para iniciar uma nova instância de fluxo de trabalho com as propriedades que você configurou e a página atual como carga. Agora, o workflow está em execução.
