---
title: Configurar o contêiner de layout e o modo de layout
description: Saiba como configurar o Contêiner de layout e o Modo de layout.
topic-tags: operations
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
source-git-commit: b6d27aa78b195a6131b43c83dc4df74b797490fa
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 2%

---


# Configurar o contêiner de layout e o modo de layout{#configuring-layout-container-and-layout-mode}

Saiba como configurar o Contêiner de layout e o Modo de layout.

>[!TIP]
>
>Este documento fornece uma visão geral do design responsivo para administradores e desenvolvedores de site, descrevendo como os recursos são realizados no AEM.
>
>Para autores de conteúdo, os detalhes de como usar recursos de design responsivo em uma página de conteúdo estão disponíveis no documento [Layout responsivo para suas páginas de conteúdo.](/help/sites-authoring/responsive-layout.md)

## Visão geral {#overview}

[Layout Responsivo](/help/sites-authoring/responsive-layout.md) é um mecanismo para realizar o [design responsivo da Web](https://en.wikipedia.org/wiki/Responsive_web_design). Isso permite que o usuário crie páginas da Web com um layout e dimensões dependentes dos dispositivos que seus usuários usam.

O AEM permite um layout responsivo para suas páginas usando uma combinação de mecanismos:

* Componente [**Contêiner de layout**](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)

  Esse componente fornece um sistema de parágrafo de grade para permitir adicionar e posicionar componentes em uma grade responsiva. Ela pode ser usada como o parsys padrão da página e/ou disponibilizada aos autores no navegador de componentes.

   * O componente **Contêiner de layout** padrão é definido em:

     /libs/wcm/foundation/components/responvegrid

   * É possível definir contêineres de layout:

      * Como um componente que o usuário pode adicionar a uma página.
      * Como o parsys padrão da página.
      * Ambos.

        Você pode ter o contêiner de layout como padrão para a página, permitindo que o usuário adicione mais contêineres de layout aqui; por exemplo, para obter o controle da coluna.

* **[Modo de layout](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**
Depois que o contêiner de layout é posicionado na página, você pode usar o modo **Layout** para posicionar conteúdo na grade responsiva.

* [**Emulador**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)
Isso permite criar e editar sites responsivos que reorganizam o layout de acordo com o tamanho do dispositivo ou da janela, redimensionando componentes interativamente. O usuário pode ver como o conteúdo é renderizado usando o Emulador.

Com esses mecanismos de grade responsivos, você pode:

* Use pontos de interrupção (que indicam o agrupamento de dispositivos) para definir comportamentos de conteúdo diferentes com base no layout do dispositivo.
* Ocultar componentes com base no grupo de dispositivos (defina em qual ponto de interrupção um componente será ocultado).
* Usar o alinhamento com a grade (colocar componentes na grade, redimensionar conforme necessário, definir quando eles devem ser recolhidos/refluir para ficarem lado a lado ou acima/abaixo).
* Executar o controle da coluna.

>[!TIP]
>
>A Adobe fornece a [documentação do GitHub](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) do layout responsivo como uma referência que pode ser fornecida para desenvolvedores front-end permitindo que usem a grade do AEM fora do AEM, por exemplo, ao criar modelos estáticos do HTML para um site futuro do AEM.

>[!NOTE]
>
>Em uma instalação predefinida, o layout responsivo foi configurado para o [site de referência We.Retail](/help/sites-developing/we-retail.md). [Ativar o componente Contêiner de Layout](#enable-the-layout-container-component-for-page) para outras páginas.

>[!CAUTION]
>
>Embora o componente **Contêiner de layout** esteja disponível na interface clássica, sua funcionalidade completa está disponível somente na interface habilitada para toque.

## Ativar modo de layout para o site {#activate-layout-mode-for-your-site}

Estes procedimentos são usados para habilitar o modo **Layout** no site.

### Configurar os pontos de interrupção {#configure-the-breakpoints}

[Pontos de interrupção](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* São usados em design responsivo.
* Pode ser definido:

   * No modelo de página, de onde as configurações são copiadas para qualquer página criada com esse modelo.
   * No nó da página, de onde as configurações são herdadas por qualquer página secundária.

* Defina um título e uma largura:

   * O título descreve o agrupamento genérico de dispositivos, com orientação se necessário; por exemplo, telefone, tablet, paisagem de tabelas.
   * A largura define a largura máxima em pixels para esse agrupamento de dispositivo genérico. Por exemplo, se o telefone do ponto de interrupção tiver uma largura de 768, isso indicará a largura máxima do layout usado para um dispositivo telefônico.

* Estão visíveis como marcadores na parte superior do editor de páginas quando você está usando o emulador.
* São herdados da hierarquia do nó principal e podem ser substituídos à vontade.
* Há um ponto de interrupção padrão (pronto para uso) que cobre tudo o que está acima do último ponto de interrupção *configurado*.

Eles podem ser definidos usando CRXDE Lite ou XML.

>[!NOTE]
>
>Se você estiver configurando um novo projeto:
>
>* adicionar pontos de interrupção aos modelos.
>
>Se você estiver migrando um projeto existente (com conteúdo existente), será necessário:
>
>* adicionar pontos de interrupção aos modelos
>* adicionar os mesmos pontos de interrupção às páginas existentes
>
>  Como a herança está em operação, é possível limitá-la à página raiz do seu conteúdo.

#### Configurar pontos de interrupção usando o CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Usando o CRXDE Lite (ou equivalente), navegue até:

   * A definição do modelo.
   * O nó `jcr:content` da página.

1. Em `jcr:content`, crie o nó:

   * Nome: `cq:responsive`
   * Tipo: `nt:unstructured`

1. Nesta seção, crie o nó:

   * Nome: `breakpoints`
   * Tipo: `nt:unstructured`

1. No nó pontos de interrupção, é possível criar qualquer número de pontos de interrupção. Cada definição é um único nó com as seguintes propriedades:

   * Nome: `<descriptive name>`
   * Tipo: `nt:unstructured`
   * Título: `String` * `<descriptive title seen in Emulator>`*
   * Largura: `Decimal` * `<value of breakpoint>`*

#### Configurar pontos de interrupção usando XML {#configuring-breakpoints-using-xml}

Os pontos de interrupção estão localizados dentro da seção `<jcr:content>` de `.context.html` na pasta de modelo (ou conteúdo) apropriada.

Um exemplo de definição:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### Adicionar um provedor de informações responsivo {#add-a-responsive-information-provider}

>[!NOTE]
>
>Isso só será necessário se o componente de Página não estiver baseado no componente de Página de base.

Copie a seguinte estrutura de nó `cq:infoProviders` no componente da página pai:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Ativar o redimensionamento de componentes para a página {#enable-component-resizing-for-the-page}

Esses procedimentos são necessários para que você possa redimensionar componentes no modo **Layout**.

### Definir contêiner de layout como parsys principal {#set-layout-container-as-main-parsys}

Para definir o parsys principal da página para ser um contêiner de layout, defina o parsys como:

`wcm/foundation/components/responsivegrid`

Em:

* Componente da página
* Modelo de página (para uso futuro)

Os dois exemplos a seguir ilustram a definição:

* **HTL:**

  ```html
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP:**

  ```html
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### Incluir o CSS responsivo {#include-the-responsive-css}

#### CSS para pontos de interrupção usando MENOS {#css-for-breakpoints-using-less}

O AEM usa MENOS para gerar partes do CSS necessário, que precisam ser incluídas nos projetos.

Você também deverá criar uma [biblioteca do cliente](https://experienceleague.adobe.com/pt-br/docs) para fornecer configuração e chamadas de função adicionais. A seguinte extração MENOS é um exemplo do mínimo que você deve adicionar ao seu projeto:

```css
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

A definição da grade base pode ser encontrada em:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Considerações sobre estilo {#styling-considerations}

Os componentes mantidos em um contêiner responsivo são redimensionados (juntamente com seus respectivos elementos DOM do HTML) de acordo com o tamanho da grade responsiva. Portanto, nessas circunstâncias, é recomendável evitar (ou atualizar) definições de elementos DOM de largura fixa (contidos).

Por exemplo:

* Antes:

   * `width=100px`

* Depois:

   * `max-width=100px`

#### Conformidade com redimensionamento e imagem adaptável {#resizing-and-adaptive-image-compliance}

Qualquer redimensionamento de um componente na grade acionará os seguintes ouvintes, conforme apropriado:

* `beforeedit`
* `beforechildedit`
* `afteredit`

* `afterchildedit`

Para redimensionar e atualizar corretamente o conteúdo de uma imagem adaptável incluída em uma grade responsiva, é necessário adicionar um conjunto `afterEdit` definido como ouvinte `REFRESH_PAGE` no arquivo `EditConfig` de cada componente contido.

Por exemplo:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

O mecanismo de imagem adaptável é disponibilizado por meio de um script que controla a seleção da imagem correta para o tamanho atual da janela. Ela é ativada depois que o DOM está pronto ou ao receber um evento dedicado. Atualmente, a página deve ser atualizada para refletir corretamente o resultado da ação do usuário.

>[!CAUTION]
>
>As clientlibs de folha de estilos personalizadas devem ser carregadas como parte do cabeçalho para que funcionem corretamente no autor e na publicação.

## Ativar o componente de Contêiner de layout para a página {#enable-the-layout-container-component-for-page}

Essas tarefas permitem que os autores arrastem instâncias do componente **Contêiner de layout** para a página.

### Ativar o componente de Contêiner de layout para edição de página {#enable-the-layout-container-component-for-page-editing}

Para permitir que os autores adicionem outras grades responsivas às páginas de conteúdo, é necessário ativar o componente Contêiner de layout para a página. Você pode fazer isso usando:

* **Ambiente do autor**

  Use o [Modo de design](/help/sites-authoring/default-components-designmode.md) para ativar o componente **Contêiner de Camada** para uma página.

* **Definição de Componente**

  Use `allowedComponent` ou uma inclusão estática ao definir o componente.

### Configurar a grade do contêiner de layout {#configure-the-grid-of-the-layout-container}

Você pode configurar o número de colunas disponíveis para cada instância específica do container de layout:

1. **Ambiente do autor**

   Você pode configurar o número de colunas disponíveis para cada instância específica do container de layout.

   Para fazer isso, use o [Modo de design](/help/sites-authoring/default-components-designmode.md) e abra a caixa de diálogo de design para o contêiner necessário. Aqui é possível especificar quantas colunas estarão disponíveis para posicionamento e dimensionamento. O padrão é 12.

1. **XML**

   As definições para a grelha responsiva são especificadas em:

   `etc/design/<*your-project-name*>/.content.xml`

   Os seguintes parâmetros podem ser definidos:

   * Número de colunas disponíveis:

      * `columns="{String}8"`

   * Componentes que podem ser adicionados ao componente atual:

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`

## Grades Responsivas Aninhadas {#nested-responsive-grids}

Pode haver ocasiões em que você ache necessário aninhar grades responsivas para suportar as necessidades do seu projeto. No entanto, lembre-se de que a prática recomendada pela Adobe é manter a estrutura o mais plana possível.

Quando não for possível evitar o uso de grades responsivas aninhadas, verifique se:

* Todos os contêineres (contêineres, guias, acordeões, etc.) têm a propriedade `layout = responsiveGrid`.
* Não misture a propriedade `layout = simple` na hierarquia de contêiner.

Isso inclui todos os containers estruturais do modelo de página.

O número da coluna do contêiner interno nunca deve ser maior que o do contêiner externo. O exemplo a seguir satisfaz essa condição. Embora o número da coluna do contêiner externo seja 8 para a tela padrão (desktop), o número da coluna do contêiner interno é 4.

>[!BEGINTABS]

>[!TAB Exemplo de estrutura de nó]

```text
container
  @layout = responsiveGrid
  cq:responsive
    default
      @offset = 0
      @width = 8
  container
  @layout = responsiveGrid
    cq:responsive
      default
        @offset = 0
        @width = 4
    text
      @text =" Text Column 1"
```

>[!TAB Exemplo de HTML resultante]

```html
<div class="container responsivegrid aem-GridColumn--default--none aem-GridColumn aem-GridColumn--default--8 aem-GridColumn--offset--default--0">
  <div id="container-c9955c233c" class="cmp-container">
    <div class="aem-Grid aem-Grid--8 aem-Grid--default--8 ">
      <div class="container responsivegrid aem-GridColumn--default--none aem-GridColumn aem-GridColumn--offset--default--0 aem-GridColumn--default--4">
        <div id="container-8414e95866" class="cmp-container">
          <div class="aem-Grid aem-Grid--4 aem-Grid--default--4 ">
            <div class="text aem-GridColumn aem-GridColumn--default--4">
              <div data-cmp-data-layer="..." id="text-1234567890" class="cmp-text">
                <p>Text Column 1</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

>[!ENDTABS]
