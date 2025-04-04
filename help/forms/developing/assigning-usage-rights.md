---
title: Atribuição de direitos de uso
description: Use as extensões do Acrobat Reader DC da API do cliente Java e da API de serviço da Web para aplicar e remover direitos de uso de documentos do PDF.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services, Reader Extensions
hide: true
hidefromtoc: true
exl-id: d8027b43-10c7-435c-8fb5-059508966d42
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '3897'
ht-degree: 0%

---

# Atribuição de direitos de uso {#assigning-usage-rights}

**Exemplos e exemplos neste documento são somente para AEM Forms no ambiente JEE.**

## Sobre o serviço de extensões do Acrobat Reader DC {#about-the-acrobat-reader-dc-extensions-service}

O serviço de extensões do Acrobat Reader DC permite que sua organização compartilhe facilmente documentos interativos do PDF, estendendo a funcionalidade do Adobe Reader. O serviço de extensões do Acrobat Reader DC oferece suporte total a qualquer documento do PDF, até e incluindo o PDF 1.7. Funciona com o Adobe Reader 7.0 e versões posteriores. O serviço adiciona direitos de uso a um documento do PDF, ativando recursos que normalmente não estão disponíveis quando um documento do PDF é aberto usando o Adobe Reader. Usuários de terceiros não precisam de software ou plug-ins adicionais para trabalhar com documentos habilitados por direitos.

É possível realizar essas tarefas usando o serviço de extensões do Acrobat Reader DC:

* Aplicar direitos de uso a documentos do PDF. Para obter informações, consulte [Aplicando direitos de uso a documentos do PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).
* Remover direitos de uso de documentos do PDF. Para obter informações, consulte [Removendo direitos de uso de documentos do PDF](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).
* Recuperar detalhes da credencial. Para obter informações, consulte [Recuperando Informações de Credencial](assigning-usage-rights.md#retrieving-credential-information).

>[!NOTE]
>
>Para obter mais informações sobre o serviço de extensões do Acrobat Reader DC, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Aplicação de direitos de uso a documentos do PDF {#applying-usage-rights-to-pdf-documents}

É possível aplicar direitos de uso a documentos do PDF usando a API do cliente Java das extensões do Acrobat Reader DC e o serviço da Web. Os direitos de uso pertencem à funcionalidade que está disponível por padrão no Acrobat, mas não no Adobe Reader, como a capacidade de adicionar comentários a um formulário ou preencher campos de formulário e salvar o formulário. Os documentos do PDF que têm direitos de uso aplicados a eles são chamados de documentos habilitados por direitos. Um usuário que abre um documento habilitado para direitos no Adobe Reader pode executar operações que estão habilitadas para esse documento específico.

>[!NOTE]
>
>Ao aplicar direitos de uso a documentos do PDF usando o método `applyUsageRights`, que faz parte da API Java, você pode definir o parâmetro `isModeFinal` do objeto `ReaderExtensionsOptionSpec` como `false`. Isso resulta na não atualização do contador de formulários processados e em uma melhoria no desempenho. Se você não estiver preocupado com a atualização do contador de formulários processados, é recomendável definir o parâmetro `isModeFinal` como `false`.

>[!NOTE]
>
>Para obter mais informações sobre o serviço de extensões do Acrobat Reader DC, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary-of-steps}

Para aplicar direitos de uso a um documento do PDF, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de extensões do Acrobat Reader DC.
1. Recupere um documento do PDF.
1. Especifique os direitos de uso a serem aplicados.
1. Aplicar direitos de uso ao documento do PDF.
1. Salve o documento do PDF com direitos ativados.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um objeto de cliente de extensões do Acrobat Reader DC**

Para executar programaticamente uma operação de serviço de extensões do Acrobat Reader DC, você deve criar um objeto cliente de serviço de extensões do Acrobat Reader DC. Se você estiver usando a API Java das extensões do Acrobat Reader DC, crie um objeto `ReaderExtensionsServiceClient`. Se você estiver usando a API de serviço da Web de extensões do Acrobat Reader DC, crie um objeto `ReaderExtensionsServiceService`.

**Recuperar um documento do PDF**

Recupere um documento do PDF para aplicar direitos de uso. Os documentos do PDF com direitos ativados contêm um dicionário de direitos de uso. Quando o Adobe Reader abre um documento contendo esse dicionário, ele ativa os direitos de uso especificados no dicionário somente para esse documento. Se o documento não contiver um dicionário de direitos de uso, o serviço de extensões do Acrobat Reader DC criará um. Se já contiver um dicionário, o serviço de extensões do Acrobat Reader DC substituirá os direitos de uso existentes pelos que você especificar. O dicionário especifica quais direitos de uso estão ativados. Quando um usuário abre o documento no Adobe Reader, somente os direitos de uso especificados no dicionário são permitidos.

**Especificar direitos de uso a serem aplicados**

Os direitos de uso que você pode definir são determinados por uma credencial que você compra da Adobe Systems Incorporated. As credenciais normalmente fornecem permissão para definir um grupo de direitos de uso relacionados, como aqueles pertencentes aos formulários interativos. Cada credencial oferece o direito de criar um determinado número de documentos do PDF com direitos ativados. Uma credencial de avaliação dá o direito de criar um número ilimitado de documentos de rascunho.

>[!NOTE]
>
>Se você tentar atribuir um direito de uso que não seja permitido pela sua credencial, você causará uma exceção.

**Aplicar direitos de uso ao documento do PDF**

Para aplicar direitos de uso a um documento do PDF, você faz referência ao alias da credencial que está usando para aplicar direitos de uso (normalmente, uma credencial é instalada durante a instalação do AEM Forms). Além disso, você deve especificar o documento do PDF ao qual os direitos de uso são aplicados. Para obter informações sobre como configurar uma credencial, consulte o guia de instalação e implantação do seu servidor de aplicativos.

**Salvar o documento do PDF habilitado para direitos**

Depois que o serviço de extensões do Acrobat Reader DC aplica direitos de uso a um documento do PDF, você pode salvar o documento do PDF habilitado para direitos como um arquivo do PDF.

**Consulte também**

[Aplicar direitos de uso usando a API Java](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Aplicar direitos de uso usando a API de serviço Web](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do serviço de extensões DC do Acrobat Reader](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Aplicar direitos de uso usando a API Java {#apply-usage-rights-using-the-java-api}

Aplique direitos de uso a um documento do PDF usando a API de extensões do Acrobat Reader DC (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente, como adobe-reader-extensions-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto Cliente de extensões do Acrobat Reader DC.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `ReaderExtensionsServiceClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Recupere um documento do PDF.

   * Crie um objeto `java.io.FileInputStream` que represente o documento PDF usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do documento PDF.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Especifique os direitos de uso a serem aplicados.

   * Crie um objeto `UsageRights` que represente direitos de uso usando seu construtor.
   * Para cada direito de uso a ser aplicado, chame um método correspondente que pertença ao objeto `UsageRights`. Por exemplo, para adicionar o direito de uso `enableFormFillIn`, chame o método `enableFormFillIn` do objeto `UsageRights` e passe `true`. (Repita essa etapa para cada direito de uso a ser aplicado).

1. Aplicar direitos de uso ao documento do PDF.

   * Crie um objeto `ReaderExtensionsOptionSpec` usando seu construtor. Esse objeto contém opções de tempo de execução que são exigidas pelo serviço de extensões do Acrobat Reader DC. Ao chamar esse construtor, você deve especificar os seguintes valores:

      * O objeto `UsageRights` que contém os direitos de uso a serem aplicados ao documento.
      * Um valor de string que especifica uma mensagem que um usuário vê quando o documento do PDF com direitos ativados é aberto no Adobe Reader 7.x. Esta mensagem não é exibida no Adobe Reader 8.0.

   * Aplique direitos de uso ao documento PDF invocando o método `applyUsageRights` do objeto `ReaderExtensionsServiceClient` e transmitindo os seguintes valores:

      * O objeto `com.adobe.idp.Document` que contém o documento PDF ao qual os direitos de uso são aplicados.
      * Um valor de string que especifica o alias da credencial que permite aplicar direitos de uso.
      * Um valor de string que especifica o valor de senha correspondente. (Atualmente, esse parâmetro é ignorado. Você pode passar `null`.)

   * O objeto `ReaderExtensionsOptionSpec` que contém opções de tempo de execução.

   O método `applyUsageRights` retorna um objeto `com.adobe.idp.Document` que contém o documento PDF habilitado para direitos.

1. Salve o documento do PDF com direitos ativados.

   * Crie um objeto `java.io.File` e verifique se a extensão do arquivo é .pdf.
   * Invoque o método `copyToFile` do objeto `com.adobe.idp.Document` para copiar o conteúdo do objeto `com.adobe.idp.Document` para o arquivo (certifique-se de usar o objeto `com.adobe.idp.Document` retornado pelo método `applyUsageRights`).

**Consulte também**

[Aplicação de direitos de uso a documentos do PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Início rápido (modo SOAP):Aplicação de direitos de uso usando a API Java](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Aplicar direitos de uso usando a API de serviço Web {#apply-usage-rights-using-the-web-service-api}

Aplique direitos de uso a um documento do PDF usando a API de extensões do Acrobat Reader DC (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de extensões do Acrobat Reader DC.

   * Crie um objeto `ReaderExtensionsServiceClient` usando seu construtor padrão.
   * Crie um objeto `ReaderExtensionsServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Certifique-se de especificar `?blob=mtom`.)
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `ReaderExtensionsServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere um documento do PDF.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar um documento PDF ao qual são aplicados direitos de uso.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream`. Passe a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `MTOM` com o conteúdo da matriz de bytes.

1. Especifique os direitos de uso a serem aplicados.

   * Crie um objeto `UsageRights` que represente direitos de uso usando seu construtor.
   * Para cada direito de uso a ser aplicado, atribua o valor `true` ao membro de dados correspondente que pertence ao objeto `UsageRights`. Por exemplo, para adicionar o direito de uso `enableFormFillIn`, atribua `true` ao membro de dados `enableFormFillIn` do objeto `UsageRights`. (Repita essa etapa para cada direito de uso a ser aplicado).

1. Aplicar direitos de uso ao documento do PDF.

   * Crie um objeto `ReaderExtensionsOptionSpec` usando seu construtor. Esse objeto contém opções de tempo de execução que são exigidas pelo serviço de extensões do Acrobat Reader DC.
   * Atribua o objeto `UsageRights` ao membro de dados `usageRights` do objeto `ReaderExtensionsOptionSpec`.
   * Atribua um valor de cadeia de caracteres que especifique a mensagem que um usuário vê quando o documento PDF com direitos habilitados é aberto no Adobe Reader para o membro de dados `message` do objeto `ReaderExtensionsOptionSpec`.
   * Aplique direitos de uso ao documento PDF invocando o método `applyUsageRights` do objeto `ReaderExtensionsServiceClient` e transmitindo os seguintes valores:

      * O objeto `BLOB` que contém o documento PDF ao qual os direitos de uso são aplicados.
      * Um valor de string que especifica o alias da credencial que permite aplicar direitos de uso.
      * Um valor de string que especifica o valor de senha correspondente. (Atualmente, esse parâmetro é ignorado. Você pode passar `null`.)

   * O objeto `ReaderExtensionsOptionSpec` que contém opções de tempo de execução.

   O método `applyUsageRights` retorna um objeto `BLOB` que contém o documento PDF habilitado para direitos.

1. Salve o documento do PDF com direitos ativados.

   * Crie um objeto `System.IO.FileStream` invocando seu construtor. Transmita um valor de string que represente o local do arquivo do documento do PDF com direitos ativados.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` retornado pelo método `applyUsageRights`. Popular a matriz de bytes obtendo o valor do membro de dados `MTOM` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `Write` do objeto `System.IO.BinaryWriter` e transmitindo a matriz de bytes.

**Consulte também**

[Aplicação de direitos de uso a documentos do PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Remoção de direitos de uso de documentos do PDF {#removing-usage-rights-from-pdf-documents}

Você pode remover direitos de uso de um documento habilitado para direitos. A remoção de direitos de uso de um documento do PDF com direitos ativados também é necessária para executar outras operações do AEM Forms nele. Por exemplo, você deve assinar digitalmente (ou certificar) um documento do PDF antes de definir os direitos de uso. Portanto, se você quiser executar operações em um documento com direitos ativados, remova os direitos de uso do documento do PDF, execute as outras operações, como assinar digitalmente o documento e reaplique os direitos de uso ao documento.

>[!NOTE]
>
>Para obter mais informações sobre o serviço de extensões do Acrobat Reader DC, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-1}

Para remover direitos de uso de um documento do PDF com direitos ativados, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de extensões do Acrobat Reader DC.
1. Recupere um documento do PDF habilitado para direitos.
1. Remover direitos de uso do documento do PDF.
1. Salve o documento do PDF.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um objeto de cliente de extensões do Acrobat Reader DC**

Antes de executar programaticamente uma operação de serviço de extensões do Acrobat Reader DC, você deve criar um objeto cliente de serviço de extensões do Acrobat Reader DC. Se você estiver usando a API Java, crie um objeto `ReaderExtensionsServiceClient`. Se você estiver usando a API de serviço da Web de extensões do Acrobat Reader DC, crie um objeto `ReaderExtensionsServiceService`.

**Recuperar um documento do PDF habilitado para direitos**

Recupere um documento do PDF com direitos ativados para remover os direitos de uso.

**Remover direitos de uso do documento do PDF**

Após recuperar um documento do PDF com direitos ativados, você pode remover os direitos de uso. Após remover os direitos de uso, o documento do PDF não terá nenhuma funcionalidade adicional enquanto for visualizado no Adobe Reader.

**Salvar o documento do PDF**

Você pode salvar o documento do PDF que não contém mais direitos de uso como um arquivo do PDF. Depois de salvo como um arquivo PDF, o documento PDF pode ser visualizado no Adobe Reader ou no Acrobat.

**Consulte também**

[Remover direitos de uso usando a API Java](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Remover direitos de uso usando a API de serviço Web](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do serviço de extensões DC do Acrobat Reader](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Aplicação de direitos de uso a documentos do PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Remover direitos de uso usando a API Java {#remove-usage-rights-using-the-java-api}

Remova os direitos de uso de um documento do PDF habilitado para direitos usando a API de extensões do Acrobat Reader DC (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-reader-extensions-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto Cliente de extensões do Acrobat Reader DC.

   Crie um objeto `ReaderExtensionsServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Recupere um documento do PDF.

   * Crie um objeto `java.io.FileInputStream` que represente o documento PDF com direitos habilitados usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do documento PDF.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Remover direitos de uso do documento do PDF.

   Remova os direitos de uso do documento PDF invocando o método `removeUsageRights` do objeto `ReaderExtensionsServiceClient` e transmitindo o objeto `com.adobe.idp.Document` que contém o documento PDF habilitado para direitos. Este método retorna um objeto `com.adobe.idp.Document` que contém um documento PDF que não tem direitos de uso.

1. Aplicar direitos de uso ao documento do PDF.

   * Crie um objeto `java.io.File` e verifique se a extensão do arquivo é .PDF.
   * Invoque o método `copyToFile` do objeto `Document` para copiar o conteúdo do objeto `Document` para o arquivo (certifique-se de usar o objeto `Document` retornado pelo método `removeUsageRights`).

**Consulte também**

[Remoção de direitos de uso de documentos do PDF](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Início rápido (modo SOAP): remoção de direitos de uso de um documento PDF usando a API Java](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Remover direitos de uso usando a API de serviço Web {#remove-usage-rights-using-the-web-service-api}

Remova os direitos de uso de um documento do PDF habilitado para direitos usando a API de extensões do Acrobat Reader DC (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de extensões do Acrobat Reader DC.

   * Crie um objeto `ReaderExtensionsServiceClient` usando seu construtor padrão.
   * Crie um objeto `ReaderExtensionsServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Certifique-se de especificar `?blob=mtom`.)
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `ReaderExtensionsServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere um documento do PDF.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar o documento do PDF habilitado para direitos do qual os direitos de uso são removidos.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com os dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `MTOM` com o conteúdo da matriz de bytes.

1. Remover direitos de uso do documento do PDF.

   Remova os direitos de uso do documento PDF invocando o método `removeUsageRights` do objeto `ReaderExtensionsServiceClient` e transmitindo o objeto `BLOB` que contém o documento PDF habilitado para direitos. Este método retorna um objeto `BLOB` que contém um documento PDF que não tem direitos de uso.

1. Aplicar direitos de uso ao documento do PDF.

   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo PDF.
   * Crie uma matriz de bytes que armazene o conteúdo de dados do objeto `BLOB` retornado pelo método `removeUsageRights`. Popular a matriz de bytes obtendo o valor do membro de dados `MTOM` do objeto `BLOB`.
   * Crie um objeto `System.IO.BinaryWriter` invocando seu construtor e transmitindo o objeto `System.IO.FileStream`.

**Consulte também**

[Remoção de direitos de uso de documentos do PDF](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Recuperando Informações de Credencial {#retrieving-credential-information}

Você pode recuperar informações sobre a credencial usada para aplicar direitos de uso a um documento do PDF habilitado para direitos. Ao recuperar informações sobre uma credencial, você pode obter informações como a data após a qual o certificado não é mais válido.

>[!NOTE]
>
>Para obter mais informações sobre o serviço de extensões do Acrobat Reader DC, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-2}

Para recuperar informações sobre a credencial usada para aplicar direitos de uso a um documento do PDF, execute as seguintes etapas:

1. Incluir arquivos de projeto.
1. Crie um objeto Cliente de extensões do Acrobat Reader DC.
1. Recupere um documento do PDF habilitado para direitos.
1. Recuperar informações sobre a credencial.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando uma aplicação cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um objeto de cliente de extensões do Acrobat Reader DC**

Antes de executar programaticamente uma operação de serviço de extensões do Acrobat Reader DC, você deve criar um objeto cliente de serviço de extensões do Acrobat Reader DC. Se você estiver usando a API Java, crie um objeto `ReaderExtensionsServiceClient`. Se você estiver usando a API de serviço da Web de extensões do Acrobat Reader DC, crie um objeto `ReaderExtensionsServiceService`.

**Recuperar um documento do PDF habilitado para direitos**

Recupere um documento do PDF com direitos ativados para recuperar informações sobre a credencial. Você também pode recuperar informações sobre uma credencial especificando seu alias; no entanto, se quiser recuperar informações sobre uma credencial usada para aplicar direitos de uso a um documento do PDF com direitos ativados específicos, você deverá recuperar o documento.

**Recuperar informações sobre a credencial**

Depois de recuperar um documento do PDF com direitos ativados, você pode obter informações sobre a credencial usada para aplicar direitos de uso a ela. Você pode obter as seguintes informações sobre a credencial:

* A mensagem que é exibida no Adobe Reader quando o documento PDF ativado por direitos é aberto.
* A data após a qual a credencial não é mais válida.
* A data antes da qual a credencial não é válida.
* Os direitos de uso que foram definidos para este documento do PDF habilitado para direitos.
* O número de vezes que a credencial foi usada.

**Consulte também**

[Remover direitos de uso usando a API Java](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Remover direitos de uso usando a API de serviço Web](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do serviço de extensões DC do Acrobat Reader](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Recuperar informações de credencial usando a API Java {#retrieve-credential-information-using-the-java-api}

Recupere informações de credenciais usando a API de extensões do Acrobat Reader DC (Java):

1. Incluir arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-reader-extensions-client.jar, no caminho de classe do projeto Java.

1. Crie um objeto Cliente de extensões do Acrobat Reader DC.

   Crie um objeto `ReaderExtensionsServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Recupere um documento do PDF.

   * Crie um objeto `java.io.FileInputStream` que represente o documento PDF com direitos habilitados usando seu construtor e transmitindo um valor de cadeia de caracteres que especifique o local do documento PDF com direitos habilitados.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Remover direitos de uso do documento do PDF.

   * Recupere informações sobre a credencial usada para aplicar direitos de uso ao documento do PDF invocando o método `getDocumentUsageRights` do objeto `ReaderExtensionsServiceClient` e transmitindo o objeto `com.adobe.idp.Document` que contém o documento do PDF habilitado para direitos. Este método retorna um objeto `GetUsageRightsResult` que contém informações de credencial.
   * Recupere a data após a qual a credencial não será mais válida invocando o método `getNotAfter` do objeto `GetUsageRightsResult`. Este método retorna um objeto `java.util.Date` que representa a data após a qual a credencial não é mais válida.
   * Recupere a mensagem que é exibida no Adobe Reader quando o documento do PDF habilitado para direitos for aberto chamando o método `getMessage` do objeto `GetUsageRightsResult`. Esse método retorna um valor de string que representa a mensagem.

**Consulte também**

[Recuperando Informações de Credencial](assigning-usage-rights.md#retrieving-credential-information)

[Início rápido (modo SOAP): recuperação de informações de credencial usando a API Java](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Definindo propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Recuperar informações de credencial usando a API do serviço Web {#retrieve-credential-information-using-the-web-service-api}

Recupere informações de credenciais usando a API de extensões do Acrobat Reader DC (serviço da Web):

1. Incluir arquivos de projeto.

   Crie um projeto Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição WSDL: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um objeto Cliente de extensões do Acrobat Reader DC.

   * Crie um objeto `ReaderExtensionsServiceClient` usando seu construtor padrão.
   * Crie um objeto `ReaderExtensionsServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Transmita um valor de cadeia de caracteres que especifique o WSDL para o serviço AEM Forms (por exemplo, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Certifique-se de especificar `?blob=mtom`.)
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `ReaderExtensionsServiceClient.Endpoint.Binding`. Converter o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `MessageEncoding` do objeto `System.ServiceModel.BasicHttpBinding` como `WSMessageEncoding.Mtom`. Esse valor garante que a MTOM seja usada.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor de senha correspondente ao campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere um documento do PDF.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar um documento PDF habilitado para direitos.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e transmitindo um valor de cadeia de caracteres que representa o local do arquivo do documento PDF habilitado para direitos e o modo no qual o arquivo será aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `Length` do objeto `System.IO.FileStream`.
   * Preencha a matriz de bytes com os dados de fluxo invocando o método `Read` do objeto `System.IO.FileStream` e transmitindo a matriz de bytes, a posição inicial e o comprimento do fluxo para leitura.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `MTOM` com o conteúdo da matriz de bytes.

1. Remover direitos de uso do documento do PDF.

   * Recupere informações sobre a credencial usada para aplicar direitos de uso ao documento do PDF invocando o método `getDocumentUsageRights` do objeto `ReaderExtensionsServiceClient` e transmitindo o objeto `com.adobe.idp.Document` que contém o documento do PDF habilitado para direitos. Este método retorna um objeto `GetUsageRightsResult` que contém informações de credencial.
   * Recupere a data após a qual a credencial não será mais válida obtendo o valor do membro de dados `notAfter` do objeto `GetUsageRightsResult`. O tipo de dados deste membro de dados é `System.DateTime`.
   * Recupere a mensagem que é exibida quando o documento do PDF habilitado para direitos é aberto no Adobe Reader obtendo o valor do membro de dados `message` do objeto `GetUsageRightsResult`. O tipo de dados deste membro de dados é uma string.
   * Recupere o número de vezes que a credencial é usada obtendo o valor do membro de dados `useCount` do objeto `GetUsageRightsResult`. O tipo de dados deste membro de dados é um inteiro.

**Consulte também**

[Recuperando Informações de Credencial](assigning-usage-rights.md#retrieving-credential-information)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
