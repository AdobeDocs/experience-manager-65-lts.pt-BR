---
title: Noções básicas sobre processos do AEM Forms
description: Saiba como os processos do AEM Forms incluem criação de formulários, envio, manipulação de dados, validação, integração, automação de fluxo de trabalho e gerenciamento de saídas.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools, coding
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: 228185f0-deef-4d49-a5b9-0c19411e30c2
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 0%

---

# Noções básicas sobre processos do AEM Forms {#understanding-aem-forms-processes}

**Exemplos e exemplos neste documento são somente para AEM Forms no ambiente JEE.**

Um caso de uso comum é um conjunto de serviços da AEM Forms que operam em um único documento. Você pode enviar uma solicitação para o contêiner de serviço criando um processo usando a Bancada. Um processo representa um processo de negócios que você está automatizando. Para obter informações sobre como criar processos, consulte [Usando o Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).

Uma vez ativado, o processo torna-se um serviço e pode ser chamado como outros serviços. Uma diferença entre um serviço padrão, como o Serviço de criptografia, e um serviço que se originou de um processo é que o último tem uma operação que executa muitas ações. Por outro lado, um serviço padrão tem muitas operações. Cada operação normalmente executa uma ação, como aplicar uma política a um documento ou criptografar um documento.

Os processos podem ter vida curta ou longa. Um processo de curta duração é uma operação executada de forma síncrona e no mesmo thread de execução do qual foi chamado. As operações de curta duração são comparáveis ao comportamento padrão encontrado na maioria das linguagens de programação, onde um aplicativo cliente chama um método e aguarda um valor de retorno.

No entanto, há situações em que um processo não pode ser concluído de forma síncrona devido a fatores como estes:

* Um processo pode se estender por um período significativo.
* Um processo pode ultrapassar os limites organizacionais.
* Um processo precisa de entrada externa para ser concluído. Por exemplo, considere uma situação em que um formulário é enviado a um gerente que está fora do escritório. Nessa situação, o processo não é concluído até que o gerente retorne e preencha o formulário.

  Esses tipos de processos são conhecidos como processos de longa duração. Um processo de longa duração é executado de forma assíncrona, permitindo que os sistemas interajam conforme os recursos permitem e permitindo o rastreamento e o monitoramento da operação. Quando um processo de longa duração é chamado, o AEM Forms cria um valor de identificador de invocação como parte de um registro que rastreia o status do processo de longa duração. O registro é armazenado no banco de dados do AEM Forms. Você pode limpar registros de processos de longa duração quando eles não são mais necessários.

>[!NOTE]
>
>O AEM Forms não cria um registro quando um processo de curta duração é chamado.

Usando o valor do identificador de invocação, você pode rastrear o status do processo de longa duração. Por exemplo, você pode usar o valor do identificador de invocação do processo para executar operações do Process Manager, como encerrar uma instância de processo em execução.

**Exemplo de processo de vida curta**

A ilustração a seguir é um exemplo de um processo de vida curta chamado *MyApplication/EncryptDocument*.

>[!NOTE]
>
>Este processo não se baseia em um processo AEM Forms existente. Para acompanhar os exemplos de código que discutem como invocar este processo, crie um processo chamado `MyApplication/EncryptDocument` usando o Workbench. (Consulte [Uso do Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Quando esse processo de vida curta é chamado, ele executa as seguintes ações:

1. Obtém o documento PDF não seguro passado para o processo como um valor de entrada.
1. Criptografa o documento PDF com uma senha. O nome do parâmetro de entrada para este processo é `inDoc` e o tipo de dados é document.
1. Salva o documento PDF criptografado por senha como um arquivo PDF no sistema de arquivos local. Esse processo retorna o documento PDF criptografado como um valor de saída. O nome do parâmetro de saída deste processo é `outDoc` e o tipo de dados é document.

   Esse processo é concluído de forma síncrona no mesmo thread de execução do qual foi chamado. O nome deste processo de curta duração é `MyApplication/EncryptDocument` e sua operação é `invoke`.

   >[!NOTE]
   >
   >Normalmente, um processo de curta duração consiste em mais de três ações. Crie um processo usando a Bancada. (Consulte [Uso do Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

   *A programação com AEM Forms* descreve as seguintes maneiras de invocar este processo de curta duração de forma programática:

   * [Invocando um processo de curta duração transmitindo um documento não seguro usando o AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting) (usando um aplicativo do Flex)
   * [Chamando um processo de vida curta usando a API de Invocação](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-short-lived-process-using-the-invocation-api) (API de Invocação Java™)
   * [Chamando o AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding) (exemplo de serviço Web)
   * [Chamando o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) (exemplo de serviço Web)
   * [Chamando o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref) (exemplo de serviço Web)
   * [Chamando o AEM Forms usando dados BLOB via HTTP](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http) (exemplo de serviço Web)
   * [Chamando o AEM Forms usando DIME](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime) (exemplo de serviço Web)
   * [Chamar o processo MyApplication/EncryptDocument usando REST](/help/forms/developing/invoking-aem-forms-using-rest.md)

**Exemplo de processo de vida longa**

A ilustração a seguir é um exemplo de um processo de longa vida.

Esse processo é chamado quando um candidato envia um formulário de empréstimo. O processo não é concluído até que um gestor de empréstimos aprove ou rejeite a solicitação de empréstimo. O nome deste processo de longa duração é *FirstAppSolution/PreLoanProcess* e sua operação é `invoke_Async`. Esse processo deve ser chamado de forma assíncrona. Para obter informações sobre como invocar programaticamente esse processo de longa duração, consulte [Invocando Processos de Longa Vida Centrados em Humanos](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

>[!NOTE]
>
>Este processo pode ser criado seguindo o tutorial especificado em [Criando seu Primeiro Aplicativo AEM Forms](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63).
