---
title: Conversão de arquivos usando o PDF Generator
description: O serviço PDF Generator converte formatos de arquivo nativos em PDF. Também converte o PDF em outros formatos de arquivo e otimiza o tamanho dos documentos do PDF.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 060bb23d64a90f0b2da487ead4c672cbf471c9a8
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 0%

---

# Conversão de arquivos usando o PDF Generator{#converting-files-using-pdf-generator}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

É possível usar as páginas da Web do PDF Generator para converter arquivos.

## Criar um arquivo do PDF {#create-a-pdf-file}

1. No console de administração, clique em Serviços > PDF Generator > Criar PDF.
1. Clique em Procurar para localizar e selecionar o arquivo.

   >[!NOTE]
   >
   >O PDF Generator é capaz de detectar automaticamente o tipo de arquivo .doc, .xls, .ppt e .rtf, mesmo quando a extensão do arquivo não aparece no nome do arquivo. Esse recurso não funciona com arquivos .docx, .xlsx e .pptx.

1. Em Configurações, selecione Usar configurações personalizadas ou Fazer upload do arquivo de configurações.

   * Se você estiver usando configurações personalizadas, selecione uma configuração do Adobe PDF, uma configuração de segurança e uma configuração de tipo de arquivo e especifique um tempo limite.

     As configurações do Adobe PDF são aplicáveis somente às conversões de PS para PDF, EPS para PDF, PRN para PDF, Imagem para PDF com OCR ativado e Nativo para PDF. A configuração de tempo limite especifica o tempo máximo que a conversão leva para ser concluída. O padrão é 270 segundos. Essas configurações não são usadas durante as conversões de Imagem para PDF e OpenOffice para PDF.

   * Se você estiver fazendo upload de um arquivo de configurações, digite o caminho e o nome na caixa ou clique em Procurar para localizar e selecionar o arquivo.

1. (Opcional) Em Arquivo de metadados do XMP, digite o caminho e o nome do arquivo do XMP ou clique em Procurar para localizar e selecionar o arquivo. Um arquivo XMP pode ser usado para incluir informações de metadados padrão. (Consulte [Sobre arquivos XMP](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Clique em Criar. Quando o arquivo for criado, será exibido um link para ele. Se ocorrer um erro durante a conversão, um aviso será exibido. Se você estiver criando um arquivo Postscript, o aviso também conterá um link para o arquivo de log.
1. Clique no link do arquivo PDF. O arquivo é aberto no Acrobat.

### Sobre arquivos XMP {#about-xmp-files}

Os documentos do PDF que o PDF Generator cria no Acrobat 5.0 ou posterior contêm metadados de documento no formato XML. *Os metadados* incluem informações sobre o documento e seu conteúdo, como o nome do autor, palavras-chave e informações de direitos autorais que os utilitários de pesquisa podem usar.

Os metadados do documento contêm (mas não se limitam a) informações que também aparecem na guia Descrição da caixa de diálogo Propriedades do documento no Acrobat. As alterações feitas na guia Descrição são refletidas nos metadados do documento. Os metadados de documentos podem ser estendidos e modificados usando produtos de terceiros.

A Adobe Extensible Metadata Platform (XMP) fornece aos aplicativos da Adobe uma estrutura XML comum que padroniza a criação, o processamento e a troca de metadados de documentos em workflows de publicação. Você pode salvar e importar o código-fonte XML de metadados do documento no formato XMP, facilitando o compartilhamento de metadados entre vários documentos. Para obter mais informações sobre arquivos XMP, consulte [Plataforma de Metadados Extensível (XMP)](https://www.adobe.com/products/xmp/) e [Centro de Desenvolvedores do Adobe XMP](https://www.adobe.com/devnet/xmp.html).

Você pode criar arquivos XMP no Acrobat.

## Converter um arquivo HTML ou ZIP em um PDF {#convert-an-html-file-or-zip-file-to-pdf}

Você pode usar o PDF Generator para converter os seguintes tipos de arquivos para o Adobe PDF:

* Arquivos HTML, que podem ser convertidos por upload de um arquivo HTML ou especificando o URL de uma página da Web ou site.
* Arquivos compactados (ZIP), que podem conter arquivos HTML, arquivos de imagem ou ambos.

Se o arquivo ZIP contiver mais de um arquivo HTML no nível mais baixo de sua hierarquia de pastas, o arquivo ZIP também deverá conter um arquivo index.htm ou index.html.

>[!NOTE]
>
>* O recurso HTML para PDF requer determinadas fontes no diretório de fontes do sistema. Nos sistemas Linux, Solaris e AIX, o diretório de fontes do sistema deve conter a fonte Courier. Em sistemas Windows, o diretório de fontes do sistema deve conter Times New Roman.
>
>* (Somente para sistemas baseados em UNIX) Uma das seguintes fontes em japonês deve estar disponível no servidor do AEM Forms para converter uma página da Web com fonte em japonês em um documento do PDF.
>
>  * &quot;Sazanami Gothic&quot;
>  * Kozuka Gothic Pro-VI
>  * Kozuka Mincho Pro-VI
>  * &quot;Sazanami Gothic&quot;
>  * &quot;Kozuka Mincho Pr6N&quot;
>  * Sazanami Mincho
>  * &quot;Adobe Heiti Std&quot;
>  * &quot;Adobe Song Std&quot;
>
>* Para fazer upload de um arquivo do sistema de arquivos local, use a opção Fazer upload do arquivo na página HTML para o PDF.

1. No console de administração, clique em Serviços > PDF Generator > HTML para PDF.
1. Especifique o arquivo a ser convertido executando uma das seguintes tarefas:

   * Em Fazer upload do arquivo, digite o caminho e o nome do arquivo HTML ou ZIP, ou clique em Procurar para localizá-lo e selecioná-lo.
   * Na caixa Especificar URL, digite o URL da página ou do site que será convertido.

   >[!NOTE]
   >
   >O arquivo que você está convertendo deve ter uma extensão de nome de arquivo .html, .htm ou .zip.

1. Especifique as definições de configuração:

   * Para usar configurações personalizadas, selecione Usar configurações personalizadas, especifique as configurações de segurança e de tipo de arquivo e especifique um valor de tempo limite. O valor padrão é de 270 segundos.

   >[!NOTE]
   >
   >Se você tiver configurado o serviço Gerar PDF para usar o Acrobat WebCapture, as Configurações de tipo de arquivo selecionadas nesta página não afetarão o PDF produzido. Em vez disso, faça as alterações apropriadas na versão do Acrobat instalada no servidor.

   * Para usar um arquivo de configurações existente, selecione Fazer upload do arquivo de configurações e clique em Procurar para ir para o local do arquivo.

1. Para fazer upload de um arquivo do XMP, clique em Procurar e vá para o local do arquivo. Um arquivo XMP pode ser usado para incluir informações de metadados padrão. (Consulte [Sobre arquivos XMP](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Clique em Criar. Quando o arquivo é criado, um link para o arquivo do PDF é exibido.
1. Clique no link para exibir o documento do PDF no Acrobat.

## Exportar um arquivo do PDF para outro formato de arquivo (somente Windows) {#export-a-pdf-file-to-another-file-format-windows-only}

Você pode exportar arquivos PDF para vários formatos de arquivo, conforme descrito no capítulo Gerar Serviços PDF da [Referência de Serviços](https://www.adobe.com/go/learn_aemforms_services_63).

1. No console de administração, clique em Serviços > PDF Generator > Export PDF.
1. Clique em Procurar para localizar o arquivo do PDF a ser exportado.
1. Na lista Export PDF file to, selecione o formato para o qual exportar o arquivo PDF.
1. Na caixa Especificar um tempo limite, digite o tempo de espera antes que o aplicativo expire. O valor padrão é de 270 segundos.

   O Tempo de conversão exibido quando o arquivo é convertido pode ser maior que o valor especificado aqui. O Tempo de conversão inclui o tempo gasto aguardando o thread ou processo, o tempo gasto para converter o arquivo e o tempo gasto pelo conversor de fallback (se aplicável). hora. O valor de Especificar um tempo limite é apenas o tempo necessário para converter o arquivo.

1. (Opcional) Na opção **Especificar perfil de comprovação personalizado**, clique em Procurar e selecione um [perfil de comprovação personalizado](https://helpx.adobe.com/acrobat/using/preflight-profiles-acrobat-pro.html). Os perfis de comprovação são usados somente ao converter documentos no formato de arquivo PDF (PDF/A).
1. Clique em Exportar. Quando a conversão estiver concluída, um link para o arquivo exportado será exibido.
1. Clique no link para exibir o arquivo convertido.

## Otimizar um PDF (somente Windows) {#optimize-a-pdf}

O PDF Generator permite reduzir o tamanho dos arquivos PDF.

>[!NOTE]
>
>A otimização de um documento assinado digitalmente remove e invalida as assinaturas digitais.

1. No console de administração, clique em Serviços > PDF Generator > Otimizar PDF.
1. Clique em Procurar para localizar o arquivo do PDF a ser otimizado.
1. Especifique as definições de configuração:

   * Para usar configurações personalizadas, selecione Usar configurações personalizadas, especifique as configurações de tipo de arquivo e especifique um valor de tempo limite. O valor padrão é de 270 segundos.
   * Para usar um arquivo de configurações existente, selecione Fazer upload do arquivo de configurações e clique em Procurar para ir para o local do arquivo.

1. Clique em Criar.
