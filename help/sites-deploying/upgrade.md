---
title: Atualização para o Adobe Experience Manager 6.5
description: Saiba mais sobre as noções básicas para atualizar uma instalação mais antiga do Adobe Experience Manager (AEM) para o AEM 6.5.
contentOwner: sarchiz
topic-tags: upgrading
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: d4f89be13039e53564cd3a3148a4b845bcc183a7
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Atualização para o Adobe Experience Manager (AEM) 6.5 LTS {#upgrading-to-aem}

>[!NOTE]
>A atualização para o AEM 6.5 LTS é compatível com os últimos 6 Service packs.

Esta seção aborda a atualização de uma instalação do AEM para o AEM 6.5 LTS:

<!-- Alexandru: drafting for now 

* [Planning Your Upgrade](/help/sites-deploying/upgrade-planning.md)
* [Assessing the Upgrade Complexity with Pattern Detector](/help/sites-deploying/pattern-detector.md)
* [Backward Compatibility in AEM 6.5](/help/sites-deploying/backward-compatibility.md)
  This was drafted before: * [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

<!--
* [Upgrade Procedure](/help/sites-deploying/upgrade-procedure.md)
* [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Performing an In-Place Upgrade](/help/sites-deploying/in-place-upgrade.md)
* [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Sustainable Upgrades](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md)

-->

Para facilitar a referência às instâncias do AEM envolvidas nesses procedimentos, os termos a seguir são usados nesses artigos:

* A instância de *origem* é a instância do AEM da qual você está atualizando.
* A instância de *destino* é para a qual você está atualizando.

## O que mudou? {#what-has-changed}

### Atualizações {#updates}

A camada do Foundation agora é compatível com o Java 17, incorporando os pacotes de código aberto mais recentes do Apache Sling, Felix e Jackrabbit Oak. Além disso, o pacote do uber-jar AEM 6.5 LTS foi alterado. Além disso, alguns recursos herdados foram removidos do AEM 6.5 LTS. Para obter mais informações, consulte [Notas de versão](/help/release-notes/release-notes.md#whats-new-what-s-new) e [Lista de Pacotes Obsoletos Desinstalados Após a Atualização](/help/sites-deploying/obsolete-bundles.md)

O AEM 6.5 LTS tem um forte foco na compatibilidade com versões anteriores de recursos e vem com uma ferramenta de análise. Consulte [Avaliando a Complexidade de Atualização com o AEM Analyzer](/help/sites-deploying/aem-analyzer.md) para obter uma avaliação da complexidade à medida que você inicia o [planejamento da atualização](/help/sites-deploying/upgrade-planning.md).
