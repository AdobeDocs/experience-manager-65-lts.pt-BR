---
title: Reconhecimento de certificados válidos e expirados em documentos do PDF
description: Saiba como reconhecer certificados válidos e expirados em documentos do PDF.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: f7402f0d-7c19-4a56-8630-208faa197f94
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Reconhecimento de certificados válidos e expirados em documentos do PDF {#recognizing-valid-and-expired-certificates-in-pdf-documents}

Quando um documento do PDF com direitos de uso aplicados pelas extensões do Reader é aberto no Adobe Reader, é exibida uma barra de status que descreve os direitos de uso específicos ativados no documento do PDF.

Quando o certificado digital que especifica os direitos de uso de um documento do PDF expira e o documento do PDF é aberto no Adobe Reader, uma caixa de diálogo informa ao usuário que o documento do PDF tem direitos de uso, mas esses direitos estão desativados. Embora a mensagem indique que o documento do PDF foi alterado ou adulterado, esse não é necessariamente o caso. O Adobe Reader exibe essa mensagem quando um certificado expira ou um documento é modificado. No Adobe Reader 7.0.x ou posterior, não é possível determinar em qual caso está o problema no momento.

Após fechar a caixa de diálogo, o Adobe Reader abre o documento do PDF. Os direitos de uso aplicados com o uso das extensões do Acrobat Reader DC não estão disponíveis, conforme esperado. Se o documento do PDF for um formulário interativo, os campos de formulário serão bloqueados e o usuário não poderá alterar os dados do formulário.
