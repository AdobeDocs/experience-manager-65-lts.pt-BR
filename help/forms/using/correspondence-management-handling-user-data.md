---
title: Gerenciamento de correspondência | Manuseio de dados do usuário
description: Saiba mais sobre o Gerenciamento de correspondência e como lidar com dados do usuário em um ambiente do Adobe Experience Manager Forms.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Form Data Model
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Gerenciamento de correspondência | Manuseio de dados do usuário {#correspondence-management-handling-user-data}

O Gerenciamento de correspondência da AEM Forms permite criar, gerenciar e simplificar correspondências seguras e personalizadas de clientes. Ele fornece uma interface intuitiva para usuários empresariais que permite criar correspondências usando blocos de conteúdo e elementos de mídia pré-aprovados. Para obter mais informações sobre como criar correspondências, consulte [Criar correspondência](/help/forms/using/create-correspondence.md).

Quando um usuário empresarial ou agente salva uma correspondência como rascunho ou a envia, uma instância de carta é salva no repositório da AEM. A ocorrência de carta inclui dados de correspondência e metadados.

>[!NOTE]
>
>No AEM 6.5 Forms, o gerenciamento de correspondência não está disponível imediatamente. Se estiver atualizando de uma versão anterior do AEM Forms, instale o pacote de compatibilidade e migre seus ativos de gerenciamento de correspondência para continuar a usá-los no AEM 6.5 Forms. Para obter mais informações, consulte [Pacote de compatibilidade](/help/forms/using/compatibility-package.md).

## Dados do usuário e armazenamentos de dados {#data}

O Gerenciamento de correspondência armazena dados de rascunho e cartas enviadas no repositório do AEM somente se a instância de publicação estiver configurada para gerenciar instâncias de cartas. Para obter mais informações sobre a configuração, consulte [Propriedades de configuração do Gerenciamento de correspondência](/help/forms/using/cm-configuration-properties.md).

Dependendo da persistência do armazenamento de dados configurada para a implantação do AEM, os dados de rascunhos e correspondência enviados são armazenados nos seguintes locais.

<table>
 <tbody>
  <tr>
   <td><p><strong>Tipo de persistência</strong></p> </td>
   <td><p><strong>Armazenamento de dados</strong></p> </td>
   <td><p><strong>Local</strong></p> </td>
  </tr>
  <tr>
   <td><p>Padrão</p> </td>
   <td><p>Repositório AEM de instâncias de instância de publicação e de autor especificado na configuração de replicação reversa</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Remoto</p> </td>
   <td><p>Repositório AEM da instância do autor de processamento remoto</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code></p> </td>
  </tr>
 </tbody>
</table>

No local do repositório do AEM especificado acima:

* `[yyyy]/[mm]/[dd]` é a estrutura do nó baseada na data em que a instância de carta foi criada
* `[node-id]` é a ID atribuída à pasta que contém a letra
* `[letter-instance-name]` é o nome especificado ao salvar ou enviar uma carta

No nó [letter-instance-name], a seguinte estrutura de nó é criada e os dados de cada instância de carta são armazenados no repositório do AEM:

| Nó | Descrição |
|---|---|
| `extendedProperties` | Armazena propriedades de metadados da instância de carta. |
| `dataXML` | Armazena um arquivo dataXML que pode ser baixado, contendo os dados de correspondência em formato binário. |
| `processedXDP` | Inclui os detalhes do modelo XDP usado para criar a carta enviada. Este nó é criado somente para correspondências enviadas. |
| `submittedLetter` | Armazena os dados da carta enviada em formato binário baixável. Este nó é criado somente para correspondências enviadas. |

## Acessar e excluir dados do usuário {#access-and-delete-user-data}

Você pode acessar dados de correspondência de rascunho e enviados nos armazenamentos de dados configurados e, se necessário, excluí-los.

### Acessar dados do usuário {#access-user-data}

O Gerenciamento de correspondência fornece APIs que podem ser usadas para localizar e acessar instâncias de rascunho e de carta enviada. Usando as APIs, você pode localizar e abrir instâncias de cartas usando a ID de instância de cartas ou o usuário que salvou ou enviou a correspondência. Para obter mais informações, consulte [APIs para acessar instâncias de cartas](/help/forms/using/cm-apis-to-access-letter-instances.md).

Como alternativa, você pode navegar até a instância de carta no repositório do AEM usando o CRXDE Lite. Consulte [Dados do usuário e armazenamentos de dados](/help/forms/using/correspondence-management-handling-user-data.md#data) para obter informações sobre dados armazenados e o local do repositório.

### Excluir dados do usuário {#delete-user-data}

Para localizar uma ocorrência de carta contendo os dados de um usuário específico, é possível:

* Usar APIs do gerenciamento de correspondência se o nome da instância da carta ou o usuário que salvou o rascunho ou enviou a correspondência for conhecido
* Use a pesquisa de repositório do AEM usando informações de identificação pessoal, como ID de email ou nome, para localizar o nó onde as informações são armazenadas

Para excluir os dados do usuário de correspondências de rascunho e enviadas completamente dos sistemas do AEM, você deve excluir manualmente o nó da instância de correspondência de todas as instâncias aplicáveis do AEM.
