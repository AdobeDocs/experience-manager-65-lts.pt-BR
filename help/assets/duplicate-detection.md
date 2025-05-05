---
title: Habilitar detecção de ativos duplicados
description: Saiba como habilitar a detecção de ativos duplicados no Experience Manager.
contentOwner: AG
role: User, Admin
feature: Asset Management,Asset Reports
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Habilitar detecção de ativos duplicados {#enable-detection-of-duplicate-assets}

Se você tentar carregar um ativo que existe em [!DNL Adobe Experience Manager Assets], o recurso de detecção de duplicidades o identifica como duplicado. A detecção de duplicados está desativada por padrão. Para ativar o recurso, siga estas etapas:

1. Abra a página de configuração do Console da Web [!DNL Experience Manager] acessando `https://[aem_server]:[port]/system/console/configMgr`.
1. Edite a configuração do servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selecione a opção **[!UICONTROL detectar duplicata]** e clique em **[!UICONTROL Salvar]**.

   ![Selecione a opção de detecção de duplicidade no servlet](assets/chlimage_1-377.png)

   *Figura: selecione a opção de detecção de duplicidade no servlet.*

O recurso de detecção de duplicidade agora está habilitado em [!DNL Assets]. Quando um usuário tenta fazer upload de um ativo que existe em [!DNL Experience Manager], o sistema verifica se há conflito e o indica. Os ativos são identificados usando o hash SHA-1 armazenado em `jcr:content/metadata/dam:sha1`, o que significa que os ativos duplicados são detectados independentemente dos nomes de arquivo.

>[!MORELIKETHIS]
>
>* [Duplicar ativos no repositório existente (um tutorial de um membro da comunidade)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)
>* [Detectar ativos duplicados no AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/detect-duplicate-assets.html?lang=pt-BR)
