---
title: Arquivos para backup e recuperação
description: Este documento descreve o aplicativo e os arquivos de dados dos quais deve ser feito backup.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 2938a1c6-c8fc-420a-8fad-bb39e5a7936b
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '2029'
ht-degree: 0%

---

# Arquivos para backup e recuperação {#files-to-back-up-and-recover}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Os arquivos de aplicativos e de dados dos quais deve ser feito backup são descritos com mais detalhes nas seções a seguir.

Considere os seguintes pontos em relação ao backup e à recuperação:

* O backup do banco de dados deve ser feito antes do repositório GDS e AEM.
* Se você precisar desativar os nós em um ambiente clusterizado para backup, certifique-se de que os nós secundários estejam desativados antes do nó principal. Caso contrário, isso pode levar a inconsistência no cluster ou servidor. Além disso, o nó primário deve ficar ativo antes de qualquer nó secundário.
* Para a operação de restauração de um cluster, o servidor de aplicativos deve ser interrompido para cada nó no cluster.

## Diretório de Armazenamento de Documentos Global {#global-document-storage-directory}

O GDS é um diretório usado para armazenar arquivos de longa duração que são usados em um processo. A duração de arquivos de longa duração deve abranger uma ou mais inicializações de um sistema de formulários AEM e pode abranger dias e até anos. Esses arquivos de longa duração podem incluir PDFs, políticas e modelos de formulário. Arquivos de longa duração são uma parte essencial do estado geral de muitas implantações de formulários AEM. Se alguns ou todos os documentos de longa duração forem perdidos ou corrompidos, o Forms Server poderá se tornar instável.

Os documentos de entrada para invocação de trabalho assíncrono também são armazenados no GDS e devem estar disponíveis para processar solicitações. Portanto, é importante considerar a confiabilidade do sistema de arquivos que hospeda o GDS e empregar um storage redundante de discos independentes (RAID) ou outra tecnologia, conforme apropriado para suas necessidades de qualidade e nível de serviço.

A localização do GDS é determinada durante o processo de instalação do AEM Forms ou posteriormente usando o console de administração. Além de manter um local de alta disponibilidade para GDS, você também pode habilitar o armazenamento de banco de dados para documentos. Consulte [Opções de backup quando o banco de dados for usado para armazenamento de documentos](files-back-recover.md#backup-options-when-database-is-used-for-document-storage).

### Localização do GDS {#gds-location}

Se você deixar a configuração de local vazia durante a instalação, o local assumirá como padrão um diretório na instalação do servidor de aplicativos. Faça backup do seguinte diretório para o servidor de aplicativos:

* (JBoss) `[appserver root]/server/'server'/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

Se você tiver alterado o local GDS para um local não-padrão, poderá determiná-lo da seguinte maneira:

* Faça logon no console de administração e clique em Configurações > Configurações do sistema principal > Configurações.
* Registre o local especificado na caixa Diretório de Armazenamento de Documentos Globais.

Em um ambiente em cluster, o GDS normalmente aponta para um diretório compartilhado na rede e acessível para leitura/gravação para cada nó de cluster.

A localização do GDS pode ser alterada durante uma recuperação se a localização original já não estiver disponível. (Consulte [Alterando o local do GDS durante a recuperação](/help/forms/using/admin-help/recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).)

### Opções de backup quando o banco de dados é usado para armazenamento de documentos {#backup-options-when-database-is-used-for-document-storage}

Você pode habilitar o armazenamento de documentos do AEM Forms no banco de dados do AEM Forms usando o console de administração. Mesmo que essa opção mantenha todos os documentos persistentes no banco de dados, os formulários do AEM ainda exigem o diretório GDS baseado no sistema de arquivos porque ele é usado para armazenar arquivos e recursos permanentes e temporários relacionados a sessões e invocações de formulários do AEM.

Quando você seleciona a opção &quot;Habilitar armazenamento de documentos no banco de dados&quot; nas Configurações principais do sistema no console de administração ou usando o Configuration Manager, o AEM Forms não permite o modo de backup de instantâneo e o modo de backup contínuo. Portanto, não é necessário gerenciar os modos de backup usando o AEM Forms. Se você usar essa opção, deverá fazer backup do GDS apenas uma vez depois de habilitar a opção. Ao recuperar formulários do AEM de um backup, não é necessário renomear o diretório de backup para o GDS nem restaurar o GDS.

## Repositório do AEM {#aem-repository}

O repositório do AEM (crx-repository) será criado se crx-repository for configurado durante a instalação do AEM Forms. O local do diretório crx-repository é determinado durante o processo de instalação do AEM Forms. O backup e a restauração do repositório do AEM são necessários junto com o banco de dados e o GDS para dados consistentes de formulários do AEM em formulários do AEM. O repositório da AEM contém dados para a Solução de gerenciamento de correspondência, o Forms Manager e o AEM Forms Workspace.

### Solução de gerenciamento de correspondência {#correspondence-management-solution}

A solução de gerenciamento de correspondência centraliza e gerencia a criação, a montagem e o fornecimento de correspondências seguras, personalizadas e interativas. Ele permite reunir rapidamente a correspondência de conteúdo pré-aprovado e criado de forma personalizada em um processo simplificado, da criação ao arquivamento. Como resultado, seus clientes obtêm comunicação oportuna, precisa, conveniente, segura e relevante. Sua empresa maximiza o valor das interações com o cliente e minimiza o custo e o risco com um processo simplificado para facilidade, velocidade e produtividade.

Uma configuração simples da Solução de gerenciamento de correspondência inclui uma instância de autor e uma instância de publicação na mesma máquina ou em máquinas diferentes

### gerenciador de formulários {#forms-manager}

o forms manager simplifica o processo de atualização, gerenciamento e baixa de formulários.

### AEM Forms Workspace {#html-workspace}

O AEM Forms Workspace corresponde aos recursos do Flex Workspace (obsoleto para o AEM Forms no JEE) e adiciona novos recursos para estender e integrar o Workspace e torná-lo mais fácil de usar.

>[!NOTE]
>
>O Flex Workspace está obsoleto para a versão do AEM Forms.

Ele permite o gerenciamento de tarefas em clientes sem o Flash Player e o Adobe Reader. Ele facilita a renderização do HTML Forms, além do PDF forms e do Flex Forms.

## banco de dados do AEM Forms {#aem-forms-database}

O banco de dados do AEM Forms armazena conteúdo, como artefatos de formulário, configurações de serviço, estado do processo e referências de banco de dados a arquivos no GDS e no diretório Raiz de armazenamento de conteúdo (para o Content Services). Os backups do banco de dados podem ser realizados em tempo real sem uma interrupção do serviço e a recuperação pode ser feita para um point-in-time específico ou para uma alteração específica. Esta seção descreve como configurar o banco de dados para que seja possível fazer backup dele em tempo real.

Em um sistema AEM Forms corretamente configurado, o administrador do sistema e o administrador do banco de dados podem colaborar facilmente para recuperar o sistema para um estado consistente e conhecido.

Para fazer backup do banco de dados em tempo real, você deve usar o modo de snapshot ou configurar o banco de dados para ser executado no modo de log especificado. Isso permite que seja feito backup dos arquivos do banco de dados enquanto o banco de dados está aberto e disponível para uso. Além disso, o banco de dados preserva seus logs de reversão e de transações quando está sendo executado nesses modos.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (Obsoleto) é um sistema de gerenciamento de conteúdo instalado com o LiveCycle. Ele permite que os usuários projetem, gerenciem, monitorem e otimizem processos centrados no ser humano. O suporte aos Content Services (obsoleto) termina em 31/12/2014. Consulte o [documento sobre o ciclo de vida do produto Adobe](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html).

### DB2 {#db2}

Configure seu banco de dados DB2 para ser executado no modo de log de arquivamento.

>[!NOTE]
>
>Se o ambiente do AEM Forms foi atualizado de uma versão anterior do AEM Forms e usa DB2, não há suporte para backup online. Nesse caso, você deve fechar o AEM Forms e executar um backup offline. As versões futuras do AEM Forms oferecerão suporte ao backup on-line para clientes de atualização.

A IBM tem um conjunto de ferramentas e sistemas de ajuda para ajudar os administradores de bancos de dados a gerenciar suas tarefas de backup e recuperação:

* Acelerador de Log de Arquivamento do IBM DB2
* Especialista em arquivamento de dados do IBM DB2

O DB2 tem recursos integrados para fazer backup de um banco de dados no Tivoli Storage Manager. Com o Tivoli Storage Manager, os backups do DB2 podem ser armazenados em outra mídia ou no disco rígido local.

### Oracle {#oracle}

Use backups de snapshot ou configure o banco de dados Oracle para ser executado no modo de log de arquivamento. (Consulte [Backup do Oracle: uma introdução](https://www.databasedesign-resource.com/oracle-backup.md).) Para obter mais informações sobre backup e recuperação do banco de dados do Oracle, vá para estes sites:

[Backup e recuperação da Oracle:](https://www.oracle.com/technetwork/database/features/availability/br-overview-097160.html) explica com mais detalhes os conceitos de backup e recuperação e as técnicas mais comuns de uso do Recovery Manager (RMAN) para backup, recuperação e emissão de relatórios, além de fornecer mais informações sobre como planejar uma estratégia de backup e recuperação.

[Guia do Usuário de Backup e Recuperação do Oracle Database:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10642.pdf) fornece informações detalhadas sobre a arquitetura RMAN, conceitos e mecanismos de backup e recuperação, técnicas avançadas de recuperação, como recuperação point-in-time e recursos de flashback de banco de dados, além de ajuste do desempenho de backup e recuperação. Ele também abrange backup e recuperação gerenciados pelo usuário, usando instalações do sistema operacional do host em vez de RMAN. Esse volume é essencial para backup e recuperação de implantações de bancos de dados mais sofisticadas e para cenários avançados de recuperação.

[Referência de Backup e Recuperação do Banco de Dados Oracle:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10643.pdf) fornece informações completas sobre sintaxe e semântica para todos os comandos RMAN e descreve as exibições de banco de dados disponíveis para relatórios sobre atividades de backup e recuperação.

### SQL Server {#sql-server}

Use backups de instantâneos ou configure o banco de dados do SQL Server para ser executado no modo de log de transações.

O SQL Server também fornece duas ferramentas de backup e recuperação:

* GUI (SQL Server Management Studio)
* T-SQL (linha de comando)

Para obter mais informações, consulte [Backup e restauração](https://msdn.microsoft.com/en-us/library/ms187048(v=SQL.90).aspx).

### MySQL {#mysql}

Use MySQLAdmin ou modifique os arquivos INI no Windows para configurar seu banco de dados MySQL para ser executado no modo de log binário. (Consulte [Log binário do MySQL](https://dev.mysql.com/doc/refman/5.1/en/binary-log.html).) Uma ferramenta de backup dinâmico para MySQL também está disponível no software InnoBase. (Consulte [Hot Backup Innobase](https://www.innodb.com/hot-backup/features.md).)

>[!NOTE]
>
>O modo de log binário padrão do MySQL é &quot;Instrução&quot;, que é incompatível com as tabelas usadas pelo Content Services (obsoleto). Usar o registro binário nesse modo padrão faz com que os Serviços de conteúdo (obsoletos) falhem. Se o seu sistema inclui os Serviços de conteúdo (obsoleto), use o modo de registro &quot;Misto&quot;. Para habilitar o log &quot;Misto&quot;, adicione o seguinte argumento ao arquivo my.ini: `binlog_format=mixed log-bin=logname`

Você pode usar o utilitário mysqldump para obter o backup completo do banco de dados. Backups completos são necessários, mas nem sempre são convenientes. Eles produzem grandes arquivos de backup e demoram para serem gerados. Para fazer um backup incremental, inicie o servidor com a opção - `log-bin`, conforme descrito na seção anterior. Cada vez que o servidor MySQL é reiniciado, ele para de gravar no log binário atual, cria um novo e, a partir de então, o novo se torna o atual. Você pode forçar uma opção manualmente com o comando `FLUSH LOGS SQL`. Após o primeiro backup completo, os backups incrementais subsequentes são feitos usando o utilitário mysqladmin com o comando `flush-logs`, que cria o próximo arquivo de log.

Consulte [Resumo da Estratégia de Backup](https://dev.mysql.com/doc/refman/5.5/en/backup-strategy-summary.html).

```text
binlog_format=mixed
log-bin=logname
```

## Diretório raiz do armazenamento de conteúdo (somente Content Services) {#content-storage-root-directory-content-services-only}

O diretório raiz de armazenamento de conteúdo contém o repositório do Content Services (obsoleto), onde todos os documentos, artefatos e índices são armazenados. Deve ser feito backup da árvore de diretório raiz do armazenamento de conteúdo. Esta seção descreve como determinar o local do diretório raiz de armazenamento de conteúdo para ambientes independentes e em cluster.

### Local raiz do armazenamento de conteúdo (ambiente independente) {#content-storage-root-location-stand-alone-environment}

O diretório raiz do armazenamento de conteúdo é criado quando o Content Services (Deprecated) é instalado. O local do diretório raiz do armazenamento de conteúdo é determinado durante o processo de instalação dos formulários AEM.

O local padrão para o diretório Raiz de Armazenamento de Conteúdo é `[aem-forms root]/lccs_data`.

Faça backup dos seguintes diretórios no diretório raiz do armazenamento de conteúdo:

/audit.contentstore

/contentstore

/contentstore.deleted

/backup-lucene-indexes

Se o diretório /backup-lucene-indexes não estiver presente, faça backup do diretório /lucene-indexes, também no diretório raiz de armazenamento de conteúdo. Se o diretório /backup-lucene-indexes estiver presente, não faça backup do diretório /lucene-indexes porque isso pode causar erros.

### Local raiz do armazenamento de conteúdo (ambiente em cluster) {#content-storage-root-location-clustered-environment}

Quando você instala o Content Services (Obsoleto) em um ambiente em cluster, o diretório raiz do armazenamento de conteúdo é dividido em dois diretórios separados:

**Diretório Raiz de Armazenamento de Conteúdo:** Geralmente, é um diretório de rede compartilhado acessível para leitura/gravação para todos os nós do cluster

**Diretório Raiz do Índice:** Um diretório criado em cada nó do cluster, sempre com o mesmo caminho e nome de diretório

O local padrão para o diretório Raiz de Armazenamento de Conteúdo é `[GDS root]/lccs_data`, onde `[GDS root]` é o local descrito em [Local GDS](files-back-recover.md#gds-location). Faça backup dos seguintes diretórios no diretório raiz do armazenamento de conteúdo:

/audit.contentstore

/contentstore

/contentstore.deleted

/backup-lucene-indexes

Se o diretório /backup-lucene-indexes não estiver presente, faça backup do diretório /lucene-indexes, também no diretório raiz de armazenamento de conteúdo. Se o diretório /backup-lucene-indexes estiver presente, não faça backup do diretório /lucene-indexes porque isso pode causar erros.

O local padrão para o diretório Raiz do Índice é `[aem-forms root]/lucene-indexes` em cada nó.

## Fontes instaladas pelo cliente {#customer-installed-fonts}

Se você instalou fontes adicionais no ambiente do AEM Forms, é necessário fazer backup delas separadamente. Faça backup de todos os diretórios de fontes do Adobe e do cliente especificados no console de administração em Configurações > Sistema principal > Configurações. Certifique-se de fazer backup de todo o diretório de fontes.

>[!NOTE]
>
>Por padrão, as fontes do Adobe instaladas com o AEM Forms estão no diretório `[aem-forms root]/fonts`.

Se você estiver reinicializando o sistema operacional no computador host e quiser usar fontes do sistema operacional anterior, o conteúdo do diretório de fontes do sistema também deverá ser submetido a backup. (Para obter instruções específicas, consulte a documentação do seu sistema operacional).
