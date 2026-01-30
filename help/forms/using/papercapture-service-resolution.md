---
title: Artigo de solução de problemas para resolver o problema de falha do serviço PaperCapture ao executar operações de OCR (Optical Character Recognition, reconhecimento ótico de caracteres) em PDFs.
description: Saiba mais sobre as etapas para resolver o problema em que o serviço PaperCapture falha ao executar operações de OCR (Optical Character Recognition, reconhecimento ótico de caracteres) em PDFs.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: de3cd0ad-0b18-4d9a-8c6b-72cc16149cfc
source-git-commit: eb6f6b994fdd3b2b01e77700d2deb7bd2830ac8f
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 2%

---

# O serviço PaperCature não executa a operação de OCRs em PDFs

## Problema

Depois de atualizar para o AEM Forms Service Pack 6.5.21.0, o serviço `PaperCapture` falha ao executar operações de OCR (Reconhecimento Ótico de Caracteres) em PDFs. O serviço não gera saída na forma de um PDF ou um arquivo de log.

## Aplica-se a

Esta solução aplica-se a:

* AEM Forms em todos os servidores JEE (JBoss®, WebLogic, WebSphere®)
* AEM Forms em servidores OSGi

## Solução

1. Baixe o [Hotfix](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0) do Portal de Distribuição de Software.
1. Extraia e copie o conteúdo da pasta baixada.
1. Navegue até os caminhos abaixo para os servidores de aplicativos correspondentes:
   * **JBoss®**:
     `..\Adobe\Adobe_Experience_Manager_Forms\jboss\standalone\svcnative\PaperCaptureSvc`
   * **WebLogic**:
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **WebSphere®**:\
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **Configuração OSGi**:\
     `..\quickstart\crx-quickstart\bedrock\svcnative\PaperCaptureSvc`
1. Pare o servidor de aplicativos do AEM.
1. Substituir o conteúdo existente da pasta `PaperCaptureSvc` pelo conteúdo copiado.
1. Reinicie o servidor de aplicativos do AEM.

   >[!NOTE]
   >
   >A Adobe recomenda usar o comando `Ctrl + C` para reiniciar o SDK. Reiniciar o AEM SDK usando métodos alternativos, por exemplo, parar processos Java, pode levar a inconsistências no ambiente de desenvolvimento do AEM.
