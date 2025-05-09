---
title: Etapas adicionais para obter e-mails com anexos
description: Saiba como corrigir o erro quando não é possível recuperar emails com anexos do AEM Forms em plataformas JEE.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: c04e0716-2aa2-420b-bbf5-74ffd1c28794
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Não é possível obter email com anexos para AEM Forms em plataformas JEE{#unable-to-get-email-with-attachments}

O problema se aplica à seguinte versão:

* Experience Manager 6.5 Forms

## Problema {#issue}

O usuário não pode executar operações como Enviar PDF por email ou Incluir anexos com a configuração de envio.

## Solução {#solution}

1. Baixe jar como [java.mail-1.0.jar](/help/forms/using/java.mail-1.0.jar) e descompacte o arquivo jar baixado para obter o arquivo de manifesto.

1. Use o arquivo de manifesto de `java.mail-1.0.jar` recuperado da Etapa 1 para criar um arquivo jar personalizado, digamos `java.mail-1.5.jar`.

1. Abrir o arquivo de manifesto e substituir todas as ocorrências de `1.5.0` por `1.5.6` e `Bundle-Version: 1.0` por `Bundle-Version:1.5`

1. Crie um arquivo jar (`java.mail-1.5.jar`) personalizado usando o seguinte comando na pasta `C:\Adobe\Adobe_Experience_Manager_Forms\java\jdk\bin` como:
   `jar -cfm java.mail-1.5.jar manifest.mf`

   No comando acima, *manifest.mf* é o nome do arquivo de manifesto e *java.mail-1.5.jar* é o nome do arquivo que seria criado após a execução do comando acima.

1. Baixar [javax.mail-1.5.6.redhat-1.jar](https://mvnrepository.com/artifact/com.sun.mail/javax.mail/1.5.6.redhat-1).

1. Navegue até `http://<server name>:<port>/lc/system/console/bundles` e exclua o conjunto com o nome `JavaMail API (com.sun.mail.javax.mail) version 1.6.2`.

1. Instalar o `java.mail-1.5.jar` obtido da etapa 3. Esta etapa reinicia as propriedades sling da implantação do JEE. Aguarde os pacotes instalados em `http://<server name>:<port>/lc/system/console/bundles` para mostrar o Status como **Ativo**.

   >Caso o status ainda seja **InActive**, reinicie   **JBoss®** do **Console de Serviços**.


1. Instale o arquivo `javax.mail-1.5.6.redhat-1.jar` baixado usando a etapa 5.

1. Pare o **JBoss®** do **Console de Serviços** e anexe as seguintes propriedades ao arquivo **Sling.properties**:
   * `org.osgi.framework.system.packages.extra=javax.activation; version\=1.2.0`
   * `sling.bootdelegation.activation=javax.activation.*`

1. Reinicie o **JBoss®**.

>[!NOTE]
>
> É recomendável usar o comando &#39;Ctrl + C&#39; para reiniciar o SDK. Reiniciar o AEM SDK usando métodos alternativos, por exemplo, parar processos Java, pode levar a inconsistências no ambiente de desenvolvimento do AEM.
