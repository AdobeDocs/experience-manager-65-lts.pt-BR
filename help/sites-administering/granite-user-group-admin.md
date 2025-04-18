---
title: Operações do Granite - Administração de usuários e grupos
description: Saiba mais sobre a administração de usuários e grupos do Granite.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---


# Operações do Granite - Administração de usuários e grupos{#granite-operations-user-and-group-administration}

Como o Granite incorpora a implementação do Repositório do CRX da especificação da API JCR, ele tem sua própria administração de usuários e grupos.

Essas contas são a base subjacente das [contas do AEM](/help/sites-administering/security.md) e quaisquer alterações de conta feitas com a administração do Granite serão refletidas se/quando as contas forem acessadas do [console de Usuários do AEM](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console) (por exemplo, `http://localhost:4502/useradmin`). No console Usuários do AEM, também é possível gerenciar os privilégios e outras especificidades do AEM.

Os consoles de administração de usuários e grupos do Granite estão disponíveis no console **[Ferramentas](/help/sites-administering/tools-consoles.md)** da interface otimizada para toque:

![Console de ferramentas](assets/chlimage_1-72a.png)

Escolher **Usuários** ou **Grupos** do console Ferramentas abre o console apropriado. Em ambos, você pode executar ações usando a caixa de cliques e depois as ações da barra de ferramentas, ou abrindo os detalhes da conta por meio do link em **Nome**.

* [Administração de usuários](#user-administration)

  ![chlimage_1-73](assets/chlimage_1-73a.png)

  O console **Usuários** lista:

   * o nome de usuário
   * o nome de login do usuário (nome da conta)
   * qualquer título que a conta recebeu

* [Administração de grupo](#group-administration)

  ![Console de gerenciamento de usuários](assets/chlimage_1-74a.png)

  O console **Grupos** lista:

   * o nome do grupo
   * a descrição do grupo
   * o número de usuários/grupos no grupo

## Administração de usuários {#user-administration}

### Adicionar um novo usuário {#adding-a-new-user}

1. Usar o ícone **Adicionar Usuário**:

   ![Ícone Adicionar Usuário](do-not-localize/chlimage_1-1.png)

1. O formulário **Criar Usuário** abre:

   ![Formulário Detalhes do Usuário](assets/chlimage_1-75a.png)

   Aqui você pode inserir os detalhes do usuário para a conta (a maioria é padrão e autoexplicativa):

   * **ID**

     É a identificação exclusiva da conta de usuário. É obrigatório e não pode conter espaços.

   * **Endereço de email**
   * **Senha**

     Uma senha é obrigatória.

   * **Senha do Retype**

     Isso é obrigatório, pois é necessário para confirmação da senha.

   * **Nome**
   * **Sobrenome**
   * **Telefone**
   * **Cargo**
   * **Rua**
   * **Móvel**
   * **Cidade**
   * **CEP**
   * **País**
   * **Estado**
   * **Título**
   * **Gênero**
   * **Sobre**
   * **Configurações da conta**

      * **Status**
Você pode sinalizar a conta como **ativa** ou **inativa**.

   * **Foto**

     Aqui você pode carregar uma foto para usar como avatar.

     Tipos de arquivo aceitos: `.jpg .png .tif .gif`

     Tamanho preferencial: `240x240px`

   * **Adicionar usuário aos grupos**

     Use o menu suspenso de seleção para selecionar grupos dos quais o usuário deve ser membro. Depois de selecionado, use o **X** pelo nome para desmarcar antes de salvar.

   * **Grupos**

     Uma lista de grupos dos quais o usuário é membro no momento. Use o **X** pelo nome para desmarcar antes de salvar.

1. Quando tiver definido a conta de usuário, use:

   * **Cancelar** para cancelar o registro.
   * **Salve** para concluir o registro. A criação da conta de usuário será confirmada com uma mensagem.

### Editar um usuário existente {#editing-an-existing-user}

1. Acesse os detalhes do usuário no link com o nome do usuário no console Usuários.

1. Agora você pode editar os detalhes como em [Adicionando um Novo Usuário](#adding-a-new-user).

1. Acesse os detalhes do usuário no link com o nome do usuário no console Usuários.

1. Agora você pode editar os detalhes como em [Adicionando um Novo Usuário](#adding-a-new-user).

### Alterando a senha de um usuário existente {#changing-the-password-for-an-existing-user}

1. Acesse os detalhes do usuário no link com o nome do usuário no console Usuários.

1. Agora você pode editar os detalhes como em [Adicionando um Novo Usuário](#adding-a-new-user). Em **Configurações de Conta**, há um link para **Alterar Senha**.

   ![Caixa de diálogo Configurações da Conta](assets/chlimage_1-76a.png)

1. A caixa de diálogo **Alterar Senha** é aberta. Digite e digite novamente a nova senha, juntamente com a senha. Use **OK** para confirmar as alterações.

   ![Caixa de diálogo Alterar senha](assets/chlimage_1-77a.png)

   Uma mensagem confirmará que a senha foi alterada.

### Atribuição rápida de grupo {#quick-group-assignment}

1. Use a caixa de clique para sinalizar um ou mais usuários.
1. Usar o ícone **Grupos**:

   ![Usando o ícone Grupos](do-not-localize/chlimage_1-2.png)

   Para abrir o menu suspenso de seleção de grupo:

   ![Seletor de grupos](assets/chlimage_1-78a.png)

1. Na caixa de seleção, é possível marcar ou desmarcar os grupos aos quais a conta de usuário deve pertencer.

1. Quando você tiver atribuído ou desatribuído os grupos, use:

   * **Cancelar** para anular as alterações
   * **Salvar** para confirmar as alterações

### Deletando Detalhes do Usuário Existente {#deleting-existing-user-details}

1. Use a caixa de clique para sinalizar um ou mais usuários.
1. Use o ícone **Excluir** para excluir os detalhes do usuário:

   ![Excluir detalhes do usuário existente](do-not-localize/chlimage_1-3.png)

1. Você será solicitado a confirmar a exclusão e, em seguida, uma mensagem confirmará que a exclusão ocorreu.

## Administração de grupo {#group-administration}

### Adicionar um novo grupo {#adding-a-new-group}

1. Use o ícone Adicionar grupo:

   ![Adicionar um novo grupo](do-not-localize/chlimage_1-4.png)

1. O formulário **Criar Grupo** abre:

   ![Formulário Detalhes do Grupo](assets/chlimage_1-79a.png)

   Aqui você pode inserir os detalhes do grupo:

   * **ID**

     É um identificador exclusivo do grupo. Isso é obrigatório e não pode conter espaços.

   * **Nome**

     Um nome para o grupo; ele é mostrado no console Grupos.

   * **Descrição**

     Uma descrição do grupo.

   * **Adicionar membros ao grupo**

     Use o menu suspenso de seleção para selecionar usuários a serem adicionados ao grupo. Depois de selecionado, use o **X** pelo nome para desmarcar antes de salvar.

   * **Membros do grupo**

     Uma lista de usuários no grupo. Use o **X** pelo nome para desmarcar antes de salvar.

1. Quando tiver definido o grupo, use:

   * **Cancelar** para cancelar o registro.
   * **Salve** para concluir o registro. A criação do grupo será confirmada com uma mensagem.

### Editar um grupo existente {#editing-an-existing-group}

1. Acesse os detalhes do grupo no link com o nome do grupo no console Grupos.

1. Agora você pode editar e salvar os detalhes como em [Adicionando um Novo Grupo](#adding-a-new-group).

### Copiando um Grupo Existente {#copying-an-existing-group}

1. Use a caixa de clique para sinalizar um grupo.
1. Use o ícone **Copiar** para copiar os detalhes do grupo:

   ![Copiar um grupo existente](do-not-localize/chlimage_1-5.png)

1. O formulário **Editar Configurações do Grupo** será aberto.

   A ID do grupo será a mesma do original, mas com o prefixo `Copy of`. Edite essa ID porque ela não pode conter espaços. Todos os outros detalhes são os mesmos do original.

   Agora você pode editar e salvar os detalhes como em [Adicionando um Novo Grupo](#adding-a-new-group).

### Excluindo um grupo existente {#deleting-an-existing-group}

1. Use a caixa de clique para sinalizar um ou mais grupos.
1. Use o ícone **Excluir** para excluir os detalhes do grupo:

   ![Excluindo um grupo existente](do-not-localize/chlimage_1-6.png)

1. Você será solicitado a confirmar a exclusão e, em seguida, uma mensagem confirmará que a exclusão ocorreu.
