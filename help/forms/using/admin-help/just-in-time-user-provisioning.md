---
title: Provisionamento de usuário just-in-time
description: Use o provisionamento just-in-time para adicionar usuários ao Gerenciamento de usuários após a autenticação bem-sucedida e atribua dinamicamente funções e grupos relevantes ao novo usuário.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: a7c566f0-ec89-4e98-b31d-e3f23f7e3524
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# Provisionamento de usuário just-in-time {#just-in-time-user-provisioning}

O AEM Forms é compatível com o provisionamento just-in-time de usuários que ainda não existem no Gerenciamento de usuários. Com o provisionamento just-in-time, os usuários são adicionados automaticamente ao Gerenciamento de usuários depois que suas credenciais forem autenticadas com êxito. Além disso, as funções e os grupos relevantes são atribuídos dinamicamente ao novo usuário.

## Necessidade de provisionamento de usuários just-in-time {#need-for-just-in-time-user-provisioning}

É assim que a autenticação tradicional funciona:

1. Quando um usuário tenta fazer logon no AEM Forms, o Gerenciamento de usuários passa as credenciais do usuário sequencialmente para todos os provedores de autenticação disponíveis. (As credenciais de logon incluem uma combinação de nome de usuário/senha, tíquete Kerberos, assinatura PKCS7 e assim por diante.)
1. O provedor de autenticação valida as credenciais.
1. O provedor de autenticação verifica se o usuário existe no banco de dados de Gerenciamento de usuários. Os seguintes resultados são possíveis:

   **Existe:** Se o usuário estiver atualizado e desbloqueado, o Gerenciamento de Usuários retornará uma autenticação com êxito. No entanto, se o usuário não for atual ou estiver bloqueado, o Gerenciamento de usuários retornará uma falha de autenticação.

   **Não existe:** o Gerenciamento de Usuários retorna uma falha de autenticação.

   **Inválido:** o Gerenciamento de Usuários retorna uma falha de autenticação.

1. O resultado retornado pelo provedor de autenticação é avaliado. Se o provedor de autenticação retornou êxito de autenticação, o usuário tem permissão para fazer logon. Caso contrário, o Gerenciamento de usuários verificará com o próximo provedor de autenticação (etapas 2-3).
1. A falha de autenticação será retornada se nenhum provedor de autenticação disponível validar as credenciais do usuário.

Quando o provisionamento just-in-time é implementado, um novo usuário é criado dinamicamente no Gerenciamento de usuários se um dos provedores de autenticação validar as credenciais do usuário. (Após a etapa 3 no procedimento de autenticação tradicional, acima.)

## Implementar o provisionamento de usuários just-in-time {#implement-just-in-time-user-provisioning}

### APIs para provisionamento just-in-time {#apis-for-just-in-time-provisioning}

O AEM Forms fornece as seguintes APIs para provisionamento just-in-time:

```java
package com.adobe.idp.um.spi.authentication  ;
publ ic interface IdentityCreator {
/**
* Tries  to create a user with the  in formation  provided in the <code>UserProvisioningBO</code> object.
* If the user is successfully created, a valid AuthResponse is returned along with the information using which the user was created.
* It is the responsibility of the IdentityCreator to set the User obje ct  in the cre dential map with th e  ke y  <code>UMA u thenticationUtil.authenticatedUserKey</code>
* The credentials are available in the <code>UserProvisioningBO</code> object in the 'credentials' property.
* If the IdentityCreator is unable to create a user due to any reason, it returns <code>null</code>
* @param userBO An object of <code>com.adobe. i dp.um . spi.authenti c ationUserProvisioningBO</code>
* @return */public AuthResponse create(UserProvisioningBO userBO);
/**
* Returns the name of the IdentityCreator which will be registered in preferences.
* This name is used to associate the IdentityProvider with the Auth Provider Configuration in the domain.
* @return The name of the Identity Creator which is recognized in Configuration.
*/
public String getName();
}
package com.adobe.idp.um.spi.authentication;
import com.adobe.idp.um.api.infomodel.User;
public interface AssignmentProvider {
/**
* Tries to assign roles or permissions or group memberships to users created via Just-in-time provisioning.
* @param user The User created via the Just-in-time provisioning process.
* @return a Boolean flag indicating whether the assignment was successful or not.
*/
public Boolean assign(User user);
/**
* Returns the name of the AssignmentProvider through which it is registered under preferences.
* This name is used to associate the AssignmentProvider with the Auth Provider Configuration in the domain.
* @return The name of the AssignmentProvider which is recognized in Configuration.
*/public String getName();
}
```

### Considerações ao criar um domínio habilitado para just-in-time {#considerations-while-creating-a-just-in-time-enabled-domain}

* Ao criar um `IdentityCreator` personalizado para um domínio híbrido, verifique se uma senha fictícia foi especificada para o usuário local. Não deixe este campo de senha vazio.
* Recomendação: use `DomainSpecificAuthentication` para validar credenciais de usuário em relação a um domínio específico.

### Criar um domínio habilitado para just-in-time {#create-a-just-in-time-enabled-domain}

1. Escreva um DSC implementando as APIs na seção &quot;APIs para provisionamento just-in-time&quot;.
1. Implante o DSC no servidor do Forms.
1. Criar um domínio habilitado para just-in-time:

   * No Console de Administração, clique em Configurações > Gerenciamento de usuários > Gerenciamento de domínio > Novo domínio corporativo.
   * Configure o domínio e selecione Ativar provisionamento just-in-time. <!--Fix broken link (See Setting up and managing domains).-->
   * Adicionar provedores de autenticação. Ao adicionar provedores de autenticação, na tela Nova autenticação, selecione um Criador de identidade e um Provedor de atribuição registrados.

1. Salve o novo domínio.

## Nos bastidores {#behind-the-scenes}

Suponha que um usuário esteja tentando fazer logon no AEM Forms e um provedor de autenticação aceite suas credenciais de usuário. Se o usuário ainda não existir no banco de dados de Gerenciamento de usuários, a verificação de identidade do usuário falhará. Os formulários do AEM agora executam as seguintes ações:

1. Crie um objeto `UserProvisioningBO` com os dados de autenticação e coloque-o em um mapa de credenciais.
1. Com base nas informações de domínio retornadas por `UserProvisioningBO`, busque e chame o `IdentityCreator` e `AssignmentProvider` registrados para o domínio.
1. Chamar `IdentityCreator`. Se retornar um `AuthResponse` bem-sucedido, extraia `UserInfo` do mapa de credenciais. Envie-o para `AssignmentProvider` para atribuição de grupo/função e qualquer outro pós-processamento depois que o usuário for criado.
1. Se o usuário for criado com sucesso, retorne a tentativa de logon por ele como bem-sucedida.
1. Para domínios híbridos, obtenha informações do usuário dos dados de autenticação fornecidos ao provedor de autenticação. Se essas informações forem buscadas com sucesso, crie o usuário dinamicamente.

>[!NOTE]
>
>O recurso de provisionamento just-in-time vem com uma implementação padrão do `IdentityCreator` que você pode usar para criar usuários dinamicamente. Os usuários são criados com as informações associadas aos diretórios no domínio.
