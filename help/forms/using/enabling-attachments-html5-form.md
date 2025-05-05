---
title: Ativação de anexos para um formulário HTML5
description: Por padrão, o suporte a anexos para formulários HTML5 está desativado.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: HTML5 Forms,Mobile Forms
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---

# Ativação de anexos para um formulário HTML5 {#enabling-attachments-for-an-html-form}

Você pode fazer upload, pré-visualizar e enviar anexos com formulários HTML5. Por padrão, o suporte para anexos está desativado. Para ativar o suporte a anexos:

1. Crie um [perfil personalizado](/help/forms/using/custom-profile.md) com uma propriedade de cadeia de caracteres de multisseleção `mfAttachmentOptions`. Cada cadeia de caracteres na propriedade `mfAttachmentOptions` deve ter um formato `property=value` para configurar opções do dispositivo de anexo de arquivo. `property` e `value` podem ter qualquer um dos seguintes valores:

   | Propriedade | Valor |
   |--- |---|
   | multiSelect | verdadeiro ou falso (verdadeiro por padrão) |
   | fileSizeLimit | Número em MBs (2 MB por padrão). Por exemplo, 5. |
   | buttonText | Texto do botão para a janela pop-up (&quot;Anexar&quot; por padrão) |
   | Aceitar | lista separada por vírgulas de tipos de arquivos a serem aceitos (&quot;audio/&ast;, video/&ast;, image/&ast;, text/&ast;, .pdf&quot; por padrão) |

   Por exemplo:

   ![configurar opções](assets/mfAttachmentOptions.png)

   Conforme necessário, você também pode especificar mais opções personalizadas para a propriedade `mfAttachmentOptions`.

   >[!NOTE]
   >
   >No Microsoft Internet Explorer 9, os usuários podem anexar arquivos maiores que o limite especificado. É um problema conhecido.

1. Use o [editor de metadados](/help/forms/using/manage-form-metadata.md) para selecionar o perfil personalizado criado acima para formulários do HTML 5.
1. Renderize seu modelo de formulário com o perfil personalizado e o ícone de anexos aparecerá na barra de ferramentas de formulários.

   >[!NOTE]
   >
   >Imediatamente, o portal de formulários fornece um perfil personalizado com os recursos de rascunhos e anexos ativados. Para obter mais informações sobre o perfil **Salvar como rascunho**, consulte [Salvando formulários do HTML5 como rascunho](/help/forms/using/saving-html5-form-draft.md).

1. Clique no ícone de anexo e será exibida uma caixa de diálogo de seleção de anexo. Procure e selecione o anexo e clique em **Anexar**.

   >[!NOTE]
   >
   >Para visualizar um anexo, clique no nome do anexo.

   >[!NOTE]
   >
   >A opção de visualização de arquivo não está disponível para usuários anônimos.

## Formato de envio do anexo {#attachment-submission-format}

Quando os anexos são ativados, o formulário HTML5 envia dados de várias partes. Os dados de envio de várias partes têm duas partes **dataXml** e **anexos**.

>[!NOTE]
>
>Para compatibilidade com versões anteriores, se a opção `mfAllowAttachments` estiver desativada, os formulários HTML5 não enviarão os dados de várias partes. Envia xml de dados simples no formato **application/xml**.

Se o sinalizador mfAllowAttachments estiver ativado, o [serviço de proxy de serviço de envio](/help/forms/using/service-proxy.md) também postará dados de várias partes com dataXml e anexos.
