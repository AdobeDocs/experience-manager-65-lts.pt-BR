---
title: Reduzindo vulnerabilidades de SSRF (Server-Side Request Forgery) para AEM Forms no JEE 6.5 LTS SP2
description: Etapas de mitigação para vulnerabilidades de SSRF (Server-Side Request Forgery) no AEM Forms em implantações do JEE 6.5 LTS Service Pack 2 em execução no JBoss.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: 7c4a9e12-3b8f-4d6a-9f1e-2a5c8d7e6b04
source-git-commit: 1d825cd821609504c5e2cff7f7002bf3afe30434
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 3%

---

# Reduzindo vulnerabilidades de SSRF (Server-Side Request Forgery) para AEM Forms no JEE 6.5 LTS SP2

## Referência rápida {#quick-reference}

| Nível de impacto | Versões afetadas | Ação recomendada |
| --- | --- | --- |
| Crítico | AEM Forms no JEE 6.5 LTS Service Pack 2 (6.5 LTS SP2) | Instalar manualmente o [hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) |
| Não afetado | AEM Forms no OSGi, Workbench, Cloud Service | Nenhuma ação necessária |

**Vulnerabilidades Endereçadas:**

* Falsificação de solicitação do lado do servidor (SSRF) (CWE-918)

## Visão geral {#overview}

### O que foi afetado {#whats-affected}

| Vulnerabilidade | Impacto | Componentes afetados |
| --- | --- | --- |
| Falsificação de solicitação do lado do servidor (SSRF) (CWE-918) | Os invasores podem induzir o servidor a fazer solicitações não intencionais para recursos internos ou externos | AEM Forms no JEE 6.5 LTS SP2 |

### O que não é afetado {#whats-not-affected}

* Experience Manager Forms Workbench (todas as versões)
* Experience Manager Forms no OSGi (todas as versões)
* Experience Manager Forms as a Cloud Service

## Opções de resolução {#resolution-options}

### Antes de começar {#before-you-start}

Antes de fazer qualquer alteração, faça um backup do arquivo EAR que você está prestes a substituir:

* Localize `adobe-edcserver-jboss.ear` no diretório de implantação:

  ```text
  [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
  ```

* Copie o arquivo para um local de backup seguro fora do diretório de implantação.
* Certifique-se de que o backup esteja completo e acessível antes de prosseguir com qualquer atualização.

Essa precaução permite restaurar o estado original caso você encontre problemas durante o processo de atualização.

### Instalação manual do Hotfix para o AEM Forms no JEE 6.5 LTS SP2 (JBoss)

1. Baixe `adobe-edcserver-jboss.ear` do [Portal de Distribuição de Software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear).

1. Localize `adobe-edcserver-jboss.ear` no diretório de implantação e substitua-o pelo arquivo baixado:

   ```text
   [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
   ```

1. Inicie o Gerenciador de configuração do AEM Forms para reimplantar o EAR atualizado e aplicar o hotfix.

1. Reinicie o servidor de aplicativos e confirme a implantação bem-sucedida a partir dos logs do servidor.

## Referência {#references}

* [Práticas recomendadas de segurança da Adobe Experience Manager Forms](/help/forms/using/hardening-securing-aem-forms-environment.md)
