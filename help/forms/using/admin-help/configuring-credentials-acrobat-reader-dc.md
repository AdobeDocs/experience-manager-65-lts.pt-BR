---
title: Configuração de credenciais para uso com extensões do Acrobat Reader DC
description: Saiba como configurar credenciais para usar com extensões do Acrobat Reader DC.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 040a4db1-45e1-4501-8117-d2d41d4a73ea
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Configuração de credenciais para uso com extensões do Acrobat Reader DC{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

Para aplicar direitos de uso a documentos do PDF, configure formulários do AEM com uma credencial válida para extensões do Acrobat Reader DC. Uma credencial pode ter sido configurada durante a instalação do AEM Forms. Se você não tiver configurado a credencial de extensões do Acrobat Reader DC ao executar o Configuration Manager ou se precisar importar uma credencial nova ou de substituição, poderá fazê-lo usando as páginas Gerenciamento de armazenamento de confiança.

Se estiver usando uma credencial de avaliação, substitua-a por uma credencial de produção ao migrar para o ambiente de produção. Para atualizar uma credencial expirada ou de avaliações, primeiro exclua a antiga credencial do Acrobat Reader DC Extensions.

Para obter informações sobre como obter uma credencial, consulte [Preparando para Instalar o AEM Forms (Servidor Único)](https://helpx.adobe.com/pdf/aem-forms/6-3/prepare-install-single-server.pdf).

O armazenamento de confiança pode conter mais de uma credencial de extensões do Acrobat Reader DC. Designe uma dessas credenciais como a credencial padrão do Reader Extensions. A credencial padrão é usada quando um usuário do Workbench não consegue determinar qual credencial usar durante a criação do processo. Estas regras se aplicam às credenciais padrão:

* Se você importar uma credencial de extensões do Acrobat Reader DC e o Armazenamento de confiança não contiver outras credenciais de extensões do Acrobat Reader DC, ela será definida como padrão.
* Se você importar uma credencial de extensões do Acrobat Reader DC com a opção Padrão selecionada, o tipo padrão será removido de uma credencial padrão existente. A credencial importada se torna o padrão.
* Não é possível excluir uma credencial padrão de extensões do Acrobat Reader DC. Para excluir a credencial padrão, primeiro defina outra credencial como padrão. Uma exceção a essa regra é que, se houver apenas uma credencial, você poderá excluí-la, mesmo que seja o padrão.
* Não é possível atualizar uma credencial padrão de extensões do Acrobat Reader DC.

>[!NOTE]
>
>Você também pode importar e excluir credenciais de forma programática. (Consulte [Programação com AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=pt-BR).)

## Importar uma credencial de extensões do Acrobat Reader DC {#import-a-acrobat-reader-dc-extensions-credential}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais locais.
1. Clique em Importar e, em Tipo de armazenamento de confiança, selecione Acrobat Reader DC Extensions Credential.
1. (Opcional) Para indicar que essa é a credencial padrão a ser usada com as extensões do Acrobat Reader DC, selecione Padrão.
1. Na caixa Alias, digite um identificador para a credencial. Esse identificador é usado como o nome de exibição da credencial nas extensões do Acrobat Reader DC. Esse alias também é usado para acessar a credencial de forma programática usando o AEM Forms SDK.

   >[!NOTE]
   >
   >O nome do alias é convertido automaticamente em maiúsculas para fins de exibição. O nome do alias não diferencia maiúsculas de minúsculas quando você faz referência a ele em um processo.

1. Clique em Escolher Arquivo para localizar a credencial, digite a senha da credencial e clique em OK.

   Se a mensagem de erro &quot;Falha ao importar credencial devido a um formato de arquivo incorreto ou senha incorreta&quot; for exibida, verifique se a senha é válida.

## Remover uma credencial de extensões do Acrobat Reader DC {#remove-a-acrobat-reader-dc-extensions-credential}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais locais.
1. Selecione a credencial e clique em Excluir.

## Substituir uma credencial de extensões do Acrobat Reader DC {#replace-a-acrobat-reader-dc-extensions-credential}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais locais.
1. Anote o alias da credencial existente, selecione-o e clique em Excluir.
1. Importe a nova credencial usando exatamente o mesmo nome de alias.
