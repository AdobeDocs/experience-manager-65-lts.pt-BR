---
title: ContextHub
description: O ContextHub é uma estrutura para armazenar, manipular e apresentar dados de contexto
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,Personalization
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 1%

---

# ContextHub{#contexthub}

O ContextHub é uma estrutura para armazenar, manipular e apresentar dados de contexto. A API do JavaScript do lado do cliente permite acessar os dados para personalizar o conteúdo.

>[!NOTE]
>
>A [implementação de referência do We.Retail](/help/sites-developing/we-retail.md) implementa o ContextHub e pode servir como referência à medida que você integra o ContextHub em seu próprio projeto.

>[!CAUTION]
>
>O caminho que contém a amostra de configuração do ContextHub usada pela [implementação de referência do We.Retail](/help/sites-developing/we-retail.md) ( `/libs/settings/cloudsettings/legacy`) deve ser usado somente como referência para criar sua própria configuração.
>
>Não use em um projeto como sua própria configuração do ContextHub.

## Persistência {#persistence}

O ContextHub armazena dados de contexto persistentes no cliente. A API do ContextHub JavaScript permite acessar armazenamentos para criar, atualizar e excluir dados conforme necessário. Dessa forma, o ContextHub representa uma camada de dados em suas páginas.

Cada armazenamento do ContextHub é uma instância de um tipo de armazenamento predefinido:

* O ContextHub fornece vários [tipos de armazenamento de amostra](/help/sites-developing/ch-samplestores.md).
* Use os consoles do AEM para [criar lojas](ch-configuring.md#creating-a-contexthub-store).
* Os desenvolvedores podem [criar tipos de armazenamento personalizados](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* Os desenvolvedores podem [acessar os dados do armazenamento](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) via JavaScript.

## Segmentação {#segmentation}

O ContextHub inclui um mecanismo de segmentação que gerencia segmentos e determina quais segmentos são resolvidos para o contexto atual. Vários segmentos estão definidos. Você pode usar a API do JavaScript para [determinar segmentos resolvidos](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments).

## Apresentação {#presentation}

A [Barra de ferramentas do ContextHub](/help/sites-authoring/ch-previewing.md) permite que profissionais de marketing e autores vejam e manipulem dados de armazenamento para simular a experiência do usuário ao criar páginas. A barra de ferramentas consiste em grupos de módulos de interface do usuário que fornecem acesso aos armazenamentos do ContextHub.

Cada módulo da interface do usuário do ContextHub é uma instância de um tipo de módulo predefinido:

* O ContextHub fornece vários [tipos de módulo de amostra](/help/sites-developing/ch-samplemodules.md).
* Use os consoles do AEM para [adicionar módulos de interface](ch-configuring.md#adding-a-ui-module) e para [agrupá-los nos modos de interface](ch-configuring.md#adding-a-ui-mode).

* Os desenvolvedores podem [criar tipos de módulo personalizados](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

Os desenvolvedores precisam [adicionar o componente ContextHub à página](/help/sites-developing/ch-adding.md).
