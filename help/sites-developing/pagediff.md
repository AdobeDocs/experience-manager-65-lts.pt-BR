---
title: Desenvolvimento e diff de página
description: Saiba como desenvolver e utilizar o recurso de comparação de páginas no Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 10%

---

# Desenvolvimento e diff de página{#developing-and-page-diff}

## Visão geral do recurso {#feature-overview}

A criação de conteúdo é um processo iterativo. A criação com eficiência requer a capacidade de ver o que foi alterado de uma iteração para outra. Visualizar uma versão da página e, em seguida, a outra é ineficiente e sujeita a erros. Um autor deseja poder comparar a página atual com uma versão anterior lado a lado com as diferenças destacadas.

A comparação de páginas permite que um usuário compare a página atual com inicializações, versões anteriores e assim por diante. Para obter detalhes sobre este recurso de usuário, consulte [Diferença de Página](/help/sites-authoring/page-diff.md).

## Detalhes da operação {#operation-details}

Ao comparar versões de uma página, a versão anterior que o usuário deseja comparar é recriada pelo AEM em segundo plano para facilitar o diferencial. Isso é necessário para poder renderizar o conteúdo [para comparação lado a lado](/help/sites-developing/pagediff.md#operation-details).

Essa operação de recriação é feita pela AEM internamente e é transparente para o usuário e não requer nenhuma intervenção. No entanto, um administrador que visualize o repositório, por exemplo, no CRXDE Lite, veria essas versões recriadas na estrutura do conteúdo.

Quando o conteúdo é comparado, a árvore inteira até a página que será comparada é recriada no seguinte local:

`/tmp/versionhistory/`

Uma tarefa de limpeza é executada automaticamente para limpar esse conteúdo temporário.

## Permissões {#permissions}

Anteriormente, na interface clássica, era necessário considerar especificamente o desenvolvimento para facilitar a comparação com o AEM (por exemplo, usar a biblioteca de tags `cq:text` ou personalizar a integração do serviço OSGi `DiffService` em componentes). Isso não é mais necessário para o novo recurso de comparação, pois a comparação ocorre no lado do cliente por meio da comparação de DOM.

No entanto, há algumas limitações que devem ser consideradas pelo desenvolvedor.

* Esse recurso usa classes CSS que não têm namespace para o produto AEM. Se outras classes CSS personalizadas ou classes CSS de terceiros com os mesmos nomes forem incluídas na página, a exibição do diferencial poderá ser afetada.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Como o diferencial é no lado do cliente e é executado no carregamento da página, os ajustes no DOM após a execução do serviço de diferencial do lado do cliente não serão considerados. Isso pode afetar

   * Componentes que usam o AJAX para incluir conteúdo
   * Aplicativos de página única
   * Componentes baseados em JavaScript que manipulam o DOM na interação do usuário.

>[!NOTE]
>
>A comparação de diferenças entre páginas funciona somente para os componentes que têm nós cq:editConfig válidos.
