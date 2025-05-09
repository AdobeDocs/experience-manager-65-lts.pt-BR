---
title: Usar o modo de layout para redimensionar componentes e criar uma comunicação interativa
description: Definir a posição dos componentes usando a grade responsiva disponível no modo Layout
feature: Interactive Communication
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 1%

---

# Usar o modo Layout para redimensionar componentes {#use-layout-mode-to-resize-components}

A interface de criação do canal da Web de comunicação interativa permite redimensionar componentes usando o modo Layout. Arraste e solte pontos azuis dentro de colunas para definir os pontos inicial e final para posicionar componentes. Os pontos azuis são exibidos depois de tocar no componente na grade responsiva. A grade responsiva consiste em 12 colunas iguais. O sombreamento das cores branco e azul em colunas alternadas diferencia uma coluna da outra.

Você pode usar o modo Layout para redimensionar componentes para todos os tipos de dispositivos, como desktop, tablet, telefone e outros dispositivos menores. O tablet deriva automaticamente a configuração de layout da versão do desktop e os dispositivos menores derivam a configuração de layout do telefone. No entanto, você pode substituir as configurações derivadas automaticamente para definir uma configuração diferente para cada tipo de dispositivo.

>[!NOTE]
>
>Se você estiver criando o canal da Web usando o [canal de impressão como mestre](../../forms/using/create-interactive-communication.md) para uma comunicação interativa, os componentes disponíveis para redimensionamento também incluirão os subformulários e campos gerados automaticamente no canal da Web usando o canal de impressão. O canal da Web retém o layout dos elementos do canal de impressão no modo Layout.

## Modo de layout de acesso {#access-layout-mode}

Selecione **Layout** na lista suspensa que aparece na parte superior da interface de criação de Comunicação interativa ao lado da opção **Visualizar**. O formulário é exibido no modo Layout.

1. Faça logon na instância de autor do AEM e navegue até **Adobe Experience Manager** > **Forms** > **Forms e Documentos**.
1. Crie uma [Comunicação Interativa](../../forms/using/create-interactive-communication.md) ou abra uma existente.
1. Selecione **Layout** na lista suspensa que aparece na parte superior ao lado da opção **Visualizar**. O formulário é exibido no modo Layout.

   ![Modo de layout para Comunicações Interativas](assets/layout_mode_ic_new.png)

## Redimensionar componentes {#resize-components}

1. No modo Layout, selecione o componente a ser redimensionado. Os pontos azuis são exibidos no início e no fim da grade responsiva.
1. Arraste e solte os pontos azuis para definir a posição do componente na grade responsiva.

   ![Redimensionando usando o modo Layout](assets/layout_mode_resize_new_updated.png)

   A barra de ferramentas exibida ao tocar em componentes consiste nas seguintes opções:

   * **Pai:** selecione o pai de um componente.
   * **Flutuar para a nova linha:** Desloque o componente para a próxima linha se houver vários componentes dentro da mesma linha.

   Você pode desfazer todas as alterações de redimensionamento e aplicar o layout padrão ao painel que contém componentes redimensionados usando a opção **[!UICONTROL Reverter layout do ponto de interrupção]** ( ![Reverter ponto de interrupção](assets/reverttopreviouslypublishedversion.png)). Selecione o pai do componente redimensionado para exibir a opção.

   >[!NOTE]
   >
   >Não é possível redimensionar componentes de coluna de tabela, barra de ferramentas, botão da barra de ferramentas e área de destino usando o modo Layout. Use o modo Estilo para redimensionar esses componentes.

### Exemplo {#example}

**Objetivo:** você deseja inserir um componente de tabela e um componente de imagem e posicioná-los paralelamente uns aos outros em uma comunicação interativa.

1. Insira os componentes de tabela e imagem usando o modo de Edição no canal da Web de uma Comunicação interativa. O componente de imagem é exibido após o componente de tabela.
1. Alterne para o modo Layout e selecione o componente Tabela. Os pontos azuis para redimensionar a exibição do componente nas colunas 1 e 12.
1. Arraste e solte o ponto azul na coluna 12 para a coluna 6 da grade responsiva.

   ![Definir o ponto final da tabela](assets/layout_mode_end_point_table_new.png)

1. Da mesma forma, selecione o componente de Imagem e arraste e solte o ponto azul na coluna 1 para a coluna 7 da grade responsiva. Os componentes de tabela e imagem são exibidos paralelamente um ao outro.

   ![Tabela e imagem em paralelo no modo Layout](assets/table_image_parallel_new.png)

   Você pode selecionar o componente de Imagem e selecionar a opção **Flutuar para a nova linha**, disponível na barra de ferramentas, para deslocar o componente de Imagem para a próxima linha.

## Redimensionar painéis {#resize-panels-layout-mode}

Execute as seguintes etapas se desejar redimensionar o painel inteiro em vez de componentes individuais:

1. Selecione qualquer um dos componentes no painel que você deseja redimensionar, selecione ![Selecionar pai](assets/select_parent_icon.svg) e selecione a primeira opção na lista suspensa, se o painel for o pai imediato do componente.

   Os pontos azuis são exibidos no início e no fim da grade responsiva.

1. Arraste e solte os pontos azuis para definir a posição do painel na grade responsiva.
Você pode repetir as etapas 1 e 2 e selecionar ![Selecionar pai](assets/float_to_new_line_icon.svg) para deslocar o painel redimensionado para a próxima linha.

## Definir layout de várias colunas para um painel

Execute as seguintes etapas para definir o número de colunas para um painel:

1. No modo **[!UICONTROL Editar]**, selecione o painel, selecione ![Configurar](assets/configure_icon.png) e selecione a opção **[!UICONTROL Responsivo - tudo na página sem navegação]** da lista suspensa **[!UICONTROL Layout do Painel]**.

1. Selecione ![Salvar](assets/save_icon.svg) para salvar as propriedades.

1. No modo **[!UICONTROL Layout]**, selecione qualquer um dos componentes no painel, selecione ![Selecionar pai](assets/select_parent_icon.svg) e selecione o painel.

1. Selecione ![multi-column](assets/multi-column.svg) e selecione o número de colunas na lista suspensa. O número de colunas pode variar de 1 a 12. O painel é dividido em um layout de várias colunas.

![várias colunas no modo de layout](assets/multi-column-layout.png)

## Desativar o modo Layout para formulários com layout responsivo antigo {#disable-layout-mode-for-forms-with-old-responsive-layout}

Você pode desativar o modo Layout para formulários com layout responsivo antigo editando propriedades para o modelo usado no formulário.

Execute as seguintes etapas para desativar o modo Layout:

1. Selecione **[!UICONTROL Ferramentas]** > **[!UICONTROL Geral]** > **[!UICONTROL Modelos]** e abra o modelo usado no formulário no modo **[!UICONTROL Editar]**.
1. Selecione o Contêiner de documentos no painel esquerdo e selecione **[!UICONTROL Política.]**

   ![Desabilitar modo de layout](assets/policy_disable_layout_mode.png)

1. Selecione a guia **[!UICONTROL Configurações de Layout]** e selecione **[!UICONTROL Desabilitar Modo de Layout]**.
1. Selecione ![Salvar alterações](assets/save_icon.png) para salvar as propriedades do modelo.
