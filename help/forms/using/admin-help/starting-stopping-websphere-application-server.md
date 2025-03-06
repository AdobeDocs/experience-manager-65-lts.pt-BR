---
title: Iniciando e interrompendo o WebSphere Application Server
description: Vários procedimentos exigem que você interrompa ou inicie a instância do WebSphere em que deseja implantar os produtos do AEM Forms. Este documento descreve como iniciar e parar o WebSphere Application Server.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 9ba3cdff6b61e57c13f27e09426aa2e19e01c8e5
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Iniciando e interrompendo o WebSphere Application Server {#starting-and-stopping-websphere-application-server}

Vários procedimentos exigem que você interrompa ou inicie a instância do WebSphere em que deseja implantar os produtos do AEM Forms. Se não tiver certeza se o servidor de aplicativos foi iniciado, você poderá exibir primeiro o status do WebSphere Application Server.

## Exibir o status do WebSphere Application Server {#view-the-status-of-websphere-application-server}

1. Em um prompt de comando, vá para o diretório `[appserver root]/bin`.
1. Digite o seguinte comando, substituindo *server_name* pelo nome do WebSphere Application Server:

   * (Windows) `serverStatus.bat`*nome_do_servidor*
   * (Linux, UNIX) ./ `serverStatus.sh`*nome_do_servidor*

## Iniciar o WebSphere Application Server {#start-websphere-application-server}

1. Em um prompt de comando, vá para o diretório `[appserver root]/bin`.
1. Digite o seguinte comando, substituindo *server_name* pelo nome do WebSphere Application Server:

   * (Windows) `startServer.bat`*nome_do_servidor*
   * (Linux, UNIX) ./ `startServer.sh`*nome_do_servidor*

## Interromper o Servidor de Aplicativos WebSphere {#stop-websphere-application-server}

1. Em um prompt de comando, vá para o diretório `[appserver root]/bin`.
1. Digite o seguinte comando, substituindo *server_name* pelo nome do WebSphere Application Server:

   * (Windows) `stopServer.bat`*nome_do_servidor*
   * (Linux, UNIX) ./ `stopServer.sh`*nome_do_servidor*
