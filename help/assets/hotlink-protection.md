---
title: Ativação da proteção de hot link no Dynamic Media
description: Informações sobre como ativar a proteção de hot link no Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
role: User, Admin
feature: Configuration
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Ativar a proteção de hot link no Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

Hot linking é quando um site de terceiros usa o código HTML para exibir uma imagem do seu site. Eles usam a largura de banda sempre que a foto é solicitada porque o navegador do visitante está acessando-a diretamente do seu servidor. A *proteção* do Hotlink é um método para impedir que outros sites vinculem diretamente a imagens, CSS ou JavaScript em suas páginas da Web. Esse tipo de blindagem ajuda a reduzir o uso desnecessário da largura de banda na conta do Dynamic Media.

O [Suporte ao Cliente do Experience Manager](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=pt-BR#support) pode configurar um filtro de referenciador no nível da CDN (Content Delivery Network) para que o conteúdo do Dynamic Media seja enviado somente aos sites da sua lista de sites permitidos para o domínio.

>[!NOTE]
>
>Esse recurso exige o uso da CDN pronta para uso que é fornecida com o Adobe Experience Manager Dynamic Media. Qualquer outra CDN personalizada não é compatível com esse recurso. Para ativar a proteção de hot link, um administrador precisa criar um tíquete de suporte ao cliente da Adobe para solicitar a alteração de configuração em sua conta do Dynamic Media. Não há custo adicional para ativar a proteção de hot link.
