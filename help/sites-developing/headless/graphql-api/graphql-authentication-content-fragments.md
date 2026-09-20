---
title: Autenticação para consultas remotas do Adobe Experience Manager GraphQL em fragmentos de conteúdo
description: Entenda a autenticação necessária para consultas remotas de GraphQL do Adobe Experience Manager para proteger sua entrega de conteúdo headless.
feature: Content Fragments,GraphQL API
solution: Experience Manager, Experience Manager Sites
role: Developer
exl-id: 8891b13d-5d7d-4ac5-99ba-bde8bff58a6d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 41%
---
# Autenticação para consultas remotas do Adobe Experience Manager GraphQL em fragmentos de conteúdo {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Um caso de uso fundamental para a [API do GraphQL do Adobe Experience Manager (AEM) para entrega de fragmentos de conteúdo](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) é o de aceitar consultas remotas de aplicativos ou serviços de terceiros. Essas consultas remotas podem exigir acesso à API autenticado para garantir a entrega de conteúdo headless.

>[!NOTE]
>
>Para testes e desenvolvimento, também é possível acessar a API GraphQL do AEM diretamente, usando a [interface GraphiQL](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphiql-interface).

Para autenticação, o serviço de terceiros precisa se autenticar usando o nome de usuário e a senha da conta do AEM.

<!-- 6.5.10.0 - does this content/page need to be migrated? -->

<!--
For authentication the third-party service needs to [retrieve an Access Token](#retrieving-access-token), that can then be [used in the GraphQL Request](#use-access-token-in-graphql-request).

## Retrieving an Access Token {#retrieving-access-token}

See [Generating Access Tokens for Server Side APIs](/help/sites-developing/generating-access-tokens-for-server-side-apis.md) for full details.

## Using the Access Token in a GraphQL Request {#use-access-token-in-graphql-request}

For a third-party service to connect with an AEM instance it needs to have an *Access Token*. The service must then add this token to the `Authorization` header on the POST request. 

For example, a GraphQL Authorization Header:

```xml
Authorization: Bearer <access_token>
```

## Permission Requirements {#permission-requirements}

All requests made using the access token will actually be made *by the user account that generated the token*. 

This means that you need to check that the account has the permissions required to run GraphQL queries. 

You can check this by using GraphiQL on the local instance.
-->
