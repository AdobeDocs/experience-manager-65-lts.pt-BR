---
title: Alterar o conjunto de caracteres
description: Você pode especificar o conjunto de caracteres usado para codificar o fluxo de saída. Saiba como alterar o conjunto de caracteres.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 1d614736-5897-4fd3-9ca4-94b115139ba3
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 1%

---

# Alterar o conjunto de caracteres {#change-the-character-set}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Você pode especificar o conjunto de caracteres usado para codificar o fluxo de saída.

1. No console de administração, clique em **[!UICONTROL Serviços > saída]**.
1. Em Internacionalização, na lista Conjunto de caracteres, selecione um conjunto de caracteres. Esta configuração depende do `TransformationFormat` e do `PrintFormat` especificados por meio da API. Para especificar um conjunto de caracteres diferente dos listados, selecione Personalizado e especifique um valor de codificação na caixa exibida.

   Se `TransformationFormat` for PDF e PDF/A ou `PrintFormat` for PCL, PostScript, Rótulo Zebra, IPL, DPL, TPCL, GenericColorPCL ou GenericPSLevel3, somente conjuntos de caracteres específicos serão suportados.

   O conjunto de caracteres deve ser um nome canônico válido. O valor padrão é ISO-8859-1.

1. Clique em **[!UICONTROL Salvar]**.
