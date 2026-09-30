---
title: Arquitetura do AEM Forms Workspace
description: Informações conceituais e visão geral da arquitetura do LiveCycle AEM Forms workspace.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
exl-id: d317274f-2c9a-4809-b43e-2efebc8fcb3f
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%
---
# Arquitetura do espaço de trabalho do AEM Forms {#aem-forms-workspace-architecture}

O espaço de trabalho do AEM Forms é um aplicativo web hospedado no CRX™. Quando um espaço de trabalho é aberto em um navegador, um recurso do CRX é acessado e o aplicativo é renderizado como uma página do HTML no navegador.

O aplicativo acessa o servidor do AEM Forms em pontos de extremidade REST para fazer o seguinte:

* Buscar tarefas do usuário, pontos de partida do processo, histórico do processo e informações do usuário
* Executar ação em tarefas
* Tarefas de consulta no banco de dados
* Atualizar preferências do usuário e muito mais

O servidor do AEM Forms acessa o banco de dados do AEM Forms pelo JDBC. O banco de dados mantém tarefas, processos e suas instâncias, usuários e informações relacionadas.

O espaço de trabalho do AEM Forms é projetado em componentes modulares do JavaScript que podem ser personalizados individualmente e reutilizados em outros aplicativos web. Os componentes são baseados no BackBone, que é uma biblioteca do JavaScript que fornece estrutura para aplicativos web. Um artigo detalhado descrevendo a interação de componentes com o BackBone está [aqui](/help/forms/using/backbone-interaction.md). A organização dos componentes na estrutura de pastas do CRX é discutida no artigo [this](/help/forms/using/folder-structure.md).

Pacotes entregues para o espaço de trabalho do AEM Forms:

* `adobe-lc-workspace-pkg-<version>.zip`: é um pacote do CRX, ou seja, pode ser implantado no CRX usando o Gerenciador de Pacotes.
* `adobe-lc-workspace-<version>-src.zip`: é um arquivo que contém o código completo do espaço de trabalho e scripts do AEM Forms para criar os pacotes de implantação — pacotes de Entrega, Depuração e Desenvolvimento.
