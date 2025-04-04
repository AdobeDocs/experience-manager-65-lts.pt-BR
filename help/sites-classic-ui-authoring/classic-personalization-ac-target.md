---
title: Direcionamento do seu Adobe Campaign
description: A configuração da segmentação inclui a criação de segmentos, uma marca, uma campanha e experiências.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---

# Direcionamento do seu Adobe Campaign{#targeting-your-adobe-campaign}

Para direcionar seu informativo no Adobe Campaign, primeiro é necessário configurar a segmentação, que só está disponível na interface clássica. Depois disso, você poderá criar experiências direcionadas para o Adobe Campaign.

## Configuração da segmentação no AEM {#setting-up-segmentation-in-aem}

A configuração da segmentação inclui a criação de segmentos, uma marca, uma campanha e experiências. Você só pode criar um segmento na interface clássica. Você pode criar marcas, campanhas e experiências na interface habilitada para toque.

>[!NOTE]
>
>A ID de segmento precisa ser mapeada para a do lado do Adobe Campaign.

### Criação de segmentos {#creating-segments}

Para criar segmentos:

1. Abra o [console de segmentação](http://localhost:4502/miscadmin#/etc/segmentation) em **&lt;host>:&lt;port>/miscadmin#/etc/segmentation**.
1. Crie uma página e insira um título - por exemplo, **Segmentos AC** - e selecione o modelo **Segmento (Adobe Campaign)**.
1. Selecione a página criada na visualização de árvore no lado esquerdo.
1. Crie um segmento, por exemplo, direcionando usuários do sexo masculino, criando uma página no segmento criado chamado Masculino e selecione o modelo **Segmento (Adobe Campaign)**.
1. Abra a página de segmento criada e arraste e solte uma **ID de segmento** do sidekick na página.
1. Clique duas vezes na característica, insira a ID que representa, neste caso, o segmento macho definido no Adobe Campaign - por exemplo, **MASCULINO** - e clique em **OK**. A seguinte mensagem deve ser exibida: `targetData.segmentCode == "MALE"`
1. Repita as etapas para outro segmento, por exemplo, um segmento direcionado a usuários do sexo feminino.

### Criar uma marca {#creating-a-brand}

Para criar uma marca:

1. Em **Sites**, navegue até a pasta **Campanhas** (por exemplo, em We.Retail).
1. Clique em **Criar Página** e insira um título para a página, por exemplo, Marca We.Retail, e selecione o modelo **Marca**.

### Criar uma campanha {#creating-a-campaign}

Para criar uma campanha:

1. Abra a página **Marca** que você criou.
1. Clique em **Criar página** e insira um título para sua página, por exemplo, Campanha We.Retail, selecione o modelo **Campanha** e clique em **Criar**.

### Criação de experiências {#creating-experiences}

Para criar experiências para segmentos:

1. Abra a página **Campanha** que você criou.
1. Crie experiências para seus segmentos clicando em **Criar página** e inserindo um título para sua página, por exemplo, Masculino, já que você está criando uma experiência para o segmento Masculino, e selecione o modelo **Experiência**.
1. Abra a página Experiência criada.
1. Clique em **Editar** e abaixo de Segmentos clique em **Adicionar item**.
1. Insira o caminho para o segmento macho, por exemplo, `/etc/segmentation/ac-segments/male` e clique em **OK**. A seguinte mensagem deve ser exibida: *A experiência está direcionada para: Masculino*
1. Repita as etapas anteriores para criar uma experiência para todos os segmentos, por exemplo, o público-alvo feminino.

## Criação de informativo com conteúdo direcionado {#creating-a-newsletter-with-targeted-content}

Depois de criar segmentos, uma marca, uma campanha e uma experiência, você pode criar um informativo com conteúdo direcionado. Depois de criar a experiência, vincule as experiências aos seus segmentos.

Você pode criar o informativo com conteúdo direcionado na interface do usuário habilitada para toque e clássica. Este documento descreve o procedimento para a interface habilitada para toque.

Para criar um informativo com conteúdo direcionado:

1. Crie um boletim informativo com conteúdo direcionado: Abaixo de Campanhas por email no Geometrixx Outdoors, clique em **Criar** > **Página** e selecione um dos modelos do Adobe Campaign Mail.

   >[!NOTE]
   >
   >[Amostras de email só estão disponíveis no Geometrixx](/help/sites-developing/we-retail.md#weretail). Baixe o conteúdo de amostra do Geometrixx do Compartilhamento de pacotes.

1. No informativo, adicione um componente Texto e Personalization.
1. Adicione texto ao componente Texto e Personalization, como &quot;Este é o padrão&quot;.
1. Clique na seta ao lado de **Editar** e selecione **Direcionamento**.
1. Selecione sua marca no menu suspenso Marca e selecione sua Campanha. (Esta é a marca e a campanha que você criou anteriormente).
1. Clique em **Iniciar o direcionamento**. Os segmentos são exibidos na área Públicos. A experiência padrão é usada se nenhum dos segmentos definidos for correspondente.

   >[!NOTE]
   >
   >Por padrão, as amostras de email incluídas no AEM usam o Adobe Campaign como mecanismo de direcionamento. Para boletins informativos personalizados, talvez seja necessário selecionar o Adobe Campaign como mecanismo de direcionamento. Ao direcionar, clique em + na barra de ferramentas, insira um título para a nova atividade e selecione **Adobe Campaign** como mecanismo de direcionamento.

1. Clique em **Padrão**, em seguida, no componente Texto e Personalization adicionado e você verá o Alvo com uma seta. Clique no ícone para direcionar esse componente.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Navegue até outro segmento (Masculino), clique em **Adicionar oferta** e clique no ícone de adição +. Em seguida, edite a oferta.
1. Navegue até outro segmento (Feminino) e clique em **Adicionar oferta** e no ícone de adição +. Em seguida, edite esta oferta.
1. Clique em **Avançar** para ver o Mapeamento e em **Avançar** para ver as Configurações, que não se aplicam ao Adobe Campaign, e clique em **Salvar**.

   O AEM gera automaticamente o código de direcionamento correto para o Adobe Campaign quando o conteúdo é usado em um delivery dentro do Adobe Campaign

1. No Adobe Campaign, crie sua entrega - selecione **Entrega de email com conteúdo do AEM** e selecione a conta do AEM local, conforme apropriado, e confirme suas alterações.

   Na visualização HTML, as diferentes experiências dos componentes direcionados são incluídas no código de direcionamento do Adobe Campaign.

   ![chlimage_1-166](assets/chlimage_1-166.png)

   >[!NOTE]
   >
   >Se você também configurou os segmentos no Adobe Campaign, clicar em **Visualizar** mostrará as experiências de cada segmento.
