---
title: Como reiniciar o AEM SDK?
description: Práticas recomendadas para reiniciar o AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms,AEM Forms on JEE,AEM Forms on OSGi
solution: Experience Manager, Experience Manager Forms
hide: true
hidefromtoc: true
exl-id: 68935045-89b1-4219-b111-88a4600200df
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 1%

---

# Reiniciar o AEM SDK

Se você reiniciar o AEM SDK interrompendo os processos do Java™, o poderá causar inconsistências no ambiente de desenvolvimento do AEM, e um erro ocorrerá:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Reiniciar-aem-sdk-erro](/help/forms/using/assets/restart-sdk-error.png)

## Solução

Para reiniciar o AEM SDK, vá para a janela de comando ativa e pressione o comando `Ctrl + C` para reiniciar o SDK.

É recomendável usar o comando &#39;Ctrl + C&#39; para reiniciar o SDK. Reiniciar o AEM SDK usando métodos alternativos, por exemplo, parar processos Java™, pode levar a inconsistências no ambiente de desenvolvimento do AEM.
