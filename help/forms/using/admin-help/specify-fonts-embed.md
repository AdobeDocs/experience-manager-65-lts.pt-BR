---
title: Especificar fontes a serem incorporadas
description: Saiba como especificar fontes a serem incorporadas em um Formulário adaptável. Você pode especificar quais fontes são incorporadas ou nunca incorporadas aos formulários gerados pelo serviço Forms.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 374f9425-b596-4481-8fd0-6df07c521a19
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Especificar fontes a serem incorporadas{#specify-fonts-to-embed}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Você pode especificar quais fontes são sempre incorporadas ou nunca incorporadas aos formulários usados pelo Output. A incorporação de fontes aumenta o tamanho do arquivo dos formulários. Incorpore fontes incomuns que os usuários provavelmente não terão em seus sistemas e não incorpore fontes comuns que terão instaladas.

>[!NOTE]
>
>Se você tiver especificado um arquivo XCI personalizado para Saída, a opção de fonte incorporada no arquivo XCI substituirá essas configurações. (Consulte [Especificar locais de arquivo para Saída](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. No console de administração, clique em Serviços > saída.
1. Em Configurações de Incorporação de Fonte, na caixa Incorporar Sempre Fontes, digite os nomes das fontes a serem incorporadas aos formulários, separadas por vírgulas. As fontes especificadas são incorporadas somente no formulário gerado se forem usadas no formulário. Essa configuração será ignorada se a opção de fonte incorporada tiver sido ativada no arquivo XCI passado para o serviço. Nesse caso, todas as fontes usadas no PDF são sempre incorporadas.
1. Na caixa Nunca incorporar fontes, digite os nomes das fontes que não serão incorporadas aos formulários, separados por vírgulas. As fontes especificadas não são incorporadas na PDF, mesmo se forem usadas na PDF gerada. Essa configuração será ignorada se a opção de fonte incorporada tiver sido desativada no arquivo XCI passado para o serviço. Nesse caso, nenhuma das fontes usadas no PDF é incorporada.
1. Clique em Salvar.
