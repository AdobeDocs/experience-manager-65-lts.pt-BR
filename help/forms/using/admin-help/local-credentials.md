---
title: Gerenciar credenciais locais
description: Saiba como gerenciar credenciais locais usando o Gerenciamento de armazenamento de confiança. Os formulários AEM são compatíveis com credenciais RSA e DSA no formulário PKCS12 padrão.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: true
hidefromtoc: true
exl-id: d297ab09-2b92-442a-8b19-ffee86e24bb9
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Gerenciar credenciais locais {#managing-local-credentials}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

As credenciais locais são credenciais de chave privada hospedadas no Gerenciamento de Repositório de Confiança. Uma *credencial local* identifica onde a credencial DES de um usuário está armazenada. Usando o Gerenciamento de Armazenamento de Confiança, você pode importar e gerenciar suas credenciais locais usando, por exemplo, arquivos PFX existentes para poder importar, editar e excluir credenciais locais.

Os formulários AEM são compatíveis com credenciais RSA e DSA de até 4.096 bits no formato PKCS12 padrão (arquivos .pfx e .p12).

É possível importar e exportar qualquer número de credenciais. Se você quiser substituir uma credencial expirada usando o mesmo alias, exclua a credencial e importe a nova credencial com o mesmo alias.

Para obter informações e instruções relacionadas às extensões do Acrobat Reader DC, consulte [Configuração de credenciais para uso com extensões do Acrobat Reader DC](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).

## Importar uma credencial {#import-a-credential}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais locais.
1. Clique em Importar. Em Tipo de armazenamento de confiança, selecione uma destas opções:

   * **Credencial de Assinatura de Documento:** Uma credencial usada para emitir uma assinatura digital em um documento.
   * **Credencial de extensões do Acrobat Reader DC:** um certificado digital específico das extensões do Acrobat Reader DC que permite que os direitos de uso do Adobe Reader sejam ativados nos documentos do PDF produzidos.
   * **Padrão:** indica que esta é a credencial padrão a ser usada com as extensões do Acrobat Reader DC.

   Para obter informações sobre como obter uma credencial, consulte [Preparando para instalar formulários do AEM](https://helpx.adobe.com/pdf/aem-forms/6-3/prepare-install-single-server.pdf).

1. Na caixa Alias, digite um identificador para a credencial. Esse identificador é usado como o nome de exibição da credencial nas extensões do Acrobat Reader DC e no serviço de assinatura. Esse alias também é usado para acessar a credencial de forma programática usando o AEM Forms SDK.

   >[!NOTE]
   >
   >O nome do alias é convertido automaticamente em maiúsculas para fins de exibição. O nome do alias não diferencia maiúsculas de minúsculas quando você faz referência a ele em um processo.

1. Clique em Procurar para localizar a credencial, digite a senha da credencial e clique em OK.

   Se a mensagem de erro &quot;Falha ao importar credencial devido a um formato de arquivo incorreto ou senha incorreta&quot; for exibida, verifique se a senha é válida.

## Exportar uma credencial {#export-a-credential}

As credenciais são exportadas como arquivos P12 no formato PKCS#12.

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais locais.
1. Clique no nome do alias da credencial que você deseja exportar e clique em Exportar.
1. Na caixa Senha, digite a senha. Essa senha é nova e é usada para criptografar a credencial exportada.
1. Clique em Exportar, siga as instruções para exportar a credencial e clique em OK.

## Editar um alias ou tipo de armazenamento de confiança da credencial {#edit-a-credential-s-alias-or-trust-store-type}

Depois que uma credencial for importada, você poderá editar seu nome de alias e tipo de armazenamento de confiança.

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais locais.
1. Clique no nome do alias da credencial que deseja editar.
1. Clique em Atualizar credencial.
1. Edite o nome do alias e o tipo de armazenamento de confiança conforme necessário e clique em OK.

## Excluir uma credencial {#delete-a-credential}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais locais.
1. Marque as caixas de seleção das credenciais a serem excluídas.
1. Clique em Excluir e em OK.
