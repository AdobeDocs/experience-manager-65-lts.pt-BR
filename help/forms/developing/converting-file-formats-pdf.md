---
title: Conversão entre formatos de arquivo e PDF
description: Use o serviço Gerar PDF para converter formatos de arquivo nativos em PDF. O serviço Gerar PDF também converte o PDF para outros formatos de arquivo e otimiza o tamanho dos documentos do PDF.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, Document Services
hide: true
hidefromtoc: true
exl-id: c6e007e9-6050-4d86-a32e-0bd942d48f27
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '7848'
ht-degree: 0%

---

# Conversão entre formatos de arquivo e PDF {#converting-between-file-formatsand-pdf}

**Exemplos e exemplos neste documento são somente para AEM Forms no ambiente JEE.**

**Sobre o Serviço de Geração de PDF**

O serviço Gerar PDF converte formatos de arquivo nativos em PDF. Também converte o PDF em outros formatos de arquivo e otimiza o tamanho dos documentos do PDF.

O serviço Gerar PDF usa aplicativos nativos para converter os seguintes formatos de arquivo para o PDF. Salvo indicação em contrário, somente as versões em alemão, francês, inglês e japonês desses aplicativos são compatíveis. *Somente Windows* indica suporte somente para Windows Server® 2003 e Windows Server 2008.

* Microsoft Office 2003 e 2007 para converter DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX, XPS e PUB (somente para Windows)

>[!NOTE]
>
>É necessário o Acrobat® 9.2 ou posterior para converter o formato Microsoft XPS em PDF.

* Autodesk AutoCAD 2005, 2006, 2007, 2008 e 2009 para converter DWF, DWG e DXW (somente em inglês)
* Corel WordPerfect 12 e X4 para converter WPD, QPW, SHW (somente em inglês)
* OpenOffice 2.0, 2.4, 3.0.1 e 3.1 para converter ODT, ODS, ODP, ODG, ODF, SXW, SXI, SXD, DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX e PUB

>[!NOTE]
>
>O serviço Gerar PDF não oferece suporte às versões de 64 bits do OpenOffice.

* Adobe Photoshop® CS2 para converter PSD (somente Windows)

>[!NOTE]
>
>O Photoshop CS3 e o CS4 não têm suporte porque não são compatíveis com o Windows Server 2003 ou o Windows Server 2008.

* Adobe FrameMaker® 7.2 e 8 para converter FM (somente Windows)
* Adobe PageMaker® 7.0 para converter PMD, PM6, P65 e PM (somente Windows)
* Formatos nativos compatíveis com aplicativos de terceiros (requer o desenvolvimento de arquivos de configuração específicos para o aplicativo) (somente Windows)

O serviço Gerar PDF converte os seguintes formatos de arquivo baseados em padrões para o PDF.

* Formatos de vídeo: SWF, FLV (somente Windows)
* Formatos de imagem: JPEG, JPG, JP2, J2Kí, JPC, J2C, GIF, BMP, TIFF, TIF, PNG, JPF
* HTML (Windows, Sun™ Solaris™ e Linux®)

O serviço Gerar PDF converte o PDF nos seguintes formatos de arquivo (somente Windows):

* PostScript encapsulado (EPS)
* HTML 3.2
* HTML 4.01 com CSS 1.0
* DOC (formato do Microsoft Word)
* RTF
* Texto (acessível e simples)
* XML
* PDF/A-1a que usa somente o espaço de cores DeviceRGB
* PDF/A-1b que usa somente o espaço de cores DeviceRGB

O serviço Gerar PDF exige a execução das seguintes tarefas administrativas:

* Instalar os aplicativos nativos necessários no computador que hospeda o AEM Forms
* Instale o Adobe Acrobat Professional ou o Acrobat Pro Extended 9.2 no computador que hospeda o AEM Forms
* Executar tarefas de configuração pós-instalação

Essas tarefas são descritas em Instalação e implantação do AEM Forms usando JBoss Turnkey.

Você pode realizar essas tarefas usando o serviço Gerar PDF:

* Converter formatos de arquivo nativos em PDF.
* Converter documentos do HTML em documentos do PDF.
* Converter documentos do PDF em formatos de arquivo.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Gerar PDF, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Convertendo Documentos do Word em Documentos do PDF {#converting-word-documents-to-pdf-documents}

Esta seção descreve como você pode usar a API Generate PDF para converter programaticamente um documento do Microsoft Word em um documento do PDF.

>[!NOTE]
>
>Para obter mais informações sobre formatos de arquivo adicionais, consulte [Adicionando Suporte para Formatos de Arquivo Nativos Adicionais](converting-file-formats-pdf.md#adding-support-for-additional-native-file-formats).

>[!NOTE]
>
>Para obter mais informações sobre o serviço Gerar PDF, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary-of-steps}

Para converter um documento do Microsoft Word em um documento do PDF, execute as seguintes tarefas:

1. Incluir arquivos de projeto.
1. Crie um cliente Generate PDF.
1. Recupere o arquivo para converter em um documento do PDF.
1. Converta o arquivo em um documento do PDF.
1. Recupere os resultados.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente para Gerar PDF**

Antes de executar programaticamente uma operação Generate PDF, crie um cliente de serviço Generate PDF. Se você estiver usando a API Java, crie um objeto `GeneratePdfServiceClient`. Se você estiver usando a API de serviço Web, crie um objeto `GeneratePDFServiceService`.

**Recuperar o arquivo para converter em um documento do PDF**

Recupere o documento do Microsoft Word para converter em um documento do PDF.

**Converter o arquivo em um documento do PDF**

Depois de criar o cliente de serviço Gerar PDF, você pode invocar o método `createPDF2`. Este método precisa de informações sobre o documento a ser convertido, incluindo a extensão do arquivo.

**Recuperar os resultados**

Depois que o arquivo for convertido em um documento do PDF, você poderá recuperar os resultados. Por exemplo, depois de converter um arquivo do Word em um documento do PDF, você pode recuperar e salvar o documento do PDF.

**Consulte também**

[Converter documentos do Word em documentos do PDF usando a API Java](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-java-api)

[Converter documentos do Word para documentos do PDF usando a API de serviço Web](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Gerar inicializações rápidas da API de serviço do PDF](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Converter documentos do Word em documentos do PDF usando a API Java {#convert-word-documents-to-pdf-documents-using-the-java-api}

Converta um documento do Microsoft Word em um documento do PDF usando a API Gerar PDF (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-generatepdf-client.jar, no caminho de classe do projeto Java.

1. Crie um cliente Generate PDF.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `GeneratePdfServiceClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Recupere o arquivo para converter em um documento do PDF.

   * Crie um objeto `java.io.FileInputStream` que represente o arquivo do Word a ser convertido usando seu construtor. Transmita um valor de string que especifique o local do arquivo.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Converta o arquivo em um documento do PDF.

   Converta o arquivo em um documento PDF invocando o método `createPDF2` do objeto `GeneratePdfServiceClient` e transmitindo os seguintes valores:

   * Um objeto `com.adobe.idp.Document` que representa o arquivo a ser convertido.
   * Um objeto `java.lang.String` que contém a extensão de arquivo.
   * Um objeto `java.lang.String` que contém as configurações de tipo de arquivo a serem usadas na conversão. As configurações de tipo de arquivo fornecem configurações de conversão para diferentes tipos de arquivo, como .doc ou .xls.
   * Um objeto `java.lang.String` que contém o nome das configurações do PDF a serem usadas. Por exemplo, você pode especificar `Standard`.
   * Um objeto `java.lang.String` que contém o nome das configurações de segurança a serem usadas.
   * Um objeto `com.adobe.idp.Document` opcional que contém configurações a serem aplicadas durante a geração do documento PDF.
   * Um objeto `com.adobe.idp.Document` opcional que contém informações de metadados a serem aplicadas ao documento do PDF.

   O método `createPDF2` retorna um objeto `CreatePDFResult` que contém o novo documento do PDF e uma informação de log. O arquivo de log normalmente contém mensagens de erro ou aviso geradas pela solicitação de conversão.

1. Recupere os resultados.

   Para obter o documento do PDF, execute as seguintes ações:

   * Invoque o método `getCreatedDocument` do objeto `CreatePDFResult`, que retorna um objeto `com.adobe.idp.Document`.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para extrair o documento PDF do objeto criado na etapa anterior.

   Se você usou o método `createPDF2` para obter o documento de log (não aplicável a conversões do HTML), execute as seguintes ações:

   * Invoque o método `getLogDocument` do objeto `CreatePDFResult`. Isso retorna um objeto `com.adobe.idp.Document`.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para extrair o documento de log.

**Consulte também**

[Resumo das etapas](converting-file-formats-pdf.md#summary-of-steps)

[Início rápido (modo SOAP): conversão de um documento do Microsoft Word em um documento PDF usando a API Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Converter documentos do Word para documentos do PDF usando a API de serviço Web {#convert-word-documents-to-pdf-documents-using-the-web-service-api}

Converta um documento do Microsoft Word em um documento do PDF usando a API Gerar PDF (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um cliente Generate PDF.

   * Crie um objeto `GeneratePDFServiceClient` usando seu construtor padrão.
   * Crie um objeto `GeneratePDFServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. No entanto, especifique `?blob=mtom`.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `GeneratePDFServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere o arquivo para converter em um documento do PDF.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar o arquivo que você deseja converter em um documento PDF.
   * Crie um objeto `System.IO.FileStream` invocando seu construtor. Transmita um valor de string que represente o local do arquivo a ser convertido e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo à propriedade `MTOM` o conteúdo da matriz de bytes.

1. Converta o arquivo em um documento do PDF.

   Converta o arquivo em um documento PDF invocando o método `CreatePDF2` do objeto `GeneratePDFServiceService` e transmitindo os seguintes valores:

   * Um objeto `BLOB` que representa o arquivo a ser convertido.
   * Uma cadeia de caracteres que contém a extensão de arquivo.
   * Um objeto `java.lang.String` que contém as configurações de tipo de arquivo a serem usadas na conversão. As configurações de tipo de arquivo fornecem configurações de conversão para diferentes tipos de arquivo, como .doc ou .xls.
   * Um objeto de string que contém as configurações do PDF a serem usadas. Você pode especificar `Standard`.
   * Um objeto de cadeia de caracteres que contém as configurações de segurança a serem usadas. Você pode especificar `No Security`.
   * Um objeto `BLOB` opcional que contém configurações a serem aplicadas durante a geração do documento PDF.
   * Um objeto `BLOB` opcional que contém informações de metadados a serem aplicadas ao documento do PDF.
   * Um parâmetro de saída do tipo `BLOB` preenchido pelo método `CreatePDF2`. O método `CreatePDF2` preenche este objeto com o documento convertido. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).
   * Um parâmetro de saída do tipo `BLOB` preenchido pelo método `CreatePDF2`. O método `CreatePDF2` preenche este objeto com o documento de log. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).

1. Recupere os resultados.

   * Recupere o documento PDF convertido atribuindo o campo `MTOM` do objeto `BLOB` a uma matriz de bytes. A matriz de bytes representa o documento PDF convertido. Use o objeto `BLOB` que é usado como parâmetro de saída para o método `createPDF2`.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF convertido.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](converting-file-formats-pdf.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Conversão de documentos do HTML em documentos do PDF {#converting-html-documents-to-pdf-documents}

Esta seção descreve como você pode usar a API Generate PDF para converter programaticamente documentos do HTML em documentos do PDF.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Gerar PDF, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-1}

Para converter um documento do HTML em um documento do PDF, execute as seguintes tarefas:

1. Incluir arquivos de projeto.
1. Crie um cliente Generate PDF.
1. Recupere o conteúdo do HTML para converter em um documento do PDF.
1. Converta o conteúdo do HTML em um documento do PDF.
1. Recupere os resultados.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente para Gerar PDF**

Antes de executar programaticamente uma operação Generate PDF, você deve criar um cliente de serviço Generate PDF. Se você estiver usando a API Java, crie um objeto `GeneratePdfServiceClient`. Se você estiver usando a API de serviço Web, crie um `GeneratePDFServiceService`.

**Recupere o conteúdo do HTML para converter em um documento do PDF**

Referencie o conteúdo do HTML que você deseja converter em um documento do PDF. Você pode fazer referência ao conteúdo do HTML, como um arquivo do HTML ou conteúdo do HTML acessível por meio de um URL.

**Converter o conteúdo do HTML em um documento do PDF**

Depois de criar o cliente de serviço, você pode chamar a operação de criação apropriada do PDF. Esta operação precisa de informações sobre o documento a ser convertido, incluindo o caminho para o documento de destino.

**Recuperar os resultados**

Depois que o conteúdo do HTML for convertido em um documento do PDF, você poderá recuperar os resultados e salvar o documento do PDF.

**Consulte também**

[Converter conteúdo do HTML em um documento do PDF usando a API Java](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-java-api)

[Converter conteúdo do HTML em um documento do PDF usando a API do serviço Web](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Gerar inicializações rápidas da API de serviço do PDF](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Converter conteúdo do HTML em um documento do PDF usando a API Java {#convert-html-content-to-a-pdf-document-using-the-java-api}

Converta um documento do HTML em um documento do PDF usando a API Gerar PDF (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-generatepdf-client.jar, no caminho de classe do projeto Java.

1. Crie um cliente Generate PDF.

   Crie um objeto `GeneratePdfServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Recupere o conteúdo do HTML para converter em um documento do PDF.

   Recupere o conteúdo do HTML criando uma variável de sequência e atribuindo um URL que aponte para o conteúdo do HTML.

1. Converta o conteúdo do HTML em um documento do PDF.

   Invoque o método `htmlToPDF2` do objeto `GeneratePdfServiceClient` e passe os seguintes valores:

   * Um objeto `java.lang.String` que contém a URL do arquivo HTML a ser convertido.
   * Um objeto `java.lang.String` que contém as configurações de tipo de arquivo a serem usadas na conversão. As configurações de tipo de arquivo podem incluir níveis de spidering.
   * Um objeto `java.lang.String` que contém o nome das configurações de segurança a serem usadas.
   * Um objeto `com.adobe.idp.Document` opcional que contém configurações a serem aplicadas durante a geração do documento PDF. Se essas informações não forem fornecidas, as configurações serão escolhidas automaticamente com base nos três parâmetros anteriores.
   * Um objeto `com.adobe.idp.Document` opcional que contém informações de metadados a serem aplicadas ao documento do PDF.

1. Recupere os resultados.

   O método `htmlToPDF2` retorna um objeto `HtmlToPdfResult` que contém o novo documento PDF gerado. Para obter o documento PDF recém-criado, execute as seguintes ações:

   * Invoque o método `getCreatedDocument` do objeto `HtmlToPdfResult`. Isso retorna um objeto `com.adobe.idp.Document`.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para extrair o documento PDF do objeto criado na etapa anterior.

**Consulte também**

[Conversão de documentos do HTML em documentos do PDF](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Início rápido (modo SOAP): conversão de conteúdo HTML em um documento PDF usando a API Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Início rápido (modo SOAP): conversão de conteúdo HTML em um documento PDF usando a API Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Converter conteúdo do HTML em um documento do PDF usando a API do serviço Web {#convert-html-content-to-a-pdf-document-using-the-web-service-api}

Converta conteúdo do HTML em um documento do PDF usando a API Generate PDF (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um cliente Generate PDF.

   * Crie um objeto `GeneratePDFServiceClient` usando seu construtor padrão.
   * Crie um objeto `GeneratePDFServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. No entanto, especifique `?blob=mtom`.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `GeneratePDFServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere o conteúdo do HTML para converter em um documento do PDF.

   Recupere o conteúdo do HTML criando uma variável de sequência e atribuindo um URL que aponte para o conteúdo do HTML.

1. Converta o conteúdo do HTML em um documento do PDF.

   Converta o conteúdo do HTML em um documento do PDF invocando o método `HtmlToPDF2` do objeto `GeneratePDFServiceService` e passe os seguintes valores:

   * Uma string que contém o conteúdo do HTML a ser convertido.
   * Um objeto `java.lang.String` que contém as configurações de tipo de arquivo a serem usadas na conversão.
   * Um objeto de cadeia de caracteres que contém as configurações de segurança a serem usadas.
   * Um objeto `BLOB` opcional que contém configurações a serem aplicadas durante a geração do documento PDF.
   * Um objeto `BLOB` opcional que contém informações de metadados a serem aplicadas ao documento do PDF.
   * Um parâmetro de saída do tipo `BLOB` preenchido pelo método `CreatePDF2`. O método `CreatePDF2` preenche este objeto com o documento convertido. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).

1. Recupere os resultados.

   * Recupere o documento PDF convertido atribuindo o campo `MTOM` do objeto `BLOB` a uma matriz de bytes. A matriz de bytes representa o documento PDF convertido. Use o objeto `BLOB` que é usado como parâmetro de saída para o método `HtmlToPDF2`.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF convertido.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Conversão de documentos do HTML em documentos do PDF](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Conversão de documentos do PDF em formatos que não são de imagem {#converting-pdf-documents-to-non-image-formats}

Esta seção descreve como você pode usar a API Java Generate PDF e a API de serviço da Web para converter programaticamente um documento do PDF em um arquivo RTF, que é um exemplo de formato que não é de imagem. Outros formatos que não são de imagem incluem HTML, texto, DOC e EPS. Ao converter um documento do PDF em RTF, verifique se o documento do PDF não contém elementos de formulário, como um botão de envio. Os elementos de formulário não são convertidos.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Gerar PDF, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-2}

Para converter um documento do PDF em qualquer um dos tipos compatíveis, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um cliente Generate PDF.
1. Recupere o documento do PDF para conversão.
1. Converta o documento do PDF.
1. Salve o arquivo convertido.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente para Gerar PDF**

Antes de executar programaticamente uma operação Generate PDF, você deve criar um cliente de serviço Generate PDF. Se você estiver usando a API Java, crie um objeto `GeneratePdfServiceClient`. Se você estiver usando a API de serviço Web, crie um objeto `GeneratePDFServiceService`.

**Recuperar o documento do PDF para conversão**

Recupere o documento do PDF para convertê-lo em um formato que não seja de imagem.

**Converter o documento do PDF**

Depois de criar o cliente de serviço, você pode chamar a operação de exportação do PDF. Esta operação precisa de informações sobre o documento a ser convertido, incluindo o caminho para o documento de destino.

**Salvar o arquivo convertido**

Salve o arquivo convertido. Por exemplo, se você converter um documento PDF em um arquivo RTF, salve o documento convertido em um arquivo RTF.

**Consulte também**

[Converter um documento do PDF em um arquivo RTF usando a API Java](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-java-api)

[Converter um documento do PDF em um arquivo RTF usando a API do serviço Web](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Gerar inicializações rápidas da API de serviço do PDF](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Converter um documento do PDF em um arquivo RTF usando a API Java {#convert-a-pdf-document-to-a-rtf-file-using-the-java-api}

Converta um documento do PDF em um arquivo RTF usando a API Gerar PDF (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-generatepdf-client.jar, no caminho de classe do projeto Java.

1. Crie um cliente Generate PDF.

   Crie um objeto `GeneratePdfServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Recupere o documento do PDF para conversão.

   * Crie um objeto `java.io.FileInputStream` que represente o documento PDF a ser convertido usando seu construtor. Transmita um valor de string que especifique o local do documento do PDF.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Converta o documento do PDF.

   Invoque o método `exportPDF2` do objeto `GeneratePdfServiceClient` e passe os seguintes valores:

   * Um objeto `com.adobe.idp.Document` que representa o arquivo PDF a ser convertido.
   * Um objeto `java.lang.String` que contém o nome do arquivo a ser convertido.
   * Um objeto `java.lang.String` que contém o nome das configurações do Adobe PDF.
   * Um objeto `ConvertPDFFormatType` que especifica o tipo de arquivo de destino para a conversão.
   * Um objeto `com.adobe.idp.Document` opcional que contém configurações a serem aplicadas durante a geração do documento PDF.

   O método `exportPDF2` retorna um objeto `ExportPDFResult` que contém o arquivo convertido.

1. Converta o documento do PDF.

   Para obter o arquivo recém-criado, execute as seguintes ações:

   * Invoque o método `getConvertedDocument` do objeto `ExportPDFResult`. Isso retorna um objeto `com.adobe.idp.Document`.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para extrair o novo documento.

**Consulte também**

[Resumo das etapas](converting-file-formats-pdf.md#summary-of-steps)

[Início rápido (modo SOAP): conversão de conteúdo HTML em um documento PDF usando a API Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Converter um documento do PDF em um arquivo RTF usando a API do serviço Web {#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api}

Converta um documento do PDF em um arquivo RTF usando a API Generate PDF (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um cliente Generate PDf.

   * Crie um objeto `GeneratePDFServiceClient` usando seu construtor padrão.
   * Crie um objeto `GeneratePDFServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. No entanto, especifique `?blob=mtom`.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `GeneratePDFServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere o documento do PDF para conversão.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar um documento PDF que é convertido.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo à propriedade `MTOM` o conteúdo da matriz de bytes.

1. Converta o documento do PDF.

   Invoque o método `ExportPDF2` do objeto `GeneratePDFServiceServiceWse` e passe os seguintes valores:

   * Um objeto `BLOB` que representa o arquivo PDF a ser convertido.
   * Uma cadeia de caracteres que contém o nome do caminho do arquivo a ser convertido.
   * Um objeto `java.lang.String` que especifica o local do arquivo.
   * Um objeto string que especifica o tipo de arquivo de destino para a conversão. Especifique `RTF`.
   * Um objeto `BLOB` opcional que contém configurações a serem aplicadas durante a geração do documento PDF.
   * Um parâmetro de saída do tipo `BLOB` preenchido pelo método `ExportPDF2`. O método `ExportPDF2` preenche este objeto com o documento convertido. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).

1. Salve o arquivo convertido.

   * Recupere o documento RTF convertido atribuindo o campo `MTOM` do objeto `BLOB` a uma matriz de bytes. A matriz de bytes representa o documento RTF convertido. Use o objeto `BLOB` que é usado como parâmetro de saída para o método `ExportPDF2`.
   * Crie um objeto `System.IO.FileStream` invocando seu construtor. Transmita um valor de string que represente o local do arquivo RTF.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo RTF invocando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](converting-file-formats-pdf.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Adição de suporte para formatos de arquivo nativos adicionais {#adding-support-for-additional-native-file-formats}

Esta seção explica como adicionar suporte para formatos de arquivo nativos adicionais. Ele fornece uma visão geral das interações entre o serviço Gerar PDF e os aplicativos nativos que esse serviço usa para converter formatos de arquivo nativos em PDF.

Esta seção também explica o seguinte:

* Como modificar a resposta que o serviço Gerar PDF fornece aos aplicativos nativos que esse produto já usa para converter formatos de arquivo nativos em PDF
* As interações entre o serviço Gerar PDF, o componente Gerar Monitor de Aplicativos de serviço PDF (AppMon) e aplicativos nativos, como o Microsoft Word
* As funções que as gramáticas XML desempenham nessas interações

### Interações de componente {#component-interactions}

O serviço Gerar PDF converte formatos de arquivo nativos, chamando o aplicativo associado ao formato de arquivo e interagindo com o aplicativo para imprimir o documento usando a impressora padrão. A impressora padrão deve ser configurada como a impressora Adobe PDF.

Esta ilustração mostra os componentes e drivers envolvidos com o suporte ao aplicativo nativo. Também menciona as gramáticas XML que influenciam as interações.

Interações de componentes para conversão de arquivo nativo

Este documento usa o termo *aplicativo nativo* para indicar o aplicativo usado para produzir um formato de arquivo nativo, como o Microsoft Word.

*AppMon* é um componente corporativo que interage com um aplicativo nativo da mesma forma que um usuário navegaria pelas caixas de diálogo apresentadas por esse aplicativo. As gramáticas XML usadas pelo AppMon para instruir um aplicativo, como o Microsoft Word, a abrir e imprimir um arquivo envolvem estas tarefas sequenciais:

1. Abrir o arquivo selecionando Arquivo > Abrir
1. Garantir que a caixa de diálogo Abrir seja exibida; caso contrário, tratar do erro
1. Fornecer o nome do arquivo no campo Nome do arquivo e clicar no botão Abrir
1. Garantir que o arquivo realmente abra
1. Abrir a caixa de diálogo Imprimir selecionando Arquivo > Imprimir
1. Verificando se a caixa de diálogo Imprimir é exibida

O AppMon usa APIs Win32 padrão para interagir com aplicativos de terceiros para transferir eventos da interface do usuário, como pressionamentos de tecla e cliques de mouse, o que é útil para controlar esses aplicativos para produzir arquivos PDF a partir deles.

Devido a uma limitação com essas APIs Win32, o AppMon não pode despachar esses eventos de interface do usuário para alguns tipos específicos de janelas, como barras de menu flutuantes (encontradas em alguns aplicativos, como TextPad), e determinados tipos de caixas de diálogo cujo conteúdo não pode ser recuperado usando as APIs Win32.

É fácil identificar visualmente uma barra de menu flutuante; no entanto, pode não ser possível identificar os tipos especiais de diálogos apenas por inspeção visual. Você precisaria de um aplicativo de terceiros, como o Microsoft Spy++ (parte do ambiente de desenvolvimento do Microsoft Visual C++) ou seu WinID equivalente (que pode ser baixado gratuitamente de [https://www.dennisbabkin.com/php/download.php?what=WinID](https://www.dennisbabkin.com/php/download.php?what=WinID)) para examinar uma caixa de diálogo para determinar se o AppMon poderia interagir com ele usando APIs Win32 padrão.

Se o WinID puder extrair o conteúdo da caixa de diálogo, como texto, subjanelas, ID de classe de janela e assim por diante, o AppMon também poderá fazer o mesmo.

Esta tabela lista o tipo de informação usada na impressão de formatos de arquivo nativos.

<table>
 <thead>
  <tr>
   <th><p>Tipo de informação</p></th>
   <th><p>Descrição</p></th>
   <th><p>Modificar/criar entradas relacionadas a arquivos nativos </p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Configurações administrativas </p></td>
   <td><p>Inclui configurações do PDF, de segurança e de tipo de arquivo. </p><p>As configurações de tipo de arquivo associam extensões de nome de arquivo aos aplicativos nativos correspondentes. As configurações de tipo de arquivo também especificam as configurações do aplicativo nativo usadas para imprimir arquivos nativos. </p></td>
   <td><p>Para alterar as configurações de um aplicativo nativo já compatível, o administrador do sistema define as Configurações de tipo de arquivo no console de administração. </p><p>Para adicionar suporte para um novo formato de arquivo nativo, você deve editar o arquivo manualmente. (Consulte <a href="converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format">Adicionando ou modificando o suporte para um formato de arquivo nativo</a>.) </p></td>
  </tr>
  <tr>
   <td><p>Script </p></td>
   <td><p>Especifica as interações entre o serviço Generate PDF e um aplicativo nativo. Essas interações geralmente direcionam o aplicativo para imprimir um arquivo no driver do Adobe PDF. </p><p>O script contém instruções que direcionam o aplicativo nativo para abrir caixas de diálogo específicas e que fornecem respostas específicas a campos e botões nessas caixas de diálogo. </p></td>
   <td><p>O serviço Gerar PDF inclui arquivos de script para todos os aplicativos nativos compatíveis. Você pode modificar esses arquivos usando um aplicativo de edição XML.</p><p>Para adicionar suporte a um novo aplicativo nativo, você deve criar um arquivo de script. (Consulte <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Criando ou modificando um arquivo XML de caixa de diálogo adicional para um aplicativo nativo</a>.) </p></td>
  </tr>
  <tr>
   <td><p>Instruções da caixa de diálogo genérica </p></td>
   <td><p>Especifica como responder a caixas de diálogo comuns a vários aplicativos. Essas caixas de diálogo são geradas por sistemas operacionais, aplicativos auxiliares (como o PDFMaker) e drivers. </p><p>O arquivo que contém essas informações é appmon.global.en_US.xml.</p></td>
   <td><p>Não modifique este arquivo. </p></td>
  </tr>
  <tr>
   <td><p>Instruções da caixa de diálogo específica do aplicativo</p></td>
   <td><p>Especifica como responder às caixas de diálogo específicas do aplicativo. </p><p>O arquivo que contém essas informações é appmon.<i>`[appname]`</i>.dialog.<i>`[locale]`</i>.xml (por exemplo, appmon.word.en_US.xml).</p></td>
   <td><p>Não modifique este arquivo. </p><p>Para adicionar instruções de caixa de diálogo para um novo aplicativo nativo, consulte <a href="converting-file-formats-pdf.md#creating_or_modifying_an_additional_dialog_xml_file_for_a_native_application">Criando ou modificando um arquivo XML de caixa de diálogo adicional para um aplicativo nativo</a>.</p></td>
  </tr>
  <tr>
   <td><p>Instruções adicionais da caixa de diálogo específica do aplicativo </p></td>
   <td><p>Especifica sobreposições e adições às instruções da caixa de diálogo específica do aplicativo. A seção apresenta um exemplo dessas informações. </p><p>O arquivo que contém essas informações é appmon.<i>`[appname]`</i>.additional.<i>`[locale]`</i>.xml. Um exemplo é appmon.adding.en_US.xml.</p></td>
   <td><p>Arquivos desse tipo podem ser criados e modificados usando um aplicativo de edição XML. (Consulte <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Criando ou modificando um arquivo XML de caixa de diálogo adicional para um aplicativo nativo</a>.) </p><p><strong>Importante</strong>: crie instruções adicionais da caixa de diálogo específica do aplicativo para cada aplicativo nativo ao qual seu servidor dará suporte. </p></td>
  </tr>
 </tbody>
</table>

### Sobre os arquivos XML de script e diálogo {#about-the-script-and-dialog-xml-files}

Os arquivos XML de script direcionam o serviço Gerar PDF para navegar pelas caixas de diálogo do aplicativo da mesma forma que um usuário navegaria pelas caixas de diálogo do aplicativo. Os arquivos XML de script também direcionam o serviço Gerar PDF para responder às caixas de diálogo, executando ações como pressionar botões, marcar ou desmarcar caixas de seleção ou selecionar itens de menu.

Por outro lado, os arquivos XML de diálogo simplesmente respondem às caixas de diálogo com os mesmos tipos de ações usadas nos arquivos XML de script.

#### Terminologia do elemento da caixa de diálogo e janela {#dialog-box-and-window-element-terminology}

Esta seção e a próxima usam terminologia diferente para caixas de diálogo e os componentes que elas contêm, dependendo da perspectiva que está sendo descrita. Os componentes da caixa de diálogo são itens como botões, campos e caixas de combinação.

Quando esta seção e a próxima descrevem caixas de diálogo e seus componentes da perspectiva de um usuário, são usados termos como *caixa de diálogo*, *botão*, *campo* e *caixa de combinação*.

Quando esta seção e a próxima descrevem caixas de diálogo e seus componentes da perspectiva de sua representação interna, o termo *elemento de janela* é usado. A representação interna de elementos de janela é uma hierarquia, onde cada instância de elemento de janela é identificada por rótulos. A ocorrência do elemento da janela também descreve suas características físicas e comportamento.

Da perspectiva de um usuário, as caixas de diálogo e seus componentes mostram comportamentos diferentes, em que alguns elementos da caixa de diálogo ficam ocultos até serem ativados. Do ponto de vista da representação interna, não existe tal questão de comportamento. Por exemplo, a representação interna de uma caixa de diálogo é semelhante àquela dos componentes que ela contém, com a exceção de que os componentes são aninhados dentro da caixa de diálogo.

Esta seção descreve elementos XML que fornecem instruções ao AppMon. Esses elementos têm nomes como o elemento `dialog` e o elemento `window`. Este documento usa uma fonte monoespaçada para distinguir elementos XML. O elemento `dialog` identifica uma caixa de diálogo que um arquivo de script XML pode fazer com que seja exibido, intencionalmente ou não. O elemento `window` identifica um elemento de janela (caixa de diálogo ou os componentes de uma caixa de diálogo).

#### Hierarquia {#hierarchy}

Este diagrama mostra a hierarquia do script e do XML de diálogo. Um arquivo XML de script está em conformidade com o esquema script.xsd, que inclui (no sentido XML) o esquema window.xsd. Da mesma forma, um arquivo XML de caixa de diálogo está em conformidade com o esquema dialogs.xsd, que também inclui o esquema window.xsd.

![as_as_xml_hierarchy](assets/as_as_xml_hierarchy.png)

Hierarquia de XML de script e caixa de diálogo

#### Arquivos XML de script {#script-xml-files}

Um *arquivo XML de script* especifica uma série de etapas que direcionam o aplicativo nativo a navegar para determinados elementos de janela e fornecer respostas a esses elementos. A maioria das respostas é texto ou pressionamentos de tecla que correspondem à entrada que um usuário forneceria a um campo, caixa de combinação ou botão na caixa de diálogo correspondente.

O propósito do suporte do serviço Gerar PDF para arquivos XML de script é direcionar um aplicativo nativo para imprimir um arquivo nativo. No entanto, os arquivos XML de script podem ser usados para realizar qualquer tarefa que um usuário possa executar ao interagir com as caixas de diálogo do aplicativo nativo.

As etapas em um arquivo XML de script são executadas em ordem, sem nenhuma oportunidade de ramificação. O único teste condicional compatível é para tempo limite/nova tentativa, o que faz com que um script seja encerrado se uma etapa não for concluída com êxito em um período específico e após um número específico de tentativas.

Além das etapas serem sequenciais, as instruções em uma etapa também são executadas em ordem. Verifique se as etapas e instruções refletem a ordem em que um usuário executaria essas mesmas etapas.

Cada etapa em um arquivo XML de script identifica o elemento da janela que deve aparecer se as instruções da etapa forem executadas com êxito. Se uma caixa de diálogo inesperada for exibida durante a execução de uma etapa de script, o serviço Gerar PDF pesquisará os arquivos XML da caixa de diálogo, conforme descrito na próxima seção.

#### Arquivos XML de diálogo {#dialog-xml-files}

A execução de aplicativos nativos exibe diferentes caixas de diálogo, que são exibidas independentemente de os aplicativos nativos estarem em um modo visível ou invisível. As caixas de diálogo podem ser geradas pelo sistema operacional ou pelo próprio aplicativo. Quando aplicativos nativos estão sendo executados sob o controle do serviço Gerar PDF, as caixas de diálogo do sistema e do aplicativo nativo são exibidas em uma janela invisível.

Um *arquivo XML de caixa de diálogo* especifica como o serviço Generate PDF responde às caixas de diálogo do sistema ou do aplicativo nativo. Os arquivos XML da caixa de diálogo permitem que o serviço Gerar PDF responda a caixas de diálogo não solicitadas de uma forma que facilite o processo de conversão.

Quando o sistema ou aplicativo nativo exibe uma caixa de diálogo que não é manipulada pelo arquivo XML de script em execução no momento, o serviço Gerar PDF pesquisa os arquivos XML da caixa de diálogo nesta ordem, parando quando encontra uma correspondência:

* appmon.`[appname]`.adicional.`[locale]`.xml
* appmon.`[appname]`.`[locale]`.xml (Não modifique este arquivo.)
* appmon.global.`[locale]`.xml (Não modifique este arquivo.)

Se o serviço Gerar PDF encontrar uma correspondência para a caixa de diálogo, ele a descartará enviando o pressionamento de tecla ou outra ação especificada para a caixa de diálogo. Se as instruções da caixa de diálogo especificarem uma mensagem de interrupção, o serviço Gerar PDF encerrará o job em execução no momento e gerará uma mensagem de erro. A mensagem de anulação seria especificada no elemento `abortMessage` da gramática XML do script.

Se o serviço Gerar PDF encontrar uma caixa de diálogo que não esteja descrita em nenhum dos arquivos listados anteriormente, o serviço Gerar PDF incorporará a legenda da caixa de diálogo à entrada do arquivo de log. O trabalho em execução no momento acaba expirando. Em seguida, você pode usar as informações no arquivo de log para compor novas instruções no arquivo XML da caixa de diálogo adicional do aplicativo nativo.

### Adição ou modificação de suporte para um formato de arquivo nativo {#adding-or-modifying-support-for-a-native-file-format}

Esta seção descreve as tarefas que você deve executar para suportar outros formatos de arquivo nativos ou para modificar o suporte para um formato de arquivo nativo já suportado.

Antes de adicionar ou modificar o suporte, você deve concluir as tarefas a seguir.

#### Escolhendo uma ferramenta para identificar elementos de janela {#choosing-a-tool-for-identifying-window-elements}

Os arquivos XML de diálogo e script exigem que você identifique o elemento da janela (caixa de diálogo, campo ou outro componente de diálogo) ao qual o elemento de diálogo ou script está respondendo. Por exemplo, depois que um script chama um menu de um aplicativo nativo, o script deve identificar o elemento da janela nesse menu ao qual os pressionamentos de tecla ou uma ação devem ser aplicados.

É possível identificar facilmente uma caixa de diálogo pela legenda exibida na barra de título. No entanto, você deve usar uma ferramenta como o Microsoft Spy++ para identificar elementos de janela de nível inferior. Os elementos de janela de nível inferior podem ser identificados por meio de uma variedade de atributos, que não são óbvios. Além disso, cada aplicativo nativo pode identificar seu elemento de janela de forma diferente. Como resultado, há várias maneiras de identificar um elemento de janela. Esta é a ordem sugerida para considerar a identificação do elemento da janela:

1. Legenda propriamente dita, se for exclusiva
1. ID de controle, que pode ou não ser exclusiva para uma determinada caixa de diálogo
1. Nome da classe, que pode ou não ser exclusivo

Qualquer um ou uma combinação desses três atributos pode ser usada para identificar uma janela.

Se os atributos não identificarem uma legenda, você poderá identificar um elemento de janela usando seu índice em relação ao pai. Um *index* especifica a posição do elemento window em relação aos seus elementos window irmãos. Frequentemente, os índices são a única maneira de identificar caixas de combinação.

Esteja ciente destes problemas:

* O Microsoft Spy++ exibe legendas usando um E comercial (&amp;) para identificar a tecla de acesso da legenda. Por exemplo, Spy++ mostra a legenda de uma caixa de diálogo Imprimir como `Pri&nt`, o que indica que a tecla de atalho é *n*. Os títulos de legenda nos arquivos XML de script e diálogo devem omitir &quot;E&quot; comercial (&amp;).
* Algumas legendas incluem quebras de linha. o serviço Gerar PDF não pode identificar quebras de linha. Se uma legenda incluir uma quebra de linha, inclua uma quantidade suficiente da legenda para diferenciá-la dos outros itens de menu e, em seguida, use expressões regulares para a parte omitida. Um exemplo é ( `^Long caption title$`). (Consulte [Usar expressões regulares em atributos de legenda](converting-file-formats-pdf.md#using-regular-expressions-in-caption-attributes).)
* Use entidades de caractere (também chamadas de sequências de escape) para caracteres XML reservados. Por exemplo, use `&` para &quot;E&quot; comercial, `<` e `>` para símbolos menor que e maior que, `&apos;` para apóstrofos e `&quot;` para aspas.

Se você planeja trabalhar em arquivos XML de diálogo ou script, deve instalar o aplicativo Microsoft Spy++.

#### Desempacotamento dos arquivos de diálogo e script {#unpackaging-the-dialog-and-script-files}

Os arquivos de diálogo e script residem no arquivo appmondata.jar. Antes de modificar qualquer um desses arquivos ou adicionar novos arquivos de script ou de diálogo, você deve desempacotar esse arquivo JAR. Por exemplo, suponha que você deseja adicionar suporte para o aplicativo EditPlus. Você cria dois arquivos XML, chamados appmon.editplus.script.en_US.xml e appmon.editplus.script.adding.en_US.xml. Esses scripts XML devem ser adicionados ao arquivo adobe-appmondata.jar em dois locais, conforme especificado abaixo:

* adobe-livecycle-native-jboss-x86_win32.ear > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar\com\adobe\appmon. O arquivo adobe-livecycle-native-jboss-x86_win32.ear está na pasta de exportação em `[AEM forms install directory]\configurationManager`. (se o AEM Forms for implantado em outro servidor de aplicativos J2EE, substitua o arquivo adobe-livecycle-native-jboss-x86_win32.ear pelo arquivo EAR que corresponde ao seu servidor de aplicativos J2EE.)
* adobe-generatepdf-dsc.jar > adobe-appmondata.jar\com\adobe\appmon (o arquivo adobe-appmondata.jar está no arquivo adobe-generatepdf-dsc.jar). O arquivo adobe-generatepdf-dsc.jar está na pasta `[AEM forms install directory]\deploy`.

Depois de adicionar esses arquivos XML ao arquivo adobe-appmondata.jar, você deve reimplantar o componente GeneratePDF. Para adicionar arquivos XML de diálogo e script ao arquivo adobe-appmondata.jar, execute estas tarefas:

1. Usando uma ferramenta como WinZip ou WinRAR, abra o arquivo adobe-livecycle-native-jboss-x86_win32.earfile > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > arquivo adobe-appmondata.jar.
1. Adicione os arquivos XML de diálogo e script ao arquivo appmondata.jar ou modifique arquivos XML existentes nesse arquivo. (Consulte [Criando ou modificando um arquivo XML de script para um aplicativo nativo](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)e [Criando ou modificando um arquivo XML de caixa de diálogo adicional para um aplicativo nativo](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).)
1. Usando uma ferramenta como WinZip ou WinRAR, abra adobe-generatepdf-dsc.jar > adobe-appmondata.jar.
1. Adicione os arquivos XML de diálogo e script ao arquivo appmondata.jar ou modifique arquivos XML existentes nesse arquivo. (Consulte [Criação ou modificação de um arquivo XML de script para um aplicativo nativo](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)e [Criação ou modificação de um arquivo XML de caixa de diálogo adicional para um aplicativo nativo](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).) Depois de adicionar os arquivos XML ao arquivo adobe-appmondata.jar, coloque o novo arquivo adobe-appmondata.jar no arquivo adobe-generatepdf-dsc.jar.
1. Se você tiver adicionado suporte para um formato de arquivo nativo adicional, crie uma variável de ambiente do sistema que forneça o caminho do aplicativo (Consulte [Criação de uma variável de ambiente para localizar o aplicativo nativo](converting-file-formats-pdf.md#creating-an-environment-variable-to-locate-the-native-application).)

**Para reimplantar o componente GeneratePDF**

1. Faça logon no Workbench.
1. Selecione **Janela** > **Mostrar Exibições** > **Componentes**. Esta ação adiciona a exibição Componentes à Bancada.
1. Clique com o botão direito no componente GeneratePDF e selecione **Parar Componente**.
1. Quando o componente for interrompido, clique com o botão direito do mouse e selecione Desinstalar componente para removê-lo.
1. Clique com o botão direito do mouse no ícone **Componentes** e selecione **Instalar Componente**.
1. Procure e selecione o arquivo adobe-generatepdf-dsc.jar modificado e clique em Abrir. Observe que um quadrado vermelho aparece ao lado do componente GeneratePDF.
1. Expanda o componente GeneratePDF, selecione Descritores de serviço, clique com o botão direito do mouse em GeneratePDFService e selecione Ativar serviço.
1. Na caixa de diálogo de configuração exibida, digite os valores de configuração aplicáveis. Se você deixar esses valores em branco, serão usados os valores de configuração padrão.
1. Clique com o botão direito do mouse em GeneratePDF e selecione Iniciar componente.
1. Expanda Serviços Ativos. Uma seta verde é exibida ao lado do nome do serviço, se ele estiver em execução. Caso contrário, o serviço estará em um estado interrompido.
1. Se o serviço estiver em um estado interrompido, clique com o botão direito do mouse no nome do serviço e selecione Iniciar serviço.

### Criando ou modificando um arquivo XML de script para uma aplicação nativa {#creating-or-modifying-a-script-xml-file-for-a-native-application}

Se quiser direcionar arquivos para um novo aplicativo nativo, você deverá criar um arquivo XML de script para esse aplicativo. Se quiser modificar como o serviço Gerar PDF interage com um aplicativo nativo já suportado, você deverá modificar o script desse aplicativo.

O script contém instruções que navegam pelos elementos de janela do aplicativo nativo e fornecem respostas específicas a esses elementos. O arquivo que contém essas informações é `appmon.`[appname]&quot;`.script.`[locale]`.xml`. Um exemplo é appmon.notepad.script.en_US.xml.

#### Identificando etapas que o script deve executar {#identifying-steps-the-script-must-execute}

Usando o aplicativo nativo, determine os elementos de janela que você deve navegar e cada resposta que deve ser executada para imprimir o documento. Observe as caixas de diálogo que resultam de qualquer resposta. As etapas serão semelhantes às seguintes:

1. Selecione Arquivo > Abrir.
1. Especifique o caminho e clique em Abrir.
1. Selecione Arquivo > Imprimir na barra de menus.
1. Especifique as propriedades necessárias para a impressora.
1. Selecione Imprimir e aguarde até que a caixa de diálogo Salvar como seja exibida. A caixa de diálogo Salvar como é necessária para que o serviço Gerar PDF especifique o destino do arquivo PDF.

#### Identificação das caixas de diálogo especificadas nos atributos de legenda {#identifying-the-dialogs-specified-in-caption-attributes}

Use o Microsoft Spy++ para obter as identidades das propriedades do elemento de janela no aplicativo nativo. Você deve ter essas identidades para gravar scripts.

#### Uso de expressões regulares em atributos de legenda {#using-regular-expressions-in-caption-attributes}

Você pode usar expressões regulares em especificações de legenda. O serviço de Geração de PDF usa a classe `java.util.regex.Matcher` para oferecer suporte a expressões regulares. Esse utilitário suporta as expressões regulares descritas em `java.util.regex.Pattern`.

**Expressão regular que acomoda o nome de arquivo anexado ao Bloco de Notas no banner do Bloco de Notas**

```xml
 <!-- The regular expression ".*Notepad" means any number of non-terminating characters followed by Notepad. -->
 <step>
     <expectedWindow>
         <window caption=".*Notepad"/>
     </expectedWindow>
 </step>
```

**Expressão regular que diferencia Impressão da Configuração de Impressão**

```xml
 <!-- This regular expression differentiates the Print dialog box from the Print Setup dialog box. The "^" specifies the beginning of the line, and the "$" specifies the end of the line. -->
 <windowList>
     <window controlID="0x01" caption="^Print$" action="press"/>
 </windowList>
```

#### Ordenação dos elementos window e windowList {#ordering-the-window-and-windowlist-elements}

Ordenar elementos `window` e `windowList` da seguinte maneira:

* Quando vários elementos `window` forem exibidos como filhos em um elemento `windowList` ou `dialog`, ordene esses elementos `window` em ordem decrescente, com os comprimentos dos nomes `caption` indicando a posição na ordem.
* Quando vários elementos `windowList` aparecerem em um elemento `window`, ordene esses elementos `windowList` em ordem decrescente, com os comprimentos dos atributos `caption` do primeiro elemento `indexes/` indicando a posição na ordem.

**Ordenando elementos da janela em um arquivo de diálogo**

```xml
 <!-- The caption attribute in the following window element is 40 characters long. It is the longest caption in this example, so its parent window element appears before the others. -->
 <window caption="Unexpected Failure in DebugActiveProcess">
     <…>
 </window>

 <!-- Caption length is 33 characters. -->
 <window caption="Adobe Acrobat - License Agreement">
     <…>
 </window>

 <!-- Caption length is 33 characters. -->
 <window caption="Microsoft Visual.*Runtime Library">
     <…>
 </window>

 <!-- The caption attribute in the following window element is 28 characters long. It is the shortest caption in this example, so its parent window element appears after the others. -->
 <window caption="Adobe Acrobat - Registration">
     <…>
 </window>
```

**Ordenando elementos de janela dentro de um elemento windowList**

```xml
 <!-- The caption attribute in the following indexes element is 56 characters long. It is the longest caption in this example, so its parent window element appears before the others. -->
 <windowList>
     <window caption="Can&apos;t exit design mode because.* cannot be created"/>
     <window className="Button" caption="OK" action="press"/>
 </windowList>
 <windowList>
     <window caption="Do you want to continue loading the project?"/>
     <window className="Button" caption="No" action="press"/>
 </windowList>
 <windowList>
     <window caption="The macros in this project are disabled"/>
     <window className="Button" caption="OK" action="press"/>
 </windowList>
```

### Criando ou modificando um arquivo XML de diálogo adicional para um aplicativo nativo {#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application}

Se você criar um script para um aplicativo nativo que não era suportado anteriormente, deverá criar também um arquivo XML de diálogo adicional para esse aplicativo. Cada aplicativo nativo que o AppMon usa deve ter apenas um arquivo XML de diálogo adicional. O arquivo XML de diálogo adicional é necessário mesmo se nenhuma caixa de diálogo não solicitada for esperada. A caixa de diálogo adicional deve ter pelo menos um elemento `window`, mesmo que esse elemento `window` seja apenas um espaço reservado.

>[!NOTE]
>
>Neste contexto, o termo adicional significa o conteúdo do arquivo `appmon.[applicationname].addition.[locale].xml`. Esse arquivo especifica substituições e adições ao arquivo XML da caixa de diálogo.

Também é possível modificar o arquivo XML da caixa de diálogo adicional para um aplicativo nativo com estas finalidades:

* Para substituir o arquivo XML da caixa de diálogo de um aplicativo com uma resposta diferente
* Para adicionar uma resposta a uma caixa de diálogo que não esteja endereçada no arquivo XML da caixa de diálogo desse aplicativo

O nome de arquivo que identifica um arquivo adicional dialogXML é `appmon.[appname].addition.[locale].xml`. Um exemplo é appmon.excel.addition.en_US.xml.

O nome do arquivo XML de caixa de diálogo adicional deve usar o formato `appmon.[applicationname].addition.[locale].xml`, em que *applicationname* deve corresponder exatamente ao nome do aplicativo usado no arquivo de configuração XML e no script.

>[!NOTE]
>
>Nenhum dos aplicativos genéricos especificados no arquivo de configuração native2pdfconfig.xml tem um arquivo XML primário de diálogo. A seção [Adicionando ou modificando o suporte para um formato de arquivo nativo](converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format) descreve essas especificações.

Ordenar elementos `windowList` que aparecem como filhos em um elemento `window`. (Consulte [Ordenação dos elementos window e windowList](converting-file-formats-pdf.md#ordering-the-window-and-windowlist-elements).)

### Modificando o arquivo XML da caixa de diálogo geral {#modifying-the-general-dialog-xml-file}

Você pode modificar o arquivo XML da caixa de diálogo geral para responder às caixas de diálogo geradas pelo sistema ou para responder às caixas de diálogo comuns a vários aplicativos.

#### Adicionando uma entrada de tipo de arquivo no arquivo de configuração XML {#adding-a-filetype-entry-in-the-xml-configuration-file}

Este procedimento explica como atualizar o arquivo de configuração do serviço Gerar PDF para associar tipos de arquivos a aplicativos nativos. Para atualizar esse arquivo de configuração, você deve usar o console de administração para exportar os dados de configuração para um arquivo. O nome de arquivo padrão para os dados de configuração é native2pdfconfig.xml.

**Atualizar o arquivo de configuração de serviço Gerar PDF**

1. Selecione **Página Inicial** > **Serviços** > **Adobe PDF Generator** > **Arquivos de Configuração** e selecione **Exportar Configuração**.
1. Modifique o elemento `filetype-settings` no arquivo native2pdfconfig.xml, conforme necessário.
1. Selecione **Início** > **Serviços** > **Gerador de Adobe PDF** >**Arquivos de Configuração** e selecione **Importar Configuração**. Os dados de configuração são importados para o serviço Gerar PDF, substituindo as configurações anteriores.

>[!NOTE]
>
>O nome do aplicativo é especificado como o valor do atributo `name` do elemento `GenericApp`. Esse valor deve corresponder exatamente ao nome especificado no script desenvolvido para esse aplicativo. Da mesma forma, o atributo `displayName` do elemento `GenericApp` deve corresponder exatamente à legenda de janela `expectedWindow` do script correspondente. Essa equivalência é avaliada após a resolução de quaisquer expressões regulares que apareçam nos atributos `displayName` ou `caption`.

Neste exemplo, os dados de configuração padrão fornecidos com o serviço Gerar PDF foram modificados para especificar que o Notepad (não o Microsoft Word) deve ser usado para processar arquivos com a extensão de nome de arquivo .txt. Antes dessa modificação, o Microsoft Word era especificado como o aplicativo nativo que deveria processar esses arquivos.

**Modificações para direcionar arquivos de texto para o Bloco de Notas (native2pdfconfig.xml)**

```xml
 <filetype-settings>

 <!-- Some native app file types were omitted for brevity. -->
 <!-- The following GenericApp element specifies Notepad as the native application that should be used to process files that have a txt file name extension. -->
             <GenericApp
                 extensions="txt"
                 name="Notepad" displayName=".*Notepad"/>
             <GenericApp
                 extensions="wpd"
                 name="WordPerfect" displayName="Corel WordPerfect"/>
             <GenericApp extensions="pmd,pm6,p65,pm"
                 name="PageMaker" displayName="Adobe PageMaker"/>
             <GenericApp extensions="fm"
                 name="FrameMaker" displayName="Adobe FrameMaker"/>
             <GenericApp extensions="psd"
                 name="Photoshop" displayName="Adobe Photoshop"/>
         </settings>
     </filetype-settings>
```

#### Criação de uma variável de ambiente para localizar o aplicativo nativo {#creating-an-environment-variable-to-locate-the-native-application}

Crie uma variável de ambiente que especifique o local do executável do aplicativo nativo. A variável deve usar o formato `[applicationname]_PATH`, onde *applicationname* deve corresponder exatamente ao nome do aplicativo usado no arquivo de configuração XML e no script, e onde o caminho contém o caminho para o executável entre aspas duplas. Um exemplo dessa variável de ambiente é `Photoshop_PATH`.

Depois de criar a nova variável de ambiente, você deve reiniciar o servidor no qual o serviço Gerar PDF está implantado.

>[!NOTE]
>
> É recomendável usar o comando &#39;Ctrl + C&#39; para reiniciar o servidor do SDK. Reiniciar o servidor do AEM SDK usando métodos alternativos, por exemplo, parar processos Java, pode levar a inconsistências no ambiente de desenvolvimento do AEM.

**Criar uma variável do sistema no ambiente do Windows XP**

1. Selecione **Painel de Controle > Sistema**.
1. Na caixa de diálogo Propriedades do Sistema, clique na guia **Avançado** e em **Variáveis de Ambiente**.
1. Em Variáveis de Sistema, na caixa de diálogo Variáveis de Ambiente, clique em **Novo**.
1. Na caixa de diálogo Nova Variável de Sistema, na caixa **Nome da variável**, digite um nome que use o formato `[applicationname]_PATH`.
1. Na caixa **Valor da variável**, digite o caminho completo e o nome do arquivo executável do aplicativo e clique em **OK**. Por exemplo, digite: `c:\windows\Notepad.exe`
1. Na caixa de diálogo Variáveis de Ambiente, clique em **OK**.

**Criar uma variável de sistema a partir da linha de comando**

1. Em uma janela de linha de comando, digite a definição da variável, usando este formato:

   ```shell
            [applicationname]_PATH=[Full path name]
   ```

   Por exemplo, digite: `NotePad_PATH=C:\WINDOWS\NOTEPAD.EXE`

1. Inicie um novo prompt de linha de comando para que a variável de sistema entre em vigor.

#### Arquivos XML {#xml-files}

O AEM Forms inclui arquivos XML de exemplo que fazem com que o serviço Gerar PDF use o Notepad para processar quaisquer arquivos com a extensão de nome de arquivo .txt. Esse código está incluído nesta seção. Além disso, você deve fazer as outras modificações descritas nesta seção.

#### Arquivo XML de diálogo adicional {#additional-dialog-xml-file}

Este exemplo contém as caixas de diálogo adicionais para o aplicativo Bloco de notas. Essas caixas de diálogo podem ser adicionadas às especificadas pelo serviço Gerar PDF.

**Caixas de diálogo do Bloco de Notas(appmon.notepad.additional.en_US.xml)**

```xml
 <dialogs app="Notepad" locale="en_US" version="7.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="dialogs.xsd">
     <window caption="Caption Title">
         <windowList>
             <window className="Button" caption="OK" action="press"/>
         </windowList>
     </window>
 </dialogs>
```

#### Arquivo XML de script {#script-xml-file}

Este exemplo especifica como o serviço Gerar PDF deve interagir com o Bloco de notas para imprimir arquivos usando a impressora Adobe PDF.

**Arquivo XML de script do Bloco de Notas (appmon.notepad.script.en_US.xml)**

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!--
*
* ADOBE CONFIDENTIAL
* ___________________
* Copyright 2004 - 2005 Adobe Systems Incorporated
* All Rights Reserved.
*
* NOTICE:  All information contained herein is, and remains
* the property of Adobe Systems Incorporated and its suppliers,
* if any.  The intellectual and technical concepts contained
* herein are proprietary to Adobe Systems Incorporated and its
* suppliers and may be covered by U.S. and Foreign Patents,
* patents in process, and are protected by trade secret or copyright law.
* Dissemination of this information or reproduction of this material
* is strictly forbidden unless prior written permission is obtained
* from Adobe Systems Incorporated.
*-->

<!-- This file automates printing of text files via notepad to Adobe PDF printer. To see the complete hierarchy Adobe recommends using the Microsoft Spy++ which details the properties of windows necessary to write scripts. In this sample there are total of eight steps-->

<application name="Notepad" version="9.0" locale="en_US" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="scripts.xsd">

    <!-- In this step we wait for the application window to appear -->
    <step>
        <expectedWindow>
            <window caption=".*Notepad"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the application window and send File->Open menu bar, menu item commands and the expectation is the windows Open dialog-->
    <step>
        <acquiredWindow>
            <window caption=".*Notepad">
                <virtualInput>
                    <menuBar>
                        <selection>
                            <name>File</name>
                        </selection>
                        <selection>
                            <name>Open...</name>
                        </selection>
                    </menuBar>
                </virtualInput>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Open"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the Open window and then select the 'Edit' widget and input the source path followed by clicking on the 'Open' button . The expectation of this 'action' is that the Open dialog will disappear -->
    <step>
        <acquiredWindow>
            <window caption="Open">
                <windowList>
                    <window className="ComboBoxEx32">
                        <windowList>
                            <window className="ComboBox">
                                <windowList>
                                <window className="Edit" action="inputSourcePath"/>
                                </windowList>
                            </window>
                        </windowList>
                    </window>
                </windowList>
                <windowList>
                    <window className="Button" caption="Open" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Open" action="disappear"/>
        </expectedWindow>
        <pause value="30"/>
    </step>

    <!-- In this step, we acquire the application window and send File->Print menu bar, menu item commands and the expectation is the windows Print dialog-->
    <step>
        <acquiredWindow>
            <window caption=".*Notepad">
                <virtualInput>
                    <menuBar>
                        <selection>
                            <name>File</name>
                        </selection>
                        <selection>
                            <name>Print...</name>
                        </selection>
                    </menuBar>
                </virtualInput>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Print">
        </window>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the Print dialog and click the 'Preferences' button and the expected window in this case is the dialog with the caption '"Printing Preferences' -->
    <step>
        <acquiredWindow>
            <window caption="Print">
                <windowList>
                    <window caption="General">
                        <windowList>
                            <window className="Button" caption="Preferences" action="press"/>
                        </windowList>
                    </window>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Printing Preferences"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the dialog "Printing Preferences' and select the combo box which is the 10th child of window with caption '"Adobe PDF Settings' and select the first index. (Note: All indeces start with 0.) Besides this we uncheck the box which has the caption '"View Adobe PDF results' and we click the button OK. The expectation is that 'Printing Preferences' dialog disappears. -->
    <step>
        <acquiredWindow>
            <window caption="Printing Preferences">
                <windowList>
                    <window caption="Adobe PDF Settings">
                        <windowList>
                            <window className="Button" caption="View Adobe PDF results" action="uncheck"/>
                        </windowList>
                        <windowList>
                            <window className="Button" caption="Ask to Replace existing PDF file" action="uncheck"/>
                        </windowList>
                    </window>
                </windowList>
                <windowList>
                    <window className="Button" caption="OK" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Printing Preferences" action="disappear"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the 'Print' dialog and click the Print button. The expectation is that the dialog with caption 'Print' disappears. In this case we use the regular expression '^Print$' for specifying the caption given there could be multiple dialogs with caption that includes the word Print. -->
    <step>
        <acquiredWindow>
            <window caption="Print">
                <windowList>
                    <window caption="General"/>
                    <window className="Button" caption="^Print$" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Print" action="disappear"/>
        </expectedWindow>
    </step>
    <step>
        <expectedWindow>
            <window caption="Save PDF File As"/>
        </expectedWindow>
    </step>
    <!-- Finally in this step, we acquire the dialog with caption "Save PDF File As" and in the Edit widget type the destination path for the output PDF file and click the Save button. The expectation is that the dialog disappears-->
    <step>
        <acquiredWindow>
            <window caption="Save PDF File As">
                <windowList>
                    <window className="Edit" action="inputDestinationPath"/>
                </windowList>
                <windowList>
                    <window className="Button" caption="Save" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Save PDF File As" action="disappear"/>
        </expectedWindow>
    </step>

    <!-- We can always set a retry count or a maximum time for a step. In case we surpass these limitations, PDF Generator generates this abort message and terminates processing. -->
    <abortMessage msg="15078"/>
</application>
```
