---
title: Mapeamento de recursos
description: Saiba como definir redirecionamentos, URLs personalizados e hosts virtuais para o Adobe Experience Manager usando o mapeamento de recursos.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
docset: aem65
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 90558227-c2c2-4130-9031-03efda5b1d94
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Mapeamento de recursos{#resource-mapping}

O mapeamento de recursos é usado para definir redirecionamentos, URLs personalizados e hosts virtuais para o Adobe Experience Manager (AEM).

Por exemplo, você pode usar esses mapeamentos para:

* Prefixe todas as solicitações com `/content` para que a estrutura interna fique oculta dos visitantes do seu site.
* Defina um redirecionamento para que todas as solicitações para a página `/content/en/gateway` do seu site sejam redirecionadas para `https://gbiv.com/`.

Um mapeamento HTTP possível prefixa todas as solicitações a `localhost:4503` com `/content`. Um mapeamento como esse pode ser usado para ocultar a estrutura interna dos visitantes do site, pois permite:

`localhost:4503/content/we-retail/en/products.html`

Para ser acessado usando:

`localhost:4503/we-retail/en/products.html`

Como o mapeamento adiciona automaticamente o prefixo `/content` a `/we-retail/en/products.html`.

>[!CAUTION]
>
>URLs personalizados não são compatíveis com padrões regex.

>[!NOTE]
>
>Consulte a documentação do Sling e os [Mapeamentos para Resolução de Recursos](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) e [Recursos](https://sling.apache.org/documentation/the-sling-engine/resources.html) para obter mais informações.

## Exibição de Definições de Mapeamento {#viewing-mapping-definitions}

Os mapeamentos formam duas listas que o JCR Resource Resolver avalia (de cima para baixo) para encontrar uma correspondência.

Essas listas podem ser exibidas (juntamente com informações de configuração) na opção **JCR ResourceResolver** do console Felix; por exemplo, `https://<*host*>:<*port*>/system/console/jcrresolver`:

* Configuração
Mostra a configuração atual (conforme definido para o [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver)).

* Teste de configuração
Isso permite inserir um URL ou um caminho de recurso. Clique em **Resolver** ou **Mapear** para confirmar como o sistema transformará a entrada.

* **Entradas do Mapa de Resolução**
A lista de entradas usadas pelos métodos ResourceResolver.resolve para mapear URLs para Recursos.

* **Mapeando Entradas do Mapa**
A lista de entradas usadas pelos métodos ResourceResolver.map para mapear Caminhos de Recursos para URLs.

As duas listas mostram várias entradas, incluindo aquelas definidas como padrão pelas aplicações. Geralmente, elas têm como objetivo simplificar URLs para o usuário.

As listas emparelham um **Padrão**, uma expressão regular que corresponde à solicitação, com uma **Substituição** que define o redirecionamento a ser imposto.

Por exemplo, o:

**Padrão** `^[^/]+/[^/]+/welcome$`

Acionará o:

**Substituição** `/libs/cq/core/content/welcome.html`.

Para redirecionar uma solicitação:

`https://localhost:4503/welcome`

Para:

`https://localhost:4503/libs/cq/core/content/welcome.html`

Novas definições de mapeamento são criadas no repositório.

>[!NOTE]
>
>Há muitos recursos disponíveis que ajudam a explicar como definir expressões regulares. Por exemplo, [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Criação de definições de mapeamento no AEM {#creating-mapping-definitions-in-aem}

Em uma instalação padrão do AEM, é possível encontrar a pasta:

`/etc/map/http`

Essa é a estrutura usada ao definir mapeamentos para o protocolo HTTP. Outras pastas ( `sling:Folder`) podem ser criadas em `/etc/map` para qualquer outro protocolo que você queira mapear.

#### Configuração de um redirecionamento interno para /content {#configuring-an-internal-redirect-to-content}

Para criar o mapeamento que prefixa qualquer solicitação para https://localhost:4503/ com `/content`:

1. Usando o CRXDE, navegue até `/etc/map/http`.

1. Criar um nó:

   * **Tipo** `sling:Mapping`
Esse tipo de nó se destina a esses mapeamentos, embora seu uso não seja obrigatório.

   * **Nome** `localhost_any`

1. Clique em **Salvar tudo**.
1. **Adicione** as seguintes propriedades a este nó:

   * **Nome** `sling:match`

      * **Tipo** `String`

      * **Valor** `localhost.4503/`

   * **Nome** `sling:internalRedirect`

      * **Tipo** `String[]`

      * **Valor** `/content/`

1. Clique em **Salvar tudo**.

Isso lida com uma solicitação como:
`localhost:4503/geometrixx/en/products.html`
como se:
`localhost:4503/content/geometrixx/en/products.html`
solicitadas.

>[!NOTE]
>
>Consulte [Recursos](https://sling.apache.org/documentation/the-sling-engine/resources.html) na Documentação do Sling para obter mais informações sobre as propriedades do sling disponíveis e como elas podem ser configuradas.

>[!NOTE]
>
>Você pode usar `/etc/map.publish` para manter as configurações para o ambiente de publicação. Estes devem ser replicados e o novo local ( `/etc/map.publish`) configurado para o **Local de Mapeamento** do [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) do ambiente de publicação.
