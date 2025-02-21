---
title: Práticas recomendadas para processar os formatos de arquivo compatíveis
description: Práticas recomendadas para processar os vários tipos de arquivos com suporte usando o  [!DNL Experience Manager Assets].
contentOwner: AG
role: Admin
feature: Asset Management,Developer Tools
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Práticas recomendadas para o formato de arquivo Assets {#assets-file-format-best-practices}

O [!DNL Adobe Experience Manager Assets] oferece suporte a muitas bibliotecas de formatos de arquivo proprietárias e de terceiros para atender a diversos requisitos de suporte de arquivos dos usuários. As bibliotecas Adobe compatíveis incluem, [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer e [!DNL Adobe InDesign Server]. Além disso, o [!DNL Experience Manager Assets] oferece suporte a bibliotecas de terceiros, incluindo [!DNL ImageMagick], [!DNL TwelveMonkeys] e assim por diante.

Para obter os formatos de arquivo compatíveis, consulte [formatos compatíveis com o Assets](/help/assets/assets-formats.md).

>[!TIP]
>
>Se você estiver usando o [!DNL Experience Manager] no Adobe Managed Services (AMS), entre em contato com o Suporte ao Cliente da Adobe se planejar processar muitos arquivos PSD ou PSB grandes. Trabalhe com o representante do Suporte ao cliente da Adobe para implementar essas práticas recomendadas para a implantação do AMS e escolher as melhores ferramentas e modelos possíveis para os formatos proprietários da Adobe. O [!DNL Experience Manager] pode não processar arquivos PSB de resolução muito alta com mais de 30.000 x 23.000 pixels.

## Biblioteca [!DNL Adobe Camera Raw] {#adobe-camera-raw-library}

Para um desempenho ideal, a Adobe recomenda usar a biblioteca [!DNL Adobe Camera Raw] para arquivos RAW e DNG.

A biblioteca [!DNL Adobe Camera Raw] oferece suporte ao perfil de cores CMYK como entrada. No entanto, gera a saída no espaço de cores do RGB e oferece suporte à saída somente no formato JPEG. Ele não retém o espaço de cores do arquivo de origem (por exemplo, CMYK) nas miniaturas.

Para obter mais informações, consulte [Suporte do Camera Raw](/help/assets/camera-raw.md).

## Biblioteca do Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Para obter melhores resultados, a Adobe recomenda o uso da biblioteca Adobe PDF Rasterizer para os seguintes arquivos:

* Arquivos PDF pesados e com grande volume de conteúdo
* Arquivos de IA com miniaturas não gerados imediatamente
* Para arquivos AI com cores SPOT (PMS)

Miniaturas e visualizações geradas usando o PDF Rasterizer têm melhor qualidade em comparação à saída de rasterização pronta para uso. A biblioteca do Adobe PDF Rasterizer não suporta nenhuma conversão de espaço de cores. Independentemente do espaço de cores do arquivo de origem do PDF, o Adobe PDF Rasterizer gera somente a saída do RGB.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

A Adobe recomenda usar [!DNL Adobe InDesign Server] para extrair representações específicas de [!DNL Adobe InDesign], como IDML e HTML. Para obter mais informações, consulte [Adicionando ativos do Experience Manager como referências no Adobe InDesign](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

O [!DNL Dynamic Media] gera e fornece várias variações de conteúdo avançado em tempo real por meio de sua rede global, escalável e otimizada para desempenho. Ele fornece experiências de visualização interativa e simplifica o processo de gerenciamento de campanhas digitais. Para obter detalhes sobre como habilitar [!DNL Dynamic Media], consulte [Configuração do Dynamic Media](/help/assets/config-dynamic.md).

Atualmente, o [!DNL Dynamic Media] pode oferecer suporte a vídeos de até 15 GB de conteúdo por arquivo.

## Biblioteca ImageMagick {#imagemagick-library}

A Adobe recomenda usar a biblioteca ImageMagick nos seguintes cenários:

* Para gerar representações em miniatura de arquivos do EPS.
* Para preservar as informações do perfil de imagem.
* Para preservar a transparência.
* Para processar arquivos PSD e PSB.

Para saber como configurar a biblioteca [!DNL ImageMagick] no [!DNL Experience Manager], consulte [Usando o ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Para obter o uso ideal, consulte [Práticas recomendadas para configurar o ImageMagick](/help/assets/best-practices-for-imagemagick.md).

## Biblioteca de transcodificação de imagens {#image-transcoding-library}

A Biblioteca de transcodificação de imagens do Adobe é uma solução de processamento de imagens que executa as funções principais de tratamento de imagens, incluindo codificação de imagens, transcodificação, reamostragem, redimensionamento e assim por diante.

A Biblioteca de Transcodificação de Imagens é compatível com os seguintes tipos MIME:

* JPG/JPEG
* PNG (8 e 16 bits)
* GIF
* BMP
* TIFF/Compressed TIFF (exceto Tiffs de 32 bits e PTiffs).
* ICO
* ICN

Para obter detalhes, consulte [Biblioteca de Transcodificação de Imagens](/help/assets/imaging-transcoding-library.md).
