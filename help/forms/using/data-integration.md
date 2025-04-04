---
title: Integração de dados do AEM Forms
description: A Integração de dados permite integrar o AEM Forms a fontes de dados diferentes e criar um modelo de dados de formulário para criar e trabalhar com formulários adaptáveis e comunicações interativas.
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
docset: aem65
feature: Form Data Model
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Integração de dados do [!DNL AEM Forms] {#aem-forms-data-integration}

![imagem-herói](do-not-localize/data-integration.png)

As infraestruturas corporativas incluem sistemas back-end distintos ou fontes de dados como bancos de dados, serviços da Web, serviços REST, serviços OData e soluções de CRM. Juntas, elas fazem um sistema de informações que serve dados para aplicativos corporativos para realizar negócios diários. Por outro lado, os aplicativos capturam os dados e os enviam de volta para atualizar as fontes de dados.

Aplicativos do [!DNL AEM Forms], como formulários adaptáveis e comunicações interativas, exigem integração com fontes de dados para buscar dados do cliente ao renderizar formulários e criar comunicações interativas. Há casos de uso em que os dados são obtidos de fontes de dados com base nas entradas do usuário em formulários adaptáveis. Além disso, os dados de formulário adaptável enviados podem ser gravados para atualizar as respectivas fontes de dados.

Embora um sistema modular e distribuído tenha seus próprios benefícios, o desafio está na integração e criação de associações de dados entre as fontes de dados. A integração de dados é a chave para uma infraestrutura empresarial funcional e eficiente, com diferentes fontes de dados conectadas a aplicativos para troca de dados de negócios.

## Visão geral da integração de dados {#data-integration-overview}

![aem-forms-data-integration](assets/aem-forms-data-integeration.png)

A Integração de Dados do [!DNL AEM Forms] permite configurar e conectar fontes de dados diferentes ao [!DNL AEM Forms]. Ele fornece uma interface de usuário intuitiva para criar um esquema de representação de dados unificada de entidades e serviços comerciais em fontes de dados conectadas. A representação unificada é conhecida como modelo de dados de formulário, uma extensão do esquema JSON. As entidades em um modelo de dados de formulário são chamadas de objetos do modelo de dados. Um modelo de dados de formulário permite:

* Acesse objetos de modelo de dados, propriedades e serviços a partir de fontes de dados conectadas.
* Criar objetos e propriedades de modelo de dados personalizados
* Crie associações entre objetos de modelo de dados em e entre fontes de dados.
* Invoque serviços de objeto de modelo de dados para consultar ou gravar dados de e para fontes de dados.

Depois de criar um modelo de dados de formulário, você pode usá-lo em vários formulários adaptáveis e workflows de comunicações interativas, como:

* Crie formulários adaptáveis e comunicações interativas com base no modelo de dados de formulário
* Preencher previamente os formulários adaptáveis e as comunicações interativas das fontes de dados configuradas
* Invocar serviços/operações de fonte de dados usando regras de formulário adaptáveis
* Gravar dados de formulário adaptável enviados nas fontes de dados

## Introdução à integração de dados {#get-started-with-data-integration}

A primeira etapa para implementar a integração de dados é identificar e configurar fontes de dados que armazenam informações que você deseja usar em formulários adaptáveis e casos de uso de comunicações interativas. Em seguida, crie um modelo de dados de formulário que use o objeto de modelo de dados, as propriedades e os serviços de uma ou mais fontes de dados. Você pode criar formulários adaptáveis e comunicações interativas com base em um modelo de dados de formulário em que os campos de formulário adaptáveis ou espaços reservados em comunicações interativas são vinculados às respectivas propriedades da fonte de dados.

O [!DNL AEM Forms] também permite criar um modelo de dados de formulário independente das fontes de dados e associar ou associar objetos e propriedades de modelo de dados no modelo de dados de formulário à fonte de dados posteriormente. Ele elimina qualquer dependência em fontes de dados enquanto você trabalha em um modelo de dados de formulário.

Analise o seguinte para começar, entender e implementar a integração de dados.

* [Configurar fontes de dados](../../forms/using/configure-data-sources.md)
* [Criar modelo de dados de formulário](../../forms/using/create-form-data-models.md)
* [Trabalhar com o modelo de dados de formulário](../../forms/using/work-with-form-data-model.md)
* [Usar modelo de dados de formulário](../../forms/using/using-form-data-model.md)
