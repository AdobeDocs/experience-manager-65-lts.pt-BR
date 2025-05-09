---
title: Configurações do serviço de nuvem
description: É possível estender as instâncias existentes para criar suas próprias configurações
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6b9b8d8c-8cd5-4c21-9b75-acd74d00354a
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 3%

---

# Configurações do serviço de nuvem{#cloud-service-configurations}

As configurações são projetadas para fornecer a lógica e a estrutura para armazenar configurações de serviço.

É possível estender as instâncias existentes para criar suas próprias configurações.

## Conceitos  {#concepts}

Os princípios usados no desenvolvimento das configurações foram baseados nos seguintes conceitos:

* Serviços/adaptadores são usados para recuperar as configurações.
* As configurações (por exemplo, propriedades/parágrafos) são herdadas dos pais.
* Referenciado a partir de nós do Analytics por caminho.
* Facilmente extensível.
* Tem flexibilidade para atender a configurações mais complexas, como o [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* Suporte para dependências (por exemplo, os plug-ins do [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) precisam da configuração [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)).

## Estrutura {#structure}

O caminho base das configurações é:

`/etc/cloudservices`.

Para cada tipo de configuração, um modelo e um componente são fornecidos. Isso possibilita ter modelos de configuração que podem atender à maioria das necessidades após a personalização.

Para fornecer uma configuração para novos serviços, faça o seguinte:

* Criar uma página de serviço no

  `/etc/cloudservices`

* Nesta seção:

   * um modelo de configuração
   * um componente de configuração

O modelo e o componente devem herdar `sling:resourceSuperType` do modelo base:

`cq/cloudserviceconfigs/templates/configpage`

Ou componente base, respectivamente

`cq/cloudserviceconfigs/components/configpage`

O provedor de serviços também deve fornecer a página de serviço:

`/etc/cloudservices/<service-name>`

### Modelo {#template}

Seu modelo estende o modelo base:

`cq/cloudserviceconfigs/templates/configpage`

E defina um `resourceType` que aponte para o componente personalizado.

```xml
/libs/cq/analytics/templates/sitecatalyst
sling:resourceSuperType = cq/cloudserviceconfigs/templates/configpage
allowedChildren = /libs/cq/analytics/templates/sitecatalyst
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
componentReference = cq/analytics/components/sitecatalyst
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/sitecatalystpage

/libs/cq/analytics/templates/generictracker
sling:resourceSuperType = cq/cloudservices/templates/configpage
allowedChildren = /libs/cq/analytics/templates/generictracker
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/generictrackerpage
```

### Componentes {#components}

Seu componente deve estender o componente básico:

`cq/cloudserviceconfigs/templates/configpage`

```xml
/libs/cq/analytics/components/sitecatalystpage

/libs/cq/analytics/components/generictrackerpage
```

Depois de definir o modelo e o componente, é possível adicionar a configuração adicionando subpáginas em:

`/etc/cloudservices/<service-name>`

### Modelo do conteúdo {#content-model}

O modelo de conteúdo é armazenado como `cq:Page` em:

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

As configurações são armazenadas no subnó `jcr:content`.

* As propriedades fixas, definidas em uma caixa de diálogo, devem ser armazenadas no `jcr:node` diretamente.
* Os elementos dinâmicos (que usam `parsys` ou `iparsys`) usam um subnó para armazenar os dados do componente.

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

Para obter a documentação de referência sobre a API, consulte [com.day.cq.wcm.webservicesupport](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### Integração do AEM {#aem-integration}

Os serviços disponíveis estão listados na guia **Serviços da Nuvem** da caixa de diálogo **Propriedades da Página** (de qualquer página que herde de `foundation/components/page` ou `wcm/mobile/components/page`).

A guia também fornece:

* um link para o local onde você pode habilitar o serviço
* escolha uma configuração (subnó do serviço) em um campo de caminho

#### Criptografia de senha {#password-encryption}

Ao armazenar credenciais de usuário para o serviço, todas as senhas devem ser criptografadas.

Você pode fazer isso adicionando um campo de formulário oculto. Este campo deve ter a anotação `@Encrypted` no nome da propriedade; ou seja, para o campo `password`, o nome seria gravado como:

`password@Encrypted`

A propriedade será criptografada automaticamente (usando o serviço `CryptoSupport`) pelo `EncryptionPostProcessor`.

>[!NOTE]
>
>Isso é semelhante às ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)` anotações padrão.

>[!NOTE]
>
>Por padrão, o `EcryptionPostProcessor` criptografa somente `POST` solicitações feitas para `/etc/cloudservices`.

#### Propriedades adicionais para a página de serviço jcr:nós de conteúdo {#additional-properties-for-service-page-jcr-content-nodes}

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td>componentReference</td>
   <td>Caminho de referência para um componente a ser incluído automaticamente na página.<br /> Usado para funcionalidade adicional e inclusões de JS.<br /> Isso inclui o componente na página em que <br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> está incluído (normalmente antes da marca <code>body</code>).<br /> No caso do Adobe Analytics e do Adobe Target, usamos isso para incluir funcionalidades adicionais, como chamadas do JavaScript para rastrear o comportamento do visitante.</td>
  </tr>
  <tr>
   <td>descrição</td>
   <td>Breve descrição do serviço.<br /> </td>
  </tr>
  <tr>
   <td>descriptionExtended</td>
   <td>Descrição estendida do serviço.</td>
  </tr>
  <tr>
   <td>classificação</td>
   <td>Classificação de serviço para uso em listagens.</td>
  </tr>
  <tr>
   <td>seletableChildren</td>
   <td>Filtro para exibir configurações na caixa de diálogo de propriedades da página.</td>
  </tr>
  <tr>
   <td>serviceUrl</td>
   <td>URL do site de serviço.</td>
  </tr>
  <tr>
   <td>serviceUrlLabel</td>
   <td>Rótulo para URL de serviço.</td>
  </tr>
  <tr>
   <td>thumbnailPath</td>
   <td>Caminho para a miniatura do serviço.</td>
  </tr>
  <tr>
   <td>visível</td>
   <td>Visibilidade na caixa de diálogo de propriedades da página; visível por padrão (opcional)</td>
  </tr>
 </tbody>
</table>

### Casos de uso {#use-cases}

Esses serviços são fornecidos por padrão:

* [Trechos do Rastreador](/help/sites-administering/external-providers.md) (Google, WebTrends e outros)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [Test&amp;Target](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
<!-- Search&Promote is end of life as of September 1, 2022 * [Search&Promote](/help/sites-administering/marketing-cloud.md#integrating-with-search-promote) -->
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Consulte também [Criação de uma Cloud Service personalizada](/help/sites-developing/extending-cloud-config-custom-cloud.md).
