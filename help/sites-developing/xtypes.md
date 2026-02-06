---
title: Usar xtypes (interface clássica)
description: Saiba mais sobre todos os xtypes disponíveis com o Adobe Experience Manager
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4a78de53-33bf-4999-ba3c-7d0bc33196a4
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '3668'
ht-degree: 0%

---

# Usar xtypes (interface clássica){#using-xtypes-classic-ui}

Esta página descreve todos os xtypes que estão disponíveis no Adobe Experience Manager (AEM).

Na linguagem ExtJS, um xtype é um nome simbólico dado a uma classe. Você pode ler o parágrafo &quot;Component XTypes&quot; da [Visão geral do ExtJS 2](https://docs.sencha.com/) para obter uma explicação detalhada sobre o que é um xtype e como ele pode ser usado.

Para obter mais informações sobre todos os widgets disponíveis no AEM, consulte a [documentação da API de widget](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

Para descobrir em quais componentes um determinado xtype é usado no AEM, você pode usar a seguinte consulta `Xpath` no CRXDE. Substitua &quot;caixa de seleção&quot; pelo xtype em que está interessado:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Esta página descreve o uso de ExtJS xtypes na interface clássica.
>
>A Adobe recomenda o uso da [interface do usuário habilitada para toque](/help/sites-developing/touch-ui-concepts.md) padrão moderna com base na [interface do usuário do Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui) e na [interface do usuário do Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Listados abaixo estão os xtypes disponíveis no Adobe Experience Manager:

* `annotation`

  [CQ.wcm.Annotation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Annotation` é uma janela especial. Ele tem um formulário em seu corpo e um grupo de botões em seu rodapé. Normalmente, é usado para editar conteúdo, mas também pode exibir somente informações.

* `arraystore`

  [CQ.Ext.data.ArrayStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Anteriormente conhecido como `SimpleStore`.

  Uma pequena classe auxiliar para facilitar a criação de [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s a partir de dados de Matriz. Um `ArrayStore` é configurado automaticamente com um [CQ.Ext.data.ArrayReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `asseteditor`

  [CQ.dam.AssetEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Asset Editor` é usado no Administrador do DAM.

* `assetreferencesearchdialog`

  [CQ.wcm.AssetReferenceSearchDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `AssetReferenceSearchDialog` é uma caixa de diálogo que aparece quando uma página faz referência a ativos ou tags.

* `blueprintconfig`

  [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `BlueprintConfig` fornece um painel para exibir as Live Copies de um Blueprint e editar essas propriedades do Blueprint (acionador de sincronização e ações de sincronização ).

* `blueprintstatus`

  [CQ.wcm.msm.BlueprintStatus](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O BlueprintStatus fornece um painel para exibir e editar um Blueprint e seus relacionamentos com Live Copies. A navegação é feita por meio de um [CQ.wcm.msm.BlueprintStatus.Tree](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), edição por meio de um [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e um [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `box`

  [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe base para qualquer [Componente](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) que deve ser dimensionado como uma caixa, usando largura e altura.

  O BoxComponent fornece ajustes automáticos do modelo de caixa para dimensionamento e posicionamento e funciona corretamente no modelo de renderização de Componente.

* `browsedialog`

  [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A caixa de diálogo Procurar permite que o usuário navegue pelo repositório para selecionar um caminho. Normalmente é usado por meio de um [BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `browsefield`

  [CQ.form.BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Obsoleto: em vez disso, use [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)**

* `bulkeditor`

  [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `BulkEditor` fornece um mecanismo de pesquisa e uma grade para editar os resultados da pesquisa.

  O `BulkEditor` deve ser inserido em um formulário HTML (exigido pela funcionalidade de importação). Funciona perfeitamente com um [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `bulkeditorform`

  [CQ.wcm.BulkEditorForm](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  BulkEditorForm fornece [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) rodeado por um formulário HTML. A versão independente do [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Um formulário do HTML é necessário para o botão de importação.

* `button`

  [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de botão simples

* `buttongroup`

  [CQ.Ext.ButtonGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Contêiner de um grupo de botões.

* `chart`

  [CQ.Ext.chart.Chart](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O pacote CQ.Ext.chart fornece a capacidade de visualizar dados com gráficos baseados em flash. Cada gráfico se vincula diretamente a um CQ.Ext.data.Store, permitindo atualizações automáticas do gráfico. Para alterar a aparência de um gráfico, consulte as opções de configuração [chartStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e [extraStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `checkbox`

  [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Campo de caixa de seleção única. Pode ser usado como uma substituição direta para campos de caixa de seleção tradicionais.

* `checkboxgroup`

  [CQ.Ext.form.CheckboxGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um contêiner de agrupamento para controles [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `clearcombo`

  [CQ.form.ClearableComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ClearableComboBox é uma caixa de combinação não editável com um acionador para limpar seu valor.

* `colorfield`

  [CQ.form.ColorField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ColorField permite que o usuário insira um valor hexadecimal de cor diretamente ou usando um [CQ.Ext.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `colorlist`

  [CQ.form.ColorList](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ColorList permite que o usuário escolha uma cor em uma lista editável.

* `colormenu`

  [CQ.Ext.menu.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um menu contendo um componente [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `colorpalette`

  [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe de paleta de cores simples para escolher cores. A paleta pode ser renderizada para qualquer container.

* `combo`

  [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um controle de caixa de combinação com suporte para preenchimento automático, carregamento remoto, paginação e muitos outros recursos.

  Uma ComboBox funciona de maneira semelhante a um campo &lt;select> tradicional do HTML. A diferença é que, para enviar o [valueField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), você deve especificar um [hiddenName](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para criar uma entrada oculta.

* `component`

  [CQ.Ext.Component](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe base para todos os componentes `Ext`. Todas as subclasses do Componente podem participar do ciclo de vida automatizado do componente `Ext` de criação, renderização e destruição fornecido pela classe [Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Os componentes podem ser adicionados a um Contêiner por meio da opção de configuração [itens](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) no momento em que o Contêiner é criado.

* `componentextractor`

  [CQ.wcm.ComponentExtrator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O ComponentExtrator permite que o usuário extraia componentes de um site/página.

* `componentselector`

  [CQ.form.ComponentSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma seleção agrupada e ordenada de Componentes disponíveis.

* `componentstyles`

  [CQ.form.ComponentStyles](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `compositefield`

  [CQ.form.CompositeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe base para campos de formulário complexos e baseados em painel que incluem um campo de formulário ou um grupo de campos de formulário.

* `container`

  [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe base para qualquer [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) que possa conter outros Componentes. Os contêineres manipulam o comportamento básico de itens que os contêm, ou seja, adicionar, inserir e remover itens.

  As classes Container mais usadas são [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `contentfinder`

  [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O ContentFinder é um [Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) especializado de duas colunas que contém o Localizador de Conteúdo real à esquerda e o Quadro de Conteúdo à direita.

* `contentfindertab`

  [CQ.wcm.ContentFinderTab](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinderTab é um painel especializado que fornece recursos usados nos painéis de guias do [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Normalmente, ele apresenta um formulário de pesquisa - a Caixa de consulta - e uma visualização de dados para exibir a pesquisa.

* `cq.workflow.model.combo`

  [CQ.wcm.WorkflowModelCombo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  WorkflowModelCombo é uma [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) personalizada que mostra uma lista de modelos de fluxo de trabalho disponíveis.

* `cq.workflow.model.selector`

  [CQ.wcm.WorkflowModelSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O WorkflowModelSelector combina um WorkflowModelCombo com uma imagem em miniatura do fluxo de trabalho e botões para criar e editar modelos de fluxo de trabalho.

* `createsitewizard`

  [CQ.wcm.CreateSiteWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O CreateSiteWizard é um assistente passo a passo para criar sites (MSM).

* `createversiondialog`

  [CQ.wcm.CreateVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CreateVersionDialog é uma caixa de diálogo que permite criar uma versão de uma página.

* `customcontentpanel`

  [CQ.CustomContentPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CustomContentPanel é um painel especial para uso no [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html): seu conteúdo é recuperado e enviado a uma URL diferente dos outros campos na caixa de diálogo.

* `cycle`

  [CQ.Ext.CycleButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um SplitButton especializado, que contém um menu de [elementos CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). O botão percorre automaticamente cada item de menu em cada clique, elevando o evento [change](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) do botão (ou chamando a função [changeHandler](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) do botão, se fornecida) para o item de menu ativo.

* `dataview`

  [CQ.Ext.DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um mecanismo para exibir dados usando modelos e formatação de layout personalizados. DataView usa um [CQ.Ext.XTemplate](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) como mecanismo de modelo interno e está associado a um [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de forma que, à medida que os dados no armazenamento forem alterados, o modo de exibição seja atualizado automaticamente para refletir as alterações.

* `datefield`

  [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ele fornece um campo de entrada de data com uma lista suspensa [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e validação de data automática.

* `datemenu`

  [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um menu contendo um Componente [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `datepicker`

  [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um seletor de datas pop-up. Esta classe é usada pela classe [DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para permitir navegação e seleção de datas válidas.

* `datetime`

  [CQ.form.DateTime](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  DateTime permite que o usuário insira uma data e uma hora combinando [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `dialog`

  [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A caixa de diálogo é uma janela especial. Ele tem um formulário em seu corpo e um grupo de botões em seu rodapé. Normalmente, é usado para editar conteúdo, mas também pode exibir somente informações.

* `dialogfieldset`

  [CQ.form.DialogFieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O DialogFieldSet é um [FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para uso em [Dialogs](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `directstore`

  [CQ.Ext.data.DirectStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma pequena classe auxiliar para criar um [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) configurado com um [CQ.Ext.data.DirectProxy](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para facilitar a interação com um [CQ.Ext.Direct](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) [Provedor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) do lado do servidor.

* `displayfield`

  [CQ.Ext.form.DisplayField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um campo de texto somente exibição que não foi validado e não foi enviado.

* `editbar`

  [CQ.wcm.EditBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A Barra de edição permite que o usuário edite o conteúdo usando botões em uma barra.

  Embora não listada aqui, EditBar tem todos os membros de [CQ.wcm.EditBase](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editor`

  [CQ.Ext.Editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um campo do editor base que lida com exibição/ocultação sob demanda e tem alguma lógica interna de dimensionamento e manipulação de eventos.

* `editorgrid`

  [CQ.Ext.grid.EditorGridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Esta classe estende a [Classe GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para fornecer edição de célula nas [colunas](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) selecionadas. As colunas editáveis são especificadas fornecendo um [editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) na [configuração de coluna](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editrollover`

  [CQ.wcm.EditRollover](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  EditRollover permite que o usuário edite o conteúdo com um clique duplo e fornece mais ações de edição por meio de um menu de contexto. A área editável é indicada com um quadro quando o mouse passa sobre o conteúdo.

* `feedimporter`

  [CQ.wcm.FeedImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O FeedImporter permite que o usuário importe RSS ou Atom feeds e crie páginas para cada entrada de feed.

* `field`

  [CQ.Ext.form.Field](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe base para campos de formulário que fornece manipulação de eventos padrão, dimensionamento, manipulação de valores e outras funcionalidades.

* `fieldset`

  [CQ.Ext.form.FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Contêiner padrão usado para agrupar itens em um [formulário](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `fileuploaddialogbutton`

  [CQ.form.FileUploadDialogButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FileUploadDialogButton cria um botão que abre uma nova caixa de diálogo para fazer upload de um arquivo por meio do FileUploadField. Pode ser usado em caixas de diálogo de edição nas quais o upload deve ocorrer em um formulário separado.

* `fileuploadfield`

  [CQ.form.FileUploadField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FileUploadField permite que o usuário selecione um único arquivo para ser carregado.

* `findreplacedialog`

  [CQ.wcm.FindReplaceDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  FindReplaceDialog é uma caixa de diálogo para localizar e substituir tokens em uma página e suas páginas secundárias.

* `flash`

  [CQ.Ext.FlashComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `grid`

  [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Essa classe representa a interface primária de um controle de grade baseado em componentes para representar dados em um formato tabular de linhas e colunas.

* `groupingstore`

  [CQ.Ext.data.GroupingStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma implementação de loja especializada que fornece registros de agrupamento por um dos campos disponíveis. Usado com um [CQ.Ext.grid.GroupingView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para provar o modelo de dados de um GridPanel agrupado.

* `heavymovedialog`

  [CQ.wcm.HeavyMoveDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O HeavyMoveDialog é uma caixa de diálogo para mover uma página e suas páginas secundárias, considerando também a reativação de páginas ativadas anteriormente (movimentação &quot;pesada&quot;).

* `hidden`

  [CQ.Ext.form.Hidden](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um campo oculto básico para armazenar valores ocultos em formulários que devem ser transmitidos no envio do formulário.

* `historybutton`

  [CQ.HistoryButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O HistoryButton é uma pequena classe auxiliar para fornecer botões de voltar e avançar facilmente. Normalmente, duas instâncias relacionadas são necessárias: a instância do botão Avançar é um botão simples vinculado à instância do botão Voltar que lida com o histórico.

* `htmleditor`

  [CQ.Ext.form.HtmlEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ele fornece um componente leve do Editor do HTML. O Safari não é compatível com alguns recursos da barra de ferramentas, portanto, o sistema os oculta automaticamente quando necessário. Anotada nas opções de configuração, quando apropriado.

  Os botões da barra de ferramentas do editor têm dicas de ferramentas definidas na propriedade [buttonTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `iframedialog`

  [CQ.IframeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma caixa de diálogo simples que mostra o conteúdo de um iframe e permite formulários em iframes.

* `iframepanel`

  [CQ.IframePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um painel que contém um iframe. Ele oferece fácil criação de iframes, um evento de carregamento de iframe e fácil acesso ao conteúdo do iframe.

* `inlinetextfield`

  [CQ.form.InlineTextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  InlineField é um campo de texto exibido como rótulo quando não está em foco.

* `jsonstore`

  [CQ.Ext.data.JsonStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma pequena classe auxiliar para facilitar a criação de [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s a partir de dados JSON. Um JsonStore é configurado automaticamente com um [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `label`

  [CQ.Ext.form.Label](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Campo Rótulo básico.

* `languagecopydialog`

  [CQ.wcm.LanguageCopyDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LanguageCopyDialog é uma caixa de diálogo para copiar árvores de idiomas.

* `linkchecker`

  [CQ.wcm.LinkChecker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O LinkChecker é uma ferramenta para verificar links externos em um site.

* `listview`

  [CQ.Ext.list.ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CQ.Ext.list.ListView é uma implementação rápida e leve de uma exibição [Semelhante à grade](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `livecopyproperties`

  [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  As Live CopyProperties fornecem um painel para exibir e editar propriedades da Live Copy ( herança de relacionamento, acionador de sincronização e ações de sincronização ).

* `lvbooleancolumn`

  [CQ.Ext.list.BooleanColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma classe de definição Column que renderiza campos de dados booleanos. Consulte a opção de configuração [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para obter mais detalhes.

* `lvcolumn`

  [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Esta classe encapsula dados de configuração de coluna a serem usados na inicialização de um [ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `lvdatecolumn`

  [CQ.Ext.list.DateColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma classe de definição Column que renderiza uma data passada de acordo com a localidade padrão ou um [formato](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) configurado. Consulte a opção de configuração [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para obter mais detalhes.

* `lvnumbercolumn`

  [CQ.Ext.list.NumberColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma classe de definição Column que renderiza um campo de dados numérico de acordo com uma cadeia de caracteres [format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Consulte a opção de configuração [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para obter mais detalhes.

* `mediabrowsedialog`

  [CQ.MediaBrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Obsoleto: em vez disso, use o [Localizador de Conteúdo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para procurar mídia.**

  MediaBrowseDialog é uma caixa de diálogo para navegar pela biblioteca de mídia.

* `menu`

  [CQ.Ext.menu.Menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um objeto de menu. O container ao qual você pode adicionar itens de menu. O menu também pode servir como classe base quando você deseja um menu especializado baseado em outro componente (como [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), por exemplo).

  Os menus podem conter [itens de menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ou [Componentes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s gerais.

* `menubaseitem`

  [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A classe base de todos os itens que são renderizados em menus. BaseItem fornece renderização padrão, gerenciamento de estado ativado e opções de configuração base compartilhadas por todos os componentes do menu.

* `menucheckitem`

  [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Por padrão, ele adiciona um item de menu que contém uma caixa de seleção, mas que também pode fazer parte de um grupo de opções.

* `menuitem`

  [CQ.Ext.menu.Item](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma classe base para todos os itens de menu que exigem funcionalidade relacionada a menu (como submenus) e não são itens de exibição estáticos. Item estende a funcionalidade base de [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) adicionando ativação específica de menu e manipulação de cliques.

* `menuseparator`

  [CQ.Ext.menu.Separador](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ele adiciona uma barra separadora a um menu, usada para dividir grupos lógicos de itens de menu. Geralmente, você adiciona um item usando &quot;-&quot; na sua chamada para add() ou na configuração dos itens, em vez de criar um diretamente.

* `menutextitem`

  [CQ.Ext.menu.TextItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ele adiciona uma string de texto estático a um menu, usada como separador de cabeçalho ou de grupo.

* `metadata`

  [CQ.dam.form.Metadata](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Metadata` fornece um conjunto de campos para determinar as informações necessárias para um campo de metadados conforme usado, por exemplo, nas páginas do Editor de ativos.

  Ela fornece os seguintes campos:

* `multifield`

  [CQ.form.MultiField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `MultiField` é uma lista editável de campos de formulário para editar propriedades de vários valores.

* `mvt`

  [CQ.form.MVT](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O componente Multivariate Testing pode ser usado para definir e editar um conjunto de imagens que são apresentadas como banners alternados. As estatísticas de taxa de click-through são coletadas por banner.

* `notificationinbox`

  [CQ.wcm.NotificationInbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `NotificationInbox` permite que o usuário assine ações WCM e gerencie notificações.

* `numberfield`

  [CQ.Ext.form.NumberField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Campo de texto numérico que fornece filtragem automática de pressionamento de tecla e validação numérica.

* `offlineimporter`

  [CQ.wcm.OfflineImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `OfflineImporter` é uma ferramenta para importar e converter documentos do Microsoft® Word para páginas do AEM. Esse recurso permite que o conteúdo seja editado offline usando um processador de texto.

* `ownerdraw`

  [CQ.form.OwnerDraw](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `OwnerDraw` pode conter código HTML personalizado (inserido diretamente ou recuperado de uma URL).

* `paging`

  [CQ.Ext.PagingToolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  À medida que o número de registros aumenta, o tempo necessário para que o navegador os renderize aumenta. A paginação é usada para reduzir a quantidade de dados trocados com o cliente.

* `panel`

  [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `panel` é um contêiner que tem funcionalidade específica e componentes estruturais que o tornam o bloco de construção perfeito para interfaces de usuário orientadas por aplicativos.

  Os painéis, em virtude de sua herança, são de [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `paragraphreference`

  [CQ.form.ParagraphReference](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O campo de referência de parágrafo permite navegar pelas páginas e selecionar um de seus parágrafos. Consiste em um campo de acionamento e uma caixa de diálogo de procura de parágrafo associada.

* `password`

  [CQ.form.Password](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Password` é como um [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), mas mantém seu valor privado, permitindo que os usuários insiram dados confidenciais.

* `pathcompletion`

  [CQ.form.PathCompletion](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Obsoleto: em vez disso, use [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)**

* `pathfield`

  [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `PathField` é um campo de entrada criado para caminhos com conclusão de caminho e um botão para abrir um [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para navegação no repositório do servidor. Ele também pode navegar pelos parágrafos da página para gerar links avançados.

* `progress`

  [CQ.Ext.ProgressBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um componente atualizável da barra de progresso. A barra de progresso suporta dois modos diferentes: manual e automático.

  No modo manual, você é responsável por mostrar, atualizar (via [updateProgress](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)) e limpar a barra de progresso, conforme necessário, do seu próprio código. Esse método é mais apropriado quando você deseja mostrar o progresso.

* `propertygrid`

  [CQ.Ext.grid.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma implementação de grade especializada destinada a imitar a grade de propriedade tradicional como normalmente visto em IDEs de desenvolvimento. Cada linha na grade representa uma propriedade de algum objeto, e os dados são armazenados como um conjunto de pares de nome/valor em [CQ.Ext.grid.PropertyRecord](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s.

* `propgrid`

  [CQ.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `PropertyGrid` é uma grade genérica usada para exibir e editar propriedades de objetos.

* `quicktip`

  [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `@xtype quicktip` - Uma classe de dica de ferramenta especializada para dicas de ferramenta que podem ser especificadas na marcação e gerenciadas automaticamente pela instância global [CQ.Ext.QuickTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Consulte o cabeçalho da classe QuickTips para obter detalhes e exemplos adicionais de uso.

* `radio`

  [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um único campo `radio`. Igual à caixa de seleção, mas fornecido como uma conveniência para definir automaticamente o tipo de entrada. O navegador agrupa botões de opção automaticamente quando cada botão de opção no grupo usa o mesmo nome.


* `radiogroup`

  [CQ.Ext.form.RadioGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um contêiner de agrupamento para controles [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `referencesdialog`

  [CQ.wcm.ReferencesDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `ReferencesDialog` é uma caixa de diálogo para exibir referências em uma página.

* `restoretreedialog`

  [CQ.wcm.RestoreTreeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `RestoreTreeDialog` é uma caixa de diálogo para restaurar uma versão anterior de uma árvore.

* `restoreversiondialog`

  [CQ.wcm.RestoreVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  RestoreVersionDialog é uma caixa de diálogo para restaurar uma versão anterior de uma página.

* `richtext`

  [CQ.form.RichText](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `RichText` fornece um campo de formulário para edição de informações de texto estilizado (rich text).

  O componente `RichText` fornece atualmente os seguintes recursos:

* `rolloutplan`

  [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O Plano de implantação fornece uma caixa de diálogo para observar o andamento de uma implantação de página. Um [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) inicia o RolloutPlan.

* `rolloutwizard`

  [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `RolloutWizard` fornece um assistente para implantação de uma página. RolloutWizard inicia um [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `searchfield`

  [CQ.form.SearchField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `SearchField` fornece um campo de pesquisa que fornece os resultados em uma lista suspensa que pode ser usada para pesquisar o repositório.

* `selection`

  [CQ.form.Selection](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Selection` permite que o usuário escolha entre várias opções. As opções podem fazer parte da configuração ou ser carregadas de uma resposta JSON. A Seleção pode ser renderizada como uma lista suspensa (selecionar) ou uma caixa combo (selecionar mais a entrada de texto livre).

* `sidekick`

  [CQ.wcm.Sidekick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Sidekick` é um auxiliar flutuante que fornece ao usuário ferramentas comuns para edição de página.

* `siteadmin`

  [CQ.wcm.SiteAdmin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `SiteAdmin` é um console que fornece funções de administração do WCM.

* `siteimporter`

  [CQ.wcm.SiteImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `SiteImporter` permite que o usuário importe sites concluídos e crie projetos iniciais.

* `sizefield`

  [CQ.form.SizeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `SizeField` permite que o usuário insira a largura e a altura (por exemplo, para uma imagem).

* `slider`

  [CQ.Ext.Slider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Controle deslizante que suporta orientação vertical ou horizontal, ajustes do teclado, ajuste configurável, clique no eixo e animação. Ele pode ser adicionado como um item a qualquer container. Por exemplo, uso: ...

* `slideshow`

  [CQ.form.Slideshow](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O componente de Apresentação de slides permite definir e editar um conjunto de imagens e títulos de imagem. Os usuários podem exibir o conjunto como uma apresentação de slides.

  O componente de Apresentação de slides é baseado no componente [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `smartfile`

  [CQ.form.SmartFile](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O SmartFile é um carregador inteligente de arquivos.

  Se um plug-in do Flash (versão >= 9) estiver instalado, os uploads serão executados usando a biblioteca SWFupload que fornece uma maneira conveniente de lidar com uploads.

* `smartimage`

  [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O SmartImage é um carregador inteligente de imagens. Ele fornece ferramentas para processar uma imagem carregada, por exemplo, uma ferramenta para definir mapas de imagem e um cortador de imagem.

  O componente foi projetado para uso em uma guia de caixa de diálogo separada.

* `spacer`

  [CQ.Ext.Spacer](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Usado para fornecer um espaço considerável em um layout.

* `spinner`

  [CQ.form.Spinner](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Spinner` é um campo de acionador para valores numéricos, de data ou de hora. O valor pode ser aumentado ou diminuído usando os acionadores para cima e para baixo, a roda de rolagem ou as teclas.

* `splitbutton`

  [CQ.Ext.SplitButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma `splitbutton` que fornece uma seta suspensa interna que pode acionar um evento separadamente do evento de clique padrão do botão. Normalmente, é usado para exibir um menu suspenso que fornece opções adicionais para a ação do botão principal, mas qualquer manipulador personalizado pode fornecer a implementação `arrowclick`.

* `static`

  [CQ.Static](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Static` pode ser usado para exibir texto arbitrário ou HTML.

* `statistics`

  [CQ.wcm.Statistics](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Statistics` exibe as impressões da página como um gráfico. O widget permite selecionar um período para o qual as estatísticas devem ser exibidas.

* `store`

  [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A classe `Store` encapsula um cache do lado do cliente de objetos [Record](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) que fornecem dados de entrada para Componentes como [GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ou [DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `suggestfield`

  [CQ.form.SuggestField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `SuggestField` fornece sugestões ao usuário com base em suas entradas.

* `switcher`

  [CQ.Switcher](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `Switcher` fornece um grupo de botões para a barra de cabeçalho em um console para alternar entre Sites, Assets Digital, Ferramentas, Fluxo de Trabalho e Segurança.

* `tableedit`

  [CQ.form.TableEdit](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Obsoleto: em vez disso, use [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).**

* `tableedit2`

  [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `TableEdit2` fornece um widget para a criação de tabelas.

* `tabpanel`

  [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um contêiner de guia básico. TabPanels podem ser usados exatamente como um [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) padrão para fins de layout, mas também têm suporte especial para conter Componentes filho ([`items`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `tags`

  [CQ.tagging.TagInputField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ```
  CQ.tagging.TagInputField
  ```

  é um widget de formulário para inserção de tags. Ele tem um menu pop-up para seleção entre tags existentes, inclui preenchimento automático e muitos outros recursos.

* `textarea`

  [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Campo de texto multilinha. Pode ser usado como substituição direta para campos `textarea` tradicionais, além de adicionar suporte para dimensionamento automático.

* `textbutton`

  [CQ.TextButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `TextButton` fornece um link de texto com os recursos de um [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `textfield`

  [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Campo de texto básico. Pode ser usado como substituição direta de entradas de texto tradicionais ou como classe base para controles de entrada mais sofisticados (como [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `thumbnail`

  [CQ.form.Thumbnail](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `timefield`

  [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ele fornece um campo de entrada de tempo com uma lista suspensa de tempo e validação de tempo automática. Exemplo de uso: ...

* `tip`

  [CQ.Ext.Tip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype tip Esta é a classe base para [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e [CQ.Ext.Tooltip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) que fornece o layout básico e o posicionamento exigidos por todas as classes baseadas em dica. Esta classe pode ser usada diretamente para dicas simples, posicionadas estaticamente.

* `titleseparator`

  [CQ.menu.TitleSeparator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ele adiciona uma barra separadora a um menu, usada para dividir grupos lógicos de itens de menu. O separador também pode carregar um título.

* `toolbar`

  [CQ.Ext.Toolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Classe `Toolbar` básica. Embora o [`defaultType`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) da Barra de Ferramentas seja [`button`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), os elementos da Barra de Ferramentas (itens filho para o contêiner da Barra de Ferramentas) podem ser praticamente qualquer tipo de Componente. Os elementos da barra de ferramentas podem ser criados explicitamente por meio de seus construtores.

* `tooltip`

  [CQ.Ext.ToolTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma implementação padrão `tooltip` para fornecer informações adicionais ao passar o mouse sobre um elemento de destino. @xtype tooltip

* `treegrid`

  [CQ.tree.TreeGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype `treegrid`

* `treepanel`

  [CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `TreePanel` fornece representação de dados estruturados em árvore da interface do usuário.

  O [TreeNode](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s adicionado ao `TreePanel` pode conter metadados usados por seu aplicativo na propriedade [attributes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `trigger`

  [CQ.Ext.form.TriggerField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Ele fornece um invólucro conveniente para `TextFields` que adiciona um botão de gatilho clicável (parece uma caixa de combinação por padrão). O gatilho não tem nenhuma ação padrão, portanto, você deve atribuir uma função para implementar o manipulador de cliques do gatilho substituindo [onTriggerClick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Você pode criar um `TriggerField` diretamente, pois ele é renderizado exatamente como uma caixa combo.

* `uploaddialog`

  [CQ.UploadDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  O `UploadDialog` permite que o usuário carregue arquivos no repositório Cria um novo UploadDialog.

* `userinfo`

  [CQ.UserInfo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Item da barra de ferramentas para exibir o nome de usuário atual e permitir ações do usuário, como editar propriedades e representação do usuário.

* `viewport`

  [CQ.Ext.Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um contêiner especializado que representa a área do aplicativo visível (a janela de visualização do navegador).

  O `Viewport` se renderiza para o corpo do documento, dimensiona-se automaticamente para o tamanho da janela de visualização do navegador e gerencia o redimensionamento de janelas. Só pode haver uma janela de visualização criada.

* `window`

  [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Um painel especializado para uso como uma janela de aplicativo. As janelas são flutuantes, [redimensionáveis](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) e [arrastáveis](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) por padrão. As janelas podem ser [maximizadas](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) para preencher o visor, restauradas ao tamanho anterior e podem ser [minimizadas](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)d.

* `xmlstore`

  [CQ.Ext.data.XmlStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Uma pequena classe auxiliar para facilitar a criação de [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s a partir de dados XML. Um `XmlStore` é configurado automaticamente com um [CQ.Ext.data.XmlReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

  `cqinclude` - Um pseudotipo que inclui definições de widget de um caminho diferente no repositório. Ele é usado com mais frequência em caixas de diálogo de página. Não há classe de widget JavaScript real para este xtype. A classe `CQ.Util` a processa usando a função `formatData()`.
