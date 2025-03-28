---
title: Armadilhas de código
description: Erros comuns de codificação a serem evitados ao desenvolver para o AEM
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Armadilhas de código{#code-pitfalls}

## Evite vinculações Sling no código Java {#avoid-sling-bindings-in-java-code}

Os Vínculos Sling são uma maneira inadequada de obter acesso a um serviço em 90% dos casos. Em vez disso, você deve usar anotações *@Reference* ou *@Inject*.

## Evitar Thread.interrupt no código Java {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* é perigoso porque pode fechar arquivos, incluindo arquivos Lucene e arquivos de cache persistente, quando chamados na hora errada.

## Evite misturar a sincronização do Java com ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Isso pode levar a uma condição de corrida na qual o código acabará bloqueando.
