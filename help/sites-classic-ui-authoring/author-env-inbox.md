---
title: Sua caixa de entrada
description: Você pode receber notificações de várias áreas do AEM, como notificações sobre itens de trabalho ou tarefas que representam ações que você deve executar no conteúdo da página.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Sua caixa de entrada{#your-inbox}

Você pode receber notificações de várias áreas do AEM, como notificações sobre itens de trabalho ou tarefas que representam ações que você deve executar no conteúdo da página.

Você recebe essas notificações em duas caixas de entrada, que são separadas pelo tipo de notificações:

* Uma caixa de entrada onde você pode ver as notificações que recebe como resultado de assinaturas é descrita na seção a seguir.
* Uma caixa de entrada especializada para itens de fluxo de trabalho está descrita no documento [Participar de fluxos de trabalho](/help/sites-classic-ui-authoring/classic-workflows-participating.md).

## Exibir suas notificações {#viewing-your-notifications}

Para exibir suas notificações:

1. Abra a caixa de entrada de notificações: no console **Sites**, clique no botão usuário no canto superior direito e selecione **Caixa de Entrada de Notificações**.

   ![screen_shot_2012-02-08at105226am](assets/screen_shot_2012-02-08at105226am.png)

   >[!NOTE]
   >
   >Você também pode acessar o console diretamente no seu navegador; por exemplo:
   >
   >
   >` https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Suas notificações estão listadas. É possível realizar ações conforme necessário:

   * [Assinando notificações](#subscribing-to-notifications)
   * [Processamento de notificações](#processing-your-notifications)

   ![chlimage_1-4](assets/chlimage_1-4.jpeg)

## Assinando notificações {#subscribing-to-notifications}

Para assinar notificações:

1. Abra a caixa de entrada de notificações: no console **Sites**, clique no botão usuário no canto superior direito e selecione **Caixa de Entrada de Notificações**.

   ![screen_shot_2012-02-08at105226am-1](assets/screen_shot_2012-02-08at105226am-1.png)

   >[!NOTE]
   >
   >Você também pode acessar o console diretamente no seu navegador; por exemplo:
   >
   >
   >`https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Clique em **Configurar...** no canto superior esquerdo para abrir a caixa de diálogo de configuração.

   ![screen_shot_2012-02-08at11056am](assets/screen_shot_2012-02-08at111056am.png)

1. Selecione o canal de notificação:

   * **Caixa de entrada**: as notificações são exibidas em sua Caixa de entrada do AEM.
   * **Email**: as notificações são enviadas por email para o endereço de email definido em seu perfil de usuário.

   >[!NOTE]
   >
   >Algumas configurações devem ser definidas para serem notificadas por email. Também é possível personalizar o template de email ou adicionar um template de email para um novo idioma. Consulte [Configurar notificação por email](/help/sites-administering/notification.md#configuringemailnotification) para configurar notificações por email no AEM.

1. Selecione as ações de página para as quais deseja ser notificado:

   * Ativado: quando uma página é ativada.
   * Desativado: quando uma página é desativada.
   * Excluída (sindicalização): quando uma página é excluída-replicada, ou seja, quando uma ação de exclusão executada em uma página é replicada.
Quando uma página é excluída ou movida, uma ação de exclusão é automaticamente replicada: a página é excluída na instância de origem em que a ação de exclusão foi executada e na instância de destino definida pelos agentes de replicação.

   * Modificado: quando uma página é modificada.
   * Criado: quando uma página é criada.
   * Excluída: quando uma página é excluída por meio da ação de exclusão da página.
   * Implantada: quando uma página é implantada.

1. Defina os caminhos das páginas para as quais você será notificado:

   * Clique em **Adicionar** para adicionar uma nova linha à tabela.
   * Clique na célula da tabela **Caminho** e insira o caminho, por exemplo, `/content/docs`.

   * Para ser notificado de todas as páginas pertencentes à subárvore, defina **Exato?** a **Não**.
Para ser notificado somente para ações na página definida pelo caminho, defina **Exato?** a **Sim**.

   * Para permitir a regra, defina **Regra** como **Permitir**. Se definida como **Negar**, a regra será negada, mas não removida, e poderá ser permitida posteriormente.

   Para remover uma definição, selecione a linha clicando em uma célula de tabela e clique em **Excluir**.

1. Clique em **OK** para salvar a configuração.

## Processamento de notificações {#processing-your-notifications}

Se você optou por receber notificações na Caixa de entrada do AEM, a caixa de entrada estará cheia de notificações. Você pode [exibir suas notificações](#viewing-your-notifications) e selecionar as notificações necessárias para:

* Aceite clicando em **Aprovar**: o valor na coluna **Ler** está definido como **true**.

* Elimine-a clicando em **Excluir**.

![chlimage_1-5](assets/chlimage_1-5.jpeg)
