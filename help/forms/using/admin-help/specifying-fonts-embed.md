---
title: Especificação de fontes a serem incorporadas
description: Saiba como especificar fontes a serem incorporadas em um Formulário adaptável. Você pode especificar quais fontes são incorporadas ou nunca incorporadas aos formulários gerados pelo serviço Forms.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: c73dced8-7242-465c-85bc-9315a9a08605
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Especificação de fontes a serem incorporadas {#specifying-fonts-to-embed}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Você pode especificar quais fontes são sempre incorporadas ou nunca incorporadas aos formulários gerados pelo serviço Forms. A incorporação de fontes aumenta o tamanho do arquivo dos formulários. Incorpore fontes incomuns que os usuários raramente têm em seus sistemas. Não incorpore fontes comuns normalmente instaladas.

>[!NOTE]
>
>Se você tiver especificado um arquivo XCI personalizado para o Forms, a opção de fonte incorporada no arquivo XCI substituirá essas configurações. (Consulte [Configuração de locais para o Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. No console de administração, clique em **[!UICONTROL Serviços > Forms]**.
1. Em **[!UICONTROL Configurações de Incorporação de Fontes]**, na caixa **[!UICONTROL Sempre Incorporar Fontes]**, digite os nomes das fontes a serem incorporadas aos formulários, separadas por vírgulas. As fontes especificadas são incorporadas somente no formulário gerado se forem usadas no formulário. Essa configuração será ignorada se a opção de fonte incorporada tiver sido ativada no arquivo XCI passado para o serviço, pois nesse caso, todas as fontes usadas no PDF são sempre incorporadas.
1. Na caixa **[!UICONTROL Nunca Incorporar Fontes]**, digite os nomes das fontes que não devem ser incorporadas aos formulários, separados por vírgulas. As fontes especificadas não são incorporadas na PDF, mesmo se forem usadas na PDF gerada. Essa configuração será ignorada se a opção de fonte incorporada tiver sido desativada no arquivo XCI passado para o serviço porque, nesse caso, nenhuma das fontes usadas no PDF é incorporada.
1. Clique em **[!UICONTROL Salvar]**.
