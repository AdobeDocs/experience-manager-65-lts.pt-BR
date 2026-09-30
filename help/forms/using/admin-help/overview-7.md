---
title: Noções básicas para configuração de formulários
description: Saiba mais sobre os vários serviços de formulários que ajudam você a criar aplicativos interativos de captura de dados.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 68e43842-cba9-47b8-b7a3-6f625dbfca08
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
source-wordcount: '200'
ht-degree: 0%
---
# Noções básicas para configuração de formulários {#basics-of-configuring-forms}

O serviço Forms permite criar aplicativos cliente de captura de dados interativos que validam, processam, transformam e fornecem formulários normalmente criados no Designer. Os autores de formulários desenvolvem um único design de formulário que o serviço Forms renderiza em vários formatos:

* como PDF no Adobe Reader ou em um navegador
* como HTML em vários ambientes do navegador, incluindo uma renderização XHTML 1.0 compatível
* como Guias de formulário em vários ambientes de navegador compatíveis com o Adobe Flash Player.

Para obter informações adicionais sobre o serviço Forms, consulte [Referência de serviços](https://www.adobe.com/go/learn_aemforms_services_63).

Usando a página Forms no console de administração, você pode configurar o comportamento do serviço Forms. Essas configurações se aplicam a todas as invocações do serviço. Quaisquer parâmetros enviados pelo AEM Forms SDK substituem as configurações definidas no console de administração; no entanto, eles afetam apenas essa invocação específica.

Depois de alterar as configurações do Forms no console de administração, clique em Salvar. Não é necessário reiniciar o servidor para que as alterações entrem em vigor. No entanto, talvez seja necessário interromper e reiniciar o serviço do Forms ao definir as configurações do modo de cache. (Consulte [Iniciando e interrompendo serviços](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
