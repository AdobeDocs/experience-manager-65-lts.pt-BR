---
title: Namespaces personalizados
description: Saiba como definir e implantar namespaces personalizados para o AEM 6.5 LTS.
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
source-git-commit: 475a77e8e4ff0ecd19a939fd3b3c9294adf24997
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
