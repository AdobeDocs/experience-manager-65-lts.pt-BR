---
title: Verificações de consistência e passagem
description: Saiba como executar verificações de consistência e percurso.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
hide: true
hidefromtoc: true
exl-id: 6ed130d5-30b5-4864-8bea-dfe41bed5422
source-git-commit: f145e5f0d70662aa2cbe6c8c09795ba112e896ea
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Verificações de consistência e passagem{#consistency-and-traversal-checks}

Durante a atualização, pode haver problemas devido a inconsistências no espaço de trabalho. Você pode executar uma atualização de teste para ver se isso é um problema ou executar as verificações de consistência como uma ação preventiva.

Se você executar uma atualização de teste que falha devido a inconsistências no espaço de trabalho, verá entradas semelhantes às seguintes em crx-quickstart/logs/crx/error.log:

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## Executar uma verificação de consistência {#perform-a-consistency-check}

Para executar uma verificação de consistência, navegue até a página de administração do Mbean JMX **com.adobe.granite (Repositório)**. Na tela principal do AEM, acesse:

**Ferramentas > Console da Web > Principal (na barra de menus) > JMX > com.adobe.granite (Repositório)**

Em uma instalação padrão, ela é encontrada aqui: **[|Mostre-me|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

Na seção **Operações** da página, você encontrará dois métodos: **`traversalCheck`** e **`consistencyCheck`**. Para executar uma verificação, clique na operação e insira os parâmetros desejados.

![chlimage_1-117](assets/chlimage_1-117.png)
