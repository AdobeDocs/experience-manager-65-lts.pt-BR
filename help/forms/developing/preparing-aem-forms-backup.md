---
title: Preparando o AEM Forms para backup
description: Saiba como usar o serviço de Backup e restauração para entrar e sair do modo de Backup do servidor do AEM Forms usando a API do Java e a API do serviço da Web.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromtoc: true
exl-id: 0fe1aef7-f607-4c40-bfa9-9ec9ebd8abeb
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '2484'
ht-degree: 0%

---

# Preparando o AEM Forms para backup {#preparing-aem-forms-for-backup}

**Exemplos e exemplos neste documento são somente para AEM Forms no ambiente JEE.**

## Sobre o Serviço de Backup e Restauração {#about-the-backup-and-restore-service}

O serviço de Backup e Restauração permite colocar o AEM Forms no *modo de backup*, que permite a execução de backups dinâmicos. O serviço de Backup e Restauração não executa realmente um backup do AEM Forms ou restaura o sistema. Em vez disso, ele coloca o servidor em um estado para backups consistentes e confiáveis, permitindo que ele continue a ser executado. Você é responsável pelas ações de backup do Armazenamento Global de Documentos (GDS) e do banco de dados conectado ao Servidor do Forms. O GDS é um diretório usado para armazenar arquivos usados em um processo de longa vida.

O modo de backup é um estado que o servidor insere para que os arquivos no GDS não sejam removidos enquanto um procedimento de backup estiver ocorrendo. Em vez disso, os subdiretórios são criados no diretório GDS para manter um registro de arquivos a serem removidos após o término do modo de backup salvo. Um arquivo é destinado a sobreviver às reinicializações do sistema e pode se estender por dias ou até anos. Esses arquivos são uma parte essencial do estado geral do Forms Server e podem incluir arquivos PDF, políticas ou modelos de formulário. Se algum desses arquivos for perdido ou for corrompido, os processos no servidor do Forms podem se tornar instáveis e os dados podem ser perdidos.

Você pode optar por executar backups de snapshot, nos quais você normalmente entraria no modo de backup por um período e deixaria o modo de backup após concluir suas atividades de backup. É necessário sair do modo de backup para que os arquivos possam ser removidos do GDS, a fim de garantir que eles não cresçam desnecessariamente grandes. Você pode deixar o modo de backup explicitamente ou aguardar o tempo para expirar em uma sessão do modo de backup.

Você também pode deixar o servidor no modo de backup permanente, o que é típico para estratégias de backup contínuas ou backups contínuos ou cobertura contínua do sistema. O modo de backup contínuo indica que o sistema está sempre no modo de backup, com uma nova sessão de modo de backup iniciada assim que a sessão anterior é lançada. Quando estiver no modo de backup contínuo, um arquivo é removido após duas sessões de modo de backup e não é mais referenciado.

Você pode usar o serviço de Backup e Restauração para adicionar aplicativos existentes ou novos aplicativos que você cria para executar backups do GDS ou do banco de dados conectado ao Forms Server.

>[!NOTE]
>
>Como em qualquer outro aspecto da implementação do AEM Forms, sua estratégia de backup e recuperação deve ser desenvolvida e testada em um ambiente de desenvolvimento ou de preparo antes de ser usada na produção, para garantir que toda a solução funcione como esperado sem perda de dados.

Você pode executar essas tarefas usando o serviço de Backup e Restauração:

* Entre no modo de backup.
* Sair do modo de backup.

>[!NOTE]
>
>Para obter mais informações sobre o que considerar ao executar backups do AEM Forms, consulte a [ajuda administrativa](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Para obter mais informações sobre o serviço de Backup e Restauração, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Entrando no modo de backup no servidor do Forms {#entering-backup-mode-on-the-forms-server}

Você entra no modo de backup para permitir backups dinâmicos de um Forms Server. Ao entrar no modo de backup, você especifica as seguintes informações com base nos procedimentos de backup de sua organização:

* Um rótulo exclusivo para identificar a sessão do modo de backup que pode ser útil para seus processos de backup.
* O tempo para a conclusão do procedimento de backup.
* Um sinalizador para indicar se deve estar no modo de backup contínuo, que é útil somente se você estiver executando backups contínuos.

Antes de gravar aplicativos para entrar no modo de backup, é recomendável compreender os procedimentos de backup que são usados depois que você coloca o Forms Server no modo de backup. Para obter mais informações sobre o que considerar ao executar backups do AEM Forms, consulte a [ajuda administrativa](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Para obter mais informações sobre o serviço de Backup e Restauração, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary-of-steps}

Para criar um aplicativo que entre no modo de backup, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto cliente BackupService.
1. Determine um rótulo exclusivo, a quantidade de tempo para executar o backup e se deve estar no modo de backup contínuo.
1. Entre no modo de backup.
1. (Opcional) Recupere informações sobre a sessão do modo de backup no servidor.
1. Faça o backup do GDS (Global Data Store) e do banco de dados.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. É importante incluir esses arquivos no projeto para compilar o código corretamente e usar a API do serviço de backup e restauração.

Para obter informações sobre o local desses arquivos, consulte [Incluindo arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Criar um objeto da API do Cliente BackupService**

Para sair programaticamente do modo de backup, você cria um objeto de cliente BackupService para usar a API de Serviço de Backup e Restauração.

**Decida sobre um rótulo exclusivo, determine o tempo de execução do backup e decida se deve estar no modo de backup contínuo**

Antes de entrar no modo de backup, você deve decidir um rótulo exclusivo, determinar o tempo que deseja alocar para executar o backup e decidir se deseja que o Forms Server permaneça no modo de backup. Essas considerações são importantes para a integração com os procedimentos de backup estabelecidos pela organização. (Consulte [ajuda administrativa](https://www.adobe.com/go/learn_aemforms_admin_63).)

**Entrar no modo de backup**

Entre no modo de backup com os parâmetros que são consistentes com os procedimentos de backup em sua organização.

**Recuperar informações sobre a sessão de modo de backup no servidor**

Depois de entrar no modo de backup, você pode recuperar informações sobre a sessão. Essas informações podem ser usadas para integração com seus procedimentos de backup

**Executar o backup do GDS e do banco de dados**

Depois de entrar no modo de backup com êxito, você pode fazer um backup do Armazenamento de Documentos Global (GDS) e do banco de dados ao qual o Servidor do Forms está conectado. Essa etapa é específica para sua organização, pois é possível executá-la manualmente ou executar outras ferramentas para executar o procedimento de backup.

### Entre no modo de backup usando a API Java {#enter-backup-mode-using-the-java-api}

Entre no modo de backup usando a API de serviço de backup e restauração:

1. Incluir arquivos de projeto

   Inclua os arquivos JAR necessários do cliente, como adobe-backup-restore-client-sdk.jar, no caminho de classe do projeto Java. Para criar o aplicativo cliente Java, os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (necessário se o AEM Forms for implantado no JBoss Application Server)
   * jbossall-client.jar (necessário se o AEM Forms for implantado no JBoss Application Server)

1. Criar um objeto da API do Cliente BackupService

   Você usa um objeto `ServiceClientFactory` e o objeto da API do cliente BackupService juntos.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão. (Consulte [Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Crie um objeto `BackupService` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Decida com base em um rótulo exclusivo, determine o tempo de execução do backup e decida se deve estar no modo de backup contínuo

   Decida com base em um rótulo exclusivo, determine o tempo que deseja alocar para executar o backup e decida se deseja que o Forms Server permaneça no modo de backup contínuo.

1. Entrar no modo de backup

   Entre no modo de backup invocando o método `enterBackupMode` com os seguintes parâmetros:

   * Um valor `String` que especifica um rótulo exclusivo legível por humanos que identifica a sessão de modo de backup. É recomendável não usar espaços ou caracteres que não possam ser codificados no formato XML.
   * Um valor `int` que especifica o número de minutos para permanecer no modo de backup. Você pode especificar um valor de `1` a `10080` (o número de minutos em uma semana). Esse valor é ignorado quando se usa o modo de backup contínuo.
   * Um valor `Boolean` que especifica se deve estar no modo de backup contínuo. Um valor de `True` especifica estar no modo de backup contínuo. Quando estiver no modo de backup contínuo, o valor especificado para o número de minutos a permanecer no modo de backup será ignorado.

     Modo de backup contínuo significa que uma nova sessão de modo de backup é iniciada depois que a atual é concluída. Um valor de `False` significa que o modo de backup contínuo não é usado e, após sair do modo de backup, a limpeza dos arquivos do GDS será retomada.

1. Recuperar informações sobre a sessão de modo de backup no servidor

   Recupere informações usando o objeto `BackupModeEntryResult` que é retornado após invocar o método `enterBackupMode`. As informações que você pode recuperar depois de entrar no modo de backup podem ser úteis para integração com seus procedimentos de backup. Por exemplo, o rótulo, a ID de backup e a hora de início podem ser úteis como entrada para nomes de arquivo para seu procedimento de backup.

1. Executar o backup do GDS e do banco de dados

   Faça backup do GDS (Global Document Storage, armazenamento global de documentos) e do banco de dados ao qual o servidor Forms está conectado. As ações para executar o backup não fazem parte do AEM Forms SDK e podem até incluir etapas manuais específicas para os procedimentos de backup em sua organização.

### Entre no modo de backup usando a API do serviço Web {#enter-backup-mode-using-the-web-service-api}

Entre no modo de backup usando o serviço Web fornecido pela API do Serviço de Backup e Restauração:

1. Incluir arquivos de projeto

   * Crie um assembly cliente Microsoft .NET que consuma o WSDL da API de Serviço de Backup e Restauração.
   * Referencie o assembly do cliente Microsoft .NET.

1. Criar um objeto da API do Cliente BackupService

   Usando o assembly do cliente Microsoft .NET, crie um objeto `BackupServiceService` invocando seu construtor padrão e especifique as credenciais usando o método `Credentials`.

1. Decida com base em um rótulo exclusivo, determine o tempo de execução do backup e decida se deve estar no modo de backup contínuo

   Decida com base em um rótulo exclusivo, determine o tempo que deseja alocar para executar o backup e decida se deseja que o Forms Server permaneça no modo de backup contínuo.

1. Entrar no modo de backup

   Para entrar no modo de backup, chame o método enterBackupMode e passe os seguintes valores:

   * Um valor `String` que especifica um rótulo exclusivo legível por humanos que identifica a sessão de modo de backup. É recomendável não usar espaços ou caracteres que não possam ser codificados no formato XML.
   * Um valor `Uint32` que especifica o número de minutos para permanecer no modo de backup. Você pode especificar um valor de `1` a `10080` (número de minutos em uma semana). Esse valor é ignorado quando se usa o modo de backup contínuo.
   * Um valor `Boolean` que especifica se deve estar no modo de backup contínuo. Um valor de `True` especifica estar no modo de backup contínuo. Quando estiver no modo de backup contínuo, o valor especificado para o número de minutos a permanecer no modo de backup será ignorado. Modo de backup contínuo significa que uma nova sessão de modo de backup é iniciada depois que a atual é concluída.

     Um valor de `False` significa que o modo de backup contínuo não é usado e, após sair do modo de backup, a limpeza dos arquivos do GDS será retomada.

1. Recuperar informações sobre a sessão de modo de backup no servidor

   Recupere informações sobre a sessão de modo de backup depois de chamar o método enterBackupMode a partir do BackupModeEntryResult que é retornado para verificar se foi bem-sucedido. As informações que você pode recuperar depois de entrar no modo de backup podem ser úteis para integração com seus procedimentos de backup. Por exemplo, o rótulo, a ID de backup e a hora de início podem ser úteis como entrada para nomes de arquivo para seu procedimento de backup.

1. Executar o backup do GDS e do banco de dados

   Faça backup do GDS (Global Document Storage, armazenamento global de documentos) e do banco de dados ao qual o servidor Forms está conectado. As ações para executar o backup não fazem parte do AEM Forms SDK e podem até incluir etapas manuais específicas para os procedimentos de backup em sua organização.

## Saindo do modo de backup no servidor do Forms {#leaving-backup-mode-on-the-forms-server}

Você deixa o modo de backup para que o Forms Server reinicie a limpeza dos arquivos do GDS (Global Document Storage, armazenamento global de documentos) no Forms Server.

Antes de gravar aplicativos para entrar no modo de licença, é recomendável compreender os procedimentos de backup usados com o AEM Forms. Para obter mais informações sobre o que considerar ao executar backups do AEM Forms, consulte a [ajuda administrativa](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Para obter mais informações sobre o serviço de Backup e Restauração, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-1}

Para sair do modo de backup, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto cliente BackupService.
1. Sair do modo de backup.
1. (Opcional) Recupere informações sobre a sessão do modo de backup que estava em execução no Forms Server.

**Incluir arquivos de projeto**

Inclua todos os arquivos necessários no projeto de desenvolvimento. Esses arquivos são importantes para a compilação adequada do código e para o uso da API do serviço de backup e restauração.

Para obter informações sobre o local desses arquivos, consulte [Incluindo arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Criar um objeto da API do Cliente BackupService**

Para sair programaticamente do modo de backup, você cria um objeto de cliente BackupService para usar a API de Serviço de Backup e Restauração.

**Sair do modo de backup**

Saia do modo de backup para retomar a limpeza normal dos arquivos do Armazenamento global de documentos (GDS). Antes de sair do modo de backup, verifique se os procedimentos de backup foram concluídos.

**Recuperar informações sobre a sessão de modo de backup que terminou**

Depois de sair do modo de backup, você pode recuperar informações sobre a sessão. Essas informações podem ser usadas para integração com seus procedimentos de backup.

### Sair do modo de backup usando a API Java {#leave-backup-mode-using-the-java-api}

Sair do modo de backup usando a API de serviço de backup e restauração (Java):

1. Incluir arquivos de projeto

   Inclua os arquivos JAR necessários do cliente, como adobe-backup-restore-client-sdk.jar, no caminho de classe do projeto Java. Para criar um aplicativo cliente Java, os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (necessário se o AEM Forms for implantado no JBoss Application Server)
   * jbossall-client.jar (necessário se o AEM Forms for implantado no JBoss Application Server)

1. Criar um objeto da API do Cliente BackupService

   Você usa um objeto `ServiceClientFactory` e o objeto da API do cliente BackupService juntos.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão. (Consulte [Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Crie um objeto `BackupService` usando seu construtor e transmitindo o objeto `ServiceClientFactory` como parâmetro.

1. Entrar no modo de backup

   Saia do modo de backup invocando o método `leaveBackupMode`.

1. Recuperar informações sobre a sessão de modo de backup no servidor

   Recupere informações sobre a operação usando o objeto `BackupModeResult` retornado. As informações que você pode recuperar depois de entrar no modo de backup podem ser úteis para integração com seus procedimentos de backup. Por exemplo, o rótulo, a ID de backup e a hora de início podem ser úteis como entrada para nomes de arquivo para seu procedimento de backup.

### Sair do modo de backup usando a API do serviço Web {#leave-backup-mode-using-the-web-service-api}

Sair do modo de backup usando a API de Serviço de Backup e Restauração (serviço da Web):

1. Incluir arquivos de projeto

   Para usar serviços da Web, você deve certificar-se de incluir os arquivos proxy. Siga estas etapas para configurar seu projeto para usar a API do Serviço de Backup e Restauração como um serviço Web.

   * Crie um assembly cliente Microsoft .NET que consuma o WSDL da API de Serviço de Backup e Restauração.
   * Referencie o assembly do cliente Microsoft .NET.

1. Criar um objeto da API do Cliente BackupService

   Usando o assembly do cliente Microsoft .NET, crie um objeto `BackupServiceService` invocando seu construtor padrão.

1. Entrar no modo de backup

   Saia do modo de backup invocando a operação do serviço Web `leaveBackupMode`.

1. Recuperar informações sobre a sessão de modo de backup no servidor

   Recupere o identificador de modo de backup após a operação para verificar se ela foi bem-sucedida. As informações que você pode recuperar depois de sair do modo de backup podem ser úteis para integração com seus procedimentos de backup.
