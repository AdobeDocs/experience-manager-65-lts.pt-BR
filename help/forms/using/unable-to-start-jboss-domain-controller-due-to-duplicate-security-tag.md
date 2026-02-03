---
title: Não é possível iniciar o controlador de domínio JBoss
description: Em implantações de cluster do AEM Forms 6.5.1 LTS usando o JBoss EAP 8, o arquivo de configuração pode conter tag duplicada.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: 259cb81eb9652405dc7270535cbf9deb996ad2ac
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# Não é possível iniciar o controlador de domínio JBoss

## Problema

Nas implantações de cluster do **AEM Forms 6.5.1 LTS** usando o **JBoss EAP 8**, o arquivo de configuração
`<JBOSS_HOME>/domain/configuration/domain_oracle.xml` (e variantes específicas do banco de dados) pode conter uma **marca `<security>` de abertura duplicada**.

Isso causa uma **configuração XML inválida**, resultando em **falha na inicialização do Controlador de Domínio JBoss** e impedindo a inicialização de cluster bem-sucedida.

## Aplica-se a

* **Produto:** AEM Forms 6.5.1 LTS
* **Tipo de Implantação:** Cluster
* **Servidor de Aplicativos:** JBoss EAP 8.x
* **Arquivos de Configuração:**

   * `<JBOSS_HOME>/domain/configuration/domain_oracle.xml`
   * `<JBOSS_HOME>/domain/configuration/domain_mysql.xml`
   * `<JBOSS_HOME>/domain/configuration/domain_mssql.xml`

## Etapas de solução de problemas

1. Durante a inicialização do controlador de domínio, os seguintes erros podem ser observados:

   * `WFLYCTL0198: Unexpected element 'security'`
   * `IJ010061: Unexpected element: security`

2. Abra o arquivo de configuração relevante:

   ```
   <JBOSS_HOME>/domain/configuration/domain_oracle.xml
   (or domain_mysql.xml / domain_mssql.xml)
   ```

3. Localize a marca de abertura `<security>` duplicada.

   **Configuração incorreta:**

   ```xml
   <security>
       <security>
           <user-name>adobe</user-name>
           <credential-reference store="db-creds" alias="EncryptDBPassword"/>
       </security>
   ```

4. Remova a tag `<security>` de abertura extra para que a configuração seja corrigida conforme mostrado abaixo:

   **Configuração correta:**

   ```xml
   <security>
       <user-name>adobe</user-name>
       <credential-reference store="db-creds" alias="EncryptDBPassword"/>
   </security>
   ```

5. Salve o arquivo e inicie o Controlador de domínio JBoss.

6. Garantir que a mesma configuração validada seja aplicada de forma consistente em todos os nós do cluster.
