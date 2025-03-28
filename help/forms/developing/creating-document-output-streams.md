---
title: Criando Fluxos de Saída de Documento
description: Use o Serviço de saída para converter documentos como PDF (incluindo documentos do PDF/A), PostScript, Printer Control Language (PCL) e formatos de rótulo Zebra - ZPL, Intermec - IPL, Datamax - DPL e TecToshiba - TPCL.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
hide: true
hidefromtoc: true
exl-id: a90ccd28-00ae-4317-bfda-c39acbdb835b
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '18860'
ht-degree: 0%

---

# Criando Fluxos de Saída de Documento  {#creating-document-output-streams}

**Exemplos e exemplos neste documento são somente para AEM Forms no ambiente JEE.**

**Sobre o Serviço de Saída**

O Serviço de saída permite produzir documentos como PDF (incluindo documentos do PDF/A), PostScript, Printer Control Language (PCL) e os seguintes formatos de rótulo:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Usando o Serviço de saída, você pode mesclar dados de formulário XML com um design de formulário e enviar o documento para uma impressora ou arquivo de rede.

Há duas maneiras de passar um design de formulário (um arquivo XDP) para o serviço de Saída. Você pode passar uma instância `com.adobe.idp.Document` que contenha um design de formulário para o serviço de Saída. Ou você pode passar um valor de URI que especifica a localização do design do formulário. Ambas as maneiras são discutidas em *Programação com AEM forms*.

>[!NOTE]
>
>O serviço de Saída não é compatível com documentos do AcroForm PDF que contenham scripts específicos de objetos de aplicativo. Os documentos do Acro Form PDF que contêm scripts específicos de objeto de aplicativo não são renderizados.

As seções a seguir mostram como passar um design de formulário para o serviço de Saída usando um valor de URI:

* [Criação de documentos do PDF](creating-document-output-streams.md#creating-pdf-documents)
* [Criação de documentos do PDF/A](creating-document-output-streams.md#creating-pdf-a-documents)

As seções a seguir mostram como passar um design de formulário em uma instância `com.adobe.idp.Document`:

* [Passagem de documentos no Content Services (desaprovado) para o Serviço de saída](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Criação de documentos do PDF usando fragmentos](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

Uma consideração ao decidir qual técnica usar é se você está obtendo o design do formulário de outro serviço do AEM Forms e, em seguida, passá-lo dentro de uma instância `com.adobe.idp.Document`. As seções *Passando Documentos para o Serviço de Saída* e *Criando Documentos do PDF usando Fragmentos* mostram como obter um design de formulário de outro serviço do AEM Forms. A primeira seção recupera o design do formulário do Content Services (desaprovado). A segunda seção recupera o design do formulário do serviço Assembler.

Se você estiver obtendo o design do formulário de um local fixo, como o sistema de arquivos, poderá usar qualquer uma das técnicas. Ou seja, você pode especificar o valor do URI para um arquivo XDP ou usar uma instância `com.adobe.idp.Document`.

Para passar um valor de URI que especifique o local do design do formulário ao criar um documento do PDF, use o método `generatePDFOutput`. Da mesma forma, para passar uma instância `com.adobe.idp.Document` para o Serviço de saída ao criar um documento do PDF, use o método `generatePDFOutput2`.

Ao enviar um fluxo de saída para uma impressora de rede, você também pode usar qualquer uma das técnicas. Para enviar um fluxo de saída para uma impressora passando uma instância `com.adobe.idp.Document` que contenha um design de formulário, use o método `sendToPrinter2`. Para enviar um fluxo de saída para uma impressora passando um valor de URI, use o método `sendToPrinter`. A seção *Enviando Fluxos de Impressão para Impressoras* usa o método `sendToPrinter`.

Você pode realizar essas tarefas usando o Serviço de saída:

* [Criação de documentos do PDF](creating-document-output-streams.md#creating-pdf-documents)
* [Criação de documentos do PDF/A](creating-document-output-streams.md#creating-pdf-a-documents)
* [Passagem de documentos no Content Services (desaprovado) para o Serviço de saída](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [Criação de documentos do PDF usando fragmentos](creating-document-output-streams.md#creating-pdf-documents-using-fragments)
* [Imprimindo em Arquivos](creating-document-output-streams.md#printing-to-files)
* [Enviando fluxos de impressão para impressoras](creating-document-output-streams.md#sending-print-streams-to-printers)
* [Criação de vários arquivos de saída](creating-document-output-streams.md#creating-multiple-output-files)
* [Criação de regras de pesquisa](creating-document-output-streams.md#creating-search-rules)
* [Nivelamento de documentos do PDF](creating-document-output-streams.md#flattening-pdf-documents)

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Criação de documentos do PDF {#creating-pdf-documents}

Você pode usar o Serviço de saída para criar um documento do PDF com base em um design de formulário e em dados de formulário XML fornecidos. O documento PDF criado pelo serviço de saída não é um documento PDF interativo; um usuário não pode inserir ou modificar dados de formulário.

Se você deseja criar um documento do PDF para armazenamento de longo prazo, é recomendável criar um documento do PDF/A. (Consulte [Criação De Documentos Do PDF/A](creating-document-output-streams.md#creating-pdf-a-documents).)

Para criar um formulário interativo do PDF que permita ao usuário inserir dados, use o serviço Forms. (Consulte [Renderização do PDF forms Interativo](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms).)

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary-of-steps}

Para criar um documento do PDF, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de saída.
1. Fazer referência a uma fonte de dados XML.
1. Definir opções de tempo de execução do PDF.
1. Definir opções de tempo de execução de renderização.
1. Gere um documento do PDF.
1. Recuperar os resultados da operação.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao classpath do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (obrigatório se o AEM Forms for implantado no JBoss)
* jbossall-client.jar (obrigatório se o AEM Forms for implantado no JBoss)

se o AEM Forms for disponibilizado em um servidor de aplicativos J2EE compatível que não seja JBoss, você deverá substituir os arquivos adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos para o servidor de aplicativos J2EE no qual o AEM Forms é disponibilizado.

**Criar um objeto de Cliente de Saída**

Antes de executar programaticamente uma operação do Serviço de saída, você deve criar um objeto cliente do Serviço de saída. Se você estiver usando a API Java, crie um objeto `OutputClient`. Se você estiver usando a API de Serviço Web de Saída, crie um objeto `OutputServiceService`.

**Referenciar uma fonte de dados XML**

Para mesclar dados com o design do formulário, você deve fazer referência a uma fonte de dados XML que contém dados. Um elemento XML deve existir para cada campo de formulário que você planeja preencher com dados. O nome do elemento XML deve corresponder ao nome do campo. Um elemento XML será ignorado se não corresponder a um campo de formulário ou se o nome do elemento XML não corresponder ao nome do campo. Não é necessário corresponder à ordem em que os elementos XML são exibidos se todos os elementos XML forem especificados.

Considere o exemplo de formulário de aplicativo de empréstimo a seguir.

![cp_cp_loanformdata](assets/cp_cp_loanformdata.png)

Para mesclar dados nesse design de formulário, você deve criar uma fonte de dados XML que corresponda ao formulário. O XML a seguir representa uma fonte de dados XML XDP que corresponde ao exemplo de formulário de aplicativo de hipoteca.

```xml
 <?xml version="1.0" encoding="UTF-8" ?>
 - <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
 - <xfa:data>
 - <data>
     - <Layer>
         <closeDate>1/26/2007</closeDate>
         <lastName>Johnson</lastName>
         <firstName>Jerry</firstName>
         <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
         <city>New York</city>
         <zipCode>00501</zipCode>
         <state>NY</state>
         <dateBirth>26/08/1973</dateBirth>
         <middleInitials>D</middleInitials>
         <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
         <phoneNumber>5555550000</phoneNumber>
     </Layer>
     - <Mortgage>
         <mortgageAmount>295000.00</mortgageAmount>
         <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
         <purchasePrice>300000</purchasePrice>
         <downPayment>5000</downPayment>
         <term>25</term>
         <interestRate>5.00</interestRate>
     </Mortgage>
 </data>
 </xfa:data>
 </xfa:datasets>
```

**Definir opções de tempo de execução do PDF**

Defina a opção de URI do arquivo ao criar um documento do PDF. Esta opção especifica o nome e o local do arquivo PDF gerado pelo serviço de saída.

>[!NOTE]
>
>Em vez de definir a opção de tempo de execução do URI do arquivo, você pode recuperar programaticamente o documento do PDF a partir do tipo de dados complexo retornado pelo serviço de Saída. No entanto, ao definir a opção de tempo de execução do URI do arquivo, não é necessário criar uma lógica de aplicativo que recupere programaticamente o documento do PDF.

**Definir opções de tempo de execução de renderização**

É possível definir opções de tempo de execução de renderização ao criar um documento do PDF. Embora essas opções não sejam necessárias (ao contrário das opções de tempo de execução do PDF que são necessárias), você pode executar tarefas como melhorar o desempenho do serviço de Saída. Por exemplo, é possível armazenar em cache o design do formulário que o serviço de Saída usa para melhorar o desempenho.

Se você usar um formulário Acrobat marcado como entrada, não poderá usar o Java do serviço de saída ou a API do serviço da Web para desativar a configuração marcada. Se você tentar definir esta opção de forma programática como `false`, o documento PDF resultante ainda será marcado.

>[!NOTE]
>
>Se você não especificar opções de tempo de execução de renderização, os valores padrão serão usados. Para obter informações sobre as opções de tempo de execução de renderização, consulte a referência de classe `RenderOptionsSpec`. (Consulte [Referência da API do AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

**Gerar um documento do PDF**

Depois de fazer referência a uma fonte de dados XML válida que contém dados de formulário e definir opções de tempo de execução, você pode chamar o serviço Output, o que resulta na geração de um documento PDF.

Ao gerar um documento do PDF, você especifica valores de URI que são exigidos pelo serviço de Saída para criar um documento do PDF. Um design de formulário pode ser armazenado em locais como o sistema de arquivos do servidor ou como parte de um aplicativo do AEM Forms. Um design de formulário (ou outros recursos, como um arquivo de imagem) que existe como parte de um aplicativo do Forms pode ser referenciado usando o valor de URI da raiz de conteúdo `repository:///`. Por exemplo, considere o seguinte design de formulário chamado *Loan.xdp* localizado em um aplicativo do Forms chamado *Applications/FormsApplication*:

![cp_cp_formrepository](assets/cp_cp_formrepository.png)

Para acessar o arquivo Loan.xdp mostrado na ilustração anterior, especifique `repository:///Applications/FormsApplication/1.0/FormsFolder/` como o terceiro parâmetro passado para o método `generatePDFOutput` do objeto `OutputClient`. Especifique o nome do formulário (*Loan.xdp*) como o segundo parâmetro passado para o método `generatePDFOutput` do objeto `OutputClient`.

Se o arquivo XDP contiver imagens (ou outros recursos, como fragmentos), coloque os recursos na mesma pasta do aplicativo que o arquivo XDP. O AEM Forms usa o URI da raiz do conteúdo como o caminho base para resolver referências a imagens. Por exemplo, se o arquivo Loan.xdp contiver uma imagem, certifique-se de colocar a imagem em `Applications/FormsApplication/1.0/FormsFolder/`.

>[!NOTE]
>
>Você pode fazer referência a um URI de aplicativo Forms ao invocar os métodos `generatePDFOutput` ou `generatePrintedOutput` do objeto `OutputClient`.

>[!NOTE]
>
>Para ver um início rápido completo que cria um documento do PDF referenciando um XDP em um aplicativo do Forms, consulte [Início Rápido (modo EJB): Criando um documento do PDF com base em um arquivo XDP de aplicativo usando a API do Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api).

**Recuperar os resultados da operação**

Depois que o Serviço de saída executa uma operação, ele retorna vários itens de dados, como dados XML de status, que especificam se a operação foi bem-sucedida.

**Consulte também**

[Criar um documento do PDF usando a API Java](creating-document-output-streams.md#create-a-pdf-document-using-the-java-api)

[Criar um documento do PDF usando a API do serviço Web](creating-document-output-streams.md#create-a-pdf-document-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Criar um documento do PDF usando a API Java {#create-a-pdf-document-using-the-java-api}

Crie um documento do PDF usando a API de saída (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `java.io.FileInputStream` que represente a fonte de dados XML usada para preencher o documento PDF usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo XML.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor. Passar o objeto `java.io.FileInputStream`.

1. Definir opções de tempo de execução do PDF.

   * Crie um objeto `PDFOutputOptionsSpec` usando seu construtor.
   * Defina a opção File URI invocando o método `setFileURI` do objeto `PDFOutputOptionsSpec`. Transmita um valor de string que especifique o local do arquivo PDF gerado pelo serviço de Saída. A opção File URI é relativa ao servidor de aplicativos J2EE que hospeda o AEM Forms, não ao computador cliente.

1. Definir opções de tempo de execução de renderização.

   * Crie um objeto `RenderOptionsSpec` usando seu construtor.
   * Armazene em cache o design do formulário para melhorar o desempenho do serviço de Saída invocando `setCacheEnabled` do objeto `RenderOptionsSpec` e transmitindo `true`.

   >[!NOTE]
   >
   >Você não pode definir a versão do documento PDF usando o método `setPdfVersion` do objeto `RenderOptionsSpec` se o documento de entrada for um formulário Acrobat (um formulário criado no Acrobat) ou um documento XFA assinado ou certificado. O documento de saída do PDF retém a versão original do PDF. Da mesma forma, não é possível definir a opção Adobe PDF marcada invocando o método `setTaggedPDF` do objeto `RenderOptionsSpec` se o documento de entrada for um formulário do Acrobat ou um documento XFA assinado ou certificado.

   >[!NOTE]
   >
   >Não é possível definir a opção PDF linearizada usando o método `setLinearizedPDF` do objeto `RenderOptionsSpec` se o documento PDF de entrada estiver certificado ou assinado digitalmente. (Consulte [Assinatura digital de documentos do PDF ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Gere um documento do PDF.

   Crie um documento PDF chamando o método `generatePDFOutput` do objeto `OutputClient` e transmitindo os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de cadeia de caracteres que especifica a raiz do conteúdo onde o design do formulário está localizado.
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `com.adobe.idp.Document` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.

   O método `generatePDFOutput` retorna um objeto `OutputResult` que contém os resultados da operação.

   >[!NOTE]
   >
   >Ao gerar um documento do PDF invocando o método `generatePDFOutput`, não é possível mesclar dados com um formulário do PDF XFA que esteja assinado ou certificado. (Consulte [Documentos de Assinatura e Certificação Digitais ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >O método `getRecordLevelMetaDataList` do objeto `OutputResult` retorna `null`*.*

   >[!NOTE]
   >
   >Você também pode criar um documento PDF invocando o método `generatePDFOutput2` do objeto `OutputClient`. (Consulte [Passando Documentos no Content Services (desaprovado) para o Serviço de Saída ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Recuperar os resultados da operação.

   * Recupere um objeto `com.adobe.idp.Document` que represente o status da operação `generatePDFOutput` invocando o método `getStatusDoc` do objeto `OutputResult`. Esse método retorna dados XML de status que especificam se a operação foi bem-sucedida.
   * Crie um objeto `java.io.File` que contenha os resultados da operação. Verifique se a extensão do nome do arquivo é .xml.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo (certifique-se de usar o objeto `com.adobe.idp.Document` retornado pelo método `getStatusDoc`).

   Embora o serviço de Saída grave o documento PDF no local especificado pelo argumento passado para o método `setFileURI` do objeto `PDFOutputOptionsSpec`, é possível recuperar programaticamente o documento PDF/A invocando o método `getGeneratedDoc` do objeto `OutputResult`.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo EJB): Criação de um documento PDF usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Início rápido (modo SOAP): Criação de um documento PDF usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Criar um documento do PDF usando a API do serviço Web {#create-a-pdf-document-using-the-web-service-api}

Crie um documento do PDF usando a API de saída (serviço Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar dados XML que serão mesclados com o documento PDF.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo XML que contém dados de formulário.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo seu campo `MTOM` com o conteúdo da matriz de bytes.

1. Definir opções de tempo de execução do PDF

   * Crie um objeto `PDFOutputOptionsSpec` usando seu construtor.
   * Defina a opção File URI atribuindo um valor de cadeia de caracteres que especifique o local do arquivo PDF que o serviço de Saída gera para o membro de dados `fileURI` do objeto `PDFOutputOptionsSpec`. A opção File URI é relativa ao servidor de aplicativos J2EE que hospeda o AEM Forms, não ao computador cliente.

1. Definir opções de tempo de execução de renderização.

   * Crie um objeto `RenderOptionsSpec` usando seu construtor.
   * Armazene em cache o design do formulário para melhorar o desempenho do serviço de Saída atribuindo o valor `true` ao membro de dados `cacheEnabled` do objeto `RenderOptionsSpec`.

   >[!NOTE]
   >
   >Você não pode definir a versão do documento PDF usando o método `setPdfVersion` do objeto `RenderOptionsSpec` se o documento de entrada for um formulário Acrobat (um formulário criado no Acrobat) ou um documento XFA assinado ou certificado. O documento de saída do PDF retém a versão original do PDF. Da mesma forma, você não pode definir a opção Adobe PDF marcada invocando o método `setTaggedPDF`* do objeto `RenderOptionsSpec` se o documento de entrada for um formulário do Acrobat ou um documento XFA assinado ou certificado.*

   >[!NOTE]
   >
   >Não é possível definir a opção PDF linearizada usando o membro `linearizedPDF` do objeto `RenderOptionsSpec` se o documento PDF de entrada estiver certificado ou assinado digitalmente. (Consulte [Assinatura digital de documentos do PDF ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Gere um documento do PDF.

   Crie um documento PDF chamando o método `generatePDFOutput` do objeto `OutputServiceService` e transmitindo os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de cadeia de caracteres que especifica a raiz do conteúdo onde o design do formulário está localizado.
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `BLOB` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com metadados gerados que descrevem o documento. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com os dados do resultado. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).
   * Um objeto `OutputResult` que contém os resultados da operação. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).

   >[!NOTE]
   >
   >Ao gerar um documento do PDF invocando o método `generatePDFOutput`, não é possível mesclar dados com um formulário do PDF XFA que esteja assinado ou certificado. (Consulte [Documentos de Assinatura e Certificação Digitais ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >Você também pode criar um documento PDF invocando o método `generatePDFOutput2` do objeto `OutputClient`. (Consulte [Passando Documentos no Content Services (desaprovado) para o Serviço de Saída ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Recuperar os resultados da operação.

   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa um local de arquivo XML que contém dados de resultado. Verifique se a extensão do nome do arquivo é .xml.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` que foi preenchido com dados de resultado pelo método `generatePDFOutput` do objeto `OutputServiceService` (o oitavo parâmetro). Preencha a matriz de bytes obtendo o valor de `MTOM` `field` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes no arquivo XML invocando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

   Consulte também:

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

   >[!NOTE]
   >
   >O método `generateOutput` do objeto `OutputServiceService` está obsoleto.

## Criação de documentos do PDF/A {#creating-pdf-a-documents}

Você pode usar o Serviço de saída para criar um documento PDF/A. Como o PDF/A é um formato de arquivamento para preservação de longo prazo do conteúdo do documento, todas as fontes são incorporadas e o arquivo é descompactado. Como resultado, um documento PDF/A geralmente é maior do que um documento PDF padrão. Além disso, um documento PDF/A não contém conteúdo de áudio e vídeo. Como outras tarefas do Serviço de saída, você fornece um design de formulário e dados para mesclar com um design de formulário para criar um documento do PDF/A.

A especificação PDF/A-1 consiste em dois níveis de conformidade, a saber, a e b. A principal diferença entre os dois diz respeito ao suporte de estrutura lógica (acessibilidade), que não é necessário para o nível de conformidade b. Independentemente do nível de conformidade, o PDF/A-1 determina que todas as fontes sejam incorporadas no documento PDF/A gerado.

Embora o PDF/A seja o padrão para arquivamento de documentos do PDF, não é obrigatório que o PDF/A seja usado para arquivamento se um documento padrão do PDF atender às necessidades da sua empresa. O objetivo do padrão PDF/A é estabelecer um arquivo PDF que possa ser armazenado por um longo período e atender aos requisitos de preservação de documentos. Por exemplo, um URL não pode ser incorporado em um PDF/A porque, com o tempo, o URL pode se tornar inválido.

Sua empresa deve avaliar suas próprias necessidades, o tempo que pretende manter o documento, as considerações sobre o tamanho do arquivo e determinar sua própria estratégia de arquivamento. Você pode determinar programaticamente se um documento do PDF é compatível com o PDF/A usando o serviço DocConverter. (Consulte [Determinação Programática Da Conformidade Com O PDF/A](/help/forms/developing/pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

Um documento PDF/A deve usar a fonte especificada no design do formulário, e as fontes não podem ser substituídas. Como resultado, se uma fonte localizada em um documento do PDF não estiver disponível no sistema operacional (SO) do host, ocorrerá uma exceção.

Quando um documento PDF/A é aberto no Acrobat, uma mensagem é exibida confirmando que o documento é um documento PDF/A, como mostrado na ilustração a seguir.

![cp_cp_pdfamessage](assets/cp_cp_pdfamessage.png)

>[!NOTE]
>
>O site do AIIM tem uma seção de perguntas frequentes do PDF/A que você pode acessar em [https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml](https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml).

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_65).

### Resumo das etapas {#summary_of_steps-1}

Para criar um documento PDF/A, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de saída.
1. Fazer referência a uma fonte de dados XML.
1. Definir opções de tempo de execução do PDF/A.
1. Definir opções de tempo de execução de renderização.
1. Gere um documento PDF/A.
1. Recuperar os resultados da operação.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação personalizada usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (obrigatório se o AEM Forms for implantado no JBoss)
* jbossall-client.jar (obrigatório se o AEM Forms for implantado no JBoss)

se o AEM Forms for disponibilizado em um servidor de aplicativos J2EE compatível que não seja JBoss, você deverá substituir os arquivos adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos para o servidor de aplicativos J2EE no qual o AEM Forms é disponibilizado.

**Criar um objeto de Cliente de Saída**

Antes de executar programaticamente uma operação do Serviço de saída, você deve criar um objeto cliente do Serviço de saída. Se você estiver usando a API Java, crie um objeto `OutputClient`. Se você estiver usando a API de Serviço Web de Saída, crie um objeto `OutputServiceService`.

**Referenciar uma fonte de dados XML**

Para mesclar dados com o design do formulário, você deve fazer referência a uma fonte de dados XML que contém dados. Um elemento XML deve existir para cada campo de formulário que você deseja preencher com dados. O nome do elemento XML deve corresponder ao nome do campo. Um elemento XML será ignorado se não corresponder a um campo de formulário ou se o nome do elemento XML não corresponder ao nome do campo. Não é necessário corresponder à ordem em que os elementos XML são exibidos se todos os elementos XML forem especificados.

**Definir opções de tempo de execução do PDF/A**

É possível definir a opção File URI ao criar um documento do PDF/A. O URI é relativo ao servidor de aplicativos J2EE que hospeda o AEM Forms. Ou seja, se você definir C:\Adobe, o arquivo será gravado na pasta no servidor, não no computador cliente. O URI especifica o nome e o local do arquivo PDF/A gerado pelo serviço de saída.

**Definir opções de tempo de execução de renderização**

É possível definir opções de tempo de execução de renderização ao criar documentos do PDF/A. Duas opções relacionadas a PDF/A que você pode definir são os valores `PDFAConformance` e `PDFARevisionNumber`. O valor `PDFAConformance` refere-se à forma como um documento PDF segue os requisitos que especificam como os documentos eletrônicos de longo prazo são preservados. Os valores válidos para esta opção são `A` e `B`. Para obter informações sobre a conformidade dos níveis a e b, consulte a especificação PDF/A-1 ISO intitulada *ISO 19005-1 Document management*.

O valor `PDFARevisionNumber` refere-se ao número de revisão de um documento PDF/A. Para obter informações sobre o número de revisão de um documento PDF/A, consulte a especificação PDF/A-1 ISO intitulada *ISO 19005-1 Document management*.

>[!NOTE]
>
>Não é possível definir a opção Adobe PDF marcada como `false` ao criar um documento PDF/A 1A. O PDF/A 1A será sempre um documento PDF marcado. Além disso, não é possível definir a opção Adobe PDF com tags como `true` ao criar um documento PDF/A 1B. O PDF/A 1B será sempre um documento PDF não marcado.

**Gerar um documento PDF/A**

Depois de fazer referência a uma fonte de dados XML válida que contém dados de formulário e definir opções de tempo de execução, você pode chamar o serviço Saída, fazendo com que ele gere um documento PDF/A.

**Recuperar os resultados da operação**

Depois que o Serviço de saída executa uma operação, ele retorna vários itens de dados, como dados XML, que especificam se a operação foi bem-sucedida.

**Consulte também**

[Criar um documento PDF/A usando a API Java](creating-document-output-streams.md#create-a-pdf-a-document-using-the-java-api)

[Criar um documento PDF/A usando a API do serviço Web](creating-document-output-streams.md#create-a-pdf-a-document-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Criar um documento PDF/A usando a API Java {#create-a-pdf-a-document-using-the-java-api}

Crie um documento PDF/A usando a API de saída (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `java.io.FileInputStream` que represente a fonte de dados XML usada para preencher o documento PDF/A usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo XML.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Definir opções de tempo de execução do PDF/A.

   * Crie um objeto `PDFOutputOptionsSpec` usando seu construtor.
   * Defina a opção File URI invocando o método `setFileURI` do objeto `PDFOutputOptionsSpec`. Transmita um valor de string que especifique o local do arquivo PDF gerado pelo serviço de Saída. A opção File URI é relativa ao servidor de aplicativos J2EE que hospeda o AEM Forms, não ao computador cliente.

1. Definir opções de tempo de execução de renderização.

   * Crie um objeto `RenderOptionsSpec` usando seu construtor.
   * Defina o valor `PDFAConformance` invocando o método `setPDFAConformance` do objeto `RenderOptionsSpec` e transmitindo um valor de enumeração `PDFAConformance` que especifica o nível de conformidade. Por exemplo, para especificar o nível de conformidade A, passe `PDFAConformance.A`.
   * Defina o valor `PDFARevisionNumber` invocando o método `setPDFARevisionNumber` do objeto `RenderOptionsSpec` e transmitindo `PDFARevisionNumber.Revision_1`.

   >[!NOTE]
   >
   >A versão do PDF de um documento PDF/A é a 1.4, independentemente do valor especificado para o `setPdfVersion`*método.* do objeto `RenderOptionsSpec`.

1. Gere um documento PDF/A.

   Crie um documento PDF/A chamando o método `generatePDFOutput` do objeto `OutputClient` e transmitindo os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF/A, especifique `TransformationFormat.PDFA`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de cadeia de caracteres que especifica a raiz do conteúdo onde o design do formulário está localizado.
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `com.adobe.idp.Document` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.

   O método `generatePDFOutput` retorna um objeto `OutputResult` que contém os resultados da operação.

   >[!NOTE]
   >
   >O método `getRecordLevelMetaDataList` do objeto `OutputResult` retorna `null`.

   >[!NOTE]
   >
   >Você também pode criar um documento PDF /A invocando o método `generatePDFOutput`2 do objeto `OutputClient`. (Consulte [Passando Documentos no Content Services (desaprovado) para o Serviço de Saída](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Recuperar os resultados da operação.

   * Crie um objeto `com.adobe.idp.Document` que represente o status do método `generatePDFOutput` invocando o método `getStatusDoc` do objeto `OutputResult`.
   * Crie um objeto `java.io.File` que conterá os resultados da operação. Verifique se a extensão do nome do arquivo é .xml.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo (certifique-se de usar o objeto `com.adobe.idp.Document` retornado pelo método `getStatusDoc`).

   >[!NOTE]
   >
   >Embora o serviço de Saída grave o documento PDF/A no local especificado pelo argumento passado para o método `setFileURI` do objeto `PDFOutputOptionsSpec`, é possível recuperar programaticamente o documento PDF/A invocando o método `getGeneratedDoc` do objeto `OutputResult`.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo SOAP): Criação de um documento PDF/A usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-a-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Criar um documento PDF/A usando a API do serviço Web {#create-a-pdf-a-document-using-the-web-service-api}

Crie um documento PDF/A usando a API de saída (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar dados que serão mesclados com o documento PDF/A.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF a ser criptografado e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo seu campo `MTOM` com o conteúdo da matriz de bytes.

1. Definir opções de tempo de execução do PDF/A.

   * Crie um objeto `PDFOutputOptionsSpec` usando seu construtor.
   * Defina a opção File URI atribuindo um valor de cadeia de caracteres que especifique o local do arquivo PDF que o serviço de Saída gera para o membro de dados `fileURI` do objeto `PDFOutputOptionsSpec`. A opção File URI é relativa ao servidor de aplicativos J2EE que hospeda o AEM Forms, não ao computador cliente

1. Definir opções de tempo de execução de renderização.

   * Crie um objeto `RenderOptionsSpec` usando seu construtor.
   * Defina o valor `PDFAConformance` atribuindo um valor de enumeração `PDFAConformance` ao membro de dados `PDFAConformance` do objeto `RenderOptionsSpec`. Por exemplo, para especificar o nível de conformidade A, atribua `PDFAConformance.A` a esse membro de dados.
   * Defina o valor `PDFARevisionNumber` atribuindo um valor de enumeração `PDFARevisionNumber` ao membro de dados `PDFARevisionNumber` do objeto `RenderOptionsSpec`. Atribuir `PDFARevisionNumber.Revision_1` a este membro de dados.

   >[!NOTE]
   >
   >A versão do PDF de um documento PDF/A é a 1.4, independentemente do valor especificado.

1. Gere um documento PDF/A.

   Crie um documento PDF chamando o método `generatePDFOutput` do objeto `OutputServiceService` e transmitindo os seguintes valores:

   * Um valor de enumeração TransformationFormat. Para gerar um documento PDF, especifique `TransformationFormat.PDFA`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de cadeia de caracteres que especifica a raiz do conteúdo onde o design do formulário está localizado.
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `BLOB` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com metadados gerados que descrevem o documento. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com os dados do resultado. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)
   * Um objeto `OutputResult` que contém os resultados da operação. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)

   >[!NOTE]
   >
   >Você também pode criar um documento PDF /A invocando o método `generatePDFOutput`2 do objeto `OutputClient`. (Consulte [Passando Documentos no Content Services (desaprovado) para o Serviço de Saída](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Recuperar os resultados da operação.

   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa um local de arquivo XML que contém dados de resultado. Verifique se a extensão do nome do arquivo é .xml.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` que foi preenchido com dados de resultado pelo método `generatePDFOutput` do objeto `OutputServiceService` (o oitavo parâmetro). Popular a matriz de bytes obtendo o valor do campo `MTOM` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes no arquivo XML invocando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Passagem de documentos no Content Services (desaprovado) para o Serviço de saída {#passing-documents-located-in-content-services-deprecated-to-the-output-service}

O serviço de Saída renderiza um formulário não interativo do PDF com base em um design de formulário que normalmente é salvo como um arquivo XDP e criado no Designer. Você pode passar um objeto `com.adobe.idp.Document` que contenha o design do formulário para o serviço de Saída. O Serviço de saída renderiza o design do formulário no objeto `com.adobe.idp.Document`.

Uma vantagem de passar um objeto `com.adobe.idp.Document` para o serviço de Saída é que outras operações de serviço do AEM Forms retornam uma instância `com.adobe.idp.Document`. Ou seja, você pode obter uma instância `com.adobe.idp.Document` de outra operação de serviço e renderizá-la. Por exemplo, digamos que um arquivo XDP esteja armazenado em um nó do Content Services (obsoleto) chamado `/Company Home/Form Designs`, como mostrado na ilustração a seguir.

Você pode recuperar programaticamente Loan.xdp do Content Services (desaprovado) e passar o arquivo XDP para o Serviço de saída em um objeto `com.adobe.idp.Document`.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Forms, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-2}

Para passar um documento obtido do Content Services (obsoleto) para o serviço de Saída, execute as seguintes tarefas:

1. Incluir arquivos de projeto.
1. Crie um objeto de Saída e de API do cliente de Gerenciamento de documentos.
1. Recuperar o design do formulário do Content Services (desaprovado).
1. Renderize o formulário não interativo do PDF.
1. Execute uma ação com o fluxo de dados.

**Incluir arquivos de projeto**

Inclua os arquivos necessários ao projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar um objeto de API de Cliente de Gerenciamento de Documentos e de Saída**

Antes de executar programaticamente uma operação da API do Serviço de saída, crie um objeto da API do Cliente de saída. Além disso, como esse fluxo de trabalho recupera um arquivo XDP do Content Services (obsoleto), crie um objeto de API do Document Management.

**Recuperar o design do formulário do Content Services (desaprovado)**

Recupere o arquivo XDP do Content Services (obsoleto) usando o Java ou a API do serviço da Web. O arquivo XDP é retornado em uma instância `com.adobe.idp.Document` (ou uma instância `BLOB` se você estiver usando serviços da Web). Em seguida, você pode passar a instância `com.adobe.idp.Document` para o serviço de Saída.

**Renderizar o formulário não interativo do PDF**

Para renderizar um formulário não interativo, passe a instância `com.adobe.idp.Document` que foi retornada do Content Services (desaprovado) para o serviço de Saída.

>[!NOTE]
>
>Dois novos métodos nomeados como `generatePDFOutput2`e g `eneratePrintedOutput2`aceitam um objeto `com.adobe.idp.Document` que contém um design de formulário. Você também pode passar um `com.adobe.idp.Document` que contenha o design do formulário para o serviço de Saída ao enviar um fluxo de impressão para uma impressora de rede.

**Executar uma ação com o fluxo de dados de formulário**

Você pode salvar o formulário não interativo como um arquivo PDF. O formulário pode ser exibido no Adobe Reader ou Acrobat.

**Consulte também**

[Enviar documentos para o Serviço de saída usando a API Java](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-java-api)

[Enviar documentos para o Serviço de saída usando a API do serviço Web](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Criação de documentos do PDF usando fragmentos](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

### Enviar documentos para o Serviço de saída usando a API Java {#pass-documents-to-the-output-service-using-the-java-api}

Envie um documento recuperado do Content Services (desaprovado) usando o Serviço de saída e a API do Content Services (desaprovado) (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar e adobe-contentservices-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto de Saída e de API do cliente de Gerenciamento de documentos.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão. (Consulte [Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.
   * Crie um objeto `DocumentManagementServiceClientImpl` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Recuperar o design do formulário do Content Services (desaprovado).

   Invoque o método `retrieveContent` do objeto `DocumentManagementServiceClientImpl` e passe os seguintes valores:

   * Um valor de string que especifica o armazenamento em que o conteúdo é adicionado. O armazenamento padrão é `SpacesStore`. Esse valor é um parâmetro obrigatório.
   * Um valor de cadeia que especifica o caminho totalmente qualificado do conteúdo a ser recuperado (por exemplo, `/Company Home/Form Designs/Loan.xdp`). Esse valor é um parâmetro obrigatório.
   * Um valor de string que especifica a versão. Esse valor é um parâmetro opcional e você pode passar uma string vazia. Nessa situação, a versão mais recente é recuperada.

   O método `retrieveContent` retorna um objeto `CRCResult` que contém o arquivo XDP. Recupere uma instância `com.adobe.idp.Document` invocando o método `getDocument` do objeto `CRCResult`.

1. Renderize o formulário não interativo do PDF.

   Invoque o método `generatePDFOutput2` do objeto `OutputClient` e passe os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de string que especifica a raiz do conteúdo onde os recursos adicionais, como imagens, estão localizados.
   * Um objeto `com.adobe.idp.Document` que representa o design do formulário (use a instância retornada pelo método `getDocument` do objeto `CRCResult`).
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `com.adobe.idp.Document` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.

   O método `generatePDFOutput2` retorna um objeto `OutputResult` que contém os resultados da operação.

1. Execute uma ação com o fluxo de dados de formulário.

   * Recupere um objeto `com.adobe.idp.Document` que represente o formulário não interativo invocando o método `getGeneratedDoc` do objeto `OutputResult`.
   * Crie um objeto `java.io.File` que contenha os resultados da operação. Verifique se a extensão do nome do arquivo é .pdf.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo (certifique-se de usar o objeto `com.adobe.idp.Document` retornado pelo método `getGeneratedDoc`).

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo EJB): Passar documentos para o serviço de saída usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Início rápido (modo SOAP): passar documentos para o serviço de saída usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Enviar documentos para o Serviço de saída usando a API do serviço Web {#pass-documents-to-the-output-service-using-the-web-service-api}

Envie um documento recuperado do Content Services (desaprovado) usando o Serviço de saída e a API do Content Services (desaprovado) (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Como este aplicativo cliente invoca dois serviços AEM Forms, crie duas referências de serviço. Use a seguinte definição WSDL para a referência de serviço associada ao serviço de Saída: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   Use a seguinte definição WSDL para a referência de serviço associada ao serviço de Gerenciamento de Documentos: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Como o tipo de dados `BLOB` é comum a ambas as referências de serviço, qualifique totalmente o tipo de dados `BLOB` ao usá-lo. No início rápido do serviço Web correspondente, todas as `BLOB` instâncias são totalmente qualificadas.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto de Saída e de API do cliente de Gerenciamento de documentos.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de string que especifique o WSDL para o serviço Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`). Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço.)
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Repita essas etapas para o cliente de serviço `DocumentManagementServiceClient`.

1. Recuperar o design do formulário do Content Services (desaprovado).

   Recupere o conteúdo chamando o método `retrieveContent` do objeto `DocumentManagementServiceClient` e transmitindo os seguintes valores:

   * Um valor de string que especifica o armazenamento em que o conteúdo é adicionado. O armazenamento padrão é `SpacesStore`. Esse valor é um parâmetro obrigatório.
   * Um valor de cadeia que especifica o caminho totalmente qualificado do conteúdo a ser recuperado (por exemplo, `/Company Home/Form Designs/Loan.xdp`). Esse valor é um parâmetro obrigatório.
   * Um valor de string que especifica a versão. Esse valor é um parâmetro opcional e você pode passar uma string vazia. Nessa situação, a versão mais recente é recuperada.
   * Um parâmetro de saída da string que armazena o valor do link de pesquisa.
   * Um parâmetro de saída `BLOB` que armazena o conteúdo. Você pode usar esse parâmetro de saída para recuperar o conteúdo.
   * Um parâmetro de saída `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` que armazena atributos de conteúdo.
   * Um parâmetro de saída `CRCResult`. Em vez de usar esse objeto, você pode usar o parâmetro de saída `BLOB` para recuperar o conteúdo.

1. Renderize o formulário não interativo do PDF.

   Invoque o método `generatePDFOutput2` do objeto `OutputServiceClient` e passe os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de string que especifica a raiz do conteúdo onde os recursos adicionais, como imagens, estão localizados.
   * Um objeto `BLOB` que representa o design do formulário (use a instância `BLOB` retornada pelo Content Services (desaprovado)).
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `BLOB` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.
   * Um objeto de saída `BLOB` preenchido pelo método `generatePDFOutput2`. O método `generatePDFOutput2` preenche este objeto com metadados gerados que descrevem o documento. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).
   * Um objeto de saída `OutputResult` que contém os resultados da operação. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).

   O método `generatePDFOutput2` retorna um objeto `BLOB` que contém o formulário PDF não interativo.

1. Execute uma ação com o fluxo de dados de formulário.

   * Crie um objeto `System.IO.FileStream` invocando seu construtor. Transmita um valor de string que represente o local do arquivo do documento interativo do PDF e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `BLOB` recuperado do método `generatePDFOutput2`. Popular a matriz de bytes obtendo o valor do membro de dados `MTOM` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Passar documentos no repositório para o serviço de saída {#passing-documents-located-in-the-repository-to-the-output-service}

O serviço de Saída renderiza um formulário não interativo do PDF com base em um design de formulário que normalmente é salvo como um arquivo XDP e criado no Designer. Você pode passar um objeto `com.adobe.idp.Document` que contenha o design do formulário para o serviço de Saída. O Serviço de saída renderiza o design do formulário no objeto `com.adobe.idp.Document`.

Uma vantagem de passar um objeto `com.adobe.idp.Document` para o serviço de Saída é que outras operações de serviço do AEM Forms retornam uma instância `com.adobe.idp.Document`. Ou seja, você pode obter uma instância `com.adobe.idp.Document` de outra operação de serviço e renderizá-la. Por exemplo, suponha que um arquivo XDP esteja armazenado no repositório do AEM Forms, conforme mostrado na ilustração a seguir.

![pd_pd_formrepository](assets/pd_pd_formrepository.png)

A pasta *FormsFolder* é um local definido pelo usuário no repositório do AEM Forms (esse local é um exemplo e não existe por padrão). Neste exemplo, um design de formulário chamado Loan.xdp está nesta pasta. Além do design do formulário, outros materiais de apoio como imagens podem ser armazenados neste local. O caminho para um recurso no repositório do AEM Forms é:

`Applications/Application-name/Application-version/Folder.../Filename`

Você pode recuperar programaticamente Loan.xdp do repositório do AEM Forms e passá-lo para o Serviço de saída em um objeto `com.adobe.idp.Document`.

Você pode criar uma PDF com base em um arquivo XDP no repositório usando uma das duas formas a seguir. Você pode passar a localização XDP por referência ou recuperar programaticamente o XDP do repositório e transmiti-lo para o serviço de Saída em um arquivo XDP.

[Início Rápido (modo EJB): criando um documento PDF com base em um arquivo XDP de aplicativo usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api) (mostra como passar a localização do arquivo XDP por referência).

[Início Rápido (modo EJB): Passar um documento no Repositório AEM Forms para o serviço de Saída usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (mostra como recuperar programaticamente o arquivo XDP do Repositório AEM Forms e passá-lo para o serviço de Saída em uma instância `com.adobe.idp.Document`). (Esta seção discute como executar esta tarefa)

>[!NOTE]
>
>Para obter mais informações sobre o serviço Forms, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-3}

Para passar um documento obtido do repositório do AEM Forms para o Serviço de saída, execute as seguintes tarefas:

1. Incluir arquivos de projeto.
1. Crie um objeto de Saída e de API do cliente de Gerenciamento de documentos.
1. Recupere o design do formulário do repositório do AEM Forms.
1. Renderize o formulário não interativo do PDF.
1. Execute uma ação com o fluxo de dados.

**Incluir arquivos de projeto**

Inclua os arquivos necessários ao projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar um objeto de API de Cliente de Gerenciamento de Documentos e de Saída**

Antes de executar programaticamente uma operação da API do Serviço de saída, crie um objeto da API do Cliente de saída. Além disso, como esse fluxo de trabalho recupera um arquivo XDP do Content Services (obsoleto), crie um objeto de API do Document Management.

**Recuperar o design do formulário do Repositório do AEM Forms**

Recupere o arquivo XDP do Repositório do AEM Forms usando a API do Repositório. (Consulte [Recursos de Leitura](/help/forms/developing/aem-forms-repository.md#reading-resources).)

O arquivo XDP é retornado em uma instância `com.adobe.idp.Document` (ou uma instância `BLOB` se você estiver usando serviços da Web). Você pode passar a instância `com.adobe.idp.Document` para o serviço de Saída.

**Renderizar o formulário não interativo do PDF**

Para renderizar um formulário não interativo, transmita a instância `com.adobe.idp.Document` que foi retornada usando a API do Repositório do AEM Forms.

>[!NOTE]
>
>Dois novos métodos chamados `generatePDFOutput2` e `generatePrintedOutput2`aceitam um objeto `com.adobe.idp.Document` que contém um design de formulário. Você também pode passar um `com.adobe.idp.Document` que contenha o design do formulário para o serviço de Saída ao enviar um fluxo de impressão para uma impressora de rede.

**Executar uma ação com o fluxo de dados de formulário**

Você pode salvar o formulário não interativo como um arquivo PDF. O formulário pode ser exibido no Adobe Reader ou Acrobat.

**Consulte também**

[Enviar documentos no repositório para o serviço de saída usando a API Java](creating-document-output-streams.md#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

ResourceRepositoryClient

### Enviar documentos no repositório para o serviço de saída usando a API Java {#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api}

Envie um documento recuperado do Repositório usando o Serviço de saída e a API do repositório (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar e adobe-repository-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto de Saída e de API do cliente de Gerenciamento de documentos.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão. (Consulte [Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.
   * Crie um objeto `DocumentManagementServiceClientImpl` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Recupere o design do formulário do Repositório do AEM Forms.

   Invoque o método `readResourceContent` do objeto `ResourceRepositoryClient` e passe um valor de cadeia de caracteres que especifique o local do URI para o arquivo XDP. Por exemplo, `/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`. Esse valor é obrigatório. Este método retorna uma instância `com.adobe.idp.Document` que representa o arquivo XDP.

1. Renderize o formulário não interativo do PDF.

   Invoque o método `generatePDFOutput2` do objeto `OutputClient` e passe os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de string que especifica a raiz do conteúdo onde os recursos adicionais, como imagens, estão localizados. Por exemplo, `repository:///Applications/FormsApplication/1.0/FormsFolder/`.
   * Um objeto `com.adobe.idp.Document` que representa o design do formulário (use a instância retornada pelo método `readResourceContent` do objeto `ResourceRepositoryClient`).
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `com.adobe.idp.Document` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.

   O método `generatePDFOutput2` retorna um objeto `OutputResult` que contém os resultados da operação.

1. Execute uma ação com o fluxo de dados de formulário.

   * Recupere um objeto `com.adobe.idp.Document` que represente o formulário não interativo invocando o método `getGeneratedDoc` do objeto `OutputResult`.
   * Crie um objeto `java.io.File` que contenha os resultados da operação. Verifique se a extensão do nome do arquivo é .pdf.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo (certifique-se de usar o objeto `com.adobe.idp.Document` retornado pelo método `getGeneratedDoc`).

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo EJB): Passar um documento no Repositório do AEM Forms para o serviço de saída usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Criação de documentos do PDF usando fragmentos {#creating-pdf-documents-using-fragments}

Você pode usar os serviços Saída e Assembler para criar um fluxo de saída, como um documento do PDF, baseado em fragmentos. O serviço do Assembler monta um documento XDP baseado em fragmentos em vários arquivos XDP. O documento XDP montado é passado para o Serviço de saída, que cria um documento PDF. Embora esse fluxo de trabalho mostre um documento PDF sendo gerado, o Serviço de saída pode gerar outros tipos de saída, como ZPL, para esse fluxo de trabalho. Um documento do PDF é usado somente para fins de discussão.

A ilustração a seguir mostra esse fluxo de trabalho.

![cp_cp_outputassemblefragments](assets/cp_cp_outputassemblefragments.png)

Antes de ler *Criação de documentos do PDF usando fragmentos*, é recomendável que você se familiarize com o uso do serviço Assembler para montar vários documentos XDP. (Consulte [Montagem de vários fragmentos XDP](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments).)

>[!NOTE]
>
>Você também pode passar um design de formulário montado pelo serviço Assembler para o serviço Forms em vez do serviço Output. A principal diferença entre o serviço de saída e o serviço do Forms é que o serviço do Forms gera documentos interativos do PDF e o serviço de saída produz documentos não interativos do PDF. Além disso, o serviço Forms não pode gerar fluxos de saída com base em impressora como ZPL.

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-4}

Para criar um documento do PDF com base em fragmentos, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Criar um objeto Cliente de Saída e Assembler.
1. Use o serviço Assembler para gerar o design do formulário.
1. Use o Serviço de saída para gerar o documento do PDF.
1. Salve o documento do PDF como um arquivo do PDF.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um objeto Cliente de Saída e Assembler**

Antes de executar programaticamente uma operação da API do Serviço de saída, crie um objeto da API do Cliente de saída. Além disso, como esse fluxo de trabalho chama o serviço Assembler para criar o design do formulário, crie um objeto de API do cliente Assembler.

**Usar o serviço Assembler para gerar o design do formulário**

Use o serviço Assembler para gerar o design do formulário usando fragmentos. O serviço Assembler retorna uma instância `com.adobe.idp.Document` que contém o design do formulário.

**Usar o Serviço de saída para gerar o documento do PDF**

Você pode usar o Serviço de saída para gerar um documento PDF usando o design de formulário criado pelo serviço Assembler. Passe a instância `com.adobe.idp.Document` que o serviço do Assembler retornou para o serviço de Saída.

**Salvar o documento do PDF como um arquivo do PDF**

Depois que o serviço de saída gerar um documento PDF, você poderá salvá-lo como um arquivo PDF.

**Consulte também**

[Criar um documento do PDF com base em fragmentos usando a API Java](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-java-api)

[Criar um documento do PDF com base em fragmentos usando a API do serviço da Web](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Montagem de vários fragmentos XDP](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments)

[Criação de documentos do PDF](creating-document-output-streams.md#creating-pdf-documents)

### Criar um documento do PDF com base em fragmentos usando a API Java {#create-a-pdf-document-based-on-fragments-using-the-java-api}

Crie um documento do PDF com base em fragmentos usando a API de serviço de saída e a API de serviço do Assembler (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar, no caminho de classe do projeto Java.

1. Criar um objeto Cliente de Saída e Assembler.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.
   * Crie um objeto `AssemblerServiceClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Use o serviço Assembler para gerar o design do formulário.

   Invoque o método `invokeDDX` do objeto `AssemblerServiceClient` e passe os seguintes valores obrigatórios:

   * Um objeto `com.adobe.idp.Document` que representa o documento DDX a ser usado.
   * Um objeto `java.util.Map` que contém os arquivos XDP de entrada.
   * Um objeto `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` que especifica as opções de tempo de execução, incluindo a fonte padrão e o nível de log do trabalho.

   O método `invokeDDX` retorna um objeto `com.adobe.livecycle.assembler.client.AssemblerResult` que contém o documento XDP montado. Para recuperar o documento XDP montado, execute as seguintes ações:

   * Invoque o método `getDocuments` do objeto `AssemblerResult`. Este método retorna um objeto `java.util.Map`.
   * Repita o objeto `java.util.Map` até encontrar o objeto `com.adobe.idp.Document` resultante.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para extrair o documento XDP montado.

1. Use o Serviço de saída para gerar o documento do PDF.

   Invoque o método `generatePDFOutput2` do objeto `OutputClient` e passe os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`
   * Um valor de string que especifica a raiz do conteúdo onde os recursos adicionais, como imagens, estão localizados
   * Um objeto `com.adobe.idp.Document` que representa o design do formulário (use a instância retornada pelo serviço Assembler)
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização
   * O objeto `com.adobe.idp.Document` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário

   O método `generatePDFOutput2` retorna um objeto `OutputResult` que contém os resultados da operação

1. Salve o documento do PDF como um arquivo do PDF.

   * Recupere um objeto `com.adobe.idp.Document` que represente o documento PDF invocando o método `getGeneratedDoc` do objeto `OutputResult`.
   * Crie um objeto `java.io.File` que contenha os resultados da operação. Verifique se a extensão do nome do arquivo é .pdf.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo. (Use o objeto `com.adobe.idp.Document` que o método `getGeneratedDoc` retornou.)

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo EJB): Criação de um documento do PDF com base em fragmentos usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Início rápido (modo SOAP): Criação de um documento PDF com base em fragmentos usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Criar um documento do PDF com base em fragmentos usando a API do serviço da Web {#create-a-pdf-document-based-on-fragments-using-the-web-service-api}

Crie um documento do PDF com base em fragmentos usando a API de serviço de saída e a API de serviço do Assembler (serviço Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Use a seguinte definição WSDL para a referência de serviço associada ao serviço de Saída:

   ```java
    http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1.
   ```

   Use a seguinte definição WSDL para a referência de serviço associada ao serviço Assembler:

   ```java
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   Como o tipo de dados `BLOB` é comum a ambas as referências de serviço, qualifique totalmente o tipo de dados `BLOB` ao usá-lo. No início rápido do serviço Web correspondente, todas as `BLOB` instâncias são totalmente qualificadas.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Criar um objeto Cliente de Saída e Assembler.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * Atribua o valor da constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Repita essas etapas para o objeto `AssemblerServiceClient`.

1. Use o serviço Assembler para gerar o design do formulário.

   Invoque o método `invokeDDX` do objeto `AssemblerServiceClient` e passe os seguintes valores:

   * Um objeto `BLOB` que representa o documento DDX
   * O objeto `MyMapOf_xsd_string_To_xsd_anyType` que contém os arquivos necessários
   * Um objeto `AssemblerOptionSpec` que especifica as opções de tempo de execução

   O método `invokeDDX` retorna um objeto `AssemblerResult` que contém os resultados do trabalho e as exceções que ocorreram. Para obter o documento XDP recém-criado, execute as seguintes ações:

   * Acesse o campo `documents` do objeto `AssemblerResult`, que é um objeto `Map` que contém os documentos PDF resultantes.
   * Repita através do objeto `Map` para recuperar o design de formulário montado. Transmitir o `value` desse membro da matriz para um `BLOB`. Passar esta instância `BLOB` para o serviço de Saída.

1. Use o Serviço de saída para gerar o documento do PDF.

   Invoque o método `generatePDFOutput2` do objeto `OutputServiceClient` e passe os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de string que especifica a raiz do conteúdo onde os recursos adicionais, como imagens, estão localizados.
   * Um objeto `BLOB` que representa o design do formulário (use a instância `BLOB` retornada pelo serviço Assembler).
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `BLOB` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.
   * Um objeto de saída `BLOB` que o método `generatePDFOutput2` preenche. O método `generatePDFOutput2` preenche este objeto com metadados gerados que descrevem o documento. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).
   * Um objeto de saída `OutputResult` que contém os resultados da operação. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).

   O método `generatePDFOutput2` retorna um objeto `BLOB` que contém o formulário PDF não interativo.

1. Salve o documento do PDF como um arquivo do PDF.

   * Crie um objeto `System.IO.FileStream` invocando seu construtor. Transmita um valor de string que represente o local do arquivo do documento interativo do PDF e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `BLOB` recuperado do método `generatePDFOutput2`. Popular a matriz de bytes obtendo o valor do membro de dados `MTOM` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Imprimindo em Arquivos {#printing-to-files}

Você pode usar o serviço de Saída para imprimir fluxos como PostScript, PCL (Printer Control Language, Linguagem de Controle de Impressora) ou os seguintes formatos de rótulo em um arquivo:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Usando o Serviço de saída, você pode mesclar dados XML com um design de formulário e imprimir o formulário em um arquivo. A ilustração a seguir mostra o Serviço de saída criando arquivos de etiquetas e laser.

>[!NOTE]
>
>Para obter informações sobre como enviar fluxos de impressão para impressoras, consulte [Enviando Fluxos de Impressão para Impressoras](creating-document-output-streams.md#sending-print-streams-to-printers).

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-5}

Para imprimir em um arquivo, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de saída.
1. Fazer referência a uma fonte de dados XML.
1. Defina as opções de tempo de execução de impressão necessárias para imprimir em um arquivo.
1. Imprima o fluxo de impressão em um arquivo.
1. Recuperar os resultados da operação.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (necessário se o AEM Forms for implantado no JBoss)
* jbossall-client.jar (necessário se o AEM Forms for implantado no JBoss)

se o AEM Forms for disponibilizado em um servidor de aplicativos J2EE compatível que não seja JBoss, você deverá substituir os arquivos adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos para o servidor de aplicativos J2EE no qual o AEM Forms é disponibilizado. (Consulte [Incluindo arquivos da biblioteca AEM Forms Java](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)

**Criar um objeto de Cliente de Saída**

Antes de executar programaticamente uma operação do Serviço de saída, você deve criar um objeto cliente do Serviço de saída. Se você estiver usando a API Java, crie um objeto `OutputClient`. Se você estiver usando a API de Serviço Web de Saída, crie um objeto `OutputServiceService`.

**Referenciar uma fonte de dados XML**

Para imprimir um documento que contenha dados, você deve fazer referência a uma fonte de dados XML que contenha elementos XML para cada campo de formulário que você deseja preencher com dados. O nome do elemento XML deve corresponder ao nome do campo. Um elemento XML será ignorado se não corresponder a um campo de formulário ou se o nome do elemento XML não corresponder ao nome do campo. Não é necessário corresponder à ordem em que os elementos XML são exibidos se todos os elementos XML forem especificados.

**Definir as opções de tempo de execução de impressão necessárias para imprimir em um arquivo**

Para imprimir em um arquivo, você deve definir a opção de tempo de execução do URI de arquivo especificando o local e o nome do arquivo no qual o serviço de Saída é impresso. Por exemplo, para instruir o serviço de Saída a imprimir um arquivo PostScript chamado *MortgageForm.ps* em C:\Adobe, especifique C:\Adobe\MortgageForm.ps.

>[!NOTE]
>
>Há opções opcionais de tempo de execução que podem ser definidas. Para obter informações sobre todas as opções que podem ser definidas, consulte a referência de classe `PrintedOutputOptionsSpec` na [Referência da API do AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Imprimir o fluxo de impressão em um arquivo**

Depois de fazer referência a uma fonte de dados XML válida que contém dados de formulário e definir opções de tempo de execução de impressão, você pode chamar o serviço Saída, o que faz com que ele imprima um arquivo.

**Recuperar os resultados da operação**

Depois que o Serviço de saída executa uma operação, ele retorna vários itens de dados, como dados XML, que especificam se a operação foi bem-sucedida.

**Consulte também**

[Imprimir em arquivos usando a API Java](creating-document-output-streams.md#print-to-files-using-the-java-api)

[Imprimir em arquivos usando a API do serviço Web](creating-document-output-streams.md#print-to-files-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Imprimir em arquivos usando a API Java {#print-to-files-using-the-java-api}

Imprima em um arquivo usando a API de saída (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `java.io.FileInputStream` que represente a fonte de dados XML usada para preencher o documento usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo XML.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Defina as opções de tempo de execução de impressão necessárias para imprimir em um arquivo.

   * Crie um objeto `PrintedOutputOptionsSpec` usando seu construtor.
   * Especifique o arquivo chamando o método `setFileURI` do objeto PrintedOutputOptionsSpec e transmitindo um valor de cadeia de caracteres que representa o nome e o local do arquivo. Por exemplo, se você quiser que o serviço de Saída imprima em um arquivo do PostScript chamado MortgageForm.ps em C:\Adobe, especifique C:\\Adobe\MortgageForm.ps.
   * Especifique o número de cópias a serem impressas invocando o método `setCopies` do objeto `PrintedOutputOptionsSpec` e transmitindo um valor inteiro que represente o número de cópias.

1. Imprima o fluxo de impressão em um arquivo.

   Imprima em um arquivo chamando o método `generatePrintedOutput` do objeto `OutputClient` e passando os seguintes valores:

   * Um valor de enumeração `PrintFormat` que especifica o formato de fluxo de impressão a ser criado. Por exemplo, para criar um fluxo de impressão PostScript, passe `PrintFormat.PostScript`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de string que especifica o local dos arquivos de materiais relacionados, como arquivos de imagem.
   * Um valor de cadeia de caracteres que especifica o local do arquivo XDC a ser usado (você pode passar `null`, se tiver especificado o arquivo XDC a ser usado, usando o objeto `PrintedOutputOptionsSpec`).
   * O objeto `PrintedOutputOptionsSpec` que contém as opções de tempo de execução necessárias para imprimir em um arquivo.
   * O objeto `com.adobe.idp.Document` que contém a fonte de dados XML que contém dados de formulário.

   O método `generatePrintedOutput` retorna um objeto `OutputResult` que contém os resultados da operação.

   >[!NOTE]
   >
   >O método `getRecordLevelMetaDataList` do objeto `OutputResult` retorna `null`.

1. Recuperar os resultados da operação.

   * Crie um objeto `com.adobe.idp.Document` que represente o status do método `generatePrintedOutput` invocando o método `getStatusDoc` do objeto `OutputResult` (o objeto `OutputResult` foi retornado pelo método `generatePrintedOutput`).
   * Crie um objeto `java.io.File` que conterá os resultados da operação. Certifique-se de que a extensão do arquivo seja XML.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo (certifique-se de usar o objeto `com.adobe.idp.Document` retornado pelo método `getStatusDoc`).

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo SOAP): impressão em um arquivo usando a API do Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-printing-to-a-file-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Imprimir em arquivos usando a API do serviço Web {#print-to-files-using-the-web-service-api}

Imprima em um arquivo usando a API de saída (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar dados de formulário.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que especifica o local do arquivo XML que contém dados de formulário.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `binaryData` com o conteúdo da matriz de bytes.

1. Defina as opções de tempo de execução de impressão necessárias para imprimir em um arquivo.

   * Crie um objeto `PrintedOutputOptionsSpec` usando seu construtor.
   * Especifique o arquivo atribuindo um valor de cadeia de caracteres que represente o local e o nome do arquivo ao membro de dados `fileURI` do objeto `PrintedOutputOptionsSpec`. Por exemplo, se você deseja que o Serviço de saída imprima em um arquivo PostScript chamado *MortgageForm.ps* em C:\Adobe, especifique C:\\Adobe\MortgageForm.ps.
   * Especifique o número de cópias a serem impressas atribuindo um valor inteiro que represente o número de cópias para os membros de dados `copies` do objeto `PrintedOutputOptionsSpec`.

1. Imprima o fluxo de impressão em um arquivo.

   Imprima em um arquivo chamando o método `generatePrintedOutput` do objeto `OutputServiceService` e passando os seguintes valores:

   * Um valor de enumeração `PrintFormat` que especifica o formato de fluxo de impressão a ser criado. Por exemplo, para criar um fluxo de impressão PostScript, passe `PrintFormat.PostScript`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de string que especifica o local dos arquivos de materiais relacionados, como arquivos de imagem.
   * Um valor de cadeia de caracteres que especifica o local do arquivo XDC a ser usado (você pode passar `null`, se tiver especificado o arquivo XDC a ser usado, usando o objeto `PrintedOutputOptionsSpec`).
   * O objeto `PrintedOutputOptionsSpec` que contém as opções de tempo de execução de impressão necessárias para imprimir em um arquivo.
   * O objeto `BLOB` que contém a fonte de dados XML que contém dados de formulário.
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com metadados gerados que descrevem o documento. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com os dados do resultado. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)
   * Um objeto `OutputResult` que contém os resultados da operação. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)

1. Recuperar os resultados da operação.

   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa um local de arquivo XML que contém dados de resultado. Certifique-se de que a extensão do arquivo seja XML.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` que foi preenchido com dados de resultado pelo método `generatePDFOutput` do objeto `OutputServiceService` (o oitavo parâmetro). Popular a matriz de bytes obtendo o valor do membro de dados `MTOM` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes no arquivo XML invocando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Enviando fluxos de impressão para impressoras {#sending-print-streams-to-printers}

Você pode usar o serviço de Saída para enviar fluxos de impressão, como PostScript, PCL (Printer Control Language, Linguagem de Controle de Impressora) ou os seguintes formatos de etiqueta para impressoras de rede:

* Zebra - ZPL
* Intermec - IPL
* Datamax - DPL
* TecToshiba - TPCL

Usando o Serviço de saída, você pode mesclar dados XML com um design de formulário e gerar a saída do formulário como um fluxo de impressão. Por exemplo, você pode criar um fluxo de impressão PostScript e enviá-lo para uma impressora de rede. A ilustração a seguir mostra o serviço de Saída enviando fluxos de impressão para impressoras de rede.

>[!NOTE]
>
>Para demonstrar como enviar um fluxo de impressão para uma impressora de rede, esta seção envia um fluxo de impressão PostScript para uma impressora de rede usando o protocolo de impressora SharedPrinter.

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-6}

Para enviar um fluxo de impressão para uma impressora de rede, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de saída.
1. Fazer referência a uma fonte de dados XML.
1. Definir opções de tempo de execução de impressão
1. Recupere um documento para imprimir.
1. Envie o documento para uma impressora de rede.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (obrigatório se o AEM Forms for implantado no JBoss)
* jbossall-client.jar (obrigatório se o AEM Forms for implantado no JBoss)

se o AEM Forms for disponibilizado em um servidor de aplicativos J2EE compatível que não seja JBoss, você deverá substituir os arquivos adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos para o servidor de aplicativos J2EE no qual o AEM Forms é disponibilizado.

**Criar um objeto de Cliente de Saída**

Antes de executar programaticamente uma operação do Serviço de saída, crie um objeto cliente do Serviço de saída. Se você estiver usando a API Java, crie um objeto `OutputClient`. Se você estiver usando a API de Serviço Web de Saída, crie um objeto `OutputServiceClient`.

**Referenciar uma fonte de dados XML**

Para imprimir um documento que contenha dados, você deve fazer referência a uma fonte de dados XML que contenha elementos XML para cada campo de formulário que você deseja preencher com dados. O nome do elemento XML deve corresponder ao nome do campo. Um elemento XML será ignorado se não corresponder a um campo de formulário ou se o nome do elemento XML não corresponder ao nome do campo. Não é necessário corresponder à ordem em que os elementos XML são exibidos se todos os elementos XML forem especificados.

**Definir opções de tempo de execução de impressão**

É possível definir as opções de tempo de execução ao enviar um fluxo de impressão para uma impressora, incluindo as seguintes opções:

* **Cópias**: especifica o número de cópias a serem enviadas para a impressora. O valor padrão é 1.
* **Grampeamento**: uma opção XCI é definida quando um grampeador é usado. Esta opção pode ser especificada no modelo de configuração pelo elemento de grampo e é usada somente para impressoras PS e PCL.
* **OutputJog**: uma opção XCI é definida quando as páginas de saída devem ser ajustadas (deslocadas fisicamente na bandeja de saída). Esta opção é somente para impressoras PS e PCL.
* **OutputBin**: valor XCI usado para habilitar o driver de impressão para selecionar o compartimento de saída apropriado.

>[!NOTE]
>
>Para obter informações sobre todas as opções de tempo de execução que você pode definir, consulte a referência de classe `PrintedOutputOptionsSpec`.

**Recuperar um documento para impressão**

Recupere um fluxo de impressão para enviar a uma impressora. Por exemplo, você pode recuperar um arquivo PostScript e enviá-lo para uma impressora.

Você pode optar por enviar um arquivo PDF se a impressora for compatível com o PDF. No entanto, um problema ao enviar um documento do PDF para uma impressora é que cada fabricante de impressora tem uma implementação diferente do interpretador PDF. Ou seja, alguns fabricantes de impressão usam a interpretação Adobe PDF, mas isso depende da impressora. Outras impressoras têm seu próprio interpretador PDF. Como resultado, os resultados da impressão podem variar.

Outra limitação do envio de um documento PDF para uma impressora é que ele apenas imprime; ele não pode acessar duplex, seleção de bandeja de papel e grampeamento, exceto pelas configurações da impressora.

Para recuperar um documento para impressão, use o método `generatePrintedOutput`. A tabela a seguir especifica os tipos de conteúdo definidos para um determinado fluxo de impressão ao usar o método `generatePrintedOutput`.

<table>
 <thead>
  <tr>
   <th><p>Formato de impressão </p></th>
   <th><p>Descrição</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>DPL </p></td>
   <td><p>Cria um fluxo de saída xdc padrão ou personalizado dpl203.xdc.</p></td>
  </tr>
  <tr>
   <td><p>DPL300DPI </p></td>
   <td><p>Cria um fluxo de saída DPL 300 DPI.</p></td>
  </tr>
  <tr>
   <td><p>DPL406DPI </p></td>
   <td><p>Cria um fluxo de saída DPL 400 DPI.</p></td>
  </tr>
  <tr>
   <td><p>DPL600DPI </p></td>
   <td><p>Cria um fluxo de saída DPL 600 DPI.</p></td>
  </tr>
  <tr>
   <td><p>GenericColorPCL </p></td>
   <td><p>Cria um fluxo de saída Generic Color PCL (5c).</p></td>
  </tr>
  <tr>
   <td><p>GenericPSLevel3 </p></td>
   <td><p>Cria um fluxo de saída genérico do PostScript nível 3.</p></td>
  </tr>
  <tr>
   <td><p>IPL </p></td>
   <td><p>Cria um fluxo de saída IPL personalizado.</p></td>
  </tr>
  <tr>
   <td><p>IPL300DPI </p></td>
   <td><p>Cria um fluxo de saída IPL 300 DPI.</p></td>
  </tr>
  <tr>
   <td><p>IPL400DPI </p></td>
   <td><p>Cria um fluxo de saída IPL 400 DPI.</p></td>
  </tr>
  <tr>
   <td><p>PCL </p></td>
   <td><p>Cria um fluxo de saída PCL monocromático genérico (5e).</p></td>
  </tr>
  <tr>
   <td><p>PostScript </p></td>
   <td><p>Cria um fluxo de saída genérico do PostScript nível 2.</p></td>
  </tr>
  <tr>
   <td><p>TPCL </p></td>
   <td><p>Cria um fluxo de saída TPCL personalizado.</p></td>
  </tr>
  <tr>
   <td><p>TPCL305DPI </p></td>
   <td><p>Cria um fluxo de saída TPCL 305 DPI.</p></td>
  </tr>
  <tr>
   <td><p>TPCL600DPI </p></td>
   <td><p>Cria um fluxo de saída TPCL 600 DPI.</p></td>
  </tr>
  <tr>
   <td><p>ZPL </p></td>
   <td><p>Cria um fluxo de saída ZPL 203 DPI.</p></td>
  </tr>
  <tr>
   <td><p>ZPL300DPI </p></td>
   <td><p>Cria um fluxo de saída ZPL 300 DPI.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Você também pode enviar um fluxo de impressão para uma impressora usando o método `generatePrintedOutput2`. No entanto, os inícios rápidos associados à seção Envio de Fluxos de Impressão para Impressoras usam o método `generatePrintedOutput`.

**Enviar o fluxo de impressão para uma impressora de rede**

Depois de recuperar um documento para impressão, você pode chamar o Serviço de saída, o que faz com que ele envie um fluxo de impressão para uma impressora de rede. Para que o Serviço de saída localize a impressora com êxito, você deve especificar o servidor de impressão e o nome da impressora. Além disso, você também deve especificar o protocolo de impressão.

>[!NOTE]
>
>Se o PDFG estiver instalado no Forms Server e o servidor for executado no Windows Server 2008, não será possível usar a propriedade SharedPrinter. Nessa situação, use um protocolo de impressora diferente.

>[!NOTE]
>
>Se você estiver usando uma impressora de rede e o mecanismo de acesso for SharedPrinter, será necessário especificar o caminho de rede completo da impressora.Envie um fluxo de impressão para uma impressora de rede usando a API Java

Envie um fluxo de impressão para uma impressora de rede usando a API de saída (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar, no caminho de classe do projeto Java.

1. Criar um objeto do Cliente de saída

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Fazer referência a uma fonte de dados XML

   * Crie um objeto `java.io.FileInputStream` que represente a fonte de dados XML usada para preencher o documento usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo XML.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Definir opções de tempo de execução de impressão

   Crie um objeto `PrintedOutputOptionsSpec` que represente opções de tempo de execução de impressão. Por exemplo, você pode especificar o número de cópias a serem impressas chamando o método `setCopies` do objeto `PrintedOutputOptionsSpec`.

   >[!NOTE]
   >
   >Você não pode definir o valor de paginação usando o método `setPagination` do objeto `PrintedOutputOptionsSpec` se estiver gerando um fluxo de impressão ZPL. Da mesma forma, não é possível definir as seguintes opções para um fluxo de impressão ZPL: OutputJog, PageOffset e Staple. O método `setPagination` não é válido para geração PostScript. É válido apenas para a geração PCL.

1. Recuperar um documento para imprimir

   * Recupere um documento para impressão invocando o método `generatePrintedOutput` do objeto `OutputClient` e passando os seguintes valores:

      * Um valor de enumeração `PrintFormat` que especifica o fluxo de impressão. Por exemplo, para criar um fluxo de impressão PostScript, passe `PrintFormat.PostScript`.
      * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
      * Um valor de string que especifica o local dos arquivos de materiais relacionados, como arquivos de imagem.
      * Um valor de cadeia de caracteres que especifica o local do arquivo XDC a ser usado.
      * O objeto `PrintedOutputOptionsSpec` que contém as opções de tempo de execução necessárias para imprimir em um arquivo.
      * O objeto `com.adobe.idp.Document` que representa a fonte de dados XML que contém dados de formulário a serem mesclados com o design do formulário.

     Este método retorna um objeto `OutputResult` que contém os resultados da operação.

   * Crie um objeto `com.adobe.idp.Document` para enviar à impressora invocando o método `getGeneratedDoc` do objeto `OutputResult`. Este método retorna um objeto `com.adobe.idp.Document`.

1. Enviar o fluxo de impressão para uma impressora de rede

   Envie o fluxo de impressão para uma impressora de rede, chamando o método `sendToPrinter` do objeto `OutputClient` e transmitindo os seguintes valores:

   * Um objeto `com.adobe.idp.Document` que representa o fluxo de impressão a ser enviado para a impressora.
   * Um valor de enumeração `PrinterProtocol` que especifica o protocolo de impressora a ser usado. Por exemplo, para especificar o protocolo SharedPrinter, passe `PrinterProtocol.SharedPrinter`.
   * Um valor de string que especifica o nome do servidor de impressão. Por exemplo, supondo que o nome do servidor de impressão seja PrintServer1, passe `\\\PrintSever1`.
   * Um valor de cadeia de caracteres que especifica o nome da impressora. Por exemplo, supondo que o nome da impressora seja Printer1, passe `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >O método `sendToPrinter` foi adicionado à API do AEM Forms na versão 8.2.1.

### Enviar um fluxo de impressão para uma impressora usando a API do serviço Web {#send-a-print-stream-to-a-printer-using-the-web-service-api}

Envie um fluxo de impressão para uma impressora de rede usando a API de saída (serviço Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar dados de formulário.
   * Crie um objeto `System.IO.FileStream` invocando seu construtor. Transmita um valor de cadeia de caracteres que especifique o local do arquivo XML que contém dados de formulário.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Determine o comprimento da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo seu campo `MTOM` com o conteúdo da matriz de bytes.

1. Definir opções de tempo de execução de impressão.

   Crie um objeto `PrintedOutputOptionsSpec` usando seu construtor. Por exemplo, você pode especificar o número de cópias a serem impressas atribuindo um valor inteiro que representa o número de cópias para o membro de dados `copies` do objeto `PrintedOutputOptionsSpec`.

   >[!NOTE]
   >
   >Você não pode definir o valor de paginação usando o membro de dados `pagination` do objeto `PrintedOutputOptionsSpec` se estiver gerando um fluxo de impressão ZPL. Da mesma forma, não é possível definir as seguintes opções para um fluxo de impressão ZPL: OutputJog, PageOffset e Staple. O membro de dados `pagination` não é válido para geração PostScript. É válido apenas para a geração PCL.

1. Recupere um documento para imprimir.

   * Recupere um documento para impressão invocando o método `generatePrintedOutput` do objeto `OutputServiceService` e passando os seguintes valores:

      * Um valor de enumeração `PrintFormat` que especifica o fluxo de impressão. Por exemplo, para criar um fluxo de impressão PostScript, passe `PrintFormat.PostScript`.
      * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
      * Um valor de string que especifica o local dos arquivos de materiais relacionados, como arquivos de imagem.
      * Um valor de cadeia de caracteres que especifica o local do arquivo XDC a ser usado.
      * O objeto `PrintedOutputOptionsSpec` que contém as opções de tempo de execução de impressão usadas ao enviar um fluxo de impressão para uma impressora de rede.
      * O objeto `BLOB` que contém a fonte de dados XML que contém dados de formulário.
      * Um objeto `BLOB` que é preenchido pelo método `generatePrintedOutput`. O método `generatePrintedOutput` preenche este objeto com metadados gerados que descrevem o documento. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)
      * Um objeto `BLOB` que é preenchido pelo método `generatePrintedOutput`. O método `generatePrintedOutput` preenche este objeto com os dados do resultado. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)
      * Um objeto `OutputResult` que contém os resultados da operação. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)

   * Crie um objeto `BLOB` para enviar à impressora obtendo o valor do método `generatedDoc` do objeto `OutputResult`. Este método retorna um objeto `BLOB` que contém dados PostScript retornados pelo método `generatePrintedOutput`.

1. Envie o fluxo de impressão para uma impressora de rede.

   Envie o fluxo de impressão para uma impressora de rede, chamando o método `sendToPrinter` do objeto `OutputClient` e transmitindo os seguintes valores:

   * Um objeto `BLOB` que representa o fluxo de impressão a ser enviado para a impressora.
   * Um valor de enumeração `PrinterProtocol` que especifica o protocolo de impressora a ser usado. Por exemplo, para especificar o protocolo SharedPrinter, passe `PrinterProtocol.SharedPrinter`.
   * Um valor `bool` que especifica se o valor do parâmetro anterior deve ser usado. Passe o valor `true`. (Este valor de parâmetro é necessário somente para a invocação do serviço Web.)
   * Um valor de string que especifica o nome do servidor de impressão. Por exemplo, supondo que o nome do servidor de impressão seja PrintServer1, passe `\\\PrintSever1`.
   * Um valor de cadeia de caracteres que especifica o nome da impressora. Por exemplo, supondo que o nome da impressora seja Printer1, passe `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >O método `sendToPrinter` foi adicionado à API do AEM Forms na versão 8.2.1.

## Criação de vários arquivos de saída {#creating-multiple-output-files}

O Serviço de saída pode criar documentos separados para cada registro em uma fonte de dados XML ou em um único arquivo que contenha todos os registros (essa funcionalidade é o padrão). Por exemplo, suponha que dez registros estejam localizados em uma fonte de dados XML e você instrua o serviço de Saída a criar documentos separados do PDF (ou outros tipos de saída) para cada registro usando a API de Serviço de Saída. Como resultado, o Serviço de saída gera dez documentos do PDF. (Em vez de criar documentos, você pode enviar vários fluxos de impressão para uma impressora.)

A ilustração a seguir também mostra o Serviço de saída processando um arquivo de dados XML que contém vários registros. No entanto, suponha que você instrua o Serviço de saída a criar um único documento do PDF que contenha todos os registros de dados. Nessa situação, o Serviço de saída gera um documento que contém todos os registros.

A ilustração a seguir mostra o Serviço de saída processando um arquivo de dados XML que contém vários registros. Suponha que você instrua o Serviço de saída a criar um documento do PDF separado para cada registro de dados. Nessa situação, o Serviço de saída gera um documento do PDF separado para cada registro de dados.

![cm_outputbatchmany](assets/cm_outputbatchmany.png)

Os dados XML a seguir mostram um exemplo de um arquivo de dados que contém três registros de dados.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <batch>
 <LoanRecord>
     <mortgageAmount>500000</mortgageAmount>
     <lastName>Blue</lastName>
     <firstName>Tony</firstName>
     <SSN>555666777</SSN>
     <PositionTitle>Product Manager</PositionTitle>
     <Address>555 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>TBlue@NoMailServer.com</Email>
     <PhoneNum>555-7418</PhoneNum>
     <FaxNum>555-9981</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 <LoanRecord>
     <mortgageAmount>300000</mortgageAmount>
     <lastName>White</lastName>
     <firstName>Sam</firstName>
     <SSN>555666222</SSN>
     <PositionTitle>Program Manager</PositionTitle>
     <Address>557 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>SWhite@NoMailServer.com</Email>
     <PhoneNum>555-7445</PhoneNum>
     <FaxNum>555-9986</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 <LoanRecord>
     <mortgageAmount>700000</mortgageAmount>
     <lastName>Green</lastName>
     <firstName>Steve</firstName>
     <SSN>55566688</SSN>
     <PositionTitle>Project Manager</PositionTitle>
     <Address>445 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>SGreeb@NoMailServer.com</Email>
     <PhoneNum>555-2211</PhoneNum>
     <FaxNum>555-2221</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 </batch>
```

Observe que o elemento XML que inicia e termina cada registro de dados é `LoanRecord`. Esse elemento XML é referenciado pela lógica do aplicativo que gera vários arquivos.

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-7}

Para criar vários arquivos PDF com base em uma origem de dados XML, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de saída.
1. Fazer referência a uma fonte de dados XML.
1. Definir opções de tempo de execução do PDF.
1. Definir opções de tempo de execução de renderização.
1. Gerar vários arquivos do PDF.
1. Recuperar os resultados da operação.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (necessário se o AEM Forms for implantado no JBoss)
* jbossall-client.jar (necessário se o AEM Forms for implantado no JBoss)

se o AEM Forms for disponibilizado em um servidor de aplicativos J2EE compatível que não seja JBoss, você deverá substituir os arquivos adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos para o servidor de aplicativos J2EE no qual o AEM Forms é disponibilizado.

**Criar um objeto de Cliente de Saída**

Antes de executar programaticamente uma operação do Serviço de saída, você deve criar um objeto cliente do Serviço de saída. Se você estiver usando a API Java, crie um objeto `OutputClient`. Se você estiver usando a API de Serviço Web de Saída, crie um objeto `OutputServiceService`.

**Referenciar uma fonte de dados XML**

Faça referência a uma fonte de dados XML que contém vários registros. Um elemento XML deve ser usado para separar os registros de dados. Por exemplo, na fonte de dados XML de exemplo mostrada anteriormente nesta seção, o elemento XML que separa registros de dados é denominado `LoanRecord`.

Um elemento XML deve existir para cada campo de formulário que você deseja preencher com dados. O nome do elemento XML deve corresponder ao nome do campo. Um elemento XML será ignorado se não corresponder a um campo de formulário ou se o nome do elemento XML não corresponder ao nome do campo. Não é necessário corresponder à ordem em que os elementos XML são exibidos se todos os elementos XML forem especificados.

**Definir opções de tempo de execução do PDF**

Defina as seguintes opções de tempo de execução para que o serviço de Saída crie com êxito vários arquivos com base em uma fonte de dados XML:

* **Muitos Arquivos**: especifica se o serviço de Saída cria um único documento ou vários documentos. Você pode especificar verdadeiro ou falso. Para criar um documento separado para cada registro de dados na fonte de dados XML, especifique verdadeiro.
* **URI do Arquivo**: especifica o local dos arquivos gerados pelo serviço de Saída. Por exemplo, suponha que você especifique C:\\Adobe\forms\Loan.pdf. Nessa situação, o serviço de saída cria um arquivo chamado Loan.pdf e coloca o arquivo na pasta C:\\Adobe\forms. Quando existem vários arquivos, os nomes dos arquivos são Loan0001.pdf, Loan0002.pdf, Loan0003.pdf e assim por diante. Se você especificar um local de arquivo, os arquivos serão colocados no servidor e não no computador cliente.
* **Nome do Registro**: especifica o nome do elemento XML na fonte de dados que separa os registros de dados. Por exemplo, na fonte de dados XML de exemplo mostrada anteriormente nesta seção, o elemento XML que separa registros de dados é chamado de `LoanRecord`. (Em vez de definir a opção de tempo de execução Nome do registro, você pode definir o Nível do registro atribuindo a ele um valor numérico que indica o nível do elemento que contém registros de dados. No entanto, você pode definir somente o Nome do registro ou o Nível do registro. Não é possível definir ambos os valores.)

**Definir opções de tempo de execução de renderização**

É possível definir opções de tempo de execução de renderização ao criar vários arquivos. Embora essas opções não sejam obrigatórias (ao contrário das opções de tempo de execução de saída, que são obrigatórias), você pode executar tarefas como melhorar o desempenho do serviço de Saída. Por exemplo, você pode armazenar em cache o design do formulário que o serviço de Saída usa para melhorar o desempenho.

Quando o Serviço de saída processa registros em lote, ele lê dados que contêm vários registros de maneira incremental. Ou seja, o Serviço de saída lê os dados na memória e libera os dados conforme o lote de registros é processado. O serviço de saída carrega dados de maneira incremental quando uma das duas opções de tempo de execução é definida. Se você definir a opção de tempo de execução Nome do registro, o serviço de Saída lerá os dados de maneira incremental. Da mesma forma, se você definir a opção de tempo de execução Record Level como 2 ou superior, o serviço Output lerá os dados de maneira incremental.

Você pode controlar se o Serviço de saída executa o carregamento incremental usando o método `PDFOutputOptionsSpec` ou `setLazyLoading` do objeto `PrintedOutputOptionSpec`. Você pode passar o valor `false` para esse método que desativa o carregamento incremental.

**Gerar vários arquivos PDF**

Depois de fazer referência a uma fonte de dados XML válida que contém vários registros de dados e definir opções de tempo de execução, você pode chamar o Serviço de saída, o que faz com que ele gere vários arquivos. Ao gerar vários registros, o método `getGeneratedDoc` do objeto `OutputResult` retorna `null`.

**Recuperar os resultados da operação**

Depois que o Serviço de saída executa uma operação, ele retorna dados XML que especificam se a operação foi bem-sucedida. O XML a seguir é retornado pelo serviço de Saída. Nessa situação, o Serviço de saída gerou 42 documentos.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <printResult>
 <status>0</status>
 <requestId>4ad85f9e2</requestId>
 <context/>
 <messages>
 <message>Printed all 42 records successfully.</message>
 </messages>
 <printSpec>
 <input>
 <validated>true</validated>
 <dataFile recordIdField="" recordLevel="0" recordName="LoanRecord"/>
 <sniffRules lookAhead="300"/>
 <formDesign>Loan.xdp</formDesign>
 <contentRoot>C:\Adobe</contentRoot>
 <metadata-spec record="false"/>
 </input>
 <output>
 <format>PDF</format>
 <fileURI>C:\Adobe\forms\Loan.pdf</fileURI>
 <optionString>cacheenabled=true&padebug=false&linearpdf=false&pdfarevisionnumber=1&pdfaconformance=A&taggedpdf=false&TransactionTimeOut=180</optionString>
 <waitForResponse>true</waitForResponse>
 <outputStream>multiple</outputStream>
 </output>
 </printSpec>
 </printResult>
```

**Consulte também**

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Criar vários arquivos PDF usando a API Java {#create-multiple-pdf-files-using-the-java-api}

Crie vários arquivos PDF usando a API de saída (Java):

1. Incluir arquivos de projeto&quot;

   Inclua arquivos JAR do cliente, como adobe-output-client.jar, no caminho de classe do projeto Java.

1. Criar um objeto do Cliente de saída

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Fazer referência a uma fonte de dados XML

   * Crie um objeto `java.io.FileInputStream` que represente a fonte de dados XML que contém vários registros usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo XML.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Definir opções de tempo de execução do PDF

   * Crie um objeto `PDFOutputOptionsSpec` usando seu construtor.
   * Defina a opção Muitos Arquivos invocando o método `setGenerateManyFiles` do objeto `PDFOutputOptionsSpec`. Por exemplo, passe o valor `true` para instruir o serviço de Saída a criar um arquivo PDF separado para cada registro na fonte de dados XML. (Se você passar `false`, o Serviço de saída gerará um único documento do PDF que conterá todos os registros).
   * Defina a opção File URI invocando o método `setFileUri` do objeto `PDFOutputOptionsSpec` e transmitindo um valor de cadeia de caracteres que especifica o local dos arquivos gerados pelo serviço de Saída. A opção File URI é relativa ao servidor de aplicativos J2EE que hospeda o AEM Forms, não ao computador cliente.
   * Defina a opção Nome do Registro invocando o método `setRecordName` do objeto `OutputOptionsSpec` e transmitindo um valor de cadeia de caracteres que especifica o nome do elemento XML na fonte de dados que separa os registros de dados. (Por exemplo, considere a fonte de dados XML mostrada anteriormente nesta seção. O nome do elemento XML que separa registros de dados é LoanRecord).

1. Definir opções de tempo de execução de renderização

   * Crie um objeto `RenderOptionsSpec` usando seu construtor.
   * Armazene em cache o design do formulário para melhorar o desempenho do Serviço de saída, chamando o `setCacheEnabled` do objeto `RenderOptionsSpec` e passando um valor `Boolean` de `true`.

1. Gerar vários arquivos do PDF

   Gere vários arquivos PDF chamando o método `generatePDFOutput` do objeto `OutputClient` e transmitindo os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de cadeia de caracteres que especifica a raiz do conteúdo onde o design do formulário está localizado.
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `com.adobe.idp.Document` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.

   O método `generatePDFOutput` retorna um objeto `OutputResult` que contém os resultados da operação.

1. Recuperar os resultados da operação

   * Crie um objeto `java.io.File` que represente um arquivo XML que conterá os resultados do método `generatePDFOutput`. Verifique se a extensão do nome do arquivo é .xml.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo (certifique-se de usar o objeto `com.adobe.idp.Document` retornado pelo método `applyUsageRights`).

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo EJB): criação de vários arquivos PDF usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-multiple-pdf-files-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Criar vários arquivos PDF usando a API do serviço Web {#create-multiple-pdf-files-using-the-web-service-api}

Crie vários arquivos PDF usando a API de saída (serviço Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar dados de formulário que contêm vários registros.
   * Crie um objeto `System.IO.FileStream` invocando seu construtor. Transmita um valor de string que represente o local do arquivo XML que contém vários registros.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo seu campo `MTOM` com o conteúdo da matriz de bytes.

1. Definir opções de tempo de execução do PDF.

   * Crie um objeto `PDFOutputOptionsSpec` usando seu construtor.
   * Defina a opção Muitos Arquivos atribuindo um valor booleano ao membro de dados `generateManyFiles` do objeto `OutputOptionsSpec`. Por exemplo, atribua o valor `true` a esse membro de dados para instruir o serviço de Saída a criar um arquivo PDF separado para cada registro na fonte de dados XML. (Se você atribuir `false` a esse membro de dados, o Serviço de saída gerará um único PDF que contém todos os registros).
   * Defina a opção de URI de arquivo atribuindo um valor de cadeia de caracteres que especifique o local do(s) arquivo(s) gerado(s) pelo serviço de Saída ao membro de dados `fileURI` do objeto `OutputOptionsSpec`. A opção File URI é relativa ao servidor de aplicativos J2EE que hospeda o AEM Forms, não ao computador cliente.
   * Defina a opção de nome de registro atribuindo um valor de cadeia de caracteres que especifique o nome do elemento XML na fonte de dados que separa os registros de dados para o membro de dados `recordName` do objeto `OutputOptionsSpec`.
   * Defina a opção copies atribuindo um valor inteiro que especifica o número de cópias que o serviço de Saída gera para o membro de dados `copies` do objeto `OutputOptionsSpec`.

1. Definir opções de tempo de execução de renderização.

   * Crie um objeto `RenderOptionsSpec` usando seu construtor.
   * Armazene em cache o design do formulário para melhorar o desempenho do serviço de Saída atribuindo o valor `true` ao membro de dados `cacheEnabled` do objeto `RenderOptionsSpec`.

1. Gerar vários arquivos do PDF.

   Crie vários arquivos PDF chamando o método `generatePDFOutput` do objeto `OutputServiceService` e transmitindo os seguintes valores:

   * Um valor de enumeração TransformationFormat. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de cadeia de caracteres que especifica a raiz do conteúdo onde o design do formulário está localizado.
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `BLOB` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com metadados gerados que descrevem o documento.
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com os dados do resultado.
   * Um objeto `OutputResult` que contém os resultados da operação.

1. Recuperar os resultados da operação

   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa um local de arquivo XML que contém dados de resultado. Verifique se a extensão do nome do arquivo é .xml.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` que foi preenchido com dados de resultado pelo método `generatePDFOutput` do objeto `OutputServiceService` (o oitavo parâmetro). Popular a matriz de bytes obtendo o valor do membro de dados `binaryData` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes no arquivo XML invocando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Criação de regras de pesquisa {#creating-search-rules}

Você pode criar regras de pesquisa que resultam no serviço de Saída examinando dados de entrada e usando diferentes designs de formulário com base no conteúdo dos dados para gerar a saída. Por exemplo, se o texto *hipoteca* estiver localizado nos dados de entrada, o serviço de Saída poderá usar um design de formulário chamado Hipoteca.xdp. Da mesma forma, se o texto *automobile* estiver nos dados de entrada, o serviço de Saída poderá usar um design de formulário salvo como AutomobileLoan.xdp. Embora o Serviço de saída possa gerar diferentes tipos de saída, esta seção presume que o Serviço de saída gera um arquivo PDF. O diagrama a seguir mostra o Serviço de saída que gera um arquivo PDF processando um arquivo de dados XML e usando um dos vários designs de formulário.

Além disso, o Serviço de saída é capaz de gerar pacotes de documentos, em que vários registros são fornecidos no conjunto de dados e cada registro é correspondido a um design de formulário, e um único documento é gerado composto de vários designs de formulário.

![cs_outputbatchmanyformdesigns2](assets/cs_outputbatchmanyformdesigns2.png)

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-8}

Para instruir o Serviço de saída a usar regras de pesquisa ao gerar um documento, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de saída.
1. Fazer referência a uma fonte de dados XML.
1. Defina as regras de pesquisa.
1. Definir opções de tempo de execução do PDF.
1. Definir opções de tempo de execução de renderização.
1. Gere um documento do PDF.
1. Recuperar os resultados da operação.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao classpath do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (obrigatório se o AEM Forms for implantado no JBoss)
* jbossall-client.jar (obrigatório se o AEM Forms for implantado no JBoss)

se o AEM Forms for disponibilizado em um servidor de aplicativos J2EE compatível que não seja JBoss, você deverá substituir adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos para o servidor de aplicativos J2EE no qual o AEM Forms é disponibilizado.

**Criar um objeto de Cliente de Saída**

Antes de executar programaticamente uma operação do Serviço de saída, você deve criar um objeto cliente do Serviço de saída.

**Referenciar uma fonte de dados XML**

Um elemento XML deve existir para cada campo de formulário que você deseja preencher com dados. O nome do elemento XML deve corresponder ao nome do campo. Um elemento XML será ignorado se não corresponder a um campo de formulário ou se o nome do elemento XML não corresponder ao nome do campo. Não é necessário corresponder à ordem em que os elementos XML são exibidos, desde que todos os elementos XML sejam especificados.

**Definir regras de pesquisa**

Para definir regras de pesquisa, defina um ou mais padrões de texto que os serviços de Saída pesquisam nos dados de entrada. Para cada padrão de texto definido, especifique um design de formulário correspondente que será usado se o padrão de texto estiver localizado. Se um padrão de texto estiver localizado, o serviço de Saída usará o design de formulário correspondente para gerar a saída. Um exemplo de padrão de texto é *hipoteca*.

>[!NOTE]
>
>Se os padrões de texto não estiverem localizados, o formulário padrão será usado. Verifique se todos os designs de formulário que você usa estão na raiz do conteúdo.

**Definir opções de tempo de execução do PDF**

Defina as seguintes opções de tempo de execução do PDF para que o serviço de Saída crie com êxito um documento do PDF com base em vários designs de formulário:

* **URI do Arquivo**: especifica o nome e o local do arquivo PDF gerado pelo serviço de Saída.
* **Regras**: especifica as regras que você definiu.
* **LookAHead**: especifica o número de bytes a serem usados desde o início do arquivo de dados de entrada para verificar os padrões de texto definidos. O padrão é 500 bytes.

**Definir opções de tempo de execução de renderização**

Ao criar arquivos PDF, é possível definir opções de tempo de execução de renderização. Embora essas opções não sejam necessárias (ao contrário das opções de tempo de execução do PDF), você pode executar tarefas como melhorar o desempenho do serviço de Saída. Por exemplo, você pode armazenar em cache o design do formulário que o serviço de Saída usa para melhorar o desempenho.

**Gerar um documento do PDF**

Depois de fazer referência a uma fonte de dados XML válida e definir opções de tempo de execução, você pode chamar o serviço de Saída, o que resultará na geração de um documento do PDF. Se o serviço de Saída localizar um padrão de texto especificado nos dados de entrada, ele usará o design de formulário correspondente. Se um padrão de texto não for usado, o serviço de Saída usará o design de formulário padrão.

**Recuperar os resultados da operação**

Depois que o Serviço de saída executa uma operação, ele retorna dados XML que especificam se a operação foi bem-sucedida.

**Consulte também**

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Criar regras de pesquisa usando a API Java {#create-search-rules-using-the-java-api}

Crie regras de pesquisa usando a API de saída (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `java.io.FileInputStream` que represente a fonte de dados XML usada para preencher o documento PDF usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo XML.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Defina as regras de pesquisa.

   * Crie um objeto `Rule` usando seu construtor.
   * Defina um padrão de texto chamando o método `setPattern` do objeto `Rule` e transmitindo um valor de cadeia de caracteres que especifica um padrão de texto.
   * Defina o design do formulário correspondente invocando o método `setForm` do objeto `Rule`. Transmita um valor de cadeia de caracteres que especifique o nome do design do formulário.

   >[!NOTE]
   >
   >Para cada padrão de texto que deseja definir, repita as três subetapas anteriores.

   * Crie um objeto `java.util.List` usando um construtor `java.util.ArrayList`.
   * Para cada objeto `Rule` criado, chame o método `add` do objeto `java.util.List` e passe o objeto `Rule`.

1. Definir opções de tempo de execução do PDF.

   * Crie um objeto `PDFOutputOptionsSpec` usando seu construtor.
   * Especifique o nome e o local do arquivo PDF gerado pelo serviço de Saída invocando o método `setFileURI` do objeto `PDFOutputOptionsSpec`. Transmita um valor de string que especifique o local do arquivo do PDF. A opção File URI é relativa ao servidor de aplicativos J2EE que hospeda o AEM Forms, não ao computador cliente.
   * Defina as regras definidas chamando o método `setRules` do objeto `PDFOutputOptionsSpec`. Passe o objeto `java.util.List` que contém os objetos `Rule`.
   * Defina o número de bytes para verificar os padrões de texto definidos invocando o método `setLookAhead` do objeto `PDFOutputOptionsSpec`. Transmita um valor inteiro que represente os números de bytes.

1. Definir opções de tempo de execução de renderização.

   * Crie um objeto `RenderOptionsSpec` usando seu construtor.
   * Armazene em cache o design do formulário para melhorar o desempenho do serviço de Saída invocando `setCacheEnabled` do objeto `RenderOptionsSpec` e transmitindo `true`.

1. Gere um documento do PDF.

   Gere um documento PDF baseado em vários designs de formulário chamando o método `generatePDFOutput` do objeto `OutputClient` e transmitindo os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de sequência de caracteres que especifica o nome do design do formulário padrão. Ou seja, o design do formulário usado se um padrão de texto não estiver localizado.
   * Um valor de sequência de caracteres que especifica a raiz de conteúdo onde os designs de formulário estão localizados.
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `com.adobe.idp.Document` que contém os dados de formulário pesquisados pelo serviço de Saída para os padrões de texto definidos.

   O método `generatePDFOutput` retorna um objeto `OutputResult` que contém os resultados da operação.

1. Recuperar os resultados da operação.

   * Crie um objeto `com.adobe.idp.Document` que represente o status do método `generatePDFOutput` invocando o método `getStatusDoc` do objeto `OutputResult`.
   * Crie um objeto `java.io.File` que conterá os resultados da operação. Verifique se a extensão do arquivo é .xml.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo (certifique-se de usar o objeto `com.adobe.idp.Document` retornado pelo método `getStatusDoc`).

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo EJB): criando regras de pesquisa usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Início rápido (modo SOAP): criação de regras de pesquisa usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Criar regras de pesquisa usando a API de serviço Web {#create-search-rules-using-the-web-service-api}

Crie regras de pesquisa usando a API de saída (serviço Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Fazer referência a uma fonte de dados XML.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar dados que serão mesclados com o documento do PDF.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF a ser criptografado e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo seu campo `MTOM` com o conteúdo da matriz de bytes.

1. Defina as regras de pesquisa.

   * Crie um objeto `Rule` usando seu construtor.
   * Defina um padrão de texto atribuindo um valor de cadeia que especifique um padrão de texto para o membro de dados `pattern` do objeto `Rule`.
   * Defina o design do formulário correspondente atribuindo um valor de cadeia de caracteres que especifique o design do formulário para o membro de dados `form` do objeto `Rule`.

   >[!NOTE]
   >
   >Para cada padrão de texto que deseja definir, repita as três subetapas anteriores.

   * Crie um objeto `MyArrayOf_xsd_anyType` que armazene as regras.
   * Atribua cada objeto `Rule` a um elemento da matriz `MyArrayOf_xsd_anyType`. Invoque o método `Add` do objeto `MyArrayOf_xsd_anyType` para cada objeto `Rule`.

1. Definir opções de tempo de execução do PDF

   * Crie um objeto `PDFOutputOptionsSpec` usando seu construtor.
   * Defina a opção de URI de arquivo atribuindo um valor de cadeia de caracteres que especifique o local do arquivo PDF que o serviço de Saída gera para o membro de dados `fileURI` do objeto `PDFOutputOptionsSpec`. A opção File URI é relativa ao servidor de aplicativos J2EE que hospeda o AEM Forms, não ao computador cliente.
   * Defina a opção copies atribuindo um valor inteiro que especifica o número de cópias que o serviço de Saída gera para o membro de dados `copies` do objeto `PDFOutputOptionsSpec`.
   * Defina as regras definidas atribuindo o objeto `MyArrayOf_xsd_anyType` que armazena as regras ao membro de dados `rules` do objeto `PDFOutputOptionsSpec`.
   * Defina o número de bytes para verificar os padrões de texto definidos, atribuindo um valor inteiro que represente os números de bytes a serem verificados para o método de dados `lookAhead` do objeto `PDFOutputOptionsSpec`.

1. Definir opções de tempo de execução de renderização

   * Crie um objeto `RenderOptionsSpec` usando seu construtor.
   * Armazene em cache o design do formulário para melhorar o desempenho do serviço de Saída atribuindo o valor `true` ao membro de dados `cacheEnabled` do objeto `RenderOptionsSpec`.

   >[!NOTE]
   >
   >Não é possível definir a versão do documento PDF usando o membro `pdfVersion` do objeto `RenderOptionsSpec`, se o documento de entrada for um formulário Acrobat. O documento de saída do PDF retém a versão PDF do formulário do Acrobat. Da mesma forma, não é possível definir a opção PDF com marcas de formatação usando o método `taggedPDF` do objeto `RenderOptionsSpec` se o documento de entrada for um formulário Acrobat.

   >[!NOTE]
   >
   >Não é possível definir a opção PDF linearizada usando o membro `linearizedPDF` do objeto `RenderOptionsSpec` se o documento PDF de entrada estiver certificado ou assinado digitalmente. Para obter informações, consulte [Assinatura digital de documentos do PDF](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).

1. Gerar um documento do PDF

   Crie um documento PDF chamando o método `generatePDFOutput` do objeto `OutputServiceService` e transmitindo os seguintes valores:

   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF, especifique `TransformationFormat.PDF`.
   * Um valor de cadeia de caracteres que especifica o nome do design do formulário.
   * Um valor de cadeia de caracteres que especifica a raiz do conteúdo onde o design do formulário está localizado.
   * Um objeto `PDFOutputOptionsSpec` que contém opções de tempo de execução do PDF.
   * Um objeto `RenderOptionsSpec` que contém opções de tempo de execução de renderização.
   * O objeto `BLOB` que contém a fonte de dados XML que contém os dados a serem mesclados com o design do formulário.
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com metadados gerados que descrevem o documento. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).
   * Um objeto `BLOB` que é preenchido pelo método `generatePDFOutput`. O método `generatePDFOutput` preenche este objeto com os dados do resultado. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).
   * Um objeto `OutputResult` que contém os resultados da operação. (Este valor de parâmetro é necessário somente para a invocação do serviço Web).

   >[!NOTE]
   >
   >Ao gerar um documento do PDF invocando o método `generatePDFOutput`, não é possível mesclar dados com um formulário do PDF XFA que esteja assinado, certificado ou contenha direitos de uso. Para obter informações sobre direitos de uso, consulte [Aplicando direitos de uso a documentos do PDF](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).

1. Recuperar os resultados da operação

   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa um local de arquivo XML que contém dados de resultado. Certifique-se de que a extensão do arquivo seja XML.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` que foi preenchido com dados de resultado pelo método `generatePDFOutput` do objeto `OutputServiceService` (o oitavo parâmetro). Popular a matriz de bytes obtendo o valor do membro de dados `MTOM` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes no arquivo XML invocando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Nivelamento de documentos do PDF {#flattening-pdf-documents}

Você pode usar o Serviço de saída para transformar um documento interativo do PDF em um PDF não interativo. Um documento interativo do PDF permite que os usuários insiram ou modifiquem dados que estejam nos campos de documento do PDF. O processo de transformação de um documento interativo do PDF em um documento não interativo do PDF é chamado de *nivelamento*. Quando um documento do PDF é nivelado, o usuário não pode modificar os dados nos campos do documento. Um motivo para nivelar um documento do PDF é garantir que os dados não possam ser modificados.

Você pode nivelar os seguintes tipos de documentos do PDF:

* Documentos XFA PDF interativos
* Acrobat Forms

A tentativa de nivelar um PDF que é um documento não interativo do PDF causa uma exceção.

>[!NOTE]
>
>Para obter mais informações sobre o Serviço de saída, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-9}

Para nivelar um documento interativo do PDF em um documento não interativo do PDF, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de saída.
1. Recupere um documento interativo do PDF.
1. Transforme o documento do PDF.
1. Salve o documento não interativo do PDF como um arquivo do PDF.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao caminho de classe do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (necessário se o AEM Forms for implantado no JBoss)
* jbossall-client.jar (necessário se o AEM Forms for implantado no JBoss)

se o AEM Forms for disponibilizado em um servidor de aplicativos J2EE compatível que não seja JBoss, você deverá substituir os arquivos adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos para o servidor de aplicativos J2EE no qual o AEM Forms é disponibilizado. Para obter informações sobre a localização de todos os arquivos JAR do AEM Forms, consulte [Incluindo arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Criar um objeto de Cliente de Saída**

Antes de executar programaticamente uma operação do Serviço de saída, você deve criar um objeto cliente do Serviço de saída. Se você estiver usando a API Java, crie um objeto `OutputClient`. Se você estiver usando a API de Serviço Web de Saída, crie um objeto `OutputServiceService`.

**Recuperar um documento interativo do PDF**

Recupere um documento interativo do PDF que você deseja transformar em um documento não interativo do PDF. A tentativa de transformar um documento PDF não interativo causa uma exceção.

**Transformar o documento do PDF**

Após recuperar um documento interativo do PDF, você pode transformá-lo em um documento não interativo do PDF. O serviço de Saída retorna um documento PDF não interativo.

**Salvar o documento não interativo do PDF como um arquivo do PDF**

Você pode salvar o documento PDF não interativo como um arquivo PDF.

**Consulte também**

[Nivelar um documento do PDF usando a API do Java](creating-document-output-streams.md#flatten-a-pdf-document-using-the-java-api)

[Nivelar um documento do PDF usando a API do serviço Web](creating-document-output-streams.md#flatten-a-pdf-document-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início Rápido da API de Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Nivelar um documento do PDF usando a API do Java {#flatten-a-pdf-document-using-the-java-api}

Nivelar um documento interativo do PDF em um documento não interativo do PDF usando a API de saída (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-output-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `OutputClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Recupere um documento interativo do PDF.

   * Crie um objeto `java.io.FileInputStream` que represente o documento PDF interativo a ser transformado usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do arquivo PDF interativo.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Transforme o documento do PDF.

   Transforme o documento interativo do PDF em um documento não interativo do PDF, chamando o método `transformPDF` do objeto `OutputServiceService` e transmitindo os seguintes valores:

   * O objeto `com.adobe.idp.Document` que contém o documento interativo do PDF.
   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF não interativo, especifique `TransformationFormat.PDF`.
   * Um valor de enumeração `PDFARevisionNumber` que especifica o número de revisão. Como esse parâmetro se destina a um documento PDF/A, você pode especificar `null`.
   * Um valor de sequência de caracteres que representa o número da alteração e o ano, separados por dois pontos. Como esse parâmetro se destina a um documento PDF/A, você pode especificar `null`.
   * Um valor de enumeração `PDFAConformance` que representa o nível de conformidade PDF/A. Como esse parâmetro se destina a um documento PDF/A, você pode especificar `null`.

   O método `transformPDF` retorna um objeto `com.adobe.idp.Document` que contém um documento PDF não interativo.

1. Salve o documento não interativo do PDF como um arquivo do PDF.

   * Crie um objeto `java.io.File` e verifique se a extensão do nome do arquivo é .pdf.
   * Invoque o método `copyToFile` do objeto `Document` para copiar o conteúdo do objeto `Document` para o arquivo (certifique-se de usar o objeto `Document` retornado pelo método `transformPDF`).

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Início rápido (modo EJB): transformação de um documento do PDF usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Início rápido (modo SOAP): transformação de um documento PDF usando a API Java](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Nivelar um documento do PDF usando a API do serviço Web {#flatten-a-pdf-document-using-the-web-service-api}

Nivelar um documento interativo do PDF em um documento não interativo do PDF usando a API de saída (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de saída.

   * Crie um objeto `OutputServiceClient` usando seu construtor padrão.
   * Crie um objeto `OutputServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/OutputService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado quando você cria uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `OutputServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere um documento interativo do PDF.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar o documento interativo do PDF.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento interativo do PDF.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `MTOM` com o conteúdo da matriz de bytes.

1. Transforme o documento do PDF.

   Transforme o documento interativo do PDF em um documento não interativo do PDF, chamando o método `transformPDF` do objeto `OutputClient` e transmitindo os seguintes valores:

   * Um objeto `BLOB` que contém o documento interativo do PDF.
   * Um valor de enumeração `TransformationFormat`. Para gerar um documento PDF não interativo, especifique `TransformationFormat.PDF`.
   * Um valor de enumeração `PDFARevisionNumber` que especifica o número de revisão.
   * Um valor booliano que especifica se o valor de enumeração `PDFARevisionNumber` é usado. Como esse parâmetro se destina a um documento PDF/A, você pode especificar `false`.
   * Um valor de sequência de caracteres que representa o número da alteração e o ano, separados por dois pontos. Como esse parâmetro se destina a um documento PDF/A, você pode especificar `null`.
   * Um valor de enumeração `PDFAConformance` que representa o nível de conformidade PDF/A.
   * Valor booliano que especifica se o valor de enumeração `PDFAConformance` é usado. Como esse parâmetro se destina a um documento PDF/A, você pode especificar `false`.

   O método `transformPDF` retorna um objeto `BLOB` que contém um documento PDF não interativo.

1. Salve o documento não interativo do PDF como um arquivo do PDF.

   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF não interativo.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` retornado pelo método `transformPDF`. Popular a matriz de bytes obtendo o valor do membro de dados `MTOM` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Resumo das etapas](creating-document-output-streams.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
