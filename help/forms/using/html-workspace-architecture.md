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
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Arquitetura do AEM Forms Workspace {#aem-forms-workspace-architecture}

O espaço de trabalho do AEM Forms é um aplicativo web hospedado no CRX™. Quando o espaço de trabalho é aberto em um navegador, um recurso do CRX é acessado e o aplicativo é renderizado como uma página do HTML no navegador.

O aplicativo acessa o servidor do AEM Forms nos endpoints REST para fazer o seguinte:

* Buscar tarefas do usuário, pontos de partida do processo, histórico do processo e informações do usuário
* Executar ação em tarefas
* Tarefas de consulta no banco de dados
* Atualizar preferências do usuário e muito mais

O servidor do AEM Forms acessa o banco de dados do AEM Forms pelo JDBC. O banco de dados mantém tarefas, processos e suas instâncias, usuários e informações relacionadas.

O espaço de trabalho do AEM Forms é projetado em componentes modulares do JavaScript™ que podem ser personalizados individualmente e reutilizados em outros aplicativos da Web. Os componentes são baseados no BackBone, uma biblioteca do JavaScript que fornece estrutura para aplicações Web. Um artigo detalhado descrevendo a interação de componentes com o BackBone está [aqui](/help/forms/using/backbone-interaction.md). A organização dos componentes na estrutura de pastas do CRX é discutida no artigo [this](/help/forms/using/folder-structure.md).

Pacotes entregues para o espaço de trabalho do AEM Forms:

* `adobe-lc-workspace-pkg-<version>.zip`: é um pacote do CRX, ou seja, pode ser implantado no CRX usando o Gerenciador de Pacotes.
* `adobe-lc-workspace-<version>-src.zip`: é um arquivo que contém o código completo do espaço de trabalho e scripts do AEM Forms para criar os pacotes de implantação — pacotes de Entrega, Depuração e Desenvolvimento.
