---
title: Perguntas frequentes
description: Perguntas frequentes sobre o AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: d18c9dc3-fdcc-4558-b9b6-ecf1ce61048a
source-git-commit: 004a3859c06e7c219e7919ac5920a9bc179ede43
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 91%

---

# Perguntas frequentes sobre o AEM 6.5 LTS {#faq}

Esta página tem como objetivo responder a algumas perguntas frequentes sobre o AEM 6.5 LTS.

## Por que a Adobe lançou a versão 6.5 LTS do AEM?

A Adobe continua profundamente comprometida com a segurança e a estabilidade dos aplicativos que oferece. O Suporte de longo prazo do AEM 6.5 estabelece a base para atualizações futuras do AEM 6.5. Vale destacar que o AEM 6.5 LTS inclui suporte para o Oracle Java 17 e o Java 21, e ainda será a ramificação do AEM que receberá novos recursos e inovações do AEM.

## Sou cliente local. O que acontece se eu não fizer o upgrade para o AEM 6.5 LTS?

O AEM 6.5 LTS inclui atualizações importantes de segurança e estabilidade, incluindo compatibilidade com o Oracle Java 17 e Java 21. Recomenda-se que as organizações planejem uma atualização para a versão 6.5 da LTS. A Adobe continuará a oferecer suporte ao AEM 6.5 até 28 de fevereiro de 2027. Verifique o [roteiro](https://experienceleague.adobe.com/pt-br/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap#aem65) para obter mais detalhes.

## Minhas personalizações e integrações já existentes serão afetadas se eu atualizar para o AEM 6.5 LTS?

Embora o AEM 6.5 LTS tenha como objetivo manter a compatibilidade com versões anteriores, alguns recursos e artefatos herdados foram removidos.
É essencial conferir as [notas de versão](/help/release-notes/release-notes.md#deprecated-and-removed-features) e usar a [ferramenta AEM Analyzer](/help/sites-deploying/aem-analyzer.md) para avaliar o impacto nas suas personalizações e integrações.

## Como posso garantir uma transição tranquila para o AEM 6.5 LTS?

Para garantir uma transição tranquila, é recomendável:

* Conferir as [notas de versão](/help/release-notes/release-notes.md) e a documentação detalhadamente.
* Usar a [ferramenta AEM Analyzer](/help/sites-deploying/aem-analyzer.md) para avaliar a complexidade do upgrade.
* Planejar e dedicar tempo e recursos suficientes ao processo de upgrade.
* Interagir com as sessões de suporte e habilitação da Adobe para obter orientação e assistência.

## O que são os pacotes de serviços do AEM 6.5 LTS?

Os pacotes de serviços do AEM 6.5 LTS são uma atualização cumulativa que inclui todas as correções e melhorias feitas no AEM 6.5 LTS desde o lançamento inicial. É recomendável aplicar o pacote de serviços mais recente para garantir que a sua instância do AEM esteja atualizada com os recursos e patches de segurança mais recentes.

## Estou usando o AEM 6.5; posso fazer o upgrade diretamente para o pacote de serviços do AEM 6.5 LTS sem fazer o upgrade para a versão AEM 6.5 LTS GA?

Sim, você pode fazer o upgrade diretamente do AEM 6.5 para qualquer pacote de serviços do AEM 6.5 LTS. É recomendável revisar as [notas de versão](/help/release-notes/release-notes.md) e a seção [Fazer upgrade para o AEM 6.5 LTS](/help/sites-deploying/upgrade.md).

## Estou usando o AEM 6.5 LTS GA; preciso fazer alterações no código para fazer o upgrade para os pacote sde serviços do AEM 6.5 LTS?

Não, não é necessário fazer alterações no código para fazer o upgrade do AEM 6.5 LTS para os pacotes de serviços do AEM 6.5 LTS. No entanto, é sempre recomendável revisar as [notas de versão](/help/release-notes/release-notes.md) e testar as suas personalizações e integrações em um ambiente de preparo antes de aplicar o pacote de serviços à sua instância de produção.

## Quero começar com uma nova configuração do AEM 6.5 LTS. Posso começar diretamente com o pacote de serviços do AEM 6.5 LTS?

Sim, você pode configurar diretamente um novo pacote de serviços do AEM 6.5 LTS sem configurar a compilação AEM 6.5 LTS GA. É recomendável revisar as [notas de versão](/help/release-notes/release-notes.md) e a seção [Instalação independente personalizada](/help/sites-deploying/custom-standalone-install.md) para mais detalhes.
