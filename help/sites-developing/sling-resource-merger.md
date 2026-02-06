---
title: Usar a Fusão de recursos do Sling no AEM
description: O Sling Resource Merger fornece serviços para acessar e mesclar recursos
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6fb6e522-fb81-4ba2-90b2-aad68f8bfa9e
source-git-commit: 9bc1cad84bb14b7513ede1fff2c1a37768dac442
workflow-type: tm+mt
source-wordcount: '1238'
ht-degree: 0%

---

# Usar a Fusão de recursos do Sling no AEM{#using-the-sling-resource-merger-in-aem}

## Propósito {#purpose}

O Sling Resource Merger fornece serviços para acessar e mesclar recursos. Ela fornece mecanismos de diferenciação para:

* **[Sobreposições](/help/sites-developing/overlays.md)** de recursos usando os [caminhos de pesquisa configurados](/help/sites-developing/overlays.md#configuring-the-search-paths).

* **Substitui** das caixas de diálogo de componente para a interface habilitada para toque (`cq:dialog`), usando a hierarquia de tipo de recurso (por meio da propriedade `sling:resourceSuperType`).

O Sling Resource Merger combina recursos de sobreposição e substituição (e suas propriedades) com os recursos e as propriedades originais:

* O conteúdo da definição personalizada tem uma prioridade mais alta que a original. Ou seja, ele *sobrepõe* ou *substitui*.

* Quando necessário, as [propriedades](#properties) definidas na personalização indicam como o conteúdo mesclado do original será usado.

>[!CAUTION]
>
>O Sling Resource Merger e métodos relacionados só podem ser usados com o [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/index.html). Essa situação também significa que ela só é apropriada para a interface padrão habilitada para toque; em particular, as substituições definidas dessa maneira são aplicáveis somente para a caixa de diálogo habilitada para toque de um componente.
>
>Para sobrepor ou substituir outras áreas (incluindo outras partes de um componente habilitado para toque ou a interface clássica), copie o nó e a estrutura apropriados do original. Coloque a cópia onde você define a personalização.

### Metas para o AEM {#goals-for-aem}

As metas para usar a Fusão de recursos do Sling no AEM são:

* verifique se as alterações de personalização não foram feitas em `/libs`.
* reduza a estrutura replicada de `/libs`.

  Ao usar o Sling Resource Merger, não é recomendável copiar toda a estrutura de `/libs`. O motivo é porque isso resultaria em muitas informações mantidas na personalização (geralmente `/apps`). A duplicação desnecessária de informações aumenta a chance de problemas quando o sistema é atualizado.

>[!NOTE]
>
>As substituições não dependem dos caminhos de pesquisa. Eles usam a propriedade `sling:resourceSuperType` para fazer a conexão.
>
>No entanto, as substituições geralmente são definidas em `/apps`, como prática recomendada no AEM, definir personalizações em `/apps`. O motivo é porque você não deve alterar nada em `/libs`.

>[!CAUTION]
>
>*Não* altere nada no caminho `/libs`.
>
>O motivo é que o conteúdo de `/libs` é substituído na próxima vez que você atualizar sua instância. Além disso, ele pode ser substituído ao aplicar uma correção ou um pacote de recursos.
>
>O método recomendado para configuração e outras alterações é:
>
>1. Recriar o item necessário (isto é, como ele existe em `/libs`) em `/apps`
>
>1. Fazer alterações em `/apps`
>

### Propriedades {#properties}

A fusão de recursos oferece as seguintes propriedades:

* `sling:hideProperties` ( `String` ou `String[]`)

  Especifica a propriedade, ou lista de propriedades, a ser ocultada.

  O curinga `*` oculta tudo.

* `sling:hideResource` ( `Boolean`)

  Indica se os recursos estão completamente ocultos, incluindo seus secundários.

* `sling:hideChildren` ( `String` ou `String[]`)

  Ela contém o nó filho, ou lista de nós filhos, a ser ocultado. As propriedades do nó são mantidas.

  O curinga `*` oculta tudo.

* `sling:orderBefore` ( `String`)

  Ele contém o nome do nó irmão no qual o nó atual está posicionado.

Essas propriedades afetam como os recursos/propriedades correspondentes/originais (de `/libs`) são usados pela sobreposição/substituição (geralmente em `/apps`).

### Criar a estrutura {#creating-the-structure}

Para criar uma sobreposição ou substituição, é necessário recriar o nó original, com a estrutura equivalente, no destino (geralmente `/apps`). Por exemplo:

* Sobreposição

   * A definição da entrada de navegação do console Sites, como mostrado no painel, é definida em:

     `/libs/cq/core/content/nav/sites/jcr:title`

   * Para sobrepor, crie o seguinte nó:

     `/apps/cq/core/content/nav/sites`

     Em seguida, atualize a propriedade `jcr:title`, conforme necessário.

* Substituir

   * A definição da caixa de diálogo habilitada para toque do console de Textos é definida da seguinte maneira:

     `/libs/foundation/components/text/cq:dialog`

   * Para substituir, crie o nó a seguir. Por exemplo:

     `/apps/the-project/components/text/cq:dialog`

Para criar um dos dois, basta recriar a estrutura do esqueleto. Para simplificar a recriação da estrutura, todos os nós intermediários podem ser do tipo `nt:unstructured` (eles não precisam refletir o tipo de nó original. Por exemplo, em `/libs`.

Portanto, no exemplo de sobreposição acima, os seguintes nós são necessários:

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>Ao usar o Sling Resource Merger (ou seja, ao lidar com a interface padrão habilitada para toque), não é recomendável copiar toda a estrutura de `/libs`. O motivo é porque isso resultaria em muitas informações mantidas em `/apps`. Como resultado, pode causar problemas quando o sistema é atualizado.

### Casos de uso {#use-cases}

Com a funcionalidade padrão, esses casos de uso permitem fazer o seguinte:

* **Adicionar uma propriedade**

  A propriedade não existe na definição `/libs`, mas é necessária na sobreposição/substituição `/apps`.

   1. Criar o nó correspondente em `/apps`
   1. Criar a nova propriedade neste nó &quot;

* **Redefinir uma propriedade (não propriedades criadas automaticamente)**

  A propriedade está definida em `/libs`, mas um novo valor é necessário na sobreposição/substituição `/apps`.

   1. Criar o nó correspondente em `/apps`
   1. Criar a propriedade correspondente neste nó (em `apps`)

      * A propriedade tem uma prioridade com base na configuração do Sling Resource Resolver.
      * Não há suporte para a alteração do tipo de propriedade.

        Se você usar um tipo de propriedade diferente daquele usado em `/libs`, o tipo de propriedade definido será usado.

  >[!NOTE]
  >
  >Não há suporte para a alteração do tipo de propriedade.

* **Redefinir uma propriedade criada automaticamente**

  Por padrão, as propriedades criadas automaticamente (como `jcr:primaryType`) não estão sujeitas a uma sobreposição/substituição para garantir que o tipo de nó atualmente em `/libs` seja respeitado. Para impor uma sobreposição/substituição, é necessário recriar o nó em `/apps`, ocultar explicitamente a propriedade e redefini-la:

   1. Crie o nó correspondente em `/apps` com o `jcr:primaryType` desejado
   1. Crie a propriedade `sling:hideProperties` nesse nó, com o valor definido como aquele da propriedade criada automaticamente; por exemplo, `jcr:primaryType`

      Esta propriedade, definida em `/apps`, agora tem prioridade sobre aquela definida em `/libs`

* **Redefinir um nó e seus filhos**

  O nó e seus filhos estão definidos em `/libs`, mas uma nova configuração é necessária na sobreposição/substituição `/apps`.

   1. Combine as ações de:

      1. Ocultar filhos de um nó (mantendo as propriedades do nó)
      1. Redefinir a propriedade/as propriedades

* **Ocultar uma propriedade**

  A propriedade está definida em `/libs`, mas não é necessária na sobreposição/substituição de `/apps`.

   1. Criar o nó correspondente em `/apps`
   1. Crie uma propriedade `sling:hideProperties` do tipo `String` ou `String[]`. Use para especificar as propriedades que devem ser ocultas/ignoradas. Curingas também podem ser usados. Por exemplo:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Ocultar um nó e seus filhos**

  O nó e seus filhos estão definidos em `/libs`, mas não são necessários na sobreposição/substituição `/apps`.

   1. Criar o nó correspondente em `/apps`
   1. Criar uma propriedade `sling:hideResource`

      * tipo: `Boolean`
      * valor: `true`

* **Ocultar filhos de um nó (ao manter as propriedades do nó)**

  O nó, suas propriedades e seus filhos estão definidos em `/libs`. O nó e suas propriedades são necessários na sobreposição/substituição `/apps`, mas alguns ou todos os nós filhos não são necessários na sobreposição/substituição `/apps`.

   1. Criar o nó correspondente em `/apps`
   1. Criar a propriedade `sling:hideChildren`:

      * tipo: `String[]`
      * value: uma lista dos nós filhos (conforme definido em `/libs`) para ocultar/ignorar

      O curinga &amp;ast; pode ser usado para ocultar ou ignorar todos os nós filhos.

* **Reordenar nós**

  O nó e seus irmãos estão definidos em `/libs`. Para alterar a ordem, recrie o nó na sobreposição ou substituição `/apps`. Defina sua nova posição fazendo referência ao nó irmão apropriado em `/libs`.


   * Usar a propriedade `sling:orderBefore`:

      1. Criar o nó correspondente em `/apps`
      1. Criar a propriedade `sling:orderBefore`:

         Especifica o nó (como em `/libs`) em que o nó atual está posicionado antes:

         * tipo: `String`
         * valor: `<before-SiblingName>`

### Invoque a Fusão de recursos do Sling a partir de seu código {#invoking-the-sling-resource-merger-from-your-code}

O Sling Resource Merger inclui dois provedores de recursos personalizados, um para sobreposições e outro para substituições. Cada pode ser chamado dentro do código usando um ponto de montagem:

>[!NOTE]
>
>Ao acessar o recurso, é recomendável usar o ponto de montagem apropriado.
>
>Essa abordagem chama a Fusão de recursos do Sling e retorna o recurso totalmente mesclado. Também reduz a quantidade de estrutura que deve ser copiada de `/libs`.

* Sobreposição:

   * finalidade: mesclar recursos com base no caminho de pesquisa
   * ponto de montagem: `/mnt/overlay`
   * uso: `mount point + relative path`
   * exemplo:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Substituir:

   * finalidade: mesclar recursos com base em seu supertipo
   * ponto de montagem: `/mnt/overide`
   * uso: `mount point + absolute path`
   * exemplo:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

### Exemplo de uso {#example-of-usage}

Alguns exemplos são abordados:

* Sobreposição:

   * [Personalização dos Consoles](/help/sites-developing/customizing-consoles-touch.md)
   * [Personalização da criação de página](/help/sites-developing/customizing-page-authoring-touch.md)

* Substituir:

   * [Configuração das propriedades da página](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)
