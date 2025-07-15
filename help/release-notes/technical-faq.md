---
title: Perguntas frequentes técnicas
description: Perguntas técnicas frequentes sobre o AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: ec722773ce3acff1d0de861523db8ff7df552c4b
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 2%

---

# Perguntas frequentes técnicas sobre o AEM 6.5 LTS {#technical-faq}

Esta página é destinada a responder algumas perguntas técnicas frequentes sobre o AEM 6.5 LTS.

## Perguntas frequentes técnicas

### O ponto de extremidade `/systemalive` não está mais disponível no AEM 6.5 LTS.

O pacote Felix System Ready que foi configurado para fornecer o ponto de extremidade `/systemalive` foi descontinuado e substituído pelas Verificações de Integridade do Apache Felix. Este pacote não está mais incluído no AEM 6.5 LTS.

O novo ponto de extremidade de verificação de integridade está disponível em `/system/health` e é implementado usando as Verificações de Integridade do Apache Felix.

Para obter a documentação detalhada sobre a estrutura de Verificação de integridade Felix, consulte a [documentação felix](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### Suporte ao console do AEM Groovy

A versão do console do AEM Groovy que estava sendo usada no AEM 6.5 pode não funcionar no AEM 6.5 LTS devido à ausência de dependências de guava. A versão recém-suportada do console do AEM Groovy é [19.0.8](https://mvnrepository.com/artifact/be.orbinson.aem/aem-groovy-console/19.0.8).

### O AEM 6.5 LTS é compatível com a sincronização de usuários?

Sim, o AEM 6.5 LTS é compatível com a sincronização de usuários. Não há alteração na funcionalidade de sincronização de usuários entre o AEM 6.5 e o 6.5 LTS.

### O Uber JAR no Maven Central parece estar corrompido. Qual é o problema?

Verifique se você está usando o Uber JAR com o classificador `apis`. Observe que a estrutura de empacotamento do Uber JAR mudou no AEM 6.5 LTS. Para obter mais informações, consulte [Atualizar a versão do AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

## Obtendo ajuda adicional

Se você encontrar problemas não cobertos aqui:
* Revise as [notas de versão](/help/release-notes/release-notes.md) para ver se há problemas conhecidos.
* Entre em contato com o Suporte da Adobe para obter assistência.
