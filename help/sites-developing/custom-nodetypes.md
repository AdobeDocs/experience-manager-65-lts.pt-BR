---
title: Tipos de nó personalizados
description: O Adobe Experience Manager (AEM) é baseado no Sling e usa um repositório JCR com tipos de nó oferecidos por ambos, mas o AEM também fornece uma variedade de tipos de nó personalizados
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1848'
ht-degree: 5%

---

# Tipos de nó personalizados{#custom-node-types}

Como o Adobe Experience Manager (AEM) é baseado no Sling e usa um repositório JCR, os tipos de nó oferecidos por ambos estão disponíveis para uso:

* [Tipos de nós JCR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Tipos de Nó do Sling](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

Além desses tipos de nó, o AEM fornece uma variedade de tipos de nó personalizados.

## Auditoria {#audit}

### cq:AuditEvent {#cq-auditevent}

**Descrição**

Define o tipo de nó de um nó de evento de auditoria.

* `@prop cq:time`
* `@prop cq:userid`
* `@prop cq:path`
* `@prop cq:type`
* `@prop cq:category`
* `@prop cq:properties`

**Definição**

* `[cq:AuditEvent]`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
* `- cq:time (date)`
* `- cq:userid (string)`
* `- cq:path (string)`
* `- cq:type (string)`
* `- cq:category (string)`
* `- cq:properties (binary)`

## Comentar {#comment}

### cq:Comment {#cq-comment}

**Descrição**

Define o nodetype de um nó de comentário.

* `@prop userIdentifier`

**Definição**

* `[cq:Comment] > mix:title, mix:created, mix:language, nt:unstructured, cq:Taggable`
* `- email (string)`
* `- ip (string)`
* `- referer (string)`
* `- url (string)`
* `- userAgent (string)`
* `- userIdentifier (string)`
* `- authorizableId (string)`

### cq:CommentAttachment {#cq-commentattachment}

**Descrição**

Define o nodetype de um nó `commentattachment`

**Definição**

* `[cq:CommentAttachment] > nt:file`
   * `- * (undefined)`
   * `- * (undefined) multiple`

### cq:CommentContent {#cq-commentcontent}

**Descrição**

Define o tipo de nó de um nó de conteúdo de comentário

**Definição**

* `[cq:Comment] > mix:title, mix:created, mix:language, nt:unstructured, cq:Taggable`
* `- email (string)`
* `- ip (string)`
* `- referer (string)`
* `- url (string)`
* `- userAgent (string)`
* `- userIdentifier (string)`
* `- authorizableId (string)`

### cq:GeoLocation {#cq-geolocation}

**Descrição**

Um mixin que define uma localização geográfica em graus decimais (DD)

* `@prop latitude` - latitude codificada como duplo usando graus decimais
* `@prop longitude` - longitude codificada como duplo usando graus decimais

**Definição**

* `[cq:GeoLocation] mixin`
* `- latitude (double)`
* `- longitude (double)`

### cq:Trackback {#cq-trackback}

**Descrição**

Define o tipo de nó de um nó de trackback.

**Definição**

* `[cq:Trackback] > mix:title, mix:created, mix:language, nt:unstructured`

## Núcleo {#core}

### cq:Page {#cq-page}

**Descrição**

Define a página CQ padrão.

* `@node jcr:content` - Conteúdo principal da página.

**Definição**

* `[cq:Page] > nt:hierarchyNode orderable`
   * `+ jcr:content (nt:base) = nt:unstructured copy primary`
   * `+ * (nt:base) = nt:base version`

### cq:PseudoPage {#cq-pseudopage}

**Descrição**

Define um tipo de mixin que marca nós como pseudo páginas. Em outras palavras, significa que eles podem ser adaptados para o suporte de edição de Página e WCM.

**Definição**

* `[cq:PseudoPage] mixin`

### cq:PageContent {#cq-pagecontent}

**Descrição**

Define o nó padrão para o conteúdo da página, com as propriedades mínimas conforme usadas pelo WCM.

* `@prop jcr:title` - Título da página.
* `@prop jcr:description` - Descrição desta página.
* `@prop cq:template` - Caminho para o modelo usado para criar a página.
* `@prop cq:allowedTemplates` - Lista de expressões regulares usadas para determinar os caminhos para o modelo permitido.
* `@prop pageTitle` - Título exibido na marca `<title>`.
* `@prop navTitle` - Título usado na navegação.
* `@prop hideInNav` - Especifica se a página deve estar oculta na navegação.
* `@prop onTime` - Hora em que esta página se torna válida.
* `@prop offTime` - Hora em que esta página se torna inválida.
* `@prop cq:lastModified` - Data da última modificação da página (ou de seus parágrafos).
* `@prop cq:lastModifiedBy` - Último usuário a alterar a página (ou seus parágrafos).
* `@prop jcr:language` - O idioma do conteúdo da página.

>[!NOTE]
>
>Não é obrigatório que o conteúdo da página use esse tipo.

**Definição**
* `[cq:PageContent] > nt:unstructured, mix:title, mix:created, cq:OwnerTaggable, sling:VanityPath, cq:ReplicationStatus, sling:Resource orderable`
   * `- cq:template (string)`
   * `- cq:allowedTemplates (string) multiple`
   * `- pageTitle (string)`
   * `- navTitle (string)`
   * `- hideInNav (boolean)`
   * `- onTime (date)`
   * `- offTime (date)`
   * `- cq:lastModified (date)`
   * `- cq:lastModifiedBy (string)`
   * `- cq:designPath (string)`
   * `- jcr:language (string)`

### cq:Template {#cq-template}

**Descrição**

Define um modelo CQ.

* `@node jcr:content` - Conteúdo padrão para novas páginas.
* `@node icon.png` - Um arquivo que contém um ícone característico.
* `@node thumbnail.png` - Um arquivo que contém uma imagem em miniatura característica.
* `@node workflows` - Atribuir automaticamente a configuração do fluxo de trabalho. A configuração segue a estrutura abaixo:
   * `+ workflows`
      * `+ name1`
         * `- cq:path`
            * `- cq:workflowName`
* `@prop allowedParents` - Padrões de expressão regular para determinar os caminhos para modelos permitidos como modelos pai.
* `@prop allowedChildren` - Padrões de expressão regular para determinar os caminhos para modelos permitidos como modelos filho.
* `@prop ranking` - Posição na lista de modelos na caixa de diálogo Criar página.

**Definição**

* `[cq:Template] > nt:hierarchyNode, mix:title`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
   * `+ jcr:content (nt:base) copy`
   * `+ icon.png (nt:file) copy`
   * `+ thumbnail.png (nt:file) copy`
   * `+ workflows (nt:base) copy`
   * `- allowedParents (string) multiple`
   * `- allowedChildren (string) multiple`
   * `- ranking (long)`

### cq:Component {#cq-component}

**Descrição**

Define um componente do CQ.

* `@prop jcr:title` - Título do componente.
* `@prop jcr:description` - Descrição do componente.
* `@node dialog` - Caixa de diálogo principal.
* `@prop dialogPath` - Caminho primário da caixa de diálogo (alternativa à caixa de diálogo).
* `@node design_dialog` - Caixa de diálogo de Design.
* `@prop cq:cellName` - Nome da célula de design.
* `@prop cq:isContainer` - Indica se é um componente de contêiner. Força os nomes das células dos componentes filhos a serem usados em vez dos nomes de caminho. Por exemplo, `parsys` é um componente de contêiner. Se esse valor não estiver definido, a verificação será feita com base na existência de um `cq:childEditConfig`.
* `@prop cq:noDecoration` - Se for verdadeiro, nenhuma marca `div` de decoração será desenhada ao incluir este componente.
* `@node cq:editConfig` - A configuração que define os parâmetros da barra de edição.
* `@node cq:childEditConfig` - A configuração de edição que é herdada por componentes filhos.
* `@node cq:htmlTag` - Define atributos de marca adicionais que são adicionados à marca `div` &quot;ao redor&quot; quando o componente é incluído.
* `@node icon.png`- Um arquivo que contém um ícone característico.
* `@node thumbnail.png` - Um arquivo que contém uma imagem em miniatura característica.
* `@prop allowedParents` - Padrões de expressão regular para determinar os caminhos de componentes permitidos como componentes pai.
* `@prop allowedChildren` - Padrões de expressão regular para determinar os caminhos de componentes permitidos como componentes filho.
* `@node virtual` - Contém subnós que refletem componentes virtuais usados para arrastar e soltar componentes.
* `@prop componentGroup` - Nome do grupo de componentes, usado para arrastar e soltar o componente.
* `@node cq:infoProviders` - Contém subnós, cada um dos quais tem uma propriedade `className` que se refere a um `PageInfoProvider`.

**Definição**

* `[cq:Component] > nt:folder, mix:title, sling:ResourceSuperType`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
   * `+ dialog (nt:base) = nt:unstructured copy`
   * `- dialogPath (string)`
   * `+ design_dialog (nt:base) = nt:unstructured copy`
   * `- cq:cellName (string)`
   * `- cq:isContainer (boolean)`
   * `- cq:noDecoration (boolean)`
   * `+ cq:editConfig (cq:EditConfig) = cq:EditConfig copy`
   * `+ cq:childEditConfig (cq:EditConfig) = cq:EditConfig copy`
   * `+ cq:htmlTag (nt:base) = nt:unstructured copy`
   * `+ icon.png (nt:file) copy`
   * `+ thumbnail.png (nt:file) copy`
   * `- allowedParents (string) multiple`
   * `- allowedChildren (string) multiple`
   * `+ virtual (nt:base) = sling:Folder copy`
   * `- componentGroup (string)`
   * `+ cq:infoProviders (nt:base) = nt:unstructured copy`

### cq:ComponentMixin {#cq-componentmixin}

**Descrição**

Define um componente CQ como um tipo de mixin.

**Definição**

`[cq:ComponentMixin] > cq:Component mixin`

### cq:EditConfig {#cq-editconfig}

**Descrição**

Define a configuração da &quot;barra de edição&quot;.

* `@prop cq:dialogMode` - Modo de diálogo:
   * `floating` - para uma caixa de diálogo flutuante normal
   * `inline` - edição em linha
   * `auto` - detecção automática (dependendo do espaço disponível)
* `@node cq:inplaceEditing` - Inserir configuração de edição para este componente.
* `@prop cq:layout`- Layout da barra de edição:
   * `editbar` - barra de edição
   * `rollover` - sobrepor quadro
   * `auto` - detecção automática
* `@node cq:formParameters`- Parâmetros adicionais para adicionar ao formulário de diálogo.
* `@prop cq:actions`- Lista de ações (botões da barra de edição ou itens de menu).
* `@node cq:actionConfigs` - Configurações de widget para a barra de edição ou itens de menu.
* `@prop cq:emptyText` - Texto a ser exibido se nenhum conteúdo visual estiver presente.
* `@node cq:dropTargets` - Coleção de `{@link cq:DropTargetConfig}` nós.

**Definição**

* `[cq:EditConfig] > nt:unstructured, nt:hierarchyNode orderable`
   * `- cq:dialogMode (string) < 'auto', 'floating', 'inline'`
   * `- cq:layout (string) < 'editbar', 'rollover', 'auto' + cq:formParameters (nt:base) = nt:unstructured`
   * `- cq:actions (string) multiple`
   * `+ cq:actionConfigs (nt:base) = nt:unstructured`
   * `- cq:emptyText (string)`
   * `+ cq:dropTargets (nt:base) = nt:unstructured`
   * `+ cq:listeners (nt:base) = cq:EditListenersConfig`

### cq:DropTargetConfig {#cq-droptargetconfig}

**Descrição**

Configura um alvo de liberação de um componente. O nome deste nó é usado como uma ID para arrastar e soltar.

* `@prop accept` - Lista de tipos MIME aceitos por este destino de lançamento; por exemplo, `["image/*"]`
* `@prop groups` - Lista de grupos de arrastar e soltar que aceitam uma origem.
* `@prop propertyName` - Nome da propriedade usada para armazenar a referência.

**Definição**

* `[cq:DropTargetConfig] > nt:unstructured orderable`
   * `- accept (string) multiple`
   * `- groups (string) multiple`
   * `- propertyName (string)`
   * `+ parameters (nt:base) = nt:unstructured`

### cq:VirtualComponent {#cq-virtualcomponent}

**Descrição**

Define um componente do CQ virtual. Atualmente usado apenas para o novo assistente de arrastar e soltar componente.

* `@prop jcr:title` - Título deste componente.
* `@prop jcr:description` - Descrição deste componente.
* `@node cq:editConfig` - Editar configuração que define os parâmetros da barra de edição.
* `@node cq:childEditConfig`- Editar configuração herdada por componentes filhos.
* `@node icon.png` - Um arquivo que contém um ícone característico.
* `@node thumbnail.png` - Um arquivo que contém uma imagem em miniatura característica.
* `@prop allowedParents` - Padrões de expressão regular para determinar caminhos de componentes permitidos como componentes pai.
* `@prop allowedChildren` - Padrões de expressão regular para determinar caminhos de componentes permitidos como componentes filho.
* `@prop componentGroup` - Nome do grupo de componentes para arrastar e soltar o componente.

**Definição**

`[cq:VirtualComponent] > nt:folder, mix:title`
`- * (undefined)`
`- * (undefined) multiple`
`+ * (nt:base) = nt:base multiple version`
`+ cq:editConfig (cq:EditConfig) = cq:EditConfig copy`
`+ icon.png (nt:file) copy`
`+ thumbnail.png (nt:file) copy`
`- allowedParents (string) multiple`
`- allowedChildren (string) multiple`
`- componentGroup (string)`

### cq:EditListenersConfig {#cq-editlistenersconfig}

**Descrição**

Define os ouvintes (do lado do cliente) a serem executados em um evento de edição. Os valores devem fazer referência a uma função de ouvinte válida do lado do cliente ou conter um atalho predefinido:

* `REFRESH_PAGE`
* `REFRESH_SELF`
* `REFRESH_PARENT`

* `@prop aftercreate` - Acionado após a criação de um componente.
* `@prop afteredit` - Acionado após um componente ter sido editado (modificado).
* `@prop afterdelete` - Acionado após a exclusão de um componente.
* `@prop afterinsert` - Acionado após a adição de um componente a este contêiner.
* `@prop afterremove` - Acionado após a remoção de um componente deste contêiner.
* `@prop aftermove` - Acionado após os componentes terem sido movidos neste contêiner.

**Definição**

* `[cq:EditListenersConfig]`
   * `- &ast; (undefined)`
   * `- &ast; (undefined) multiple`
   * `+ &ast; (nt:base) = nt:base multiple version`
   * `- aftercreate (string)`
   * `- afteredit (string)`
   * `- afterdelete (string)`
   * `- afterinsert (string)`
   * `- afterremove (string)`
   * `- aftermove (string)`

## DAM {#dam}

### dam:AssetContent {#dam-assetcontent}

**Descrição**

Conteúdo de um ativo DAM.

**Definição**

* `[dam:AssetContent] > nt:unstructured`
   * `+ metadata (nt:unstructured)`
   * `+ renditions (nt:folder)`

### dam:Asset {#dam-asset}

**Descrição**

Ativo DAM.

**Definição**

`[dam:Asset] > nt:hierarchyNode`
`+ jcr:content (dam:AssetContent) = dam:AssetContent copy primary`
`+ * (nt:base) = nt:base version`

### dam:Miniatura {#dam-thumbnail}

**Descrição**

Miniatura para representar um ativo DAM.

**Definição**

* `[dam:Thumbnails]`
   * `mixin`
   * `+ dam:thumbnails (nt:folder)`

## Lista de contêineres de entrega {#delivery-container-list}

### cq:containerList {#cq-containerlist}

**Descrição**

Lista de Contêineres.

**Definição**

* `[cq:containerList]`
   * `mixin`

## Página de entrega {#delivery-page}

### cq:Cq4PageAttributes {#cq-cq-pageattributes}

**Descrição**

O tipo de nó `cq:attributes` é para as marcas de versão do ContentBus. Esse nó tem apenas uma série de propriedades; das quais três são predefinidas &quot;created&quot;, &quot;csd&quot; e &quot;timestamp&quot;.

* `@prop created (long) mandatory copy` - Carimbo de data e hora de criação das informações de versão, geralmente a hora de check-in da versão anterior ou a hora de criação da página.
* `@prop csd (string) mandatory copy` - atributo padrão csd, cópia da propriedade cq:csd do nó da página
* `@prop timestamp (long) mandatory copy` - Carimbo de data/hora da última modificação de versão, geralmente verificando a hora.
* `@prop * (string) copy` - Atributos adicionais, com controle de versão com o nó pai.

**Definição**

* `[cq:Cq4PageAttributes] > nt:base`
   * `- created (long) mandatory copy`
   * `- csd (string) mandatory copy`
   * `- timestamp (long) mandatory copy`
   * `- &ast; (string) copy`

### cq:Cq4ContentPage {#cq-cq-contentpage}

**Descrição**

O tipo de nó `cq:contentPage` contém a propriedade e as definições de nó filho para páginas de conteúdo do ContentBus. Somente quando este tipo de mixin é adicionado a um nó do tipo `cq:page`, um nó se torna uma página de conteúdo do ContentBus.

Os itens em um `cq:Cq4ContentPage` são:

* `@prop cq:csd` - O CSD do ContentBus da página.
* `@node cq:content` - O conteúdo da página. Esse nó secundário não existe se o nó da página estiver no estado &quot;Existente sem conteúdo&quot; ou &quot;Excluído&quot;.
* `@node cq:attributes` - A lista de atributos de página, que eram conhecidos anteriormente como marcas de versão. Esse nó é obrigatório para o tipo cq:contentPage. Quando é feita a versão do nó da página, é feita a versão do nó dos atributos.

**Definição**

* `[cq:Cq4ContentPage]`
   * `- cq:csd (string) mandatory copy`
   * `+ cq:attributes (cq:Cq4PageAttributes)`

## Importador {#importer}

### cq:PollConfig {#cq-pollconfig}

**Descrição**

Configuração de enquete.

* `@prop source (String) mandatory` - URI da fonte de dados. Obrigatório e não deve estar vazio.
* `@prop target (String)` - O local de destino onde os dados recuperados da fonte de dados são armazenados. Opcional e assume como padrão o nó cq:PollConfig.
* `@prop interval (Long)` - O intervalo em segundos no qual pesquisar dados novos ou atualizados da fonte de dados. Opcional e o padrão é 30 minutos (1800 segundos).
* [Criando serviços personalizados de importação de dados para o Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/polling.html)

**Definição**

* `[cq:PollConfig]`
   * `mixin`
   * `- source (String) mandatory`
   * `- target (String)`
   * `- interval (Long)`

### cq:PollConfigFolder {#cq-pollconfigfolder}

**Descrição**

Tipo de nó principal de conveniência para criar facilmente nós de configuração de pesquisa.

**Definição**

`[cq:PollConfigFolder] > sling:Folder, cq:PollConfig`

## Local {#location}

### cq:GeoLocation {#cq-geolocation-1}

**Descrição**

Um mixin que define uma localização geográfica em graus decimais (DD).

* `@prop latitude` - Latitude codificada como duplo usando graus decimais.
* `@prop longitude` - Longitude codificada como duplo usando graus decimais.

**Definição**

* `[cq:GeoLocation]`
   * `mixin`
   * `- latitude (double)`
   * `- longitude (double)`

## Mailer {#mailer}

### cq:mailerMessage {#cq-mailermessage}

**Descrição**

Tipos de nó MailerService. O mailer usa nós que têm esse mixin como nós raiz de definições de mensagem.

**Definição**

* `[cq:mailerMessage]`
   * `mixin`
   * `- messageStatus (string)`
   * `= 'new'`
   * `mandatory autocreated`

## MSM {#msm}

### cq:LiveRelationship {#cq-liverelationship}

**Descrição**

Define uma combinação de LiveRelationship. Um nó de origem principal (controle) e um nó de live copy (controlado) podem ser vinculados virtualmente por meio de um LiveRelationship.

**Definição**

* `[cq:LiveRelationship] mixin`
   * `- cq:lastRolledout (date)`
   * `- cq:lastRolledoutBy (string)`
   * `- cq:sourceUUID (string)`

### cq:LiveSync {#cq-livesync}

**Descrição**

Define um mixin do LiveSync. Se um nó estiver envolvido em um LiveRelationship com um nó de origem primária (controle) e um nó de live copy (controlado), ele será marcado como um LiveSync.

* `@prop cq:master` - Caminho da origem primária (controle) do LiveRelationship.
* `@prop cq:isDeep` - Define se a relação está disponível para filhos.
* `@prop cq:syncTrigger` - Define quando é acionada a sincronização.
* `@node * LiveSyncAction` - Ações a serem executadas na sincronização

**Definição**

`[cq:LiveSync] > cq:LiveRelationship mixin orderable`
`+ * (cq:LiveSyncAction) = cq:LiveSyncAction`
`+ cq:LiveSyncConfig (nt:base) = cq:LiveSyncConfig`

### cq:LiveSyncCancelled {#cq-livesynccancelled}

**Descrição**

Define um mixin LiveSyncCancelled. Cancele o comportamento do LiveSync de um nó de live copy (controlado) que pode estar envolvido em um LiveRelationship devido a um de seus pais.

* `@prop cq:isCancelledForChildren` - Define se um LiveSync é cancelado; também para filhos.

**Definição**

* `[cq:LiveSyncCancelled] > cq:LiveRelationship mixin`
   * `- cq:isCancelledForChildren (boolean)`

### cq:LiveSyncAction {#cq-livesyncaction}

**Descrição**

Define uma LiveSyncAction anexada a uma LiveSync.

* `@prop name` - Nome da ação
* `@prop value` - Valor de ação

**Definição**

* `[cq:LiveSyncAction] > nt:unstructured`

### cq:LiveSyncConfig {#cq-livesyncconfig}

**Descrição**

Configuração do Live Sync.

**Definição**

* `[cq:LiveSyncConfig]`
   * `- cq:master (string) mandatory`
   * `- cq:isDeep (boolean)`
   * `- cq:trigger (string) /** deprecated **/`

Para o AEM 5.4, adicione ao final da lista:

* `- cq:rolloutConfigs (string) multiple /** deprecated **/`

### cq:BlueprintAction {#cq-blueprintaction}

**Descrição**

Ação de blueprint

**Definição**

* `[cq:BlueprintAction] > nt:unstructured`

## Platform {#platform}

### cq:Console {#cq-console}

**Descrição**

Define o tipo de nó de um nó de console.

**Definição**

* `[cq:Console] > sling:VanityPath, mix:title`
   * `mixin`

## Replicação {#replication}

### cq:ReplicationStatus {#cq-replicationstatus}

**Descrição**

Define a combinação de informações do status de replicação.

* `@prop cq:lastPublished`- A data em que a página foi publicada pela última vez (não é mais usada).
* `@prop cq:lastPublishedBy`- O usuário que publicou a página por último (não é mais usado).
* `@prop cq:lastReplicated` - A data da última replicação da página.
* `@prop cq:lastReplicatedBy` - O usuário que replicou a página por último.
* `@prop cq:lastReplicationAction` - A ação de replicação: ativar ou desativar.
* `@prop cq:lastReplicationStatus` - O status de replicação (não é mais usado).

**Definição**

* `[cq:ReplicationStatus]`
   * `mixin`
   * `- cq:lastPublished (date) ignore`
   * `- cq:lastPublishedBy (string) ignore`
   * `- cq:lastReplicated (date) ignore`
   * `- cq:lastReplicatedBy (string) ignore`
   * `- cq:lastReplicationAction (string) ignore`
   * `- cq:lastReplicationStatus (string) ignore`

## Segurança {#security}

### cq:ApplicationPrivilege {#cq-applicationprivilege}

**Descrição**

Define um privilégio de aplicativo.

**Definição**

* `[cq:ApplicationPrivilege] mixin`

### cq:PrivilegeAcl {#cq-privilegeacl}

**Descrição**

Define uma ACL de privilégio de aplicativo.

* `@prop cq:isPathDependent`
* `@node * ACEs`

**Definição**

* `[cq:PrivilegeAcl] > cq:ApplicationPrivilege mixin orderable`
   * `- cq:isPathDependent (boolean)`
   * `+ * (cq:PrivilegeAce) = cq:PrivilegeAce`

### cq:PrivilegeAce {#cq-privilegeace}

**Descrição**

Define um ACE de privilégio de aplicativo.

* `@prop path`
* `@prop deny`

**Definição**

* `[cq:PrivilegeAce]`
   * `- path mandatory`
   * `- deny (boolean)`

### cq:ApplicationPrivilege {#cq-applicationprivilege-1}

**Descrição**

Define um privilégio de aplicativo.

**Definição**

* `[cq:ApplicationPrivilege] mixin`

### cq:PrivilegeAcl {#cq-privilegeacl-1}

**Descrição**

Define uma ACL de privilégio de aplicativo.

* `@prop cq:isPathDependent`
* `@node * ACEs`

**Definição**

* `[cq:PrivilegeAcl] > cq:ApplicationPrivilege mixin orderable`
   * `- cq:isPathDependent (boolean)`
   * `+ * (cq:PrivilegeAce) = cq:PrivilegeAce`

### cq:PrivilegeAce {#cq-privilegeace-1}

**Descrição**

Define um ACE de privilégio de aplicativo.

* `@prop path`
* `@prop deny`

**Definição**

* `[cq:PrivilegeAce]`
   * `- path mandatory`
   * `- deny (boolean)`

## Importador de sites {#site-importer}

### cq:ComponentExtratorSource {#cq-componentextractorsource}

**Descrição**

Define um tipo de mixin que marca arquivos que podem ser abertos com o extrator de componentes.

**Definição**

`[cq:ComponentExtractorSource] mixin`

## Marcação com tags {#tagging}

### cq:Tag {#cq-tag}

**Descrição**

Define uma única tag, mas também pode conter tags, criando uma taxonomia

**Definição**

* `[cq:Tag] > nt:base, mix:title`
   * `- sling:resourceType (String)`
   * `- * (undefined) multiple`
   * `- * (undefined)`
   * `+ * (nt:base) = cq:Tag version`

### cq:Taggable {#cq-taggable}

**Descrição**

Mistura de base abstrata para conteúdo rastreável.

* `@node cq:tags`

**Definição**

* `[cq:Taggable]`
   * `- cq:tags (string) multiple`

### cq:OwnerTaggable {#cq-ownertaggable}

**Descrição**

Somente os autores/proprietários têm permissão para marcar o conteúdo (marcação moderada/administrada).

**Definição**

* `[cq:OwnerTaggable] > cq:Taggable`

### cq:UserTaggable {#cq-usertaggable}

**Descrição**

Qualquer site do usuário/público pode marcar o conteúdo (estilo Web2.0), usado dentro de cq:userContent.

**Definição**

* `[cq:UserTaggable] > cq:Taggable`
   * `mixin`

### cq:AllowsUserContent {#cq-allowsusercontent}

**Descrição**

Adiciona um subnó `cq:userContent` que pode ser modificado pelos usuários. Cada usuário tem seu próprio subnó `cq:userContent/<userid>`, que normalmente tem o mixin `cq:UserTaggable`.

**Definição**

* `[cq:AllowsUserContent]`
   * `mixin`
   * `+ cq:userContent (nt:unstructured)`

Variante estendida, definindo mais explicitamente a árvore `cq:userContent`

* `[cq:AllowsUserContent]`
   * `mixin`
   * `+ cq:userContent (cq:UserContent)`

### cq:UserContent {#cq-usercontent}

**Descrição**

Pode ser modificado por usuários.

**Definição**

* `[cq:UserContent] > nt:unstructured`
   * `// userids`
   * `+ * (cq:UserData)`
   * `// other content`
   * `+ * (nt:base)`

### cq:UserData {#cq-userdata}

**Descrição**

Dados do usuário

**Definição**

* `[cq:UserData] > nt:unstructured, cq:UserTaggable`

## Widgets {#widgets}

### cq:ClientLibraryFolder {#cq-clientlibraryfolder}

**Descrição**

Pasta da biblioteca do cliente

**Definição**

* `[cq:ClientLibraryFolder] > sling:Folder`
   * `- categories (string) multiple`
   * `- dependencies (string) multiple`

### cq:Widget {#cq-widget}

**Descrição**

Widget

**Definição**

* `[cq:Widget] > nt:unstructured orderable`
   * `- xtype (string)`
   * `- name (string)`
   * `- title (string)`
   * `+ items (nt:base) = cq:WidgetCollection copy`

### cq:WidgetCollection {#cq-widgetcollection}

**Descrição**

Coleção do widget

**Definição**

* `[cq:WidgetCollection] > nt:unstructured`
   * `orderable`
   * `+ * (cq:Widget) = cq:Widget copy`

### cq:Dialog {#cq-dialog}

**Descrição**

Caixa de diálogo

**Definição**

* `[cq:Dialog] > cq:Widget orderable`

### cq:Panel {#cq-panel}

**Descrição**

Painel

**Definição**

`[cq:Panel] > cq:Widget orderable`

### cq:TabPanel {#cq-tabpanel}

**Descrição**

Painel de guias

**Definição**

* `[cq:TabPanel]` > `cq:Panel orderable`
   * `- activeTab (long)`

### cq:Field {#cq-field}

**Descrição**

Texto

**Definição**

* `[cq:Field] > cq:Widget orderable`
   * `- fieldLabel (string)`
   * `- value (string)`
   * `- ignoreData (boolean)`

## Wiki {#wiki}

### wiki:Tópico {#wiki-topic}

**Descrição**

Tópico Wiki

**Definição**

* `[wiki:Topic] > nt:unstructured, nt:hierarchyNode, mix:versionable, mix:lockable`
   * `+ * (wiki:Topic) version`
   * `+ wiki:attachments (nt:folder) = nt:folder version`
   * `+ wiki:properties (wiki:Properties) = wiki:Properties copy`
   * `- wiki:text (string) mandatory primary`
   * `- wiki:lastModified (date) mandatory`
   * `- wiki:lastModifiedBy (string) mandatory`
   * `- wiki:topicName`
   * `- wiki:topicTitle`
   * `- wiki:lockedBy`
   * `- wiki:logMessage (string)`
   * `- wiki:quietSave (boolean)`

### wiki:Usuário {#wiki-user}

**Descrição**

Usuário wiki

**Definição**

* `[wiki:User] mixin`
   * `- wiki:subscriptions (string) multiple`

### wiki:Propriedades {#wiki-properties}

**Descrição**

Propriedades da wiki

**Definição**

* `[wiki:Properties]`
   * `- wiki:isGlobal (boolean)`
   * `- * (undefined)`

## Fluxo de trabalho {#workflow}

### cq:Workflow {#cq-workflow}

**Descrição**

Representa uma instância de workflow.

**Definição**

* `[cq:Workflow] > nt:base, mix:referenceable`
   * `- modelId (String)`
   * `- modelVersion (String)`
   * `- startTime (Date)`
   * `- endTime (Date)`
   * `- initiator (String)`
   * `- &ast; (undefined)`
   * `- &ast; (undefined) multiple`
   * `- sling:resourceType (String) = "cq/workflow/components/instance" mandatory autocreated`
   * `+ workflowStack (nt:unstructured)`
   * `+ wait (nt:unstructured)`
   * `+ orTab (nt:unstructured)`
   * `+ data (cq:WorkflowData)`
   * `+ history (nt:unstructured)`
   * `+ metaData (nt:unstructured)`
   * `+ workItems (nt:unstructured)`

### cq:WorkItem {#cq-workitem}

**Descrição**

Item de trabalho.

**Definição**

* `[cq:WorkItem]`
   * `- assignee (String)`
   * `- workflowId (String)`
   * `- nodeId (String)`
   * `- startTime (Date)`
   * `- endTime (Date)`
   * `- dueTime (Date)`
   * `- sling:resourceType (String) = "cq/workflow/components/workitem" mandatory autocreated`
   * `+ metaData (nt:unstructured)`

### cq:Payload {#cq-payload}

**Descrição**

Carga útil

**Definição**

* `[cq:Payload]`
   * `- path (Path)`
   * `- uuid (String)`
   * `- jcr:url (String)`
   * `- binary (Binary)`
   * `- javaObject (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`

### cq:WorkflowData {#cq-workflowdata}

**Descrição**

Dados do fluxo de trabalho

**Definição**

* `[cq:WorkflowData]`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ payload (cq:Payload)`
   * `+ metaData (nt:unstructured) copy`

### cq:WorkflowModel {#cq-workflowmodel}

**Descrição**

Autoatribuir configuração de fluxo de trabalho. A configuração segue essa estrutura abaixo:
* `workflows`
   * `+ name1`
      * `- cq:path`
      * `- cq:workflowName`
   * `+ workflows (nt:base)`

**Definição**

* `[cq:WorkflowModel] > nt:base, mix:versionable`
   * `orderable`
   * `- title (String)`
   * `- description (String)`
   * `- sling:resourceType (String) = "cq/workflow/components/model" mandatory autocreated`
   * `+ nodes (nt:unstructured)`
      * `copy`
   * `+ transitions (nt:unstructured)`
      * `copy`
   * `+ metaData (nt:unstructured)`
      * `copy`

### cq:WorkflowNode {#cq-workflownode}

**Descrição**

Nó do fluxo de trabalho

**Definição**

* `[cq:WorkflowNode] orderable`
   * `- title (String)`
   * `- description (String)`
   * `- maxIdleTime (long)`
   * `- type (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ metaData (nt:unstructured)`
      * `copy`
   * `+ timeoutConfiguration (nt:unstructured)`
      * `copy`

### cq:WorkflowTransition {#cq-workflowtransition}

**Descrição**

Transição de fluxo de trabalho

**Definição**

* `[cq:WorkflowTransition] orderable`
   * `- from (String)`
   * `- to (String)`
   * `- rule (String)`
   * `+ metaData (nt:unstructured)`
      * `copy`

### cq:OrTab {#cq-ortab}

**Descrição**

Guia Ou

**Definição**

* `[cq:OrTab]`
   * `- workflowId (String) // not compulsory as this node will already be attached to the workflow node`
   * `- nodeId (String)`

### cq:Wait {#cq-wait}

**Descrição**

Aguardar

**Definição**

* `[cq:Wait]`
   * `- workflowId (String) // not compulsory as this node will be already attached to the workflow node`
   * `- destNodeId (String)`
   * `- fromNodeId (String)`

### cq:WorkflowStack {#cq-workflowstack}

**Descrição**

Pilha de fluxo de trabalho

**Definição**

* `[cq:WorkflowStack]`
   * `- containeeInstanceId (String)`
   * `- parentInstanceId (String)`
   * `- nodeId (String)`

### cq:ProcessStack {#cq-processstack}

**Descrição**

Pilha de processos

**Definição**

* `[cq:ProcessStack]`
   * `- workflowId (String) // not compulsory as this node will be already attached to the workflow node`
   * `- containerWorkflowModelId (String)`
   * `- containerWorkflowNodeId`
   * `- containerWorkflowEndNodeId // still needed (if name already defines that id)`

### cq:WorkflowLauncher {#cq-workflowlauncher}

**Descrição**

Iniciador do fluxo de trabalho

**Definição**

* `[cq:WorkflowLauncher]`
   * `- nodetype (String)`
   * `- glob (String)`
   * `- eventType (Long)`
   * `- description (String)`
   * `- condition (String)`
   * `- workflow (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`
