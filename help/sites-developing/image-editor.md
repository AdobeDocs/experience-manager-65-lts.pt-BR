---
title: Editor de imagem
description: O Editor de imagens é uma parte principal do AEM e pode ser usado por componentes para facilitar a manipulação de imagens por autores de conteúdo.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 9%

---

# Editor de imagem{#image-editor}

O Editor de imagens é uma parte principal do AEM e pode ser usado por componentes para facilitar a manipulação de imagens por autores de conteúdo.

>[!CAUTION]
>
>Para usar os recursos do Editor de Imagens descritos neste artigo, o [pacote de recursos 24267](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/cq-6.4.0-featurepack-24267) deve estar instalado.

## Unidades relativas do mapa de imagem {#relative-units-for-image-map}

O Editor de imagens mantém as áreas do mapa de imagens como unidades absolutas e relativas. As unidades relativas são úteis quando fornecidas como atributos de dados para redimensionar dinamicamente um mapa de imagem (em relação ao tamanho da imagem) no lado do cliente em um componente de imagem responsivo.

### Propriedade imageMap {#imagemap-property}

As coordenadas do mapa de imagem são mantidas para o JCR como uma propriedade `imageMap` pelo Editor de imagens. Ela tem o formato a seguir.

A propriedade armazena áreas de mapa da seguinte maneira:

`[area1][area2][...]`

Formato da área:

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Exemplo:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Suporte para imagens do SVG {#support-for-svg-images}

Scalable Vetor Graphics (SVG) são compatíveis com o Editor de imagens.

* Tanto o processo de arrastar e soltar um ativo SVG do DAM quanto o de fazer upload de um arquivo SVG de um sistema de arquivos local são compatíveis.

## Habilitando plug-ins por tipo de MIME {#enabling-plugins-by-mime-type}

Em determinadas situações, as ações de criação devem ser restritas para determinados tipos MIME, devido à falta de suporte no processamento do lado do servidor. Por exemplo, editar imagens SVG pode não ser permitido.

Os plug-ins no Editor de imagens podem ser ativados seletivamente pelo tipo MIME ao configurar uma propriedade `supportedMimeTypes` no nó de configuração do plug-in individual.

### Exemplo {#example}

Como exemplo, digamos que a capacidade de recorte só seja permitida para imagens do GIF, JPEG, PNG, WEBP e TIFF.

A propriedade `supportedMimeTypes` deve ser definida como uma cadeia de caracteres dos tipos MIME permitidos no nó de configuração do plug-in no nó `cq:editConfig` do componente de imagem.

`/apps/core/wcm/components/image/v2/image/cq:editConfig`

```xml
 jcr:primaryType="cq:EditConfig">
     <cq:dropTargets jcr:primaryType="nt:unstructured">
         <image ...>
            ...
         </image>
     </cq:dropTargets>
     <cq:inplaceEditing
         jcr:primaryType="cq:InplaceEditingConfig"
         active="{Boolean}true"
         editorType="image">
         <config jcr:primaryType="nt:unstructured">
             <plugins jcr:primaryType="nt:unstructured">
                 <crop
                     jcr:primaryType="nt:unstructured"
                     supportedMimeTypes="[image/gif,image/jpeg,image/png,image/webp,image/tiff]"
                     features="*">
                     <aspectRatios jcr:primaryType="nt:unstructured">
                        ...
                     </aspectRatios>
                 </crop>
                 ...
             </plugins>
             <ui jcr:primaryType="nt:unstructured">
                 ...
             </ui>
         </config>
     </cq:inplaceEditing>
 </jcr:root>
```
