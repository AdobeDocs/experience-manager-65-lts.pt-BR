---
title: Desenvolvimento headless para sites do AEM 6.5
description: Saiba como os recursos headless avançados do AEM 6.5, como Modelos de conteúdo, Fragmentos de conteúdo e a API do GraphQL, funcionam juntos para permitir gerenciar suas experiências centralmente e distribuí-las entre canais.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 32%

---

# Desenvolvimento headless para sites do AEM 6.5 {#headless-development}

Saiba como os recursos headless avançados do AEM 6.5, como Modelos de conteúdo, Fragmentos de conteúdo e a API do GraphQL, funcionam juntos para permitir gerenciar suas experiências centralmente e distribuí-las entre canais.

## Visão geral {#overview}

A implementação headless está se tornando cada vez mais importante para fornecer experiências para o seu público-alvo, onde quer que esteja e independentemente do canal.

A implementação headless deixa de lado o gerenciamento de páginas e componentes, como é tradicional em soluções de pilha completa e híbridas, e se concentra na criação de fragmentos de conteúdo reutilizáveis e neutros em relação à canais, assim como na entrega desses fragmentos entre canais. É um padrão de desenvolvimento moderno e dinâmico para implementar experiências na web.

![Modelos de implementação do AEM](/help/sites-developing/headless/getting-started/assets/aem-implementation-models.png)

## Comparação entre headful e headless {#headful-headless}

Este documento se concentra no modelo completo de implementação headless do AEM. No entanto, &quot;headful ou headless&quot; não precisa ser uma escolha binária no AEM. Os recursos headless podem ser usados para gerenciar e entregar seu conteúdo a uma variedade de endpoints, além de permitir que os autores de conteúdo editem aplicativos de página única. Tudo no AEM.

>[!TIP]
>
>Consulte o documento [Headful e Headless no AEM](/help/sites-developing/headful-headless.md) para obter mais informações.

## AEM 6.5 e Headless {#aem-headless}

O AEM 6.5 é uma ferramenta flexível para o modelo de implementação headless, oferecendo três serviços avançados:

1. Modelos de conteúdo
   * Os modelos de conteúdo são uma representação estruturada do conteúdo.
   * Eles são definidos pelos arquitetos de informações no editor de modelos de fragmento de conteúdo do AEM.
   * Os modelos de conteúdo são a base para os fragmentos de conteúdo.
1. Fragmentos de conteúdo
   * Fragmentos de conteúdo são instanciações de modelos de conteúdo.
   * Eles são criados por autores de conteúdo por meio do editor de fragmentos de conteúdo do AEM.
   * Eles são armazenados no AEM Assets e gerenciados na interface do administrador do Assets.
1. API de conteúdo para entrega
   * A API GraphQL do AEM é compatível com a entrega de fragmentos de conteúdo.
   * A API REST do AEM Assets é compatível com operações CRUD de fragmentos de conteúdo.
   * A entrega direta de conteúdo também é possível com a exportação JSON do [Componente principal do fragmento de conteúdo.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=pt-BR)

## Primeiros passos no AEM Headless {#first-steps}

Há vários recursos disponíveis para o seu para começar a usar os recursos headless do AEM. Eles são destinados a casos de uso diferentes, mas fornecem uma visão geral sólida dos recursos headless do AEM.

| Recurso | Descrição | Tipo | Público | Est. Hora |
|---|---|---|---|---|
| [Jornada de desenvolvedores headless](/help/journey-headless/developer/overview.md) | **Para usuários novatos no AEM e em tecnologias headless**: comecem aqui para obter uma introdução abrangente ao AEM e seus recursos headless, desde a teoria do headless até a inauguração do seu primeiro projeto headless. | Guia | Desenvolvedores **novatos no AEM e no headless** | 1 hora |
| [Guia de Introdução Headless](/help/sites-developing/headless/getting-started/introduction.md) | **Para usuários experientes do AEM** que precisam de um breve resumo dos principais recursos headless do AEM, confira esta visão geral de início rápido. | Início rápido | Desenvolvedores e administradores **com experiência no AEM** | 20 minutos |
| [Tutorial prático do AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=pt-BR) | **Se preferir uma abordagem prática e estiver familiarizado com o AEM**, este tutorial aborda diretamente a criação de um projeto headless simples. | Tutorial | Desenvolvedores | 2 horas |
| [Portal do Desenvolvedor do AEM](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=pt-BR) | Esta coleção de recursos é fornecida para desenvolvedores **novos** e **experientes**. | Coleta de recursos | Desenvolvedores | |
