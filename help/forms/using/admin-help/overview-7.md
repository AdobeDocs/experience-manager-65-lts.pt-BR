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
hidefromtoc: true
exl-id: 68e43842-cba9-47b8-b7a3-6f625dbfca08
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '197'
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
