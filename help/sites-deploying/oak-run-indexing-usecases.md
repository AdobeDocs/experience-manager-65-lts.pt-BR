---
title: Casos de uso de indexação do Oak-run.jar
description: Saiba mais sobre os vários casos de usuário para executar a indexação com a ferramenta de execução do Oak.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
noindex: true
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: a7a8a20a-e513-43df-80b7-1e6daf957f20
source-git-commit: c714e51f0c0368988ce552969747ab5fce5c186f
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 0%

---

# Casos de uso de indexação do Oak-run.jar{#oak-run-jar-indexing-use-cases}

A execução do Oak suporta casos de uso de indexação na linha de comando sem precisar orquestrar a execução desses casos de uso por meio do console JMX da AEM.

Os benefícios abrangentes de usar a abordagem de comando de índice `oak-run.jar` para gerenciar índices Oak são os seguintes:

* O comando Oak-run index fornece um novo conjunto de ferramentas de indexação desde o lançamento do AEM 6.4.
* A execução da Oak diminui o tempo para reindexação, o que reduz os tempos de reindexação em repositórios maiores.
* A execução do Oak reduz o consumo de recursos durante a reindexação no AEM, resultando em um melhor desempenho geral do sistema.
* O Oak-run fornece reindexação fora da banda, situações de suporte em que a produção deve estar disponível e não pode tolerar manutenção ou tempo de inatividade necessário para reindexação.

As seções abaixo fornecem exemplos de comandos. O comando Oak-run index oferece suporte a todas as configurações de NodeStore e BlobStore. Os exemplos fornecidos abaixo são para configurações que têm FileDataStore e SegmentNodeStore.

## Caso de uso 1 — Verificação de consistência do índice {#usercase1indexconsistencycheck}

Esse caso de uso está relacionado à corrupção de índice. Às vezes, não era possível determinar quais dos índices estão corrompidos. Portanto, a Adobe forneceu ferramentas que:

* Executa verificações de consistência de índice em todos os índices e fornece um relatório sobre quais índices são válidos e quais não são válidos.
* A ferramenta é utilizável mesmo se o AEM não estiver acessível;
* É fácil de usar.

Use `--index-consistency-check` para verificar se há índices corrompidos:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Esta operação gera um relatório em `indexing-result/index-consistency-check-report.txt`. Consulte abaixo para obter um relatório de exemplo:

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### Benefícios {#uc1benefits}

Os administradores de suporte e sistema podem usar a ferramenta para identificar índices corrompidos rapidamente e reindexá-los.

## Caso de uso 2 — Estatísticas de índice {#usecase2indexstatistics}

Para diagnosticar alguns dos casos relacionados ao desempenho da consulta, a Adobe geralmente exigia a definição de índice existente e estatísticas relacionadas ao índice da configuração do cliente. Para facilitar a solução de problemas, a Adobe criou ferramentas que fazem o seguinte:

1. Despejar todas as definições de índice presentes no sistema em um único arquivo JSON;

1. Descartar estatísticas importantes de índices existentes;

1. Conteúdo do índice de despejo para análise offline;

1. Pode ser usado mesmo se o AEM não estiver acessível

Você pode executar as operações acima usando os seguintes comandos index:

* `--index-info` - Coleta e descarta várias estatísticas relacionadas aos índices

* `--index-definitions` - Coleta e descarta definições de índice

* `--index-dump` - Despeja o conteúdo do índice

Veja abaixo um exemplo de como os comandos funcionam na prática:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

Os relatórios serão gerados em `indexing-result/index-info.txt` e `indexing-result/index-definitions.json`

Além disso, os mesmos detalhes são fornecidos por meio do Console da Web e fariam parte do dump de configuração zip. Eles podem ser acessados no seguinte local:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Benefícios {#uc2benefits}

Essa ferramenta permite reunir rapidamente todos os detalhes necessários relacionados a problemas de indexação ou consulta e reduzir o tempo gasto na extração dessas informações.

## Caso de uso 3 — Reindexação {#usecase3reindexing}

Dependendo dos [cenários](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing), às vezes, a reindexação deve ser executada. Atualmente, você reindexa definindo o sinalizador `reindex` como `true` no nó de definição de índice usando o CRXDE ou a interface do usuário do Gerenciador de Índices. Depois de definir o sinalizador, a reindexação é executada de forma assíncrona. Depois que o sinalizador é definido, a reindexação é feita de forma assíncrona.

Alguns pontos a serem observados sobre a reindexação:

* A reindexação é muito mais lenta nas configurações de `DocumentNodeStore` em comparação às configurações de `SegmentNodeStore`, onde todo o conteúdo é local;

* Com o design atual, enquanto a reindexação acontece, o indexador assíncrono é bloqueado e todos os outros índices assíncronos se tornam obsoletos e não são atualizados durante a indexação. Consequentemente, se o sistema estiver em uso, os usuários podem não ver resultados atualizados;
* A reindexação envolve a passagem de todo o repositório, o que pode colocar uma carga alta na configuração do AEM e, portanto, afetar a experiência do usuário final;
* Para uma instalação `DocumentNodeStore` em que a reindexação pode demorar um tempo considerável, uma falha de conexão do banco de dados Mongo durante a operação pode interromper a indexação. Nesse caso, você deve reiniciar a indexação do zero.


* Às vezes, a reindexação pode demorar muito tempo devido à extração de texto. Esse problema pode ocorrer quando é específico para configurações que têm muitos arquivos PDF, em que o tempo gasto na extração de texto pode afetar o tempo de indexação.

Para atender a esses objetivos, a ferramenta de indexação executada pela Oak oferece suporte a diferentes modos de reindexação, que podem ser usados conforme necessário. O comando Oak-run index oferece os seguintes benefícios:

* **reindexação fora de banda** - a reindexação executada pela Oak pode ser feita separadamente de uma configuração do AEM em execução e, portanto, minimiza o impacto na instância do AEM que está em uso;

* **reindexação fora do plano** - A reindexação ocorre sem afetar as operações de indexação. O indexador assíncrono pode continuar a indexar outros índices;

* **Reindexação simplificada para instalações do DocumentNodeStore** - Para `DocumentNodeStore` instalações, a reindexação pode ser feita com um único comando que garante que a reindexação seja feita da melhor maneira;

* **Oferece suporte à atualização de definições de índice e à introdução de novas definições de índice**

### Reindexar - DocumentNodeStore {#reindexdocumentnodestore}

Para instalações do `DocumentNodeStore`, é possível executar a reindexação usando um único comando Oak-run:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Essa operação oferece os seguintes benefícios:

* Impacto mínimo na execução de instâncias do AEM. A maioria das leituras pode ser feita em servidores secundários e a execução de caches do AEM não é afetada negativamente devido a toda a travessia necessária para reindexação;
* Os usuários também podem fornecer um JSON de um índice novo ou atualizado por meio da opção `--index-definitions-file`.

### Reindexar - SegmentNodeStore {#reindexsegmentnodestore}

Para `SegmentNodeStore` instalações, a reindexação pode ser feita de uma das seguintes maneiras:

#### Reindexação online - SegmentNodeStore {#onlinereindexsegmentnodestore}

Siga a maneira estabelecida em que a reindexação é feita definindo o sinalizador `reindex`.

#### Reindexação online - SegmentNodeStore - A instância do AEM está em execução {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

Para instalações do `SegmentNodeStore`, somente um processo pode acessar arquivos de segmento no modo leitura-gravação. Dessa forma, algumas operações na indexação executada pela Oak exigem a execução de etapas manuais adicionais envolvendo o seguinte:

1. Texto da etapa.
1. Conecte o `oak-run` ao mesmo repositório usado pelo AEM no modo somente leitura.
1. Execute a indexação usando o seguinte exemplo:

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Finalmente, importe os arquivos de índice criados por meio da operação `IndexerMBean#importIndex` do caminho em que o Oak-run salvou os arquivos de indexação após executar o comando acima.

Nesse cenário, não é necessário interromper o servidor do AEM ou provisionar nenhuma nova instância. No entanto, como a indexação envolve a passagem de todo o repositório, isso aumentaria a carga de I/O na instalação, afetando negativamente o desempenho do tempo de execução.

#### Reindexação online - SegmentNodeStore - A instância do AEM foi encerrada {#onlinereindexsegmentnodestoreaeminstanceisdown}

Para instalações do `SegmentNodeStore`, é possível executar a reindexação usando um único comando Oak-run. No entanto, a instância do AEM deve ser encerrada.

Você pode acionar a reindexação com o seguinte comando:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

A diferença entre essa abordagem e a explicada acima é que a criação de pontos de verificação e a importação de índice são feitas automaticamente. A desvantagem é que o AEM deve estar inativo durante o processo.

#### Reindexação fora de banda - SegmentNodeStore {#outofbandreindexsegmentnodestore}

Nesse caso de uso, é possível executar a reindexação em uma configuração clonada para minimizar o impacto na instância do AEM em execução:

1. Crie um ponto de verificação por meio de uma operação JMX. Vá para o [Console JMX](/help/sites-administering/jmx-console.md) e procure por `CheckpointManager`. Em seguida, clique na operação **createCheckpoint(long p1)** usando um valor alto para expiração em segundos (por exemplo, **2592000**).
1. Copie a pasta `crx-quickstart` para uma nova máquina.
1. Execute a reindexação por meio do comando Oak-run index.

1. Copie os arquivos de índice gerados em um servidor do AEM.

1. Importe os arquivos de índice por meio do JMX.

Nesse caso de uso, o Armazenamento de Dados deve ser acessível de outra instância, o que pode não ser possível quando `FileDataStore` reside em uma solução de armazenamento baseada em nuvem, como EBS. Essa situação exclui o cenário em que `FileDataStore` também é clonado. Se a definição do índice não executar a indexação de texto completo, o acesso a `DataStore` não será necessário.

## Caso de uso 4 - Atualização das definições de índice {#usecase4updatingindexdefinitions}

Atualmente, você pode enviar alterações de definição de índice por meio do pacote [ACS Verificar Índice](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html). Você pode enviar as definições de índice em um pacote de conteúdo e, em seguida, executar a reindexação definindo o sinalizador `reindex` como `true`.


Isso funciona bem em instalações menores em que a reindexação não leva muito tempo. No entanto, para repositórios grandes, a reindexação é feita em uma quantidade de tempo consideravelmente maior. Para esses casos, agora é possível usar a ferramenta de indexação executada pela Oak.

A execução do Oak agora é compatível com o fornecimento de definições de índice no formato JSON e a criação de índice no modo fora de banda, em que nenhuma alteração é executada em uma instância ativa.

O processo a ser considerado neste caso de uso é o seguinte:

1. Um desenvolvedor atualiza as definições de índice em uma instância local e gera um arquivo JSON de definição de índice por meio da opção `--index-definitions`.
1. O JSON atualizado é fornecido ao Administrador do sistema.
1. O administrador do sistema segue a abordagem out-of-band e prepara o índice para uma instalação diferente.
1. Quando concluídos, os arquivos de índice gerados são importados em uma instalação do AEM em execução.
