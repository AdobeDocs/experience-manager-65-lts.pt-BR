---
title: Hospedagem de duas instâncias do espaço de trabalho do AEM Forms em um servidor
description: Como os administradores de LC podem personalizar o HTML WS para hospedar duas instâncias em um único servidor acessível por URLs diferentes.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Hospedagem de duas instâncias do espaço de trabalho do AEM Forms em um servidor {#hosting-two-aem-forms-workspace-instances-on-one-server}

A instalação e as configurações padrão do AEM Forms permitem que apenas um espaço de trabalho do AEM Forms esteja disponível no servidor. No entanto, talvez seja necessário hospedar duas instâncias diferentes do espaço de trabalho do AEM Forms em um único AEM Forms Server. As duas instâncias podem ser acessadas por URLs diferentes.

Os administradores do AEM Forms personalizam o espaço de trabalho para criar dois URLs diferentes e disponibilizar dois espaços de trabalho no mesmo servidor. Neste artigo de personalização, você pode presumir que os dois espaços de trabalho estão acessíveis em `https://'[server]:[port]'/lc/ws` e `https://'[server]:[port]':/lc/ws2`.

Siga estas etapas para configurar o espaço de trabalho do AEM Forms.

1. Instale o pacote dev do espaço de trabalho do AEM Forms em seu servidor. Consulte [pacote dev](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p), para obter instruções sobre como criá-lo.
1. Faça logon no CRXDE Lite como administrador acessando `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. Copie o nó ws em /content e cole em /content. Renomeie o nó para ws2. Clique em **[!UICONTROL Salvar tudo]**. Nas propriedades deste nó, altere o valor de `sling:resourceType` para ws2. Clique em **[!UICONTROL Salvar tudo]**.

1. Copie a pasta ws de /libs e cole em /apps. Renomeie a pasta para ws2. Clique em **[!UICONTROL Salvar tudo]**.
1. Em `GET.jsp` às `/apps/ws2`, faça as seguintes alterações de código. Substitua o seguinte

   ```html
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" /><html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" />
   ```

   com o seguinte código

   ```html
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/apps/ws2/index.html'" />
   ```

1. Em `registry.js` às `/apps/ws2/js`, altere o caminho dos modelos para fazer referência aos modelos em `/apps/ws2/js/runtime/templates`. Substitua o código a seguir

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/libs/ws/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

   com o seguinte código

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/apps/ws2/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

1. Em `userinfo.js` às `/apps/ws2/js/runtime/models` e `/apps/ws2/js/runtime/views`, altere a cadeia de caracteres `/lc/content/ws` para `lc/content/ws2`.

1. Em `/apps/ws2/js/runtime/services/service.js`, altere o caminho na função `getLocalizationData` para apontar para `/lc/apps/ws2/Locale.html`.

1. Para consultar `pdf.html` do novo Workspace, altere o caminho de `pdf.html` em `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. Para consultar `pdf.html` da nova Workspace, altere os caminhos de `pdf.html` e `WsNextAdapter.swf` em `startprocess.html`, `taskdetails.html` e `processinstancehistory.html` em `/apps/ws2/js/runtime/templates`.

1. Copiar pasta `/etc/map/ws` e colar em `/etc/map`. Renomeie a nova pasta para ws2. Clique em Salvar tudo.

1. Nas propriedades de `ws2`, altere o valor de `sling:redirect` para `content/ws2`.

1. Altere o valor de `sling:match` para `^[^/\||]/[^/\||]/ws2$`.
