---
title: Relatório
description: Saiba como trabalhar com relatórios no Adobe Experience Manager (AEM).
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '2782'
ht-degree: 3%

---

# Relatório {#reporting}

Para ajudar você a monitorar e analisar o estado da sua instância, o Adobe Experience Manager (AEM) fornece uma seleção de relatórios padrão, que podem ser configurados para seus requisitos individuais:

* [Relatório do componente](#component-report)
* [Uso do disco](#disk-usage)
* [Verificação de integridade](#health-check)
* [Relatório de atividades de página](#page-activity-report)
* [Relatório de conteúdo gerado pelo usuário](#user-generated-content-report)
* [Relatório do usuário](#user-report)
* [Relatório de instâncias do fluxo de trabalho](#workflow-instance-report)
* [Relatório de fluxo de trabalho](#workflow-report)

>[!NOTE]
>
>Esses relatórios só estão disponíveis na interface clássica. Para obter relatórios e monitoramento do sistema na interface moderna, consulte o [Painel de Operações.](/help/sites-administering/operations-dashboard.md)

Todos os relatórios podem ser acessados no console **Ferramentas**. Selecione **Relatórios** no painel à esquerda e clique duas vezes no relatório necessário no painel à direita para abri-lo para exibição, configuração ou ambos.

Novas instâncias de um relatório também podem ser criadas no console **Ferramentas**. Selecione **Relatórios** no painel esquerdo e, em seguida, **Novo...** na barra de ferramentas. Defina um **Título** e um **Nome**, selecione o tipo de relatório necessário e clique em **Criar**. A nova instância do relatório aparece na lista. Clique duas vezes para abrir, em seguida, arraste um componente do sidekick para que você possa criar a primeira coluna e iniciar a definição do relatório.

>[!NOTE]
>
>Além dos relatórios padrão do AEM que estão disponíveis prontamente, você pode [desenvolver seus próprios (novos) relatórios](/help/sites-developing/dev-reports.md).

## Noções básicas da personalização de relatórios {#the-basics-of-report-customization}

Há vários formatos de relatórios disponíveis. Os relatórios a seguir usam colunas que podem ser personalizadas conforme detalhado nas seções a seguir:

* [Relatório do componente](#component-report)
* [Relatório de atividades de página](#page-activity-report)
* [Relatório de conteúdo gerado pelo usuário](#user-generated-content-report)
* [Relatório do usuário](#user-report)
* [Relatório de instâncias do fluxo de trabalho](#workflow-instance-report)

>[!NOTE]
>
>Os seguintes relatórios têm seu próprio formato e personalização:
>
>
>* A [Verificação de integridade](#health-check) usa campos de seleção para especificar os dados que você deseja relatar.
>* [Uso do disco](#disk-usage) usa links para detalhar a estrutura do repositório.
>* [Fluxo de trabalho](/help/sites-administering/reporting.md#workflow-report) fornece uma visão geral dos fluxos de trabalho em execução na sua instância.
>
>Portanto, os procedimentos a seguir para a configuração da coluna não são apropriados. Consulte as descrições de relatórios individuais para obter seus detalhes.

### Seleção e posicionamento das colunas de dados {#selecting-and-positioning-the-data-columns}

As colunas podem ser adicionadas, reposicionadas ou removidas de qualquer um dos relatórios, seja padrão ou personalizado.

A guia **Components** do sidekick (disponível na página de relatório) lista todas as categorias de dados que podem ser selecionadas como colunas.

Para alterar a seleção de dados:

* para adicionar uma coluna, arraste o componente desejado do sidekick e solte na posição desejada

   * um sinal verde indica quando a posição é válida e um par de setas indica exatamente onde ela é colocada
   * um símbolo vermelho indica quando a posição é inválida

* para mover uma coluna, clique no cabeçalho, mantenha pressionada e arraste para a nova posição
* para remover uma coluna, clique no título da coluna, mantenha a tecla pressionada e arraste para cima na área do cabeçalho do relatório (um símbolo de menos vermelho indica que a posição não é válida). Solte o botão do mouse e a caixa de diálogo Excluir componentes solicitando confirmação de que você realmente deseja excluir a coluna.

### Menu Suspenso de Coluna {#column-drop-down-menu}

Cada coluna no relatório tem um menu suspenso. Isso se torna visível quando o cursor do mouse se move sobre a célula de título da coluna.

Uma ponta de seta é exibida na extremidade direita da célula de título (não confunda com a ponta de seta imediatamente à direita do texto do título que indica o [mecanismo de classificação atual](#sorting-the-data)).

![reportcolumnsort](assets/reportcolumnsort.png)

As opções disponíveis no menu dependem da configuração da coluna (conforme feito durante o desenvolvimento do projeto), as opções inválidas ficam esmaecidas (esmaecidas).

### Classificação dos dados {#sorting-the-data}

Os dados podem ser classificados de acordo com uma coluna específica por:

* clicar no cabeçalho de coluna apropriado; a classificação alterna entre crescente e decrescente, indicado por um cabeçalho de seta imediatamente ao lado do texto do título
* use o menu suspenso da [coluna](#column-drop-down-menu) para selecionar especificamente **Classificar em Ordem Crescente** ou **Classificar em Ordem Decrescente**; novamente, isso é indicado por uma seta imediatamente ao lado do texto do título

### Gráfico de Grupos e Dados Atuais {#groups-and-the-current-data-chart}

Nas colunas apropriadas, você pode selecionar **Agrupar por esta coluna** no menu suspenso da [coluna](#column-drop-down-menu). Isso agrupa os dados de acordo com cada valor distinto nessa coluna. É possível selecionar mais de uma coluna a ser agrupada. A opção fica esmaecida (esmaecida) quando os dados na coluna são inadequados. Ou seja, cada entrada é distinta e única, de modo que nenhum grupo pode ser formado. Por exemplo, a coluna ID de usuário do relatório do usuário.

Depois que pelo menos uma coluna é agrupada, um gráfico de pizza de **Dados atuais** é gerado, com base neste agrupamento. Se várias colunas forem agrupadas, isso será indicado no gráfico.

![reportuser](assets/reportuser.png)

Mover o cursor sobre o gráfico de pizza mostra o valor agregado do segmento apropriado. Usa a agregação definida no momento para a coluna; por exemplo, count, minimum, average, entre outros.

### Filtros e agregações {#filters-and-aggregates}

Nas colunas apropriadas, você também pode definir **Configurações de Filtro** e/ou **Agregações** no menu suspenso da [coluna](#column-drop-down-menu).

#### Filtros {#filters}

As Configurações de filtro permitem que você especifique os critérios para as entradas a serem exibidas. Os operadores disponíveis são:

* `contains`
* `equals`

![reportfilter](assets/reportfilter.png)

Para definir um filtro:

1. Selecione o operador desejado na lista suspensa.
1. Digite o texto a ser filtrado.
1. Clique em **Aplicar**.

Para desativar o filtro:

1. Remova o texto do filtro.
1. Clique em **Aplicar**.

#### Agregados {#aggregates}

Você também pode selecionar um método de agregação (que pode variar dependendo da coluna selecionada):

![reportaggregate](assets/reportaggregate.png)

### Propriedades da coluna {#column-properties}

Esta opção só está disponível quando a [coluna Genérica](#generic-column) foi usada no [Relatório de Usuário](#user-report).

### Dados históricos {#historic-data}

Um gráfico da mudança em seus dados ao longo do tempo pode ser visto em **Dados históricos**. Isso é derivado de instantâneos tirados em intervalos regulares.

Os dados são:

* Coletada por, se disponível, a primeira coluna classificada; caso contrário, a primeira coluna (não agrupada)
* Agrupado pela coluna apropriada

O relatório pode ser gerado:

1. Defina **Agrupamento** na coluna necessária.
1. **Edite** a configuração para poder definir instantâneos por hora ou por dia.
1. **Concluir...** a definição para iniciar a coleção de instantâneos.

   O botão deslizante vermelho/verde na parte superior esquerda indica quando os instantâneos estão sendo coletados.

O gráfico resultante é mostrado na parte inferior direita:

![reporttrends](assets/reporttrends.png)

Quando a coleta de dados começar, é possível selecionar:

* **Período**

  Você pode selecionar datas de e até para os dados do relatório a serem mostrados.

* **Intervalo**

  Mês, Semana, Dia, Hora podem ser selecionados para a escala e agregação do relatório.

  Por exemplo, se os instantâneos diários estiverem disponíveis para fevereiro de 2011:

   * Se o intervalo estiver definido como `Day`, cada instantâneo será mostrado como um valor único no gráfico.
   * Se o intervalo for definido como `Month`, todos os instantâneos de fevereiro serão agregados em um único valor (exibido como um único &quot;ponto&quot; no gráfico).

Selecione seus requisitos e clique em **Ir** para aplicá-los ao relatório. Para atualizar a exibição depois da criação de mais instantâneos, clique novamente em **Ir**.

![chlimage_1-43](assets/chlimage_1-43.png)

Quando os instantâneos estão sendo coletados, você pode:

* Use **Concluir...** novamente para reinicializar a coleção.

  **Término** &quot;congela&quot; a estrutura do relatório (ou seja, as colunas atribuídas ao relatório e que são agrupadas, classificadas, filtradas, etc.) e começa a tirar instantâneos.

* Abra a caixa de diálogo **Editar** para poder selecionar **Nenhum instantâneo de dados** para encerrar a coleção até que seja necessário.

  **Editar** alterna somente a captura de instantâneos. Se tirar instantâneos estiver ativado novamente, ele usa o estado do relatório quando foi concluído pela última vez para tirar mais instantâneos.

>[!NOTE]
>
>Os instantâneos são armazenados em `/var/reports/...`, onde o restante do caminho espelha o caminho do respectivo relatório e a ID criada quando o relatório foi concluído.
>
>
>Os snapshots antigos podem ser removidos manualmente, se você tiver certeza de que não precisa mais dessas instâncias.

>[!NOTE]
>
>Os relatórios pré-configurados não exigem alto desempenho, mas ainda é recomendável usar snapshots diários em um ambiente de produção. Se possível, execute esses instantâneos diários em um horário do dia quando não houver muita atividade no site. Isso pode ser definido com o parâmetro `Daily snapshots (repconf.hourofday)` para **Configuração de relatório do Day CQ**. Consulte [Configuração OSGI](/help/sites-deploying/configuring-osgi.md) para obter mais detalhes sobre como configurar isso.

#### Limites de exibição {#display-limits}

O relatório de dados históricos também pode mudar levemente de aparência devido a limites que podem ser definidos, de acordo com o número de resultados do período selecionado.

Cada linha horizontal é conhecida como uma série (e corresponde a uma entrada na legenda do gráfico), cada coluna vertical de pontos representa os instantâneos agregados.

![chlimage_1-44](assets/chlimage_1-44.png)

Para manter o gráfico limpo por longos períodos de tempo, há limites que podem ser definidos. Para os relatórios padrão, são:

* série horizontal - o padrão e o máximo do sistema são `9`

* instantâneos agregados verticais - o padrão é `35` (por série horizontal)

Assim, quando os limites (apropriados) são excedidos, o:

* os pontos não são exibidos
* a legenda do gráfico de dados históricos pode mostrar um número de entradas diferente daquele do gráfico de dados atual

![chlimage_1-45](assets/chlimage_1-45.png)

Relatórios personalizados também podem mostrar o valor **Total** para todas as séries. Isso é mostrado como uma série (linha horizontal e entrada na legenda).

>[!NOTE]
>
>Para relatórios personalizados, os limites podem ser definidos de maneiras diferentes.

### Editar (Relatório) {#edit-report}

O botão **Editar** abre a Caixa de Diálogo **Editar Relatório**.

Este é um local onde o período para coletar instantâneos de [Dados históricos](#historic-data) é definido, mas várias outras configurações também podem ser definidas:

![editarrelatório](assets/reportedit.png)

* **Título**

  Você pode definir seu próprio título.

* **Descrição**

  Você pode definir sua própria descrição.

* **Caminho raiz** (*ativo somente para determinados relatórios*)

  Use essa opção para limitar o relatório a uma (sub) seção do repositório.

* **Processamento de Relatório**

   * **atualizar dados automaticamente**

     Os dados do relatório são atualizados toda vez que você atualiza a definição do relatório.

   * **atualizar dados manualmente**

     Essa opção pode ser usada para evitar atrasos causados por operações automáticas de atualização quando há um grande volume de dados.

     Selecionar essa opção indica que os dados do relatório devem ser atualizados manualmente quando qualquer aspecto da configuração do relatório for alterado. Também significa que, quando você altera qualquer aspecto da configuração, a tabela de relatório fica em branco.

     Quando selecionado, o botão **[Carregar dados](#load-data)** é exibido (ao lado de **Editar** no relatório). **Carregar dados** carrega os dados e atualiza os dados de relatório mostrados.

* **Instantâneos**
Você pode definir a frequência com que os instantâneos devem ser criados, diariamente, a cada hora ou não.

### Carregar dados {#load-data}

O botão **Carregar dados** só estará visível quando **atualizar dados manualmente** for selecionado em **[Editar](#edit-report)**.

![chlimage_1-46](assets/chlimage_1-46.png)

Clicar em **Carregar dados** recarregará os dados e atualizará o relatório que está sendo mostrado.

Selecionar para atualizar dados manualmente significa que:

1. Quando você altera a configuração do relatório, a tabela de dados do relatório fica em branco.

   Por exemplo, se você alterar o mecanismo de classificação de uma coluna, os dados não serão exibidos.

1. Se quiser que os dados do relatório sejam exibidos novamente, clique em **Carregar dados** para recarregar os dados.

### Concluir (relatório) {#finish-report}

Quando você **Concluir** o relatório:

* A definição de relatório *a partir desse momento* é usada para tirar instantâneos. Depois disso, você pode continuar trabalhando em uma definição de relatório porque ela é separada dos instantâneos.
* Todos os snapshots existentes serão removidos.
* Novos instantâneos são coletados para os [dados históricos](#historic-data).

Com essa caixa de diálogo, você pode definir ou atualizar seu próprio título e descrição para o relatório resultante.

![reportfinish](assets/reportfinish.png)

## Tipos de relatório {#report-types}

### Relatório do componente {#component-report}

O relatório de componentes fornece informações sobre como seu site usa os componentes.

[Colunas de informações](#selecting-and-positioning-the-data-columns) sobre:

* Autor
* Caminho do componente
* Tipo de componente
* Última modificação
* Página

Isso significa que você pode ver o seguinte:

* Quais componentes são usados e onde são usados.

  Útil, por exemplo, ao testar.

* Como as instâncias de um componente específico são distribuídas.

  Isso pode ser interessante se páginas específicas (ou seja, &quot;páginas pesadas&quot;) estiverem com problemas de desempenho.

* Identificar partes do site com alterações frequentes/menos frequentes.
* Veja como o conteúdo da página se desenvolve ao longo do tempo.

Todos os componentes estão incluídos, são padrão do produto e específicos do projeto. Usando a caixa de diálogo **Editar**, o usuário também pode definir um **Caminho raiz** que defina o ponto inicial do relatório. Todos os componentes dessa raiz serão considerados para o relatório.

![reportcomponent](assets/reportcomponent.png) ![reportcompentall](assets/reportcompentall.png)

### Uso do disco {#disk-usage}

O relatório de uso do disco mostra informações sobre os dados armazenados no repositório.

O relatório começa na raiz ( / ) do repositório; clicando em uma ramificação específica, é possível detalhar dentro do repositório (o caminho atual é refletido no título do relatório).

![reportdiskusage](assets/reportdiskusage.png)

### Verificação de integridade {#health-check}

Este relatório analisa o log de solicitação atual:

`<cq-installation-dir>/crx-quickstart/logs/request.log`

Para ajudar a identificar as solicitações mais caras em um determinado período.

Para gerar o relatório, você pode especificar o seguinte:

* **Período (horas)**

  O número de horas (passadas) a serem analisadas.

  Padrão: `24`

* **máx. Resultados**

  Número máximo de linhas de saída.

  Padrão: `50`

* **máx. Solicitações**

  Número máximo de solicitações a serem analisadas.

  Padrão: `-1` (todos)

* **Endereço de email**

  Enviar resultados para um endereço de email.

  Opcional; Padrão: em branco

* **Executar diariamente às (hh:mm)**

  Especifique um horário para que o relatório seja executado automaticamente diariamente.

  Opcional; Padrão: em branco

![reportthealth](assets/reporthealth.png)

### Relatório de atividades de página {#page-activity-report}

O relatório de atividade da página lista as páginas e as ações nelas feitas.

[Colunas de informações](#selecting-and-positioning-the-data-columns) sobre:

* Página
* Hora
* Tipo
* Usuário

Isso significa que é possível monitorar:

* As modificações mais recentes.
* Autores trabalhando em páginas específicas.
* Páginas que não foram modificadas recentemente, portanto, podem estar precisando de ação.
* Páginas alteradas com mais/menos frequência.
* Usuários mais/menos ativos.

O relatório de atividade de página obtém todas as informações do log de auditoria. Por padrão, o caminho raiz está configurado para o log de auditoria em `/var/audit/com.day.cq.wcm.core.page`.

![reportpageactivity](assets/reportpageactivity.png)

### Relatório de conteúdo gerado pelo usuário {#user-generated-content-report}

Este relatório fornece informações sobre conteúdo gerado pelo usuário; seja comentários, classificações ou fóruns.

[Colunas de informações](#selecting-and-positioning-the-data-columns) sobre:

* Data
* Endereço IP
* Página
* Referenciador
* Tipo
* Identificador do usuário

Permite:

* Veja quais páginas estão recebendo mais comentários.
* Obtenha uma visão geral de todos os comentários que os visitantes específicos do site estão deixando, talvez os problemas estejam relacionados.
* Avalie se o novo conteúdo está provocando comentários, monitorando quando os comentários estão sendo feitos em uma página.

![reportusercontent](assets/reportusercontent.png)

### Relatório do usuário {#user-report}

Este relatório fornece informações sobre todos os usuários que registraram uma conta e/ou perfil; isso pode incluir autores em sua organização e visitantes externos.

[Colunas de informações](#selecting-and-positioning-the-data-columns) (quando disponíveis) sobre:

* Idade
* País
* Domínio
* E-mail
* Nome da família
* Sexo
* [Genérico](#generic-column)
* Nome
* Informações
* Interesse
* Idioma
* Hashcode NTLM
* ID de usuário

Permite:

* Veja a distribuição demográfica de seus usuários.
* Relatar campos personalizados adicionados aos perfis.

![reportusercanned](assets/reportusercanned.png)

#### Coluna genérica {#generic-column}

A coluna **Genérica** está disponível no Relatório de Usuário para que você possa acessar informações personalizadas, geralmente de [perfis de usuário](/help/sites-administering/identity-management.md#profiles-and-user-accounts); por exemplo, [Cor Favorita, conforme detalhado em Adição de Campos à Definição de Perfil](/help/sites-administering/identity-management.md#adding-fields-to-the-profile-definition).

A caixa de diálogo Coluna genérica é aberta quando você realiza uma das ações a seguir:

* Arraste o componente Genérico do sidekick para o relatório.
* Selecione as Propriedades da Coluna para uma coluna Genérica existente.

![reportusrgenericMalcolm](assets/reportusrgenericcolm.png)

Na guia **Definições**, é possível definir:

* **Título**

  Seu próprio título para a coluna genérica.

* **Propriedade**

  O nome da propriedade conforme armazenado no repositório, geralmente no perfil do usuário.

* **Caminho**

  Normalmente, a propriedade é retirada de `profile`.

* **Tipo**

  Selecione o tipo de campo de `String`, `Number`, `Integer`, `Date`.

* **Agregação Padrão**

  Isso define a agregação usada por padrão se a coluna for desagrupada em um relatório com pelo menos uma coluna agrupada. Selecione a agregação necessária de `Count`, `Minimum`, `Average`, `Maximum`, `Sum`.

  Por exemplo, *Count* para um campo `String` significa que o número de valores `String` distintos é exibido para a coluna no estado agregado.

Na guia **Extended**, você também pode definir as agregações e os filtros disponíveis:

![reportusrgenericcolmextented](assets/reportusrgenericcolmextented.png)

### Relatório de instâncias do fluxo de trabalho {#workflow-instance-report}

Isso fornece uma visão geral concisa, fornecendo informações sobre as instâncias individuais de workflows, em execução e concluídos.

[Colunas de informações](#selecting-and-positioning-the-data-columns) sobre:

* Concluído
* Duração
* Iniciador
* Modelo
* Carga útil
* Iniciado
* Status

Isso significa que você pode:

* Monitore a duração média dos workflows; se isso ocorrer regularmente, pode destacar problemas com o workflow.

![reportworkflowintance](assets/reportworkflowintance.png)

### Relatório de fluxo de trabalho {#workflow-report}

Isso fornece estatísticas importantes sobre os workflows em execução na sua instância.

![reportworkflow](assets/reportworkflow.png)

## Uso de relatórios em um ambiente de publicação {#using-reports-in-a-publish-environment}

Depois de configurar os relatórios de acordo com seus requisitos específicos, você pode ativá-los para transferir a configuração para o ambiente de publicação.

>[!CAUTION]
>
>Se você quiser **dados históricos** do ambiente de Publicação, **Conclua** o relatório no ambiente de Autor antes de ativar a página.

O relatório apropriado é então acessível em

`/etc/reports`

Por exemplo, o relatório de Conteúdo gerado pelo usuário pode ser encontrado em:

`http://localhost:4503/etc/reports/ugcreport.html`

Isso agora relata os dados coletados do ambiente de publicação.

Como nenhuma configuração de relatório é permitida no ambiente de Publicação, os botões **Editar** e **Concluir** não estão disponíveis. No entanto, você pode selecionar o **Período** e o **Intervalo** para os relatórios de **Dados históricos** se os instantâneos estiverem sendo coletados.

![reportsucgpublish](assets/reportsucgpublish.png)

>[!CAUTION]
>
>O acesso a esses relatórios pode ser um problema de segurança; portanto, a Adobe recomenda que você configure o Dispatcher para que `/etc/reports` não fique disponível para visitantes externos. Consulte a [Lista de Verificação de Segurança](security-checklist.md) para obter mais detalhes.

## Permissões necessárias para executar relatórios {#permissions-needed-for-running-reports}

As permissões necessárias dependem da ação:

* Os dados do relatório são coletados usando os privilégios do usuário atual.
* Os dados históricos são coletados usando os privilégios do usuário que concluiu o relatório.

Em uma instalação padrão do AEM, as seguintes permissões são predefinidas para os relatórios:

* **Relatório de usuário**

  `user administrators` - ler e gravar

* **Relatório de atividades da página**

  `contributors` - ler e gravar

* **Relatório de componentes**

  `contributors` - ler e gravar

* **Relatório de conteúdo gerado pelo usuário**

  `contributors` - ler e gravar

* **Relatório de instâncias do fluxo de trabalho**

  `workflow-users` - ler e gravar

Todos os membros do grupo `administrators` têm os direitos necessários para criar relatórios.
