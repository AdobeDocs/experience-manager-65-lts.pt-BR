---
title: Utilização de gráficos em Comunicações interativas
description: Ao usar gráficos em uma comunicação interativa, é possível condensar grandes quantidades de informações em um formato visual fácil de analisar
content-type: reference
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '2621'
ht-degree: 1%

---

# Utilização de gráficos em Comunicações interativas{#using-charts-in-interactive-communications}

Um gráfico é uma representação visual de dados. Ele condensa grandes quantidades de informações em um formato visual fácil de entender, permitindo que os recipients da Comunicação interativa visualizem, interpretem e analisem melhor dados complexos.

Ao criar uma Comunicação interativa, você pode adicionar gráficos para representar visualmente dados bidimensionais do modelo de dados de formulário da Comunicação interativa. O componente de Gráfico permite adicionar e configurar os seguintes tipos de gráficos: Pizza, Coluna, Rosca, Barra, Linha, Linha e Ponto, Ponto, Área e Quadrante.

## Adicionar e configurar o gráfico em uma comunicação interativa {#add-and-configure-chart-in-an-interactive-communication}

Execute as seguintes etapas para adicionar e configurar um gráfico em uma comunicação interativa:

1. Selecione **Componentes** no sidekick da Comunicação interativa.
1. Arraste e solte o componente **Gráfico** para um dos seguintes componentes:

   * Canal de impressão: área de destino ou campo de imagem
   * Canal da Web: painel ou área de direcionamento

1. Selecione o componente de gráfico no editor de Comunicação Interativa e selecione **[!UICONTROL Configurar (]** ![configure_icon](assets/configure_icon.png)) na barra de ferramentas Componente.

   As Propriedades do Gráfico são exibidas no painel esquerdo.

   ![Propriedades básicas de um gráfico de tipo de linha no canal de impressão](assets/chart_properties_print_new.png)

   Propriedades básicas de um gráfico de tipo de linha no canal de impressão

   ![Propriedades básicas de um gráfico de tipo de linha no canal da Web](assets/chart_properties_web_new.png)

   Propriedades básicas de um gráfico de tipo de linha no canal da Web

1. Configure as [propriedades do gráfico](../../forms/using/chart-component-interactive-communications.md#configure-chart-properties) com base no tipo de canal.
1. (Somente canal de impressão) Em **[!UICONTROL Configurações do agente]**, especifique se é obrigatório que o agente use este gráfico. Se a opção **[!UICONTROL t É Obrigatório para o Agente Usar Este Gráfico]** não estiver selecionada, o agente poderá selecionar o ícone de olho para o gráfico na guia **[!UICONTROL Conteúdo]** da Interface do Usuário do Agente para mostrar ou ocultar o gráfico.

   ![propriedades_do_gráfico](assets/chart_agentproperties.png)

1. Selecione ![done_icon](assets/done_icon.png) para salvar as propriedades do gráfico.

   Selecione **[!UICONTROL Visualizar]** para exibir a aparência e os dados associados ao gráfico. Selecione **[!UICONTROL Editar]** para reconfigurar as propriedades do gráfico.

## Configurar propriedades do gráfico {#configure-chart-properties}

Configure as seguintes propriedades ao criar gráficos para canais de impressão e da Web:

<table>
 <tbody>
  <tr>
   <td>Texto</td>
   <td>Descrição</td>
   <td>Tipo de Canal</td>
  </tr>
  <tr>
   <td>Nome</td>
   <td>Identificador do elemento do gráfico. O nome do gráfico especificado neste campo não está visível no gráfico. É usado ao fazer referência ao elemento de outros componentes, scripts e expressões SOM.</td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Tipo de gráfico</td>
   <td>Tipo de gráfico que você deseja gerar. As opções disponíveis são Pizza, Coluna, Rosca, Barra, Linha, Linha e Ponto, Ponto e Área.</td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Séries &gt; Várias séries</td>
   <td>Selecione para adicionar várias séries para os itens de coleção de modelo de dados de formulário representados no eixo X e no eixo Y.</td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Série &gt; Objeto de modelo de dados</td>
   <td>Nome do item de coleção de modelo de dados de formulário para adicionar várias séries ao gráfico.<br /> Escolha uma propriedade de objeto de modelo de dados de formulário pai para as propriedades representadas no eixo X e no eixo Y para formar uma série significativa. O objeto de modelo de dados vinculado deve ser do tipo Number, String ou Date.</td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Mostrar empilhado</td>
   <td>Opte por empilhar os valores de cada séria, um sobre o outro.</td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Eixo X &gt; Título</td>
   <td>Título para o eixo X.</td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Eixo X &gt; Objeto do modelo de dados</td>
   <td><p>Nome do item de coleção de modelo de dados de formulário a ser representado no eixo X.</p> <p>Escolha duas propriedades de tipo de coleção/matriz do mesmo objeto de modelo de dados pai que sejam significativas em relação umas às outras para plotar no eixo X e Y de um gráfico. O objeto de modelo de dados vinculado deve ser do tipo Number, String ou Date.</p> </td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Eixo Y &gt; Título</td>
   <td>Título para o eixo Y. </td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Eixo Y &gt; Objeto do modelo de dados</td>
   <td><p>Item de coleção de modelo de dados de formulário a ser representado no eixo Y. No canal de impressão, o objeto de modelo de dados para o eixo Y deve ser do tipo Number.</p> <p>Escolha duas propriedades de tipo de coleção/matriz do mesmo objeto de modelo de dados pai que sejam significativas em relação umas às outras para plotar no eixo X e Y de um gráfico. </p> </td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Eixo Y &gt; Função</td>
   <td>Função estatística/personalizada para usar para calcular os valores no eixo y.</td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Ocultar objeto</td>
   <td>Selecione para ocultar o gráfico na saída final.</td>
   <td>Impressão e Web</td>
  </tr>
  <tr>
   <td>Título</td>
   <td>Título do gráfico. </td>
   <td>Imprimir</td>
  </tr>
  <tr>
   <td>Altura</td>
   <td>Altura do gráfico em pixels.</td>
   <td>Imprimir</td>
  </tr>
  <tr>
   <td>Largura</td>
   <td>Largura do gráfico em pixels. É possível controlar a largura do gráfico no canal da Web usando a camada de estilo ou aplicando um tema.</td>
   <td>Imprimir</td>
  </tr>
  <tr>
   <td>Quebra de página obrigatória antes de</td>
   <td>Selecione para adicionar uma quebra de página obrigatória antes do gráfico e colocar o gráfico na parte superior de uma nova página. </td>
   <td>Imprimir</td>
  </tr>
  <tr>
   <td>Quebra de página obrigatória depois de</td>
   <td>Selecione para adicionar uma quebra de página obrigatória após o gráfico e colocar o conteúdo após o gráfico na parte superior de uma nova página. </td>
   <td>Imprimir</td>
  </tr>
  <tr>
   <td>Recuo</td>
   <td>Recuo do gráfico à esquerda da página. </td>
   <td>Imprimir</td>
  </tr>
  <tr>
   <td>Dica</td>
   <td><p>Formato no qual a dica de ferramenta aparece ao passar o mouse em um ponto de dados no gráfico no canal da Web. O valor padrão é ${x}(${y}). Dependendo do tipo de gráfico, quando você aponta o mouse em um ponto, barra ou fatia no gráfico, as variáveis ${x} e ${y} são substituídas dinamicamente pelos valores correspondentes no eixo X e no eixo Y e exibidas na dica de ferramenta.</p> <p>Para desabilitar a dica de ferramenta, deixe a <span class="uicontrol">dica</code> campo em branco. Essa opção não é aplicável para gráficos de linha e de área. Por exemplo, consulte <a href="#chartoutputprintweb">Exemplo 1: saída de gráfico em impressão e Web</a>.</p> </td>
   <td>Web</td>
  </tr>
  <tr>
   <td>Configurações específicas do gráfico</td>
   <td><p>Além das configurações comuns, as seguintes configurações específicas do gráfico estão disponíveis:</p>
    <ul>
     <li><strong>Mostrar legenda: </strong>Mostra uma legenda para o gráfico de pizza ou rosca quando habilitado.</li>
     <li><strong>Posição da legenda: </strong>Especifica a posição da legenda em relação ao gráfico. As opções disponíveis são Direita, Esquerda, Superior e Inferior. Use a legenda do lado direito no canal de impressão.</li>
     <li><strong>Raio interno</strong>: Disponível para gráficos de rosca para especificar o raio (em pixels) do círculo interno no gráfico.</li>
     <li><strong>Cor da linha</strong>: Disponível para gráficos de Linha, Linha e Ponto e Área para especificar a cor da linha no gráfico.</li>
     <li><strong>Cor do ponto</strong>: disponível para gráficos de Ponto e Linha e Ponto para especificar a cor dos pontos no gráfico.<br /> </li>
     <li><strong>Cor da área</strong>: disponível para gráficos de área para especificar a cor da área abaixo da linha do gráfico.</li>
     <li><strong>Ponto de Referência &gt; Tipo de Associação: </strong>Disponível para gráficos de Quadrante para<strong> </strong>especificar o tipo de associação para o ponto de referência. Use texto estático ou a propriedade do objeto de modelo de dados para definir o valor do ponto de referência.</li>
     <li><strong>Ponto de Referência &gt; Eixo X: </strong>Disponível para gráficos do Quadrante se você selecionar <span class="uicontrol">Estático</code> na lista suspensa Tipo de vinculação para especificar o valor do eixo X para o ponto de referência.</li>
     <li><strong>Ponto de Referência &gt; Eixo Y: </strong>Disponível para gráficos do Quadrante se você selecionar <span class="uicontrol">Estático</code> na lista suspensa Tipo de vinculação para especificar o valor do eixo Y para o ponto de referência.</li>
     <li><strong>Ponto de Referência &gt; Objeto de Modelo de Dados para Série: </strong>Disponível para vários gráficos de Quadrante de série se você selecionar <span class="uicontrol">Objeto de Modelo de Dados</code> na lista suspensa Tipo de vínculo. Defina a propriedade do objeto de modelo de dados de formulário para identificar a série do ponto de referência. </li>
     <li><strong>Ponto de Referência &gt; Valor do Objeto de Modelo de Dados para Série: </strong>Disponível para vários gráficos de Quadrante de série se você selecionar <span class="uicontrol">Objeto de Modelo de Dados</code> na lista suspensa Tipo de vínculo. Use a propriedade do objeto de modelo de dados de formulário para a série e o valor definido neste campo para identificar a série do ponto de referência.</li>
     <li><strong>Ponto de Referência &gt; Objeto de Modelo de Dados do Ponto de Referência: </strong>Disponível para gráficos do Quadrante se você selecionar <span class="uicontrol">Objeto de Modelo de Dados</code> na lista suspensa Tipo de vínculo. Defina uma propriedade do objeto de modelo de dados de formulário que seja semelhante às propriedades representadas no eixo X e no eixo Y. Além disso, para várias séries, defina uma propriedade do objeto de modelo de dados que seja uma entidade secundária da propriedade do objeto de modelo de dados definida para a série.</li>
     <li><strong>Ponto de Referência &gt; Valor do Objeto de Modelo de Dados para o Ponto de Referência: </strong>Disponível para gráficos do Quadrante se você selecionar <span class="uicontrol">Objeto de Modelo de Dados</code> na lista suspensa Tipo de vínculo. Use a propriedade do objeto de modelo de dados de formulário para o ponto de referência e o valor definido neste campo para identificar o ponto de referência do gráfico.<br /> <strong>Rótulos do quadrante &gt; Parte superior esquerda:</strong> Disponível para gráficos do quadrante para especificar o nome do quadrante superior esquerdo.</li>
     <li><strong>Rótulos do quadrante &gt; Parte superior direita:</strong> Disponível para gráficos do quadrante para especificar o nome do quadrante Parte superior direita.</li>
     <li><strong>Rótulos do quadrante &gt; Parte Inferior Direita: </strong>Disponível para gráficos do quadrante para especificar o nome do quadrante Inferior Direito.</li>
     <li><strong>Rótulos do quadrante &gt; Parte Inferior Esquerda: </strong>Disponível para gráficos do quadrante para especificar o nome do quadrante Inferior Esquerdo.</li>
    </ul> </td>
   <td>Impressão e Web</td>
  </tr>
 </tbody>
</table>

## Usar funções no gráfico {#use-functions-in-chart}

Você pode configurar um gráfico para usar funções estatísticas para calcular valores a partir dos dados de origem para plotar no gráfico. Ao aplicar funções em um gráfico, é possível plotar dados que não são fornecidos diretamente pelo modelo de dados de formulário.

![Funções em gráficos](assets/functions_charts_new.png)

Embora o componente de Gráfico venha com algumas funções integradas, você pode gravar [funções personalizadas](#customfunctionsweb) e disponibilizá-las para uso na configuração de gráfico no canal da Web.

As seguintes funções estão disponíveis por padrão com o componente de Gráfico:

**Média (Média)** Retorna a média dos valores no eixo X ou Y de um determinado valor no outro eixo.

**Sum** Retorna a soma de todos os valores no eixo X ou Y de um determinado valor no outro eixo.

**Máximo** Retorna o máximo dos valores no eixo X ou Y para um determinado valor no outro eixo.

**Frequência** Retorna o número de valores no eixo X ou Y para um determinado valor no outro eixo.

**Intervalo** Retorna a diferença entre o máximo e o mínimo dos valores nos eixos X ou Y de um determinado valor no outro eixo.

**Mediana** Retorna o valor que separa valores mais altos e mais baixos na metade no eixo X ou Y para um determinado valor no outro eixo.

**Mínimo** Retorna o mínimo dos valores no eixo X ou Y para um determinado valor no outro eixo.

**Mode** Retorna o valor com mais ocorrências no eixo X ou Y para um determinado valor no outro eixo.

Para obter mais informações, consulte [Exemplo 2: Aplicação das funções Sum e Frequency em um gráfico de linhas](#applicationsumfrequency).

### Funções personalizadas no canal da Web {#customfunctionsweb}

Além de usar as funções padrão em gráficos, você pode escrever funções personalizadas no JavaScript™ e disponibilizá-las na lista de funções no componente Gráfico para canal da Web.

Uma função assume uma matriz ou valores e um nome de categoria como entradas e retorna um valor. Por exemplo:

```javascript
Multiply(valueArray, category) {
 var val = 1;
 _.each(valueArray, function(value) {
 val = val * value;
 });
 return val;
}
```

Depois de escrever uma função personalizada, faça o seguinte para disponibilizá-la para uso na configuração do gráfico:

1. Adicione a função personalizada na biblioteca do cliente associada à Comunicação interativa relevante. Para obter mais informações, consulte [Configurando a ação Enviar](/help/forms/using/configuring-submit-actions.md) e [Usando Bibliotecas do Lado do Cliente](/help/sites-developing/clientlibs.md).

1. Para exibir a função personalizada na lista suspensa Função, no CRXDe Lite, crie um nó `nt:unstructured` na pasta de aplicativos com as seguintes propriedades:

   * Adicionar propriedade `guideComponentType` com valor como `fd/af/reducer`. (obrigatório)

   * Adicione a propriedade `value` a um nome totalmente qualificado da função JavaScript™ personalizada. (obrigatório) e defina seu valor como o nome da função personalizada, como Multiplicar.
   * Adicione a propriedade `jcr:description` com o valor que você deseja exibir como o nome da função personalizada que aparece no menu suspenso Função. Por exemplo, **Multiplicar**.

   * Adicione a propriedade `qtip` com um valor que será uma breve descrição da função personalizada. Ela aparece como uma dica de ferramenta ao passar o cursor sobre o nome da função na lista suspensa **Função**.

1. Clique em **Salvar tudo** para salvar a configuração.

A função agora está disponível para uso no gráfico.

## Exemplo 1: saída de gráfico em impressão e Web {#chartoutputprintweb}

Na guia Básico, defina o tipo de gráfico, as propriedades do modelo de dados do formulário de origem que contêm dados, os rótulos a serem plotados no eixo X e no eixo Y do gráfico e, opcionalmente, a função estatística para calcular os valores para plotagem no gráfico.

Vamos entender em detalhes sobre o mínimo necessário de informações em propriedades básicas, com a ajuda de uma instrução de cartão gerada usando uma Comunicação interativa. Considere que você deseja gerar um gráfico para descrever a quantia de despesas diferentes no demonstrativo. Você deseja usar diferentes tipos de gráficos para impressão e saída da Web da Comunicação Interativa.

### Gráfico de colunas para impressão {#columnchartprint}

Para fazer isso, especifique as seguintes propriedades:

* **[!UICONTROL Nome]** - Especifique o nome do gráfico.
* **[!UICONTROL Tipo de Gráfico]** - Selecione **Coluna** na lista suspensa.
* **[!UICONTROL Título]** - Especifique o Tipo de Despesa para o eixo X e o Valor da Transação para o eixo Y.
* **[!UICONTROL Objetos do Modelo de Dados]** - Selecione as propriedades do objeto de modelo de dados para criar associações de dados para o eixo X (Tipo de Despesa) e o eixo Y (Valor da Transação).

![Gráfico de colunas no canal de impressão de uma Comunicação Interativa](assets/sample_chart_print_column_new.png)

Gráfico de colunas no canal de impressão de uma comunicação interativa

### Gráfico de rosca para Web {#donutchartweb}

Para fazer isso, especifique as seguintes propriedades:

* **[!UICONTROL Nome]** - Especifique o nome do gráfico.
* **[!UICONTROL Tipo de Gráfico]** - Selecione **[!UICONTROL Rosca]** na lista suspensa.
* **[!UICONTROL Objetos do Modelo de Dados]** - Selecione as propriedades do objeto de modelo de dados para criar associações de dados para o eixo X (Tipo de Despesa) e o eixo Y (Valor da Transação).
* **[!UICONTROL Raio Interno]** - Especifique o valor do Raio Interno como 150 para especificar o raio (em pixels) do círculo interno no gráfico.
* **[!UICONTROL Dica de ferramenta]** - Use o formato padrão ${x}(${y}) para exibir a dica de ferramenta. A dica de ferramenta é exibida como: Tipo de Despesa (Valor da Transação). Exemplo: Débito para Bitcoin(10000).

![Gráfico de rosca no canal Web de uma Comunicação Interativa](assets/sample_chart_web_new.png)

Gráfico de rosca no canal da Web de uma comunicação interativa

## Exemplo 2: Aplicação das funções Soma e Frequência em um gráfico de linhas {#applicationsumfrequency}

Ao aplicar funções em um gráfico, é possível plotar dados que não são fornecidos diretamente pelo modelo de dados de formulário. Neste exemplo, usamos um exemplo de demonstrativo de cartão de crédito para entender como as funções Soma e Frequência podem ser aplicadas ao gráfico.

![Gráfico de linhas sem uma função com duas transações &quot;Débito para AirBnB&quot;](assets/line_chart_web_new.png)

Gráfico de linhas sem uma função com duas transações &quot;Débito para AirBnB&quot;

### Função Sum {#sum-function}

Você pode aplicar a função sum para adicionar valores de várias instâncias da mesma propriedade de dados e mostrá-la apenas uma vez. Por exemplo, no gráfico a seguir, a função Sum é aplicada no eixo Y para somar o valor dos dois Débitos para transações AirBnB (2050 e 1050) e mostrar apenas uma transação (3100).

A função Sum pode tornar o gráfico mais útil quando você deseja agrupar e exibir a soma de muitas instâncias da mesma propriedade de dados.

![Soma do gráfico de linhas](assets/line_chart_web_sum_new.png)

### Função de frequência {#frequency-function}

A função Frequency retorna o número de valores do eixo Y para um determinado valor no outro eixo. Com a aplicação da função Frequência no eixo Y (Quantia da Transação), o gráfico mostra que houve duas ocorrências de Débito para transações AirBnB e uma ocorrência do resto dos tipos de transações.

![Frequência do gráfico de linha](assets/line_chart_web_functions_frequency_new.png)

## Exemplo 3: gráfico Quadrante Multissérie na Web {#example-multi-series-quadrant-chart-in-web}

O gráfico representa o valor das transações executadas em um determinado intervalo de datas. O gráfico de Quadrante oferece a capacidade de dividir a área do gráfico em quatro seções rotuladas. O gráfico usa um ponto de referência estático para o eixo X e o eixo Y. Use o recurso de várias séries para separar dados com base no nome do banco.

Para fazer isso, especifique as seguintes propriedades:

* **Nome:** Especifique o nome do gráfico.
* **Tipo de Gráfico:** Selecione **Quadrante** na lista suspensa.

* Marque a caixa de seleção **Várias Séries**.
* **Objeto de Modelo de Dados**: especifique a propriedade do objeto de modelo de dados para a série. A propriedade do objeto de modelo de dados para o nome do banco é pai das propriedades do objeto de modelo de dados representadas no eixo X e no eixo Y.
* **Objetos do Modelo de Dados:** Selecione as propriedades do objeto de modelo de dados para criar associações de dados para o eixo X (Data da Transação) e o eixo Y (Valor da Transação).
* Na seção **Ponto de Referência**, selecione **Estático** como o Tipo de Associação.

* Especifique os valores para os pontos de referência do eixo X e do eixo Y.
* Especifique os rótulos de quadrante dos quadrantes Superior Esquerdo, Superior Direito, Inferior Direito e Inferior Esquerdo.
* Marque a caixa de seleção **Mostrar legendas** para exibir os códigos de cor para os nomes dos bancos.

![Gráficos de quadrante](assets/charts_quadrant_example_new.png)
