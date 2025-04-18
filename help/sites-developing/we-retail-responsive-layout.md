---
title: Experimentar layout responsivo no We.Retail
description: Saiba como experimentar o Layout responsivo no Adobe Experience Manager usando o We.Retail.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 6%

---

# Experimentar layout responsivo no We.Retail{#trying-out-responsive-layout-in-we-retail}

Todas as páginas do We.Retail usam o componente de Contêiner de layout para implementar um design responsivo. O contêiner de layout fornece um sistema de parágrafo que permite posicionar componentes em uma grade responsiva. Essa grade pode reorganizar o layout de acordo com o tamanho e o formato do dispositivo/janela. O componente é usado em conjunto com o modo **Layout** no editor de páginas, que permite criar e editar seu layout responsivo dependendo do dispositivo.

## Experimentando {#trying-it-out}

1. Edite a página de Navegação no Ártico na seção Experiências da ramificação de idioma principal.

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html

1. Alterne para **Visualização** para ver a página como ela seria renderizada para um visitante do site. Role para baixo até o conteúdo do artigo *Almoços Aloha no norte da Noruega*.

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Redimensione a janela do navegador e observe enquanto o layout se adapta dinamicamente ao redimensionamento.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Alternar para o modo Layout. A barra de ferramentas do emulador é exibida automaticamente, permitindo planejar o layout por dispositivo direcionado.

   Selecionar um componente exibe as opções flutuantes e ocultas no menu de edição juntamente com as alças de redimensionamento do componente.

   ![chlimage_1-180](assets/chlimage_1-180.png)

1. A ação de arrastar e segurar a alça de redimensionamento do componente mostra automaticamente a grade do layout para ajudá-lo com o redimensionamento.

   ![chlimage_1-181](assets/chlimage_1-181.png)

## Informações adicionais {#further-information}

Para obter mais informações, consulte o documento de criação [Layout responsivo](/help/sites-authoring/responsive-layout.md) ou o documento do administrador [Configurando o contêiner de layout e o modo de layout](/help/sites-administering/configuring-responsive-layout.md) para obter detalhes técnicos completos.
