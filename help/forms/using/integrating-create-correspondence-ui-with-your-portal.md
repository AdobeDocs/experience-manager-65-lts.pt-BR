---
title: Integração da solução Criar correspondência com seu portal personalizado
description: Saiba como integrar criar interface do usuário de correspondência ao portal personalizado
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 496b125b-b091-4843-ba9f-2479dbeba07b
source-git-commit: 16f57ae1663f035d1dc39005d37426c7a0d8dc16
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 4%

---

# Integração da solução `Create Correspondence` com seu portal personalizado{#integrating-create-correspondence-ui-with-your-custom-portal}

## Visão geral {#overview}

Este artigo detalha como você pode integrar a solução `Create Correspondence` ao seu ambiente.

## Chamada baseada em URL {#url-based-invocation}

Uma maneira de chamar o aplicativo `Create Correspondence` de um portal personalizado é preparar a URL com os seguintes parâmetros de solicitação:

* o identificador do modelo de correspondência (usando o parâmetro cmLetterId).

* o URL para os dados XML obtidos da fonte de dados desejada (usando o parâmetro cmDataUrl ).

Por exemplo, o portal personalizado prepararia o URL como\
`https://'[server]:[port]'/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, que pode ser o href de um link no portal.

>[!NOTE]
>
>Chamar dessa maneira não é seguro, pois os parâmetros necessários são transmitidos como uma solicitação do GET, expondo o mesmo (claramente visível) no URL.

>[!NOTE]
>
>Antes de chamar o aplicativo `Create Correspondence`, salve e carregue os dados para chamar a interface do usuário `Create Correspondence` no dataURL especificado. Esse processo pode ser feito no próprio portal personalizado ou por meio de outro processo de back-end.

## Chamada embutida baseada em dados {#inline-data-based-invocation}

Outra maneira mais segura de chamar o aplicativo `Create Correspondence` é acessar a URL em https://&#39;[server]:[port]&#39;/[contextPath]/aem/forms/createcorrespondence.html. Execute esta URL ao enviar os parâmetros e dados para chamar o aplicativo `Create Correspondence` como uma solicitação POST, ocultando-os do usuário final. Este fluxo de trabalho também significa que agora você pode transmitir os dados XML para o aplicativo `Create Correspondence` em linha (como parte da mesma solicitação, usando o parâmetro `cmData`). Esse fluxo de trabalho não era possível ou ideal na abordagem anterior.

### Parâmetros para especificação de carta {#parameters-for-specifying-letter}

| **Nome** | **Tipo** | **Descrição** |
| --- | --- | --- |
| cmLetterInstanceId | String | O identificador para a ocorrência de carta. |
| cmLetterId | String | O nome do modelo de Carta. |

A ordem dos parâmetros na tabela especifica a preferência dos parâmetros usados para carregar a correspondência.

### Parâmetros para especificação da fonte de dados XML {#parameters-for-specifying-the-xml-data-source}

<table>
 <tbody>
  <tr>
   <td><strong>Nome</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>Dados XML de um arquivo de origem usando protocolos básicos, como cq, ftp, http ou file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>String</td> 
   <td>Usando dados xml disponíveis na ocorrência de carta.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Booleano</td> 
   <td>Para reutilizar os dados de teste anexados em um dicionário de dados.</td> 
  </tr>
 </tbody>
</table>

A ordem dos parâmetros na tabela especifica a preferência dos parâmetros usados para carregar os dados XML.

### Outros parâmetros {#other-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Nome</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Booleano</td> 
   <td>Verdadeiro para abrir a carta no modo de visualização<br /> </td> 
  </tr>
  <tr>
   <td>Aleatório</td> 
   <td>Carimbo de data e hora</td> 
   <td>Para resolver problemas de cache do navegador.</td> 
  </tr>
 </tbody>
</table>

Se você usar o protocolo http ou cq para `cmDataURL`, a URL de `http/cq` deverá estar acessível anonimamente.
