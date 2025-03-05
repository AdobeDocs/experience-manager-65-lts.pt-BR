---
title: Tarefas de Manutenção de Pré-Atualização
description: Saiba mais sobre as tarefas de pré-atualização recomendadas para o AEM.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: b7304709729915dbcc27533caf88b61cd5657a2c
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 0%

---

# Tarefas de Manutenção de Pré-Atualização{#pre-upgrade-maintenance-tasks}

Antes de iniciar a atualização, é importante seguir estas tarefas de manutenção para garantir que o sistema esteja pronto e possa ser revertido caso ocorram problemas:

* [Definições de índice](#index-definitions)
* [Garantir espaço suficiente em disco](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Fazer backup completo do AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Gerar o arquivo quickstart.properties](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Configurar a limpeza do fluxo de trabalho e do log de auditoria](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Instalar, Configurar e Executar as Tarefas de Pré-Atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Remover Atualizações Do Diretório /install](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Interromper Quaisquer Instâncias De Modo De Espera Por Frio](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Desabilitar Trabalhos Agendados Personalizados](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Executar limpeza de revisão offline](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Executar coleta de lixo do armazenamento de dados](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Fazer Upgrade do Esquema de Banco de Dados, Se Necessário](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#upgradethedatabaseschemaifneeded)
* [Girar arquivos de registro](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Definições de índice {#index-definitions}

Verifique se você instalou as definições de índice necessárias lançadas com os Service Packs do AEM 6.5 fornecidos até o AEM Service Pack 22, no mínimo. (Consulte as [notas de versão do Service Pack do AEM 6.5](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/release-notes) para obter mais informações).

## Garantir espaço suficiente em disco {#ensure-sufficient-disk-space}

Ao executar a atualização, verifique se há espaço em disco suficiente.

## Fazer backup completo do AEM {#fully-back-up-aem}

O backup do AEM deve ser concluído antes do início da atualização. Faça backup do repositório, da instalação do aplicativo, do armazenamento de dados e das instâncias Mongo, se aplicável. Para obter mais informações sobre como fazer backup e restaurar uma instância do AEM, consulte [Backup e Restauração](/help/sites-administering/backup-and-restore.md).

## Gerar o arquivo quickstart.properties {#generate-quickstart-properties}

Ao iniciar o AEM do arquivo jar, um arquivo `quickstart.properties` é gerado em `crx-quickstart/conf`. Se o AEM só tiver sido iniciado com o script de inicialização no passado, esse arquivo não estará presente e a atualização falhará. Verifique a existência desse arquivo e reinicie o AEM a partir do arquivo jar, se ele não estiver presente.

## Configurar a limpeza do fluxo de trabalho e do log de auditoria {#configure-wf-audit-purging}

As tarefas `WorkflowPurgeTask` e `com.day.cq.audit.impl.AuditLogMaintenanceTask` exigem configurações OSGi separadas e não podem funcionar sem elas. Se eles falharem durante a execução da tarefa de pré-atualização, a falta de configurações será o motivo mais provável. Portanto, adicione configurações OSGi para essas tarefas ou remova-as completamente da lista de tarefas de otimização de pré-atualização se não quiser executá-las. A documentação para configurar tarefas de limpeza de fluxo de trabalho pode ser encontrada em [Administrando Instâncias de Fluxo de Trabalho](/help/sites-administering/workflows-administering.md) e a configuração da tarefa de manutenção de log de auditoria pode ser encontrada em [Manutenção de Log de Auditoria no AEM 6](/help/sites-administering/operations-audit-log.md).


## Instalar, Configurar e Executar as Tarefas de Pré-Atualização {#install-configure-run-pre-upgrade-tasks}

As tarefas de manutenção pré-atualização que antes tinham de ser realizadas manualmente estão sendo otimizadas e automatizadas. A otimização de manutenção de pré-atualização permite uma maneira unificada de acionar essas tarefas e inspecionar seus resultados sob demanda.

### Como usá-lo {#how-to-use-it}

O componente OSGI `PreUpgradeTasksMBean` vem pré-configurado com uma lista de tarefas de manutenção de pré-atualização que podem ser executadas todas de uma vez. Você pode configurar as tarefas seguindo o procedimento abaixo:

1. Vá para o Console da Web navegando até *https://serveraddress:serverport/system/console/configMgr*

1. Procure por &quot;**tarefas de pré-atualização**&quot; e clique no primeiro componente correspondente. O nome completo do componente é `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`

1. Modifique a lista de tarefas de manutenção que devem ser executadas conforme mostrado abaixo:

   ![1487758925984](assets/1487758925984.png)

Abaixo está uma descrição do modo de execução para o qual cada tarefa de manutenção foi projetada.

| Tarefa | Notas |
|---|---|
| TarefaDeLimpezaDeFluxoDeTrabalho | É necessário configurar o OSGi de configuração de limpeza de fluxo de trabalho do Adobe Granite antes de executar. |
| GenerateBundlesListFileTask |   |
| TarefaDeLimpezaDeRevisão |   |
| com.day.cq.audit.impl.AuditLogMaintenanceTask | É necessário definir a configuração OSGi do Agendador de limpeza de log de auditoria antes de executar. |

### Configuração padrão das verificações de integridade de pré-atualização {#default-configuration-of-the-pre-upgrade-health-checks}

O componente OSGI `PreUpgradeTasksMBeanImpl` vem pré-configurado com uma lista de marcas de verificação de integridade de pré-atualização a serem executadas quando o método `runAllPreUpgradeHealthChecks` for chamado:

* **sistema** - a marca usada pelas verificações de integridade de manutenção do Granite

* **pré-atualização** - uma marca personalizada que pode ser adicionada a todas as verificações de integridade que você pode definir para execução antes de uma atualização

**Métodos MBean**

A funcionalidade do bean gerenciado pode ser acessada usando o [Console JMX](/help/sites-administering/jmx-console.md).

Você pode acessar os MBeans ao:

1. Indo para o Console JMX em *https://serveraddress:serverport/system/console/jmx*
1. Pesquise por **PreUpgradeTasks** e clique no resultado

1. Selecione qualquer método na seção **Operações** e selecione **Chamar** na janela a seguir.

Abaixo está uma lista de todos os métodos disponíveis que `PreUpgradeTasksMBeanImpl` expõe:

| Nome do método | Tipo | Descrição |
|---|---|---|
| runAllPreUpgradeTasks() | AÇÃO | Executa todas as tarefas de manutenção de pré-atualização da lista. |
| runPreUpgradeTask(preUpgradeTaskName) | AÇÃO | Executa a tarefa de manutenção de pré-atualização com o nome fornecido como o parâmetro. |
| getPreUpgradeTaskLastRunTime(preUpgradeTaskName) | AÇÃO | Exibe o tempo de execução exato da tarefa de manutenção de pré-atualização com o nome fornecido como parâmetro. |
| getPreUpgradeTaskLastRunState(preUpgradeTaskName) | AÇÃO | Exibe o último estado de execução da tarefa de manutenção de pré-atualização com o nome fornecido como o parâmetro. |
| runAllPreUpgradeHealthChecks(shutDownOnSuccess) | AÇÃO | Executa todas as verificações de integridade pré-atualização e salva o status em um arquivo chamado preUpgradeHCStatus.properties no caminho do sling home. Se shutDownOnSuccess estiver definido como true, a instância do AEM será encerrada, mas somente se todas as verificações de integridade anteriores à atualização tiverem um status OK. O arquivo de propriedades é usado como uma pré-condição para qualquer atualização futura e o processo de atualização é interrompido se a execução da verificação de integridade pré-atualização falhar. Se quiser ignorar o resultado das verificações de integridade de pré-atualização e iniciar a atualização de qualquer maneira, você poderá excluir o arquivo. |
| detectUsageOfUnavailableAPI(aemVersion) | AÇÃO | Lista todos os pacotes importados que não são mais satisfeitos ao atualizar para a versão do AEM especificada. A versão de destino do AEM deve ser fornecida como um parâmetro. |

>[!NOTE]
>
>Os métodos MBean podem ser chamados por meio de:
>
>* A console JMX
>* Qualquer aplicativo externo que se conecta ao JMX
>* cURL
>

## Remover Atualizações Do Diretório /install {#remove-updates-install-directory}

>[!NOTE]
>
>Remova pacotes somente do diretório crx-quickstart/install APÓS desligar a instância do AEM. Esta etapa é uma das últimas antes de iniciar o procedimento de atualização no local.

Remova service packs, pacotes de recursos ou hotfixes que foram implantados por meio do diretório `crx-quickstart/install` no sistema de arquivos local. Isso impede a instalação inadvertida de hotfixes e service packs antigos na nova versão do AEM, após a conclusão da atualização.

## Interromper Quaisquer Instâncias De Modo De Espera Por Frio {#stop-tarmk-coldstandby-instance}

Se estiver usando a espera a frio do TarMK, interrompa todas as instâncias a frio da espera. Isso garante uma maneira eficiente de voltar a ficar online em caso de problemas na atualização. Depois que o upgrade for concluído com sucesso, as instâncias off-line deverão ser recriadas a partir das instâncias principais atualizadas.

## Desabilitar Trabalhos Agendados Personalizados {#disable-custom-scheduled-jobs}

Desative todos os trabalhos agendados OSGi incluídos no código do aplicativo.

## Executar limpeza de revisão offline {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Esta etapa só é necessária para instalações TarMK

Se estiver usando TarMK, você deve executar a Limpeza de revisão offline antes da atualização. Isso torna a etapa de migração do repositório e as tarefas de atualização subsequentes muito mais rápidas e ajuda a garantir que a Limpeza de revisão online possa ser executada com êxito após a conclusão da atualização. Para obter informações sobre como executar a Limpeza de Revisão Offline, consulte [Execução da Limpeza de Revisão Offline](/help/sites-deploying/revision-cleanup.md#revision-cleanuprevision-cleanup).

## Executar coleta de lixo do armazenamento de dados {#execute-datastore-garbage-collection}

Depois de executar a limpeza de revisão nas instâncias do CRX3, você deve executar a Coleta de lixo do armazenamento de dados para remover os blobs não referenciados no armazenamento de dados. Para obter instruções, consulte a documentação em [Coleta de lixo do armazenamento de dados](/help/sites-administering/data-store-garbage-collection.md).

## Girar arquivos de registro {#rotate-log-files}

A Adobe recomenda arquivar seus arquivos de log atuais antes de iniciar a atualização. Isso facilita a monitoração e a varredura dos arquivos de registro durante e após a atualização para identificar e resolver quaisquer problemas que possam ocorrer.
