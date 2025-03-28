---
title: Procedimento de atualização
description: Saiba mais sobre o procedimento para atualizar o Adobe Experience Manager (AEM).
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: ae78421de75518894f3996829e554acd9003a6d1
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---

# Procedimento de atualização {#upgrade-procedure}

>[!NOTE]
>
>A atualização requer tempo de inatividade para a camada Autor, pois a maioria das atualizações do Adobe Experience Manager (AEM) é executada no local. Seguindo essas práticas recomendadas, você pode minimizar ou eliminar o tempo de inatividade do nível de publicação.

Ao atualizar os ambientes do AEM, você deve considerar as diferenças na abordagem entre atualizar os ambientes do autor ou de publicação para minimizar o tempo de inatividade dos autores e usuários finais. Esta página descreve o procedimento de alto nível para atualizar uma topologia do AEM atualmente em execução em uma versão do AEM 6.x. Como o processo difere entre os níveis de criação e publicação e implantações baseadas em Mongo e TarMK, cada nível e microkernel foi listado em uma seção separada. Ao executar a implantação, a Adobe recomenda primeiro atualizar o ambiente do autor, determinar o sucesso e prosseguir para os ambientes de publicação.

<!--
>[!IMPORTANT]
>
>The downtime during the upgrade can be significally reduced by indexing the repository before performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)
-->

## Camada de autor TarMK {#tarmk-author-tier}

### Topologia Inicial {#starting-topology}

A topologia presumida para esta seção consiste em um servidor de Autores em execução no TarMK com um Modo de Espera a Frio. A replicação ocorre do servidor do autor para o farm de publicação TarMK. Embora não ilustrada aqui, essa abordagem também pode ser usada para implantações que usam descarga. Atualize ou recrie a instância de descarregamento na nova versão após desabilitar os agentes de replicação na instância do autor e antes de habilitá-los novamente.

![tarmk_starting_topology](assets/tarmk_starting_topology.jpg)

### Preparação de atualização {#upgrade-preparation}

![autor-preparação-atualização](assets/upgrade-preparation-author.png)

1. Interrompa a criação de conteúdo.

1. Interrompa a instância standby.

1. Desative os agentes de replicação no autor.

1. Execute as [tarefas de manutenção de pré-atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md).

### Execução de atualização {#upgrade-execution}

![executar_atualização](assets/execute_upgrade.jpg)

1. Execute a [atualização no local](/help/sites-deploying/in-place-upgrade.md).
1. Atualize o módulo Dispatcher *se necessário*.

1. O controle de qualidade valida a atualização.

1. Desligue a instância do autor.

### Se bem-sucedido {#if-successful}

![if_successful](assets/if_successful.jpg)

1. Copie a instância atualizada para criar um Modo de Espera Restrito.

1. Inicie a instância do Autor.

1. Inicie a instância Stand-by.

### Se Não Tiver Êxito (Reversão) {#if-unsuccessful-rollback}

![reversão](assets/rollback.jpg)

1. Inicie a instância do Modo de Espera Off-line como o novo Principal.

1. Recrie o ambiente do Autor a partir do Modo de Espera por Frio.

## Cluster de autores do MongoMK {#mongomk-author-cluster}

### Topologia Inicial {#starting-topology-1}

A topologia presumida para esta seção consiste em um cluster de Autores MongoMK com pelo menos duas instâncias de Autor do AEM, apoiadas por pelo menos dois bancos de dados MongoMK. Todas as instâncias de Autor compartilham um armazenamento de dados. Essas etapas devem se aplicar aos armazenamentos de dados S3 e File. A replicação ocorre dos servidores do autor para o farm de publicação TarMK.

![topologia-mongo](assets/mongo-topology.jpg)

### Preparação de atualização {#upgrade-preparation-1}

![mongo-upgrade_prep](assets/mongo-upgrade_prep.jpg)

1. Interrompa a criação de conteúdo.
1. Clonar o armazenamento de dados para backup.
1. Interrompa todas as instâncias de autor do AEM, exceto uma instância de autor principal.
1. Remova todos os nós MongoDB, exceto um do conjunto de réplicas, sua instância Mongo primária.
1. Atualize o arquivo `DocumentNodeStoreService.cfg` no Autor principal para refletir seu único conjunto de réplicas membro.
1. Reinicie o Author principal para garantir que ele seja reiniciado corretamente.
1. Desative os agentes de replicação no autor principal.
1. Execute [tarefas de manutenção de pré-atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) na instância de Autor primária.

### Execução de atualização {#Upgrade-execution-1}

![execução-mongo](assets/mongo-execution.jpg)

1. Execute uma [atualização no local](/help/sites-deploying/in-place-upgrade.md) no Autor principal.
1. Atualize o Dispatcher ou o Módulo Web *se necessário*.
1. O controle de qualidade valida a atualização.

### Se bem-sucedido {#if-successful-1}

![mongo-secondaries](assets/mongo-secondaries.jpg)

1. Crie novas instâncias do Autor do AEM 6.5 LTS, conectadas à instância Mongo atualizada.

1. Recrie os nós MongoDB que foram removidos do cluster.

1. Atualize os arquivos `DocumentNodeStoreService.cfg` para refletir o conjunto de réplicas completo.

1. Reinicie as instâncias do Autor, uma de cada vez.

1. Remova o armazenamento de dados clonado.

### Se Não Tiver Êxito (Reversão)  {#if-unsuccessful-rollback-2}

![reversão mongo](assets/mongo-rollback.jpg)

1. Reconfigure as instâncias secundárias do Autor para se conectarem ao armazenamento de dados clonado.

1. Desligue a instância primária do autor atualizada.

1. Desligue a instância primária do Mongo atualizada.

1. Inicie as instâncias secundárias do Mongo com uma delas como a nova primária.

1. Configure os arquivos `DocumentNodeStoreService.cfg` nas instâncias secundárias do Autor para apontar para o conjunto de réplicas das instâncias Mongo ainda não atualizadas.

1. Inicie as instâncias secundárias do Autor.

1. Limpe as instâncias do autor atualizadas, o nó Mongo e o armazenamento de dados.

## Farm de publicação do TarMK {#tarmk-publish-farm}

### Farm de publicação do TarMK {#tarmk-publish-farm-1}

A topologia assumida para esta seção consiste em duas instâncias de publicação TarMK, lideradas pelos Dispatchers que, por sua vez, são liderados por um balanceador de carga. A replicação ocorre do servidor do autor para o farm de publicação TarMK.

![tarmk-pub-farmv5](assets/tarmk-pub-farmv5.png)

### Execução de atualização {#upgrade-execution-2}

![publicação-atualização2](assets/upgrade-publish2.png)

1. Pare o tráfego para a instância de Publicação 2 no balanceador de carga.
1. Execute a [manutenção de pré-atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) na Publicação 2.
1. Execute uma [atualização no local](/help/sites-deploying/in-place-upgrade.md) na Publicação 2.
1. Atualize o Dispatcher ou o Módulo Web *se necessário*.
1. Limpe o cache do Dispatcher.
1. O controle de qualidade valida a Publicação 2 pela Dispatcher, atrás do firewall.
1. Desligar Publicação 2.
1. Copie a instância Publish 2.
1. Iniciar publicação 2.

### Se bem-sucedido {#if-successful-2}

![publicação-atualização1](assets/upgrade-publish1.png)

1. Ative o tráfego para a Publicação 2.
1. Interromper o tráfego para a Publicação 1.
1. Interrompa a instância do Publish 1.
1. Substitua a instância de Publicação 1 por uma cópia de Publicação 2.
1. Atualize o Dispatcher ou o Módulo Web *se necessário*.
1. Limpe o cache do Dispatcher para Publicar 1.
1. Iniciar publicação 1.
1. O controle de qualidade valida a Publicação 1 pela Dispatcher, atrás do firewall.

### Se Não Tiver Êxito (Reversão) {#if-unsuccessful-rollback-1}

![reversão_do_pub](assets/pub_rollback.jpg)

1. Criar uma cópia de Publicar 1.
1. Substitua a instância de Publicação 2 por uma cópia de Publicação 1.
1. Limpe o cache do Dispatcher para o Publish 2.
1. Iniciar publicação 2.
1. O controle de qualidade valida a Publicação 2 pela Dispatcher, atrás do firewall.
1. Ative o tráfego para a Publicação 2.

## Etapas finais de atualização {#final-upgrade-steps}

1. Ative o tráfego para Publicar 1.
1. O controle de qualidade executa a validação final de um URL público.
1. Ative os agentes de replicação no ambiente do Autor.
1. Retomar a criação de conteúdo.
1. Executar [verificações pós-atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).

![final](assets/final.jpg)
