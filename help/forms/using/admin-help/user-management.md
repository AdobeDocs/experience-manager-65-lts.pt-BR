---
title: Gerenciamento de usuários
description: O Gerenciamento de usuários permite habilitar o SSO entre módulos do AEM Forms e aplicativos protegidos pelo Netegrity SiteMinder usando SAML. Este documento fornece mais informações sobre o Gerenciamento de usuários.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 5a87e340-053b-4b72-99a0-df14d7bf304c
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Gerenciamento de usuários {#user-management}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

O Gerenciamento de usuários permite habilitar o logon único (SSO) entre módulos de formulários do AEM e aplicativos protegidos pelo Netegrity SiteMinder usando a SAML (Security Assertion Markup Language). Quando o SSO é implementado, as páginas de logon do usuário dos formulários do AEM não são necessárias e não são exibidas se o usuário já estiver autenticado por meio do portal da empresa.

Para obter informações sobre como melhorar o desempenho da sincronização de diretório e banco de dados para DB2, consulte [Banco de dados IBM DB2: Executando comandos para manutenção regular](/help/forms/using/admin-help/ibm-db2-database-running-commands.md#ibm-db2-database-running-commands-for-regular-maintenance).

## Configurando o Gerenciamento de Usuários para um servidor LDAP habilitado para SSL {#configuring-user-management-for-an-ssl-enabled-ldap-server}

Se você tiver um servidor LDAP habilitado para SSL, configure o Gerenciamento de usuários para trabalhar com ele. (Consulte [Configurar o Gerenciamento de Usuários para um servidor LDAP habilitado para SSL](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)

## Definição de privilégios de usuário para uso com Segurança de documentos {#setting-user-privileges-for-use-with-document-security}

Crie um usuário administrador que tenha os privilégios apropriados para criar usuários e grupos. Se o ambiente do AEM Forms incluir Segurança de documentos, conceda o privilégio de gerenciar usuários convidados e locais a um usuário que será o administrador desses usuários. Atribua também a função de Usuário do console de administração, para fornecer ao usuário acesso ao console de administração. (Consulte [Criação e configuração de funções](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)

Para exibir usuários e grupos em domínios selecionados durante pesquisas de usuário de política, um superadministrador ou administrador de conjunto de políticas deve selecionar e adicionar domínios (criados no Gerenciamento de usuários) à lista de usuários e grupos visíveis para cada conjunto de políticas criado.

A lista de usuários e grupos visíveis é visível para o coordenador de conjuntos de políticas e é usada para restringir quais domínios o usuário final pode navegar ao escolher usuários ou grupos para adicionar às políticas. Se essa tarefa não for executada, o coordenador de definições de políticas não localizará nenhum usuário ou grupo para adicionar à política. Pode haver mais de um coordenador de conjunto de políticas para qualquer conjunto de políticas fornecido.

>[!NOTE]
>
>A criação de domínios deve ser feita antes que qualquer política possa ser criada.

### Definir usuários e grupos visíveis {#set-visible-users-and-groups}

Depois de instalar e configurar o ambiente do AEM Forms com a Segurança de documentos, configure todos os domínios apropriados no Gerenciamento de usuários.

1. No console de administração, clique em Serviços > Segurança de documentos > Políticas e, em seguida, clique na guia Conjuntos de políticas.
1. Selecione Conjunto de políticas globais e clique na guia Usuários e grupos visíveis.
1. Clique em Adicionar domínio(s) e adicione os domínios existentes conforme necessário.
1. Navegue até Serviços > segurança de documentos > Configuração > Minhas políticas e clique na guia Usuários e grupos visíveis.
1. Clique em Adicionar domínio(s) e adicione os domínios existentes conforme necessário.

## Restrições de usuário administrador {#administrator-user-restrictions}

Os usuários com determinados tipos de privilégios de administrador não podem acessar as páginas da Web do usuário final do Workspace por motivos de segurança. Como essas páginas da Web podem existir fora de um firewall, a permissão de tarefas no nível de administração pode representar um risco de segurança. Somente os usuários que têm privilégios de Administrador do Workspace ou Usuário do Workspace podem acessar as páginas da Web do usuário final.

>[!NOTE]
>
>O Flex Workspace está obsoleto para a versão do AEM Forms.
