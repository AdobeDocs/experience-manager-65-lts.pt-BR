---
title: Namespaces personalizados
description: Saiba como definir e implantar namespaces personalizados para o AEM 6.5 LTS.
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: f2d27a5f-0d67-4d85-8a24-86a8d8a3574b
    internal-label: Developer tools
subfeature_v2:
  - id: cd14456d-a492-4b5c-8a82-1fbd4460dbd2
    internal-label: Java Content Repository
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 8%
---

# Namespaces personalizados{#custom-namespaces}

Saiba como definir e implantar [namespaces](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/1.0/4.5_Namespaces.html) personalizados no AEM 6.5 LTS.

Os namespaces personalizados são a parte opcional de uma propriedade JCR que precede um `:`. O AEM usa vários namespaces, como:

+ `jcr` para propriedades do sistema JCR
+ `cq` para propriedades do AEM (anteriormente conhecido como Adobe CQ)
+ `dam` para propriedades do AEM específicas para ativos DAM
+ `dc` para as propriedades principais de Dublin

... e muitos outros.

Os namespaces podem ser usados para denotar o escopo e a intenção de uma propriedade. A criação de um namespace personalizado, geralmente o nome da sua empresa, ajuda a identificar claramente os nós ou propriedades específicos da sua implementação do AEM e contém dados específicos da sua empresa.

Os namespaces personalizados são gerenciados nos scripts [Inicialização do Repositório do Sling (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html) e implantados como configurações de OSGi no pacote de configuração do seu projeto (por exemplo, `ui.config`).

## Recursos {#resources}

+ [Documentação de inicialização do repositório Sling (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios)

## Código {#code}

O código a seguir é usado para configurar um namespace `wknd`.

### Configuração OSGi de RepositoryInitializer

`/ui.config/src/main/content/jcr_root/apps/wknd-examples/osgiconfig/config/org.apache.sling.jcr.repoinit.RepositoryInitializer~wknd-examples-namespaces.cfg.json`

```json
{
    "scripts": [
        "register namespace (wknd) https://site.wknd/1.0"
    ]
}
```

Isso permite que propriedades personalizadas usando o namespace `wknd`, conforme indicado pelo primeiro parâmetro após a instrução `register namespace`, sejam usadas no AEM. Para obter definições de script mais avançadas, reveja os exemplos na [documentação de Inicialização do Repositório do Sling (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios).
