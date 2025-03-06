---
title: Introdução ao AEM Content and Commerce
description: Saiba como implantar um projeto do AEM Content and Commerce.
topics: Commerce
feature: Commerce Integration Framework
solution: Experience Manager,Commerce
role: Admin, Developer
exl-id: 15face30-3039-49a0-bfee-56bff21e5c27
source-git-commit: 2e0cbe62754866d31de69547f9af1f2f63930f2c
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 2%

---

# Introdução ao AEM Content and Commerce {#start}

Para começar a usar o AEM Content and Commerce, é necessário instalar o AEM Content and Commerce Add-On for AEM 6.5.


## Integração {#onboarding}

A integração do AEM Content and Commerce é um processo de duas etapas:

1. Instale o complemento Conteúdo e Commerce do AEM para AEM 6.5

2. Conectar o AEM com sua solução comercial

### Instale o complemento Conteúdo e Commerce do AEM para AEM 6.5 {#install-add-on}

Baixe e instale o Complemento AEM Commerce para AEM 6.5 no portal [Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html).

Inicie e instale o AEM 6.5 Service Pack necessário. Recomendamos instalar o último service pack disponível.

>[!NOTE]
>
>Isso será feito pelo CSE para clientes do AEM Managed Service.

### Conectar o AEM ao seu sistema Commerce {#connect}

O AEM pode ser conectado a qualquer sistema de comércio que tenha um endpoint do GraphQL acessível para o AEM. Esses endpoints geralmente estão disponíveis publicamente ou podem ser conectados por VPN privada ou conexões locais, dependendo da configuração individual do projeto.

Opcionalmente, o cabeçalho de autenticação pode ser fornecido para usar recursos adicionais do CIF que exigem autenticação.

Os projetos gerados pelo [Arquétipo de Projetos AEM](https://github.com/adobe/aem-project-archetype) e pela [Loja de Referência AEM Venia](https://github.com/adobe/aem-cif-guides-venia) que já estão incluídos na [configuração padrão](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) devem ser ajustados.

Substitua o valor de `url` em `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` pelo ponto de extremidade GraphQL do sistema de comércio. Essa configuração pode ser feita por meio do console OSGI ou implantando a configuração OSGI por meio do projeto. Diferentes configurações para sistemas de preparo e produção são compatíveis com o uso de diferentes modos de execução do AEM.

O Complemento de conteúdo e Commerce do AEM e os Componentes principais do CIF usam conexões do lado do servidor e do lado do cliente do AEM. Os Componentes principais do CIF do lado do cliente e as ferramentas de criação do complemento do CIF se conectam por padrão ao `/api/graphql`. Isso pode ser ajustado por meio da configuração do CIF Cloud Service, se necessário (veja abaixo).

O Complemento do CIF fornece um servlet de proxy do GraphQL em `/api/graphql` que pode ser usado opcionalmente para [desenvolvimento local](develop.md). Para implantações de produção, é altamente recomendável configurar um proxy reverso para o endpoint do GraphQL de comércio por meio do AEM Dispatcher ou em outras camadas de rede (como o CDN).

## Configurando lojas e catálogos {#catalog}

O Complemento e os [Componentes Principais do CIF](https://github.com/adobe/aem-core-cif-components) podem ser usados em várias estruturas de site do AEM conectadas a diferentes lojas de comércio (ou exibições de loja e assim por diante). Por padrão, o complemento CIF é implantado com uma configuração padrão conectada ao armazenamento e catálogo padrão da Adobe Commerce.

Essa configuração pode ser ajustada para o projeto por meio da configuração do CIF Cloud Service, seguindo estas etapas:

1. No AEM, acesse Ferramentas > Serviços da nuvem > Configuração do CIF

2. Selecione a configuração de comércio que deseja alterar

3. Abrir as propriedades de configuração por meio da barra de ações

![Configuração do CIF Cloud Services](/help/commerce/cif/assets/cif-cloud-service-config.png)

As seguintes propriedades podem ser configuradas:

- Cliente GraphQL - selecione o cliente GraphQL configurado para comunicação de back-end de comércio. Normalmente, isso deve permanecer no padrão.
- Exibição de loja - o identificador de exibição de loja. Se estiver vazia, a exibição de loja padrão será usada.
- Caminho de proxy do GraphQL - o caminho de URL que o Proxy da GraphQL no AEM usa para solicitações de proxy para o endpoint do GraphQL de back-end de comércio.

  >[!NOTE]
  >
  >Na maioria das configurações, o valor padrão `/api/graphql` não deve ser alterado. Somente a configuração avançada que não usa o proxy do GraphQL fornecido deve alterar essa configuração.

- Habilitar suporte ao UID do catálogo - habilite o suporte para o UID em vez da ID nas chamadas de GraphQL de back-end de comércio.

  >[!NOTE]
  >
  >O suporte para UIDs foi introduzido no Adobe Commerce 2.4.2. Habilite isso somente se o back-end de comércio suportar um esquema do GraphQL versão 2.4.2 ou posterior.

- Identificador de categoria raiz do catálogo - o identificador (UID ou ID) da raiz do catálogo de armazenamento

  >[!CAUTION]
  >
  >A partir da versão 2.0.0 dos Componentes Principais do CIF, o suporte para `id` foi removido e substituído por `uid`. Se o seu projeto usar os Componentes principais do CIF versão 2.0.0, você deverá ativar o Suporte ao UID do catálogo e usar uma categoria válida do UID como &quot;Identificador de categoria raiz do catálogo&quot;.

A configuração mostrada acima serve como referência. Os projetos devem fornecer suas próprias configurações.

Para configurações mais complexas usando várias estruturas de site do AEM combinadas com diferentes catálogos de comércio, consulte o tutorial [Configuração de várias lojas do Commerce](configuring/multi-store-setup.md).

## Recursos adicionais {#additional-resources}

- [Arquétipo de projeto do AEM](https://github.com/adobe/aem-project-archetype)
- [Loja de referência Venia](https://github.com/adobe/aem-cif-guides-venia)
- [Configuração de várias lojas do Commerce](configuring/multi-store-setup.md)
