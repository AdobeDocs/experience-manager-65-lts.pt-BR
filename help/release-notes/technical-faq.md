---
title: Perguntas frequentes técnicas
description: Perguntas técnicas frequentes sobre o AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: f994a8712a403083de1edc62579846ba99bd3afd
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 59%

---

# Perguntas frequentes técnicas sobre o AEM 6.5 LTS {#technical-faq}

Esta página tem como objetivo responder a algumas perguntas técnicas frequentes sobre o AEM 6.5 LTS.

## Perguntas frequentes técnicas

### O ponto de acesso `/systemalive` não está mais disponível no AEM 6.5 LTS.

O pacote Felix System Ready, que foi configurado para fornecer o ponto de acesso `/systemalive`, foi descontinuado e substituído pelas verificações da integridade do Apache Felix. Este pacote não está mais incluído no AEM 6.5 LTS.

O novo ponto de acesso de verificação da integridade está disponível em `/system/health` e é implementado por meio das verificações da integridade do Apache Felix.

Para conferir a documentação detalhada sobre a estrutura de verificação da integridade do Felix, consulte a [documentação do Felix](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### Suporte ao console do AEM Groovy

A versão do console do AEM Groovy que estava sendo usada no AEM 6.5 pode não funcionar no AEM 6.5 LTS devido à ausência de dependências de guava. A versão mais recente com suporte do Console do AEM Groovy é [19.0.8](https://github.com/orbinson/aem-groovy-console/releases/download/19.0.8/aem-groovy-console-all-19.0.8.zip).

#### Configuração adicional necessária para o console do AEM Groovy

Se você estiver usando o Console do AEM Groovy, deverá adicionar explicitamente a seguinte configuração OSGi para `com.adobe.granite.apicontroller.FilterResolverHookFactory`. Adicione `aem-groovy-console-bundle` à lista de pacotes permitidos para a chave `org.apache.sling.distribution.api`, estendendo os padrões da plataforma:

```
"org.apache.sling.distribution.api": "com.adobe.*,com.day.*,org.apache.sling.*,aem-groovy-console-bundle"
```

### O AEM 6.5 LTS é compatível com a sincronização de usuários?

Sim, o AEM 6.5 LTS é compatível com a sincronização de usuários. Não houve nenhuma mudança na funcionalidade de sincronização de usuários entre o AEM 6.5 e o 6.5 LTS.

### O Uber JAR do Maven Central parece estar corrompido. Qual é o problema?

Verifique se você está usando o Uber JAR com o classificador `apis`. Observe que a estrutura de empacotamento do Uber JAR mudou no AEM 6.5 LTS. Para mais informações, consulte [Atualizar a versão Uber Jar do do AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### O AEM 6.5 LTS é compatível com os namespaces de pacote `jakarta.*` (por exemplo, `jakarta.annotation`)?

Não. O AEM 6.5 LTS não oferece suporte a artefatos do Sling migrados para os namespaces do pacote `jakarta.*`. Use os equivalentes `javax.*` em seu código e dependências — por exemplo, `javax.annotation.PostConstruct` em vez de `jakarta.annotation.PostConstruct` em Modelos Sling. A implementação dos Modelos Sling no AEM 6.5 LTS reconhece apenas as `javax.*` anotações, portanto, `jakarta.*` anotações são ignoradas silenciosamente durante a inicialização.

Para obter mais informações, consulte o artigo da base de dados de conhecimento [Sling Models with `jakarta.annotation.PostConstruct` fail on AEM 6.5 LTS](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-30339).

## Como obter mais ajuda

Se você se deparar com problemas não abordados aqui:
* Confira as [notas de versão](/help/release-notes/release-notes.md) para ver se há problemas conhecidos.
* Entre em contato com o suporte da Adobe para obter assistência.
