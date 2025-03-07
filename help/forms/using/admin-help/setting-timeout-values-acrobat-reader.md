---
title: Configuração de valores de tempo limite para uso com extensões do Acrobat Reader DC
description: Saiba como definir valores de tempo limite para usar com as extensões do Acrobat Reader DC.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: c2f96686-15e3-4d92-acfe-f971c5849de4
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Configuração de valores de tempo limite para uso com extensões do Acrobat Reader DC  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Ao trabalhar em muitos arquivos PDF nas extensões do Acrobat Reader DC, verifique se os seguintes valores de tempo limite estão definidos adequadamente para evitar que as tarefas atinjam o tempo limite e falhem:

**Tempo Limite para Descarte de Documentos**

Esse valor pode ser definido no console de administração. Clique em Configurações > Configurações principais do sistema > Configurações e especifique um valor para Tempo limite padrão de descarte de documentos.

**Tempo limite de formulários AEM do User Manager:** Esse valor pode ser definido ao editar o arquivo config.xml. No console de administração, clique em Configurações > Gerenciamento de usuários > Configuração > Importar e exportar arquivos de configuração e clique em Exportar. Abra o arquivo config.xml exportado e edite as seguintes linhas:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Salve e importe o arquivo config.xml de volta para o console de administração.

**Tempo Limite da Sessão do Servidor de Aplicativos:** Esse valor pode ser definido no servidor de aplicativos. Para obter mais informações, consulte a documentação fornecida com o servidor de aplicativos.
