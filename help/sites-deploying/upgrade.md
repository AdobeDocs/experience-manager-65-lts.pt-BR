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
source-git-commit: f66bb283e5c2a746821839269e112be8c2714ba7
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 1%

---

# Atualização para o Adobe Experience Manager (AEM) 6.5 LTS {#upgrading-to-aem}

>[!NOTE]
>A atualização para o AEM 6.5 LTS é compatível com os últimos 6 Service packs.

Esta seção aborda a atualização de uma instalação do AEM para o AEM 6.5:

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

Estas são as principais alterações observadas nas últimas versões do AEM:

1. A camada Foundation foi atualizada para ser compatível com o Java 17 (que inclui camadas de código aberto de pacotes do Apache Sling, Apache Felix e Apache Jackrabbit Oak)

1. O empacotamento jar do AEM 6.5 LTS agora é compatível com as especificações 5 das APIs do Jarkarta Servlet e o empacotamento war pode ser implantado em contêineres de servlet que implementam as especificações 5/6 da API do Jakarta Servlet

1. O empacotamento do AEM 6.5 LTS uber-jar foi alterado. Consulte [Atualizando código e personalizações](/help/sites-deploying/upgrading-code-and-customizations.md) para obter mais informações.

### Recursos/artefatos herdados removidos {#removed-legacy-features-artifacts}

As seguintes soluções herdadas foram removidas do AEM 6.5 LTS. Para obter mais informações, consulte TBD: link para notas de versão e [Lista de Pacotes Obsoletos Desinstalados Após a Atualização](/help/sites-deploying/obsolete-bundles.md)

1. Social
1. Commerce
1. Screens
1. We-retail
1. Integração de pesquisa e promoção

**Artefatos Removidos**

1. CRX-explorer
1. Crx2oak
1. Google guava (removido devido a vulnerabilidades de segurança)
1. Abdera-parser (removido devido a vulnerabilidades de segurança)
1. jdom (`org.apache.servicemix.bundles.jdom`) (removido devido a vulnerabilidades de segurança)
1. `com.github.jknack.handlebars` (removido devido a vulnerabilidades de segurança)

O AEM 6.5 LTS tem um forte foco na compatibilidade com versões anteriores de recursos e vem com uma ferramenta de análise. Consulte [Avaliando a Complexidade da Atualização com o AEM Analyzer](/help/sites-deploying/pattern-detector.md) para obter uma avaliação da complexidade à medida que você começa a planejar a atualização. Para obter mais detalhes sobre o que mais mudou, consulte as notas de versão completas aqui. A definir: link para as notas de versão do AEM 6.5 LTS