---
title: Gerenciando programaticamente os PreferencesNodes
description: Use a API de serviço do Gerenciador de preferências (Java) para gerenciar os nós de preferências de forma programática.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 95a83858-c0b7-4c68-b4a9-d525bfc663c0
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 516393bc-fa69-5e74-a04e-f7ec9ffe2c5e
    internal-label: APIs & Integrations
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
---
# Gerenciando programaticamente os nós de preferências {#programmatically-managing-the-preferencesnodes}

**Exemplos e exemplos neste documento são somente para o AEM Forms no ambiente JEE.**

Este tópico descreve como você pode usar a API de serviço (Java) do Gerenciador de preferências para gerenciar os nós de preferências de forma programática.

Você pode alterar manualmente as definições de configuração na interface do Administrador. Para alterar as opções, navegue até `Home>Settings>User Management> Configuration>Manual Configuration`. Importar `config.xml` depois de fazer as alterações, você notará que todas as alterações, exceto as alterações feitas no nó `/Adobe/Adobe Experience Manager Forms/Config/UM persist`, foram perdidas. A visualização da Importação e Exportação do Gerenciamento de Usuários não oferece suporte à alteração das definições de configuração de outros componentes. Agora, essas alterações podem ser feitas usando as APIs `PreferencesManagerServiceClient`.

**Resumo das etapas**
Para gerenciar os nós de preferências programaticamente, faça o seguinte:

1. Inclua os arquivos do projeto.
1. Criar um cliente `PreferencesManagerService`.
1. Chame as operações de função ou permissão apropriadas.

**Incluir os arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente `PreferencesManagerService`**

Antes de executar programaticamente uma operação `PreferencesManagerService` do Gerenciamento de Usuários, você deve criar um cliente `PreferencesManagerService`. Com a API Java, crie um objeto `PreferencesManagerServiceClient`.

**Invocar as operações de permissão ou função apropriadas**

Depois de criar o cliente de serviço, você pode chamar as operações do Gerenciador de preferências. O cliente do serviço permite ler e definir permissões.
