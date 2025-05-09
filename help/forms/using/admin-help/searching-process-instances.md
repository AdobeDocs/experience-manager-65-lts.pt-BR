---
title: Pesquisando instâncias de processo
description: Utilize a página Pesquisa de Processo para informar critérios de pesquisa para localizar uma instância de processo.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: e358ee51-c23f-4737-9dcf-3193ed541bbb
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Pesquisando instâncias de processo{#searching-for-process-instances}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Utilize a página Pesquisa de Processo para informar critérios de pesquisa para localizar uma instância de processo. Você pode acessar a página Pesquisa de Processo na página de fluxo de trabalho de formulários ou clicando em Pesquisar na página Instância de Processo.

Você pode informar critérios básicos para executar uma pesquisa geral, atributos específicos para executar uma pesquisa detalhada ou uma combinação de critérios básicos e atributos específicos para executar uma pesquisa combinada.

## Realizar uma pesquisa geral {#perform-a-general-search}

Uma pesquisa geral de um processo é mais apropriada se você souber a ID do processo da instância do processo, se estiver procurando um grupo de instâncias de processo relacionadas ou se apenas algumas instâncias de processo estiverem em execução.

Informe os critérios básicos para executar uma pesquisa geral. Se você informar vários critérios, a pesquisa será executada com uma condição AND implícita.

1. No console de administração, clique em Serviços > Fluxo de trabalho do Forms > Pesquisa de processo.
1. Na página Pesquisa do processo, em Pesquisa geral, forneça os seguintes critérios:

   * **ID do Processo:** O inteiro positivo que identifica cada instância de processo exclusiva.
   * **Status do Processo:** Selecione um status na lista.
   * **Aplicativo:** selecione um aplicativo da lista. Somente os aplicativos implantados são exibidos.
   * **Nome do Processo - Versão:** Selecione um nome de processo no menu. Somente os processos implantados são exibidos.

1. Clique em Pesquisar. A página Instância do processo é exibida, listando as instâncias encontradas.

## Executar uma pesquisa detalhada para um processo {#perform-a-detailed-search-for-a-process}

Você pode informar atributos específicos para executar uma pesquisa detalhada. Uma pesquisa detalhada é mais apropriada se você tiver muitas instâncias de processo em execução e precisar restringir as possíveis localizações por determinados critérios.

1. No console de administração, clique em Serviços > Fluxo de trabalho do Forms > Pesquisa de processo.
1. Na página Pesquisa do processo, em Pesquisa detalhada, especifique seu primeiro conjunto de critérios:

   * Na lista Atributo, selecione um atributo.
   * Na lista Filtro, selecione um operador.
   * Na caixa Valor, digite um valor apropriado para o atributo selecionado.

1. Para adicionar outra linha, selecione Mais filtros. É exibido outro conjunto de listas de Atributo, Filtro e Valor e uma lista de Condições.
1. Em Condição, selecione AND ou OR. Repita as etapas de 1 a 3, conforme necessário, para restringir ainda mais sua pesquisa.
1. Para adicionar ou remover linhas, clique em Mais filtros ou Menos filtros. Você pode ter de uma a quatro linhas.
1. Clique em Pesquisar. A página Instância do processo é exibida, listando as instâncias encontradas.

[Sobre status de instância de processo](/help/forms/using/admin-help/processes.md#about-process-instance-statuses)

## Executar uma pesquisa combinada para um processo {#perform-a-combined-search-for-a-process}

Para criar uma pesquisa com base em uma pesquisa geral e em uma pesquisa detalhada, com um AND implícito entre as áreas, informe seus critérios de pesquisa nas áreas Pesquisa Geral e Pesquisa Detalhada na página Pesquisa do Processo.

Se a pesquisa for muito estreita, nenhuma instância será encontrada.
