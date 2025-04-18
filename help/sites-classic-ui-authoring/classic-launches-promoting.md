---
title: Promoção de inicializações
description: É necessário promover as páginas de lançamento para mover o conteúdo de volta para a origem (produção) antes de publicar. Quando uma página de inicialização é promovida, a página correspondente das páginas de origem é substituída pelo conteúdo da página promovida.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 56%

---

# Promoção de inicializações{#promoting-launches}

É necessário promover as páginas de lançamento para mover o conteúdo de volta para a origem (produção) antes de publicar. Quando uma página de lançamento é promovida, a página de origem correspondente é substituída pelo conteúdo da página promovida. As seguintes opções estão disponíveis ao promover uma página de lançamento:

* Promover somente a página atual ou todo o lançamento.
* Promover as páginas secundárias da página atual.
* Promover o lançamento completo ou somente as páginas alteradas.

## Promover páginas de lançamento {#promoting-launch-pages}

Para promover páginas, execute as seguintes etapas ao editar a página de inicialização que deseja promover:

1. Na guia **Página** do Sidekick, clique em **Promover Inicialização**.
1. Especificar as páginas a serem promovidas:

   * (Padrão) Para promover somente a página atual, selecione **Promover alterações de página para versão de produção**.
   * Para promover também as páginas secundárias da página atual, selecione **Incluir subpáginas**.
   * Para promover todas as páginas no lançamento, selecione **Promover Inicialização Completa para Versão de Produção**.

1. Para adicionar as páginas de produção a um pacote de fluxo de trabalho, selecione **Adicionar ao Pacote de Fluxo de Trabalho** e, em seguida, selecione o pacote de fluxo de trabalho.
1. Clique em **Promover**.

## Processamento de Páginas promovidas usando o fluxo de trabalho do AEM {#processing-promoted-pages-using-aem-workflow}

Use modelos de fluxo de trabalho para executar o processamento em massa das páginas de lançamento promovidas:

1. Crie um pacote de fluxo de trabalho.
1. Quando autores(as) promovem as páginas de lançamento, elas são armazenadas no pacote de fluxo de trabalho.
1. Inicie um modelo de fluxo de trabalho usando o pacote como o conteúdo.

Para iniciar um fluxo de trabalho automaticamente quando as páginas forem promovidas, [configure um iniciador de fluxo de trabalho](/help/sites-administering/workflows-starting.md#workflows-launchers) para o nó do pacote.

Por exemplo, você pode gerar solicitações de ativação de página automaticamente quando autores(as) promoverem páginas de lançamento. Configure um iniciador de fluxo de trabalho para iniciar o fluxo de trabalho Solicitar ativação quando o nó do pacote for modificado.

![chlimage_1-136](assets/chlimage_1-136.png)
