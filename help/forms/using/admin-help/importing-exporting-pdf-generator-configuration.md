---
title: Importação e exportação de arquivos de configuração do PDF Generator
description: Saiba como importar e exportar arquivos de configuração do PDF Generator.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 3bd5ef75-7e35-4398-a7a3-0178a9c06db0
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Importação e exportação de arquivos de configuração do PDF Generator {#importing-and-exporting-pdf-generator-configuration-files}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

O arquivo de configuração contém as informações de conversão do PDF Generator, incluindo o PDF, o tipo de arquivo e as configurações de segurança.

>[!NOTE]
>
>Não é possível alterar a configuração de tempo limite do PDF Generator importando um arquivo nativo2pdfconfig.xml personalizado. A configuração de tempo limite nesse arquivo é apenas para fins informativos e exibe a configuração atual no PDF Generator. Para alterar a configuração de tempo limite, consulte &quot;Definindo parâmetros de desempenho do PDF Generator&quot; em [Instalando e implantando formulários do AEM](https://www.adobe.com/go/learn_aemforms_installJBoss_63).

## Exportar seu arquivo de configuração atual {#export-your-current-configuration-file}

1. No console de administração, clique em Serviços > PDF Generator > Arquivos de configuração > Exportar configuração.
1. Para exportar as configurações, selecione a opção apropriada:

   * Para exportar todas as configurações nomeadas, selecione Baixar configuração inteira.
   * Para exportar apenas uma configuração do Adobe PDF, de segurança ou de tipo de arquivo, selecione Baixar configuração mínima.

     Se estiver exportando uma configuração mínima, selecione as configurações de Adobe PDF, segurança e tipo de arquivo a serem exportadas.

1. Clique em Baixar e salve o arquivo XML em um local apropriado.

## Importar um arquivo de configuração {#import-a-configuration-file}

>[!NOTE]
>
>O sistema será reconfigurado com base nas informações do arquivo importado.

1. No console de administração, clique em Serviços > PDF Generator > Arquivos de configuração > Importar configuração.
1. Selecione Import An Existing Configuration File.
1. Para especificar o local do arquivo na caixa Arquivo de Configuração, clique em Procurar para localizar e selecionar o arquivo e clique em **Importar**.

## Converter todas as camadas dentro de arquivos do AutoCAD {#convert-all-layers-within-autocad-files}

Por padrão, o PDF Generator converte somente a camada padrão dos arquivos do AutoCAD para o PDF, em vez de todas as camadas do arquivo. Para converter todas as camadas, siga este procedimento.

1. No console de administração, clique em Serviços > PDF Generator > Arquivos de configuração > Exportar configuração.
1. Selecione Baixar toda a configuração e clique em Baixar.
1. Em um editor de texto, abra o arquivo baixado e, na tag `AutoCAD` dentro da tag `PDFMaker`, adicione o texto `convertAllPages="true"`.
1. No console de administração, clique em Serviços > PDF Generator > Arquivos de configuração > Importar configuração.
1. Selecione Importar um arquivo de configuração existente, especifique o arquivo atualizado e clique em Importar.

   Todos os arquivos do AutoCAD convertidos com o arquivo de configuração modificado terão todas as camadas convertidas.

## Redefina suas configurações para as configurações originais instaladas com o PDF Generator {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. No console de administração, clique em Serviços > PDF Generator > Arquivos de configuração > Importar configuração.
1. Selecione Redefinir configuração para configurações padrão e clique em Importar.
