---
title: Configuração de pontos de extremidade Remotos
description: Saiba como configurar pontos de extremidade remotos. Este documento explica como habilitar o aplicativo criado com o Flex para chamar o serviço usando o AEM Forms Remoting.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: d19b7265-42cc-41d9-9897-e7b044c4529c
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---

# Configuração de pontos de extremidade Remotos {#configuring-remoting-endpoints}

Um endpoint de comunicação remota permite que um aplicativo criado com o Flex chame o serviço usando o AEM Forms Remoting (obsoleto para o AEM Forms). Um ponto de extremidade remoto é criado automaticamente para cada serviço ativado. Um destino do Flex que tem o mesmo nome do endpoint é criado, e os clientes Flex podem criar objetos remotos que apontam para esse destino para chamar operações no serviço relevante.

## Configurações de ponto de extremidade de comunicação remota {#remoting-endpoint-settings}

**Método de Autenticação de Cliente do Flex:** Determina o tipo de resposta que o servidor envia de volta ao cliente quando o serviço chamado está habilitado para segurança, a operação invocada não dá suporte a invocações anônimas e o cliente transmite credenciais inválidas ou nenhuma.
