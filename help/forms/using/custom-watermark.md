---
title: Marca d'água personalizada na visualização de carta do PDF
description: Saiba como criar uma marca d'água personalizada na visualização de carta do PDF.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Marca d&#39;água personalizada na visualização de carta do PDF{#custom-watermark-in-letter-pdf-preview}

## Visão geral {#overview}

Na interface Criar correspondência, os usuários do agente visualizam a correspondência na forma final na qual é enviada para pós-processamento, como para email ou impressão.

Para evitar o uso não autorizado desses dados, as organizações podem impor uma marca d&#39;água na pré-visualização do PDF. A marca d&#39;água padrão é &quot;PRÉ-VISUALIZAÇÃO&quot;, que aparece na PDF.

Para habilitar a marca d&#39;água na visualização do PDF, selecione a opção **[!UICONTROL Aplicar Marca D&#39;Água]** Durante Visualização em **[!UICONTROL Configurações de Gerenciamento de Correspondências]** em https://&#39;[server]:[port]&#39;/system/console/configMgr.

![marca-d&#39;água padrão](assets/default-watermark.png)

Você pode usar as seguintes etapas para personalizar o texto e a aparência da marca d&#39;água:

## Personalizar a marca d&#39;água na visualização do PDF na interface de Criar correspondência {#customizewatermark-}

1. Vá para `https://'[server]:[port]'/[ContextPath]/crx/de` e faça logon como Administrador.
1. Na pasta de aplicativos, crie uma pasta chamada **[!UICONTROL previewwatermark]** com caminho/estrutura semelhante à pasta previewwatermark na pasta libs:

   1. Clique com o botão direito do mouse na pasta **previewwatermark** no seguinte caminho e selecione **Sobrepor Nó**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **Caminho:** /libs/fd/cm/configFiles/previewwatermark

      **Local de Sobreposição:** /apps/

      **Corresponder Tipos De Nó:** Marcado

      >[!NOTE]
      >
      >Não faça alterações na ramificação /libs. As alterações feitas podem ser perdidas, pois essa ramificação pode sofrer alterações sempre que você:
      >
      >    
      >    
      >    * Atualizar na sua instância
      >    * Aplicar um hot fix
      >    * Instalar um pacote de recursos
      >    
      >

   1. Clique em **OK** e em **Salvar tudo**. A pasta **[!UICONTROL previewwatermark]** é criada no caminho especificado.

1. Copie e cole o arquivo ddx da pasta &quot;/libs/fd/cm/configFiles/previewwatermark&quot; para a pasta &quot;/apps/fd/cm/configFiles/previewwatermark&quot; e clique em **[!UICONTROL Salvar tudo]**.
1. Faça as alterações desejadas no arquivo ddx em /apps/fd/cm/configFiles/previewwatermark/.

   ```xml
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   Para obter informações sobre como personalizar a aparência, o texto e o alinhamento da marca d&#39;água, consulte Adição e remoção de marcas d&#39;água e planos de fundo no documento [Serviço de Assembler e Referência DDX](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf).

   >[!NOTE]
   >
   >No arquivo ddx, as referências ao resultado e à fonte devem permanecer inalteradas para output.pdf e input.pdf. O nome do arquivo ddx também não deve ser alterado.

1. Clique em **Salvar tudo**.
