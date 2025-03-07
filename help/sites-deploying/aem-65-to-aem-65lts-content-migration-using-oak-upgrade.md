---
title: Migração de conteúdo do AEM 6.5 para o AEM 6.5 LTS usando a atualização do Oak
description: Saiba como migrar conteúdo do AEM 6.5 para o AEM 6.5 LTS usando a ferramenta oak-upgrade
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 8c4ffb0e-b4dc-4a81-ac43-723754cbc0de
source-git-commit: 9bf502146a309cd0d91f2aaa1778d5b550d424a8
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Migração de conteúdo do AEM 6.5 para o AEM 6.5 LTS usando a atualização do Oak {#aem-65-to-aem-65lts-content-migration-using-oak-upgrade}

Este documento fornece um guia abrangente para atualizar o Adobe Experience Manager da versão **6.5** para a **6.5 LTS**, com foco na migração do repositório de conteúdo usando a ferramenta oak-upgrade, um utilitário avançado para transferir conteúdo entre repositórios diferentes com precisão e controle.

## Pré-requisitos {#prerequisites}

Antes de iniciar a migração, verifique se os seguintes requisitos foram atendidos:

1. Compatibilidade com Java: o AEM 6.5 LTS deve ser instalado e configurado para ser executado com o Java™ 17. Depois de configurado, inicie a instância do AEM e verifique se todos os pacotes estão ativos e em execução sem problemas
1. Recursos do sistema: verifique se há espaço em disco e memória adequados disponíveis para lidar com ambos os repositórios durante o processo de migração
1. Ferramenta Oak-upgrade: baixe o jar `oak-upgrade` do [repositório Maven oficial](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade). Verifique se a versão corresponde à versão do oak-core usada no AEM 6.5 LTS. A ferramenta de atualização da Oak é executada no Oracle® Java™ 11 ou posterior

## Processo de migração passo a passo {#step-by-step-migration-process}

### Interrupção do AEM 6.5 e AEM 6.5 LTS {#stopping-aem65-and-aem65lts}

Antes de iniciar a migração, pare as instâncias do AEM 6.5 e do AEM 6.5 LTS. Isso garante que o repositório esteja em um estado estável e que não ocorram gravações adicionais durante a migração.

### Backup da instância do AEM 6.5 {#backing-up-the-aem65-instance}

Faça um backup completo da instância do AEM 6.5 se ainda não tiver sido feito.

### Uso da ferramenta Oak-upgrade para migração de conteúdo {#using-the-oak-upgrade-tool-for-content-migration}

A ferramenta Oak-Upgrade é executada por meio da linha de comando, conforme mostrado aqui:

```
java -jar oak-upgrade-*.jar [options] /path/to/source/repository /path/to/destination/repository 
```

Abaixo estão os comandos e opções essenciais:

**Opções de Chave**

* `--include-paths`: especifique subárvores para incluir na migração. Consulte este exemplo para obter o uso do comando:

  ```
  java -jar oak-upgrade-*.jar --include-paths=/content/site /old/repository /new/repository
  ```

* `--exclude-paths`: Excluir caminhos específicos da migração. Tenha cuidado ao usar essa opção; se o caminho existir no sistema de destino, ele será removido. Consulte este exemplo para obter o uso do comando:

  ```
  java -jar oak-upgrade-*.jar --exclude-paths=/content/old_site /old/repository /new/repository 
  ```

* `--copy-binaries`: por padrão, o oak-upgrade migra somente referências a binários, deixando os arquivos reais no blob/armazenamento de dados original. Como resultado, o novo repositório ainda depende do armazenamento de origem para binários. Para migrar binários junto com o conteúdo do repositório, use o parâmetro `--copy-binaries` para copiar todos os dados binários para o novo repositório, conforme mostrado abaixo:

  ```
  java -jar oak-upgrade-*.jar \
  --copy-binaries \
  --src-datastore=/old/repository/datastore \
  --datastore=/new/repository/datastore \
  /old/repository \
  /new/repository 
  ```

### Migrando pontos de verificação {#migratiing-checkpoints}

Ao migrar um repositório SegmentMK antigo (anterior ao Oak 1.6) para um novo SegmentMK (versão do Oak superior ou igual a 1.6), os pontos de verificação também são migrados. Isso permite que a reindexação seja evitada quando o Oak estiver sendo executado pela primeira vez no novo repositório. No entanto, os pontos de verificação não serão migrados nos seguintes casos:

1. Os caminhos de inclusão, exclusão ou mesclagem personalizados são especificados ou
1. Os binários são copiados por referências, nenhum armazenamento de dados de origem é especificado e dois pontos de verificação diferentes contêm um binário diferente no mesmo caminho.

No segundo caso, o oak-upgrade emite o seguinte aviso e interrompe:

```
Checkpoints won't be copied, because no external datastore has been specified. This will result in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info. 
```

A maneira mais fácil de corrigir esse problema é especificar o armazenamento de dados de origem nas opções de linha de comando (por exemplo, `--src-datastore` ou `--src-s3datastore`).

O aviso também pode ser ignorado, mas nesse caso, o repositório será totalmente reindexado na primeira inicialização. Pode ser um processo longo, especialmente para a grande instância. O repositório não poderá ser usado até que o processo de reindexação seja concluído. Use a opção `--skip-checkpoints` para suprimir o aviso.

Você também pode reindexar offline o repositório antes de iniciar o AEM usando [reindexação offline](/help/sites-deploying/upgrade-offline-reindexing.md) para evitar a reindexação completa na primeira inicialização.

Para obter mais informações sobre a ferramenta oak-upgrade e o uso avançado, consulte a [documentação oficial](https://jackrabbit.apache.org/oak/docs/migration.html).
