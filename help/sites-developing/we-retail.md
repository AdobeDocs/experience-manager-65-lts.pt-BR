---
title: Implementação de referência do We.Retail
description: We.Retail é uma visualização de tecnologia de uma implementação de referência que ilustra a maneira recomendada de configurar uma presença online com o AEM
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: ac26c0163309b6cb6c0cfde2098a8cc05955d03f
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 7%

---

# Implementação de referência do We.Retail{#we-retail-reference-implementation}

## Introdução {#introduction}

We.Retail é uma implementação de referência e conteúdo de amostra que ilustra a maneira recomendada de configurar uma presença online com o Adobe Experience Manager.

O We.Retail usa as tecnologias mais recentes do Adobe Experience Manager (AEM), como HTL, layouts responsivos, modelos editáveis, componentes principais e muito mais.

Embora ele ilustre um vertical de varejo, a forma como o site é configurado pode ser aplicada a qualquer vertical e somente os recursos do catálogo de produtos e do carrinho são específicos de varejo.

## Recursos {#features}

Como a implementação de referência padrão do AEM, o We.Retail apresenta alguns dos recursos mais avançados do AEM.

| **Recurso** | **Descrição** | **Interessado?** |
|---|---|---|
| [Estrutura de site globalizada](/help/sites-administering/tc-bp.md) | O We.Retail inclui matrizes de idioma que são copiadas em tempo real para sites específicos de cada país. | [Experimente!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [Layout responsivo](/help/sites-authoring/responsive-layout.md) | Todas as páginas apresentam um layout responsivo para adaptar dinamicamente à tela e ao tamanho do dispositivo. | [Experimente!](/help/sites-developing/we-retail-responsive-layout.md) |
| [Modelos editáveis](/help/sites-developing/page-templates-editable.md) | Todas as páginas são baseadas em modelos editáveis, permitindo que não desenvolvedores adaptem e personalizem os modelos. | [Experimente!](/help/sites-developing/we-retail-editable-templates.md) |
| [Linguagem de Modelo do HTML](https://experienceleague.adobe.com/pt-br/docs/experience-manager-htl/content/overview) | Todos os componentes são baseados em HTL |  |
| [Componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction) | Todos os componentes são baseados nos novos componentes principais e são mais utilizáveis e configuráveis pelo usuário, prontos para uso | [Experimente!](/help/sites-developing/we-retail-core-components.md) |
| [Fragmentos de conteúdo](/help/assets/content-fragments/content-fragments.md) | A seção Experiências do We.Retail mostra o poder de reutilizar conteúdo por meio de fragmentos de conteúdo. | [Experimente-os!](/help/sites-developing/we-retail-content-fragments.md) |
| [Fragmentos de experiência](/help/sites-authoring/experience-fragments.md) | Um Fragmento de experiência é um grupo de um ou mais componentes, incluindo conteúdo e layout, que podem ser referenciados nas páginas. | [Experimente-os!](/help/sites-developing/we-retail-experience-fragments.md) |

## Introdução {#getting-started}

O We.Retail é fornecido como conteúdo de amostra do AEM. Para usar o, basta [iniciar o AEM como você faria normalmente](/help/sites-deploying/deploy.md#getting-started), certificando-se de que o conteúdo de amostra não esteja desativado.

>[!CAUTION]
>
>Não instale o We.Retail em instâncias de produção. As instâncias de Produção devem ser iniciadas no `nosamplecontent` [modo de execução](/help/sites-deploying/configure-runmodes.md).

>[!CAUTION]
>
>O We.Retail é baseado na tecnologia mais recente do AEM e, portanto, não oferece suporte à [criação da interface clássica](/help/sites-classic-ui-authoring/classic-page-author-first-steps.md).

### Versão mais recente {#latest-version}

Embora o We.Retail seja distribuído com a versão do AEM, as atualizações do conteúdo e de seus recursos podem ser feitas após o lançamento. Portanto, é possível [baixar a versão mais recente do GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) e depois [carregá-la](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) e [instalá-la](/help/sites-administering/package-manager.md#installing-packages) como um pacote na sua instância do AEM.

### Primeiras etapas {#first-steps}

1. Depois que o AEM for iniciado (e/ou que o We.Retail for instalado), o site **We.Retail** estará disponível no [console Sites](/help/sites-authoring/basic-handling.md#global-navigation).
1. Por exemplo, a seguinte página pode ser aberta e deve parecer como exibida no [apêndice](#appendix) abaixo:

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## We.Retail e Geometrixx {#we-retail-geometrixx}

O Geometrixx e suas várias encarnações serviram como conteúdo de amostra em versões anteriores do AEM. Desde a versão 6.3, We.Retail é o conteúdo de amostra entregue com o AEM e serve como a nova implementação de referência padrão.

O We.Retail é tecnicamente mais robusto e explora a mais recente tecnologia da AEM para ser mais flexível e escalável, além de demonstrar os recursos mais recentes do produto.

### Comparação de recursos {#feature-comparison}

A tabela a seguir fornece uma visão geral dos principais recursos disponíveis no We.Retail em comparação ao Geometrixx.

* **Disponível** significa que exemplos do recurso foram encontrados no conteúdo de exemplo.
* **Não disponível** significa que exemplos do recurso não estão disponíveis no conteúdo de exemplo, mas não significa que o recurso em si não esteja.

| **Recurso** | **We.Retail** | **Geometrixx** |
|---|---|---|
| Estrutura do site globalizada | Idiomas principais copiados para sites específicos do país | Não disponível |
| Fragmentos de conteúdo | Disponível | Não disponível |
| Fragmentos de experiência | Disponível | Não disponível |
| Layout responsivo | Para todas as páginas | Somente Geometrixx Media |
| Modelos editáveis | Para todas as páginas | Não disponível |
| HTL | Todos os componentes | Limitado |
| Direcionamento | Para todas as páginas | Somente Geometrixx Outdoors |
| Manuscritos | Não disponível | Disponível |
| Visualizador do carrossel, downloads e componentes de gráfico | Não disponível | Disponível |
| Controle de coluna | Substituído pelo contêiner de layout | Disponível |
| Forms | Não disponível | Disponível |
| Campaign | Nenhuma amostra de email | Disponível |

>[!NOTE]
>
>Essa lista se esforça para ser completa, mas não deve ser considerada exaustiva.

## Contribute {#contribute}

O We.Retail foi lançado como um projeto de código aberto e a versão mais recente do código-fonte pode ser baixada do GitHub.

CÓDIGO NO GITHUB

Você pode encontrar o código desta página no GitHub.

* [Abrir projeto aem-sample-we-retail no GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* Baixar o projeto como [um arquivo ZIP](https://codeload.github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/zip/refs/heads/master)

A versão mais recente também pode ser [baixada diretamente](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/tag/we.retail.reactor-4.0.0) como um pacote instalável.

Se você encontrar problemas, registre um [problema do GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues).

Fique à vontade para bifurcar ou contribuir com [solicitações de pull](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls).

## Visualização {#preview}

Pré-visualização da página de boas-vindas do We.Retail:

![screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
