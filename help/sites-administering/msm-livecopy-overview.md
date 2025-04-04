---
title: Visão geral do console da Live Copy
description: Saiba mais sobre as noções básicas do Console de visão geral da Live Copy.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
feature: Multi Site Manager
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 32184455f3c74605a11c20152cf9c8879101a5c2
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 31%

---

# Visão geral do console da Live Copy{#live-copy-overview-console}

A **Visão geral da Live Copy** permite:

* Visualizar/gerenciar a herança em um site:

   * Visualizar a árvore do blueprint e a estrutura correspondente da live copy, junto com o status da herança
   * Alterar o status da herança; por exemplo, suspender, retomar
   * Exibir propriedades de blueprint e Live Copy

* Executar ações de implantação

## Abrir a visão geral da Live Copy {#opening-the-live-copy-overview}

Você pode abrir a visão geral da Live Copy em:

* [Painel lateral Referências de uma página do blueprint (console Sites)](#opening-live-copy-overview-references-for-a-blueprint-page)
* [Propriedades de uma página do blueprint](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Abrir a visão geral da Live Copy - referências para uma página do blueprint {#opening-live-copy-overview-references-for-a-blueprint-page}

A **Visão geral da Live Copy** pode ser aberta a partir do painel lateral **Referências** do console **Sites**:

1. No console **Sites**, [navegue até a página do blueprint e selecione-a](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Abra o painel **[Referências](/help/sites-authoring/basic-handling.md#references)** e selecione **Live Copies**.

   ![Painel de referências - Live copies](assets/chlimage_1-359.png)

   >[!NOTE]
   >
   >Você também pode abrir Referências primeiro e depois selecionar o blueprint.

1. Selecione **Visão geral da Live Copy** para exibir e usar a visão geral de todas as live copies relacionadas ao blueprint selecionado.
1. Use **Fechar** para sair e retornar ao console **Sites**.

### Abrir a visão geral da Live Copy - propriedades de uma página do blueprint {#opening-live-copy-overview-properties-of-a-blueprint-page}

A **Visão geral da Live Copy** pode ser aberta ao visualizar propriedades de uma página do blueprint:

1. Abra as **Propriedades** para a página do blueprint apropriada.
1. Abra a guia **Blueprint** e verá a opção **Visão geral da Live Copy** exibida na barra de ferramentas superior:

   ![Guia Blueprint - Visão geral da Live Copy](assets/chlimage_1-360.png)

1. Selecione **Visão geral da Live Copy** para exibir e usar a visão geral de todas as live copies relacionadas ao blueprint atual.

1. Use **Fechar** para sair e retornar ao console **Sites**.

## Usar a visão geral da Live Copy {#using-the-live-copy-overview}

A **Visão geral da Live Copy** também pode ser usada para executar ações na live copy:

1. Abra a **Visão geral da Live Copy**. 
1. Selecione o blueprint necessário ou a página de live copy - a barra de ferramentas será atualizada para mostrar as ações disponíveis. As [ações](/help/sites-administering/msm.md#terms-used) disponíveis dependem se você selecionar uma [blueprint](#actions-for-a-blueprint-page) ou uma [live copy](#actions-for-a-live-copy-page) página:

### Ações para uma página do blueprint {#actions-for-a-blueprint-page}

Quando você seleciona uma página do blueprint, as seguintes ações estão disponíveis:

![Blueprint selecionado - ações disponíveis](assets/chlimage_1-361.png)

* Editar

   * Abra a página do blueprint para edição.

* [Implantação](/help/sites-administering/msm.md#rollout-and-synchronize)

   * Execute uma implantação para enviar as alterações da origem para a live copy.

### Ações para uma página de Live Copy {#actions-for-a-live-copy-page}

Quando você seleciona uma página de live copy, as seguintes ações estão disponíveis:

![Página de Live Copy selecionada - ações disponíveis](assets/chlimage_1-362.png)

* Editar

   * Abra a página de live copy para edição.

* [Status do relacionamento](#relationship-status)

   * Exibir informações sobre o status e a herança.

* [Sincronizar](/help/sites-administering/msm.md#rollout-and-synchronize)

   * Sincronize uma live copy para extrair as alterações da origem para a live copy.

* [Redefinir](/help/sites-administering/msm-livecopy.md#resetting-a-live-copy-page)

   * Redefina uma página de live copy para remover todos os cancelamentos de herança e retornar a página ao mesmo estado que a página de origem.

* [Suspender](/help/sites-administering/msm.md#suspending-and-cancelling-inheritance-and-synchronization)

   * Desativa temporariamente a relação dinâmica entre uma live copy e sua página do blueprint.

* [Retomar](/help/sites-administering/msm-livecopy.md#resuming-inheritance-for-a-page)

   * Retomar permite restaurar uma relação suspensa.

* [Desconectar](/help/sites-administering/msm.md#detaching-a-live-copy)

   * Remove permanentemente o relacionamento dinâmico entre uma live copy e sua página de blueprint.

## Status do relacionamento {#relationship-status}

O console **Status do Relacionamento** tem duas guias que fornecem um intervalo de funcionalidades:

* [Informações de Status do Relacionamento](#relationship-status-information)
* [Informações da Live Copy](#live-copy-information)

### Informações de Status do Relacionamento {#relationship-status-information}

Essa guia fornece informações detalhadas sobre o status do relacionamento entre o blueprint e a live copy:

![Informações sobre o status do relacionamento](assets/chlimage_1-363.png)

### Informações da Live Copy {#live-copy-information}

Essa guia permite visualizar e editar a configuração da live copy:

![Informações da Live Copy](assets/chlimage_1-364.png)
