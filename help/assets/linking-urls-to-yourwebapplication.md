---
title: Vincular URLs ao seu aplicativo web
description: Como vincular URLs ao aplicativo da Web no Dynamic Media
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
feature: Configuration
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 4%

---

# Vincular URLs ao seu aplicativo web {#linking-urls-to-your-web-application}

Seus sites e aplicativos acessam os serviços do Dynamic Media por meio de chamadas de URL. Depois de publicar um ativo, o Dynamic Media ativa uma cadeia de caracteres de URL que faz referência ao ativo. Você pode colar esses URLs em um navegador da Web para testes.

Você vincula a URLs somente se estiver *não* usando o Experience Manager como o WCM. A vinculação, em vez da incorporação, é usada quando você deseja disponibilizar um player de vídeo como uma janela pop-up ou modal. Se você estiver usando o Experience Manager como o WCM, [adicione os ativos diretamente na sua página](adding-dynamic-media-assets-to-pages.md).

Para colocar essas cadeias de caracteres de URL em suas páginas da Web e aplicativos, copie-as do Dynamic Media.

>[!NOTE]
>
>As cadeias de caracteres de URL só estão disponíveis para representações dinâmicas de ativos. No momento, eles não estão disponíveis para ativos estáticos que residem no DAM e não no servidor do Dynamic Media. O botão URL não é exibido para representações estáticas.

Consulte também [Incorporar o Visualizador de Vídeo ou Imagem em uma página da Web](embed-code.md).

Consulte também [Vincular URLs do YouTube ao Aplicativo Web](video.md).

Consulte também [Fornecer imagens otimizadas para um site responsivo](responsive-site.md).

Consulte também [Carregar ativos](manage-assets.md#uploading-assets).

## Obter um URL para um ativo {#obtaining-a-url-for-an-asset}

É possível obter uma string de URL gerada por uma Predefinição de imagem ou uma Predefinição do visualizador. Depois de copiar o URL, ele é colocado na Área de transferência para que você possa colá-lo conforme necessário nas páginas do site ou aplicativo.

>[!NOTE]
>
>O URL não está disponível para cópia até que você tenha publicado o ativo selecionado. Além disso, você também deve publicar a predefinição do visualizador ou a predefinição da imagem.
>
>Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).
>
>Consulte [Publicar Predefinições Do Visualizador](managing-viewer-presets.md#publishing-viewer-presets).
>
>Consulte [Publicar Predefinições De Imagem](managing-image-presets.md#publishing-image-presets).

Há várias maneiras diferentes de obter uma string de URL. No entanto, as etapas abaixo mostram apenas um método que você pode usar.

**Para obter uma URL para um ativo:**

1. Navegue até o ativo *publicado* cujo URL da predefinição de imagem ou URL da predefinição do visualizador você deseja copiar e selecione o ativo para abri-lo.

   Lembre-se de que os URLs só estão disponíveis para cópia *depois* que você *publicou* os ativos pela primeira vez. Além disso, a predefinição do visualizador ou da imagem também deve ser publicada.

   Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).

   Consulte [Publicar Predefinições Do Visualizador](managing-viewer-presets.md#publishing-viewer-presets).

   Consulte [Publicar Predefinições De Imagem](managing-image-presets.md#publishing-image-presets).

1. Com base no ativo selecionado, siga um destes procedimentos:

   * Se você selecionou uma imagem, no menu suspenso, selecione **[!UICONTROL Representações]**.

     No cabeçalho **[!UICONTROL Dinâmico]**, selecione um nome predefinido para exibir sua representação no quadro direito. Se necessário, role a lista Representações para ver o cabeçalho Dinâmico.

     Na parte inferior do painel esquerdo, selecione **[!UICONTROL URL]**.

     ![chlimage_1-270](assets/chlimage_1-270.png)

   * Se você selecionou um conjunto de rotação, um conjunto de imagem, um conjunto de carrossel ou um vídeo, no menu suspenso, selecione **[!UICONTROL Visualizadores]**.

     No painel à esquerda, selecione um nome de predefinição do visualizador. Uma visualização do conjunto ou vídeo é aberta em uma página separada.

     No painel esquerdo, na parte inferior, selecione **[!UICONTROL URL]**.

     ![chlimage_1-271](assets/chlimage_1-271.png)

1. Selecione e copie o texto no navegador da Web para que você possa visualizar o ativo ou adicioná-lo à página de conteúdo da Web.

   Para sair da janela da URL, selecione o **[!UICONTROL X]** ou selecione **[!UICONTROL Fechar]**.

## Obtenção de um URL para um ativo estático {#obtaining-a-url-for-a-static-asset}

O Dynamic Media é compatível com a entrega de ativos estáticos, que são ativos adicionais, além de apenas imagens e vídeos. Os formatos de ativos estáticos compatíveis para entrega incluem o seguinte:

* arquivos 3D
* GIF animado
* Arquivos de áudio
* CSS
* JavaScript (quando sua empresa está configurada com seu próprio domínio)
* PDF
* SVG
* XML
* ZIP

**Para obter uma URL para um ativo estático:**

1. Navegue até o ativo estático *publicado* cuja URL você deseja copiar e selecione o ativo para abri-lo.

   Lembre-se de que as URLs só estão disponíveis para copiar *após* você publicou *primeiro* o ativo estático.

   Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).

1. Use qualquer um dos métodos a seguir para obter o URL do ativo estático publicado:

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

        Por exemplo, `https://aem.com/is/content/adobe/image.gif`.

   * Selecione **[!UICONTROL Ativo]** > **[!UICONTROL Representações dinâmicas]**, selecione uma representação dinâmica do ativo estático e copie a URL.

     Altere a URL copiada para usar `is/content` no caminho em vez de `is/image/`.

## Obter um URL de vídeo para uma representação de vídeo publicada {#obtaining-a-video-url-for-a-published-video-rendition}

1. No Experience Manager, navegue até **[!UICONTROL Ferramentas]** > **[!UICONTROL Implantação]** > **[!UICONTROL Nuvem]** > **[!UICONTROL Serviços em Nuvem]**.
1. Na página **[!UICONTROL Cloud Services]**, role para baixo até o cabeçalho **[!UICONTROL Dynamic Media Cloud Services]** e selecione **[!UICONTROL Mostrar configurações]**.
1. Em **[!UICONTROL Configurações disponíveis]**, selecione o nome da configuração desejada.

1. Na página **[!UICONTROL Configurações da Dynamic Media Cloud]**, em **[!UICONTROL URL do Serviço de Vídeo]**, copie todo o caminho da URL. É necessário inserir o caminho do URL copiado posteriormente nas etapas.

   Por exemplo, o caminho do URL pode parecer semelhante ao seguinte:

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (O caminho acima é apenas um exemplo; não é o caminho real que você copia.)

1. Em **[!UICONTROL ID de registro]**, copie o nome do cliente encontrado na última parte da ID.

   Por exemplo, se a ID de registro fosse `87654321|MyCompany`, o nome do cliente seria `MyCompany`.

1. Próximo ao canto superior esquerdo da página, selecione **[!UICONTROL Cloud Services]**, selecione o logotipo do Experience Manager e navegue até **[!UICONTROL Geral]** > **[!UICONTROL CRXDE Lite]**.
1. Copie o caminho de representação de vídeo inteiro do JCR (Java™ Content Repository).

   Por exemplo, o caminho de representação do vídeo pode ser semelhante ao seguinte:

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (O caminho acima é apenas um exemplo; não é o caminho real que você copia.)

1. Organize as informações copiadas na seguinte ordem para que formem um caminho de URL completo:

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   Por exemplo, usando os caminhos de exemplo e o nome de cliente de exemplo das etapas acima, o caminho completo é exibido da seguinte maneira:

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   Este exemplo é o URL completo do vídeo para uma representação de vídeo publicada.

## Obter um URL de vídeo para transmissão adaptável da taxa de bits (DASH ou HLS) {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. No Experience Manager, navegue até **[!UICONTROL Ferramentas]** > **[!UICONTROL Implantação]** > **[!UICONTROL Nuvem]** > **[!UICONTROL Serviços em Nuvem]**.
1. Na página **[!UICONTROL Cloud Services]**, role para baixo até o cabeçalho **[!UICONTROL Dynamic Media Cloud Services]** e selecione **[!UICONTROL Mostrar configurações]**.
1. Em **[!UICONTROL Configurações disponíveis]**, selecione o nome da configuração desejada.
1. Na página **[!UICONTROL Configurações do Dynamic Media Cloud Services]**, faça o seguinte:

   * Em **[!UICONTROL URL do Serviço de Vídeo]**, copie todo o caminho da URL. Posteriormente, você precisará do caminho do URL copiado nessas etapas. Por exemplo, o caminho do URL pode parecer semelhante ao seguinte:

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (O caminho acima é apenas um exemplo; não é o caminho real que você copia.)

   * Em **[!UICONTROL ID de Registro]**, copie o nome do cliente encontrado na última parte da ID. Posteriormente, você precisará do nome do cliente copiado nessas etapas.

     Por exemplo, se a ID de registro fosse `87654321|demoCo`, o nome do cliente copiado seria `demoCo`.

1. Com base no protocolo de entrega de vídeo que você está usando, copie o respectivo seletor de protocolo. Posteriormente, você precisará do seletor de protocolo copiado nessas etapas.

   | Protocolo de entrega de vídeo que você está usando | Seletor de protocolo a ser usado |
   |---|---|
   | HTTP <br> Se estiver usando HTTP (entrega de vídeo não segura), altere https para http no valor da URL do Serviço de Vídeo copiada anteriormente. | `public/` |
   | HTTPS | `public-ssl/` |

1. Copie o caminho completo do ativo de vídeo no Experience Manager, conforme processado pelo Dynamic Media. Posteriormente, você precisará desse caminho do ativo de vídeo copiado nessas etapas.

   Por exemplo:

   `/content/dam/marketing/MyVideo.mp4`

1. Combine todas as partes copiadas anteriormente para criar uma cadeia de caracteres na seguinte ordem:

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   Por exemplo, usando as informações copiadas dos exemplos dessas etapas, a cadeia de caracteres seria exibida da seguinte maneira:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. Conclua a URL anexando `.m3u8` ao final da cadeia de caracteres. Por exemplo, ao anexar `.m3u8` à cadeia de caracteres da etapa anterior, o caminho completo da URL seria mostrado da seguinte maneira:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## Usar HTTP/2 para entregar seus ativos do Dynamic Media {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 é o novo protocolo da Web atualizado que melhora a maneira como navegadores e servidores se comunicam. Ele possibilita a transferência mais rápida de informações e reduz a quantidade necessária de poder de processamento. A entrega de ativos do Dynamic Media agora pode ser por HTTP/2, o que fornece melhores tempos de resposta e carregamento.

Consulte [Entrega de conteúdo HTTP2](http2.md) para obter detalhes completos sobre a introdução ao uso de HTTP/2 com sua conta do Dynamic Media.
