---
title: Sincronização do Adaptive Forms com modelos de formulário XFA
description: Saiba como sincronizar formulários com arquivos XFA/XDP. Ele reutiliza campos de formulários sincronizados com alterações feitas aos campos correspondentes nos arquivos XFA/XDP.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---

# Sincronização do Adaptive Forms com modelos de formulário XFA{#synchronizing-adaptive-forms-with-xfa-form-templates}

A Adobe <span class="preview"> recomenda usar os [Componentes principais](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=pt-BR) de captura de dados moderna e extensível para [criar um novo Forms Adaptável](/help/forms/using/create-an-adaptive-form-core-components.md) ou [adicionar o Forms Adaptável às páginas do AEM Sites](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Esses componentes representam um avanço significativo na criação do Forms adaptável, garantindo experiências de usuário impressionantes. Este artigo descreve a abordagem mais antiga para criar o Forms adaptável usando componentes de base. </span>

## Introdução {#introduction}

Você pode criar um Formulário adaptável com base em um modelo de formulário XFA (arquivo `*.XDP`). Essa reutilização permite que você preserve seu investimento em formulários XFA existentes. Para obter informações sobre como usar um modelo de formulário XFA para criar um formulário adaptável, [Crie um formulário adaptável com base em um modelo](../../forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p).

Você pode reutilizar campos do arquivo XDP no formulário adaptável. Esses campos são chamados de campos vinculados. As propriedades dos campos vinculados (como scripts, rótulos e formato de exibição) são copiadas do arquivo XDP. Você também pode optar por substituir o valor de algumas dessas propriedades.

O AEM Forms fornece uma maneira de ajudar a manter os campos dos formulários adaptáveis sincronizados com qualquer alteração feita posteriormente nos campos correspondentes no arquivo XDP. Este artigo explica como você pode habilitar essa sincronização.

![Você pode arrastar campos de um formulário XFA para um formulário adaptável](assets/drag-drop-xfa.gif.gif)

No ambiente de criação do AEM Forms, você pode arrastar campos de um formulário XFA (à esquerda) para um formulário adaptável (à direita)

## Pré-requisitos {#prerequisites}

Para usar as informações deste artigo, é recomendável estar familiarizado com as seguintes áreas:

* [Criação de um formulário adaptável](../../forms/using/creating-adaptive-form.md)

* XFA (XML Forms Architecture, arquitetura XML do)

Para usar os ativos fornecidos para o exemplo no artigo, baixe o pacote de exemplo conforme explicado na próxima seção, [Pacote de exemplo](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-sample-package-p).

## Pacote de exemplo {#sample-package}

O artigo usa um exemplo para demonstrar como sincronizar o formulário adaptável com um modelo de formulário XFA atualizado. Os ativos usados no exemplo estão disponíveis em um pacote, que pode ser baixado da seção [Downloads](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-downloads-p) deste artigo.

Depois de fazer upload do pacote, é possível visualizar esses ativos na interface do usuário do AEM Forms.

Instalar o pacote usando o Gerenciador de Pacotes: `https://<server>:<port>/crx/packmgr/index.jsp`

O pacote contém os seguintes ativos:

1. `sample-form.xdp`: o modelo de formulário XFA usado como exemplo

1. `sample-xfa-af`: o formulário adaptável baseado no arquivo sample-form.xdp. No entanto, esse formulário adaptável não inclui campos. Na próxima etapa, adicione conteúdo a este formulário adaptável.

### Adicionar conteúdo ao formulário adaptável {#add-content-to-adaptive-form-br}

1. Navegue até https://&lt;server>:&lt;port>/aem/forms.html. Insira suas credenciais, se solicitado.
1. Abra o sample-af-xfa para edição no modo de autor.
1. No navegador Conteúdo da barra lateral, escolha a guia Objetos do modelo de dados. Arraste NumericField1 e TextField1 para o Formulário adaptável.
1. Altere o Título de NumericField1 de **Campo Numérico** para **Campo Numérico AF.**

>[!NOTE]
>
>Nas etapas anteriores, você substituiu uma propriedade de um campo no arquivo XDP. Portanto, essa propriedade não é sincronizada se a propriedade correspondente no arquivo XDP for editada posteriormente.

## Detecção de alterações no arquivo XDP {#detecting-changes-in-xdp-file}

Sempre que houver qualquer alteração em um arquivo XDP ou fragmento, a interface do usuário do AEM Forms sinaliza todos os formulários adaptáveis baseados no arquivo XDP ou no fragmento.

Depois de atualizar um arquivo XDP, é necessário carregá-lo novamente na interface do usuário do AEM Forms para que as alterações sejam sinalizadas.

Como exemplo, atualizemos o arquivo `sample-form.xdp` usando estas etapas:

1. Navegue até `https://<server>:<port>/projects.html.` Insira suas credenciais, se solicitado.
1. Clique na guia Forms à esquerda.
1. Baixe o arquivo `sample-form.xdp` no computador local. O arquivo XDP é baixado como um arquivo `.zip`, que pode ser extraído usando qualquer utilitário de descompactação de arquivo.

1. Abra o arquivo `sample-form.xdp` e altere o título do campo TextField1 de **Campo de Texto** para **Meu Campo de Texto**.

1. Carregue o arquivo `sample-form.xdp` de volta para a interface do usuário do AEM Forms.

Se um arquivo XDP for atualizado, você verá um ícone no editor ao editar os formulários adaptáveis com base no arquivo XDP. Esse ícone indica que o formulário adaptável está fora de sincronia com o arquivo XDP. Na imagem a seguir, veja o ícone ao lado na barra lateral.

![Ícone para mostrar que o formulário adaptável está fora de sincronia com o arquivo XDP](assets/sync-af-xfa.png)

## Sincronização de formulários adaptáveis com o arquivo XDP mais recente {#synchronizing-adaptive-forms-with-the-latest-xdp-file}

Quando um formulário adaptável que está fora de sincronia com o arquivo XDP for aberto para criação na próxima vez, a seguinte mensagem será exibida: **O Modelo de esquema/formulário para o Formulário adaptável foi atualizado. `Click Here` para trocar sua base pela nova versão.**

Clicar na mensagem sincroniza os campos no formulário adaptável com os campos correspondentes no arquivo XDP.

Para o exemplo usado neste artigo, abra `sample-xfa-af` no modo de criação. A mensagem é exibida na parte inferior do formulário adaptável.

![Mensagem solicitando que você sincronize o formulário adaptável com o arquivo XDP](assets/sync-af-xfa-1.png)

### Atualização das propriedades {#updating-the-properties}

Todas as propriedades que foram copiadas do arquivo XDP para o formulário adaptável são atualizadas, exceto as propriedades que foram explicitamente substituídas no formulário adaptável (da Caixa de diálogo Componente) pelo Autor. A lista de propriedades que foram atualizadas está disponível nos logs do servidor.

Para atualizar as propriedades no formulário adaptável de exemplo, clique no link (rotulado `"Click Here"`) na mensagem. O título de TextField1 é alterado de **Campo de Texto** para **Meu Campo de Texto**.

![propriedade-atualização](assets/update-property.png)

>[!NOTE]
>
>O campo numérico de AF do rótulo não foi alterado porque você substituiu esta propriedade na caixa de diálogo de propriedades do componente, conforme descrito em [Adicionar conteúdo a formulários adaptáveis](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-add-content-to-adaptive-form-br-p).

### Adição de novos campos do arquivo XDP ao formulário adaptável   {#adding-new-fields-from-xdp-file-to-adaptive-form-nbsp}

Todos os campos adicionados posteriormente ao arquivo XDP original aparecem na guia Hierarquia do formulário e você pode arrastar esses novos campos para o formulário adaptável.

Não é necessário clicar no link da mensagem de erro para atualizar os campos na guia Hierarquia do formulário.

### Campos excluídos no arquivo XDP {#deleted-fields-in-xdp-file}

Se um campo que foi copiado anteriormente para um formulário adaptável for excluído de um arquivo XDP, uma mensagem de erro será exibida no modo de criação informando que o campo não existe no arquivo XDP. Nesses casos, exclua manualmente o campo do formulário adaptável ou limpe a propriedade `bindRef` na caixa de diálogo do componente.

As etapas a seguir ilustram esse fluxo de uso para os ativos no exemplo usado neste artigo:

1. Atualize o arquivo `sample-form.xdp` e exclua NumericField1.
1. Carregar o arquivo `sample-form.xdp` na interface do usuário do AEM Forms
1. Abra o formulário adaptável `sample-xfa-af` para criação. A seguinte mensagem de erro é exibida: O Modelo de esquema/formulário para o Formulário adaptável foi atualizado. `Click Here` para trocar sua base pela nova versão.

1. Clique no link (rotulado como &quot;`Click Here`&quot;) na mensagem. Uma mensagem de erro é exibida observando que o campo não existe mais no arquivo XDP.

![Erro exibido ao excluir um elemento do arquivo XDP](assets/no-element-xdp.png)

O campo que foi excluído também é marcado com um ícone para indicar um erro no campo.

![Ícone de erro no campo](assets/error-field.png)

>[!NOTE]
>
>Os campos no formulário adaptável que têm uma associação incorreta (um valor `bindRef` inválido na caixa de diálogo de edição) também são considerados campos excluídos. Se o autor não corrigir esses erros e publicar o formulário adaptável, o campo será tratado como um campo de formulário adaptável normal não vinculado e será incluído na seção desvinculada do arquivo XML de saída.

## Downloads {#downloads}

Pacote de conteúdo para o exemplo neste artigo

[Obter arquivo](assets/sample-xfa-af-sync-1.0.zip)
