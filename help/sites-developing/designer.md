---
title: Designs e o Designer
description: Saiba como criar um design para seu site e no AEM usando o Designer.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: e12f12862c31cef81b2808897fab5cf8e19dfa86
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Designs e o Designer{#designs-and-the-designer}

>[!CAUTION]
>
>Este artigo descreve como criar um site com base na interface clássica. A Adobe recomenda usar as tecnologias AEM mais recentes para seus sites, conforme descrito detalhadamente no artigo [Introdução ao desenvolvimento do AEM Sites](/help/sites-developing/getting-started.md).

O Designer é usado para criar um design para o seu site usando a [Interface clássica](/help/sites-classic-ui-authoring/classicui.md) no AEM.

>[!NOTE]
>
>Para obter mais informações sobre acessibilidade da Web, consulte [AEM e as Diretrizes de Acessibilidade da Web](/help/managing/web-accessibility.md).

## Uso do Designer {#using-the-designer}

Seu design pode ser definido na seção **designs** da guia **Ferramentas**:

![screen_shot_2012-02-01at30237pm](assets/screen_shot_2012-02-01at30237pm.png)

Aqui você pode criar a estrutura necessária para armazenar o design e, em seguida, fazer upload das folhas de estilos em cascata e imagens necessárias.

Os designs são armazenados em `/apps/<your-project>`. O caminho para o design a ser usado para um site é especificado usando a propriedade `cq:designPath` do nó `jcr:content`.

![chlimage_1-74](assets/chlimage_1-74a.png)

>[!NOTE]
>
>Todas as alterações feitas em uma página no modo de design são persistentes abaixo do nó de design do site e são aplicadas automaticamente a todas as páginas que têm o mesmo design.

## Do que você precisará {#what-you-will-need}

Para realizar seu design, você precisará:

**CSS** - As Folhas de Estilo em Cascata definem os formatos de áreas específicas nas suas páginas.
**Imagens** - Qualquer imagem que você use para recursos como planos de fundo, botões.

### Considerações Ao Projetar O Site {#considerations-when-designing-your-website}

Ao desenvolver um site, é altamente recomendável armazenar imagens e arquivos CSS em `/apps/<your-project>` para que você possa fazer referência aos seus recursos com base no design atual, conforme descrito pelo seguinte trecho.

```xml
<%= currentDesign.getPath() + "/static/img/icon.gif %>
```

O exemplo anterior oferece vários benefícios:

* Os componentes podem ter uma aparência diferente com base em cada site usando um caminho de design diferente.
* A recriação do site pode ser feita simplesmente apontando o caminho de design para um nó diferente na raiz do site de `design/v1` para `design/v2.`

* `/etc/designs` e `/content` são os únicos URLs externos que o navegador vê protegendo você de um usuário externo ficar curioso sobre o que está sob a árvore `/apps`. Os benefícios do URL acima também ajudam o administrador do sistema a configurar uma segurança melhor, pois você está limitando a exposição dos ativos a alguns locais distintos.
