---
title: Trabalhar com documentos do PDF/A
description: Use o serviço DocConverter para determinar se um documento do PDF é um documento PDF/A e converter documentos do PDF em documentos PDF/A.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '2331'
ht-degree: 1%

---

# Trabalhar com documentos do PDF/A {#working-with-pdf-a-documents}

**Sobre o Serviço DocConverter**

O serviço DocConverter pode converter documentos do PDF em documentos PDA/A. Você pode realizar estas tarefas usando este serviço:

* Converter documentos do PDF em documentos do PDF/A. (Consulte [Conversão de documentos em documentos do PDF/A](pdf-a-documents.md#converting-documents-to-pdf-a-documents).)
* Determine se os documentos do PDF são documentos PDF/A. (Consulte [Determinação Programática Da Conformidade Com O PDF/A](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

>[!NOTE]
>
>Para obter mais informações sobre o serviço DocConverter, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Conversão de documentos em documentos do PDF/A {#converting-documents-to-pdf-a-documents}

Você pode usar o serviço DocConverter para converter um documento do PDF em um documento do PDF/A. Como o PDF/A é um formato de arquivamento para preservação de longo prazo do conteúdo do documento, todas as fontes são incorporadas e o arquivo é descompactado. Como resultado, um documento PDF/A geralmente é maior do que um documento PDF padrão. Além disso, um documento PDF/A não tem conteúdo de áudio e vídeo. Antes de converter um documento do PDF em um documento do PDF PDF/A, verifique se esse não é um documento do PDF/A.

A especificação PDF/A-1 consiste em dois níveis de conformidade, A e B. A principal diferença entre os dois diz respeito ao suporte de estrutura lógica (acessibilidade), que não é necessário para o nível de conformidade B. Independentemente do nível de conformidade, o PDF/A-1 determina que todas as fontes sejam incorporadas no documento PDF/A gerado. No momento, somente o PDF/A-1b é compatível com a validação (e conversão).

Embora o PDF/A seja o padrão para arquivamento de documentos do PDF, não é obrigatório que o PDF/A seja usado para arquivamento se um documento padrão do PDF atender aos requisitos da sua empresa. O objetivo do padrão PDF/A é estabelecer um arquivo PDF destinado a necessidades de arquivamento de longo prazo e preservação de documentos.

>[!NOTE]
>
>Para obter mais informações sobre o serviço DocConverter, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary-of-steps}

Para converter um documento do PDF em um documento do PDF/A, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Criar um cliente DocConvert
1. Referencie um documento do PDF para converter em um documento do PDF/A.
1. Definir informações de rastreamento.
1. Converta o documento.
1. Salve o documento do PDF/A.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (necessário se o AEM Forms for implantado no JBoss Application Server)
* jbossall-client.jar (necessário se o AEM Forms for implantado no JBoss Application Server)

Para obter informações sobre a localização desses arquivos JAR, consulte [Incluindo arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Criar um cliente DocConvert**

Antes de executar programaticamente uma operação DocConverter, você deve criar um cliente DocConverter. Se você estiver usando a API Java, crie um objeto `DocConverterServiceClient`. Se você estiver usando a API do serviço Web DocConverter, crie um objeto `DocConverterServiceService`.

**Referencie um documento PDF para converter em um documento PDF/A**

Recupere um documento PDF para converter em um documento PDF/A. Se você tentar converter um documento do PDF, como um formulário do Acrobat, em um documento do PDF/A, causará uma exceção.

**Definir informações de rastreamento**

Você pode definir uma opção de tempo de execução que determine quantas informações são rastreadas durante o processo de conversão. Ou seja, você pode definir nove níveis diferentes que especificam quantas informações o serviço DocConverter rastreia quando converte um documento PDF em um documento PDF/A.

**Converter o documento**

Depois de criar o cliente de serviço DocConverter, consulte o documento PDF para conversão e defina a opção de tempo de execução que especifica quantas informações são rastreadas, você pode converter o documento PDF em um documento PDF/A.

**Salvar o documento do PDF/A**

Você pode salvar o documento PDF/A como um arquivo PDF.

**Consulte também**

[Converter documentos em documentos do PDF/A usando a API Java](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-java-api)

[Converter documentos em documentos do PDF/A usando a API do serviço Web](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Determinação programática da conformidade com o PDF/A](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy)

### Converter documentos em documentos do PDF/A usando a API Java {#convert-documents-to-pdf-a-documents-using-the-java-api}

Converta um documento PDF em um documento PDF/A usando a API Java:

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente, como adobe-docconverter-client.jar, no caminho de classe do projeto Java.

1. Criar um cliente DocConvert

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `DocConverterServiceClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Referencie um documento do PDF para converter em um documento do PDF/A

   * Crie um objeto `java.io.FileInputStream` que represente o documento PDF a ser convertido usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo PDF.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Definir informações de rastreamento

   * Crie um objeto `PDFAConversionOptionSpec` usando seu construtor.
   * Defina o nível de rastreamento de informações invocando o método `setLogLevel` do objeto `PDFAConversionOptionSpec` e transmitindo um valor de cadeia de caracteres que especifica o nível de rastreamento. Por exemplo, passe o valor `FINE`. Para obter informações sobre os diferentes valores, consulte o método `setLogLevel` na [Referência da API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Converter o documento

   Converta o documento PDF em um documento PDF/A invocando o método `toPDFA` do objeto `DocConverterServiceClient` e transmitindo os seguintes valores:

   * O objeto `com.adobe.idp.Document` que contém o documento PDF a ser convertido
   * O objeto `PDFAConversionOptionSpec` que especifica informações de rastreamento

   O método `toPDFA` retorna um objeto `PDFAConversionResult` que contém o documento PDF/A.

1. Salve o documento do PDF/A

   * Recupere o documento PDF/A invocando o método `getPDFA` do objeto `PDFAConversionResult`. Este método retorna um objeto `com.adobe.idp.Document` que representa o documento PDF/A.
   * Crie um objeto `java.io.File` que represente o arquivo PDF/A. Verifique se a extensão do nome do arquivo é .pdf.
   * Preencha o arquivo com dados PDF/A invocando o método `copyToFile` do objeto `com.adobe.idp.Document` e transmitindo o objeto `java.io.File`.

**Consulte também**

[Trabalhar com documentos do PDF/A](pdf-a-documents.md#working-with-pdf-a-documents)

[Início rápido (modo SOAP): conversão de um documento em um documento PDF/A usando a API Java](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Converter documentos em documentos do PDF/A usando a API do serviço Web {#convert-documents-to-pdf-a-documents-using-the-web-service-api}

Converta um documento do PDF em um documento do PDF/A usando a API DocConverter (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly cliente Microsoft .NET que consuma o WSDL DocConverter.
   * Referencie o assembly do cliente Microsoft .NET.

1. Criar um cliente DocConvert

   * Usando o assembly do cliente Microsoft .NET, crie um objeto `DocConverterServiceService` invocando seu construtor padrão.
   * Defina o membro de dados `Credentials` do objeto `DocConverterServiceService` com um valor `System.Net.NetworkCredential` que especifique o nome de usuário e o valor da senha.

1. Referencie um documento do PDF para converter em um documento do PDF/A

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar o documento PDF que é convertido em um documento PDF/A.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF e o modo em que o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com os dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `binaryData` com o conteúdo da matriz de bytes.

1. Definir informações de rastreamento

   * Crie um objeto `PDFAConversionOptionSpec` usando seu construtor.
   * Defina o nível de rastreamento de informações atribuindo um valor que especifique o nível de rastreamento ao membro de dados `logLevel` do objeto `PDFAConversionOptionSpec`. Por exemplo, atribua o valor `FINE` a esse membro de dados.

1. Converter o documento

   Converta o documento PDF em um documento PDF/A invocando o método `toPDFA` do objeto `DocConverterServiceService` e transmitindo os seguintes valores:

   * O objeto `BLOB` que contém o documento PDF a ser convertido
   * O objeto `PDFAConversionOptionSpec` que especifica informações de rastreamento

   O método `toPDFA` retorna um objeto `PDFAConversionResult` que contém o documento PDF/A.

1. Salve o documento do PDF/A

   * Crie um objeto `BLOB` que armazene o documento PDF/A obtendo o valor do membro de dados `PDFADocument` do objeto `PDFAConversionResult`.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `BLOB` que foi retornado usando o objeto `PDFAConversionResult`. Popular a matriz de bytes obtendo o valor do membro de dados `binaryData` do objeto `BLOB`.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF/A.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Trabalhar com documentos do PDF/A](pdf-a-documents.md#working-with-pdf-a-documents)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Criando um assembly de cliente .NET que usa codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Determinação programática da conformidade com o PDF/A {#programmatically-determining-pdf-a-compliancy}

Você pode usar o serviço DocConverter para determinar se um documento do PDF é compatível com o PDF/A. Para obter informações sobre um documento PDF/A e como converter um documento PDF em um documento PDF/A, consulte [Conversão de documentos em documentos PDF/A](pdf-a-documents.md#converting-documents-to-pdf-a-documents).

>[!NOTE]
>
>Para obter mais informações sobre o serviço DocConverter, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-1}

Para determinar a conformidade com o PDF/A, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Criar um cliente DocConvert
1. Consulte um documento do PDF usado para determinar a conformidade com o PDF/A.
1. Definir opções de tempo de execução.
1. Recupere informações sobre o documento do PDF.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (necessário se o AEM Forms for implantado no JBoss Application Server)
* jbossall-client.jar (necessário se o AEM Forms for implantado no JBoss Application Server)

Para obter informações sobre a localização desses arquivos JAR, consulte [Incluindo arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Criar um cliente DocConvert**

Antes de executar programaticamente uma operação DocConverter, você deve criar um cliente DocConverter. Se você estiver usando a API Java, crie um objeto `DocConverterServiceClient`. Se você estiver usando a API do serviço Web DocConverter, crie um objeto `DocConverterServiceService`.

**Referencie um documento do PDF usado para determinar a conformidade com o PDF/A**

Um documento do PDF deve ser referenciado e passado para o serviço DocConverter para determinar se o documento do PDF é compatível com o PDF/A.

**Definir opções de tempo de execução**

Você pode definir uma opção de tempo de execução que determine quantas informações são rastreadas durante o processo de conversão. Ou seja, você pode definir nove níveis diferentes que especificam quantas informações o serviço DocConverter rastreia quando converte um documento PDF em um documento PDF/A.

**Recuperar informações sobre o documento do PDF**

Depois de criar o cliente de serviço DocConverter, fazer referência ao documento do PDF e definir as opções de tempo de execução, você pode determinar se o documento do PDF é um documento compatível com PDF/A.

**Consulte também**

[Determine a conformidade do PDF/A usando a API Java](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[Determine a conformidade do PDF/A usando a API do serviço Web](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Determine a conformidade do PDF/A usando a API Java {#determine-pdf-a-compliancy-using-the-java-api}

Determine a conformidade do PDF/A usando a API Java:

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente, como adobe-docconverter-client.jar, no caminho de classe do projeto Java.

1. Criar um cliente DocConvert

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `DocConverterServiceClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Referência a um documento do PDF usado para determinar a conformidade com o PDF/A

   * Crie um objeto `java.io.FileInputStream` que represente o documento PDF a ser convertido usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo PDF.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Definir opções de tempo de execução

   * Crie um objeto `PDFAValidationOptionSpec` usando seu construtor.
   * Defina o nível de conformidade chamando o método `setCompliance` do objeto `PDFAValidationOptionSpec` e transmitindo `PDFAValidationOptionSpec.Compliance.PDFA_1B`.
   * Defina o nível de rastreamento de informações invocando o método `setLogLevel` do objeto `PDFAValidationOptionSpec` e transmitindo um valor de cadeia de caracteres que especifica o nível de rastreamento. Por exemplo, passe o valor `FINE`. Para obter informações sobre os diferentes valores, consulte o método `setLogLevel` na [Referência da API AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Recuperar informações sobre o documento do PDF

   Determine a conformidade do PDF/A chamando o método `isPDFA` do objeto `DocConverterServiceClient` e transmitindo os seguintes valores:

   * O objeto `com.adobe.idp.Document` que contém o documento PDF.
   * O objeto `PDFAValidationOptionSpec` que especifica as opções de tempo de execução.

   O método `isPDFA` retorna um objeto `PDFAValidationResult` que contém os resultados desta operação.

**Consulte também**

[Trabalhar com documentos do PDF/A](pdf-a-documents.md#working-with-pdf-a-documents)

[Início rápido (modo SOAP): determinação da conformidade com o PDF/A usando a API do Java](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Determine a conformidade do PDF/A usando a API do serviço Web {#determine-pdf-a-compliancy-using-the-web-service-api}

Determine a conformidade do PDF/A usando a API do serviço da Web:

1. Incluir arquivos de projeto

   * Crie um assembly cliente Microsoft .NET que consuma o WSDL DocConverter.
   * Referencie o assembly do cliente Microsoft .NET.

1. Criar um cliente DocConvert

   * Usando o assembly do cliente Microsoft .NET, crie um objeto `DocConverterServiceService` invocando seu construtor padrão.
   * Defina o membro de dados `Credentials` do objeto `DocConverterServiceService` com um valor `System.Net.NetworkCredential` que especifique o nome de usuário e o valor da senha.

1. Referência a um documento do PDF usado para determinar a conformidade com o PDF/A

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar o documento PDF que é convertido em um documento PDF/A.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF e o modo em que o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com os dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `binaryData` com o conteúdo da matriz de bytes.

1. Definir opções de tempo de execução

   * Crie um objeto `PDFAValidationOptionSpec` usando seu construtor.
   * Defina o nível de conformidade atribuindo o membro de dados `compliance` do objeto `PDFAValidationOptionSpec` com o valor `PDFAConversionOptionSpec_Compliance.PDFA_1B`.
   * Defina o nível de rastreamento de informações atribuindo o membro de dados `resultLevel` do objeto `PDFAValidationOptionSpec` com o valor `PDFAValidationOptionSpec_ResultLevel.DETAILED`.

1. Recuperar informações sobre o documento do PDF

   Determine a conformidade do PDF/A chamando o método `isPDFA` do objeto `DocConverterServiceService` e transmitindo os seguintes valores:

   * O objeto `BLOB` que contém o documento PDF.
   * O objeto `PDFAValidationOptionSpec` que contém opções de tempo de execução.

   O método `isPDFA` retorna um objeto `PDFAValidationResult` que contém os resultados desta operação.

**Consulte também**

[Trabalhar com documentos do PDF/A](pdf-a-documents.md#working-with-pdf-a-documents)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Criando um assembly de cliente .NET que usa codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
