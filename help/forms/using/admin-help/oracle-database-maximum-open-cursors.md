---
title: Limite máximo de cursores abertos do banco de dados do Oracle
description: Saiba como configurar um valor máximo para cursores abertos no Oracle.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 98663f16-6c05-4485-9bf2-a2de9d1975c8
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Limite máximo de cursores abertos do banco de dados do Oracle {#oracle-database-maximum-open-cursors-threshold}

Para configurar um valor máximo para cursores abertos no Oracle, talvez seja necessário ajustar esse valor para um número apropriado ao seu aplicativo. É evidente que, sob uma carga moderada, a média de cursores abertos era de 2700. Recomenda-se iniciar com um limite superior de 3000. Para obter mais informações, acesse [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
