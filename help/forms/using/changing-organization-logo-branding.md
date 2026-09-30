---
title: Alteração do logotipo da organização para identidade visual
description: Para marcar a AEM Forms, forneça o logotipo da sua organização personalizando o logotipo padrão.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 3aa4aca3-3c94-4936-ba9c-484bbb196256
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
source-wordcount: '116'
ht-degree: 0%
---
# Alteração do logotipo da organização para identidade visual {#changing-the-organization-logo-for-branding}

O logotipo da organização é exibido no canto superior esquerdo do espaço de trabalho do AEM Forms. Para atualizar o logotipo, siga as [etapas genéricas de personalização do espaço de trabalho do AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) e as etapas a seguir.

1. Criar um logotipo e nomear o arquivo como `NewWorkspace.png`. Coloque o arquivo de imagem na pasta /apps/ws/images usando um cliente WebDAV.

   >[!NOTE]
   >
   >O tamanho recomendado da imagem do logotipo é 218 px × 20 px.

   >[!NOTE]
   >
   >Para obter mais informações, consulte [Acesso ao WebDAV](/help/sites-administering/webdav-access.md).

1. Referencie a nova imagem de logotipo na folha de estilos em /apps/ws/css/newStyle.css, adicionando o estilo a seguir.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
