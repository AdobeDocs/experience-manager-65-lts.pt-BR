---
title: Recuperação dos dados de formulários do AEM
description: Este documento descreve as etapas necessárias para recuperar os dados de formulários do AEM.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---

# Recuperação dos dados de formulários do AEM {#recovering-the-aem-forms-data}

Esta seção descreve as etapas necessárias para recuperar os dados de formulários do AEM. Consulte também [Considerações especiais sobre backup e recuperação](/help/forms/using/admin-help/backup-recovery-strategy-aem-forms.md#special-considerations-for-backup-and-recovery).

>[!NOTE]
>
>O banco de dados, o GDS, o repositório do AEM e os diretórios raiz do armazenamento de conteúdo devem ser restaurados em um computador com o mesmo nome DNS do original.

Os formulários do AEM devem se recuperar de forma confiável das seguintes falhas:

**Falha de Disco:** A mídia de backup mais recente é necessária para recuperar o conteúdo do banco de dados.

**Corrupção de Dados:** Os sistemas de arquivos não registram transações passadas e os sistemas podem substituir acidentalmente os dados de processo necessários.

**Erro de Usuário:** a recuperação está limitada aos dados disponibilizados pelo banco de dados. Se os dados foram armazenados e estão disponíveis, a recuperação é simplificada.

**Falta de Energia, Falha do Sistema:** As APIs do sistema de arquivos geralmente não são projetadas ou usadas de maneira robusta que proteja contra falhas inesperadas do sistema. Se ocorrer uma falta de energia ou uma falha no sistema, o conteúdo do documento armazenado no banco de dados estará mais provavelmente atualizado do que o conteúdo armazenado em um sistema de arquivos.

Se estiver usando o modo de backup contínuo, você ainda estará no modo de backup após a recuperação. Se estiver usando o modo de backup de snapshot, você não estará no modo de backup após a recuperação.

Ao restaurar de um backup para um novo sistema, as configurações a seguir podem ser diferentes. Essa diferença não deve afetar uma recuperação bem-sucedida do aplicativo AEM Forms:

* Endereço IP
* Configuração do sistema físico (CPUs, disco, memória)
* Localização do GDS

>[!NOTE]
>
>O backup do diretório raiz do armazenamento de conteúdo deve ser restaurado no local desse diretório, conforme definido durante a configuração do Content Services.

Se um único nó de um cluster de vários nós falhar e os nós restantes do cluster estiverem operando corretamente, execute o procedimento de recuperação de nó único do cluster.

## Recuperar os dados de formulários do AEM {#recover-the-aem-forms-data}

1. Pare os serviços de formulários do AEM e o servidor de aplicativos, se estiver em execução.
1. Se necessário, recrie o sistema físico a partir de uma imagem do sistema. Por exemplo, esta etapa pode não ser necessária se o motivo da recuperação for um servidor de banco de dados com defeito.
1. Aplique patches ou atualizações aos formulários do AEM que foram aplicados desde que a imagem foi criada. Essas informações foram registradas no procedimento de backup. Os formulários do AEM devem ser corrigidos no mesmo nível de patch de quando foi feito o backup do sistema.
1. (WebSphere® Application Server) Se estiver recuperando uma nova instância do WebSphere® Application Server, execute o comando restoreConfig.bat/sh.
1. Recupere o banco de dados do AEM Forms executando primeiro uma operação de restauração de banco de dados usando os arquivos de backup do banco de dados e, em seguida, aplicando os redo logs de transação ao banco de dados recuperado. (Consulte [banco de dados de formulários do AEM](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).) Para obter mais informações, consulte um destes artigos da base de dados de conhecimento:

   * [DB2](/help/forms/using/admin-help/files-back-recover.md#db2)
   * [Formulários Oracle Backup and Recovery for AEM](/help/forms/using/admin-help/files-back-recover.md#oracle)
   * [Microsoft](/help/forms/using/admin-help/files-back-recover.md#sql-server)
   * [Backup e recuperação MySQL para formulários AEM](/help/forms/using/admin-help/files-back-recover.md#mysql)

1. Recupere o diretório GDS, primeiro excluindo o conteúdo do diretório GDS na instalação existente do AEM Forms e, em seguida, copiando o conteúdo do diretório GDS do GDS de backup. Se você alterou o local do diretório GDS, consulte [Alterando o local GDS durante a recuperação](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).
1. Renomeie o diretório de backup de GDS a ser restaurado, conforme mostrado nestes exemplos:

   >[!NOTE]
   >
   >Se o diretório /restore já existir, faça backup dele e depois exclua-o antes de renomear o diretório /backup que contém os dados mais recentes.

   * (JBoss®) Renomear `[appserver root]/server/'server'/svcnative/DocumentStorage/backup` para:

     `[appserver root]/server/'server'/svcnative/DocumentStorage/restore`.

   * (WebLogic) Renomear `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/backup` para:

     `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/restore`.

   * (WebSphere®) Renomear `[appserver root]/installedApps/adobe/'server'/DocumentStorage/backup` para:

     `[appserver root]/installedApps/adobe/'server'/DocumentStorage/restore`.

1. Recupere o diretório raiz de armazenamento de conteúdo primeiro excluindo o conteúdo do diretório raiz de armazenamento de conteúdo na instalação existente do AEM Forms e, em seguida, recuperando o conteúdo seguindo as tarefas para ambientes independentes ou em cluster:

   >[!NOTE]
   >
   >O backup do diretório raiz do armazenamento de conteúdo deve ser restaurado no local do diretório raiz do armazenamento de conteúdo conforme definido durante a configuração do Content Services (obsoleto).

   **Autônomo:** Durante o processo de recuperação, restaure todos os diretórios que foram incluídos no backup. Quando esses diretórios forem restaurados, se o diretório /backup-lucene-indexes estiver presente, renomeie-o para /lucene-indexes. Caso contrário, o diretório de índices Lucene já deve existir e nenhuma ação é necessária.

   **Clusterizado:** Durante o processo de recuperação, restaure todos os diretórios que foram incluídos no backup. Para restaurar o diretório Raiz do Índice, execute as seguintes etapas em cada nó do cluster:

   * Exclua todo o conteúdo no diretório Raiz do Índice.
   * Se o diretório /backup-lucene-indexes estiver presente, copie o conteúdo do *diretório Raiz de Armazenamento de Conteúdo*/backup-lucene-indexes para o diretório Raiz de Índice e exclua o *diretório Raiz de Armazenamento de Conteúdo*/backup-lucene-indexes.
   * Se o diretório /lucene-indexes estiver presente, copie o conteúdo do *diretório Raiz de Armazenamento de Conteúdo*/lucene-indexes para o diretório Raiz de Índice.

1. Restaurar/recuperar o repositório do CRX.

   * **Independente**

     *Restaurar instâncias de criação e publicação*: se ocorrer um desastre, você poderá restaurar o repositório para o último estado de backup executando as etapas descritas em [Backup e Restauração.](https://helpx.adobe.com/experience-manager/kb/CRXBackupAndRestoreProcedure.html)

     A restauração completa do nó Autor determina a restauração dos dados do Forms Manager e do AEM Forms Workspace também.

   * **Clusterizado**

     Para restauração em um ambiente em cluster, consulte [Estratégia de backup e restauração em um ambiente em cluster](/help/forms/using/admin-help/strategy-backup-restore-clustered-environment.md#strategy-for-backup-and-restore-in-a-clustered-environment).

1. Exclua todos os arquivos temporários de formulários do AEM que foram criados no diretório java.io.temp ou no diretório temporário do Adobe.
1. Inicie os formulários do AEM (consulte [Iniciando e interrompendo serviços](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))<!-- BROKEN LINK and the application server(s) (see [Maintaining the Application Server](/help/forms/using/admin-help/topics/maintaining-the-application-server.md))-->.

## Alteração da localização do GDS durante a recuperação {#changing-the-gds-location-during-recovery}

Se o GDS for restaurado para um local diferente do local original, execute o script LCSetGDS para definir o GDS para o novo local. O script está na pasta `[aem-forms root]\sdk\misc\Foundation\SetGDSCommandline` O script usa dois parâmetros, `defaultGDS` e `newGDS`. Consulte o arquivo `ReadMe.txt` na mesma pasta para obter instruções sobre como executar o script.

>[!NOTE]
>
>Se você tiver ativado o armazenamento de documentos no banco de dados, não será necessário alterar o local do GDS.

>[!NOTE]
>
>Essa circunstância é a única sob a qual você deve usar esse script para alterar a localização do GDS. Para alterar a localização do GDS enquanto o AEM Forms estiver em execução, use o Console de Administração. (Consulte [Definir configurações gerais de formulários do AEM](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).)

>[!NOTE]
>
>A implantação do componente falhará no Windows se o diretório GDS estiver na raiz da unidade (por exemplo, D:\). Para GDS, você deve verificar se o diretório não está localizado na raiz da unidade, mas está em um subdiretório. Por exemplo, o diretório deve ser D:\GDS e não apenas D:\.

## Recuperação do GDS em um ambiente em cluster {#recovering-the-gds-to-a-clustered-environment}

Para alterar a localização do GDS em um ambiente clusterizado, desligue todo o cluster e execute o script LCSetGDS em um único nó do cluster. (Consulte [Alterando o local do GDS durante a recuperação](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).) Inicie somente esse nó. Quando esse nó for totalmente iniciado, outros nós no cluster poderão ser iniciados com segurança e apontarão corretamente para o novo GDS.

>[!NOTE]
>
>Se você não puder garantir que inicie um nó completamente antes de iniciar outros nós, execute o script LCSetGDS em cada nó do cluster antes de iniciar o cluster.
