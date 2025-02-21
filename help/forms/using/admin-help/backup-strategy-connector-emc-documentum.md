---
title: Estratégia de backup do Connector para usuários do EMC Documentum&reg;
description: Verifique como criar uma estratégia de backup para o Connector para usuários do EMC Documentum&reg;.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Estratégia de backup para o Connector para usuários do EMC Documentum® {#backup-strategy-for-connector-for-emc-documentum-users}

Se você tiver o Connector for EMC Documentum® instalado, além das instruções neste capítulo, sua estratégia de backup e recuperação deve incluir backup (ou recuperação) do computador em que o sistema ECM está instalado. (Consulte a documentação do ECM Documentum®).

Faça backup do ambiente AEM Forms usando o repositório ECM e executando as seguintes tarefas:

* Faça backup dos formulários do AEM seguindo as instruções descritas neste documento.
* Faça backup do sistema ECM Documentum® seguindo as instruções em [Fazer backup do EMC Documentum® Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#back-up-the-emc-documentum-content-server).

Restaurar o ambiente do AEM Forms usando o repositório ECM e executando as seguintes tarefas:

* Restaure o respectivo sistema de ECM seguindo as instruções em [Restaurar o EMC Documentum® Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#restore-the-emc-documentum-content-server).
* Restaure os formulários do AEM seguindo as instruções descritas neste documento.
