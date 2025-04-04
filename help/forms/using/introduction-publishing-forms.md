---
title: Introdução à publicação de formulários em um portal
description: O Adobe Experience Manager Forms fornece componentes que você pode usar para criar seu portal do Forms. Este artigo apresenta os componentes disponíveis do Forms Portal.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 1%

---

# Introdução à publicação de formulários em um portal{#introduction-to-publishing-forms-on-a-portal}

| Versão | Link do artigo |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Clique aqui](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html?lang=pt-BR) |
| AEM 6.5 | Este artigo |


## Visão geral dos componentes do portal do AEM Forms {#aem-forms-portal-components-overview}

Em um cenário típico de implantação de portal centrada em formulários, o desenvolvimento de formulários e o desenvolvimento de portal são duas atividades distintas. Enquanto os designers de formulários criam e armazenam formulários em um repositório, os desenvolvedores da Web criam um aplicativo da Web para listar formulários e manipular o envio de formulários. Os Forms são copiados para o nível da Web, pois não há comunicação entre o repositório de formulários e o aplicativo web.

Esses cenários geralmente resultam em problemas de gerenciamento e atrasos de produção. Por exemplo, se houver uma versão mais recente de um formulário disponível no repositório, você deverá substituir o formulário no nível da Web, modificar o aplicativo da Web e reimplantar o formulário no site público. A reimplantação do aplicativo Web pode causar algum tempo de inatividade do servidor. Normalmente, o tempo de inatividade do servidor é uma atividade planejada e, portanto, as alterações não podem ser enviadas para o site público instantaneamente.

A AEM Forms fornece componentes de portal que reduzem as despesas gerais de gerenciamento e os atrasos de produção. Os componentes fazem com que os desenvolvedores da Web criem e personalizem um Forms Portal em sites criados usando o Adobe Experience Manager (AEM).

![Portal do AEM Forms](assets/aem-forms-portal.png)

Os componentes do portal de formulários permitem que você adicione a seguinte funcionalidade:

* Listar formulários em layouts personalizados. Os layouts de exibição de Lista, Cartão e Painel prontos para uso são fornecidos. Você pode criar seus próprios layouts personalizados.
* Permite exibir metadados personalizados e ações personalizadas ao listá-los.
* Listar formulários publicados pela interface do usuário do AEM Forms na instância de publicação em que os componentes do Forms Portal estão sendo usados.
* Permitir que os usuários finais renderizem formulários nos formatos HTML e PDF.
* Use o perfil personalizado do HTML para renderizar formulários.
* Permita a pesquisa de formulários com base em vários critérios, como propriedades de formulário, metadados e tags.
* Enviar dados de formulário para um servlet.
* Use o CSS personalizado para personalizar a aparência do portal.
* Criar links para formulários.
* Lista rascunhos e envios relacionados ao Formulário adaptável criado pelo usuário final.

## Componentes disponíveis do AEM Forms Portal {#available-aem-forms-portal-components}

A AEM Forms fornece os seguintes componentes de portal prontos para uso, agrupados em **Serviços de Documento** e **Predicados de Serviços de Documento** grupos de componentes:

### Pesquisa e Lister {#search-amp-lister}

O componente de Pesquisa e Lister permite listar formulários do repositório de formulários na página do portal e fornece opções de configuração para listar formulários com base em critérios especificados. Também permite especificar critérios de pesquisa para permitir que os usuários do portal pesquisem na lista de formulários.

### Rascunhos e envios {#drafts-amp-submissions}

Enquanto o componente Pesquisa e Lister exibe formulários que são tornados públicos pelo autor do Forms, o componente Rascunhos e envios exibe formulários que são salvos como rascunho para concluir formulários posteriores e enviados. Este componente fornece experiência personalizada para qualquer usuário conectado.

### Link {#link}

O componente Link permite criar um link para um formulário em qualquer lugar da página. Considere um cenário em que você está oferecendo um programa de treinamento e deseja que seus usuários enviem um formulário para se registrarem no treinamento. Em seu site, você postou os detalhes do programa. Abaixo dos detalhes, você deseja fornecer um link para o formulário de registro. O componente Link pode ajudar você a criar esse link.

## Fluxo de trabalho do portal do Forms {#forms-portal-workflow}

O Forms Portal permite listar formulários do repositório de formulários na página do portal. Também permite especificar critérios de pesquisa para permitir que os usuários do portal pesquisem na lista de formulários. Você também pode usar o componente Rascunhos e envios para exibir formulários salvos como rascunho para preencher formulários e enviados posteriormente. Você executa um determinado conjunto de operações antes que essas funcionalidades fiquem disponíveis em uma página do Sites. Execute as etapas na sequência listada para disponibilizar os componentes e as respectivas funcionalidades em uma página de sites:

1. **Habilitar componentes do Forms Portal**: por padrão, os componentes do Forms Portal não estão disponíveis para uso. [Habilitar os componentes do AEM sidekick](/help/forms/using/enabling-forms-portal-components.md) para uma página do AEM Sites.
1. **Listar formulários em uma página (criar página do Forms Portal):** Você pode listar formulários em páginas do AEM Sites e de sites que não sejam da AEM. A lista contém formulários disponíveis na instância de publicação. Um usuário pode abrir formulários e começar a preenchê-los. Sempre que um usuário abrir um formulário, uma nova instância do formulário será criada:

   1. **Listar formulários em uma página do AEM Sites**: adicione o componente **[Pesquisa e Listagem](../../forms/using/creating-form-portal-page.md)** à página e configure o **[Painel de Lista](../../forms/using/creating-form-portal-page.md#p-list-pane-p)** nela para listar formulários em uma página. Adicione e configure o componente **Painel de Pesquisa** para o componente **Pesquisa e Lister** também para adicionar a funcionalidade de pesquisa à página. A página com o componente Forms Portal é conhecida como [página Forms Portal](../../forms/using/creating-form-portal-page.md).

   1. **Formulários de lista em uma página que não seja do AEM Sites:** Use as [APIs de pesquisa do Forms Portal](/help/forms/using/listing-forms-webpage-using-apis.md) para consultar, recuperar e listar formulários em páginas que não sejam do AEM Sites.

1. **Listar rascunhos e formulários enviados em uma página do Forms Portal**: adicione e configure o componente Rascunhos e Envios à página do Forms Portal. O componente lista todos os formulários que estão no estado de rascunho e os formulários que já foram enviados.

   Para habilitar a exibição de um formulário adaptável enviado na guia envios, defina a **Ação de envio** como **[Ação de envio do portal do Forms](configuring-submit-actions.md).** Como alternativa, habilite a opção Enviar do Portal Forms. Sempre que um usuário enviar o formulário, ele será adicionado à guia Envios.

1. **Configure o armazenamento para os dados de rascunho e de formulários enviados:** Por padrão, os dados de rascunho e de envio são armazenados no repositório do AEM. Em um ambiente de produção, é recomendável não armazenar dados de formulário de rascunho ou enviados no repositório do AEM. [Configure o componente Forms Portal para salvar dados em um local seguro](../../forms/using/draft-submission-component.md#customizing-the-storage).
1. **(Opcional) Personalização dos componentes do Portal do Forms:** [Personalize seus modelos de página do Portal do Forms](../../forms/using/customizing-templates-forms-portal-components.md) para fornecer uma aparência distinta aos componentes.
1. **(Opcional) Adicionar metadados personalizados a formulários:** [Adicionar metadados personalizados a formulários](../../forms/using/customizing-templates-forms-portal-components.md) para melhorar a listagem e a experiência de pesquisa.
1. **Publicar a página do Portal do Forms:** A página do Portal do Forms está pronta. Publique a página.

## Artigos relacionados {#related-articles}

* [Habilitar componentes do Forms Portal](/help/forms/using/enabling-forms-portal-components.md)
* [Criar página do portal do Forms](../../forms/using/creating-form-portal-page.md)
* [Listar formulários em uma página da Web usando APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Usar componente de rascunhos e envios](../../forms/using/draft-submission-component.md)
* [Personalizar o armazenamento de rascunhos e formulários enviados](../../forms/using/draft-submission-component.md#customizing-the-storage)
* [Amostra para integrar o componente de rascunhos e envios ao banco de dados](integrate-draft-submission-database.md)
* [Personalização de modelos para componentes do Forms Portal](../../forms/using/customizing-templates-forms-portal-components.md)
* [Introdução à publicação de formulários em um portal](../../forms/using/introduction-publishing-forms.md)
