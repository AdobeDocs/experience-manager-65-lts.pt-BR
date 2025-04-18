---
title: Modelos
description: Os modelos são usados ao criar uma página que é usada como base para a nova página.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
legacypath: /content/docs/en/aem/6-1/develop/the-basics/templates
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: a6121f570f7840c9b7a63d10c7a95cd2894fe4ec
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 0%

---

# Modelos{#templates}

Os modelos são usados em vários pontos do AEM:

* [Ao criar uma página, selecione um modelo](#templates-pages). Esse modelo é usado como base para a nova página. O modelo define a estrutura da página, qualquer conteúdo inicial e os [componentes](/help/sites-authoring/default-components.md) que podem ser usados (propriedades de design).

Os seguintes templates são abordados em detalhes:

* [Modelos de página - Editável](/help/sites-developing/page-templates-editable.md)

## Modelos - Páginas {#templates-pages}

O AEM agora oferece dois tipos básicos de modelos para criar páginas:

>[!NOTE]
>
>Ao usar um modelo para [criar uma página](/help/sites-authoring/managing-pages.md#creating-a-new-page), não há diferença visível (para o autor da página) e nenhuma indicação do tipo de modelo que está sendo usado.

### Modelos editáveis {#editable-templates}

Os modelos editáveis agora são considerados práticas recomendadas para desenvolvimento com o AEM.

As vantagens dos Modelos editáveis:

* Pode ser [criado](/help/sites-authoring/templates.md#creating-a-new-template-template-author) e [editado](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) pelos seus autores.

* Foram introduzidos para permitir que você defina o seguinte para qualquer página criada com o modelo:

   * a estrutura
   * o conteúdo inicial
   * políticas de conteúdo

* Após a criação da nova página, uma conexão dinâmica é mantida entre a página e o modelo. Essa conexão significa que as alterações na estrutura do modelo são refletidas em qualquer página criada com esse modelo; as alterações no conteúdo inicial não são refletidas.
* Usa políticas de conteúdo (editadas pelo editor de modelo) para manter as propriedades de design (não usa o modo Design no editor de páginas).
* São armazenados em `/conf`
* Consulte [Modelos editáveis](/help/sites-developing/page-templates-editable.md) para obter mais informações.

>[!NOTE]
>
>Consulte [Usar modelos de página editáveis para desenvolver um site do Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/template-editor-feature-video-use.html?lang=pt-BR).

### Modelos estáticos {#static-templates}

Modelos estáticos:

* Deve ser definido e configurado pelos desenvolvedores.
* O sistema de modelos original do AEM que está disponível para muitas versões.
* Um modelo estático é uma hierarquia de nós que tem a mesma estrutura que a página a ser criada, mas sem nenhum conteúdo real.
* São copiados para criar a página; não existe conexão dinâmica depois.
* Usa o [Modo de Design](/help/sites-authoring/default-components-designmode.md) para manter as propriedades de design.
* São armazenados em `/apps`

>[!NOTE]
>
>A partir do AEM 6.5, o uso de Modelos estáticos não é considerado uma prática recomendada. Em vez disso, use Modelos editáveis.
>
>As ferramentas de [Modernização do AEM](modernization-tools.md) podem ajudar você a migrar de modelos estáticos para editáveis.

### Disponibilidade de modelo {#template-availability}

>[!CAUTION]
>
>A AEM oferece várias propriedades para controlar os modelos permitidos em **Sites**. No entanto, combiná-los pode levar a regras complexas que são difíceis de rastrear e gerenciar.
>
>Portanto, a Adobe recomenda começar simples, definindo:
>
>* somente a propriedade `cq:allowedTemplates`
>
>* somente na raiz do site
>
>Para obter um exemplo, consulte We.Retail: `/content/we-retail/jcr:content`
>
>As propriedades `allowedPaths`, `allowedParents` e `allowedChildren` também podem ser colocadas nos modelos para definir regras mais sofisticadas. No entanto, quando possível, é *muito* mais simples definir outras propriedades `cq:allowedTemplates` em subseções do site se houver necessidade de restringir ainda mais os modelos permitidos.
>
>Uma vantagem extra é que as propriedades `cq:allowedTemplates` podem ser atualizadas por um autor na guia **Avançado** das **Propriedades da página**. As outras propriedades do template não podem ser atualizadas usando a interface do usuário (padrão), portanto, seria necessário um desenvolvedor para manter as regras e uma implantação de código para cada alteração.

Ao criar uma página na interface do administrador do site, a lista de modelos disponíveis depende do local da nova página e das restrições de posicionamento especificadas em cada modelo.

As propriedades a seguir determinam se um modelo `T` é usado para que uma nova página seja colocada como secundária da página `P`. Cada uma dessas propriedades é uma string de vários valores que contém zero ou mais expressões regulares usadas para correspondência com caminhos:

* A propriedade `cq:allowedTemplates` do subnó `jcr:content` de `P` ou um ancestral de `P`.

* A propriedade `allowedPaths` de `T`.

* A propriedade `allowedParents` de `T`.

* A propriedade `allowedChildren` do modelo de `P`.

A avaliação funciona da seguinte forma:

* A primeira propriedade `cq:allowedTemplates` não vazia encontrada ao aumentar a hierarquia de páginas que começa com `P` é comparada com o caminho de `T`. Se nenhum dos valores for correspondente, `T` será rejeitado.

* Se `T` tiver uma propriedade `allowedPaths` não vazia, mas nenhum dos valores corresponder ao caminho de `P`, `T` será rejeitado.

* Se ambas as propriedades acima estiverem vazias ou não existirem, `T` será rejeitado, a menos que pertença ao mesmo aplicativo que `P`. `T` pertence ao mesmo aplicativo que `P` se, e somente se, o nome do segundo nível do caminho de `T` é o mesmo que o nome do segundo nível do caminho de `P`. Por exemplo, o modelo `/apps/geometrixx/templates/foo` pertence ao mesmo aplicativo que a página `/content/geometrixx`.

* Se `T` tiver uma propriedade `allowedParents` não vazia, mas nenhum dos valores corresponder ao caminho de `P`, `T` será rejeitado.

* Se o modelo de `P` tiver uma propriedade `allowedChildren` não vazia, mas nenhum dos valores corresponder ao caminho de `T`, `T` será rejeitado.

* Em todos os outros casos, `T` é permitido.

O diagrama a seguir descreve o processo de avaliação do modelo:

![chlimage_1-176](assets/chlimage_1-176.png)

#### Limite de modelos usados em páginas secundárias {#limiting-templates-used-in-child-pages}

Para limitar quais modelos podem ser usados para criar páginas secundárias em uma determinada página, use a propriedade `cq:allowedTemplates` do nó `jcr:content` da página para especificar a lista de modelos a serem permitidos como páginas secundárias. Cada valor na lista deve ser um caminho absoluto para um modelo de uma página secundária permitida, por exemplo, `/apps/geometrixx/templates/contentpage`.

Você pode usar a propriedade `cq:allowedTemplates` no nó `jcr:content` do modelo para aplicar essa configuração a todas as páginas recém-criadas que usam esse modelo.

Se quiser adicionar mais restrições, por exemplo, em relação à hierarquia do modelo, você pode usar as propriedades `allowedParents/allowedChildren` no modelo. Em seguida, é possível especificar explicitamente que as páginas criadas a partir de um modelo T devem ser páginas principais/secundárias das páginas criadas a partir de um modelo T.

