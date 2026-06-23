---
title: Reduzindo as vulnerabilidades de VULN-36128 e VULN-36120 para AEM Forms no JEE 6.5 LTS SP2
description: Etapas de mitigação para VULN-36128 e VULN-36120 no AEM Forms em implantações do JEE 6.5 LTS Service Pack 2 em execução no JBoss.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin
exl-id: 7c4a9e12-3b8f-4d6a-9f1e-2a5c8d7e6b04
source-git-commit: 1b876f20cbc3a00a02a4449f0d353fb858695235
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# Reduzindo as vulnerabilidades de VULN-36128 e VULN-36120 para AEM Forms no JEE 6.5 LTS SP2

## Referência rápida {#quick-reference}

| Nível de impacto | Versões afetadas | Ação recomendada |
| --- | --- | --- |
| Crítico | AEM Forms no JEE 6.5 LTS Service Pack 2 (6.5 LTS SP2) | Instalar manualmente o [hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) |
| Não afetado | AEM Forms no OSGi, Workbench, Cloud Service | Nenhuma ação necessária |

**Vulnerabilidades Endereçadas:**

* **VULN-36128**: vulnerabilidade de execução de código remoto que permite que invasores remotos não autorizados executem código arbitrário.
* **VULN-36120**: vulnerabilidade de validação de entrada inadequada que poderia permitir acesso não autorizado a informações confidenciais.

## Etapas de atenuação {#mitigation-steps}

### Antes de começar {#before-you-start}

Antes de fazer qualquer alteração, faça backup do arquivo EAR que você está prestes a substituir:

* Localize `adobe-edcserver-jboss.ear` no diretório de implantação:

  ```text
  [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
  ```

* Copie o arquivo para um local de backup seguro fora do diretório de implantação.
* Certifique-se de que o backup esteja completo e acessível antes de prosseguir com qualquer atualização.

Essa precaução permite restaurar o estado original se você encontrar problemas durante o processo de atualização.

### Instalação manual do Hotfix para o AEM Forms no JEE 6.5 LTS SP2 (JBoss) {#manual-hotfix-installation-aem-forms-jee-65-lts-sp2-jboss}

1. Baixe `adobe-edcserver-jboss.ear` do [Portal de Distribuição de Software da Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear).

1. Localize `adobe-edcserver-jboss.ear` no diretório de implantação e substitua-o pelo arquivo baixado:

   ```text
   [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
   ```

1. Inicie o AEM Forms Configuration Manager para reimplantar o EAR atualizado e aplicar totalmente o patch.

1. Reinicie o servidor de aplicativos e confirme a implantação bem-sucedida a partir dos logs do servidor.

## Referências {#references}

* [Práticas recomendadas de segurança do Adobe Experience Manager Forms](/help/forms/using/hardening-securing-aem-forms-environment.md)
