---
title: Criação de um guia de início rápido do Assets Folder Headless
description: Use os modelos de fragmento de conteúdo do AEM para definir a estrutura dos fragmentos de conteúdo, a base do seu conteúdo headless.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 78%

---

# Criação de um guia de início rápido do Assets Folder Headless {#creating-an-assets-folder}

Use os modelos de fragmento de conteúdo do AEM para definir a estrutura dos fragmentos de conteúdo, a base do seu conteúdo headless. Os fragmentos de conteúdo são armazenados nas pastas de ativos.

## O que é uma pasta de ativos? {#what-is-an-assets-folder}

[Agora que você criou modelos de fragmento de conteúdo](create-content-model.md) que definem a estrutura desejada para os fragmentos de conteúdo futuros, você provavelmente está animado para criar alguns fragmentos.

No entanto, primeiro será necessário criar uma pasta de ativos na qual você os armazenará.

As pastas do Assets são usadas para [organizar ativos de conteúdo tradicionais](/help/assets/manage-assets.md), como imagens e vídeos e Fragmentos de conteúdo.

## Como criar uma pasta de ativos {#how-to-create-an-assets-folder}

Um administrador só precisaria criar pastas ocasionalmente para organizar o conteúdo, conforme ele fosse criado. Para os propósitos deste guia de introdução, precisamos criar apenas uma pasta.

1. Faça logon no AEM e, no menu principal, selecione **Navegação > Assets > Arquivos**.
1. Clique em **Criar > Pasta**.
1. Forneça um **Título** e um **Nome** para sua pasta.
   * O **Título** deve ser descritivo.
   * O **Nome** se tornará o nome do nó no repositório.
      * Ele será gerado automaticamente com base no título e ajustado de acordo com as [convenções de nomenclatura do AEM.](/help/sites-developing/naming-conventions.md)
      * Ele pode ser ajustado, se necessário.

   ![Criar pasta](assets/assets-folder-create.png)
1. Selecione a pasta que você criou e selecione **Propriedades** na barra de ferramentas (ou use o `p` [atalho de teclado.](/help/sites-authoring/keyboard-shortcuts.md))
1. Na janela **Propriedades**, selecione a guia **Serviços em nuvem**.
1. Para a **Configuração na nuvem**, selecione a [configuração criada anteriormente.](create-configuration.md)
   ![Configurar pasta de ativos](assets/assets-folder-configure.png)
1. Clique em **Salvar e fechar**.
1. Clique em **OK** na janela de confirmação.

   ![Janela de confirmação](assets/assets-folder-confirmation.png)

É possível criar subpastas adicionais dentro da pasta criada. As subpastas herdarão a **Configuração na nuvem** da pasta principal. Isso pode ser alterado, no entanto, se você quiser usar modelos de outra configuração.

Se estiver usando uma estrutura de site localizada, é possível [criar uma raiz de idioma](/help/assets/multilingual-assets.md) abaixo da nova pasta.

## Próximas etapas {#next-steps}

Depois de criar uma pasta para os fragmentos de conteúdo, você pode seguir para a quarta parte do guia de introdução e [criar fragmentos de conteúdo.](create-content-fragment.md)

>[!TIP]
>
>Para obter detalhes completos sobre o gerenciamento de fragmentos de conteúdo, consulte a [documentação dos Fragmentos de conteúdo](/help/assets/content-fragments/content-fragments.md)
