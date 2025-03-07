---
title: Limitações de backup do PDF Generator
description: Saiba mais sobre as limitações de backup do PDF Generator. Não é possível fazer backup do diretório temporário que o PDF Generator usa, pois ele limpa o conteúdo em intervalos definidos.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
noindex: true
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: f76ce3be-6d50-4531-a982-2e902f866208
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '73'
ht-degree: 0%

---

# Limitações de backup do PDF Generator {#pdf-generator-backup-limitations}

Não é possível fazer backup do diretório temporário que o PDF Generator usa para converter arquivos. Mesmo que o serviço seja restaurado corretamente, os dados podem ser perdidos porque o PDF Generator revisa e limpa o conteúdo do diretório temporário em intervalos definidos.
