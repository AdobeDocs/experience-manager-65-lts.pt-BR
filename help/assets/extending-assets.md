---
title: Personalizar e estender [!DNL Assets]
description: Saiba mais sobre como personalizar e estender o Compartilhamento de ativos e o Editor de ativos, que apresentam aos usuários uma interface e um conjunto de funcionalidades especificamente adaptados.
contentOwner: AG
role: Developer
feature: Developer Tools
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Personalizar e estender [!DNL Assets] {#customizing-and-extending-assets}

O Editor de Ativos é o principal ponto de acesso que os usuários de um site do Adobe Enterprise Manager usam para localizar, exibir e manipular os ativos digitais no seu repositório.

Como desenvolvedor do [!DNL Experience Manager], você pode personalizar e estender o Editor de ativos de várias maneiras, apresentando aos usuários uma interface e um conjunto de funcionalidades especificamente adaptados.

Os seguintes aspectos da funcionalidade podem ser personalizados ou aprimorados:

* [Estender editor de ativos](asseteditorx.md)
* [Estender a pesquisa do Assets](searchx.md)
* [Processar o Assets usando manipuladores de mídia e fluxos de trabalho](media-handlers.md)
* [Integrar o Assets ao fluxo de atividade](extending-activity-stream.md)
* [Desenvolvimento de proxy do Assets](proxy.md)
* [Práticas recomendadas para configurar o ImageMagick](best-practices-for-imagemagick.md)

## Personalizar a aparência {#customizing-the-look-and-feel}

Os seguintes aspectos da aparência do Editor de ativos são personalizáveis:

* Logotipo: você pode adicionar o logotipo de sua própria organização à interface do.
* Cores e fontes: é possível alterar as cores e as fontes usadas na interface.
* Código HTML: para uma personalização mais completa, é possível alterar o código HTML subjacente que define as interfaces.

## Personalizar representações {#customizing-renditions}

Na terminologia do [!DNL Experience Manager Assets], uma representação é a forma na qual um ativo é apresentado. Em geral, um ativo específico pode ter várias representações. Por exemplo, uma imagem colorida pode ter uma representação em seu tamanho original, outra em um tamanho reduzido e outra que é dimensionada e convertida em tons de cinza.

As representações em que um ativo específico está disponível podem ser personalizadas e novas representações podem ser criadas.
