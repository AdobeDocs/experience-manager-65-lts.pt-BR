---
title: Perguntas frequentes técnicas
description: Perguntas técnicas frequentes sobre o AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: ec722773ce3acff1d0de861523db8ff7df552c4b
workflow-type: ht
source-wordcount: '247'
ht-degree: 100%

---

# Perguntas frequentes técnicas sobre o AEM 6.5 LTS {#technical-faq}

Esta página tem como objetivo responder a algumas perguntas técnicas frequentes sobre o AEM 6.5 LTS.

## Perguntas frequentes técnicas

### O ponto de acesso `/systemalive` não está mais disponível no AEM 6.5 LTS.

O pacote Felix System Ready, que foi configurado para fornecer o ponto de acesso `/systemalive`, foi descontinuado e substituído pelas verificações da integridade do Apache Felix. Este pacote não está mais incluído no AEM 6.5 LTS.

O novo ponto de acesso de verificação da integridade está disponível em `/system/health` e é implementado por meio das verificações da integridade do Apache Felix.

Para conferir a documentação detalhada sobre a estrutura de verificação da integridade do Felix, consulte a [documentação do Felix](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### Compatibilidade com o console do AEM Groovy

A versão do console do AEM Groovy usada no AEM 6.5 pode não funcionar no AEM 6.5 LTS devido à ausência de dependências do Guava. A nova versão compatível do console do AEM Groovy é a [19.0.8](https://mvnrepository.com/artifact/be.orbinson.aem/aem-groovy-console/19.0.8).

### O AEM 6.5 LTS é compatível com a sincronização de usuários?

Sim, o AEM 6.5 LTS é compatível com a sincronização de usuários. Não houve nenhuma mudança na funcionalidade de sincronização de usuários entre o AEM 6.5 e o 6.5 LTS.

### O Uber JAR do Maven Central parece estar corrompido. Qual é o problema?

Verifique se você está usando o Uber JAR com o classificador `apis`. Observe que a estrutura de empacotamento do Uber JAR mudou no AEM 6.5 LTS. Para mais informações, consulte [Atualizar a versão Uber Jar do do AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

## Como obter mais ajuda

Se você se deparar com problemas não abordados aqui:
* Confira as [notas de versão](/help/release-notes/release-notes.md) para ver se há problemas conhecidos.
* Entre em contato com o suporte da Adobe para obter assistência.
