---
title: Entregar ativos do Dynamic Media
description: Saiba como fornecer ativos do Dynamic Media, como vídeo e imagens, às suas páginas da Web.
role: User, Admin
feature: Asset Management,Renditions
solution: Experience Manager, Experience Manager Assets
exl-id: b91173b4-f1d1-4aad-97d2-782bc8aeaeab
source-git-commit: 47b82956b41c3f78bed5ae220c7e993ce29e0385
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 10%

---

# Entregar ativos do Dynamic Media{#delivering-dynamic-media-assets}

A maneira de fornecer os ativos do Dynamic Media, como vídeo e imagens, depende de como seu site é implementado.

Com o Dynamic Media, você tem várias opções:

* Se o site estiver hospedado no Adobe Experience Manager, será necessário adicionar os ativos do Dynamic Media diretamente à página.
* Se o seu site não estiver no Experience Manager, você terá a opção de:

   * Incorporar o vídeo ou a imagem no site.
   * Vincule URLs ao aplicativo da Web. Use a vinculação quando quiser fornecer um reprodutor de vídeo como uma janela pop-up ou modal.
   * Se o seu site é responsivo, você pode [fornecer imagens otimizadas](/help/assets/responsive-site.md).

>[!NOTE]
>
>A geração de imagens inteligentes funciona com suas predefinições de imagens existentes e usa inteligência nos últimos milissegundos do delivery para reduzir ainda mais o tamanho do arquivo de imagem com base na velocidade do navegador ou da conexão de rede. Consulte [Smart Imaging](/help/assets/imaging-faq.md) para obter mais informações.

Para obter mais informações, consulte os seguintes tópicos:

* [Adicionar ativos do Dynamic Media a páginas da Web](/help/assets/adding-dynamic-media-assets-to-pages.md)
* [Incorporar o visualizador de vídeo ou imagem em uma página da Web](/help/assets/embed-code.md)
* [Ativar proteção de hotlink no Dynamic Media](/help/assets/hotlink-protection.md)
* [Vincular URLs ao seu aplicativo web](/help/assets/linking-urls-to-yourwebapplication.md)
* [Entregar imagens otimizadas para um site responsivo](/help/assets/responsive-site.md)
* [Entrega de conteúdo HTTP2](/help/assets/http2.md)
* [Usar conjuntos de regras para transformar URLs](/help/assets/using-rulesets-to-transform-urls.md)

## Entrega HTTP/2 de ativos do Dynamic Media {#http-delivery-of-dynamic-media-assets}

O Experience Manager agora é compatível com a entrega de todo o conteúdo do Dynamic Media (imagens e vídeo) por HTTP/2. Ou seja, um URL publicado ou código incorporado para a imagem ou vídeo está disponível para ser integrado a qualquer aplicativo que aceite um ativo hospedado. Esse ativo publicado é entregue por meio do protocolo HTTP/2. Esse método de entrega melhora a maneira como os navegadores e servidores se comunicam, permitindo melhores tempos de resposta e carregamento de todos os ativos do Dynamic Media.

Para saber mais, consulte [Perguntas frequentes sobre entrega de conteúdo HTTP/2](/help/sites-administering/scene7-http2faq.md).
