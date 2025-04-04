---
title: Jornada do arquiteto de conteúdo do Adobe Experience Manager Headless
description: Uma introdução aos recursos headless avançados e flexíveis do Adobe Experience Manager e como modelar conteúdo para seu projeto.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Architect,Data Architect
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 76%

---

# Modelagem de conteúdo para headless com o AEM - uma introdução {#architect-headless-introduction}

Nesta parte da [Jornada do arquiteto de conteúdo do AEM Headless](overview.md), você pode aprender os conceitos e a terminologia (básicos) necessários para entender a modelagem de conteúdo para a entrega de conteúdo headless com o Adobe Experience Manager (AEM).

Este documento ajuda você a entender a entrega de conteúdo headless, como o AEM é compatível com a tecnologia headless e como o conteúdo é modelado para a tecnologia headless. Depois de ler esse documento, você deverá:

* Entender os conceitos básicos de entrega de conteúdo headless.
* Familiarizar-se com o modo com que o AEM é compatível com a modelagem headless e de conteúdo.

## Objetivo {#objective}

* **Público**: iniciante
* **Objetivo**: apresentar os conceitos e a terminologia relevantes para a Modelagem de conteúdo headless.

## Entregar conteúdo em pilha completa {#full-stack}

Desde a ascensão dos sistemas de gerenciamento de conteúdo (CMS) de larga escala e fácil utilização, as organizações estão usando-os como um local central para gerenciar mensagens, comunicações e a identidade visual de sua marca. Usar o CMS como ponto central para administrar experiências melhorou a eficiência, eliminando a necessidade de duplicar tarefas em sistemas diferentes.

![O CMS clássico de pilha completa](/help/journey-headless/developer/assets/full-stack.png)

Em uma CMS de pilha completa, toda a funcionalidade para manipular conteúdo está no CMS. Os recursos do sistema constituem componentes diferentes da pilha do CMS. A solução de pilha completa tem muitas vantagens.

* Há um sistema para manter.
* O conteúdo é gerenciado centralmente.
* Todos os serviços do sistema estão integrados.
* A criação de conteúdo é contínua.

Portanto, se um novo canal precisar ser adicionado ou se o suporte para novos tipos de experiências for necessário, um novo componente (ou mais) poderá ser inserido na pilha e as alterações são feitas em um único lugar.

![Adicionar um novo canal à pilha](/help/journey-headless/developer/assets/adding-channel.png)

No entanto, a complexidade das dependências na pilha rapidamente se torna aparente, pois outros itens na pilha precisam ser ajustados para acomodar as alterações.

## A interface no headless {#the-head}

A interface de qualquer sistema é geralmente o renderizador de saída, normalmente na forma de uma GUI ou outra saída gráfica.

Quando falamos de um CMS headless, o CMS gerencia o conteúdo e continua a entregá-lo aos consumidores. No entanto, apenas entregando o **conteúdo** de forma padronizada, um CMS headless omite a renderização final de saída, deixando a **apresentação** do conteúdo para o serviço de consumo.

![CMS headless](/help/journey-headless/developer/assets/headless-cms.png)

Os serviços de consumo, sejam experiências de RA, um webshop, experiências móveis, aplicativos web progressivos (PWAs) e assim por diante, recebem conteúdo do CMS headless e fornecem sua própria renderização. Eles fornecem suas próprias interfaces para o conteúdo.

Omitir a interface simplifica o CMS ao remover a complexidade. Isso também altera a responsabilidade de renderizar o conteúdo para os serviços que realmente precisam do conteúdo e que geralmente são mais adequados para essa renderização.

## Modelagem de conteúdo {#content-modeling}

A modelagem de conteúdo (também conhecida como modelagem de dados) é sua especialidade. Portanto, o que precisa ser considerado ao modelar para headless?

Para que os aplicativos headless possam acessar seu conteúdo e fazer algo com ele, o conteúdo precisa realmente ter uma estrutura predefinida. Seria possível ter seu conteúdo de forma livre, mas isso complicaria *muito* a vida dos aplicativos.

Para o AEM, você, como Arquiteto de conteúdo, executará a modelagem de conteúdo para projetar uma variedade de **Modelos de fragmentos de conteúdo**. Eles definem a estrutura usada quando os autores de conteúdo criam os **Fragmentos de conteúdo** que contêm o conteúdo.

### Acesso ao conteúdo {#access-content}

Isso é mais um detalhe de desenvolvimento, mas pode interessar a você, apenas para completar a história.

Depois de criar os modelos de fragmento de conteúdo e de os autores os usarem para gerar o conteúdo, os aplicativos headless devem acessar esse conteúdo.

O Adobe Experience Manager (AEM) pode acessar seletivamente os fragmentos de conteúdo usando a API GraphQL do AEM para retornar somente o conteúdo necessário. Usando a API, um desenvolvedor pode formular consultas que selecionam conteúdo específico. Esse processo de seleção se baseia em *seus* Modelos de fragmentos de conteúdo.

Isso significa que seu projeto pode realizar a entrega headless de conteúdo estruturado para uso em seus aplicativos.

## O que vem a seguir {#whats-next}

Agora que você aprendeu os conceitos e a terminologia, o próximo passo é [Saber mais sobre as noções básicas de modelagem com Modelos de fragmentos de conteúdo](basics.md).

## Recursos adicionais {#additional-resources}

* Jornada do desenvolvedor AEM headless
   * [Saiba mais sobre o desenvolvimento headless do CMS](/help/journey-headless/developer/learn-about.md)
   * [Saiba como modelar seu conteúdo](/help/journey-headless/developer/model-your-content.md)
* [Introdução ao AEM as a Headless CMS](/help/sites-developing/headless/introduction.md)
* [Portal do Desenvolvedor do AEM](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=pt-BR)
* [Tutoriais do Headless no AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=pt-BR)
