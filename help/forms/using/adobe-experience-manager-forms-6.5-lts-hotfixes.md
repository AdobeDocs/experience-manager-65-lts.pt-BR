---
title: Hotfixes do Adobe Experience Manager Forms 6.5 LTS SP1
description: Fornece informações sobre como baixar e instalar um hotfix do AEM Forms 6.5 LTS.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: fbe90ee89a2c20496800b545ec5637e829e7c7d7
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---

# Hotfixes LTS do Adobe Experience Manager Forms 6.5{#aem-form-hotfix}

Este artigo lista as correções críticas implementadas para resolver problemas conhecidos, melhorar a estabilidade do sistema e aprimorar o desempenho geral do AEM Forms 6.5 LTS.

>[!NOTE]
>
> Os hotfixes foram projetados para serem cumulativos, abrangendo todas as correções anteriores. Ao aplicar a correção mais recente a uma versão do, ele não apenas aborda o problema mais recente, mas também incorpora todas as correções de erros e aprimoramentos anteriores.

## Hotfixes para o AEM Forms 6.5 LTS {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Data</strong></td>
    <td><strong>Link de download do Hotfix (link de Distribuição de software da AEM)</strong></td>
    <td><strong>Problemas corrigidos</strong></td>
  </tr>
  <tr>
    <td>
      <strong>9 de setembro de 2025</strong><br>
    <td>
    <ul>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-hotfix-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip">Hotfix2 para AEM Service Pack 6.5 LTS no Windows</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]hotfix-on-add-on/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip">Hotfix2 para AEM Service Pack 6.5 LTS no Linux</a></li>
     <li>MacOS- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip">Hotfix2 para AEM Service Pack 6.5 LTS no MacOS</a></li>
    <td>
    <ul>
    <li>Maior confiabilidade no envio de formulários, solucionando um problema em que os envios podem falhar quando a Validação no lado do servidor (SSV) foi ativada. Se encontrar problemas, entre em contato com o [Suporte da Adobe Experience Manager Forms](https://business.adobe.com/in/support/main.html)
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Baixe e instale um Hotfix OSGi {#download-install-hotfix}

Execute as seguintes etapas para baixar e instalar o Hotfix:

1. Baixar [Hotfix](#hotfix-for-adaptive-forms) do link de Distribuição de Software.
1. Extraia o arquivo de Hotfix para obter um pacote do Experience Manager (.zip) e arquivos de pacote (.jar).
1. Carregue e instale o pacote (.zip) por meio do [Gerenciador de Pacotes](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
1. Abra os pacotes do gerenciador de configurações `https://server:host/system/console/bundles`, carregue e instale o pacote (.jar). O hotfix do está instalado.
