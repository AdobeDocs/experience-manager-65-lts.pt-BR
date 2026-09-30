---
title: Alteração do conteúdo da Página zero no Designer
description: Você sabe como alterar a mensagem exibida na Página Zero de uma PDF XFA ao visualizá-la em um visualizador que não seja da Adobe PDF?
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms,Forms Designer,Designer
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: f966f5fb-338a-4d8e-91c6-aa0eddd03420
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 1af3c3d4-88d7-5e0f-813c-eb70824bfcdd
    internal-label: Forms Designer
  - id: 794033c1-20ea-55a4-a8a6-b1107e12deb0
    internal-label: Designer
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%
---
# Alteração do conteúdo da Página zero no Designer {#changing-page-zero-content-in-designer}

O conteúdo da Página Zero é exibido por padrão quando um visualizador que não seja da Adobe PDF, como o visualizador padrão do PDF em [!DNL Chrome] ou [!DNL Firefox], não consegue ler o conteúdo do formulário PDF/XFA. A mensagem padrão de Página zero é mostrada abaixo.

![defaultpage0message](assets/defaultpage0message.png)

A versão [!DNL AEM Forms] do Designer permite alterar a mensagem que é exibida na Página Zero. Para alterar a mensagem Página zero, execute as seguintes etapas:

1. Verifique se você tem a versão [!DNL AEM Forms] do Designer instalada. Você pode verificar a versão na tela Sobre do designer.

1. Abra o formulário para o qual deseja alterar o conteúdo da Página zero.

1. Clique em **[!UICONTROL Arquivo]** > **[!UICONTROL Propriedades do Formulário]**.

1. Na caixa de diálogo [!UICONTROL Propriedades do Formulário], clique em ![mais](assets/plus.png) (ícone de adição) para adicionar uma propriedade personalizada.

1. Especifique **_pagezerocontent** como o nome da propriedade.
1. Adicione a nova mensagem Página zero, em formato Rich Text, como valor. Por exemplo:


   `<body xmlns="http://www.w3.org/1999/xhtml" xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download_br.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader_br.</p></body>`

1. Salve o formulário como PDF.

1. Exiba o formulário do PDF no navegador para confirmar que a mensagem foi atualizada. O exemplo de valor acima aparece da seguinte maneira:

   ![mensagem alterada](assets/changedmessage.png)

>[!NOTE]
>
>A propriedade personalizada criada pode não aparecer corretamente na caixa de diálogo Propriedades do formulário quando você reabrir o formulário. No entanto, funciona bem e o formulário exibe a mensagem Página zero atualizada.
