---
title: Estender funcionalidade de pesquisa
description: Estender os recursos de pesquisa de  [!DNL Adobe Experience Manager Assets]  além dos padrões.
contentOwner: AG
role: Developer
feature: Search
solution: Experience Manager, Experience Manager Assets
exl-id: 92efe52b-8fa5-4006-bd68-2472b4ba04f6
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 16%

---

# Estender pesquisa de ativos {#extending-assets-search}

Você pode estender os recursos de pesquisa do [!DNL Adobe Experience Manager Assets]. Pronto para uso, [!DNL Experience Manager Assets] procura ativos por sequências de caracteres.

A pesquisa é feita por meio da interface do QueryBuilder para que a pesquisa possa ser personalizada com vários predicados. Você pode sobrepor o conjunto padrão de predicados no seguinte diretório: `/apps/dam/content/search/searchpanel/facets`.

Você também pode adicionar outras guias ao painel de administração [!DNL Assets].

>[!CAUTION]
>
>A partir do [!DNL Experience Manager] 6.4, a interface clássica será descontinuada. A Adobe recomenda usar a interface habilitada para toque. Para personalização, consulte [aspectos da pesquisa](/help/assets/search-facets.md).

## Sobreposição {#overlaying}

Para sobrepor os predicados pré-configurados, copie o nó `facets` de `/libs/dam/content/search/searchpanel` para `/apps/dam/content/search/searchpanel/` ou especifique outra propriedade `facetURL` na configuração `searchpanel` (o padrão é `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>Por padrão, a estrutura de diretório em `/apps` não existe, portanto, crie-a. Verifique se os tipos de nó correspondem àqueles em `/libs`.

## Adicionar guias {#adding-tabs}

Você pode adicionar outras guias de pesquisa configurando-as na interface do administrador do [!DNL Assets]. Para criar guias adicionais:

1. Crie a estrutura de pastas `/apps/wcm/core/content/damadmin/tabs,`se ela ainda não existir, copie o nó `tabs` de `/libs/wcm/core/content/damadmin` e cole-a.
1. Crie e configure a segunda guia, conforme desejado.

   >[!NOTE]
   >
   >Ao criar um segundo `siteadminsearchpanel`, defina uma propriedade `id` para evitar conflitos de formulário.

## Criar predicados personalizados {#creating-custom-predicates}

O [!DNL Assets] vem com um conjunto de predicados predefinidos que podem ser usados para personalizar uma página de Compartilhamento de ativos. A personalização de um Compartilhamento de ativos dessa maneira é abordada em [criar e configurar uma página de Compartilhamento de ativos](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Além de usar predicados pré-existentes, os desenvolvedores do [!DNL Experience Manager] também podem criar seus próprios predicados usando a [API do Construtor de Consultas](/help/sites-developing/querybuilder-api.md).

A criação de predicados personalizados requer conhecimento básico sobre a [Estrutura de widgets](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

A prática recomendada é copiar um predicado existente e ajustá-lo. Os predicados de amostra estão em **/libs/cq/search/components/predicates**.

### Exemplo: criar um predicado de propriedade simples {#example-build-a-simple-property-predicate}

Para criar um predicado de propriedade:

1. Crie uma pasta de componente no diretório de projetos, por exemplo, **/apps/weretail/components/title predicate**.
1. Adicionar **content.xml**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Adicionar `titlepredicate.jsp`.

   ```java
   <%--
   
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items are appended to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property", and so on.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate, additional parameters let you configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
       });
   </script>
   ```

1. Para disponibilizar o componente, é necessário editá-lo. Para tornar um componente editável, no CRXDE, adicione um nó **cq:editConfig** do tipo primário **cq:EditConfig**. Para que possa remover parágrafos, adicione uma propriedade de vários valores **cq:actions** com um único valor **DELETE**.
1. Navegue até o navegador e, na página de exemplo (por exemplo, **press.html**), alterne para o modo de design e habilite o novo componente para o sistema de parágrafo de predicado (por exemplo, **left**).

1. No modo **Editar**, o novo componente agora está disponível no sidekick (encontrado no grupo **Pesquisar**). Insira o componente na coluna **Predicados** e digite uma palavra de pesquisa, por exemplo, **Diamante**, e clique na lupa para iniciar a pesquisa.

   >[!NOTE]
   >
   >Ao pesquisar, digite o termo exatamente, incluindo as maiúsculas e minúsculas corretas.

### Exemplo: criar um predicado de grupo simples {#example-build-a-simple-group-predicate}

Para criar um predicado de grupo:

1. Crie uma pasta de componente no diretório de projetos, por exemplo, **/apps/weretail/components/picspredicate**.
1. Adicionar **content.xml**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Adicionar **titlepredicate.jsp**:

   ```java
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items are append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return for example, "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value, and so on.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
       });
   ```

1. Para disponibilizar o componente, é necessário editá-lo. Para tornar um componente editável, no CRXDE, adicione um nó **cq:editConfig** do tipo primário **cq:EditConfig**. Para que possa remover parágrafos, adicione uma propriedade de vários valores **cq:actions** com um único valor **DELETE**.
1. Navegue até o navegador e, na página de exemplo (por exemplo, **press.html**), alterne para o modo de design e habilite o novo componente para o sistema de parágrafo de predicado (por exemplo, **left**).
1. No modo **Editar**, o novo componente agora está disponível no sidekick (encontrado no grupo **Pesquisar**). Insira o componente na coluna **Predicados**.

## Widgets de predicado instalados {#installed-predicate-widgets}

Os seguintes predicados estão disponíveis como widgets ExtJS pré-configurados.

### PredicadoTextoCompleto {#fulltextpredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| predicateName | String | Nome do predicado. O padrão é `fulltext` |
| searchCallback | Função | Retorno de chamada para disparar a pesquisa no evento `keyup`. O padrão é `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| predicateName | String | Nome do predicado. O padrão é `property` |
| propertyName | String | Nome da propriedade JCR. O padrão é `jcr:title` |
| defaultValue | String | Valor padrão pré-preenchido. |

### PathPredicate {#pathpredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| predicateName | String | Nome do predicado. O padrão é `path` |
| rootPath | String | Caminho raiz do predicado. O padrão é `/content/dam` |
| pathFieldPredicateName | String | O padrão é `folder` |
| showFlatOption | Booleano | Sinalizador para mostrar Caixa de Seleção `search in subfolders`. O padrão é true. |

### DatePredicate {#datepredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| predicateName | String | Nome do predicado. O padrão é `daterange` |
| propertyname | String | Nome da propriedade JCR. O padrão é `jcr:content/jcr:lastModified` |
| defaultValue | String | Valor padrão pré-preenchido |

### OptionsPredicate {#optionspredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| cargo | String | Adiciona um título superior adicional |
| predicateName | String | Nome do predicado. O padrão é `daterange` |
| propertyname | String | Nome da propriedade JCR. O padrão é `jcr:content/metadata/cq:tags` |
| recolher | String | Recolher nível. O padrão é `level1` |
| triggerSearch | Booleano | Sinalizador para acionar a pesquisa na verificação. O padrão é falso |
| searchCallback | Função | Retorno de chamada para acionar a pesquisa. O padrão é `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Número | Tempo limite antes do acionamento de searchCallback. O padrão é 800 ms |

## Personalizar resultados da pesquisa {#customizing-search-results}

A apresentação dos resultados da pesquisa em uma página de Compartilhamento de ativos é regida pelas lentes selecionadas. O [!DNL Experience Manager Assets] vem com um conjunto de lentes predefinidas que podem ser usadas para personalizar uma página de Compartilhamento de ativos. A personalização de um Compartilhamento de ativos dessa maneira é abordada em [Criação e configuração de uma página de compartilhamento de ativos](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Além de usar lentes preexistentes, os desenvolvedores do [!DNL Experience Manager] também podem criar suas próprias lentes.
