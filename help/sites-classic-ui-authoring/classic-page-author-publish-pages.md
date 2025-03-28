---
title: Publicar páginas
description: Depois de criar e revisar seu conteúdo no ambiente de criação, disponibilize-o em seu site público.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 9%

---

# Publicar páginas{#publishing-pages}

Depois de criar e revisar seu conteúdo no ambiente de criação, disponibilize-o em seu site público (seu ambiente de publicação).

Isso é chamado de publicação de uma página. Quando você deseja remover uma página do ambiente de publicação, este é o processo de desfazer a publicação. Ao publicar ou desfazer a publicação, a página permanecerá disponível no ambiente do autor para mais alterações até ser excluída.

Você também pode publicar/desfazer a publicação de uma página imediatamente ou em uma data/hora predefinida posteriormente.

>[!NOTE]
>
>Alguns termos relacionados à publicação podem ser confundidos:
>
>* **Publicar/Desfazer a publicação**
>  Esses são os termos principais para as ações que tornam o conteúdo publicamente disponível no ambiente de publicação (ou não).
>
>* **Ativar / Desativar**
>  Estes termos são sinônimos de publicar/desfazer a publicação.
>
>* **Replicar / Replicação**
>  Esses são os termos técnicos que descrevem a movimentação de dados (por exemplo, conteúdo da página, arquivos, código, comentários do usuário) de um ambiente para outro, como ao publicar ou reverter a replicação de comentários do usuário.
>

>[!NOTE]
>
>Se você não tiver os privilégios necessários para publicar uma página específica:
>
>* Um fluxo de trabalho será acionado para notificar a pessoa apropriada sobre sua solicitação de publicação.
>* Uma mensagem será exibida (por um curto período de tempo) para notificá-lo sobre isso.
>

## Publicar uma página {#publishing-a-page}

Há dois métodos para ativar uma página:

* [no console Sites](#activating-a-page-from-the-websites-console)
* [do sidekick na própria página](#activating-a-page-from-sidekick)

>[!NOTE]
>
>Você também pode ativar uma subárvore de várias páginas usando [Ativar árvore](#howtoactivateacompletesectiontreeofyourwebsite) no console Ferramentas.

### Ativar uma página no console Sites {#activating-a-page-from-the-websites-console}

Você pode ativar páginas no console Sites. Depois de abrir uma página e modificar seu conteúdo, você retorna ao console Sites:

1. No console Sites, selecione a página que deseja ativar.
1. Selecione **Ativar**, no menu superior ou no menu suspenso do item de página selecionado.

   Para ativar o conteúdo da página e de todas as suas subpáginas, use o console [**Ferramentas**](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#howtoactivateacompletesectiontreeofyourwebsite).

   ![screen_shot_2012-02-08at13817pm](assets/screen_shot_2012-02-08at13817pm.png)

   >[!NOTE]
   >
   >Se necessário, o AEM solicita que você ative ou reative quaisquer ativos vinculados à página. Você pode marcar ou desmarcar as caixas de seleção para ativar esses ativos.
   >
   >

1. Se necessário, o AEM solicita que você ative ou reative quaisquer ativos vinculados à página. Você pode marcar ou desmarcar as caixas de seleção para ativar esses ativos.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. O AEM WCM ativa o conteúdo selecionado. As páginas publicadas aparecem no [console de Sites](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) (marcado em verde) com informações sobre quem ativou o conteúdo e a data e hora da ativação.

   ![screen_shot_2012-02-08at14335pm](assets/screen_shot_2012-02-08at14335pm.png)

### Ativar uma página do Sidekick {#activating-a-page-from-sidekick}

Você também pode ativar uma página quando ela estiver aberta para edição.

Depois de abrir a página e modificar seu conteúdo, você:

1. Selecione a guia **Página** na Sidekick.
1. Clique em **Ativar página**.
Uma mensagem é exibida na parte superior direita da janela confirmando que a página foi ativada.

## Desfazer a publicação de uma página {#unpublishing-a-page}

Para remover uma página do ambiente de publicação, você desativa o conteúdo.

Para desativar uma página:

1. No console Sites, selecione a página que deseja desativar.
1. Selecione **Desativar**, no menu superior ou no menu suspenso do item de página selecionado. Você será solicitado a confirmar a exclusão.

   ![screen_shot_2012-02-08at14859pm](assets/screen_shot_2012-02-08at14859pm.png)

1. Atualize o [console de Sites](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) e o conteúdo está marcado em vermelho, indicando que não está mais publicado.

   ![screen_shot_2012-02-08at15018pm](assets/screen_shot_2012-02-08at15018pm.png)

## Ativar/desativar mais tarde {#activate-deactivate-later}

### Ativar mais tarde {#activate-later}

Para agendar sua ativação para um horário posterior:

1. No console Sites, vá para o menu **Ativar** e selecione **Ativar mais tarde**.
1. Na caixa de diálogo que é aberta, forneça a data e a hora para a ativação e clique em **OK**. Isso cria uma versão da página que é ativada no horário especificado.

   ![screen_shot_2012-02-08at14751pm](assets/screen_shot_2012-02-08at14751pm.png)

Ativar mais tarde inicia um fluxo de trabalho para ativar essa versão da página no horário especificado. Por outro lado, a desativação posterior inicia um fluxo de trabalho para desativar essa versão de página em um momento específico.

Para cancelar essa ativação/desativação, acesse o [Console de Fluxos de Trabalho](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd) para encerrar o fluxo de trabalho correspondente.

### Desativar mais tarde {#deactivate-later}

Para programar a desativação para um momento posterior:

1. No console Site, vá para o menu **Desativar** e selecione **Desativar mais tarde**.

1. Na caixa de diálogo que é aberta, forneça a data e a hora para a desativação e clique em **OK**.

   ![screen_shot_2012-02-08at15129pm](assets/screen_shot_2012-02-08at15129pm.png)

**A desativação atrasada** r inicia um fluxo de trabalho para desativar esta versão da página em um horário específico.

Para cancelar esta desativação, acesse o [Console de Fluxos de Trabalho](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd) para encerrar o fluxo de trabalho correspondente.

## Ativação/Desativação Programada (Hora de Ativação/Desativação) {#scheduled-activation-deactivation-on-off-time}

Você pode agendar a publicação/despublicação de uma página usando o **Momento da ativação** e o **Momento da desativação** que podem ser definidos nas [Propriedades da página](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md).

### Determinação do status de publicação da página {#determining-page-publication-status-classic-ui}

O status pode ser visto no [console de Sites](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console). As cores indicam o status da publicação.

## Ativar uma seção completa (árvore) do site {#activating-a-complete-section-tree-of-your-website}

Na guia **Sites**, é possível ativar páginas individuais. Quando você tiver inserido ou atualizado um número considerável de páginas de conteúdo, todas as quais residem na mesma página raiz, pode ser mais fácil ativar toda a árvore em uma ação. Também é possível executar um Dry Run para emular uma ativação e realçar quais páginas seriam ativadas.

1. Abra o console **Ferramentas** selecionando-o na página **Boas-vindas** e clicando duas vezes em **Replicação** para abrir o console ( `https://localhost:4502/etc/replication.html`).

   ![screen_shot_2012-02-08at125033pm](assets/screen_shot_2012-02-08at125033pm.png)

1. No console **Replicação**, clique em **Ativar árvore**.

   A janela a seguir ( `https://localhost:4502/etc/replication/treeactivation.html`) será exibida.

   ![screen_shot_2012-02-08at125033pm-1](assets/screen_shot_2012-02-08at125033pm-1.png)

1. Insira o **Caminho Inicial**. Especifica o caminho para a raiz da seção que você deseja ativar (publicar). Esta página e todas as páginas abaixo dela são consideradas para ativação (ou usadas na emulação se um Dry Run estiver selecionado).
1. Ative os critérios de seleção conforme necessário:

   * **Somente modificados**: ativar somente páginas que foram modificadas.
   * **Somente ativado**: ativar somente páginas que (já) foram ativadas. Atua como uma forma de reativação.
   * **Ignorar Desativados**: ignorar as páginas que foram desativadas.

1. Selecione a ação que deseja executar:

   1. Selecione **Execução Seca** se quiser verificar quais páginas *seriam* ativadas. Isso é apenas uma emulação, nenhuma página será ativada.

   1. Selecione **Ativar** se desejar ativar as páginas.
