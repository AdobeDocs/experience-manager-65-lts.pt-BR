---
title: Notas de versão do  [!DNL Adobe Experience Manager] 6.5 LTS SP1
description: Encontre informações sobre a versão, novidades, instruções de instalação e uma lista de alterações detalhada para o [!DNL Adobe Experience Manager] 6.5 LTS SP1
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
source-git-commit: 27ec3c516b0746fd7e0d82f86750fbb4ef410711
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 3%

---


# Notas de versão do Adobe Experience Manager (AEM) Forms 6.5 LTS SP1 em JEE

## Informações da versão

| **Produto** | Adobe Experience Manager Forms |
| -------------------- | ------------------------------------ |
| **Versão** | 6.5 LTS SP1 |
| **Tipo** | Service Pack (JEE) de suporte a longo prazo |
| **Categoria de versão** | Versão de atualização |
| **URL de Download** | Distribuição de software |

## O que está incluído no [!DNL Experience Manager] 6.5 LTS SP1 {#what-is-included-in-aem-65ltssp1}

O Adobe Experience Manager (AEM) Forms **6.5 LTS SP1 no JEE** oferece novos recursos, atualizações importantes de plataformas solicitadas por clientes e correções gerais de erros, com forte foco na estabilidade do produto e suporte a longo prazo.

## O que está incluído no AEM Forms 6.5 LTS SP1

### &#x200B;1. Atualizações de suporte do Java

O suporte para versões mais recentes do Java foi introduzido:

* **Java™ 17**
* **Java™ 21**

### &#x200B;2. Atualizações de Suporte do Servidor de Aplicativos

#### Suporte a JBoss EAP 8

* Foi adicionado suporte para **JBoss EAP 8**.
* A estrutura de segurança **PicketBox** herdada foi removida.
* **Repositórios de credenciais baseados em Elytron** agora têm suporte para gerenciamento de credenciais seguro.

##### Configuração: armazenamento de credenciais (baseado em Elytron)

O AEM Forms no JBoss EAP 8 usa o Elytron para gerenciar credenciais seguras. Os clientes devem configurar um Armazenamento de credenciais baseado no Elytron para garantir a inicialização bem-sucedida do servidor e a autenticação segura do banco de dados.

Para obter detalhes sobre a configuração, consulte o guia de instalação e configuração.

### &#x200B;3. Alterações na plataforma e na compatibilidade

#### Suporte à especificação de servlet

* Suporte para **Especificação de Servlet 5+**
* Com base na conformidade com o **Jakarta EE 9**

#### Requisito de migração de namespace

* Jakarta EE 9 introduz uma alteração de namespace de `javax.*` para `jakarta.*`
* Todos os **DSCs personalizados** devem ser migrados para o namespace `jakarta.*`
* O AEM Forms 6.5 LTS SP1 oferece suporte a **somente servidores de aplicativos baseados em Jakarta EE 9+**

Para obter mais informações, consulte **Migração do javax para o Jakarta Namespace**.

## Atualizar

Para obter instruções detalhadas de atualização, consulte o [Guia de Atualização para o AEM Forms 6.5 LTS SP1 no JEE](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

## Instalação

Para obter etapas e pré-requisitos de instalação, consulte o **Guia de Instalação do AEM Forms 6.5 LTS SP1 (JEE)**.

## Plataformas compatíveis

Para obter a lista completa de plataformas, sistemas operacionais, bancos de dados e servidores de aplicativos compatíveis, consulte:

**Matriz de Plataformas Compatíveis - AEM Forms 6.5 LTS SP1 (JEE)**

## Recursos obsoletos e removidos

* A persistência de repositório do **RDBMK** para CRX foi removida.
* Para ambientes clusterizados, **somente MongoMK** tem suporte para persistência de repositório.

## Migração do javax para o Jakarta Namespace

### Migração de `javax` para o Namespace `jakarta`

A partir do **AEM Forms 6.5 LTS SP1**, somente os servidores de aplicativos que implementam a **API do Servlet Jakarta 5/6** têm suporte. Com **Jakarta EE 9 e posterior**, todas as APIs passaram do namespace `javax.{}` para `jakarta.`.

Como resultado, **todos os DSCs personalizados devem usar o `jakarta` namespace**. Os componentes personalizados criados com as APIs do `javax.{}` são **incompatíveis** com os servidores de aplicativos com suporte.

### Opções de migração para DSCs personalizados

Você pode migrar DSCs personalizados existentes usando uma das seguintes abordagens:

#### Opção 1: Migração de código do Source (recomendada)

* Atualizar todas as instruções de importação de `javax.{}` para `jakarta.`
* Reconstruir e recompilar os projetos DSC personalizados
* Reimplante os componentes atualizados no servidor de aplicativos

**Vantagens:**

* Garante compatibilidade de longo prazo com o Jakarta EE 9+
* Mais adequado para projetos mantidos ativamente

#### Opção 2: migração binária usando o transformador do Eclipse

* Use a ferramenta **Eclipse Transformer** para converter binários compilados (`.jar`, `.war`) de `javax` para `jakarta`
* Não é necessária nenhuma alteração ou recompilação do código-fonte
* Reimplantar os binários transformados no servidor de aplicativos

>[!NOTE]
>
> A transformação binária é executada no **nível de código de bytes**.

Mapeamentos de Importação de Exemplo

Abaixo estão exemplos comuns de alterações de namespace necessárias durante a migração:

Antes (javax)    Depois (Jacarta)
javax.servlet.*    jakarta.servlet.*
javax.servlet.http.*    jakarta.servlet.http.*

### Mapeamentos de Importação de Exemplo

A tabela a seguir mostra as alterações comuns do namespace necessárias durante a migração de `javax` para `jakarta`:

| Antes de (`javax`) | Depois de (`jakarta`) |
| ---------------------- | ------------------------ |
| `javax.servlet.*` | `jakarta.servlet.*` |
| `javax.servlet.http.*` | `jakarta.servlet.http.*` |

Use esses mapeamentos como referência ao atualizar o código fonte DSC personalizado ou validar binários transformados.

