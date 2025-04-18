---
title: Suporte a cookies Same Site para o AEM 6.5
description: Saiba mais sobre o Suporte a cookies do mesmo site para o AEM 6.5.
topic-tags: security
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 77%

---

# Suporte a cookies Same Site para o AEM 6.5 {#same-site-cookie-support-for-aem-65}

Desde a versão 80, o Chrome e, mais tarde, o Safari introduziram um novo modelo para segurança de cookies. Esse modo é projetado para introduzir controles de segurança em torno da disponibilidade de cookies para sites de terceiros, por meio de uma configuração chamada `SameSite`. Para obter informações mais detalhadas, consulte este artigo [web.dev - SameSite cookies explained](https://web.dev/samesite-cookies-explained/).

O valor padrão dessa configuração (`SameSite=Lax`) pode fazer com que a autenticação entre instâncias ou serviços AEM não funcione. Isso ocorre porque os domínios ou as estruturas de URL desses serviços podem não se enquadrar nas restrições dessa política de cookie.

Para contornar isso, você precisa definir o atributo de cookie `SameSite` como `None` para o token de logon.

>[!CAUTION]
>
>A configuração `SameSite=None` só é aplicada se o protocolo for seguro (HTTPS).
>
>Se o protocolo não for seguro (HTTP), a configuração será ignorada e o servidor exibirá esta mensagem de AVISO:
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

É possível adicionar a configuração seguindo as etapas abaixo:

1. Vá para o Console da Web em `http://serveraddress:serverport/system/console/configMgr`
1. Pesquise e clique em **Manipulador de autenticação de token do Adobe Granite**
1. Defina o **atributo SameSite para o cookie de token de logon** para `None`, conforme mostrado na imagem abaixo
   ![samesite](assets/samesite1.png)
1. Clique em Salvar
1. Depois que esta configuração for atualizada e os usuários forem desconectados e conectados novamente, os cookies `login-token` terão o atributo `None` definido e serão incluídos em solicitações entre sites.
