---
title: Experimentar a estrutura globalizada de sites no We.Retail
description: Saiba como experimentar uma estrutura de site globalizada no Adobe Experience Manager usando o We.Retail.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Experimentar a estrutura globalizada de sites no We.Retail{#trying-out-the-globalized-site-structure-in-we-retail}

O We.Retail foi criado com uma estrutura de site globalizada que oferece um idioma principal que pode ser copiado para sites específicos de cada país. Tudo é configurado imediatamente para permitir que você experimente essa estrutura e os recursos de tradução integrados.

## Experimentando {#trying-it-out}

1. Abra o console Sites em **Navegação Global > Sites**.
1. Alterne para a exibição de coluna (se ainda não estiver ativa) e selecione We.Retail. Observe o exemplo de estrutura de país com Suíça, Estados Unidos, França e assim por diante, ao lado do Idioma principal.

   ![chlimage_1-87](assets/chlimage_1-87a.png)

1. Selecione Suíça e veja as raízes de idioma para os idiomas desse país. Ainda não há conteúdo abaixo dessas raízes.

   ![chlimage_1-88](assets/chlimage_1-88a.png)

1. Alterne para a exibição de lista e veja se as cópias de idioma dos países são todas live copies.

   ![chlimage_1-89](assets/chlimage_1-89a.png)

1. Retorne à exibição de coluna, clique no Idioma principal e veja as raízes do idioma principal com conteúdo. Somente o inglês tem conteúdo.

   O We.Retail não vem com nenhum conteúdo traduzido, mas a estrutura e a configuração estão em vigor para permitir que você demonstre os serviços de tradução.

   ![chlimage_1-90](assets/chlimage_1-90a.png)

1. Com a opção Idioma principal em inglês selecionada, abra o painel **Referências** no console de sites e selecione **Cópias de idioma**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Marque a caixa de seleção ao lado do rótulo **Cópias de idioma** para selecionar todas as cópias de idioma. Na seção **Atualizar cópias de idioma** do painel, selecione a opção para **Criar um novo projeto de tradução**. Forneça um nome para o projeto e clique em **Atualizar**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Um projeto é criado para cada tradução de idioma. Exiba em **Navegação > Projetos**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. Clique em Alemão para ver os detalhes do projeto de tradução. O status está em **Rascunho**. Para iniciar a tradução com o serviço de tradução da Microsoft®, clique na divisa ao lado do cabeçalho **Tarefa de tradução** e selecione **Iniciar**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. O projeto de tradução é iniciado. Clique nas reticências na parte inferior do cartão chamado Tarefa de tradução para ver os detalhes. As páginas com o estado **Pronto para revisão** já foram traduzidas pelo serviço de tradução.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Selecionar uma das páginas na lista e depois **Visualizar nos Sites** na barra de ferramentas abre a página traduzida no editor de páginas.

   ![chlimage_1-96](assets/chlimage_1-96.png)

>[!NOTE]
>
>Este procedimento demonstrou a integração integrada com a tradução automática da Microsoft®. Usando a [Estrutura de integração de tradução do AEM](/help/sites-administering/translation.md), você pode integrar muitos serviços de tradução padrão para orquestrar a tradução do AEM.

## Mais informações {#further-information}

Para obter mais informações, consulte o documento de criação [Tradução de conteúdo para sites multilíngues](/help/sites-administering/translation.md) para obter detalhes técnicos completos.
