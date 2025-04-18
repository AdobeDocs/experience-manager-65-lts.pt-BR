---
title: Tag de decoração
description: Quando um componente em uma página da Web é renderizado, um elemento HTML pode ser gerado, vinculando o componente renderizado dentro de si mesmo. Para desenvolvedores, o AEM oferece lógica simples e clara controlando as tags de decoração que envolvem componentes incluídos.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 7%

---

# Tag de decoração{#decoration-tag}

Quando um componente em uma página da Web é renderizado, um elemento HTML pode ser gerado, vinculando o componente renderizado dentro de si mesmo. Isso serve principalmente a dois propósitos:

* Um componente só pode ser editado quando envolvido com um elemento HTML.
* O elemento de encapsulamento é usado para aplicar classes HTML que fornecem:

   * informações de layout
   * informações de estilo

Para desenvolvedores, o AEM oferece lógica simples e clara controlando as tags de decoração que envolvem componentes incluídos. Se e como a tag de decoração é renderizada é definida pela combinação de dois fatores, nos quais essa página se aprofundará:

* O próprio componente pode configurar a tag de decoração com um conjunto de propriedades.
* Os scripts que incluem componentes (HTL, JSP, dispatcher e assim por diante) podem definir os aspectos da tag de decoração com parâmetros de inclusão.

## Recomendações {#recommendations}

Estas são algumas recomendações gerais de quando incluir o elemento invólucro que devem ajudar a evitar problemas inesperados:

* A presença do elemento wrapper não deve diferir entre WCMModes (modo de edição ou pré-visualização), instâncias (autor ou publicação) ou ambiente (preparo ou produção), para que o CSS e os JavaScripts da página funcionem de forma idêntica em todos os casos.
* O elemento wrapper deve ser adicionado a todos os componentes editáveis, para que o editor de páginas possa inicializá-los e atualizá-los corretamente.
* Para componentes não editáveis, o elemento invólucro pode ser evitado se não atender a uma função específica, de modo que a marcação resultante não fique desnecessariamente sobrecarregada.

## Controles de componente {#component-controls}

As seguintes propriedades e nós podem ser aplicados aos componentes para controlar o comportamento da tag de decoração:

* **`cq:noDecoration {boolean}`:** Essa propriedade pode ser adicionada a um componente e um valor verdadeiro força o AEM a não gerar elementos wrapper sobre o componente.

* Nó **`cq:htmlTag`:** Este nó pode ser adicionado em um componente e pode ter as seguintes propriedades:

   * **`cq:tagName {String}`:** Pode ser usado para especificar uma marca HTML personalizada para ser usada para envolver os componentes em vez do elemento DIV padrão.
   * **`class {String}`:** Pode ser usado para especificar nomes de classe css a serem adicionados ao invólucro.
   * Outros nomes de propriedades serão adicionados como atributos do HTML com o mesmo valor de string fornecido.

## Controles de script {#script-controls}

No entanto, o comportamento do invólucro é diferente dependendo se o [HTL](/help/sites-developing/decoration-tag.md#htl) ou o [JSP](/help/sites-developing/decoration-tag.md#jsp) é usado para incluir o elemento.

### HTL {#htl}

Em geral, o comportamento do invólucro no HTL pode ser resumido da seguinte maneira:

* Nenhum DIV de wrapper é renderizado por padrão (quando apenas faz `data-sly-resource="foo"`).
* Todos os modos wcm (desativado, pré-visualização, edição no autor e publicação) são renderizados de forma idêntica.

O comportamento do invólucro também pode ser totalmente controlado.

* O script HTL tem controle total sobre o comportamento resultante da tag do invólucro.
* As propriedades do componente (como `cq:noDecoration` e `cq:tagName`) também podem definir a marca wrapper.

É possível controlar totalmente o comportamento das tags do invólucro de scripts HTL e sua lógica associada.

Para obter mais informações sobre como desenvolver em HTL, consulte a [documentação HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=pt-BR).

#### Árvore de decisão {#decision-tree}

Essa árvore decisória resume a lógica que determina o comportamento das tags do invólucro.

![chlimage_1-75](assets/chlimage_1-75a.png)

#### Casos de uso {#use-cases}

Os três casos de uso a seguir fornecem exemplos de como as tags do invólucro são tratadas e também ilustram como é simples controlar o comportamento desejado das tags do invólucro.

Todos os exemplos a seguir pressupõem a seguinte estrutura de conteúdo e componentes:

```
/content/test/
  @resourceType = "test/components/one"
  child/
    @resourceType = "test/components/two"
```

```
/apps/test/components/
  one/
    one.html
  two/
    two.html
    cq:htmlTag/
      @cq:tagName = "article"
      @class = "component-two"
```

#### Caso de uso 1: Incluir um componente para reutilização de código {#use-case-include-a-component-for-code-reuse}

O caso de uso mais comum é quando um componente inclui outro componente por motivos de reutilização de código. Nesse caso, o componente incluído não é desejado para ser editável com sua própria barra de ferramentas e caixa de diálogo, portanto, nenhum invólucro é necessário, e o `cq:htmlTag` do componente será ignorado. Esse pode ser considerado o comportamento padrão.

`one.html: <sly data-sly-resource="child"></sly>`

`two.html: Hello World!`

Saída resultante em `/content/test.html`:

**`Hello World!`**

Um exemplo seria um componente que inclui um componente de imagem principal para exibir uma imagem, normalmente nesse caso usando um recurso sintético, que consiste em incluir um componente filho virtual ao passar para o recurso data-sly um objeto de Mapa que representa todas as propriedades que o componente teria.

#### Caso de uso 2: incluir um componente editável {#use-case-include-an-editable-component}

Outro caso de uso comum é quando componentes de contêiner incluem componentes filhos editáveis, como um Contêiner de layout. Nesse caso, cada filho incluído precisa imperativamente de um invólucro para que o editor funcione (a menos que explicitamente desabilitado com a propriedade `cq:noDecoration` ).

Como o componente incluído é, neste caso, um componente independente, ele precisa de um elemento wrapper para que o editor funcione e para definir seu layout e estilo a serem aplicados. Para acionar esse comportamento, há a opção `decoration=true`.

`one.html: <sly data-sly-resource="${'child' @ decoration=true}"></sly>`

`two.html: Hello World!`

Saída resultante em `/content/test.html`:

**`<article class="component-two">Hello World!</article>`**

#### Caso de uso 3: comportamento personalizado {#use-case-custom-behavior}

Pode haver qualquer número de casos complexos, que podem ser facilmente obtidos com a possibilidade de o HTL fornecer explicitamente:

* **`decorationTagName='ELEMENT_NAME'`** Para definir o nome do elemento do invólucro.
* **`cssClassName='CLASS_NAME'`** Para definir os nomes de classe CSS a serem definidos.

`one.html: <sly data-sly-resource="${'child' @ decorationTagName='aside', cssClassName='child'}"></sly>`

`two.html: Hello World!`

Saída resultante `/content/test.html`:

**`<aside class="child">Hello World!</aside>`**

## JSP {#jsp}

Ao incluir um componente usando `cq:includ`e ou `sling:include`, o comportamento padrão no AEM é usar um DIV para envolver o elemento. No entanto, essa embalagem pode ser personalizada de duas maneiras:

* Diga explicitamente ao AEM para não empacotar o componente usando `cq:noDecoration`.
* Use uma marca HTML personalizada para envolver o componente usando `cq:htmlTag`/ `cq:tagName` ou `decorationTagName`.

### Árvore de decisão {#decision-tree-1}

A árvore decisória a seguir ilustra como `cq:noDecoration`, `cq:htmlTag`, `cq:tagName` e `decorationTagName` afetam o comportamento do invólucro.

![chlimage_1-3](assets/chlimage_1-3a.jpeg)
