---
title: Uso de tags
description: As tags são um método rápido e fácil de classificar conteúdo em um site. As tags podem ser consideradas palavras-chave ou rótulos que podem ser anexados a uma página, um ativo ou outro conteúdo para permitir que as pesquisas localizem esse conteúdo e outros relacionados.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 39%

---

# Uso de tags{#using-tags}

As tags são um método rápido e fácil de classificar conteúdo em um site. As tags podem ser consideradas palavras-chave ou rótulos que podem ser anexados a uma página, um ativo ou outro conteúdo para permitir que as pesquisas localizem esse conteúdo e outros relacionados.

* Consulte [Administrando tags](/help/sites-administering/tags.md) para obter informações sobre como criar e gerenciar tags e às quais tags de conteúdo foram aplicadas.
* Consulte [Marcação para desenvolvedores](/help/sites-developing/tags.md) para obter informações sobre a estrutura de marcação e sobre como incluir e estender tags em aplicativos personalizados.

## Dez razões para usar marcação {#ten-reasons-to-use-tagging}

1. Organização do conteúdo : a marcação facilita a vida dos autores, pois eles podem organizar rapidamente o conteúdo com pouco esforço.
1. Organização de Tags : enquanto tags organizam conteúdo, taxonomias/espaços de nome hierárquicos organizam tags.
1. Tags profundamente organizadas : com a capacidade de criar tags e subtags, é possível expressar sistemas taxonômicos inteiros, abrangendo termos, subtermos e seus relacionamentos. É possível criar uma segunda (ou terceira) hierarquia de conteúdo em paralelo à oficial.
1. Marcação Controlada : a marcação pode ser controlada com a aplicação de permissões a tags e/ou espaços de nome para controlar a criação e a aplicação de tags.
1. Marcação flexível : tags têm muitos nomes e faces: tags, termos de taxonomia, categorias, rótulos e muito mais. Elas são flexíveis em seu modelo de conteúdo e na maneira como podem ser usadas. Por exemplo, ao estruturar dados demográficos de direcionamento, categorizar e classificar conteúdo ou criar uma hierarquia de conteúdo secundário.
1. Pesquisa aprimorada : o componente de pesquisa padrão no AEM inclui amplamente tags criadas e tags aplicadas, às quais é possível aplicar filtros para restringir os resultados apenas àqueles que são relevantes.
1. Habilitação de SEO : tags aplicadas como propriedades de página aparecerão automaticamente nas metatags da página, tornando-a visível para os mecanismos de pesquisa.
1. Sofisticação simples : tags podem ser criadas simplesmente a partir de uma palavra e com o toque de um botão. Posteriormente, um título, uma descrição e um número ilimitado de etiquetas podem ser adicionadas para fornecer mais semântica à tag.
1. Consistência básica : o sistema de marcação é um componente central do AEM e é usado por todos os recursos do AEM para categorizar o conteúdo. Além disso, a API de marcação está disponível para os desenvolvedores criarem aplicativos ativados para marcação com acesso às mesmas taxonomias.
1. Combina estrutura e flexibilidade : o AEM é ideal para trabalhar com informações estruturadas, devido ao aninhamento de páginas e caminhos. Ela é igualmente eficiente ao trabalhar com informações não estruturadas, devido à pesquisa integrada de texto completo. A marcação combina os pontos fortes da estrutura e da flexibilidade.

Ao projetar a estrutura de conteúdo para um site e o esquema de metadados para ativos, considere a abordagem mais leve e acessível oferecida pela marcação.

## Aplicação de tags   {#applying-tags}

No ambiente de criação, os autores podem aplicar tags acessando as propriedades da página e digitando uma ou mais tags no campo **Tags/Palavras-chave**.

Para aplicar [marcas predefinidas](/help/sites-administering/tags.md), na janela **Propriedades da Página** use o menu suspenso do campo `Tags/Keywords` para selecionar na lista de marcas permitidas para a página. A guia **Tags Padrão** é o namespace padrão, o que significa que não há `namespace-string:` prefixado à taxonomia.

![chlimage_1-2](assets/chlimage_1-2a.png)

### Publicação de tags {#publishing-tags}

Assim como com as páginas, você pode executar o seguinte em tags e namespaces:

**Ativar**

* Ativar tags individuais.

  Assim como com as páginas, tags recém-criadas devem ser ativadas antes de serem disponibilizadas no ambiente de publicação.

>[!NOTE]
>
>Quando você ativa uma página, uma caixa de diálogo é aberta automaticamente e permite ativar tags não ativadas pertencentes a essa página.

**Desativar**

* Desativar as tags selecionadas.

## Nuvens de tags {#tag-clouds}

Nuvens de tags mostram uma nuvem de tags, para a página atual, para o site inteiro ou para aqueles mais acessados. Nuvens de tags são um meio de destacar as questões que são (foram) de interesse para o usuário. O tamanho do texto usado para exibir a tag varia em relação ao seu uso.

O componente [Nuvem de Marcas](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md#tag-cloud) (grupo de componentes Geral) é usado para adicionar uma nuvem de marcas a uma página.

## Pesquisar em tags {#searching-on-tags}

Você pode pesquisar tags nos ambientes do autor e de publicação.

### Utilização do componente de Pesquisa {#using-search-component}

Adicionar um [componente de Pesquisa](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md#search) a uma página fornece um recurso de pesquisa que inclui marcas e pode ser usado nos ambientes do autor e de publicação.

![chlimage_1-3](assets/chlimage_1-3a.png)
