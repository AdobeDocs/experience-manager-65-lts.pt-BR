---
title: Configuração de opções de internacionalização
description: Saiba como especificar a localidade usada para renderizar formulários e como especificar o conjunto de caracteres usado para codificar o fluxo de saída.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 47a49147-2921-4d28-8d04-2281c0b9a190
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Configuração de opções de internacionalização{#setting-internationalization-options}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

## Especificar a localidade usada para renderizar formulários {#specify-the-locale-used-to-render-forms}

Você pode especificar a localidade usada ao renderizar um formulário do PDF. Os campos em um formulário do PDF usam o local especificado para exibir dados. Por exemplo, se o local estiver definido como Alemão, o formulário usará separadores decimais alemães para valores numéricos. O local também é usado para enviar mensagens de validação para dispositivos clientes, como navegadores da Web, como parte das transformações do HTML.

1. No console de administração, clique em Serviços > Forms.
1. Em Internacionalização, na lista Idioma, selecione o local usado para renderizar um formulário. O valor padrão é inglês (Estados Unidos).
1. Clique em Salvar.

## Especifique o conjunto de caracteres usado para codificar o fluxo de saída {#specify-the-character-set-used-to-encode-the-output-stream}

1. Em Internacionalização, na lista Conjunto de caracteres, selecione um conjunto de caracteres. Essa configuração depende da API usada, renderHTMLForm ou renderPDFForm. Para especificar um conjunto de caracteres diferente dos listados, selecione Personalizado e especifique um valor de codificação na caixa exibida.

   Para transformações de HTML, os formulários AEM são compatíveis com valores de codificação de caracteres definidos pelo pacote `java.nio.charset`. Se sFormPreference for PDFForm, somente conjuntos de caracteres específicos serão suportados. O conjunto de caracteres deve ser um nome canônico válido. O valor padrão é ISO-8859-1.

1. Clique em Salvar.
