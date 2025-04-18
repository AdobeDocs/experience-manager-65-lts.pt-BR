---
title: Baixar um XFA ou um modelo de formulário do PDF
description: É possível exportar formulários do repositório para o sistema local e migrar os formulários baixados para um novo repositório.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Baixar um XFA ou um modelo de formulário do PDF {#download-an-xfa-or-a-pdf-form-template}

A operação de download, como o nome indica, permite exportar formulários do repositório para o sistema local. Em combinação com a operação de upload, essa operação ajuda a migrar seus formulários de um repositório para outro.

No AEM Forms, a operação de download é compatível com os seguintes tipos de ativos:

* Modelos de formulário (XFA Forms)
* PDF forms
* Documentos (arquivos simples do PDF)

O AEM Forms permite o download desses tipos de formulário individualmente ou em uma pasta que contenha um ou mais formulários compatíveis.

Além desses ativos, você pode baixar o tipo de ativo `Resource` se ele estiver presente em uma pasta. Essa funcionalidade é fornecida para permitir que você baixe o recurso referido por um formulário XFA junto com o formulário.

## Baixar um ou mais formulários {#download-one-or-more-forms}

1. Faça logon na interface do usuário do AEM Forms em `https://<server>:<port>/aem/forms.html`.

1. Navegue até o local do ativo que deseja baixar.

1. Selecione o ativo. Clique no ícone **[!UICONTROL Download]** ![aem6forms_download](assets/aem6forms_download.png) na barra de ferramentas.

   >[!NOTE]
   >
   >Você pode selecionar apenas um formulário para download. Para baixar vários formulários, é necessário baixá-los como uma pasta.

1. Na caixa de diálogo exibida, clique em **[!UICONTROL Baixar]**.

   O AEM Forms gera um arquivo ZIP contendo o arquivo selecionado ou a pasta selecionada.

   Se você estiver baixando uma pasta, os ativos compatíveis dentro da pasta serão baixados em sua hierarquia existente.

   O arquivo ZIP foi salvo na pasta `Downloads` do sistema.

## Considerações relacionadas para a operação de upload {#related-considerations-for-the-upload-operation}

* Você pode fazer upload do arquivo ZIP para qualquer outro local no mesmo repositório ou em outro repositório
* A hierarquia dos ativos em uma pasta é retida durante a operação de upload
* Todas as alterações de metadados feitas nos ativos baixados antes do download são refletidas no upload
