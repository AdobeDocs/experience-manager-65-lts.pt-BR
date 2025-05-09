---
title: Iniciar APIs de serviços de documento a partir do fluxo de trabalho do AEM
description: Saiba como chamar os serviços de documento do AEM no DDX ou nas entradas fornecidas. Veja também como converter PDF para PDF/A
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 0%

---

# Iniciar APIs de serviços de documento a partir do fluxo de trabalho do AEM  {#initiate-document-services-apis-from-aem-workflow}

## Assembler {#assembler}

O AEM Forms fornece fluxos de trabalho personalizados para chamar as seguintes APIs de serviço do Assembler:

* **invoke**: invoca operações especificadas no DDX de entrada nas entradas fornecidas.
* **toPDFA**: converte o documento PDF de entrada em um documento PDF/A.

### Chamar fluxo de trabalho DDX {#invoke-ddx-workflow}

O fluxo de trabalho **Invocar DDX** invoca a API de serviço do Assembler `Invoke`, que você pode usar para reunir ou desmontar documentos, adicionar marca d&#39;água a uma PDF e assim por diante.

1. Arraste a etapa de fluxo de trabalho **[!UICONTROL Invocar DDX]** para a guia Forms Workflow no Sidekick.
1. Clique duas vezes na etapa de fluxo de trabalho adicionada para editar o componente.
1. Na caixa de diálogo Editar componente, configure documentos de entrada, opções de ambiente e documentos de saída e clique em **[!UICONTROL OK]**.

#### Documentos de entrada {#input-documents}

O fluxo de trabalho Chamar DDX requer os seguintes documentos de entrada:

* **DDX**: é uma entrada obrigatória para a etapa de fluxo de trabalho Chamar DDX e pode ser especificada selecionando uma das seguintes opções no menu suspenso de entrada DDX.

   * *Relativo à Carga*: o arquivo de entrada DDX é relativo à pasta de carga do item de fluxo de trabalho.
   * *Usar carga*: a carga do item de fluxo de trabalho é usada como o documento DDX de entrada.
   * *Caminho absoluto*: o caminho absoluto para o documento DDX no repositório do CRX.

* **Criar mapa a partir de carga**: quando selecionado, todos os documentos na pasta de carga são adicionados ao Mapa do documento de entrada para a API `invoke` no Assembler. O nome do nó de cada documento é usado como uma chave no mapa.

* **Mapa do Documento de Entrada**: especifica o Mapa do Documento de Entrada. Você pode adicionar qualquer número de entradas, onde cada entrada especifica a chave do documento no mapa e a origem do documento.

#### Opções de ambiente {#environment-options}

A guia Opções de ambiente permite definir várias opções de processamento para a API invoke.

* *Nível de Log do Trabalho*: especifica o nível de log para os logs de processamento.
* *Validar Somente*: verifica a validade do DDX de entrada.

* *Falha ao errar*: especifica se a chamada para o serviço Assembler deve falhar em caso de erro. O valor padrão é Falso.

#### Documentos de saída {#output-documents}

Dependendo do DDX de entrada, a API invoke pode produzir vários documentos de saída. A guia Documentos de saída permite selecionar onde o documento de saída será salvo.

1. *Salvar Saída na Carga*: salva os documentos de saída na pasta de carga útil ou substitui a carga útil, se a carga útil for um arquivo.
1. *Mapa do Documento de Saída*: Permite especificar explicitamente onde salvar cada documento de saída, adicionando uma entrada por documento de saída. Cada entrada especifica o documento e onde salvá-lo. Um documento de saída pode substituir o conteúdo ou ser salvo na pasta de conteúdo. É útil quando há vários documentos de saída.

1. *Log de Trabalho*: especifica onde salvar o documento de log de trabalho, o que é útil para solucionar falhas.

### Converter em fluxo de trabalho do PDF/A {#convert-to-pdf-a-workflow}

A etapa de fluxo de trabalho Converter em PDF/A chama a API de serviço do Assembler `toPDFA`. Ele é usado para converter documentos do PDF em documentos compatíveis com o PDF/A.

1. Arraste a etapa de fluxo de trabalho **[!UICONTROL ConvertToPDFA]** para a guia Forms Workflow no Sidekick.

1. Clique duas vezes na etapa de fluxo de trabalho adicionada para editar o componente.
1. Na caixa de diálogo Editar componente, configure documentos de entrada, opções de conversão e documentos de saída e clique em **[!UICONTROL OK]**.

#### Documentos de entrada {#input-documents-1}

Especifique a origem do documento a ser convertido em um documento compatível com PDF/A de uma das seguintes maneiras.

* *Relativo à Carga*: o documento de entrada é relativo à pasta de carga do item de fluxo de trabalho.
* *Usar carga*: a carga do item de fluxo de trabalho é usada como o documento de entrada.
* *Caminho absoluto*: o caminho absoluto do documento de entrada no repositório do CRX.

#### Opções de conversão {#conversion-options}

As Opções de conversão permitem especificar opções que alteram o processo de conversão do PDF/A.

* *Conformidade* : especifica o padrão PDF/A que o PDF/A de saída deve atender.
* *Nível de Resultado* : especifica o nível de log a ser usado para logs de conversão do PDF/A.
* *Assinaturas* : especifica como as assinaturas no documento de entrada devem ser processadas durante a conversão.
* *Espaço de Cor* : especifica o espaço de cor predefinido a ser usado para o documento PDF/A de saída.
* *Verificar* Conversão: especifica se o documento PDF/A convertido deve ser verificado quanto à conformidade com o PDF/A após a conversão.
* *Nível de Log do Trabalho* : especifica o nível de log a ser usado para processar logs.

* *Esquema de Extensão de Metadados* : especifica o caminho para o esquema de extensão de metadados a ser usado para propriedades XMP nos metadados do documento PDF.

#### Documentos de saída {#output-documents-1}

A guia Documentos de saída permite especificar o destino dos documentos de saída

* *Documento PDFA*: especifica o local onde o documento PDF/A convertido é salvo. Ele pode substituir o documento de carga útil ou ser salvo na pasta de carga útil.
* *Log de conversão*: especifica o local onde os logs de conversão são salvos. Ele pode substituir o documento de carga útil ou ser salvo na pasta de carga útil.

## Forms {#forms}

O fluxo de trabalho Renderizar formulário PDF é um invólucro sobre a API de serviço do Forms `renderPDFForm` para criar um formulário PDF usando um modelo XDP e dados xml.

### Renderizar fluxo de trabalho do PDF Form {#render-pdf-form-workflow}

1. Arraste a etapa Renderizar fluxo de trabalho do PDF Form na guia Forms Workflow no Sidekick.
1. Clique duas vezes na etapa de fluxo de trabalho adicionada para editar o componente.
1. Na caixa de diálogo Editar componente, configure documentos de entrada, documentos de saída e parâmetros adicionais e clique em **[!UICONTROL OK]**.

#### Documentos de entrada {#input-documents-2}

* *Arquivo de modelo*: especifica o local do modelo XDP. É um campo obrigatório.

* *Documento de Dados*: especifica o local do xml de dados que precisa ser mesclado com o modelo.

#### Documentos de saída {#output-documents-2}

* *Documento de saída*: - especifica o nome do formulário PDF gerado.

#### Parâmetros adicionais {#additional-parameters}

* *Raiz de Conteúdo*: especifica o caminho para a pasta no repositório onde os fragmentos ou imagens usados no modelo XDP de entrada são armazenados.
* *Enviar URL*: especifica a URL de envio padrão para o formulário PDF gerado.
* *Localidade*: especifica a localidade padrão para o formulário PDF gerado.
* *Versão do Acrobat*: especifica a versão do Acrobat de destino para o formulário do PDF gerado.
* *PDF Marcado*: especifica se o PDF gerado deve ficar acessível.
* *Documento XCI*: especifica o caminho para o arquivo XCI.

## Saída {#output}

O Fluxo de Trabalho de Geração de PDF Não Interativo é um wrapper em torno da API de serviço de Saída `generatePDFOutput`. É usado para gerar documentos não interativos do PDF a partir de modelo XDP e xml de dados.

### Gerar fluxo de trabalho de saída do PDF não interativo   {#generate-non-interactive-pdf-output-workflow-nbsp}

1. Arraste o workflow Gerar saída do PDF não interativa para a guia Forms Workflow no Sidekick.
1. Clique duas vezes na etapa de fluxo de trabalho adicionada para editar o componente.
1. Na caixa de diálogo Editar componente, configure documentos de entrada, documentos de saída e parâmetros adicionais e clique em **[!UICONTROL OK]**.

#### Documentos de entrada {#input-documents-3}

* *Arquivo de modelo*: especifica o local do modelo XDP. É um campo obrigatório.

* *Documento de Dados*: especifica o local do xml de dados que precisa ser mesclado com o modelo.

#### Documento de saída {#output-document}

*Documento de saída*: especifica o nome do formulário PDF gerado.

#### Parâmetros adicionais {#additional-parameters-1}

* *Raiz de Conteúdo*: especifica o caminho para a pasta no repositório onde os fragmentos ou imagens usados no modelo XDP de entrada são armazenados.
* *Localidade*: especifica a localidade padrão para o formulário PDF gerado.
* *Versão do Acrobat*: especifica a versão do Acrobat de destino para o formulário do PDF gerado.
* PDF linearizado: especifica se o PDF gerado deve ser otimizado para visualização na Web.
* *PDF Marcado*: especifica se o PDF gerado deve ficar acessível.
* *Documento XCI*: especifica o caminho para o arquivo XCI.
