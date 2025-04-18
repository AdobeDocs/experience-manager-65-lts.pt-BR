---
title: Trabalhar com formulários com códigos de barras
description: Decodifique dados de um formulário do PDF ou de uma imagem que contenha um código de barras usando a API do Java e a API do serviço da Web.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, APIs & Integrations, Barcoded Forms
hide: true
hidefromtoc: true
exl-id: 71dc8036-f9a3-4e00-bce1-3f162428053d
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1911'
ht-degree: 0%

---

# Trabalhar com formulários com códigos de barras {#working-with-barcoded-forms}

**Exemplos e exemplos neste documento são somente para AEM Forms no ambiente JEE.**

## Sobre o serviço de formulários com código de barras {#about-the-barcoded-forms-service}

O serviço de formulários com código de barras automatiza a captura de dados de formulários de preenchimento e impressão e integra as informações capturadas aos principais sistemas de TI de uma organização.

Usando o serviço de formulários com código de barras, você pode adicionar códigos de barras unidimensionais e bidimensionais ao PDF forms interativo. Em seguida, você pode publicar os formulários com código de barras em um site ou distribuí-los por email ou CD. Quando um usuário preenche um formulário com código de barras usando o Adobe Reader, o Acrobat Professional ou o Acrobat Standard, o código de barras é atualizado automaticamente para codificar os dados de formulário fornecidos pelo usuário. O usuário pode enviar o formulário eletronicamente ou imprimi-lo em papel e enviá-lo por correio, fax ou mão. Posteriormente, você pode extrair os dados fornecidos pelo usuário como parte de um fluxo de trabalho automatizado, roteando os dados entre processos de aprovação e sistemas de negócios.

Para obter mais informações sobre o serviço de formulários com código de barras, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Decodificação de dados de formulário com código de barras {#decoding-barcoded-form-data}

Você pode usar a API do serviço de formulários com código de barras para decodificar dados de um formulário do PDF ou de uma imagem que contenha um código de barras. Decodificar dados do formulário significa extrair dados que estão no código de barras. Antes que os dados possam ser decodificados de um formulário (ou imagem) do PDF, um usuário precisa preencher o formulário com dados.

>[!NOTE]
>
>Para obter mais informações sobre o serviço de formulários com código de barras, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary-of-steps}

Para decodificar dados de um formulário do PDF, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto de API formsClient com código de barras.
1. Obtenha um formulário do PDF que contenha dados com código de barras.
1. Decodifique os dados do formulário do PDF.
1. Converta os dados em uma fonte de dados XML.
1. Processe os dados decodificados.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao classpath do projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utilities.jar (obrigatório se o AEM Forms for implantado no JBoss)
* jbossall-client.jar (obrigatório se o AEM Forms for implantado no JBoss)
* xercesImpl.jar (em &lt;diretório de instalação>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdparty)

Se o AEM Forms for disponibilizado em um servidor de aplicativos J2EE compatível que não seja JBOSS, você deverá substituir adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos para o servidor de aplicativos J2EE no qual o AEM Forms é disponibilizado. Para obter informações sobre a localização de todos os arquivos JAR do AEM Forms, consulte [Incluindo arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Criar um objeto de API do Cliente de formulários com código de barras**

Antes de executar programaticamente uma operação do serviço de formulários com código de barras, você deve criar um cliente de serviço do Forms com código de barras. Se você estiver usando a API Java, crie um objeto `BarcodedFormsServiceClient`. Se você estiver usando a API do serviço Web de formulários com código de barras, crie um objeto `BarcodedFormsServiceService`.

**Obter um formulário do PDF que contenha dados com código de barras**

Obtenha um formulário do PDF que contenha um código de barras que tenha sido preenchido com dados do usuário.

**Decodifique os dados do formulário do PDF**

Depois de obter um formulário (ou imagem) do PDF que contém um código de barras, você pode decodificar os dados. O serviço Forms com código de barras é compatível com os seguintes tipos de códigos de barras:

* Códigos de barras PDF417.
* Códigos de barras da matriz de dados.
* Códigos de barras do código QR.
* Códigos de barras de codabar.
* Código 128 códigos de barras.
* Código 39 códigos de barras.
* Códigos de barras EAN-13.
* Códigos de barras EAN-8.

A entrada do conjunto de caracteres como hexadecimal na API de decodificação implica que o conteúdo do código de barras é codificado como uma string hexadecimal. Por exemplo, se UTF-8 for especificado como a codificação de caracteres no formulário e Hex for especificado na operação de decodificação, o conteúdo do código de barras será codificado como uma cadeia de caracteres Hex no elemento &lt; `xb:content`> na saída decodificada. É possível converter esse valor hexadecimal para obter o conteúdo original criando a lógica do aplicativo no aplicativo cliente.

**Converter os dados em uma fonte de dados XML**

Após decodificar os dados do formulário, é possível convertê-los em dados XDP ou XFDF. Por exemplo, suponha que você deseja importar os dados para outro formulário. Para importar os dados em um formulário XFA, é necessário converter os dados em dados XDP. Para obter informações, consulte [Importando dados do formulário](/help/forms/developing/importing-exporting-data.md#importing-form-data).

**Processar os dados decodificados**

Você pode processar os dados convertidos para atender aos requisitos da sua empresa. Por exemplo, depois de decodificar e converter os dados, você pode salvá-los em um arquivo, armazená-los em um banco de dados corporativo, preencher outro formulário e assim por diante. Esta seção discute como salvar os dados convertidos em um arquivo XML.

>[!NOTE]
>
>O serviço de formulários com código de barras não decodifica os dados do código de barras quando os parâmetros delimitador de linha e delimitador de campo têm o mesmo valor

**Consulte também**

[Decodificar dados de formulário com código de barras usando a API do Java](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[Decodificar dados de formulário com código de barras usando a API do serviço Web](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Decodificar dados de formulário com código de barras usando a API do Java {#decode-barcoded-form-data-using-the-java-api}

Decodifique dados de formulário usando a API de formulários com código de barras (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho de classe do projeto Java.

1. Criar um objeto de API do cliente de formulários com código de barras

   Crie um objeto `BarcodedFormsServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Obter um formulário do PDF que contenha dados com código de barras

   * Crie um objeto `java.io.FileInputStream` que represente o formulário PDF que contém dados com código de barras usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do documento PDF.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Decodificar os dados do formulário do PDF

   Decodifique os dados do formulário chamando o método `decode` do objeto `BarcodedFormsServiceClient` e transmitindo os seguintes valores:

   * O objeto `com.adobe.idp.Document` que contém o formulário PDF.
   * Um objeto `java.lang.Boolean` que especifica se um código de barras PDF417 deve ser decodificado.
   * Um objeto `java.lang.Boolean` que especifica se um código de barras de matriz de dados deve ser decodificado.
   * Um objeto `java.lang.Boolean` que especifica se um código de barras QR deve ser decodificado.
   * Um objeto `java.lang.Boolean` que especifica se deve ser decodificado um código de barras de barra de código.
   * Um objeto `java.lang.Boolean` que especifica se um código de barras 128 deve ser decodificado.
   * Um objeto `java.lang.Boolean` que especifica se um código de barras 39 deve ser decodificado.
   * Um objeto `java.lang.Boolean` que especifica se um código de barras EAN-13 deve ser decodificado.
   * Um objeto `java.lang.Boolean` que especifica se um código de barras EAN-8 deve ser decodificado.
   * Um valor de enumeração `com.adobe.livecycle.barcodedforms.CharSet` que especifica o valor de codificação do conjunto de caracteres usado no código de barras.

   O método `decode` retorna um objeto `org.w3c.dom.Document` que contém dados de formulário decodificados.

1. Converter os dados em uma fonte de dados XML

   Converta os dados decodificados em dados XDP ou XFDF invocando o método `extractToXML` do objeto `BarcodedFormsServiceClient` e transmitindo os seguintes valores:

   * O objeto `org.w3c.dom.Document` que contém dados decodificados (certifique-se de usar o valor de retorno do método `decode`).
   * Um valor de enumeração `com.adobe.livecycle.barcodedforms.Delimiter` que especifica o delimitador de linha. É recomendável especificar `Delimiter.Carriage_Return`.
   * Um valor de enumeração `com.adobe.livecycle.barcodedforms.Delimiter` que especifica o delimitador de campo. Por exemplo, especifique `Delimiter.Tab`.
   * Um valor de enumeração `com.adobe.livecycle.barcodedforms.XMLFormat` que especifica se os dados de código de barras devem ser convertidos em dados XML XDP ou XFDF. Por exemplo, especifique `XMLFormat.XDP` para converter os dados em dados XDP.

   >[!NOTE]
   >
   >Não especifique os mesmos valores para os parâmetros delimitador de linha e delimitador de campo.

   O método `extractToXML` retorna um objeto `java.util.List` em que cada elemento é um objeto `org.w3c.dom.Document`. Há um elemento separado para cada código de barras localizado no formulário. Ou seja, se houver quatro códigos de barras no formulário, haverá quatro elementos no objeto `java.util.List` retornado.

1. Processar os dados decodificados

   * Repita o objeto `java.util.List` para obter cada objeto `org.w3c.dom.Document` que esteja na lista.
   * Para cada elemento na lista, converta o objeto `org.w3c.dom.Document` em um objeto `com.adobe.idp.Document`. (A lógica do aplicativo que converte um objeto `org.w3c.dom.Document` em um objeto `com.adobe.idp.Document` é mostrada na Decodificação de dados de formulário com código de barras usando o exemplo da API Java).
   * Salve os dados XML como um arquivo XML invocando o `copyToFile` do objeto `com.adobe.idp.Document` e transmitindo um objeto File que representa o arquivo XML.

**Consulte também**

[Início rápido (modo SOAP): decodificação de dados de formulário com código de barras usando a API Java](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Decodificar dados de formulário com código de barras usando a API do serviço Web {#decode-barcoded-form-data-using-the-web-service-api}

Decodifique dados de formulário usando a API de formulários com código de barras (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly cliente Microsoft .NET que consuma o WSDL do serviço de formulários com código de barras. Para obter informações, consulte [Chamar o AEM Forms usando a codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).
   * Referencie o assembly do cliente Microsoft .NET. Para obter informações, consulte &quot;Referenciando o assembly do cliente .NET&quot; em [Chamando o AEM Forms usando a codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Criar um objeto de API do cliente de formulários com código de barras

   Usando o assembly do cliente Microsoft .NET que consome o WSDL do serviço de formulários com código de barras, crie um objeto `BarcodedFormsServiceService` invocando seu construtor padrão.

1. Obter um formulário do PDF que contenha dados com código de barras

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar um documento PDF que contém um código de barras.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `binaryData` com o conteúdo da matriz de bytes.

1. Decodificar os dados do formulário do PDF

   Decodifique os dados do formulário chamando o método `decode` do objeto `BarcodedFormsServiceService` e transmitindo os seguintes valores:

   * O objeto `BLOB` que contém o formulário PDF.
   * Um objeto `Boolean` que especifica se um código de barras PDF417 deve ser decodificado.
   * Um objeto `Boolean` que especifica se um código de barras de matriz de dados deve ser decodificado.
   * Um objeto `Boolean` que especifica se um código de barras QR deve ser decodificado.
   * Um objeto `Boolean` que especifica se deve ser decodificado um código de barras de barra de código.
   * Um objeto `Boolean` que especifica se um código de barras 128 deve ser decodificado.
   * Um objeto `Bolean` que especifica se um código de barras 39 deve ser decodificado.
   * Um objeto `Boolean` que especifica se um código de barras EAN-13 deve ser decodificado.
   * Um objeto `Boolean` que especifica se um código de barras EAN-8 deve ser decodificado.
   * Um valor de enumeração `CharSet` que especifica o valor de codificação do conjunto de caracteres usado no código de barras.

   O método `decode` retorna um valor de cadeia de caracteres que contém dados de formulário decodificados.

1. Converter os dados em uma fonte de dados XML

   Converta os dados decodificados em dados XDP ou XFDF invocando o método `extractToXML` do objeto `BarcodedFormsServiceService` e transmitindo os seguintes valores:

   * Um valor de cadeia de caracteres que contém dados decodificados (certifique-se de usar o valor de retorno do método `decode`).
   * Um valor de enumeração `Delimiter` que especifica o delimitador de linha. É recomendável especificar `Delimiter.Carriage_Return`.
   * Um valor de enumeração `Delimiter` que especifica o delimitador de campo. Por exemplo, especifique `Delimiter.Tab`.
   * Um valor de enumeração `XMLFormat` que especifica se os dados de código de barras devem ser convertidos em dados XML XDP ou XFDF. Por exemplo, especifique `XMLFormat.XDP` para converter os dados em dados XDP.

   >[!NOTE]
   >
   >Não especifique os mesmos valores para os parâmetros delimitador de linha e delimitador de campo.

   O método `extractToXML` retorna uma matriz `Object` em que cada elemento é uma instância `BLOB`. Há um elemento separado para cada código de barras localizado no formulário. Ou seja, se houver quatro códigos de barras no formulário, então haverá quatro elementos na matriz `Object` retornada.

1. Processar os dados decodificados

   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF protegido.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` retornado pelo método `encryptPDFUsingPassword`. Popular a matriz de bytes obtendo o valor do membro de dados `binaryData` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
