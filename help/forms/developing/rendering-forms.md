---
title: Renderização do Forms
description: Use o serviço Forms para criar aplicativos cliente de captura de dados interativos que validam, processam, transformam e fornecem formulários normalmente criados no Designer. Os autores de formulários podem desenvolver um único design de formulário que o serviço do Forms renderiza no PDF, SWF ou HTML em vários ambientes do navegador.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/performing_service_operations_using_apis
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: 3f1f9ecb-be62-4428-8db8-23c57081b0f7
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Renderização do Forms {#rendering-forms}

**Exemplos e exemplos neste documento são somente para AEM Forms no ambiente JEE.**

**Sobre o serviço Forms**

O serviço Forms permite criar aplicativos cliente de captura de dados interativos que validam, processam, transformam e fornecem formulários normalmente criados no Designer. Os autores de formulários podem desenvolver um único design de formulário que o serviço do Forms renderiza no PDF, SWF ou HTML em vários ambientes do navegador.

Quando um usuário final solicita um formulário, um aplicativo cliente envia a solicitação ao serviço do Forms, que retorna o formulário em um formato apropriado. Assim que o serviço Forms recebe uma solicitação, ele mescla dados com um design de formulário e entrega o formulário no formato desejado. A saída do serviço de formulário é um formulário interativo, geralmente um documento do PDF. Um formulário interativo permite que os usuários preencham os campos localizados no formulário.

Dependendo do tipo de aplicativo cliente, você pode gravar o formulário em um navegador da Web cliente ou salvá-lo como um arquivo PDF. Um aplicativo baseado na Web pode gravar o formulário no navegador da Web. Um aplicativo de desktop pode salvar o formulário como um arquivo PDF. Para demonstrar como gravar em um navegador da Web e em um arquivo PDF, os inícios rápidos na seção *Renderização do Forms* são organizados da seguinte maneira:

* Os exemplos fortemente tipados da API Java (modo SOAP) são um servlet Java.
* Os exemplos de serviço Web (Java Base64) são um servlet Java.
* Os exemplos de serviço Web (MTOM) são um aplicativo de console (nem todos os inícios rápidos têm um exemplo de MTOM).

>[!NOTE]
>
>Para obter informações sobre como criar uma aplicação Web que use servlets java para chamar o serviço Forms, consulte [Criando Aplicações Web que Renderizam o Forms](/help/forms/developing/creating-web-applications-renders-forms.md).

Você pode passar um design de formulário (um arquivo XDP) ou um documento PDF para o serviço Forms usando uma das duas formas a seguir:

* Você pode fazer referência ao design do formulário usando um valor de URL. Esta abordagem envolve o uso de um objeto `URLSpec`. A raiz do conteúdo é passada para o serviço Forms usando o método `setContentRootURI` do objeto `URLSpec`. O nome de design do Formulário ( `formQuery`) é passado como um parâmetro separado. Os dois valores são concatenados para obter a referência absoluta para o design do formulário. (A maioria das inicializações rápidas na seção *Renderização do Forms* usa esta abordagem.)
* Você pode passar um `com.adobe.idp.Document` que contenha o design do formulário para o serviço Forms. Dois novos métodos chamados `renderPDFForm2` e `renderHTMLForm2` aceitam um objeto `com.adobe.idp.Document` que contém um design de formulário. (Consulte [Passando documentos para o serviço Forms](/help/forms/developing/passing-documents-forms-service.md)

É possível realizar essas tarefas usando o serviço Forms:

* Renderizar o PDF forms interativo. (Consulte [Renderização do PDF forms Interativo](/help/forms/developing/rendering-interactive-pdf-forms.md).)
* Renderizar formulários no cliente. (Consulte [Renderização do Forms no cliente](/help/forms/developing/rendering-forms-client.md).)
* Renderizar formulários com base em fragmentos. (Consulte [Renderização de Forms com base em fragmentos](/help/forms/developing/rendering-forms-based-fragments.md).)
* Renderizar formulários habilitados por direitos. (Consulte [Renderização de Forms com Direitos Habilitados](/help/forms/developing/rendering-rights-enabled-forms.md).)
* Renderizar formulários como HTML. (Consulte [Renderização do Forms como HTML](/help/forms/developing/rendering-forms-html.md).)
* Renderização do HTML Forms Usando Arquivos CSS Personalizados ([Renderização do HTML Forms Usando Arquivos CSS Personalizados](/help/forms/developing/rendering-html-forms-using-custom.md).)
* Manipular formulários enviados. (Consulte [Manipulação de Forms Enviada](/help/forms/developing/handling-submitted-forms.md).)
* Criação de documentos do PDF com dados XML enviados. (Consulte [Criação de Documentos do PDF com Dados XML Enviados](/help/forms/developing/creating-pdf-documents-submitted-xml.md).)
* Preencher formulários previamente. (Consulte [Preenchimento prévio de Forms com Layouts Fluxáveis](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
* Envio de documentos. (Consulte [Passando documentos para o serviço Forms](/help/forms/developing/passing-documents-forms-service.md)
* Calcular dados do formulário. (Consulte [Calcular Dados De Formulário](/help/forms/developing/calculating-form-data.md).)
* Otimizar um aplicativo. (Consulte [Otimização do desempenho do serviço Forms](/help/forms/developing/optimizing-performance-forms-service.md).)
