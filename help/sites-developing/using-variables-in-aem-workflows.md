---
title: Variáveis em workflows do AEM
description: Crie uma variável, defina um valor para a variável e use-o nas etapas de fluxo de trabalho OR Split e Goto AEM.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: eb75efb8-c59a-4d51-af54-942cca178f2e
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 0%

---

# Variáveis em workflows do AEM{#variables-in-aem-workflows}

Uma variável em um modelo de fluxo de trabalho é uma maneira de armazenar um valor com base em seu tipo de dados. Em seguida, você pode usar o nome da variável em qualquer etapa do fluxo de trabalho para recuperar o valor armazenado na variável. Você também pode usar nomes de variáveis para definir expressões para tomar decisões de roteamento.

Nos modelos de fluxo de trabalho do AEM, é possível:

* [Crie uma variável](/help/sites-developing/using-variables-in-aem-workflows.md#create-a-variable) de um tipo de dados com base no tipo de informações que você deseja armazenar nela.
* [Defina um valor para a variável](/help/sites-developing/using-variables-in-aem-workflows.md#set-a-variable) usando a etapa de fluxo de trabalho Definir Variável.
* [Use a variável](/help/sites-developing/using-variables-in-aem-workflows.md#use-a-variable) nas etapas de fluxo de trabalho OR Split e Goto AEM para definir uma expressão para tomar decisões de roteamento. Também é possível usar variáveis em todas as etapas do fluxo de trabalho do AEM Forms.

As variáveis são uma extensão da interface [MetaDataMap](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html). Você pode usar [MetaDataMap](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) no ECMAScript para acessar metadados salvos usando variáveis.

## Criar uma variável {#create-a-variable}

Você cria variáveis usando a seção Variáveis disponível no sidekick do modelo de fluxo de trabalho. As variáveis de fluxo de trabalho do AEM são compatíveis com os seguintes tipos de dados:

* **Tipos de dados primitivos**: Long, Double, Boolean, Date e String
* **Tipos de dados complexos**: [XML](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Document.html) e [JSON](https://www.javadoc.io/doc/com.google.code.gson/gson/2.3/com/google/gson/JsonObject.html)

>[!NOTE]
>
>Os fluxos de trabalho são compatíveis apenas com o formato ISO8601 para variáveis do tipo Date.

Para obter outros tipos de dados complexos disponíveis em fluxos de trabalho do AEM Forms, consulte [Variáveis em fluxos de trabalho do AEM Forms](/help/forms/using/variable-in-aem-workflows.md). Use o tipo de dados ArrayList para criar coleções de variáveis. Você pode criar uma variável ArrayList para todos os tipos de dados primitivos e complexos. Por exemplo, crie uma variável ArrayList e selecione String como subtipo para armazenar vários valores de string usando a variável.

Para criar uma variável,

1. Em uma instância do AEM, navegue até Ferramentas > Fluxo de trabalho > Modelos.
1. Selecione **[!UICONTROL Criar]** e especifique o título e um nome opcional para o modelo de fluxo de trabalho. Selecione o modelo e selecione **[!UICONTROL Editar]**.
1. Selecione o ícone de variáveis disponível no sidekick do modelo de fluxo de trabalho e selecione **[!UICONTROL Adicionar variável]**.

   ![Adicionar variável](assets/variables_add_variable_new.png)

1. Na caixa de diálogo Adicionar variável, especifique o nome e selecione o tipo da variável.
1. Selecione o tipo de dados na lista suspensa **[!UICONTROL Tipo]** e especifique os seguintes valores:

   * Tipo de dados primitivo - Especifique um valor padrão opcional para a variável.
   * JSON ou XML - especifique um caminho de esquema JSON ou XML opcional. O sistema valida o caminho do esquema enquanto mapeia e armazena as propriedades disponíveis nesse esquema para outra variável.
   * Modelo de dados de formulário - especifique um caminho de Modelo de dados de formulário.
   * ArrayList - Especifique um subtipo para a coleção.

1. Especifique uma descrição opcional para a variável e selecione ![Ícone Salvar indicado por uma marca de seleção dentro de uma caixa.](assets/Done_Icon.png) para salvar as alterações. A variável é exibida na lista disponível no painel esquerdo.

Ao criar variáveis, considere as seguintes práticas:

* Crie quantas variáveis um fluxo de trabalho exigir. No entanto, para conservar recursos do banco de dados, use o número mínimo de variáveis necessárias e reutilize variáveis quando possível.
* As variáveis fazem distinção entre maiúsculas e minúsculas. Certifique-se de fazer referência a variáveis usando a mesma capitalização no fluxo de trabalho.
* Evite usar caracteres especiais no nome da variável

## Definir uma variável {#set-a-variable}

Você pode usar a etapa Definir variável para definir o valor de uma variável e a ordem na qual os valores são definidos. A variável é definida na ordem em que os mapeamentos de variável são listados na etapa Definir variável.

As alterações nos valores da variável afetam somente a instância do processo na qual a alteração ocorre. Por exemplo, quando um workflow é iniciado e os dados variáveis são alterados, as alterações afetam somente essa instância do workflow. As alterações não afetam outras instâncias do fluxo de trabalho que foram iniciadas anteriormente ou são iniciadas posteriormente.

Dependendo do tipo de dados da variável, você pode usar as seguintes opções para definir o valor de uma variável:

* **Literal:** Use a opção quando você souber o valor exato a ser especificado.
* **Expressão:** use a opção quando o valor a ser usado for calculado com base em uma expressão. A expressão é criada no editor de expressão fornecido.
* **Anotação JSON Dot:** Use a opção para recuperar um valor de uma variável do tipo JSON ou FDM.
* **XPATH:** Use a opção para recuperar um valor de uma variável do tipo XML.
* **Relativo à carga:** use a opção quando o valor a ser salvo na variável estiver disponível em um caminho relativo à carga.
* **Caminho absoluto:** Use a opção quando o valor a ser salvo na variável estiver disponível em um caminho absoluto.

Você também pode atualizar elementos específicos de uma variável do tipo JSON ou XML usando a notação JSON DOT ou XPATH.

### Adicionar mapeamento entre variáveis {#add-mapping-between-variables}

Para adicionar o mapeamento entre variáveis, faça o seguinte:

1. Na página de edição do workflow, selecione o ícone Etapas disponível no sidekick do modelo de workflow.
1. Arraste e solte a etapa **Definir Variável** no editor de fluxo de trabalho, selecione a etapa e selecione ![Configurar ícone indicado por uma chave inglesa.](assets/configure_icon.png) (Configurar).
1. Na caixa de diálogo Definir variável, selecione **[!UICONTROL Mapeamento]** > **[!UICONTROL Adicionar mapeamento]**.
1. Na seção **Mapear Variável**, selecione a variável para armazenar dados, selecione o modo de mapeamento e especifique um valor para armazenar na variável. Os modos de mapeamento variam de acordo com o tipo de variável.
1. Mapeie mais variáveis para poder fazer uma expressão significativa. Selecione o ícone Salvar ![indicado por uma marca de seleção dentro de uma caixa.](assets/Done_Icon.png) para salvar as alterações.

### Exemplo 1: consultar uma variável XML para definir o valor de uma variável de string {#example-query-an-xml-variable-to-set-value-for-a-string-variable}

Selecione uma variável do tipo XML que você deseja armazenar um arquivo XML. Consulte a variável XML para definir o valor de uma variável de string para a propriedade disponível no arquivo XML. Use **Especificar XPATH para o campo de variável XML** para definir a propriedade a ser armazenada na variável de cadeia de caracteres.

Neste exemplo, selecione uma variável XML **formdata** para armazenar o arquivo **cc-app.xml**. Consulte a variável **formdata** para definir o valor da variável de cadeia de caracteres **emailaddress** para armazenar o valor da propriedade **emailAddress** disponível no arquivo **cc-app.xml**.

### Exemplo 2: usar uma expressão para armazenar valor com base em outras variáveis {#example2}

Use uma expressão para calcular a soma das variáveis e armazenar o resultado em uma variável.

Neste exemplo, use o editor de expressão para definir uma expressão para calcular a soma das variáveis **assetscost** e **balanceamount** e armazenar o resultado na variável **totalvalue**.

## Usar editor de expressão {#use-expression-editor}

Também é possível usar expressões para calcular o valor de uma variável no tempo de execução. As variáveis fornecem um editor de expressão para definir expressões.

Use o editor de expressão para:

* Defina o valor das variáveis usando outras variáveis de fluxo de trabalho, números ou expressões matemáticas.
* Usar variáveis de fluxo de trabalho, string, número ou uma expressão em uma expressão matemática
* Adicione condições para que você possa definir valores de variáveis.
* Adicione operadores entre condições.

![Editor de expressão](assets/variables_expression_editor_new.png)

Tem como base o editor de regras de formulários adaptáveis com as alterações a seguir. Editor de regras em variáveis:

* Não suporta funções.
* Não fornece uma interface para exibir um resumo das regras
* Não tem editor de código.
* Não suporta a ativação e desativação do valor de um objeto.
* Não suporta a configuração da propriedade de um objeto.
* Não há suporte para a chamada de um serviço Web.

Para obter mais informações, consulte [editor de regras de formulários adaptáveis](/help/forms/using/rule-editor.md).

## Usar uma variável {#use-a-variable}

Você pode usar variáveis para recuperar entradas e saídas ou salvar o resultado de uma etapa. O editor de workflow fornece dois tipos de etapas de workflow:

* Etapas do fluxo de trabalho com suporte para variáveis
* Etapas de fluxo de trabalho sem suporte para variáveis

### Etapas do fluxo de trabalho com suporte para variáveis {#workflow-steps-with-support-for-variables}

As etapas Ir para, OU Dividir e todas as etapas do fluxo de trabalho do AEM Forms são compatíveis com variáveis.

#### OU Etapa de divisão {#or-split-step}

A divisão OR cria uma divisão no fluxo de trabalho, depois da qual apenas uma ramificação fica ativa. Essa etapa permite introduzir caminhos de processamento condicional no fluxo de trabalho. Adicione etapas do fluxo de trabalho a cada ramificação, conforme necessário.

Você pode definir a expressão de roteamento para uma ramificação usando uma definição de regra, um script ECMA ou um script externo.

Você pode usar variáveis para definir a expressão de roteamento usando o editor de expressão. Para obter mais informações sobre como usar expressões de roteamento para a etapa de Divisão OR, consulte [OU Etapa de divisão](/help/sites-developing/workflows-step-ref.md#or-split).

Neste exemplo, antes de definir a expressão de roteamento, use o [exemplo 2](/help/sites-developing/using-variables-in-aem-workflows.md#example2) para definir o valor da variável **totalvalue**. A ramificação 1 estará ativa se o valor da variável **totalvalue** for maior que 50000. Da mesma forma, é possível definir uma regra para tornar a Ramificação 2 ativa se o valor da variável **totalvalue** for menor que 50000.

Da mesma forma, selecione um caminho de script externo ou especifique o script ECMA para expressões de roteamento para avaliar a ramificação ativa. Selecione **[!UICONTROL Renomear ramificação]** para especificar um nome alternativo para a ramificação.

Para obter mais exemplos, consulte [Criar um modelo de fluxo de trabalho](/help/forms/using/aem-forms-workflow.md#create-a-workflow-model).

#### Etapa Ir para {#go-to-step}

A **Etapa Ir para** permite especificar a próxima etapa a ser executada no modelo de fluxo de trabalho, dependendo do resultado de uma expressão de roteamento.

Semelhante à etapa OU Split, você pode definir a expressão de roteamento para a etapa Ir para usando uma definição de regra, um script ECMA ou um script externo.

Você pode usar variáveis para definir a expressão de roteamento usando o editor de expressão. Para obter mais informações sobre o uso de expressões de roteamento para a etapa Ir para, consulte [Etapa Ir para](/help/sites-developing/workflows-step-ref.md#goto-step).

![Regra de Ir para](assets/variables_goto_rule1_new.png)

Neste exemplo, a etapa Ir para especifica Revisar Aplicativo de Cartão de Crédito como a próxima etapa se o valor da variável **actiontaken** for igual a **Need more info**.

Para obter mais exemplos sobre como usar a definição de regra na etapa Ir para, consulte [Simulando um loop For](/help/sites-developing/workflows-step-ref.md#simulateforloop).

#### Etapas de fluxo de trabalho centradas no fluxo de trabalho do Forms {#forms-workflow-centric-workflow-steps}

Todas as etapas do fluxo de trabalho do AEM Forms são compatíveis com variáveis. Para obter mais informações, consulte [Fluxo de trabalho centrado no Forms no OSGi](/help/forms/using/aem-forms-workflow-step-reference.md).

### Etapas de fluxo de trabalho sem suporte para variáveis {#workflow-steps-without-support-for-variables}

Você pode usar a interface [MetaDataMap](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) para acessar variáveis em etapas de fluxo de trabalho que não oferecem suporte a variáveis.

#### Recuperar o valor da variável {#retrieve-the-variable-value}

Para recuperar valores para variáveis existentes com base no tipo de dados, use as seguintes APIs no Script ECMA.

| Tipo de dados variável | API |
|---|---|
| Primitiva (Longa, Dupla, Booleana, Data e String) | workItem.getWorkflowData().getMetaDataMap().get(variableName, type) |
| XML | Packages.org.w3c.dom.Document xmlObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.org.w3c.dom.Document.class); |
| JSON | Packages.com.google.gson.JsonObject jsonObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.google.gson.JsonObject.class); |

Para obter informações sobre APIs para tipos de dados de variáveis complexas adicionais disponíveis em fluxos de trabalho do AEM Forms, consulte [Variáveis em fluxos de trabalho do AEM Forms](/help/forms/using/variable-in-aem-workflows.md).

**Exemplo**

Recupere o valor do tipo de dados string usando a seguinte API:

```
workItem.getWorkflowData().getMetaDataMap().get(accname, Packages.java.lang.String)
```

#### Atualizar o valor da variável {#update-the-variable-value}

Para atualizar o valor de uma variável, use a seguinte API no Script ECMA.

```
workItem.getWorkflowData().getMetaDataMap().put(variableName, value)
```

**Exemplo**

```
workItem.getWorkflowData().getMetaDataMap().put(salary, 50000)
```

Atualiza o valor da variável **salário** para 50000.

### Definir variáveis para chamar workflows {#apiinvokeworkflow}

Você pode usar uma API para definir variáveis e passá-las para chamar instâncias de fluxo de trabalho.

[workflowSession.startWorkflow](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/workflow/WorkflowSession.html#startWorkflow-com.adobe.granite.workflow.model.WorkflowModel-com.adobe.granite.workflow.exec.WorkflowData-java.util.Map-) usa model, wfData e metaData como argumentos. Use MetaDataMap para definir o valor da variável.

Nesta API, a variável **variableName** está definida como **value** usando metaData.put(variableName, value);

```java
import com.adobe.granite.workflow.model.WorkflowModel;
import com.adobe.granite.workflow.metadata.MetaDataMap;
import com.adobe.aemfd.docmanager.Document;

/*Assume that you already have a workflowSession and modelId along with the payloadType and payload*/
WorkflowData wfData = workflowSession.newWorkflowData(payloadType, payload);
MetaDataMap metaData = wfData.getMetaDataMap();
metaData.put(variableName, value); //Create a variable "variableName" in your workflow model
WorkflowModel model = workflowSession.getModel(modelId);
workflowSession.startWorkflow(model, wfData, metaData);
```

## Editar uma variável {#edit-a-variable}

1. Na página Editar workflow, selecione o ícone Variáveis disponível no sidekick do modelo de workflow. A seção Variáveis, no painel esquerdo, exibe todas as variáveis existentes.
1. Selecione o ícone ![Editar indicado por um lápis.Ícone ](assets/edit.png) (Editar) ao lado do nome da variável que você deseja editar.
1. Edite as informações da variável e selecione ![Ícone Salvar indicado por uma marca de seleção.](assets/Done_Icon.png) para salvar as alterações. Não é possível editar os campos **[!UICONTROL Nome]** e **[!UICONTROL Tipo]** para uma variável.

## Excluir uma variável {#delete-a-variable}

Antes de excluir a variável, remova todas as referências da variável do fluxo de trabalho. Verifique se a variável não está sendo usada no fluxo de trabalho.

Para excluir uma variável,

1. Na página Editar workflow, selecione o ícone Variáveis disponível no sidekick do modelo de workflow. A seção Variáveis, no painel esquerdo, exibe todas as variáveis existentes.
1. Selecione o ícone Excluir ao lado do nome da variável que você deseja excluir.
1. Selecione o ícone ![Concluído indicado por um símbolo de marca de seleção.](assets/Done_Icon.png) para confirmar e excluir a variável.
