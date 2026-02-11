---
title: Fluxo de trabalho de instalação e atualização do AEM Forms no JEE
description: Fluxo de trabalho de instalação e atualização do AEM Forms 6.5 LTS no JEE (JBoss), com uma lista consolidada de PDFs relevantes e sua finalidade.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: AEM Forms on JEE,AEM Forms Upgrade
exl-id: 6d8c0e24-7f08-4e66-bb12-2cf1cfe1d5d3
source-git-commit: fb9f6ef794da7f3b242e9e81a6c2505692c16cd8
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 2%

---


# Fluxo de trabalho de instalação e atualização do AEM Forms no JEE {#aem-forms-jee-installation-upgrade-documentation}

## Aplica-se a {#applies-to}

Esta documentação se aplica ao **AEM 6.5 LTS Forms**.

Use o fluxo de trabalho e as tabelas a seguir para escolher os guias corretos para o seu cenário. Alguns documentos são publicados como PDFs; documentos adicionais podem ser adicionados ao longo do tempo, à medida que estiverem disponíveis.

## Fluxo de trabalho de instalação e atualização {#installation-upgrade-workflow}

1. Revise as [plataformas com suporte para AEM Forms no JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) e verifique se o seu sistema atende às combinações de software/hardware necessárias.
2. Decida se você está executando uma **nova instalação** ou uma **atualização**.
3. Para o caminho escolhido, siga a sequência descrita abaixo (alguns cenários exigem mais de um guia).

## Etapas de pré-instalação e pré-atualização {#start-here}

| Guia | Descrição |
| --- | --- |
| [Plataformas com suporte para o AEM Forms no JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) | Lista as combinações de software e hardware compatíveis com o AEM Forms no JEE. Use-o para validar os pré-requisitos antes de iniciar uma instalação ou atualização. |
| [Arquitetura e topologias de implantação para o AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md) | Explica as arquiteturas e topologias de implantação recomendadas para que você possa escolher uma abordagem que corresponda ao seu ambiente (por exemplo, um único servidor vs. cluster). |
| [Escolhendo um tipo de persistência para uma instalação do AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md) | Ajuda a selecionar um tipo de persistência apropriado para sua topologia de instalação antes de você começar. |

## Como instalar o Adobe Experience Manager Forms (AEM Forms) no JEE no JBoss? {#installing-aem-forms-jee-jboss}

### Turnkey {#install-jee-jboss-turnkey}

| Guia | Descrição |
| --- | --- |
| [Instalando e implantando o AEM Forms 6.5 LTS no JEE usando o JBoss Turnkey (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-turnkey.pdf) | Use para uma **nova instalação completa** no JBoss. Este documento fornece instruções para instalar e implantar o AEM Forms no JEE usando a distribuição JBoss turnkey. |

### Servidor único (não chave na mão) {#install-jee-jboss-single-server}

| Guia | Descrição |
| --- | --- |
| [Preparando para Instalar o AEM Forms (Servidor Único) (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-install-single-server.pdf) | Use **antes** uma **instalação de servidor único (sem chave na mão) atualizada**. Este documento lista os pré-requisitos e as etapas de preparação do ambiente para instalar o AEM Forms no JEE em uma topologia de servidor único. |
| [Instalando e implantando o AEM Forms no JEE para JBoss (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-jboss.pdf) | Use para a **instalação e implantação passo a passo** do AEM Forms no JEE no JBoss (**non-turnkey**). Para instalações de servidor único, siga este guia **depois** de concluir *Preparando para Instalar o AEM Forms (Servidor Único)*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **fresh cluster installation**. Describes prerequisites and environment preparation steps for installing AEM Forms on JEE in a server cluster topology. *(Link will be added once the PDF is available.)* |
| [Configuring AEM Forms on JEE on JBoss Cluster (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/cluster-jboss.pdf) | Use when setting up and configuring a **JBoss cluster topology** for AEM Forms on JEE. |
-->

## Como atualizo o Adobe Experience Manager Forms (AEM Forms) no JEE no JBoss? {#upgrading-aem-forms-jee-jboss}

### Turnkey {#upgrade-jee-jboss-turnkey}

| Guia | Descrição |
| --- | --- |
| [Atualizando para o AEM Forms 6.5 LTS no JEE para JBoss Turnkey (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-turnkey.pdf) | Use para uma **atualização completa**. Este documento fornece instruções para atualizar um AEM Forms existente na instalação completa do JEE JBoss. |

### Um único servidor {#upgrade-jee-jboss-single-server}

| Guia | Descrição |
| --- | --- |
| [Preparando para atualizar o AEM Forms (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-upgrade.pdf) | Use **antes** uma **atualização de servidor único**. Descreve como preparar o ambiente antes de atualizar para o AEM 6.5 LTS Forms. Ela se aplica a ambientes que executam o AEM Forms no JEE em um modo de instalação de servidor único. |
| [Atualizando para AEM Forms no JEE para JBoss (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-jboss.pdf) | Use para o **procedimento de atualização passo a passo** no JBoss em um modo de instalação **único servidor**. Siga este guia **depois** de concluir *Preparando para atualizar o AEM Forms*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **cluster upgrade**. Describes how to prepare the environment for a server cluster before upgrading to AEM 6.5 LTS Forms. It applies to environments running AEM Forms on JEE in a server cluster installation mode. *(Link will be added once the PDF is available.)* |
| Upgrading to AEM Forms on JEE for JBoss (Cluster) (PDF) (**TBD**) | Use for the **step-by-step upgrade procedure** on JBoss in a **clustered** installation mode. Follow this guide **after** completing *Preparing to Install AEM Forms (Server Cluster)*. *(Link will be added once the PDF is available.)* | -->

