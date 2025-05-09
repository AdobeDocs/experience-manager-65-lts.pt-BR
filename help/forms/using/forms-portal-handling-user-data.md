---
title: Portal Forms | Manuseio de dados do usuário
description: Saiba mais sobre como gerenciar dados do usuário, como acesso, exclusão e armazenamento de dados no AEM Forms Portal.
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Portal Forms | Manuseio de dados do usuário {#forms-portal-handling-user-data}

O Portal [!DNL AEM Forms] fornece componentes que você pode usar para listar formulários adaptáveis, formulários HTML5 e outros ativos do Forms na página [!DNL AEM Sites]. Além disso, você pode configurá-lo para exibir rascunhos e formulários adaptáveis enviados e formulários HTML5 para um usuário conectado. Para obter mais informações sobre o Forms Portal, consulte [Introdução à publicação de formulários em um portal](/help/forms/using/introduction-publishing-forms.md).

Quando um usuário conectado salva um formulário adaptável como rascunho ou o envia, eles são exibidos nas guias Rascunhos e envios no Portal do Forms. Os dados para formulários em rascunho ou enviados são armazenados no armazenamento de dados configurado para implantação do AEM. Os rascunhos e envios de usuários anônimos não são exibidos na página do Forms Portal; no entanto, os dados são armazenados no armazenamento de dados configurado. Consulte [Configurando serviços de armazenamento para rascunhos e envios](/help/forms/using/configuring-draft-submission-storage.md).

## Dados do usuário e armazenamentos de dados {#user-data-and-data-stores}

O Forms Portal armazena dados para formulários de rascunho e enviados nos seguintes cenários:

* A ação de envio configurada no formulário adaptável é **Ação de Envio do Portal do Forms**.
* Para ações de envio diferentes de **Ação de Envio do Forms Portal**, a opção **[!UICONTROL Armazenar dados no Forms Portal]** está habilitada nas propriedades **[!UICONTROL Envio]** do contêiner de formulário adaptável.

Para cada rascunho e formulário enviado para usuários conectados e anônimos, o Portal do Forms armazena os seguintes dados:

* Metadados de formulário, como nome do formulário, caminho do formulário, ID de rascunho ou envio, caminho de anexos e ID de dados do usuário
* Anexo de formulário como bytes de dados
* Dados de formulário como bytes de dados

Dependendo da persistência do armazenamento de dados configurado, os dados de rascunhos e formulários enviados são armazenados nos seguintes locais.

<table>
 <tbody>
  <tr>
   <td><p><strong>Tipo de persistência</strong></p> </td>
   <td><p><strong>Armazenamento de dados</strong></p> </td>
   <td><p><strong>Local</strong></p> </td>
  </tr>
  <tr>
   <td><p>Padrão</p> </td>
   <td><p>Repositório AEM de instâncias de Autor e Publicação</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Remoto</p> </td>
   <td><p>Repositório AEM de instâncias de Autor e AEM remotas</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Banco de dados</p> </td>
   <td><p>Repositório AEM da instância do autor e tabelas do banco de dados</p> </td>
   <td>Tabelas do banco de dados <code>data</code>, <code>metadata</code> e <code>additionalmetadata</code></td>
  </tr>
 </tbody>
</table>

## Acessar e excluir dados do usuário {#access-and-delete-user-data}

Você pode acessar dados de rascunho e de formulários enviados para usuários conectados e anônimos nos armazenamentos de dados configurados e, se necessário, excluí-los.

### Instâncias do AEM {#aem-instances}

Todos os rascunhos e dados de formulários enviados em instâncias do AEM (autor, publicação ou remoto) para usuários conectados e anônimos são armazenados no nó `/content/forms/fp/` do repositório aplicável do AEM. Toda vez que um usuário conectado ou anônimo salva um rascunho ou envia um formulário, um `draft ID` ou `submission ID`, um `user data ID` e um `ID` aleatório para cada anexo (se aplicável) é gerado. Está associado ao respectivo rascunho ou envio.

#### Acessar dados do usuário {#access-user-data}

Quando um usuário conectado salva um rascunho ou envia um formulário, um nó secundário é criado com sua ID de usuário. Por exemplo, os dados de rascunhos e envios de Sarah Rose cuja ID de usuário é `srose` são armazenados no nó `/content/forms/fp/srose/` no repositório do AEM. No nó da ID de usuário, os dados são organizados em uma estrutura hierárquica.

A tabela a seguir explica como os dados de todos os rascunhos de `srose` são armazenados no repositório do AEM.

>[!NOTE]
>
>Uma estrutura exata como `drafts` é replicada para formulários enviados para `srose` no nó `/content/forms/fp/srose/submit/`.
>
>Todos os rascunhos e envios de usuários `anonymous` são armazenados no nó `/content/forms/fp/anonymous/`, que organiza rascunhos e envios para todos os usuários anônimos nos nós `draft` e `submit`.

| Nó | Descrição |
|---|---|
| `/content/forms/fp/srose/drafts` | Dados do nó de container para todos os rascunhos do usuário |
| `/content/forms/fp/srose/drafts/attachments/` | Organiza todos os anexos para o usuário com base na ID de rascunho |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Contém um anexo para a ID selecionada em formato binário |
| `/content/forms/fp/srose/drafts/metadata/` | Organiza metadados de formulário para o usuário com base na ID de rascunho |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Contém metadados de formulário para a ID de rascunho selecionada |
| `/content/forms/fp/srose/drafts/data/` | Organiza dados de formulários para o usuário com base na ID de dados do usuário |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Contém dados de formulário para a ID de dados do usuário selecionada em formato binário |

#### Excluir dados do usuário {#delete-user-data}

Para excluir completamente os dados do usuário nos rascunhos e envios de um usuário conectado dos sistemas AEM, você deve excluir o nó `user ID` de um usuário específico do nó do autor. Exclua manualmente os dados de todas as instâncias aplicáveis do AEM.

Rascunhos e dados de envio para todos os usuários anônimos são armazenados nos nós `drafts` e `submit` comuns em `/content/forms/fp/anonymous`. Não há um método para encontrar dados para um usuário anônimo específico, a menos que algumas informações identificáveis sejam conhecidas. Nesse caso, você pode pesquisar informações que identifiquem o usuário anônimo no repositório do AEM e excluir manualmente o nó que o contém de todas as instâncias aplicáveis do AEM para remover dados do sistema do AEM. No entanto, para excluir dados de todos os usuários anônimos, você pode excluir o nó `anonymous` para remover os rascunhos e os dados de envio de todos os usuários anônimos.

### Banco de dados {#database}

Quando o AEM é configurado para armazenar dados em um banco de dados, os dados de rascunho e envio do Forms Portal são armazenados nas seguintes tabelas do banco de dados para usuários conectados e anônimos:

* dados
* metadados
* metadados adicionais

#### Acessar dados do usuário {#access-user-data-1}

Para acessar os dados de rascunhos e envios de um usuário conectado e anônimo nas tabelas do banco de dados, execute o seguinte comando do banco de dados. Na consulta, substitua `logged-in user` pela ID de usuário cujos dados você deseja acessar ou por `anonymous` para usuários anônimos.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Excluir dados do usuário {#delete-user-data-1}

Para excluir das tabelas do banco de dados os rascunhos e os dados de envio de um usuário conectado, execute o seguinte comando do banco de dados. Na consulta, substitua `logged-in user` pela ID de usuário cujos dados você deseja excluir ou por `anonymous` para usuários anônimos. Para deletar dados de um usuário anônimo específico do banco de dados, você deve encontrá-los usando algumas informações identificáveis e deletá-los das tabelas do banco de dados que contêm as informações.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```
