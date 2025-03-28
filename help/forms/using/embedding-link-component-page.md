---
title: Incorporação do componente de link em uma página
description: Você pode usar o componente Link para vincular um documento adaptável ou um formulário adaptável de qualquer página.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Incorporação do componente de link em uma página{#embedding-link-component-in-a-page}

## Pré-requisitos {#prerequisites}

O componente de link é um membro da categoria Serviços de documento. Verifique se a categoria Serviços de documento está visível no navegador de componentes do AEM. Se a categoria não estiver listada, siga as etapas listadas em [Habilitando componentes do portal de formulários](/help/forms/using/enabling-forms-portal-components.md).

## Componente do link {#link-component}

O componente Link permite que os autores do portal de formulários criem um link para um formulário adaptável de qualquer lugar em uma página. O componente Link está disponível na seção Serviços de documento no navegador de componentes.

Execute as seguintes etapas para adicionar um componente Link à página:

1. Arraste o componente **Link** na página. Selecione o componente e selecione ![cmppr](assets/cmppr.png). A caixa de diálogo Editar componente de link se abre.

   ![edit-link-component](assets/edit-link-component.png)

1. Na guia **Exibir**, especifique o seguinte:

   * **Legenda do link**: texto ou legenda do link.
   * **Dica de Ferramenta do Link**: dica de ferramenta do link.
   * **Modelo de layout**: modelo para o layout do componente Link.

1. Abra a guia **Informações do ativo** e especifique o tipo do ativo. Um ativo pode ser um **formulário**. Dependendo do tipo de ativo selecionado, as opções listadas abaixo são exibidas:

   * **Caminho do ativo**: caminho do repositório onde o ativo está armazenado.

   * **Tipo de renderização**: o formato de renderização — PDF, HTML ou Auto. O tipo de renderização automática detecta o ambiente do usuário e renderiza o formulário de acordo com ele como HTML ou PDF. Por exemplo, se o formulário for acessado de um dispositivo móvel, o tipo de renderização Automática renderiza o formulário no HTML.
   * **Enviar URL:** URL para o servlet para o qual os dados de formulário são enviados.
   * **Perfil do HTML**: perfil para renderizar o formulário como HTML.
   * **Perfil do PDF**: perfil para renderizar o formulário como documento do PDF.

1. Abra a guia **Avançado**. Você pode especificar os parâmetros adicionais no formato de par de valor-chave. Quando o link for clicado, esses parâmetros adicionais serão transmitidos junto com o formulário.

   Selecione **Concluído** para salvar a configuração.

## Práticas recomendadas para usar o componente Link {#best-practices-for-using-link-component-br}

* Selecione PDF como o tipo de renderização se o caminho especificado no Caminho do formulário apontar para um documento que tenha PDF como formato de renderização permitido.
* A URL de envio de um formulário pode ser especificada em vários locais e sua ordem de precedência é a seguinte:

   1. O URL de envio incorporado ao formulário (no botão enviar) tem a prioridade mais alta.
   1. O URL de envio mencionado no Forms Manager tem a prioridade média.
   1. O URL de envio mencionado no portal de formulários tem a prioridade mais baixa.
