---
title: Configurar uma solução de gerenciamento de correspondência
description: Saiba como configurar uma solução de Gerenciamento de correspondência em um ambiente do AEM Forms.
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 1%

---

# Configurar uma solução de gerenciamento de correspondência {#configuring-a-correspondence-management-solution}

## Definindo o URL da instância do autor para VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Use as etapas a seguir para definir um URL da instância do autor para a restauração da versão da instância do autor:

1. Acesse *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Faça logon com as credenciais de usuário do Console de gerenciamento OSGi. As credenciais padrão são admin/admin.
1. Localize e clique no ícone **[!UICONTROL Editar]** ao lado da configuração **[!UICONTROL com.adobe.livecycle.content.ativate.impl.VersionRestoreManagerImpl.name]**.
1. No campo **[!UICONTROL URL do Autor de VersionRestoreManager]**, especifique a URL da instância do Autor de VersionRestoreManager.

   **cadeia de caracteres de URL**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Se houver várias instâncias de autor (Clusterizadas) com base em um Balanceador de Carga, especifique a URL para o balanceador de carga no campo **[!UICONTROL URL do Autor de VersionRestoreManager]**.

1. Clique em **[!UICONTROL Salvar]**.

## Definição do URL da instância de publicação para AtivationManagerImpl (gerenciador de ativação da instância pública) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Siga estas etapas para poder definir o URL da instância de publicação para o gerenciador de ativação da instância pública:

1. Vá para *https://:&lt;authorHost>:&lt;authorPort>/lc/system/console/configMgr*. Faça logon com as credenciais de usuário do Console de gerenciamento OSGi. As credenciais padrão são admin/admin.
1. Localize e clique no ícone **[!UICONTROL Editar]** ao lado da configuração **[!UICONTROL com.adobe.livecycle.content.ativate.impl.AtivationManagerImpl.name]**.
1. No campo **[!UICONTROL Publicar URL]** do AtivationManager, especifique a URL para acessar o AtivationManager da instância de publicação. Você pode fornecer os seguintes URLs.

   * **URL do Balanceador de Carga (Recomendado)**: Forneça a URL do balanceador de carga, caso você tenha um servidor Web que atue como balanceador de carga na frente do farm de publicação (várias instâncias de publicação não clusterizadas).
   * **URL da instância de publicação**: forneça qualquer URL da instância de publicação, se você tiver uma única instância de publicação ou se o servidor Web que está à frente do farm de publicação não estiver acessível do ambiente de criação devido a restrições. Caso a instância de publicação especificada esteja inativa, há um mecanismo de fallback que deve ser tratado no lado do autor.
   * **cadeia de caracteres de URL**:

     `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Clique em **[!UICONTROL Salvar]**.

Para obter mais informações sobre como configurar o Gerenciamento de Correspondências, consulte [Propriedades de Configuração do Gerenciamento de Correspondências](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html).
