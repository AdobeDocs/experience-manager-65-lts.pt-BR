---
title: Configuração de serviços de armazenamento para rascunhos e envios
description: Saiba como configurar o armazenamento para rascunhos e envios
topic-tags: publish
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Configuração de serviços de armazenamento para rascunhos e envios {#configuring-storage-services-for-drafts-and-submissions}

## Visão geral {#overview}

Com o AEM Forms, você pode armazenar:

* **Rascunhos**: um formulário de trabalho em andamento que os usuários finais preenchem e salvam para depois e enviam depois.

* **Envios**: formulários enviados contendo dados fornecidos pelo usuário.

Os serviços de dados e metadados do AEM Forms Portal fornecem suporte a rascunhos e envios. Por padrão, os dados são armazenados na instância de publicação, que é então replicada revertida para a instância de autor configurada para estar disponível para filtragem para outras instâncias de publicação.

A preocupação com a abordagem pronta para uso existente é que ela armazene todos os dados na instância de publicação, incluindo os dados que podem ser Informações pessoais identificáveis (PII).

Além da abordagem padrão mencionada acima, uma implementação alternativa também está disponível para enviar diretamente os dados do formulário para processamento, em vez de salvá-lo localmente. Os clientes que estiverem preocupados com o armazenamento de dados potencialmente confidenciais na instância de publicação podem escolher a implementação alternativa em que os dados serão enviados para um servidor de processamento. Como o processamento ocorre na instância do autor, ele normalmente permanece em uma zona segura.

>[!NOTE]
>
>Ao usar a ação enviar do Portal do Forms ou habilitar a opção Armazenar dados no portal de formulários no formulário adaptável, os dados do formulário são armazenados no repositório do AEM. Em um ambiente de produção, é recomendável não armazenar dados de formulário de rascunho ou enviados no repositório do AEM. Em vez disso, você deve integrar o componente de rascunhos e envio a um armazenamento seguro, como o banco de dados corporativo, para armazenar rascunhos e dados de formulários enviados.
>
>Para obter mais informações, consulte [Amostra para integrar o componente de rascunhos e envios ao banco de dados](/help/forms/using/integrate-draft-submission-database.md).

## Configuração dos serviços de rascunhos e envios do Forms Portal {#configuring-forms-portal-drafts-and-submissions-services}

Na Configuração do Console da Web do AEM ( `https://[host]:'port'/system/console/configMgr`), clique para abrir a **Configuração de Rascunho e Envio do Forms Portal** no modo de edição.

Especifique os valores para propriedades com base em seus requisitos, conforme descrito abaixo:

### Serviços prontos para uso para armazenar dados na instância de publicação {#out-of-the-box-services-to-store-data-on-publish-instance}

Os dados são revertidos e replicados na instância de autor configurada.

<table>
 <tbody>
  <tr>
   <th>Propriedade</th>
   <th>Valor</th>
  </tr>
  <tr>
   <td>Serviço de Dados de Rascunho do Portal Forms (Identificador do serviço de dados de rascunho (<strong>draft.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Serviço de Metadados de Rascunho do Portal do Forms (Identificador do serviço de metadados de rascunho (<strong>rascunho.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Serviço de Envio de Dados do Forms Portal (Identificador para envio de serviço de dados (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Serviço de Metadados de Envio do Forms Portal (Identificador para enviar serviço de metadados (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceImpl<br /> </td>
  </tr>
 </tbody>
</table>

### Serviços prontos para uso para armazenar dados na instância de processamento remoto {#out-of-the-box-services-to-store-data-on-remote-processing-instance}

Os dados são enviados diretamente para a instância remota configurada

<table>
 <tbody>
  <tr>
   <th>Propriedade</th>
   <th>Valor</th>
  </tr>
  <tr>
   <td>Serviço de Dados de Rascunho do Portal Forms (Identificador do serviço de dados de rascunho (<strong>draft.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Serviço de Metadados de Rascunho do Portal do Forms (Identificador do serviço de metadados de rascunho (<strong>rascunho.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Serviço de Envio de Dados do Forms Portal (Identificador para envio de serviço de dados (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Serviço de Metadados de Envio do Forms Portal (Identificador para enviar serviço de metadados (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceRemoteImpl<br /> </td>
  </tr>
 </tbody>
</table>

Além da configuração especificada acima, forneça informações sobre a instância de processamento remoto configurada.

Na Configuração do Console da Web do AEM ( `https://[host]:'port'/system/console/configMgr`), clique para abrir o **Serviço de Configurações do AEM DS** no modo de edição. Na caixa de diálogo Serviço de Configurações do AEM DS, forneça informações sobre o URL do servidor de processamento, o nome de usuário do servidor de processamento e a senha.

>[!NOTE]
>
>Uma amostra de implementação também é fornecida para armazenar dados do usuário em um banco de dados. Para entender como configurar serviços de dados e metadados para armazenar dados do usuário em um banco de dados externo, consulte [Amostra para integração do componente de rascunhos e envios ao banco de dados](/help/forms/using/integrate-draft-submission-database.md).
