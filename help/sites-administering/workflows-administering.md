---
title: Administração de instâncias do fluxo de trabalho
description: Saiba como o console de fluxo de trabalho fornece várias ferramentas para administrar instâncias de fluxo de trabalho e garantir que elas estejam sendo executadas conforme esperado.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 66%

---

# Administração de instâncias do fluxo de trabalho{#administering-workflow-instances}

O console do fluxo de trabalho fornece várias ferramentas para administrar instâncias do fluxo de trabalho e garantir que elas estejam em execução conforme esperado.

>[!NOTE]
>
>O [console JMX](/help/sites-administering/jmx-console.md#workflow-maintenance) fornece operações adicionais de manutenção de fluxo de trabalho.

Há vários consoles disponíveis para administrar seus fluxos de trabalho. Use a [navegação global](/help/sites-authoring/basic-handling.md#global-navigation) para abrir o painel **Ferramentas** e selecione **Fluxo de trabalho**:

* **Modelos**: gerenciar definições de fluxo de trabalho
* **Instâncias**: exibir e gerenciar instâncias de fluxos de trabalho em execução
* **Iniciadores**: gerenciar o modo como os fluxos de trabalho devem ser inicializados
* **Arquivo**: exibir o histórico de fluxos de trabalho que foram concluídos com sucesso
* **Falhas**: exibir o histórico de fluxos de trabalho que foram concluídos com erros
* **Atribuição automática**: configurar a atribuição automática de fluxos de trabalho aos modelos

## Monitorar o status de instâncias de fluxo de trabalho {#monitoring-the-status-of-workflow-instances}

1. Usando a navegação, selecione **Ferramentas** e, em seguida, **Fluxo de trabalho**.
1. Selecione **Instâncias** para exibir a lista de instâncias de fluxo de trabalho em andamento.

   ![wf-96](assets/wf-96.png)

<!--
## Search Workflow Instances {#search-workflow-instances}

1. Using Navigation select **Tools**, then **Workflow**.
1. Select **Instances** to display the list of workflow instances currently in progress. On the top rail, in the left corner, select **Filters**. Alternatively, you can use the keystrokes alt+1. The following dialog is displayed:

   ![wf-99-1](assets/wf-99-1.png)

1. In the Filter dialog, select the workflow search criteria. You can search based on these inputs:

   * Payload path: Select a specific path
   * Workflow model: Select a workflow model
   * Assignee: Select a workflow Assignee
   * Type: Task, Workflow item, or Workflow Failure
   * Task Status: Active, Complete, or Terminated
   * Where I Am: Owner AND Assignee, Owner only, Assignee only
   * Start Date: Start date before or after a specified date
   * End Date: End date before or after a specified date
   * Due Date: Due date before or after a specified date
   * Updated Date: Updated date before or after a specified date
-->

## Suspensão, retomada e encerramento de uma instância de fluxo de trabalho {#suspending-resuming-and-terminating-a-workflow-instance}

1. Usando a navegação, selecione **Ferramentas** e, em seguida, **Fluxo de trabalho**.
1. Selecione **Instâncias** para exibir a lista de instâncias de fluxo de trabalho em andamento.

   ![wf-96-1](assets/wf-96-1.png)

1. Selecione um item específico e use **Encerrar**, **Suspender** ou **Retomar**, conforme adequado; é necessária uma confirmação e/ou outros pormenores:

   ![wf-97-1](assets/wf-97-1.png)

## Visualização de fluxos de trabalho arquivados {#viewing-archived-workflows}

1. Usando a navegação, selecione **Ferramentas** e, em seguida, **Fluxo de trabalho**.
1. Selecione **Arquivar** para exibir a lista de instâncias de fluxo de trabalho concluídas com êxito.

   ![wf-98](assets/wf-98.png)

   >[!NOTE]
   >
   >O status interrompido é considerado um encerramento bem-sucedido, pois ocorre como resultado da ação do usuário; por exemplo:
   >
   >* o uso da ação **Encerrar**
   >* quando uma página que está sujeita a um fluxo de trabalho é excluída (à força), o fluxo de trabalho é encerrado

1. Selecione um item específico e **Abra o histórico** para ver mais detalhes:

   ![wf-99](assets/wf-99.png)

## Correção de falhas na instância do fluxo de trabalho {#fixing-workflow-instance-failures}

Quando um fluxo de trabalho falha, o AEM fornece o console **Falhas**, que permite investigar e tomar as medidas apropriadas após tratar a causa original:

* **Detalhes da falha**
Abre uma janela para mostrar a **Mensagem de Falha**, **Etapa** e **Pilha de Falhas**.

* **Abrir histórico**
Mostra detalhes do histórico do fluxo de trabalho.

* **Repetir Etapa** - Executa a instância do componente Etapa do Script novamente. Use o comando Repetir etapa após corrigir a causa do erro original. Por exemplo, repita a etapa depois de corrigir um erro no script que a Etapa do processo executa.
* **Encerrar** - Encerra o fluxo de trabalho se o erro tiver gerado uma situação irreparável para o fluxo de trabalho. Por exemplo, o fluxo de trabalho pode depender de condições ambientais, como informações no repositório que não são mais válidas para a instância do fluxo de trabalho.
* **Encerrar e repetir** - Semelhante a **Encerrar**, exceto que uma nova instância de fluxo de trabalho é iniciada usando a carga, o título e a descrição originais.

Para investigar falhas e, em seguida, retomar ou encerrar o fluxo de trabalho, use as seguintes etapas:

1. Usando a navegação, selecione **Ferramentas** e, em seguida, **Fluxo de trabalho**.
1. Selecione **Falhas** para exibir a lista de instâncias de fluxo de trabalho que não foram concluídas com êxito.
1. Selecione um item específico e, em seguida, a ação apropriada:

   ![wf-47](assets/wf-47.png)

## Limpeza regular de instâncias de fluxo de trabalho {#regular-purging-of-workflow-instances}

Minimizar o número de instâncias de fluxo de trabalho aumenta o desempenho do motor de workflow. Portanto, você pode remover regularmente do repositório as instâncias de fluxo de trabalho concluídas ou em execução.

Defina a **configuração de limpeza de fluxos de trabalho do Adobe Granite** para remover instâncias de fluxo de trabalho de acordo com sua idade e status. Você também pode remover as instâncias de fluxo de trabalho de todos os modelos ou de um modelo específico.

Você também pode criar várias configurações do serviço para remover as instâncias de fluxo de trabalho que satisfaçam critérios diferentes. Por exemplo, crie uma configuração que remova as instâncias de um modelo de fluxo de trabalho específico quando elas estiverem em execução por mais tempo do que o esperado. Crie outra configuração que remova todos os fluxos de trabalho concluídos após um determinado número de dias para minimizar o tamanho do repositório.

Para configurar o serviço, você pode usar o [Console da Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ou [adicionar uma configuração OSGi ao repositório](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository). A tabela a seguir descreve as propriedades necessárias para qualquer método.

>[!NOTE]
>
>Para adicionar a configuração ao repositório, o PID do serviço é:
>
>`com.adobe.granite.workflow.purge.Scheduler`
>
>Como o serviço é de fábrica, o nome do nó `sling:OsgiConfig` requer um sufixo identificador. Por exemplo:
>
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

<table>
 <tbody>
  <tr>
   <th>Nome da propriedade (console da Web)</th>
   <th>Nome da propriedade OSGi</th>
   <th>Descrição</th>
  </tr>
  <tr>
   <td>Nome da tarefa</td>
   <td>scheduledpurge.name</td>
   <td>Um nome descritivo para a limpeza agendada.</td>
  </tr>
  <tr>
   <td>Status do fluxo de trabalho</td>
   <td>scheduledpurge.workflowStatus</td>
   <td><p>O status das instâncias de fluxo de trabalho a serem removidas. Os seguintes valores são válidos:</p>
    <ul>
     <li>CONCLUÍDO: as instâncias de fluxo de trabalho concluídas são removidas.</li>
     <li>EM EXECUÇÃO: as instâncias de fluxo de trabalho em execução são removidas.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Modelos a remover</td>
   <td>scheduledpurge.modelIds</td>
   <td><p>A ID dos modelos de fluxo de trabalho a serem removidos. A ID é o caminho para o nó do modelo, por exemplo:<br /> /var/workflow/models/dam/update_asset<br /> </p> <p>Para especificar vários modelos, clique no botão + no console da Web. </p> <p>Não especifique nenhum valor para remover instâncias de todos os modelos de fluxo de trabalho.</p> </td>
  </tr>
  <tr>
   <td>Idade do fluxo de trabalho</td>
   <td>scheduledpurge.daysold</td>
   <td>A idade das instâncias de fluxo de trabalho a serem removidas em dias.</td>
  </tr>
 </tbody>
</table>

## Configuração do tamanho máximo da caixa de entrada {#setting-the-maximum-size-of-the-inbox}

Você pode definir o tamanho máximo da caixa de entrada configurando o **Serviço de Fluxo de Trabalho do Adobe Granite**, usando o [Console da Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ou [adicionando uma configuração OSGi ao repositório](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository). A tabela a seguir descreve a propriedade que você configura para qualquer método.

>[!NOTE]
>
>Para adicionar a configuração ao repositório, o PID do serviço é:
>
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Nome da propriedade (console da Web) | Nome da propriedade OSGi |
|---|---|
| Tamanho máximo da consulta da caixa de entrada | granite.workflow.inboxQuerySize |

## Uso de variáveis de fluxo de trabalho para armazenamentos de dados de propriedade do cliente {#using-workflow-variables-customer-datastore}

Os dados processados por fluxos de trabalho são armazenados no armazenamento fornecido pela Adobe (JCR). Esses dados podem ser de natureza sensível. É recomendado salvar todos os metadados/dados definidos pelo usuário em seu próprio armazenamento gerenciado, em vez de usar o armazenamento fornecido pela Adobe. Essas seções descrevem como configurar essas variáveis em um armazenamento externo.

### Definir o modelo para usar o armazenamento externo de metadados {#set-model-for-external-storage}

No nível do modelo de fluxo de trabalho, um sinalizador é fornecido para indicar que o modelo e suas instâncias de tempo de execução têm acesso ao armazenamento externo de metadados. As variáveis de fluxo de trabalho não são mantidas no JCR para as instâncias de fluxo de trabalho dos modelos marcados para armazenamento externo.

A propriedade *userMetadataPersistenceEnabled* será armazenada no *nó jcr:content* do modelo de fluxo de trabalho. Esse sinalizador será mantido nos metadados do fluxo de trabalho como *cq:userMetaDataCustomPersistenceEnabled*.

A ilustração abaixo mostra como definir o sinalizador em um fluxo de trabalho.

![workflow-externalize-config](assets/workflow-externalize-config.png)

### APIs de metadados no armazenamento externo {#apis-for-metadata-external-storage}

Para armazenar as variáveis externamente, implemente as APIs que o fluxo de trabalho expõe.

UserMetaDataPersistenceContext

Os exemplos a seguir mostram como usar a API.

```
@ProviderType
public interface UserMetaDataPersistenceContext {
 
    /**
     * Gets the workflow for persistence
     * @return workflow
     */
    Workflow getWorkflow();
 
    /**
     * Gets the workflow id for persistence
     * @return workflowId
     */
    String getWorkflowId();
 
    /**
     * Gets the user metadata persistence id
     * @return userDataId
     */
    String getUserDataId();
}
```

UserMetaDataPersistenceProvider

```
/**
 * This provider can be implemented to store the user defined workflow-data metadata in a custom storage location
 */
@ConsumerType
public interface UserMetaDataPersistenceProvider {
 
   /**
    * Retrieves the metadata using a unique identifier
    * @param userMetaDataPersistenceContext
    * @param metaDataMap of user defined workflow data metaData
    * @throws WorkflowException
    */
   void get(UserMetaDataPersistenceContext userMetaDataPersistenceContext, MetaDataMap metaDataMap) throws WorkflowException;
 
   /**
    * Stores the given metadata to the custom storage location
    * @param userMetaDataPersistenceContext
    * @param metaDataMap metadata map
    * @return the unique identifier that can be used to retrieve metadata. If null is returned, then workflowId is used.
    * @throws WorkflowException
    */
   String put(UserMetaDataPersistenceContext userMetaDataPersistenceContext, MetaDataMap metaDataMap) throws WorkflowException;
} 
```
