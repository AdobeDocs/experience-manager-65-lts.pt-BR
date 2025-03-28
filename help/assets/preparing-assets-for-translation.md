---
title: Preparar ativos para tradução
description: Crie pastas raiz de idioma para preparar ativos para tradução de modo a suportar ativos multilíngues.
contentOwner: AG
role: User, Admin
feature: Projects
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Preparar ativos para tradução {#preparing-assets-for-translation}

Ativos multilíngues são ativos com binários, metadados e tags em vários idiomas. Geralmente, binários, metadados e tags para ativos existem em um idioma, que são traduzidos para outros idiomas para uso em projetos multilíngues.

No [!DNL Adobe Experience Manager Assets], ativos multilíngues são incluídos em pastas, onde cada pasta contém os ativos em um idioma diferente.

Cada pasta de idioma é chamada de cópia de idioma. A pasta raiz de uma cópia de idioma, conhecida como raiz de idioma, identifica o idioma do conteúdo na cópia de idioma. Por exemplo, */content/dam/it* é a raiz do idioma italiano para a cópia do idioma italiano. As cópias de idioma devem usar uma [raiz de idioma configurada corretamente](preparing-assets-for-translation.md#creating-a-language-root) para que o idioma correto seja escolhido quando as traduções dos ativos de origem forem executadas.

A cópia de idioma para a qual você adicionou ativos originalmente é o idioma principal. O idioma principal é a fonte, que é traduzida para outros idiomas. Um exemplo de hierarquia de pastas inclui várias raízes de idioma:

```shell
/content
    /- dam
        |- en
        |- fr
        |- de
        |- es
        |- it
        |- ja
        |- zh
```

Execute as seguintes etapas para preparar seus ativos para tradução:

1. Crie a raiz do idioma do idioma principal. Por exemplo, a raiz de idioma da cópia em inglês na hierarquia de pastas de exemplo é `/content/dam/en`. Verifique se a raiz do idioma está configurada corretamente de acordo com as informações em [Criar uma raiz de idioma](preparing-assets-for-translation.md#creating-a-language-root).

1. Adicione ativos ao idioma principal.
1. Crie a raiz de idioma de cada idioma de destino para o qual você precisa de uma cópia de idioma.

## Criar uma raiz de idioma {#creating-a-language-root}

Para criar a raiz do idioma, crie uma pasta e use um código de idioma ISO como o valor da propriedade Nome. Depois de criar a raiz do idioma, você pode criar uma cópia de idioma em qualquer nível dentro da raiz de idioma.

Por exemplo, a página raiz da cópia em italiano da hierarquia de amostra tem `it` como a propriedade Nome. A propriedade Nome é usada como o nome do nó do ativo no repositório e, portanto, determina o caminho dos ativos. (`https://[aem_server]:[port]/assets.html/content/dam/it/`)

1. No console [!DNL Assets], clique em **[!UICONTROL Criar]** e escolha **[!UICONTROL Pasta]** no menu.

   ![Criar pasta](assets/Create-folder.png)

1. No campo **[!UICONTROL Nome]**, digite o código do país no formato de `<language-code>`.

   ![Adicionar código de idioma na pasta](assets/Add-language-code-in-folder.png)

1. Clique em **[!UICONTROL Criar]**. A raiz do idioma é criada no console [!DNL Assets].

## Exibir raízes de idioma {#viewing-language-roots}

A interface [!DNL Experience Manager] fornece um painel **[!UICONTROL Referências]** que exibe uma lista de raízes de idioma que foram criadas dentro de [!DNL Assets].

1. No console [!DNL Assets], selecione o idioma principal para o qual deseja criar cópias de idioma.
1. No painel esquerdo, selecione a opção **[!UICONTROL Referências]** para abrir o painel [!UICONTROL Referência].

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. No painel Referências, clique em **[!UICONTROL Cópias de idioma]**. O painel [!UICONTROL Cópias de idioma] mostra as cópias de idioma dos ativos.

   ![cópias de idioma](assets/lang-copy2.png)
