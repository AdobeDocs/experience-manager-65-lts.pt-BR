---
title: Especificação de configurações de segurança
description: Saiba como especificar configurações de segurança para proteger arquivos de dados XML. O recurso de configuração de segurança controla as entidades externas nas entradas XML.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
source-git-commit: eded255b54ff83f60f73cece8824c778d3a87680
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 1%

---

# Especificação de configurações de segurança {#specifying-security-settings}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

O Forms permite controlar se as entidades externas nas entradas XML são resolvidas. Por padrão, elas são resolvidas, mas você pode alterar esse comportamento para aumentar a segurança do sistema de formulários do AEM.

**Impedir o processamento de arquivos de dados XML que contêm referências a entidades externas**

1. No console de administração, clique em **[!UICONTROL Serviços > Forms]**.
1. Desmarque a caixa de seleção Resolver entidades externas.
1. Clique em **[!UICONTROL Salvar]**.
