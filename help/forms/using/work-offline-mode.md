---
title: Trabalhar no modo offline
description: Coloque seu dispositivo móvel offline fora do alcance da rede AEM Forms ou em um modo totalmente offline e trabalhe no aplicativo AEM Forms
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Trabalhar no modo offline {#working-in-the-offline-mode}

O modo offline do aplicativo AEM Forms permite que você trabalhe sem interrupções, mesmo que o aplicativo fique offline. Você pode abrir, atualizar e enviar um formulário sem precisar de conectividade de rede.

Você começa a trabalhar no aplicativo AEM Forms sincronizando o aplicativo com o servidor do AEM Forms. Todos os formulários atribuídos a você são baixados no aplicativo. Para o AEM Forms no JEE, as tarefas são buscadas na guia tarefas e os pontos de partida são formulários associados e outros formulários na guia Forms. Para o AEM Forms no OSGi, somente o Forms é carregado na guia Forms.

Para obter detalhes sobre como sincronizar o aplicativo, consulte [Sincronizando o aplicativo](/help/forms/using/sync-app.md).

## Disponibilização do Forms offline {#making-forms-available-offline}

Ao sincronizar o aplicativo com o servidor do AEM Forms, os formulários são baixados para o dispositivo móvel. No entanto, por padrão, os anexos associados ao formulário não são baixados. Isso significa que, se você estiver on-line, poderá exibir os anexos. No entanto, para garantir que você possa exibir o anexo no modo offline, altere as configurações padrão no aplicativo.

Para garantir que os anexos associados sejam baixados com cada formulário, defina Buscar anexos como ATIVADO. Para obter detalhes, consulte [Atualizando configurações gerais](/help/forms/using/update-general-settings.md).

Como o download de dados no dispositivo móvel pode afetar o desempenho do dispositivo, por padrão, a configuração Buscar anexos está definida como DESATIVADO. Os anexos são obtidos no dispositivo para qualquer tarefa que seja baixada do servidor depois que a configuração é atualizada para ATIVADA. No modo offline, um usuário pode trabalhar em todas as tarefas baixadas no dispositivo depois de definir as opções **Buscar anexos** como ATIVADAS.

## Configuração do serviço offline para o aplicativo AEM Forms {#configuring-offline-service-for-aem-forms-app-br}

O serviço off-line do aplicativo AEM Forms identifica os recursos usados em um formulário. O aplicativo AEM Forms depende desse serviço para obter informações sobre dependências de formulário. Informações sobre dependências de formulário são necessárias para habilitar funcionalidades offline. O serviço off-line do aplicativo AEM Forms armazena em cache os caminhos ou URLs dos recursos usados em um formulário. O cache é atualizado com base nas alterações no formulário e no período de validade configurado para o serviço offline. O armazenamento em cache de caminhos ou URLs dos recursos usados em um formulário melhora o desempenho do lado do servidor.

Para configurar o componente offline do lado do servidor do aplicativo AEM Forms:

1. Na instância do autor, navegue até **Adobe Experience Manager** >**Ferramentas** > **Forms** > **Configurar Serviço Offline do Aplicativo Forms**.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Em Configurações gerais, você pode executar o seguinte:

   * **Limpar Cache**: limpa o cache do lado do servidor das dependências de formulário.
   * **Redefinir Configuração**: redefine a configuração offline do aplicativo AEM Forms.
   * **Validade do Cache**: especifica o período de validade do cache offline do lado do servidor.
   * **Caminhos de Observação de Recursos**: especifica os caminhos em que o serviço offline monitora as alterações de recursos. Se ocorrerem alterações nos caminhos especificados, o cache offline de todos os formulários dependentes será atualizado. Por exemplo, `/etc/clientlibs/fd,/content/dam/images`.

1. Na guia **Cache de Recursos Manual**, especifique as dependências de formulário que o serviço offline não pode identificar. Você pode especificar recursos como imagens carregadas no JavaScript. O aplicativo AEM Forms baixará esses recursos também para o modo offline.
