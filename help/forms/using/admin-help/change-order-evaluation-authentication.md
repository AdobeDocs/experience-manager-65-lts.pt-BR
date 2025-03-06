---
title: Alterar a ordem de avaliação para autenticação
description: Você pode alterar a ordem na qual o AEM Forms avalia vários provedores de autenticação.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 92609575368de96d07ce7f67fef4301fa838213e
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Alterar a ordem de avaliação para autenticação {#change-the-order-of-evaluation-for-authentication}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Se você configurou vários provedores de autenticação, é possível alterar a ordem em que o AEM Forms os avalia para autenticação. A ordem dos provedores de autenticação listados no arquivo config.xml determina a ordem de avaliação para autenticação.

1. No console de administração, clique em Configurações > Gerenciamento de usuários > Configuração > Importar e exportar arquivos de configuração.
1. Para exportar a definição da configuração atual para um arquivo, clique em Exportar e salve o arquivo de configuração em outro local.
1. Localize o seguinte nó no arquivo:

   ```xml
    <node name="AuthSchemes">
        <map />
            <node name="CertificateAuth">
                <map>
                    <entry key="order" value="3" />
                    <entry key="name" value="edc.server.auth.scheme.certificate" />
                </map>
        </node>
        <node name="Kerberos">
            <map>
                <entry key="kerberosSPN" value="defaultSPN" />
                <entry key="order" value="1" />
                <entry key="name" value="edc.server.auth.scheme.kerberos" />
            </map>
    </node>
   ```

   Em `<entry key="order" value="3" />`, edite o valor de cada nó para definir a ordem da avaliação de autenticação.

1. Para importar o arquivo atualizado, no Gerenciamento de usuários, clique em Configuração > Importar e exportar arquivos de configuração.
1. Clique em Procurar para localizar o arquivo, clique em Importar e em OK.
