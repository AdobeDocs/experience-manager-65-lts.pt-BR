---
title: Execução de uma atualização no local
description: Saiba como executar uma atualização no local para o AEM 6.5 LTS.
topic-tags: upgrading
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: c7351625-b29e-45a7-b966-e7c0f56d4f22
source-git-commit: db9bf14ec9fefcbafb7b6d749de966e97c54abda
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Execução de uma atualização no local {#performing-an-in-place-upgrade}

>[!NOTE]
>
>Esta página descreve o procedimento de atualização no local do AEM 6.5 LTS. Se você tiver uma instalação implantada em um servidor de aplicativos, consulte [Etapas de Atualização para Instalações do Servidor de Aplicativos](/help/sites-deploying/app-server-upgrade.md).

## Etapas de pré-atualização {#pre-upgrade-steps}

Antes de executar a atualização, há várias etapas que devem ser concluídas. Consulte [Atualizando Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md) e [Tarefas de Manutenção de Pré-Atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) para obter mais informações. Além disso, verifique se o seu sistema atende aos [requisitos do AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md) e veja as [considerações de planejamento de atualização](/help/sites-deploying/upgrade-planning.md) e como o [Analyzer](/help/sites-deploying/pattern-detector.md) pode ajudá-lo a estimar a complexidade.

<!--Finally, the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Pré-requisitos de migração {#migration-prerequisites}

* **Versão mínima do Java necessária:** verifique se o Java™ 17 da Oracle está instalado no sistema.

## Preparação do arquivo jar do AEM Quickstart {#prep-quickstart-file}

1. Baixe o novo arquivo jar do AEM 6.5 LTS

1. [Determine o comando de início de atualização correto](#determining-the-correct-upgrade-start-command)

1. Pare a instância se ela estiver em execução

1. Use o novo jar do AEM 6.5 LTS para substituir o antigo fora da pasta `crx-quickstart`

1. Faça um backup do arquivo `sling.properties` (geralmente presente no `crx-quickstart/conf/`) e exclua-o

1. Descompacte o novo jar de início rápido executando:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

1. O comando unpack gerará um novo arquivo `sling.properties` na pasta `crx-quickstart/conf/`. Agora você pode aplicar suas alterações personalizadas ao arquivo `sling.properties` recém-gerado.

<!-- Alexandru: drafting temporarily

## Content Repository Migration {#content-repository-migration}

This migration is not required if you are upgrading from AEM 6.3. For versions older than 6.3, Adobe provides a tool that can be used to migrate the repository to the new version of the Oak Segment Tar present in AEM 6.3. It is provided as part of the quickstart package and is mandatory for any upgrades that will be using TarMK. Upgrades for environments that are using MongoMK do not require repository migration. For more information on what the benefits of the new Segment Tar format are, see the [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

The actual migration is performed using the standard AEM quickstart jar file, executed with a new `-x crx2oak` option which executes the crx2oak tool to simplify the upgrade and make it more robust.

>[!NOTE]
>
>If you are performing TarMK repository content migration using the CRX2Oak Quickstart extension, you might remove the **samplecontent** runmode by adding the following to the migration command line:
>
>* `--promote-runmode nosamplecontent`
>

To determine the command that you should run, use the following command:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Where `<<YOUR_PROFILE>>` and `<<ADDITIONAL_FLAGS>>` are replaced with the profile and flags listed in the following table:

<table>
 <tbody>
  <tr>
   <td><strong>Source Repository</strong></td>
   <td><strong>Target Repository</strong></td>
   <td><strong>Profile</strong></td>
   <td><strong>Additional Flags</strong><br /> </td>
  </tr>
  <tr>
   <td>crx2 or TarMK with <code>FileDataStore</code></td>
   <td>TarMK</td>
   <td>segment-fds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>crx2</td>
   <td>MongoMK</td>
   <td>mongo-from-crx2 </td>
   <td><code>-T mongo-uri=mongo://mongo-host:mongo-port -T mongo-db=mongo-database-name</code></td>
  </tr>
  <tr>
   <td>TarMK or crx2 with <code>S3DataStore</code></td>
   <td>TarMK</td>
   <td>segment-custom-ds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>TarMK with no datastore</td>
   <td>TarMK</td>
   <td>segment-no-ds</td>
   <td> </td>
  </tr>
  <tr>
   <td>MongoMK</td>
   <td>MongoMK</td>
   <td>No migration is needed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

**Where:**

* `mongo-host` is the MongoDB server IP (for example, 127.0.0.1)

* `mongo-port` is the MongoDB server port (for example: 27017)

* `mongo-database-name` represents the name of the database (for example: aem-author)

**You may also require additional switches for the following scenarios:**

* If you are performing the upgrade on a Windows system where Java memory mapping is not handled correctly, add the `--disable-mmap` parameter to the command.

For additional instructions on using the crx2oak tool, see Using the [CRX2Oak Migration Tool](/help/sites-deploying/using-crx2oak.md). The crx2oak helper JAR can be manually upgraded if needed, by manually replacing it with newer versions after unpacking the quickstart. Its location in the AEM installation folder is: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. The newest version of the CRX2Oak migration tool is available for download from the Adobe Repository at: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

If the migration has completed successfully, the tool will exit with an exit code of zero. Additionally, check for WARN and ERROR messages in the `upgrade.log` file, located under `crx-quickstart/logs` in the AEM installation directory, as these could indicate non-fatal errors that occurred during the migration.

Check the configuration files beneath `crx-quickstart/install` folder. If a migration was necessary these will be updated to reflect the target repository.

**A note on datastores:**

While `FileDataStore` is the new default for AEM 6.3 installations, using an external datastore is not required. While using an external datastore is recommended as a best practice for production deployments, it is not a prerequisite to upgrade. Due to the complexity already present in upgrading AEM, Adobe recommends performing the upgrade without doing a datastore migration. If desired, a datastore migration can be executed afterwards as a separate effort.

## Troubleshooting Migration Issues {#troubleshooting-migration-issues}

Skip this section if you are upgrading from 6.3. While the provided crx2oak profiles should meet the needs of most customers, there are times when additional parameters will be necessary. If you run into an error during your migration, it is possible that there are aspects of your environment that require additional configuration options to be provided. If so, you will likely encounter the following error:

**Checkpoints are not copied, because no external datastore has been specified. This will result in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info.**

For some reason, the migration process needs access to binaries in the datastore and is unable to find it. To specify your datastore configuration, include the following flags in the `<<ADDITIONAL_FLAGS>>` portion of your migration command:

**For S3 datastores:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Where `/path/to/SharedS3DataStore.config` represents the path to your S3 datastore config file and `/path/to/datastore` represents the path to your S3 datastore.

**For File datastores:**

```shell
--src-datastore=/path/to/datastore
```

Where `/path/to/datastore` represents the path to your File Datastore.

-->

## Execução Da Atualização {#performing-the-upgrade}

**Se estiver usando S3:**

1. Remova os jars abaixo de `crx-quickstart/install` associados a uma versão anterior do conector S3.

1. Baixe a versão mais recente do conector S3 1.60.2 de [https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) <!-- Alexandru: this is a stub link for now -->

1. Extraia o conector S3 (versão 1.60.2) e copie o conteúdo das seguintes pastas em `crx-quickstart/install`, da seguinte maneira:

   1. Copiar `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/1` em `crx-quickstart/install/1`
   1. Copiar `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/15` em `crx-quickstart/install/15`

Agora, inicie a instância do AEM usando o novo comando determinado usando as informações na seção [Determinando o comando de início de atualização correto](#determining-the-correct-upgrade-start-command).

### Determinando o comando de início de atualização correto {#determining-the-correct-upgrade-start-command}

>[!NOTE]
>
>O suporte para alguns argumentos do Java 8/11 foi removido no Java 17, consulte [Documentos do Oracle Java™ 17](https://docs.oracle.com/en/java/javase/17/docs/specs/man/java.html) e [Considerações sobre argumentos Java&amp;trade do AEM 6.5 LTS](/help/sites-deploying/custom-standalone-install.md#java-17-considerations-java-considerations).

Para executar a atualização, é importante iniciar o AEM usando o arquivo jar para ativar a instância.

Observe que iniciar o AEM a partir do script de inicialização não iniciará a atualização. A maioria dos clientes inicia o AEM usando o script de inicialização e personaliza esse script de inicialização para incluir switches para configurações de ambiente, como configurações de memória, certificados de segurança etc. Por esse motivo, a Adobe recomenda seguir esse procedimento para determinar o comando de atualização adequado:

1. Em uma instância do AEM em execução, execute o seguinte a partir da linha de comando:

   ```shell
   ps -ef | grep java
   ```

1. Procure o processo do AEM. Será semelhante a:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.5.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Modifique o comando substituindo o caminho para o jar existente ( `crx-quickstart/app/aem-quickstart*.jar` neste caso) pelo novo jar do AEM 6.5 LTS que é irmão da pasta `crx-quickstart`. Usando nosso comando anterior como exemplo, nosso comando seria:

   ```shell
   /usr/bin/java -server -Xmx4096m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar <AEM-6.5-LTS.jar> -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Isso garantirá que todas as configurações apropriadas de memória, modos de execução personalizados e outros parâmetros ambientais sejam aplicados para a atualização. Após a conclusão da atualização, a instância poderá ser iniciada a partir do script de inicialização em inicializações futuras.

## Implantar Base De Código Atualizada {#deploy-upgraded-codebase}

Depois que o processo de atualização no local for concluído, a base de código atualizada deverá ser implantada. As etapas para atualizar a base de código para funcionar na versão de destino do AEM podem ser encontradas na [página Atualizar Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md).

## Executar Verificações Pós-Upgrade e Solução de Problemas {#perform-post-upgrade-check-troubleshooting}

Consulte [Solução de problemas e verificações pós-atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
