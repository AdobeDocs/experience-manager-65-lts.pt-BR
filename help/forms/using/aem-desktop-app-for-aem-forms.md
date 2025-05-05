---
title: Aplicativo de desktop do Adobe Experience Manager (AEM) para AEM Forms
description: Aplicativo de desktop do Adobe Experience Manager (AEM) para AEM Forms
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: manage
noindex: true
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Aplicativo de desktop do Adobe Experience Manager (AEM) para AEM Forms {#aem-desktop-app-for-aem-forms}

O aplicativo de desktop do AEM permite mapear o repositório do Adobe Experience Manager (AEM) Assets e os arquivos binários do AEM Forms para um diretório de rede no sistema. Você pode exibir os ativos sincronizados e os arquivos binários em um explorador de arquivos e usar vários aplicativos para editar os arquivos conforme desejado. Além de visualizar os arquivos, você também pode criar, fazer upload e excluir os arquivos binários. Você também pode abrir, editar e salvar arquivos diretamente do software. Por exemplo, você pode abrir e editar diretamente um arquivo XDP do Designer. As alterações feitas nos ativos localmente são refletidas no repositório do AEM Assets e na interface do usuário do AEM Forms.

Você pode baixar o aplicativo de uma instância do AEM. Para obter informações detalhadas sobre como baixar o aplicativo, consulte as [Notas de versão do aplicativo de desktop da AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=pt-BR).

## Ativos do AEM Forms compatíveis com o aplicativo de desktop do AEM {#aem-forms-assets-supported-in-aem-desktop-app}

Você pode usar o aplicativo para sincronizar arquivos binários AEM Forms dos seguintes tipos: Modelos de formulário (.xdp), Formulário PDF (.pdf), Documento (.pdf), Imagens, Esquema XML (.xsd), Folhas de estilos (.xfs). O aplicativo lista todos os outros arquivos (arquivos não compatíveis) como arquivos de 0 byte. Listar arquivos não compatíveis como arquivos de 0 byte garante que o usuário esteja ciente da existência de outros ativos disponíveis no servidor do AEM Forms.

>[!NOTE]
>
>Um nome de arquivo só pode conter caracteres alfanuméricos, hífen ou sublinhado.

## Habilitar o aplicativo de desktop AEM Forms para AEM {#enable-aem-forms-for-aem-desktop-app}

O aplicativo de desktop da AEM usa o protocolo WebDAV no Microsoft® Windows e SMB1 no macOS X para se conectar a um servidor AEM Forms. Pronto para uso, o AEM Forms Server não é habilitado para sincronizar arquivos binários e outros ativos com um cliente WebDAV ou SMB. Execute as seguintes etapas para habilitar o aplicativo de desktop AEM Forms para AEM:

1. Faça logon no AEM Forms como administrador.
1. Na instância do autor, clique em ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Ferramentas]** ![martelo](assets/hammer.png) **[!UICONTROL > Implantação > Operações > Console da Web]**. O Console da Web é aberto em uma nova janela.
1. Na janela Console da Web, localize e abra a opção **[!UICONTROL Configuração de complemento do FormsManager]**.
1. Na caixa de diálogo Configuração de complemento do FormsManager, desmarque a caixa de seleção **[!UICONTROL Sincronizar recursos de forma assíncrona]** e clique em **[!UICONTROL Salvar]**.
1. Reinicie o servidor do AEM Forms. Após a reinicialização, o servidor do AEM Forms é ativado para aceitar e compartilhar conteúdo com o aplicativo de desktop do AEM.
1. Abra o aplicativo e conecte-se ao AEM Forms Server.

   >[!NOTE]
   >
   > É recomendável usar o comando &#39;Ctrl + C&#39; para reiniciar o SDK. Reiniciar o AEM SDK usando métodos alternativos, por exemplo, parar processos Java, pode levar a inconsistências no ambiente de desenvolvimento do AEM.

   Ao se conectar com êxito, o aplicativo preenche as pastas `content/dam` e `content/dam/formsanddocuments`. Além de mover arquivos das pastas acima para pastas locais e vice-versa, você pode usar o aplicativo para mover conteúdo entre pastas preenchidas automaticamente.
