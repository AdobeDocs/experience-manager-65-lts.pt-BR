---
title: Não foi possível restaurar o repositório CRX corrompido aplicável ao servidor de cluster JEE
description: Saiba mais sobre como restaurar um repositório do CRX corrompido.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 716d8eb2-2010-4d55-b8fe-bd4f6f256a4d
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---

# Não foi possível restaurar o repositório CRX corrompido {#unable-to-restore-corrupt-crx-repository}

## Problema {#issue}

Para o AEM Forms no JEE que usa um banco de dados relacional, o tempo na máquina que hospeda o AEM Forms e o banco de dados relacional devem estar sempre em sincronia absoluta. Se o tempo nessas máquinas sair de sincronia, o repositório do CRX do AEM Forms no servidor JEE poderá ficar inacessível. Ele pode parecer corrompido e se tornar inacessível por meio do URL. O erro `AuthenticationsupportService missing` foi registrado em log.

## Pré-requisitos {#prerequisites}

Faça o backup do seu repositório CRX antes de executar as etapas mencionadas abaixo.

## Solução {#solution}

1. Ir para `https://[AEM Forms Server]:[port]/system/console/bundles`.

1. Localize o pacote `oak-core` e verifique se ele está em execução.

1. Reinicie o pacote `oak-core` se ele não estiver em execução. Se o ícone do ![Botão Pausar](/help/forms/using/assets/stop.png) estiver presente na frente do pacote `oak-core`, isso indicará que o pacote está em estado de execução.

1. Se o problema ainda não for resolvido, restaure a partir do repositório da CRX a partir do backup ou recrie o repositório da CRX se o backup não estiver disponível.


## Aplica-se a {#applies-to}

Essa solução se aplica ao AEM Forms no cluster JEE.
