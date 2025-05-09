---
title: Implantação de práticas recomendadas
description: Saiba como implantar e manter o Adobe Experience Manager (AEM) da maneira mais eficiente e eficaz possível.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 4f830ee9-e0e3-48df-b67d-709258cb1991
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 5%

---

# Implantação de práticas recomendadas{#deploying-best-practices}

A implantação de práticas recomendadas descreve como implantar ou manter o Adobe Experience Manager (AEM) da maneira mais eficiente e eficaz possível. Essa lista crescente de tópicos inclui várias áreas no AEM.

As seguintes áreas têm documentação disponível sobre implantação e manutenção de práticas recomendadas e recomendações:

* [Oak](#oak)
* [Interface](#ui)
* [Desempenho](#performance)

Para obter as práticas recomendadas sobre administração, desenvolvimento ou criação, consulte uma das seguintes opções:

* [Administração de práticas recomendadas](/help/sites-administering/administer-best-practices.md)
* [Desenvolvimento de práticas recomendadas](/help/sites-developing/best-practices.md)
* [Práticas recomendadas de criação](/help/sites-authoring/best-practices.md)

Os documentos específicos são descritos e vinculados nas tabelas seguintes.

## Oak {#oak}

O [Oak](/help/sites-deploying/platform.md) é um repositório de conteúdo hierárquico escalável e eficiente que é a base do AEM.

<table>
 <tbody>
  <tr>
   <td><p>Escalabilidade, desempenho e recuperação de desastres</p> </td>
   <td><a href="/help/sites-deploying/performance.md">Desempenho e escalabilidade</a></td>
   <td>Fornece um white paper sobre a agilidade técnica, o alto desempenho e os recursos sólidos de recuperação de desastres</td>
  </tr>
  <tr>
   <td>Implantações recomendadas do Oak</td>
   <td><a href="/help/sites-deploying/recommended-deploys.md">Implantações recomendadas</a></td>
   <td>Descreve cenários de implantação</td>
  </tr>
  <tr>
   <td>Topologia de Mongo</td>
   <td><a href="/help/sites-deploying/recommended-deploys.md">Práticas recomendadas da topologia Mongo</a></td>
   <td>Descreve a topologia mongo - quando usar qual topologia.</td>
  </tr>
  <tr>
   <td>Opções de armazenamento de dados</td>
   <td><a href="/help/sites-deploying/data-store-config.md">Configuração de nós e armazenamentos de dados</a></td>
   <td>Este documento explica as práticas recomendadas para armazenar dados binários e nós de conteúdo. Inclui informações sobre o uso do armazenamento de dados do Amazon S3.</td>
  </tr>
  <tr>
   <td>Pesquisar no Oak</td>
   <td><a href="/help/sites-deploying/best-practices-for-queries-and-indexing.md">Práticas recomendadas para consultas e indexação</a><br /> </td>
   <td>Descreve as práticas recomendadas para indexar conteúdo.</td>
  </tr>
 </tbody>
</table>

## Interface {#ui}

Atualmente, o AEM tem duas interfaces do usuário: clássica e otimizada para toque na mesma versão. Portanto, os clientes têm de tomar uma decisão sobre qual usar durante a implementação do projeto. Este documento tem como objetivo ajudar a encontrar a escolha certa.

## Desempenho {#performance}

As práticas recomendadas para o desempenho estão listadas aqui:

<table>
 <tbody>
  <tr>
   <td>Práticas recomendadas para o Quality Assurance</td>
   <td><a href="/help/sites-deploying/configuring-performance.md#best-practices-for-quality-assurance">Práticas recomendadas para o Quality Assurance</a></td>
   <td>Uma visão geral padronizada dos problemas envolvidos na definição de um Conceito de Teste especificamente para testes de desempenho no seu ambiente <em>publicar</em>. Isso é de interesse principalmente para engenheiros de controle de qualidade, gerentes de projeto e administradores de sistema.</td>
  </tr>
  <tr>
   <td>Uso do Dispatcher com um CDN</td>
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=pt-BR#using-dispatcher-with-a-cdn">Uso do Dispatcher com um CDN</a></td>
   <td>Uma rede de entrega de conteúdo (CDN), como Akamai Edge Delivery ou Amazon Cloud Front, fornece conteúdo de um local próximo ao usuário final.</td>
  </tr>
  <tr>
   <td>Otimização do desempenho</td>
   <td><a href="/help/sites-deploying/configuring-performance.md">Otimização do desempenho</a></td>
   <td>Um problema importante é o tempo que o site leva para responder às solicitações do visitante.</td>
  </tr>
  <tr>
   <td>Teste de desempenho</td>
   <td><a href="/help/sites-deploying/best-practices-for-performance-testing.md">Práticas recomendadas para testes de desempenho</a></td>
   <td>Descreve as práticas recomendadas para executar testes de desempenho em uma implantação do AEM.<br /> </td>
  </tr>
 </tbody>
</table>
