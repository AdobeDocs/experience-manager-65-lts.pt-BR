---
title: Visão geral da configuração do SSL
description: Saiba como melhorar a segurança da comunicação configurando o SSL.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 2e81b9b9-321d-4423-9748-6385956b1d90
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Visão geral da configuração do SSL {#overview-of-configuring-ssl}

Você pode criar credenciais SSL (Secure Sockets Layer) e configurar o SSL no servidor de aplicativos para melhorar a segurança da comunicação com o servidor de aplicativos.

Como produto de segurança, o Rights Management exige a configuração do SSL. Ao configurar certificados SSL, certifique-se de usar somente chaves RSA. Certificados SSL com chaves DSA não são compatíveis.

As informações fornecidas se aplicam às instalações manuais, automáticas e turnkey. Ele oferece um exemplo de um método para configurar o SSL. Você também pode usar outros métodos mais apropriados para sua rede ou organização.

>[!NOTE]
>
>É recomendável concluir a instalação, a configuração e a implantação dos módulos de formulários do AEM e garantir que os produtos estejam sendo executados corretamente antes de configurar o SSL no servidor de aplicativos.

>[!NOTE]
>
>Ao criar certificados de segurança SSL e credenciais, use os mesmos privilégios de conta de usuário que você usou para executar o servidor de aplicativos. Se o servidor de aplicativos for executado usando outros privilégios de usuário, o formulário poderá não ser renderizado corretamente para representações PDFForm quando ContentRootURI apontar para https.

Se você tiver um servidor LDAP habilitado para SSL, configure o Gerenciamento de usuários para trabalhar com ele. (Consulte [Configurar o Gerenciamento de Usuários para um servidor LDAP habilitado para SSL](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)
