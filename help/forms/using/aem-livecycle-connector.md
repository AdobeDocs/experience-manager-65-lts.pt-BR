---
title: Conexão do AEM Forms com o Adobe LiveCycle
description: O conector do LiveCycle do Adobe Experience Manager (AEM) permite iniciar o LiveCycle ES4 Acrobat Services a partir de aplicativos e fluxos de trabalho do AEM.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---

# Conexão do AEM Forms com o Adobe LiveCycle {#connecting-aem-forms-with-adobe-livecycle}

O conector do Adobe Experience Manager (AEM) LiveCycle permite a invocação simplificada do Adobe LiveCycle ES4 Acrobat Services a partir de aplicativos Web e fluxos de trabalho da AEM. O LiveCycle fornece um SDK cliente avançado, que permite que os aplicativos clientes iniciem os serviços do LiveCycle usando APIs Java™. O AEM LiveCycle Connector simplifica o uso dessas APIs no ambiente OSGi.

## Conectar o servidor do AEM ao Adobe LiveCycle {#connecting-aem-server-to-adobe-livecycle}

O AEM LiveCycle Connector faz parte do [pacote complementar do AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Depois de instalar o pacote complementar do AEM Forms, siga as etapas abaixo para adicionar detalhes do servidor LiveCycle ao AEM Web Console.

1. No gerenciador de configurações do console da Web do AEM, localize o componente de configuração do Adobe LiveCycle Client SDK.
1. Clique no componente para editar o URL do servidor de configuração, nome de usuário e senha.
1. Revise as configurações e clique em **Salvar**.

Embora as propriedades sejam autoexplicativas, as importantes são as seguintes:

* **URL do Servidor** - Especifica a URL para o servidor do LiveCycle. Se quiser que o LiveCycle e o AEM se comuniquem via https, inicie o AEM com a seguinte JVM

  ```java
  argument
   -Djavax.net.ssl.trustStore=<<em>path to LC keystore</em>>
  ```

  opção.

* **Nome de usuário**- Especifica o nome de usuário da conta usada para estabelecer a comunicação entre o AEM e o LiveCycle. A conta é uma conta de usuário do LiveCycle que tem permissões para iniciar os Serviços da Acrobat.
* **Senha**- Especifica a senha.
* **Nome do Serviço** - Especifica os serviços que são iniciados usando as credenciais de usuário fornecidas nos campos Nome de Usuário e Senha. Por padrão, nenhuma credencial é transmitida ao iniciar os serviços do LiveCycle.

## Iniciando serviços de documento {#starting-document-services}

Os aplicativos clientes podem iniciar programaticamente os serviços do LiveCycle usando uma API Java™, Serviços da Web, Comunicação remota e REST. Para clientes Java™, o aplicativo pode usar o LiveCycle SDK. O LiveCycle SDK fornece uma API Java™ para iniciar esses serviços remotamente. Por exemplo, para converter um documento do Microsoft® Word para o PDF, o cliente inicia GeneratePDFService. O fluxo de chamada consiste nas seguintes etapas:

1. Crie uma instância ServiceClientFactory.
1. Cada serviço fornece uma classe de cliente. Para iniciar um serviço, crie uma instância do cliente do serviço.
1. Inicie o serviço e processe o resultado.

O AEM LiveCycle Connector simplifica o fluxo ao expor essas instâncias do cliente como serviços OSGi que podem ser acessados usando meios OSGi padrão. O conector do LiveCycle fornece os seguintes recursos:

* Instâncias do cliente como Serviço OSGi: os clientes empacotados como pacotes OSGi estão listados na seção [Lista de serviços do Acrobat](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p). Cada jar do cliente registra a instância do cliente como um serviço OSGi com o Registro de serviço OSGi.
* Propagação de credencial do usuário: os detalhes de conexão necessários para se conectar ao servidor do LiveCycle são gerenciados em um local central.
* ServiceClientFactory Service: Para iniciar os processos, o aplicativo cliente pode acessar a instância ServiceClientFactory.

### Iniciando por Referências de Serviço do Registro de Serviço OSGi {#starting-via-service-references-from-osgi-service-registry}

Para iniciar um serviço exposto a partir do AEM, execute as seguintes etapas:

1. Determine as dependências do Maven. Adicione a dependência ao jar do cliente necessário em seu arquivo maven pom.xml. No mínimo, adicione dependência aos jars adobe-livecycle-client e adobe-usermanager-client.

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-livecycle-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-usermanager-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-cq-integration-api</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

   Para iniciar um serviço, adicione uma dependência Maven correspondente para o serviço. Para obter a lista de dependências, consulte [Lista de Serviços da Acrobat](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p). Por exemplo, para o serviço Gerar PDF, adicione a seguinte dependência:

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-generatepdf-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

1. Obter a referência do serviço. Obtenha um identificador para a instância do serviço. Se você estiver gravando uma classe Java™, poderá usar as anotações do Declarative Services.

   ```java
   import com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient;
   import com.adobe.livecycle.generatepdf.client.CreatePDFResult;
   import com.adobe.idp.Document;
   
   @Reference
   GeneratePdfServiceClient generatePDF;
   ...
   
   Resource r = resourceResolver.getResource("/path/tp/docx");
   Document sourceDoc = new Document(r.adaptTo(InputStream.class));
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

   O trecho de código acima inicia a API createPDF de GeneratePdfServiceClient para converter um documento para o PDF. Você pode executar uma invocação semelhante em um JSP usando o código a seguir. A principal diferença é que o código a seguir usa o Sling ScriptHelper para acessar o GeneratePdfServiceClient.

   ```jsp
   <%@ page import="com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient" %>
   <%@ page import="com.adobe.livecycle.generatepdf.client.CreatePDFResult" %>
   <%@ page import="com.adobe.idp.Document" %>
   
   GeneratePdfServiceClient generatePDF = sling.getService(GeneratePdfServiceClient.class);
   Document sourceDoc = ...
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

### Iniciando via ServiceClientFactory {#starting-via-serviceclientfactory}

Às vezes, a classe ServiceClientFactory é necessária. Por exemplo, você precisa de ServiceClientFactory para chamar processos.

```java
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider;
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;

@Reference
ServiceClientFactoryProvider scfProvider;

...
ServiceClientFactory scf = scfProvider.getDefaultServiceClientFactory();
...
```

## Suporte a RunAs {#runas-support}

Quase todos os serviços da Acrobat no LiveCycle exigem autenticação. Você pode usar qualquer uma das seguintes opções para iniciar esses serviços sem fornecer credenciais explícitas no código:

### configurações de Inclui na lista de permissões {#allowlist-configuration}

A configuração do LiveCycle Client SDK contém uma configuração sobre nomes de serviço. Essa configuração é uma lista de serviços para os quais a lógica de invocação usa uma credencial de administrador pronta para uso. Por exemplo, se você adicionar serviços do DiretoryManager (parte da API de gerenciamento de usuários) a essa lista, qualquer código de cliente poderá usar o serviço diretamente. Além disso, a camada de chamada passa automaticamente as credenciais configuradas como parte da solicitação enviada ao servidor do LiveCycle.

### RunAsManager {#runasmanager}

Como parte da integração, um novo serviço RunAsManager é fornecido. Ele permite controlar programaticamente uma credencial a ser usada ao chamar o servidor do LiveCycle.

```java
import com.adobe.livecycle.dsc.clientsdk.security.PasswordCredential;
import com.adobe.livecycle.dsc.clientsdk.security.PrivilegedAction;
import com.adobe.livecycle.dsc.clientsdk.security.RunAsManager;
import com.adobe.idp.dsc.registry.component.ComponentRegistry;

@Reference
private RunAsManager runAsManager;

List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
            public List<Component> run() {
                return componentRegistry.getComponents();
            }
        });
assertNotNull(components);
```

Se quiser passar uma credencial diferente, você poderá usar o método sobrecarregado que usa uma instância PasswordCredential.

```java
PasswordCredential credential = new PasswordCredential("administrator","password");
List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
    public List<Component> run() {
        return componentRegistry.getComponents();
    }
},credential);
```

### Propriedade InvocationRequest {#invocationrequest-property}

Se você chamar um processo ou fizer uso direto da classe ServiceClientFactory e criar uma InvocationRequest, poderá especificar uma propriedade para indicar que a camada de chamada deve usar credenciais configuradas.

```java
import com.adobe.idp.dsc.InvocationResponse
import com.adobe.idp.dsc.InvocationRequest
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory
import com.adobe.livecycle.dsc.clientsdk.InvocationProperties

ServiceClientFactoryProvider scfp = sling.getService(ServiceClientFactoryProvider.class)
ServiceClientFactory serviceClientFactory = scfp.getDefaultServiceClientFactory()
InvocationRequest ir = serviceClientFactory.createInvocationRequest("sample/LetterSubmissionProcess", "invoke", new HashMap(), true);

//Here we are invoking the request with system user
ir.setProperty(InvocationProperties.INVOKER_TYPE,InvocationProperties.INVOKER_TYPE_SYSTEM)

InvocationResponse response = serviceClientFactory.getServiceClient().invoke(ir);
```

## Lista de serviços da Acrobat {#document-services-list}

### Pacote de API do Adobe LiveCycle Client SDK {#adobe-livecycle-client-sdk-api-bundle}

Os seguintes serviços estão disponíveis:

* com.adobe.idp.um.api.AuthenticationManager
* com.adobe.idp.um.api.DirectoryManager
* com.adobe.idp.um.api.AuthorizationManager
* com.adobe.idp.dsc.registry.service.ServiceRegistry
* com.adobe.idp.dsc.registry.component.ComponentRegistry

#### Dependências do Maven {#maven-dependencies}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-client</artifactId>
  <version>11.0.0</version>
</dependency>
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-usermanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do Adobe LiveCycle Client SDK {#adobe-livecycle-client-sdk-bundle}

Os seguintes serviços estão disponíveis:

* com.adobe.livecycle.dsc.clientsdk.security.RunAsManager
* com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider

#### Dependências do Maven {#maven-dependencies-1}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-cq-integration-api</artifactId>
  <version>1.1.10</version>
</dependency>
```

### Pacote do cliente TaskManager do Adobe LiveCycle {#adobe-livecycle-taskmanager-client-bundle}

Os seguintes serviços estão disponíveis:

* com.adobe.idp.taskmanager.dsc.client.task.TaskManager
* com.adobe.idp.taskmanager.dsc.client.TaskManagerQueryService
* com.adobe.idp.taskmanager.dsc.client.queuemanager.QueueManager
* com.adobe.idp.taskmanager.dsc.client.emailsettings.EmailSettingService
* com.adobe.idp.taskmanager.dsc.client.endpoint.TaskManagerEndpointClient
* com.adobe.idp.taskmanager.dsc.client.userlist.UserlistService

#### Dependências do Maven {#maven-dependencies-2}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-taskmanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote de clientes do fluxo de trabalho do Adobe LiveCycle {#adobe-livecycle-workflow-client-bundle}

O seguinte serviço está disponível:

* com.adobe.idp.workflow.client.WorkflowServiceClient

#### Dependências do Maven {#maven-dependencies-3}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-workflow-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente do Adobe LiveCycle PDF Generator {#adobe-livecycle-pdf-generator-client-bundle}

O seguinte serviço está disponível:

* com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient

#### Dependências do Maven {#maven-dependencies-4}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-generatepdf-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente do Adobe LiveCycle Application Manager {#adobe-livecycle-application-manager-client-bundle}

Os seguintes serviços estão disponíveis:

* com.adobe.idp.applicationmanager.service.ApplicationManager
* com.adobe.livecycle.applicationmanager.client.ApplicationManager
* com.adobe.livecycle.design.service.DesigntimeService

#### Dependências do Maven {#maven-dependencies-5}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-applicationmanager-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente do Adobe LiveCycle Assembler {#adobe-livecycle-assembler-client-bundle}

O seguinte serviço está disponível:

* com.adobe.livecycle.assembler.client.AssemblerServiceClient

#### Dependências do Maven {#maven-dependencies-6}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-assembler-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente de integração de dados do formulário do Adobe LiveCycle {#adobe-livecycle-form-data-integration-client-bundle}

O seguinte serviço está disponível:

* com.adobe.livecycle.formdataintegration.client.FormDataIntegrationClient

#### Dependências do Maven {#maven-dependencies-7}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-formdataintegration-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente do Adobe LiveCycle Forms {#adobe-livecycle-forms-client-bundle}

O seguinte serviço está disponível:

* com.adobe.livecycle.formsservice.client.FormsServiceClient

#### Dependências do Maven {#maven-dependencies-8}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-forms-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente de saída do Adobe LiveCycle {#adobe-livecycle-output-client-bundle}

O seguinte serviço está disponível:

* com.adobe.livecycle.output.client.OutputClient

#### Dependências do Maven {#maven-dependencies-9}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-output-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente de extensões do Adobe LiveCycle Reader {#adobe-livecycle-reader-extensions-client-bundle}

O seguinte serviço está disponível:

* com.adobe.livecycle.readerextensions.client.ReaderExtensionsServiceClient

#### Dependências do Maven {#maven-dependencies-10}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-reader-extensions-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente do Adobe LiveCycle Rights Manager {#adobe-livecycle-rights-manager-client-bundle}

Os seguintes serviços estão disponíveis:

* com.adobe.livecycle.rightsmanagement.client.DocumentManager
* com.adobe.livecycle.rightsmanagement.client.EventManager
* com.adobe.livecycle.rightsmanagement.client.ExternalUserManager
* com.adobe.livecycle.rightsmanagement.client.LicenseManager
* com.adobe.livecycle.rightsmanagement.client.WatermarkManager
* com.adobe.livecycle.rightsmanagement.client.PolicyManager
* com.adobe.livecycle.rightsmanagement.client.AbstractPolicyManager

#### Dependências do Maven {#maven-dependencies-11}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-rightsmanagement-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente de assinaturas do Adobe LiveCycle {#adobe-livecycle-signatures-client-bundle}

O seguinte serviço está disponível:

* com.adobe.livecycle.signatures.client.SignatureServiceClientInterface

#### Dependências do Maven {#maven-dependencies-12}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-signatures-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do Adobe LiveCycle Truststore Client {#adobe-livecycle-truststore-client-bundle}

Os seguintes serviços estão disponíveis:

* com.adobe.truststore.dsc.TrustConfigurationService
* com.adobe.truststore.dsc.CRLService
* com.adobe.truststore.dsc.CredentialService
* com.adobe.truststore.dsc.CertificateService

#### Dependências do Maven {#maven-dependencies-13}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-truststore-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Pacote do cliente do repositório do Adobe LiveCycle {#adobe-livecycle-repository-client-bundle}

Os seguintes serviços estão disponíveis:

* com.adobe.repository.bindings.ResourceRepository
* com.adobe.repository.bindings.ResourceSynchronizer

#### Dependências do Maven {#maven-dependencies-14}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-repository-client</artifactId>
  <version>11.0.0</version>
</dependency>
```
