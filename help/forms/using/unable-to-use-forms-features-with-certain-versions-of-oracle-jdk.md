---
title: Não é possível usar o Experience Manager Forms com determinadas versões do JDK do Oracle
description: Não é possível usar o Experience Manager Forms com determinadas versões do JDK do Oracle
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 1%

---

# Não é possível usar o Experience Manager Forms com determinadas versões do JDK do Oracle {#unable-to-use-forms-with-certain-versions-of-oracle-jdk}

O problema se aplica às seguintes versões:

* Experience Manager 6.3 Forms
* Experience Manager 6.4 Forms
* Experience Manager 6.5 Forms

## Problema {#issue}

O usuário encontra a seguinte exceção:
`Caused by: javax.xml.xpath.XPathExpressionException: javax.xml.transform.TransformerException: JAXP0801002: the compiler encountered an XPath expression containing '101' operators that exceeds the '100' limit set by 'FEATURE_SECURE_PROCESSING'.`

## Motivo {#reason}

A exceção ocorre quando você executa o Experience Manager Forms com uma versão do Oracle JDK (Java Development Kit) maior ou igual às seguintes versões:

* [JDK7u341](https://www.oracle.com/java/technologies/javase/7u341-relnotes.html)
* [JDK8u331](https://www.oracle.com/java/technologies/javase/8u331-relnotes.html)
* [JDK11u15](https://www.oracle.com/java/technologies/javase/11-0-15-relnotes.html)

As versões acima mencionadas e posteriores do Java incluem novos limites de processamento XML na JVM (Java Virtual Machine), o que causa a falha de determinadas operações específicas do Forms.

## Solução alternativa {#workaround}

1. Pare o Experience Manager Forms Server.
1. Configure o seguinte argumento JVM para seu servidor de aplicativos:

   `-Djdk.xml.xpathExprOpLimit=2000`

   Ela define a propriedade do sistema na JVM com um valor razoavelmente alto para que o limite padrão não seja atingido.

1. Inicie o Experience Manager Forms Server.
