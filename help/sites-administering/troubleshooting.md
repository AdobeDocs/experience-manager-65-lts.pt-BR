---
title: Trabalhar com logs
description: Saiba como solucionar problemas do AEM trabalhando com logs.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---

# Trabalhar com logs{#working-with-logs}

Esta seção inclui informações detalhadas sobre logs disponíveis para ajudar a solucionar problemas.

>[!NOTE]
>
>Para obter mais informações sobre logs, consulte:
>
>* [Manutenção do Log de Auditoria no AEM](/help/sites-administering/operations-audit-log.md)
>* [Trabalhando com Registros de Auditoria e Arquivos de Log](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)

O CRX registra logs detalhados. Depois de descompactar e iniciar o Quickstart, você pode encontrar logs nos seguintes locais:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Ativando o Nível de Log DEBUG {#activating-the-debug-log-level}

O nível de log padrão é INFO, ou seja, as mensagens DEBUG não são registradas.

Para ativar o nível de log DEBUG, use o explorador do CRX para definir o

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

propriedade a ser depurada. Não deixe o log no nível de log DEBUG mais tempo do que o necessário, pois ele gera vários logs.

Uma linha no arquivo de depuração geralmente começa com DEBUG e, em seguida, fornece o nível de log, a ação do instalador e a mensagem de log. Por exemplo:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Os níveis de log são os seguintes:

| 0 | Erro fatal | A ação falhou e o instalador não pode continuar. |
|---|---|---|
| 1 | Erro | Falha na ação. A instalação continua, mas uma parte do CRX não foi instalada corretamente e não funcionará. |
| 2 | Aviso | A ação foi bem-sucedida, mas encontrou problemas. O CRX pode ou não funcionar corretamente. |
| 3 | Informações | A ação foi bem-sucedida. |

## Opção detalhada usada para solução de problemas {#verbose-option-used-for-troubleshooting}

Ao iniciar o CRX, você pode adicionar a opção -v (detalhada) à linha de comando como em:

` java -jar crx-<*version*>-<*edition*>.jar -v`

Use a opção detalhada para solução de problemas, pois essa opção exibe parte da saída de registro de início rápido no console.
