---
title: Importação e exportação do arquivo de configuração
description: Saiba como importar e exportar o arquivo de configuração para editar as preferências do servidor ou configurar outra instância do produto AEM Forms.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 92fdcee3-2007-4bbc-be4b-426d65b8dbc1
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Importação e exportação do arquivo de configuração {#importing-and-exporting-the-configuration-file}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Use a página Configuração Manual para baixar uma cópia das definições de configuração no formato XML. As configurações deste arquivo controlam todas as preferências do servidor. Em seguida, você pode editar o arquivo e carregá-lo de volta no servidor. Você também pode usar o arquivo para configurar outra instância do produto AEM Forms.

Para evitar riscos de segurança, o valor da senha de vinculação do servidor de diretório não é incluído em um arquivo de configuração exportado. Atualize a senha no arquivo XML antes de importar o arquivo para um novo sistema.

>[!NOTE]
>
>A importação do arquivo de configuração reconfigura os formulários do AEM com base nas informações do arquivo. Somente um administrador do sistema ou um consultor de serviços profissionais familiarizado com o produto AEM Forms e o XML deve considerar a modificação do arquivo de configuração. Talvez seja necessário editar o arquivo de configuração, por exemplo, para redefinir uma configuração corrompida.

**Exportar as informações de configuração**

1. No Console De Administração, clique Em Configurações > Gerenciamento De Usuários > Configuração > Importar E Exportar Arquivos De Configuração.
1. Clique em Exportar. Se estiver usando o Microsoft Internet Explorer, você será solicitado a especificar um local para salvar o arquivo. Se você estiver usando o Firefox, o arquivo será salvo na área de trabalho.

**Importar as informações de configuração**

1. No Console De Administração, clique Em Configurações > Gerenciamento De Usuários > Configuração > Importar E Exportar Arquivos De Configuração.
1. Clique em Procurar para localizar o arquivo de configuração, clique em Importar e em OK.
