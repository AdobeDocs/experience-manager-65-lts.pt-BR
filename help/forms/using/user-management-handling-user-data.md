---
title: Gerenciamento de usuários do Forms | Manuseio de dados do usuário
description: Saiba como o componente de Gerenciamento de usuários do AEM Forms JEE permite criar, autorizar e gerenciar usuários que precisam de acesso ao AEM Forms.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---

# Gerenciamento de usuários do Forms | Manuseio de dados do usuário {#forms-user-management-handling-user-data}

O gerenciamento de usuários é um componente do AEM Forms JEE que permite criar, gerenciar e autorizar usuários do AEM Forms a acessar o AEM Forms. O gerenciamento de usuários usa domínios como diretórios para obter informações do usuário. Os seguintes tipos de domínio são compatíveis:

**Domínios locais**: este tipo de domínio não está conectado a um sistema de armazenamento de terceiros. Em vez disso, os usuários e grupos são criados localmente e residem no banco de dados de Gerenciamento de usuários. As senhas são armazenadas localmente e a autenticação é feita usando um banco de dados local.

**Domínios híbridos**: esse tipo de domínio não está conectado a um sistema de armazenamento de terceiros. Em vez disso, os usuários e grupos são criados localmente e residem no banco de dados de Gerenciamento de usuários. Diferentemente dos domínios locais, os domínios híbridos usam um provedor de autenticação externo, que pode ser LDAP, Kerberos, SAML ou um provedor de autenticação personalizado.

**Domínios da empresa**: consiste em usuários e grupos que residem em um sistema de armazenamento de terceiros, como um diretório LDAP. O gerenciamento de usuários não grava no sistema de armazenamento de terceiros. Em vez disso, o Gerenciamento de usuários sincroniza as informações do usuário e do grupo com o banco de dados do Gerenciamento de usuários. Domínios Enterprise também usam um provedor de autenticação externo, que pode ser LDAP, Kerberos, SAML ou um provedor de autenticação personalizado.

<!-- Fix broken links For more information about how user management works and configured, see AEM Forms JEE administration help. -->

## Dados do usuário e armazenamentos de dados {#user-data-and-data-stores}

O gerenciamento de usuários armazena dados do usuário em um banco de dados como, por exemplo, My Sql, Oracle, MS® SQL Server e IBM® DB2®. Além disso, qualquer usuário que tenha feito logon pelo menos uma vez nos aplicativos do Forms em um autor do AEM em `https://'[server]:[port]'lc`, ele será criado no repositório do AEM. Portanto, o gerenciamento de usuários é armazenado nos seguintes armazenamentos de dados:

* Banco de dados
* Repositório do AEM
* Armazenamento de terceiros, como o diretório LDAP

>[!NOTE]
>
>Os dados armazenados em armazenamentos de terceiros estão fora do escopo deste documento. Entre em contato diretamente com o fornecedor de terceiros para gerenciar os dados do usuário nesses armazenamentos.

### Banco de dados {#database}

O gerenciamento de usuários armazena dados do usuário nas seguintes tabelas de banco de dados:

<table>
 <tbody>
  <tr>
   <td>Tabela do banco de dados</td>
   <td>Descrição</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalEntity</code></td>
   <td><p>Armazena informações sobre entidades principais. Um principal pode ser um usuário, um grupo ou uma função.</p> <p> </p> </td>
  </tr>
  <tr>
   <td><code>EdcPrincipalUserEntity</code></td>
   <td>Armazena informações de identificação pessoal (PII) de usuários. Ele contém uma entrada para cada usuário de domínios locais, corporativos e híbridos.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalLocalAccountEntity</code></p> <p><code class="code">EdcPrincipalLocalAccount
       </code>(bancos de dados Oracle e MS® SQL)</p> </td>
   <td>Armazena dados somente para usuários locais.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalEmailAliasEntity</code></p> <p><code class="code">EdcPrincipalEmailAliasEn
       </code>(bancos de dados Oracle e MS® SQL)</p> </td>
   <td>Contém entradas de todos os usuários de domínios locais, corporativos e híbridos. Ele contém IDs de email do usuário.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalGrpCtmntEntity</code></p> <p><code>EdcPrincipalGrpCtmntEnti</code><br /> (bancos de dados Oracle e MS® SQL)</p> </td>
   <td>Armazena o mapeamento entre usuários e grupos.</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalRoleEntity</code></td>
   <td>Armazena o mapeamento entre funções e entidades para usuários e grupos.</td>
  </tr>
  <tr>
   <td><code>EdcPriResPrmEntity</code></td>
   <td>Armazena o mapeamento entre a entidade de segurança e as permissões para usuários e grupos.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalMappingEntity</code></p> <p><code>EdcPrincipalMappingEntit</code><br /> (bancos de dados Oracle e MS® SQL)</p> </td>
   <td>Armazena valores de atributos antigos e novos correspondentes a uma entidade de segurança.<br /> </td>
  </tr>
 </tbody>
</table>

### Repositório do AEM {#aem-repository}

Os dados de gerenciamento de usuários para usuários que acessaram pelo menos uma vez os aplicativos da Forms em `https://'[server]:[port]'lc` também são armazenados no repositório do AEM.

## Acessar e excluir dados do usuário {#access-and-delete-user-data}

Você pode acessar e exportar dados de gerenciamento de usuários para usuários nos bancos de dados de gerenciamento de usuários e no repositório do AEM e, se necessário, excluí-los permanentemente.

### Banco de dados {#database-1}

Para exportar ou excluir dados do usuário do banco de dados de gerenciamento de usuários, você deve se conectar ao banco de dados usando um cliente de banco de dados e descobrir a ID principal com base em algumas PIIs do usuário. Por exemplo, para recuperar a ID da entidade de segurança de um usuário usando uma ID de logon, execute o seguinte comando `select` no banco de dados.

No comando `select`, substitua `<user_login_id>` pela ID de logon do usuário cuja ID principal você deseja recuperar.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Depois de saber a ID principal, é possível exportar ou excluir os dados do usuário.

#### Exportar dados do usuário {#export-user-data}

Execute os seguintes comandos de banco de dados para que você possa exportar dados de gerenciamento de usuários para uma ID principal de tabelas de banco de dados. No comando `select`, substitua `<principal_id>` pela ID principal do usuário cujos dados você deseja exportar.

>[!NOTE]
>
>Os comandos a seguir usam nomes de tabelas de bancos de dados em My SQL e bancos de dados IBM® DB2®. Ao executar esses comandos em bancos de dados Oracle e MS® SQL, substitua os seguintes nomes de tabela nos comandos:
>
>* Substituir `EdcPrincipalLocalAccountEntity` por `EdcPrincipalLocalAccount`
>
>* Substituir `EdcPrincipalEmailAliasEntity` por `EdcPrincipalEmailAliasEn`
>
>* Substituir `EdcPrincipalMappingEntity` por `EdcPrincipalMappingEntit`
>
>* Substituir `EdcPrincipalGrpCtmntEntity` por `EdcPrincipalGrpCtmntEnti`
>

```sql
Select * from EdcPrincipalLocalAccountEntity where refuserprincipalid in (Select id from EdcPrincipalUserEntity where refprincipalid in (Select id from EDCPRINCIPALENTITY where id='<principal_id>'));

Select * from EdcPrincipalEmailAliasEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalRoleEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPriResPrmEntity where refprinid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalUserEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalMappingEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalGrpCtmntEntity where refchildprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalEntity where id='<principal_id>';
```

#### Excluir dados do usuário {#delete-user-data}

Faça o seguinte para excluir das tabelas do banco de dados os dados de gerenciamento de usuários para uma ID principal.

1. Exclua os dados do usuário do repositório do AEM, se aplicável, conforme descrito em [Excluir dados do usuário](/help/forms/using/user-management-handling-user-data.md#delete-aem).
1. Desligue o servidor do AEM Forms.
1. Execute os seguintes comandos de banco de dados para que você possa excluir dados de gerenciamento de usuários de uma ID principal das tabelas de banco de dados. No comando `Delete`, substitua `<principal_id>` pela ID principal do usuário cujos dados você deseja excluir.

   ```sql
   Delete from EdcPrincipalLocalAccountEntity where refuserprincipalid in (Select id from EdcPrincipalUserEntity where refprincipalid in (select id from EdcPrincipalEntity where id='<principal_id>'));
   
   Delete from EdcPrincipalEmailAliasEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalRoleEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPriResPrmEntity where refprinid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalUserEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalMappingEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalGrpCtmntEntity where refchildprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalEntity where id='<principal_id>';
   ```

1. Inicie o servidor do AEM Forms.

### Repositório do AEM {#aem-repository-1}

Os usuários do Forms JEE têm os dados no repositório do AEM se acessaram a instância do autor do AEM Forms pelo menos um. Você pode acessar e excluir os dados do usuário no repositório do AEM.

#### Acessar dados do usuário {#access-user-data}

Para exibir o usuário criado no repositório do AEM, faça logon em `https://'[server]:[port]'/lc/useradmin` com credenciais de administrador do AEM. Observe que `server` e `port` na URL são os da instância de autor do AEM. Aqui, você pode procurar usuários com seus nomes de usuário. Clique duas vezes em um usuário para exibir informações como propriedades, permissões e grupos do usuário. A propriedade `Path` de um usuário especifica o caminho para o nó do usuário criado no repositório do AEM.

#### Excluir dados do usuário {#delete-aem}

Para excluir um usuário:

1. Vá para `https://'[server]:[port]'/lc/useradmin` com credenciais de administrador do AEM.
1. Procure um usuário e clique duas vezes no nome de usuário para abrir as propriedades dele. Copie a propriedade `Path`.
1. Vá para o AEM CRXDE Lite em `https://'[server]:[port]'/lc/crx/de/index.jsp` e navegue ou pesquise o caminho do usuário.
1. Exclua o caminho e clique em **[!UICONTROL Salvar tudo]** para excluir permanentemente o usuário do repositório do AEM.
