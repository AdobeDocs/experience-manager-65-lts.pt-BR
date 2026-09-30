---
title: Migração para o complemento da Estrutura de integração do AEM Commerce (CIF)
description: Como migrar de uma versão antiga para o complemento Estrutura de integração do AEM Commerce (CIF).
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 847c33c1-17d6-447a-9f2c-91f2a81a3f04
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 5%
---
# Guia de migração para o complemento do Experience Manager {#cif-migration}

Este guia ajuda a identificar as áreas que você precisa atualizar para a migração de complementos do Experience Manager.

## Complemento do CIF

O complemento CIF está disponível no [Portal de Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=commerce*&2_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3Aversion&2_group.propertyvalues.operation=equals&2_group.propertyvalues.0_values=target-version%3Aaem%2F6-5-lts&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=16). Ele é compatível e fornece os mesmos recursos que o complemento CIF para o Experience Manager as a Cloud Service.

Consulte [Introdução ao AEM Content and Commerce](getting-started.md).

Para prestar suporte a projetos que implantam a CIF, a Adobe fornece os [Componentes principais da CIF do AEM](https://github.com/adobe/aem-core-cif-components).

## Catálogo de produtos

A importação de dados do catálogo de produtos não é suportada pelo complemento CIF. Usando as entidades principais do complemento do CIF, as solicitações de produtos e catálogos são feitas sob demanda por meio de chamadas em tempo real para uma solução de comércio externo. Acesse o capítulo Integração para saber mais sobre a integração de uma solução comercial.

>[!TIP]
>
>Se nenhuma API em tempo real estiver disponível, um cache de produto externo com APIs deverá ser usado para a integração. Exemplo [código aberto do Magento](https://business.adobe.com/products/magento/open-source.html).

## Experiências do catálogo de produtos com renderização do AEM

Se você usar o blueprint do catálogo com o CIF clássico, será necessário atualizar o fluxo de trabalho do catálogo de produtos. O complemento CIF agora renderiza experiências de catálogo de produtos dinamicamente usando modelos de catálogo do AEM. Não é mais necessária a replicação de dados ou páginas de produtos.

## Interação de compra e dados não armazenáveis em cache

As solicitações do lado do cliente para dados e interações não armazenáveis em cache (por exemplo, adição ao carrinho, pesquisa) devem ir diretamente para o endpoint de comércio (solução de comércio ou camada de integração) por meio de CDN/Dispatcher. Remova todas as chamadas em que o AEM era apenas um proxy.
