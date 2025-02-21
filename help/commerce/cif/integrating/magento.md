---
title: Integração do AEM e da Adobe Commerce usando o Commerce integration framework
description: O AEM e o Adobe Commerce são perfeitamente integrados usando o Commerce integration framework (CIF). O CIF permite que o AEM acesse uma instância do Adobe Commerce e se comunique com o Adobe Commerce por meio do GraphQL. Ela também permite que os autores do AEM usem seletores de produtos e categorias e o console de produtos para navegar pelos dados de produtos e categorias obtidos da Adobe Commerce sob demanda. Além disso, a CIF fornece uma loja pronta para uso que agiliza projetos de comércio.
thumbnail: aem-magento-architecture.jpg
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 23%

---

# Integração do AEM e do Adobe Commerce (Magento) usando o Commerce integration framework {#aem-commerce-framework}

O Experience Manager e o Adobe Commerce são perfeitamente integrados usando o Commerce integration framework (CIF). O CIF permite que o AEM acesse diretamente e se comunique com a instância de comércio usando as [APIs do GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/) da Adobe Commerce.

>[!NOTE]
>
>A versão mínima da API do GraphQL com suporte é 2.3.5. Alguns recursos são compatíveis somente com versões mais recentes ou apenas com a edição do Adobe Commerce.

## Visão geral da arquitetura {#overview}

Esta é a arquitetura geral:

![Visão geral da arquitetura da CIF](../assets/AEM_Magento_Architecture.png)

No CIF, há suporte para padrões de comunicação do lado do servidor e do lado do cliente.
As chamadas de APIs do lado do servidor são implementadas usando o [cliente GraphQL](https://github.com/adobe/commerce-cif-graphql-client) integrado e genérico junto com um [conjunto de modelos de dados gerados](https://github.com/adobe/commerce-cif-magento-graphql) para o esquema GraphQL de comércio. Além disso, podem ser usados qualquer consulta ou mutação GraphQL no formato GQL.

Para os componentes do lado do cliente, que são criados usando o [React](https://reactjs.org/), o [cliente Apollo](https://www.apollographql.com/docs/react/) é usado.

## Arquitetura dos Componentes principais do AEM CIF {#cif-core-components}

![Arquitetura dos Componentes principais da CIF do AEM](../assets/cif-component-architecture.jpg)

Os [Componentes principais do AEM CIF](https://github.com/adobe/aem-core-cif-components) seguem padrões de design e práticas recomendadas muito semelhantes aos dos [Componentes principais do AEM WCM](https://github.com/adobe/aem-core-wcm-components).

A lógica de negócios e a comunicação de back-end com o Adobe Commerce para os Componentes principais do AEM CIF são implementadas nos Modelos do Sling. Caso seja necessário personalizar essa lógica para atender aos requisitos específicos do projeto, o padrão de delegação para Modelos do Sling pode ser usado.

>[!TIP]
>
>A página [Personalizar os Componentes principais da CIF do AEM](../customizing/customize-cif-components.md) tem um exemplo detalhado e oferece as práticas recomendadas para personalizar os componentes principais da CIF.

Nos projetos, os Componentes principais do AEM CIF e os componentes do projeto personalizado podem recuperar facilmente o cliente configurado para uma loja da Adobe Commerce associada a uma página do AEM por meio da configuração com reconhecimento de contexto do Sling.
