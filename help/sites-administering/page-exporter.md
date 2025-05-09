---
title: O exportador da página
description: Saiba como usar o Exportador de páginas do Adobe Experience Manager (AEM).
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 997637d5-1627-4102-8b7c-a0cfd871a7b2
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# O exportador da página{#the-page-exporter}

O Adobe Experience Manager (AEM) permite exportar uma página como uma página da Web completa incluindo imagens, `.js` e `.css` arquivos.

Quando configurado, você solicita uma exportação de página do seu navegador, substituindo `html` por `export.zip` na URL. Isso gera um arquivo (zip) contendo a página renderizada em formato html, junto com os ativos referenciados. Todos os caminhos na página (por exemplo, caminhos para imagens) são regravados para apontar para os arquivos incluídos no arquivamento ou para os recursos no servidor. O arquivo compactado (zip) pode ser baixado do navegador.

>[!NOTE]
>
>Dependendo do navegador e das configurações, o download pode ser:
>
>* um arquivo morto (`<page-name>.export.zip`)
>* uma pasta (`<page-name>`); efetivamente, o arquivo morto já foi expandido

## Exportar uma página {#exporting-a-page}

As etapas a seguir descrevem como exportar uma página e supor que exista um modelo de exportação para o site. Um modelo de exportação define o modo como uma página é exportada e é específico do site. Para criar um modelo de exportação, consulte [Criando uma Configuração de Exportador de Página para seu Site](#creating-a-page-exporter-configuration-for-your-site).

Para exportar uma página:

1. Navegue até a página desejada no console **Sites**.

1. Selecione a página e abra a caixa de diálogo **Propriedades**.

1. Selecione a guia **Avançado**.

1. Expanda o campo **Exportar** para selecionar um modelo de exportação.
Selecione o modelo necessário para o site e confirme com **OK**.

1. Selecione **Salvar e fechar** para fechar a caixa de diálogo de propriedades da página.

1. Solicite a página para exportação, substituindo o sufixo `html` por `export.zip` na URL.

   Por exemplo:
   * localhost:4502/content/we-retail/language-masters/en.html

   Acessado por meio de:
   * localhost:4502/content/we-retail/language-masters/en.export.zip

1. Baixe o arquivo morto no sistema de arquivos.

1. Em seu sistema de arquivos, descompacte o arquivo, se necessário. Quando expandida, há uma pasta com o mesmo nome da página selecionada. Esta pasta contém:

   * a subpasta `content`, que é a raiz de uma série de subpastas que refletem o caminho para a página no repositório

      * dentro dessa estrutura há o arquivo html para a página selecionada (`<page-name>.html`)

   * outros recursos (`.js` arquivos, `.css` arquivos, imagens e assim por diante) estão localizados de acordo com as configurações no modelo de exportação

1. Abra o arquivo html da página (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) em seu navegador para que você possa verificar a renderização.

## Criação de uma configuração do Exportador de página para seu site {#creating-a-page-exporter-configuration-for-your-site}

O exportador da página é baseado na [estrutura de sincronização de conteúdo](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/package-summary.html). As configurações disponíveis na caixa de diálogo **Propriedades da página** são modelos de exportação que definem as dependências necessárias para uma página.

Quando uma exportação de página é acionada, o modelo de exportação é referenciado. O caminho da página e o caminho de design são aplicados dinamicamente. O arquivo zip é então criado usando a funcionalidade padrão Sincronização de conteúdo.

Uma instalação predefinida do AEM inclui um modelo padrão em `/etc/contentsync/templates/default`.

* Esse é o modelo de fallback quando nenhum modelo de exportação é encontrado no repositório.

* O modelo `default` mostra como uma exportação de página pode ser configurada, para que possa servir como base para um novo modelo de exportação.

* Para exibir a estrutura de nó do modelo em seu navegador como formato JSON, solicite o seguinte URL:
  `http://localhost:4502/etc/contentsync/templates/default.json`

O método mais fácil para criar um modelo de exportador de página é:

* copiar o modelo `default`,

* atribuir um novo nome, apropriado ao seu site,

* em seguida, faça as atualizações necessárias.

Para criar um template completamente novo:

1. Em **CRXDE Lite**, crie um nó abaixo de `/etc/contentsync/templates`:

   * `Name`: um nome apropriado para o seu site; por exemplo, `<mysite>`. O nome aparece na caixa de diálogo de propriedades da página ao escolher o modelo do exportador da página.

   * `Type`: `nt:unstructured`

2. Abaixo do nó do modelo, chamado aqui `mysite`, crie uma estrutura de nó usando os nós de configuração descritos abaixo.

## Ativar um modelo do exportador da página para suas páginas {#activating-a-page-exporter-configuration-for-your-pages}

Quando seu template estiver configurado, disponibilize-o:

1. No CRXDE, navegue até a página necessária na ramificação `/content`. Pode ser uma página individual ou a página raiz de uma subárvore.

1. No nó `jcr:content` da página, crie a propriedade:
   * `Name`: `cq:exportTemplate`
   * `Type`: `String`
   * `Value`: caminho para o modelo; por exemplo: `/etc/contentsync/templates/mysite`

### Nós de configuração do exportador da página {#page-exporter-configuration-nodes}

O modelo consiste em uma estrutura de nó, pois usa a [estrutura de sincronização de conteúdo](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/package-summary.html). Cada nó tem uma propriedade `type` que define uma ação específica no processo de criação do arquivo zip.

<!-- For more details about the type property, see the Overview of configuration types section in the Content Sync framework page.
-->

Os seguintes nós podem ser usados para criar um template de exportação:

* `page`
O nó da página é usado para copiar o html da página para o arquivo zip. Ele tem as seguintes características:

   * Um nó obrigatório.
   * Localizado abaixo de `/etc/contentsync/templates/<mysite>`.
   * Definido com a propriedade `Name`definida como `page`.
   * O tipo de nó é `nt:unstructured`

  O nó `page` tem as seguintes propriedades:

   * Uma propriedade `type` definida com o valor `pages`.

   * Ele não tem uma propriedade `path`, pois o caminho da página atual é copiado dinamicamente para a configuração.
  <!--
  * The other properties are described in the Overview of configuration types section of the Content Sync framework.
  -->

* `rewrite`
O nó rewrite define como os links são reescritos na página exportada. Os links regravados podem apontar para os arquivos incluídos no arquivo zip ou para os recursos no servidor.
  <!-- See the Content Sync page for a complete description of the `rewrite` node. -->

* `design`
O nó de design é usado para copiar o design usado para a página exportada. Ele tem as seguintes características:

   * Opcional.
   * Localizado abaixo de `/etc/contentsync/templates/<mysite>`.
   * Definido com a propriedade `Name` definida como `design`.
   * O tipo de nó é `nt:unstructured`.

  O nó `design` tem as seguintes propriedades:

   * Uma propriedade `type` foi definida com o valor `copy`.

   * Ele não tem uma propriedade `path`, pois o caminho da página atual é copiado dinamicamente para a configuração.

* `generic`
Um nó genérico é usado para copiar recursos como clientlibs `.js` ou `.css` arquivos para o arquivo zip. Ele tem as seguintes características:

   * Opcional.
   * Localizado abaixo de `/etc/contentsync/templates/<mysite>`.
   * Nenhum nome específico.
   * O tipo de nó é `nt:unstructured`.
   * Tem uma propriedade `type` e `type` propriedades relacionadas. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

  Por exemplo, o nó de configuração a seguir copia os arquivos `mysite.clientlibs.js` para o arquivo zip:

  ```xml
  "mysite.clientlibs.js": {
      "extension": "js",
      "type": "clientlib",
      "path": "/etc/designs/mysite/clientlibs",
      "jcr:primaryType": "nt:unstructured"
  }
  ```

**Implementando uma Configuração Personalizada**

Configurações personalizadas também são possíveis.

<!--
As you may have noticed in the node structure, the **Geometrixx** page export template has a `logo` node with a `type` property set to `image`. This is a special configuration type that has been created to copy the image logo to the zip file. 
-->

Para atender a alguns requisitos específicos, implemente um [manipulador de atualização personalizado](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/handler/package-summary.html).

<!-- To meet some specific requirements, you may need to implement a custom `type` property. To do so, see the Implementing a custom update handler section in the Content Sync page.
-->

## Exportar programaticamente uma página {#programmatically-exporting-a-page}

Para exportar uma página de forma programática, você pode usar o serviço OSGI [PageExporter](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html). Esse serviço permite:

* Exportar uma página e gravar na resposta do servlet HTTP.
* Exporte uma página e salve o arquivo zip em um local específico.

O servlet associado ao seletor `export` e à extensão `zip` usa o serviço PageExporter.

## Resolução de problemas {#troubleshooting}

Se você tiver um problema com o download do arquivo zip, poderá excluir o nó `/var/contentsync` no repositório e enviar a solicitação de exportação novamente.
