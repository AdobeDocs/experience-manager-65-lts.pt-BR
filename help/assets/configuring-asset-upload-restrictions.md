---
title: Configurar restrições de upload de ativos
description: Restringir os tipos de ativos (arquivos) que os usuários podem fazer upload
contentOwner: AG
role: Developer, Admin, Architect
feature: Asset Management,Upload
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 18%

---

# Configurar restrições de upload de ativos {#configuring-asset-upload-restrictions}

Você pode configurar o [!DNL Adobe Experience Manager Assets] para restringir os tipos de ativos que os usuários podem carregar. Ele ajuda a impedir uploads acidentais de formato indesejado e arquivos mal-intencionados. O serviço `Day CQ DAM Asset Upload Restriction` permite que você controle o tipo de arquivo que os usuários podem carregar. Por padrão, o [!DNL Assets] permite que usuários carreguem ativos de todos os tipos MIME. No entanto, você pode configurar o serviço para impedir que os usuários façam upload de arquivos apenas de tipos MIME específicos.

1. Abra o console da Web do Configuration Manager. Acessar `https://[aem_server]:[port]/system/console/configMgr`.
1. Abra o serviço **[!UICONTROL Restrição de carregamento de ativos DAM CQ do]** no modo de Edição. Por padrão, a opção **Permitir todos os MIME** está selecionada, o que permite que os usuários carreguem arquivos de todos os tipos MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Para impedir que usuários façam upload de arquivos apenas de determinados tipos MIME, desmarque a opção **[!UICONTROL Permitir todos os tipos MIME]** e especifique os tipos MIME permitidos nos campos **[!UICONTROL MIMEs de ativos permitidos (regex)]** usando expressões regulares.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Clique em **[!UICONTROL Salvar]** para salvar as alterações. Se você especificar cadeias de caracteres MIME para os tipos MIME permitidos, a operação de upload falhará todos os ativos de tipo MIME que não correspondam às cadeias de caracteres MIME configuradas nesses campos.
