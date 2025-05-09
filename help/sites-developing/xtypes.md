---
title: Uso do xtypes (Interface clássica)
description: Saiba mais sobre todos os xtypes disponíveis com o Adobe Experience Manager
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4a78de53-33bf-4999-ba3c-7d0bc33196a4
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '3865'
ht-degree: 0%

---

# Uso do xtypes (Interface clássica){#using-xtypes-classic-ui}

Esta página descreve todos os xtypes que estão disponíveis no Adobe Experience Manager (AEM).

Na linguagem ExtJS, um xtype é um nome simbólico dado a uma classe. Você pode ler o parágrafo &quot;Component XTypes&quot; da [Visão geral do ExtJS 2](https://www.sencha.com/learn/overview-of-extjs-2) para obter uma explicação detalhada sobre o que é um xtype e como ele pode ser usado.

Para obter informações completas sobre todos os widgets disponíveis no AEM, consulte a [documentação da API de widget](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

Para descobrir em quais componentes um determinado xtype é usado no AEM, você pode usar a seguinte consulta Xpath no CRXDE substituindo &quot;caixa de seleção&quot; pelo xtype em que está interessado:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Esta página descreve o uso de ExtJS xtypes na interface clássica.
>
>A Adobe recomenda o uso da [interface do usuário habilitada para toque](/help/sites-developing/touch-ui-concepts.md) padrão moderna com base na [interface do usuário do Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui) e na [interface do usuário do Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Listados abaixo estão os xtypes disponíveis no Adobe Experience Manager:

* anotação

  [CQ.wcm.Annotation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.Annotation)

  A caixa de diálogo é um tipo especial de janela com um formulário no corpo e um grupo de botões no rodapé. Normalmente, é usado para editar conteúdo, mas também pode exibir somente informações.

* arraystore

  [CQ.Ext.data.ArrayStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.ArrayStore)

  Anteriormente conhecido como &quot;SimpleStore&quot;.

  Pequena classe auxiliar para facilitar a criação de [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store)s a partir de dados de matriz. Um ArrayStore é configurado automaticamente com um [CQ.Ext.data.ArrayReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.ArrayReader).

* asseteditor

  [CQ.dam.AssetEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.dam.AssetEditor)

  O Editor de ativos usado no Administrador do DAM.

* assetreferencesearchdialog

  [CQ.wcm.AssetReferenceSearchDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.AssetReferenceSearchDialog)

  O AssetReferenceSearchDialog é uma caixa de diálogo que aparece quando uma página faz referência a ativos ou tags.

* blueprintconfig

  [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig)

  O BlueprintConfig fornece um painel para exibir as Live Copies de um Blueprint e editar essas propriedades do Blueprint ( acionador de sincronização e ações de sincronização ).

* status do blueprint

  [CQ.wcm.msm.BlueprintStatus](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus)

  O BlueprintStatus fornece um painel para exibir e editar um Blueprint e seus relacionamentos com Live Copies. A navegação é feita por meio de um [CQ.wcm.msm.BlueprintStatus.Tree](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus.Tree), edição por meio de um [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig) e um [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties).

* caixa

  [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.BoxComponent)

  Classe base para qualquer [Componente](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Component) que deve ser dimensionado como uma caixa, usando largura e altura.

  O BoxComponent fornece ajustes automáticos do modelo de caixa para dimensionamento e posicionamento e funciona corretamente no modelo de renderização de Componente.

* browsedialog

  [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.BrowseDialog)

  A caixa de diálogo Procurar permite que o usuário navegue pelo repositório para selecionar um caminho. Normalmente é usado por meio de um [BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.BrowseField).

* browsefield

  [CQ.form.BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.BrowseField)

  **Obsoleto: em vez disso, use [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.PathField)**

* bulkeditor

  [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.BulkEditor)

  O BulkEditor fornece um mecanismo de pesquisa e uma grade para editar os resultados da pesquisa.

  O BulkEditor deve ser inserido em um formulário do HTML (exigido pela funcionalidade de importação). Funciona perfeitamente com um [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog).

* bulkeditorform

  [CQ.wcm.BulkEditorForm](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.BulkEditorForm)

  BulkEditorForm fornece [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.BulkEditor) rodeado por um formulário HTML. Esta é a versão autônoma do [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.BulkEditor). O formulário do HTML é necessário para o botão de importação.

* botão

  [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Button)

  Classe de botão simples

* grupo de botões

  [CQ.Ext.ButtonGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ButtonGroup)

  Contêiner de um grupo de botões.

* gráfico

  [CQ.Ext.chart.Chart](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.chart.Chart)

  O pacote CQ.Ext.chart fornece a capacidade de visualizar dados com gráficos baseados em flash. Cada gráfico se vincula diretamente a um CQ.Ext.data.Store, permitindo atualizações automáticas do gráfico. Para alterar a aparência de um gráfico, consulte as opções de configuração [chartStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.chart.Chart) e [extraStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.chart.Chart).

* caixa de seleção

  [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Checkbox)

  Campo de caixa de seleção única. Pode ser usado como uma substituição direta para campos de caixa de seleção tradicionais.

* checkboxgroup

  [CQ.Ext.form.CheckboxGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.CheckboxGroup)

  Um contêiner de agrupamento para controles [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Checkbox).

* clearcombo

  [CQ.form.ClearableComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ClearableComboBox)

  ClearableComboBox é uma caixa de combinação não editável com um acionador para limpar seu valor.

* colorfield

  [CQ.form.ColorField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ColorField)

  ColorField permite que o usuário insira um valor hexadecimal de cor diretamente ou usando um [CQ.Ext.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ColorMenu).

* colorlist

  [CQ.form.ColorList](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ColorList)

  ColorList permite que o usuário escolha uma cor em uma lista editável.

* colormenu

  [CQ.Ext.menu.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.ColorMenu)

  Um menu contendo um componente [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ColorPalette).

* colorpalette

  [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ColorPalette)

  Classe de paleta de cores simples para escolher cores. A paleta pode ser renderizada para qualquer container.

* combinação

  [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox)

  Um controle de caixa de combinação com suporte para preenchimento automático, carregamento remoto, paginação e muitos outros recursos.

  Uma ComboBox funciona de maneira semelhante a um campo &lt;select> tradicional do HTML. A diferença é que, para enviar o [valueField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox), você deve especificar um [hiddenName](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox) para criar uma entrada oculta.

* componente

  [CQ.Ext.Component](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Component)

  Classe base para todos os componentes Ext. Todas as subclasses de Componente podem participar do ciclo de vida automatizado do componente Ext de criação, renderização e destruição fornecido pela classe [Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container). Os componentes podem ser adicionados a um Contêiner por meio da opção de configuração [itens](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container) no momento em que o Contêiner é criado.

* component extrator

  [CQ.wcm.ComponentExtrator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ComponentExtractor)

  O ComponentExtrator permite que o usuário extraia componentes de um site/página.

* seletor de componentes

  [CQ.form.ComponentSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ComponentSelector)

  Uma seleção agrupada e ordenada de Componentes disponíveis.

* componentstyle

  [CQ.form.ComponentStyles](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ComponentStyles)

* composefield

  [CQ.form.CompositeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.CompositeField)

  Classe base para campos de formulário complexos e baseados em painel que incluem um campo de formulário ou um grupo de campos de formulário.

* container

  [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container)

  Classe base para qualquer [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.BoxComponent) que possa conter outros Componentes. Os contêineres manipulam o comportamento básico de itens que os contêm, ou seja, adicionar, inserir e remover itens.

  As classes Container mais usadas são [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Panel), [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window) e [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.TabPanel).

* contentfinder

  [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ContentFinder)

  O ContentFinder é um [Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Viewport) especializado de duas colunas que contém o Localizador de Conteúdo real à esquerda e o Quadro de Conteúdo à direita.

* contentfindertab

  [CQ.wcm.ContentFinderTab](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ContentFinderTab)

  ContentFinderTab é um painel especializado que fornece recursos usados nos painéis de guias do [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ContentFinder). Normalmente, ela apresenta um formulário de pesquisa - a Caixa de consulta - e uma visualização de dados para exibir a pesquisa.

* cq.workflow.model.combo

  [CQ.wcm.WorkflowModelCombo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.WorkflowModelCombo)

  WorkflowModelCombo é uma [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox) personalizada que mostra uma lista de modelos de fluxo de trabalho disponíveis.

* cq.workflow.model.selector

  [CQ.wcm.WorkflowModelSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.WorkflowModelSelector)

  O WorkflowModelSelector combina um WorkflowModelCombo com uma imagem em miniatura do fluxo de trabalho e botões para criar e editar modelos de fluxo de trabalho.

* createsitewwizard

  [CQ.wcm.CreateSiteWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.CreateSiteWizard)

  O CreateSiteWizard é um assistente passo a passo para criar sites (MSM).

* createversiondialog

  [CQ.wcm.CreateVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.CreateVersionDialog)

  CreateVersionDialog é uma caixa de diálogo que permite criar uma versão de uma página.

* customcontentpanel

  [CQ.CustomContentPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.CustomContentPanel)

  CustomContentPanel é um painel especial para uso no [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog): seu conteúdo é recuperado e enviado a uma URL diferente dos outros campos na caixa de diálogo.

* ciclo

  [CQ.Ext.CycleButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.CycleButton)

  Um SplitButton especializado, que contém um menu de [elementos CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.CheckItem). O botão percorre automaticamente cada item de menu em um clique, elevando o evento [change](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.CycleButton) do botão (ou chamando a função [changeHandler](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.CycleButton) do botão, se fornecida) para o item de menu ativo.

* dataview

  [CQ.Ext.DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DataView)

  Um mecanismo para exibir dados usando modelos e formatação de layout personalizados. DataView usa um [CQ.Ext.XTemplate](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.XTemplate) como mecanismo de modelo interno e está associado a um [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store) de forma que, à medida que os dados no armazenamento forem alterados, o modo de exibição seja atualizado automaticamente para refletir as alterações.

* datefield

  [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.DateField)

  Fornece um campo de entrada de data com uma lista suspensa [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DatePicker) e validação de data automática.

* datemenu

  [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.DateMenu)

  Um menu contendo um Componente [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DatePicker).

* datepicker

  [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DatePicker)

  Um seletor de datas pop-up. Esta classe é usada pela classe [DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.DateField) para permitir navegação e seleção de datas válidas.

* datetime

  [CQ.form.DateTime](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.DateTime)

  DateTime permite que o usuário insira uma data e uma hora combinando [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.DateField) e [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TimeField).

* caixa de diálogo

  [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog)

  A caixa de diálogo é uma janela especial com um formulário no corpo e um grupo de botões no rodapé. Normalmente, é usado para editar conteúdo, mas também pode exibir somente informações.

* dialogfieldset

  [CQ.form.DialogFieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.DialogFieldSet)

  O DialogFieldSet é um [FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.FieldSet) para uso em [Dialogs](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Dialog).

* directstore

  [CQ.Ext.data.DirectStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.DirectStore)

  Pequena classe auxiliar para criar um [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store) configurado com um [CQ.Ext.data.DirectProxy](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.DirectProxy) e [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.JsonReader) para facilitar a interação com um [CQ.Ext.Direct](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Direct) [Provedor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.direct.Provider) do lado do servidor.

* displayfield

  [CQ.Ext.form.DisplayField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.DisplayField)

  Um campo de texto somente exibição que não foi validado e não foi enviado.

* barra de edição

  [CQ.wcm.EditBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.EditBar)

  A Barra de edição permite que o usuário edite o conteúdo usando botões em uma barra.

  Embora não listada aqui, EditBar tem todos os membros de [CQ.wcm.EditBase](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.EditBase).

* editor

  [CQ.Ext.Editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Editor)

  Um campo do editor base que lida com exibição/ocultação sob demanda e tem alguma lógica interna de dimensionamento e manipulação de eventos.

* editorgrid

  [CQ.Ext.grid.EditorGridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)

  Esta classe estende a [Classe GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) para fornecer edição de célula nas [colunas](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.Column) selecionadas. As colunas editáveis são especificadas fornecendo um [editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) na [configuração de coluna](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.Column).

* substituição de edição

  [CQ.wcm.EditRollover](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.EditRollover)

  EditRollover permite que o usuário edite o conteúdo com um clique duplo e fornece mais ações de edição por meio de um menu de contexto. A área editável é indicada com um quadro quando o mouse passa sobre o conteúdo.

* feedimporter

  [CQ.wcm.FeedImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.FeedImporter)

  O FeedImporter permite que o usuário importe RSS ou Atom feeds e crie páginas para cada entrada de feed.

* campo

  [CQ.Ext.form.Field](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Field)

  Classe base para campos de formulário que fornece manipulação de eventos padrão, dimensionamento, manipulação de valores e outras funcionalidades.

* fieldset

  [CQ.Ext.form.FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.FieldSet)

  Contêiner padrão usado para agrupar itens em um [formulário](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.FormPanel).

* fileuploaddialogbutton

  [CQ.form.FileUploadDialogButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.FileUploadDialogButton)

  FileUploadDialogButton cria um botão que abre uma nova caixa de diálogo para fazer upload de um arquivo por meio do FileUploadField. Pode ser usado em caixas de diálogo de edição nas quais o upload deve ocorrer em um formulário separado.

* fileuploadfield

  [CQ.form.FileUploadField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.FileUploadField)

  FileUploadField permite que o usuário selecione um único arquivo para ser carregado.

* localizardiálogo

  [CQ.wcm.FindReplaceDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.FindReplaceDialog)

  FindReplaceDialog é uma caixa de diálogo para localizar e substituir tokens em uma página e suas páginas secundárias.

* flash

  [CQ.Ext.FlashComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.FlashComponent)

* grade

  [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)

  Essa classe representa a interface primária de um controle de grade baseado em componentes para representar dados em um formato tabular de linhas e colunas.

* groupingstore

  [CQ.Ext.data.GroupingStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)

  Uma implementação de loja especializada que fornece registros de agrupamento por um dos campos disponíveis. Isso é usado com um [CQ.Ext.grid.GroupingView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GroupingView) para provar o modelo de dados de um GridPanel agrupado.

* diálogo de movimentação pesada

  [CQ.wcm.HeavyMoveDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.HeavyMoveDialog)

  O HeavyMoveDialog é uma caixa de diálogo para mover uma página e suas páginas secundárias, considerando também a reativação de páginas ativadas anteriormente (movimentação &quot;pesada&quot;).

* oculto

  [CQ.Ext.form.Hidden](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Hidden)

  Um campo oculto básico para armazenar valores ocultos em formulários que devem ser transmitidos no envio do formulário.

* historybutton

  [CQ.HistoryButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.HistoryButton)

  O HistoryButton é uma pequena classe auxiliar para fornecer facilmente botões de voltar e avançar. Normalmente, duas instâncias relacionadas são necessárias: a instância do botão Avançar é um botão simples vinculado à instância do botão Voltar que lida com o histórico.

* htmleditor

  [CQ.Ext.form.HtmlEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)

  Fornece um componente leve do Editor do HTML. Alguns recursos da barra de ferramentas não são compatíveis com o Safari e são ocultos automaticamente quando necessário. Isso é observado nas opções de configuração, quando apropriado.

  Os botões da barra de ferramentas do editor têm dicas de ferramentas definidas na propriedade [buttonTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor).

* iframedialog

  [CQ.IframeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.IframeDialog)

  Uma caixa de diálogo simples que mostra o conteúdo de um iframe e permite formulários em iframes.

* iframepanel

  [CQ.IframePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.IframePanel)

  Um painel que contém um iframe. Fornece fácil criação de iframes, um evento de carregamento de iframe e fácil acesso ao conteúdo do iframe.

* inlinetextfield

  [CQ.form.InlineTextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.InlineTextField)

  InlineField é um campo de texto exibido como rótulo quando não está em foco.

* jsonstore

  [CQ.Ext.data.JsonStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.JsonStore)

  Pequena classe de ajuda para facilitar a criação de [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store)s a partir de dados JSON. Um JsonStore é configurado automaticamente com um [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.JsonReader).

* rótulo

  [CQ.Ext.form.Label](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Label)

  Campo Rótulo básico.

* language copydialog

  [CQ.wcm.LanguageCopyDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.LanguageCopyDialog)

  LanguageCopyDialog é uma caixa de diálogo para copiar árvores de idiomas.

* linkchecker

  [CQ.wcm.LinkChecker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.LinkChecker)

  O LinkChecker é uma ferramenta para verificar links externos em um site.

* listview

  [CQ.Ext.list.ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.ListView)

  CQ.Ext.list.ListView é uma implementação rápida e leve de uma exibição [Semelhante à grade](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel).

* livecopyproperties

  [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties)

  As Live CopyProperties fornecem um painel para exibir e editar propriedades da Live Copy ( herança de relacionamento, acionador de sincronização e ações de sincronização ).

* lvbooleancolumn

  [CQ.Ext.list.BooleanColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.BooleanColumn)

  Uma classe de definição Column que renderiza campos de dados booleanos. Consulte a opção de configuração [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column) para obter mais detalhes.

* lvcolumn

  [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column)

  Esta classe encapsula dados de configuração de coluna a serem usados na inicialização de um [ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.ListView).

* lvdatecolumn

  [CQ.Ext.list.DateColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.DateColumn)

  Uma classe de definição Column que renderiza uma data passada de acordo com a localidade padrão ou um [formato](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.DateColumn) configurado. Consulte a opção de configuração [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column) para obter mais detalhes.

* lvnumbercolumn

  [CQ.Ext.list.NumberColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)

  Uma classe de definição Column que renderiza um campo de dados numérico de acordo com uma cadeia de caracteres [format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.NumberColumn). Consulte a opção de configuração [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column) de [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.list.Column) para obter mais detalhes.

* mediabrowsedialog

  [CQ.MediaBrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.MediaBrowseDialog)

  **Obsoleto: em vez disso, use o [Localizador de Conteúdo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ContentFinder) para procurar mídia.**

  MediaBrowseDialog é uma caixa de diálogo para navegar na biblioteca de mídia.

* menu

  [CQ.Ext.menu.Menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.Menu)

  Um objeto de menu. Este é o contêiner ao qual você pode adicionar itens de menu. O menu também pode servir como classe base quando você deseja um menu especializado baseado em outro componente (como [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.DateMenu) por exemplo).

  Os menus podem conter [itens de menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.Item) ou [Componentes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Component)s gerais.

* menubaseitem

  [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.BaseItem)

  A classe base de todos os itens que são renderizados em menus. BaseItem fornece renderização padrão, gerenciamento de estado ativado e opções de configuração base compartilhadas por todos os componentes do menu.

* menucheckitem

  [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)

  Adiciona um item de menu que contém uma caixa de seleção por padrão, mas que também pode fazer parte de um grupo de opções.

* menuitem

  [CQ.Ext.menu.Item](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.Item)

  Uma classe base para todos os itens de menu que exigem funcionalidade relacionada a menu (como submenus) e não são itens de exibição estáticos. Item estende a funcionalidade base de [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.BaseItem) adicionando ativação específica de menu e manipulação de cliques.

* menuseparator

  [CQ.Ext.menu.Separador](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.Separator)

  Adiciona uma barra separadora a um menu, usada para dividir grupos lógicos de itens de menu. Geralmente, você adiciona um desses itens usando &quot;-&quot; na chamada para add() ou na configuração dos itens, em vez de criar um diretamente.

* menutextitem

  [CQ.Ext.menu.TextItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.menu.TextItem)

  Adiciona uma cadeia de texto estática a um menu, usada como separador de cabeçalho ou de grupo.

* metadados

  [CQ.dam.form.Metadata](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.dam.form.Metadata)

  Os metadados fornecem um conjunto de campos para determinar as informações necessárias para um campo de metadados conforme usado, por exemplo, nas páginas do Editor de ativos.

  Ela fornece os seguintes campos:

* multicampo

  [CQ.form.MultiField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.MultiField)

  O MultiField é uma lista editável de campos de formulário para editar propriedades de vários valores.

* mvt

  [CQ.form.MVT](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.MVT)

  O componente Multivariate Testing pode ser usado para definir e editar um conjunto de imagens que são apresentadas como banners alternados. As estatísticas de taxa de click-through são coletadas por banner.

* caixa de entrada de notificações

  [CQ.wcm.NotificationInbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.NotificationInbox)

  A NotificationInbox permite que o usuário assine ações WCM e gerencie notificações.

* numberfield

  [CQ.Ext.form.NumberField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.NumberField)

  Campo de texto numérico que fornece filtragem automática de pressionamento de tecla e validação numérica.

* offlineimporter

  [CQ.wcm.OfflineImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.OfflineImporter)

  O OfflineImporter é uma ferramenta para importar e converter documentos do Microsoft® Word para páginas do AEM. Esse recurso permite que o conteúdo seja editado offline usando um processador de texto.

* ownerdraw

  [CQ.form.OwnerDraw](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.OwnerDraw)

  O OwnerDraw pode conter código HTML personalizado (inserido diretamente ou recuperado de um URL).

* paginação

  [CQ.Ext.PagingToolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.PagingToolbar)

  À medida que o número de registros aumenta, o tempo necessário para que o navegador os renderize aumenta. A paginação é usada para reduzir a quantidade de dados trocados com o cliente.

* painel

  [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Panel)

  O painel é um contêiner que tem funcionalidade específica e componentes estruturais que o tornam o bloco de construção perfeito para interfaces do usuário orientadas por aplicativos.

  Os painéis são, em virtude de sua herança de [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container).

* referênciaparágrafo

  [CQ.form.ParagraphReference](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.ParagraphReference)

  O campo de referência de parágrafo permite navegar pelas páginas e selecionar um de seus parágrafos. Consiste em um campo de acionamento e uma caixa de diálogo de procura de parágrafo associada.

* senha

  [CQ.form.Password](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Password)

  A Senha é como um [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextField), mas mantém seu valor privado, permitindo que os usuários insiram dados confidenciais.

* pathcompletion

  [CQ.form.PathCompletion](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.PathCompletion)

  **Obsoleto: em vez disso, use [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.PathField)**

* pathfield

  [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.PathField)

  PathField é um campo de entrada criado para caminhos com conclusão de caminho e um botão para abrir um [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.BrowseDialog) para navegação no repositório do servidor. Ele também pode navegar pelos parágrafos da página para gerar links avançados.

* progresso

  [CQ.Ext.ProgressBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ProgressBar)

  Um componente atualizável da barra de progresso. A barra de progresso suporta dois modos diferentes: manual e automático.

  No modo manual, você é responsável por mostrar, atualizar (via [updateProgress](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ProgressBar)) e limpar a barra de progresso, conforme necessário, do seu próprio código. Esse método é mais apropriado quando você deseja mostrar o progresso.

* propertygrid

  [CQ.Ext.grid.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.PropertyGrid)

  Uma implementação de grade especializada destinada a imitar a grade de propriedade tradicional como normalmente visto em IDEs de desenvolvimento. Cada linha na grade representa uma propriedade de algum objeto, e os dados são armazenados como um conjunto de pares de nome/valor em [CQ.Ext.grid.PropertyRecord](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.PropertyRecord)s.

* propgrid

  [CQ.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.PropertyGrid)

  PropertyGrid é uma grade genérica usada para exibir e editar propriedades de objetos.

* dica rápida

  [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.QuickTip)

  @xtype quicktip Uma classe de dica de ferramenta especializada para dicas de ferramentas que podem ser especificadas na marcação e gerenciadas automaticamente pela instância global [CQ.Ext.QuickTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.QuickTips). Consulte o cabeçalho da classe QuickTips para obter detalhes e exemplos adicionais de uso.

* rádio

  [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Radio)

  Um único campo de rádio. Igual à caixa de seleção, mas fornecido como uma conveniência para definir automaticamente o tipo de entrada. O agrupamento de botões de opção é manipulado automaticamente pelo navegador se você atribuir o mesmo nome a cada rádio em um grupo.

* radiogroup

  [CQ.Ext.form.RadioGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.RadioGroup)

  Um contêiner de agrupamento para controles [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.Radio).

* referencesdialog

  [CQ.wcm.ReferencesDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.ReferencesDialog)

  A caixa de diálogo Referências é uma caixa de diálogo para exibir referências em uma página.

* restoretreedialog

  [CQ.wcm.RestoreTreeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.RestoreTreeDialog)

  RestoreTreeDialog é uma caixa de diálogo para restaurar uma versão anterior de uma árvore.

* restoreversiondialog

  [CQ.wcm.RestoreVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.RestoreVersionDialog)

  RestoreVersionDialog é uma caixa de diálogo para restaurar uma versão anterior de uma página.

* richtext

  [CQ.form.RichText](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.RichText)

  O RichText fornece um campo de formulário para editar informações de texto estilizado (rich text).

  O componente de RichText fornece atualmente os seguintes recursos:

* rolloutplan

  [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan)

  O Plano de implantação fornece uma caixa de diálogo para observar o andamento de uma implantação de página. O RolloutPlan foi iniciado por um [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard).

* rolloutwizard

  [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard)

  O Assistente de implantação fornece um assistente para implantar uma página. RolloutWizard inicia um [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan).

* searchfield

  [CQ.form.SearchField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SearchField)

  O SearchField fornece um campo de pesquisa que fornece os resultados em uma lista suspensa que pode ser usada para pesquisar o repositório.

* seleção

  [CQ.form.Selection](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Selection)

  A Selection permite que o usuário escolha entre várias opções. As opções podem fazer parte da configuração ou ser carregadas de uma resposta JSON. A Seleção pode ser renderizada como uma lista suspensa (selecionar) ou uma caixa combo (selecionar mais a entrada de texto livre).

* sidekick

  [CQ.wcm.Sidekick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.Sidekick)

  O Sidekick é um auxiliar flutuante que fornece ao usuário ferramentas comuns para edição de página.

* siteadmin

  [CQ.wcm.SiteAdmin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.SiteAdmin)

  O SiteAdmin é um console que fornece funções de administração do WCM.

* siteimporter

  [CQ.wcm.SiteImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.SiteImporter)

  O SiteImporter permite que o usuário importe sites completos e crie projetos iniciais.

* sizefield

  [CQ.form.SizeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SizeField)

  SizeField permite que o usuário insira a largura e a altura (por exemplo, para uma imagem).

* controle deslizante

  [CQ.Ext.Slider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Slider)

  Controle deslizante que suporta orientação vertical ou horizontal, ajustes do teclado, ajuste configurável, clique no eixo e animação. Pode ser adicionado como um item a qualquer container. Exemplo de uso: ...

* apresentação de slides

  [CQ.form.Slideshow](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Slideshow)

  A Apresentação de slides fornece um componente que pode ser usado para definir e editar um conjunto de imagens e títulos de imagem que podem ser exibidos como uma apresentação de slides.

  O componente de Apresentação de slides é baseado no componente [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SmartImage).

* smartfile

  [CQ.form.SmartFile](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SmartFile)

  O SmartFile é um carregador inteligente de arquivos.

  Se um plug-in do Flash (versão >= 9) estiver instalado, os uploads serão executados usando a biblioteca SWFupload que fornece uma maneira conveniente de lidar com uploads.

* smartimage

  [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SmartImage)

  O SmartImage é um carregador inteligente de imagens. Ele fornece ferramentas para processar uma imagem carregada, por exemplo, uma ferramenta para definir mapas de imagem e um cortador de imagem.

  O componente foi projetado para uso em uma guia de caixa de diálogo separada.

* espaçador

  [CQ.Ext.Spacer](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Spacer)

  Usado para fornecer um espaço considerável em um layout.

* ponteiro

  [CQ.form.Spinner](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Spinner)

  O Indicador de rotação é um campo de acionamento para valores numéricos, de data ou de hora. O valor pode ser aumentado e diminuído usando os acionadores para cima e para baixo fornecidos, a roda de rolagem ou as teclas.

* splitbutton

  [CQ.Ext.SplitButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.SplitButton)

  Um botão dividido que fornece uma seta suspensa integrada que pode acionar um evento separadamente do evento de clique padrão do botão. Normalmente, isso seria usado para exibir um menu suspenso que fornece opções adicionais para a ação do botão principal, mas qualquer manipulador personalizado pode fornecer a implementação de clique de seta.

* estático

  [CQ.Static](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Static)

  O estático pode ser usado para exibir texto arbitrário ou HTML.

* statistics

  [CQ.wcm.Statistics](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.Statistics)

  A página Estatísticas exibe as impressões da página como um gráfico. O widget permite selecionar um período para o qual as estatísticas devem ser exibidas.

* loja

  [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store)

  A classe Store encapsula um cache no lado do cliente de objetos [Record](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Record) que fornecem dados de entrada para Componentes como [GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), [ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox) ou [DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.DataView).

* sugestfield

  [CQ.form.SuggestField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.SuggestField)

  O campo Sugerir fornece ao usuário sugestões com base em sua entrada.

* alternador

  [CQ.Switcher](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Switcher)

  O Alternador fornece um grupo de botões para a barra de cabeçalho em um console para alternar entre Sites, Assets digital, Ferramentas, Fluxo de trabalho e Segurança.

* tableedit

  [CQ.form.TableEdit](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.TableEdit)

  **Obsoleto: em vez disso, use [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.TableEdit2).**

* tableedit2

  [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.TableEdit2)

  O TableEdit2 fornece um widget para criar tabelas.

* tabpanel

  [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.TabPanel)

  Um contêiner de guia básico. TabPanels podem ser usados exatamente como um [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Panel) padrão para fins de layout, mas também têm suporte especial para conter Componentes filho ([`items`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container)).

* tags

  [CQ.tagging.TagInputField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.tagging.TagInputField)

  ```
  CQ.tagging.TagInputField
  ```

  é um widget de formulário para inserção de tags. Ele tem um menu pop-up para seleção entre tags existentes, inclui preenchimento automático e muitos outros recursos.

* textarea

  [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextArea)

  Campo de texto multilinha. Pode ser usado como uma substituição direta para campos de área de texto tradicionais, além de adicionar suporte para dimensionamento automático.

* textbutton

  [CQ.TextButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.TextButton)

  O TextButton fornece um link de texto com os recursos de um [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Button).

* textfield

  [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextField)

  Campo de texto básico. Pode ser usado como substituição direta de entradas de texto tradicionais ou como classe base para controles de entrada mais sofisticados (como [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextArea) e [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.ComboBox)).

* miniatura

  [CQ.form.Thumbnail](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Thumbnail)

* campo de tempo

  [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TimeField)

  Fornece um campo de entrada de tempo com uma lista suspensa de tempo e validação de tempo automática. Exemplo de uso: ...

* dica

  [CQ.Ext.Tip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Tip)

  @xtype tip Esta é a classe base para [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.QuickTip) e [CQ.Ext.Tooltip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Tooltip) que fornece o layout básico e o posicionamento exigidos por todas as classes baseadas em dica. Esta classe pode ser usada diretamente para dicas simples, posicionadas estaticamente.

* titleseparator

  [CQ.menu.TitleSeparator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.menu.TitleSeparator)

  Adiciona uma barra separadora a um menu, usada para dividir grupos lógicos de itens de menu. O separador também pode carregar um título.

* barra de ferramentas

  [CQ.Ext.Toolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Toolbar)

  Classe da barra de ferramentas básica. Embora o [`defaultType`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Container) da Barra de Ferramentas seja [`button`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Button), os elementos da Barra de Ferramentas (itens filho para o contêiner da Barra de Ferramentas) podem ser praticamente qualquer tipo de Componente. Os elementos da barra de ferramentas podem ser criados explicitamente por meio de seus construtores.

* dica de ferramenta

  [CQ.Ext.ToolTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.ToolTip)

  Uma implementação de dica de ferramenta padrão para fornecer informações adicionais ao passar o mouse sobre um elemento de destino. @xtype tooltip

* treegrid

  [CQ.tree.TreeGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.tree.TreeGrid)

  @xtype treegrid

* treepanel

  [CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)

  O TreePanel fornece uma representação de dados estruturados em árvore na interface do usuário.

  O [TreeNode](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreeNode)s adicionado ao TreePanel pode conter metadados usados por seu aplicativo na propriedade [attributes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreeNode).

* acionador

  [CQ.Ext.form.TriggerField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TriggerField)

  Fornece um invólucro conveniente para TextFields que adiciona um botão acionador clicável (parece uma caixa combo por padrão). O gatilho não tem nenhuma ação padrão, portanto, você deve atribuir uma função para implementar o manipulador de cliques do gatilho substituindo [onTriggerClick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TriggerField). Você pode criar um TriggerField diretamente, pois ele é renderizado exatamente como uma caixa de combinação.

* upload

  [CQ.UploadDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.UploadDialog)

  O UploadDialog permite que o usuário carregue arquivos no repositório Cria um novo UploadDialog.

* userinfo

  [CQ.UserInfo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.UserInfo)

  Item da barra de ferramentas para exibir o nome de usuário atual e permitir ações do usuário, como editar propriedades e representação do usuário.

* viewport

  [CQ.Ext.Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Viewport)

  Um contêiner especializado que representa a área do aplicativo visível (a janela de visualização do navegador).

  O Viewport se renderiza para o corpo do documento e automaticamente se dimensiona para o tamanho do visor do navegador e gerencia o redimensionamento da janela. Só pode haver uma janela de visualização criada.

* janela

  [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window)

  Um painel especializado para uso como uma janela de aplicativo. As janelas são flutuantes, [redimensionáveis](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window) e [arrastáveis](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window) por padrão. As janelas podem ser [maximizadas](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window) para preencher o visor, restauradas ao tamanho anterior e podem ser [minimizadas](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window)d.

* xmlstore

  [CQ.Ext.data.XmlStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.XmlStore)

  Pequena classe auxiliar para facilitar a criação de [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.Store)s a partir de dados XML. Um XmlStore é configurado automaticamente com um [CQ.Ext.data.XmlReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.XmlReader).

  **cqinclude** Pseudo-xtype que inclui definições de widget de um caminho diferente no repositório. É usado com mais frequência em caixas de diálogo de página. Não há classe de widget JavaScript real para este xtype. Ele é processado pela função formatData() da classe CQ.Util. Para obter mais informações, consulte este artigo da knowledge base.
