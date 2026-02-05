---
title: Habilitação de exportação em JSON para um componente
description: Os componentes podem ser adaptados para gerar a exportação JSON de seu conteúdo com base em uma estrutura de modelador.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: aeb8e954-dd6c-4e18-bb78-6eaac86fa4b9
source-git-commit: cc96a14ebaf9f895a798b5f4904f5b4769b990bb
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 4%

---

# Ativar exportação em JSON para um componente{#enabling-json-export-for-a-component}

Os componentes podem ser adaptados para gerar a exportação JSON de seu conteúdo com base em uma estrutura de modelador.

## Visão geral {#overview}

A exportação JSON é baseada em [Modelos Sling](https://sling.apache.org/documentation/bundles/models.html) e na estrutura [Exportador de Modelo Sling](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) (que se baseia em [Anotações Jackson](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

Essa abordagem significa que o componente deve ter um Modelo Sling se precisar exportar JSON. Portanto, siga estas duas etapas para ativar a exportação JSON em qualquer componente.

* [Definir um modelo do Sling para o componente](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Anotar a interface do Modelo do Sling](#annotate-the-sling-model-interface)

## Definir um modelo do Sling para o componente {#define-a-sling-model-for-the-component}

Primeiro, um Modelo do Sling deve ser definido para o componente.

>[!NOTE]
>
>Para obter um exemplo de uso de Modelos Sling, consulte [Desenvolvendo exportadores de modelo Sling no AEM](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter).

A classe de implementação do Modelo do Sling deve ser anotada com o seguinte:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Isso garante que seu componente possa ser exportado sozinho, usando o seletor `.model` e a extensão `.json`.

Além disso, especifica que a classe Modelo Sling pode ser adaptada à interface `ComponentExporter`.

>[!NOTE]
>
>As anotações Jackson não são especificadas no nível de classe do Modelo Sling, mas no nível da interface do Modelo. Essa abordagem é para garantir que a exportação JSON seja considerada como parte da API do componente.

>[!NOTE]
>
>As classes `ExporterConstants` e `ComponentExporter` vêm do pacote `com.adobe.cq.export.json`.

### Usar vários seletores {#multiple-selectors}

Embora não seja um caso de uso padrão, é possível configurar vários seletores além do seletor `model`.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

No entanto, nesse caso, o seletor `model` deve ser o primeiro e a extensão deve ser `.json`.

## Anotar a interface do Modelo do Sling {#annotate-the-sling-model-interface}

Para que a estrutura do Exportador JSON processe-a, a interface Modelo deve implementar a interface `ComponentExporter` (ou `ContainerExporter` para um componente de contêiner).

A interface do Modelo Sling correspondente ( `MyComponent`) seria então anotada usando [anotações Jackson](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) para definir como ela deve ser exportada (serializada).

A interface do modelo deve ser anotada corretamente para definir quais métodos são serializados. Por padrão, todos os métodos que respeitam a convenção de nomenclatura usual para getters são serializados e derivam seus nomes de propriedade JSON naturalmente dos nomes de getter. Esta abordagem pode ser impedida ou substituída usando `@JsonIgnore` ou `@JsonProperty` para renomear a propriedade JSON.

## Exemplo {#example}

Os Componentes Principais têm suporte para exportação JSON desde a versão [1.1.0 dos componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction) e podem ser usados como referência.

Para obter um exemplo, consulte a implementação do Modelo Sling do Componente principal de imagem e sua interface anotada.

CÓDIGO NO GITHUB

Você pode encontrar o código desta página no GitHub

* [Abrir o projeto aem-core-wcm-components no GitHub](https://github.com/adobe/aem-core-wcm-components)
* Baixar o projeto como [um arquivo ZIP](https://codeload.github.com/adobe/aem-core-wcm-components/zip/main)


## Documentação relacionada {#related-documentation}

* O [tópico Fragmentos de conteúdo no guia do usuário do Assets](https://experienceleague.adobe.com/en/docs/experience-manager-64/assets/home#)
* [Modelos de fragmentos de conteúdo](/help/assets/content-fragments/content-fragments-models.md)
* [Criação com fragmentos de conteúdo](/help/sites-authoring/content-fragments.md)
* [Exportador JSON para serviços de conteúdo](/help/sites-developing/json-exporter.md)
* [Componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction) e o [componente de Fragmento de Conteúdo](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/wcm-components/content-fragment-component)
