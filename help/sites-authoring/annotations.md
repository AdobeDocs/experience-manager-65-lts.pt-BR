---
title: Anotações ao editar uma página de conteúdo
description: Muitos componentes diretamente relacionados ao conteúdo permitem adicionar uma anotação.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 31%

---

# Anotações ao editar uma página{#annotations-when-editing-a-page}

Adicionar conteúdo às páginas do seu site geralmente está sujeito a discussões antes de realmente ser publicado. Para auxiliar nisso, muitos componentes diretamente relacionados ao conteúdo (em vez de, por exemplo, ao layout) permitem adicionar uma anotação.

Uma anotação coloca um marcador colorido/nota adesiva na página. A anotação permite a você (ou outros usuários) deixar comentários e/ou perguntas para outros autores/revisores.

>[!NOTE]
>
>A definição de um tipo de componente individual determina se é possível adicionar uma anotação (ou não) nas instâncias desse componente.

>[!NOTE]
>
>As anotações criadas na interface clássica são mostradas na interface habilitada para toque. No entanto, os rascunhos são específicos da interface do usuário e são exibidos somente na interface do usuário em que foram criados.

>[!CAUTION]
>
>A exclusão de um recurso (por exemplo, parágrafo) exclui todas as anotações e rascunhos associados a ele, independentemente de sua posição na página como um todo.

>[!NOTE]
>
>Dependendo dos seus requisitos, também é possível desenvolver um fluxo de trabalho para enviar notificações quando anotações são adicionadas, atualizadas ou excluídas.

## Anotações {#annotations}

Um [modo](/help/sites-authoring/author-environment-tools.md#page-modes) é usado para criar e visualizar anotações.

>[!NOTE]
>
>Não esqueça que [comentários](/help/sites-authoring/basic-handling.md#timeline) também estão disponíveis para fornecer feedback em uma página.

>[!NOTE]
>
>É possível anotar em vários recursos:
>
>* [Ativos de anotação](/help/assets/manage-assets.md#annotating)
>* [Anotação de ativos de vídeo](/help/assets/managing-video-assets.md#annotate-video-assets)
>

### Anotação em componente {#annotating-a-component}

O modo Anotar permite criar, editar, mover ou excluir anotações do seu conteúdo:

1. É possível entrar no modo Anotar usando o ícone na barra de ferramentas (canto superior direito) ao editar uma página:

   ![Anotar](do-not-localize/screen_shot_2018-03-22at110414.png)

   Agora é possível exibir todas as anotações existentes.

   >[!NOTE]
   >
   >Para sair do modo de Anotação, clique no ícone Anotar (símbolo x) à direita da barra de ferramentas superior.

1. Clique no ícone Adicionar anotação (símbolo de mais à esquerda da barra de ferramentas) para começar a adicionar anotações.

   >[!NOTE]
   >
   >Para interromper a adição de anotações (e voltar à exibição), clique no ícone Cancelar (símbolo x em um círculo branco) à esquerda da barra de ferramentas superior.

1. Clique no componente desejado (os componentes que podem ser anotados serão destacados com uma borda azul) para adicionar a anotação e abrir a caixa de diálogo:

   ![screen_shot_2018-03-22at110606](assets/screen_shot_2018-03-22at110606.png)

   Aqui você pode usar o campo e/ou ícone apropriado para:

   * Inserir o texto da anotação.
   * Criar um rascunho (linhas e formas) para realçar uma área do componente.

     O cursor se transformará em um fio cruzado ao criar um rascunho. Você pode desenhar várias linhas distintas. A linha de rascunho reflete a cor da anotação e pode ser uma seta, círculo ou forma oval.

     ![Esboço](do-not-localize/screen_shot_2018-03-22at110640.png)

   * Escolher/alterar a cor:

     ![Escolher/alterar cor](do-not-localize/chlimage_1-19.png)

   * Excluir a anotação.

     ![Excluir anotação](do-not-localize/screen_shot_2018-03-22at110647.png)

1. Você pode fechar a caixa de diálogo de anotação clicando/tocando fora dela. Uma exibição truncada (a primeira palavra) da anotação, juntamente com os rascunhos existentes, é mostrada:

   ![screen_shot_2018-03-22at110850](assets/screen_shot_2018-03-22at110850.png)

1. Depois que terminar de editar uma anotação específica, você pode:

   * Clique em um marcador de texto para abrir a anotação. Depois de aberta, você pode exibir o texto completo, fazer alterações ou excluir a anotação.

      * Os rascunhos não podem ser excluídos independentemente da anotação.

   * Reposicionar o marcador de texto.
   * Clique em uma linha de rascunho para selecionar esse rascunho e arrastá-lo para a posição desejada.
   * Mover ou copiar um componente

      * As anotações relacionadas e seus rascunhos também serão movidos ou copiados e sua posição em relação ao parágrafo permanecerá a mesma.

1. Para sair do modo Anotação e voltar ao modo usado anteriormente, clique no ícone Anotar (símbolo x) à direita da barra de ferramentas superior.

>[!NOTE]
>
>As anotações não podem ser adicionadas a uma página que foi bloqueada por outro usuário.

### Indicador de anotação {#annotation-indicator}

As anotações não aparecem no modo Editar, mas o selo na parte superior direita da barra de ferramentas mostra quantas anotações existem para a página atual. O selo substitui o ícone de Anotações padrão, mas ainda funciona como um link rápido que alterna de/para o modo Anotar:

![Indicador de anotações](assets/chlimage_1-242.png)
