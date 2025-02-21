---
title: Adicionar fontes para renderização gráfica
description: O AEM permite gerar gráficos incorporando texto dinamicamente retirado do conteúdo
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Adicionar fontes para renderização gráfica{#adding-fonts-for-graphic-rendering}

O AEM permite gerar gráficos incorporando texto dinamicamente retirado do conteúdo.

Para fazer isso, você também pode carregar e usar suas próprias fontes.

Atualmente, todas as implementações da Plataforma Java oferecem suporte a [TrueType](https://en.wikipedia.org/wiki/Truetype) fontes.

1. Abra o CRXDE Lite e navegue até a pasta do aplicativo do projeto:

   `/apps/<your-project>/`

1. Em `/apps/<your-project>/`, crie um nó:

   * **Nome**: `fonts`
   * **Tipo**: `sling:Folder`

   Salve todas as alterações.

1. Copie os arquivos de fonte nesta pasta; por exemplo, usando WebDAV.

   >[!NOTE]
   >
   >Os arquivos de fonte no repositório devem ter o sufixo `*.ttf` ou `*.TTF`.

1. Atualize a [configuração OSGi](/help/sites-deploying/configuring-osgi.md) do [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). Adicione o caminho à pasta de fontes; ou seja, `/apps/<your-project>/fonts`.

1. Retorne ao CRXDE Lite. Agora você deve ver um nó `.fontlist` na pasta que contém o nome das fontes importadas.

   Essas fontes agora estão prontas para serem usadas na API do Java.

Para obter detalhes completos sobre como usar as fontes com a API Java, consulte a [documentação da classe Font da API Java](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
