---
title: Ativando e desativando o modo de backup seguro
description: Na página Configurações de backup, você pode operar formulários AEM no modo de backup seguro para poder fazer backup de seu banco de dados e do diretório GDS (Armazenamento global de documentos) de maneira confiável. Saiba como ativar e desativar o modo de backup seguro.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: eded255b54ff83f60f73cece8824c778d3a87680
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Ativando e desativando o modo de backup seguro {#enabling-and-disabling-safe-backup-mode}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Na página Configurações de backup, você pode operar formulários AEM no modo de backup seguro para poder fazer backup de seu banco de dados e do diretório GDS (Armazenamento global de documentos) de maneira confiável.

Embora o AEM Forms esteja no modo de backup seguro, ele funciona normalmente, exceto por não remover ativamente os arquivos do diretório GDS.

>[!NOTE]
>
>A configuração dessa opção não faz backup do sistema; ela prepara o sistema para backup.

## Ativar modo de backup seguro {#enable-safe-backup-mode}

1. No console de administração, clique em Configurações > Configurações dos sistemas principais > Configurações de backup.
1. Na página Configurações de backup, selecione Operar no modo de backup seguro e clique em OK.

>[!NOTE]
>
>Se o sistema já estiver sendo executado no modo de backup seguro, uma nova reserva não será criada quando você clicar em OK.

## Desabilitar modo de backup seguro {#disable-safe-backup-mode}

1. No console de administração, clique em Configurações > Configurações dos sistemas principais > Configurações de backup.
1. Na página Configurações de backup, desmarque a opção Operar no modo de backup seguro e clique em OK.
