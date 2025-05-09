---
title: Exibição principal para gerenciamento de permissões
description: Saiba mais sobre a nova interface de toque que facilita o gerenciamento de permissões.
contentOwner: sarchiz
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 1%

---


# Exibição principal para gerenciamento de permissões{#principal-view-for-permissions-management}

## Visão geral {#overview}

O AEM 6.5 apresenta o Gerenciamento de permissões para usuários e grupos. A funcionalidade principal permanece a mesma da interface clássica, mas é mais amigável e eficiente.

## Como usar {#how-to-use}

### Acesso à interface {#accessing-the-ui}

O novo gerenciamento de permissões com base em interface é acessado por meio do cartão Permissões, em Segurança, conforme mostrado abaixo:

![Interface de Gerenciamento de Permissões](assets/screen_shot_2019-03-17at63333pm.png)

A nova exibição facilita a análise de todo o conjunto de privilégios e restrições para uma determinada entidade de segurança em todos os caminhos nos quais as Permissões foram concedidas explicitamente. Isso elimina a necessidade de ir para

CRXDE para gerenciar privilégios e restrições avançados. Ela foi consolidada na mesma visão. A visualização assume como padrão o Grupo &quot;todos&quot;.

![Exibição do grupo &quot;todos&quot;](assets/unu-1.png)

Há um filtro que permite ao usuário selecionar o tipo de entidades de segurança a serem observadas em **Usuários**, **Grupos** ou **Todos os** e procurar qualquer entidade de segurança **.**

![Pesquisar tipos de Entidades de Segurança](assets/image2019-3-20_23-52-51.png)

### Exibindo permissões para um Principal {#viewing-permissions-for-a-principal}

O quadro à esquerda permite que os usuários rolem para baixo para encontrar qualquer principal ou pesquisar por um Grupo ou um Usuário com base no filtro selecionado, conforme mostrado abaixo:

![Exibir Permissões para uma Entidade de Segurança](assets/doi-1.png)

Clicar no nome mostra as permissões atribuídas à direita. O painel de permissões mostra a lista de Entradas de controle de acesso em caminhos específicos, juntamente com as restrições configuradas.

![Exibir Lista de ACLs](assets/trei-1.png)

### Adicionando uma nova Entrada de Controle de Acesso para um Principal {#adding-new-access-control-entry-for-a-principal}

Novas permissões podem ser adicionadas adicionando uma Entrada de controle de acesso. Basta clicar no botão Adicionar ACE.

![Adicionar nova ACL para uma Entidade](assets/patru.png)

Isso exibe a janela mostrada abaixo. A próxima etapa é escolher um caminho em que a permissão deve ser configurada.

![Configurar caminho de permissões](assets/cinci-1.png)

Aqui, um caminho é selecionado onde você pode configurar uma permissão para **dam-users**:

![Exemplo de configuração para dam-users](assets/sase-1.png)

Depois que o caminho é selecionado, o fluxo de trabalho volta para essa tela, onde o usuário pode selecionar um ou mais privilégios dos namespaces disponíveis (como `jcr`, `rep` ou `crx`), conforme mostrado abaixo.

Os privilégios podem ser adicionados pesquisando usando o campo de texto e selecionando na lista.

>[!NOTE]
>
>Para obter uma lista completa de privilégios e descrições, consulte [Administração de Usuários, Grupos e Direitos de Acesso](/help/sites-administering/user-group-ac-admin.md#access-right-management).

![Permissão de pesquisa para um determinado caminho.](assets/image2019-3-21_0-5-47.png) ![Adicionar nova entrada para &#39;dam-users&#39; como mostrado por um caminho selecionado em colunas verticais.](assets/image2019-3-21_0-6-53.png)

Depois que a lista de privilégios for selecionada, o usuário poderá escolher o Tipo de permissão: Negar ou Permitir, conforme mostrado abaixo.

![Selecionar permissão](assets/screen_shot_2019-03-17at63938pm.png) ![Selecionar permissão](assets/screen_shot_2019-03-17at63947pm.png)

### Uso de restrições {#using-restrictions}

Além da lista de privilégios e do Tipo de permissão em um determinado caminho, essa tela também permite adicionar restrições para controle de acesso refinado, como mostrado abaixo:

![Adicionar restrições](assets/image2019-3-21_1-4-14.png)

>[!NOTE]
>
>Para obter mais informações sobre o que significa cada restrição, consulte [a Documentação do Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html).

É possível adicionar restrições, como mostrado abaixo, escolhendo o tipo de restrição, inserindo o valor e clicando no ícone **+**.

![Adicionar o tipo de restrição](assets/sapte-1.png) ![Adicionar o tipo de restrição](assets/opt-1.png)

O novo ACE é refletido na Lista de controle de acesso conforme mostrado abaixo. Observe que `jcr:write` é um privilégio agregado que inclui `jcr:removeNode` que foi adicionado acima, mas não é mostrado abaixo como coberto por `jcr:write`.

### Edição de ACEs {#editing-aces}

As Entradas de controle de acesso podem ser editadas selecionando um principal e escolhendo o ACE que você deseja editar.

Por exemplo, aqui você pode editar a entrada abaixo para **dam-users** clicando no ícone de lápis à direita:

![Adicionar restrição](assets/image2019-3-21_0-35-39.png)

A tela de edição é exibida com ACEs configuradas pré-selecionadas, que podem ser excluídas clicando no ícone cruzado ao lado delas ou novos privilégios podem ser adicionados ao caminho fornecido, conforme mostrado abaixo.

![Editar entrada](assets/noua-1.png)

Aqui o privilégio `addChildNodes` é adicionado para **dam-users** no caminho especificado.

![Adicionar privilégio](assets/image2019-3-21_0-45-35.png)

As alterações podem ser salvas clicando no botão **Salvar** na parte superior direita, e são refletidas nas novas permissões para **dam-users**, conforme mostrado abaixo:

![Salvar alterações](assets/zece-1.png)

### Exclusão de ACEs {#deleting-aces}

As Entradas de Controle de Acesso podem ser excluídas para remover todas as permissões concedidas a um principal em um caminho específico. O ícone X ao lado de ACE pode ser usado para excluí-lo, conforme mostrado abaixo:

![Excluir ACEs](assets/image2019-3-21_0-53-19.png) ![Excluir ACEs](assets/unspe.png)

### Combinações de Privilégios da Interface Clássica {#classic-ui-privilege-combinations}

A nova interface de permissões usa explicitamente o conjunto básico de privilégios em vez de combinações predefinidas que não refletem realmente os privilégios subjacentes exatos que foram concedidos.

Causou confusão sobre o que exatamente está sendo configurado. A tabela a seguir lista o mapeamento entre as combinações de privilégios da interface clássica para os privilégios reais que as constituem:

<table>
 <tbody>
  <tr>
   <th>Combinações de Privilégios da Interface Clássica</th>
   <th>Privilégio de Permissões da Interface do Usuário</th>
  </tr>
  <tr>
   <td>Ler</td>
   <td><code>jcr:read</code></td>
  </tr>
  <tr>
   <td>Modificar</td>
   <td><p><code>jcr:modifyProperties</code></p> <p><code>jcr:lockManagement</code></p> <p><code>jcr:versionManagement</code></p> </td>
  </tr>
  <tr>
   <td>Criar</td>
   <td><p><code>jcr:addChildNodes</code></p> <p><code>jcr:nodeTypeManagement</code></p> </td>
  </tr>
  <tr>
   <td>Excluir</td>
   <td><p><code>jcr:removeNode</code></p> <p><code>jcr:removeChildNodes</code></p> </td>
  </tr>
  <tr>
   <td>Ler ACL</td>
   <td><code>jcr:readAccessControl</code></td>
  </tr>
  <tr>
   <td>Editar ACL</td>
   <td><code>jcr:modifyAccessControl</code></td>
  </tr>
  <tr>
   <td>Replicar</td>
   <td><code>crx:replicate</code></td>
  </tr>
 </tbody>
</table>
