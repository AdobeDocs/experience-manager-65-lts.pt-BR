---
title: Pesquisa abrangente
description: Encontre seu conteúdo mais rapidamente com a pesquisa abrangente.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 57%

---

# Pesquisar{#searching}

O ambiente de criação do AEM fornece vários mecanismos de pesquisa de conteúdo, dependendo do tipo de recurso.

>[!NOTE]
>
>Fora do ambiente de criação, outros mecanismos também estão disponíveis para pesquisa, como o [Construtor de Consultas](/help/sites-developing/querybuilder-api.md) e o [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Noções básicas de pesquisa {#search-basics}

A pesquisa está disponível na barra de ferramentas superior:

![Pesquisar](do-not-localize/chlimage_1-17.png)

Com o painel de pesquisa, você pode:

* Procure por uma palavra-chave, um caminho ou uma tag específica.
* Filtre de acordo com os critérios específicos dos recursos, como datas modificadas, status da página, tamanho do arquivo e assim por diante.
* Defina e use uma [pesquisa salva](#saved-searches) - com base nos critérios acima.

>[!NOTE]
>
>A pesquisa também pode ser invocada usando a tecla de atalho `/` (barra) sempre que o painel de pesquisa estiver visível.

## Pesquisar e filtrar {#search-and-filter}

Para pesquisar e filtrar os recursos:

1. Abra **Pesquisar** (com a lupa na barra de ferramentas) e insira o termo de pesquisa. Serão feitas sugestões e elas poderão ser selecionadas:

   ![s-01](assets/s-01.png)

   Por padrão, os resultados da pesquisa ficarão limitados à sua localização atual (ou seja, o console e o tipo de recurso relacionado):

   ![screen_shot_2018-03-23at101445](assets/screen_shot_2018-03-23at101445.png)

1. Se necessário, você pode remover o filtro de localização (selecione **X** no filtro que deseja remover) para pesquisar em todos os tipos de consoles/recursos.
1. Os resultados são mostrados, agrupados de acordo com o console e o tipo de recurso relacionado.

   Você pode selecionar um recurso específico (para a ação adicional) ou detalhar selecionando o tipo de recurso desejado; por exemplo, **Exibir todos os sites**:

   ![captura de tela_2019-03-05at101900](assets/screen-shot_2019-03-05at101900.png)

1. Se desejar mais detalhes, selecione o símbolo do Painel (parte superior esquerda) para abrir o painel lateral **Filtros e opções**.

   ![Filtros e opções](do-not-localize/screen_shot_2018-03-23at101542.png)

   De acordo com o tipo de recurso, a Pesquisa mostrará uma seleção predefinida de critérios de pesquisa/filtro.

   O painel lateral permite selecionar:

   * Pesquisas salvas
   * Diretório de pesquisa
   * Tags
   * Critérios de pesquisa; por exemplo, Datas modificadas, Status de publicação, Status da Live Copy.

   >[!NOTE]
   >
   >Os critérios de pesquisa podem variar:
   >
   >
   >
   >    * Dependendo do tipo de recurso selecionado; por exemplo, os critérios de Ativos e comunidades são compreensivelmente especializados.
   >    * Sua instância como o [Forms de Pesquisa](/help/sites-administering/search-forms.md) pode ser personalizada (adequada ao local no AEM).
   >
   >

   ![captura de tela_2019-03-05at102509](assets/screen-shot_2019-03-05at102509.png)

1. Você também pode adicionar outros termos de pesquisa:

   ![captura de tela_2019-03-05at102613](assets/screen-shot_2019-03-05at102613.png)

1. Feche a **Pesquisa** com o **X** (canto superior direito).

>[!NOTE]
>
>Os critérios de pesquisa são mantidos ao selecionar um item nos resultados da pesquisa.
>
>Quando você seleciona um item na página de resultados da pesquisa e retorna à página de pesquisa após usar o botão Voltar do navegador, os critérios de pesquisa permanecem.

## Pesquisas salvas {#saved-searches}

Além de pesquisar por uma grande variedade de aspectos, também é possível salvar uma configuração de pesquisa específica para recuperar e usar em um estágio posterior:

1. Defina seus critérios de pesquisa e clique em **Salvar**.

   ![captura de tela_2019-03-05at102613-1](assets/screen-shot_2019-03-05at102613-1.png)

1. Atribua um nome, em seguida, use **Salvar** para confirmar:

   ![captura de tela_2019-03-05at102725](assets/screen-shot_2019-03-05at102725.png)

1. Sua pesquisa salva estará disponível no seletor da próxima vez que você acessar o painel de pesquisa:

   ![captura de tela_2019-03-05at102927](assets/screen-shot_2019-03-05at102927.png)

1. Depois de salvo, é possível:

   * Usar o **x** (próximo ao nome da pesquisa salva) para iniciar uma nova consulta (a pesquisa salva em si não será excluída).
   * **Editar pesquisa salva**, alterar as condições de pesquisa e **Salvar** novamente.

As pesquisas salvas podem ser modificadas ao selecionar a pesquisa salva e clicar em **Editar pesquisa salva** na parte inferior do painel de pesquisa.

![captura de tela_2019-03-05at103010](assets/screen-shot_2019-03-05at103010.png)
