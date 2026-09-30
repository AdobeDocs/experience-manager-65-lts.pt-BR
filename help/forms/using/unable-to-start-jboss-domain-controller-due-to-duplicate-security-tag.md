---
title: Não é possível iniciar o controlador de domínio JBoss
description: Em implantações de cluster do AEM Forms 6.5.1 LTS usando o JBoss EAP 8, o arquivo de configuração pode conter tag duplicada.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: f24e7245-7b43-4b1c-ba7a-162344ef545c
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%
---
# Não é possível iniciar o controlador de domínio JBoss

## Problema

Nas implantações de cluster do **AEM Forms 6.5.1 LTS** usando o **JBoss EAP 8**, o arquivo de configuração
`<JBOSS_HOME>/domain/configuration/domain_oracle.xml` (e variantes específicas do banco de dados) pode conter uma **marca de abertura `<security>` duplicada**.

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
