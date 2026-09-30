---
title: Configurar o serviço de informação do sistema
description: Saiba como configurar o serviço de informações do sistema.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/system_information_service
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: e31614a9-d670-4d22-88ba-8953797f6e14
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
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
source-wordcount: '114'
ht-degree: 0%
---
# Configurar o serviço de informação do sistema {#set-up-the-system-information-service}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

O serviço de informações do sistema fornece APIs REST para recuperar informações. Para usar o serviço de informações do sistema, habilite o endpoint REST no console de administração. Execute as seguintes etapas para habilitar o endpoint REST:

1. Faça logon no console de administração. A URL padrão do console de administração é `https://[hostname]:'port'/adminui.`
1. Navegue até Serviços > Aplicativos e serviços > Gerenciamento de serviços.
1. Na página Gerenciamento de Serviços, clique no serviço **SystemInfo**.
1. Na lista da guia Pontos de Extremidade, selecione REST e clique em **Adicionar**.
1. Na tela Adicionar Ponto de Extremidade REST, clique em **Adicionar**.
