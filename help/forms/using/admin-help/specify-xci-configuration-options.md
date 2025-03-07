---
title: Especificar opções de configuração XCI
description: Saiba como especificar as opções de configuração de XCI. Você pode especificar valores personalizados de arquivos XCI para o Formulário adaptável, de modo que ele possa ser usado durante a renderização do formulário.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 5fb6e6cc-6af7-4cf5-804b-bb3030079383
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%

---

# Especificar opções de configuração XCI {#specify-xci-configuration-options}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Output permite especificar um arquivo XCI personalizado que ele usa para renderização. Consulte [Especificar locais de arquivo para Saída](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

Por padrão, o Resultado substitui algumas das opções especificadas no arquivo XCI, incluindo o seguinte:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Você pode selecionar opções que cancelam a substituição das opções listadas acima, nesse caso, a Saída usa os valores especificados no arquivo XCI personalizado.

1. No console de administração, clique em **Serviços** > saída.
1. Marque ou desmarque a caixa de seleção Usar opções XCI padrão do sistema. Quando essa opção é selecionada, o Output usa seus valores padrão para as configurações packets, creator, producer e compressObjectStream. Quando essa opção é desmarcada, o Output usa os valores especificados no arquivo XCI personalizado.
1. Clique em **Salvar**.
