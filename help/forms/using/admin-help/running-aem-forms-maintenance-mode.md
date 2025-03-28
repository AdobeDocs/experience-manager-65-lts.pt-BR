---
title: Execução de formulários do AEM no modo de manutenção
description: O modo de manutenção é útil ao executar tarefas como corrigir um DSC, atualizar formulários do AEM ou aplicar um service pack. Saiba mais sobre como executar formulários do AEM no modo de manutenção.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: d4cfe1c1-8b44-4bd5-b6ec-29e5f70f0674
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Execução de formulários do AEM no modo de manutenção {#running-aem-forms-in-maintenance-mode}

O modo de manutenção é útil ao executar tarefas como corrigir um DSC, atualizar formulários do AEM ou aplicar um service pack.

Evite chamar processos enquanto o servidor estiver no modo de manutenção. Isso é o que acontece se um processo é chamado enquanto o servidor está no modo de manutenção:

* Se o processo for de longa duração, ele será adicionado ao banco de dados de jobs, mas não será iniciado. Ao sair do modo de manutenção, o AEM Forms processa as tarefas de longa duração em sua fila, mesmo que o servidor tenha sido reiniciado enquanto estava no modo de manutenção.
* Se o processo tiver vida curta, ele será processado imediatamente.

**Colocar formulários do AEM no modo de manutenção**

1. Em um navegador da Web, digite:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=[administrator username]&password=[password]`

   Uma mensagem &quot;now paused&quot; é exibida na janela do navegador.

   >[!NOTE]
   >
   >Se você desligar o servidor enquanto ele estiver no modo de manutenção, ele ainda estará no modo de manutenção quando for reiniciado. Desative o modo de manutenção quando terminar suas tarefas de manutenção.

**Verifique se o AEM Forms está em execução no modo de manutenção**

1. Em um navegador da Web, digite:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=[administrator username]&password=[password]`

   O status é exibido na janela do navegador. Um status &quot;true&quot; indica que o servidor está sendo executado no modo de manutenção e &quot;false&quot; indica que o servidor não está no modo de manutenção.

**Desativar modo de manutenção**

1. Em um navegador da Web, digite:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=[administrator username]&password=[password]`

   Uma mensagem &quot;now running&quot; é exibida na janela do navegador.
