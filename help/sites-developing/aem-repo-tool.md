---
title: Ferramenta AEM Repo
description: A ferramenta AEM Repo é uma solução simples para transferir conteúdo JCR entre seu sistema de arquivos local e o servidor do AEM por meio da linha de comando comparável ao FTP. A ferramenta AEM Repo é semelhante à ferramenta Jackrabbit FileVault, mas é mais rápida, tem dependências mínimas e é um script bash simples.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Ferramenta AEM Repo{#aem-repo-tool}

A AEM Repo Tool é uma solução simples para transferir conteúdo JCR entre seu sistema de arquivos local e o servidor do AEM por meio da linha de comando comparável ao FTP. A AEM Repo Tool é semelhante à [ferramenta Jackrabbit FileVault](/help/sites-developing/ht-vlttool.md), mas é mais rápida, tem dependências mínimas e é um script bash simples.

Essa ferramenta simplifica a transferência de arquivos para o desenvolvedor e também pode ser integrada ao IntelliJ e ao Eclipse para tornar o desenvolvimento ainda mais eficiente.

## Visão geral {#overview}

Para um determinado caminho dentro de uma estrutura de cofre de arquivos `jcr_root` no sistema de arquivos, a Ferramenta de Repositório do AEM cria um pacote com um único filtro para toda a subárvore e o envia por push ao servidor (semelhante ao FTP `put`), o busca no servidor ( `get`) ou compara as diferenças ( `status` e `diff`).

A ferramenta não oferece suporte a vários caminhos de filtro ou ao `filter.xml` do FileVault.

>[!CAUTION]
>
>A AEM Repo Tool sempre substitui todo o arquivo ou diretório especificado.

## Download e documentação {#download-and-documentation}

A [AEM Repo Tool está disponível no GitHub neste link](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo), juntamente com instruções detalhadas de instalação e uso.

Se quiser baixar a origem da ferramenta AEM Repo, consulte o projeto GitHub vinculado abaixo.

CÓDIGO NO GITHUB

Você pode encontrar o código desta página no GitHub

* [Abrir projeto de ferramentas no GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Baixar o projeto como [um arquivo ZIP](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip)
