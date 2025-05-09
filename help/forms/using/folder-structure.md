---
title: Como entender a estrutura de pastas
description: Como entender a estrutura de pastas do código-fonte do espaço de trabalho do AEM Forms para personalizar.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Como entender a estrutura de pastas {#understanding-the-folder-structure}

Os componentes do espaço de trabalho do AEM Forms foram projetados na arquitetura MVC usando o Backbone (rede de transmissão). Cada componente tem um arquivo para:

* Modelo, que contém lógica de negócios.
* Modelo, que é um arquivo HTML contendo controles de interface.
* Exibição, que atua como uma classe Controlador para Modelo.

Os ativos de todos os componentes são colocados na estrutura de pastas descrita abaixo. Para acessar os ativos, faça logon no CRXDE Lite e navegue até `/libs/ws/js/runtime/`.

**templates** Contém modelos de backbone.

**exibições** contém exibições de backbone.

**modelos** Contém apenas os modelos HTML para os componentes.

**rotas** contém rotas universais. A pasta Templates dentro de rotas contém o código HTML e as referências aos componentes.

**services** Contém interface de serviço para chamar APIs de servidor do Adobe Experience Manager no ponto de extremidade REST.

**util** Contém utilitários genéricos utilizáveis por vários componentes.
