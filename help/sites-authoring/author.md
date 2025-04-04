---
title: 'Criação  '
description: Conceitos de criação e publicação no Adobe Experience Manager 6.5.
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: d1297182b801ff4db163b8ae91332f5aebb94b9b
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 32%

---

# Criação  {#authoring}

## Conceito de criação (e publicação) {#concept-of-authoring-and-publishing}

O AEM fornece dois ambientes:

* Autor
* Publicação

Eles interagem para permitir que você disponibilize conteúdo no seu site, para que os visitantes possam lê-lo.

O ambiente de criação oferece os mecanismos para criação, atualização e análise desse conteúdo, antes de realmente publicá-lo:

* Um autor cria e revisa o conteúdo (que pode ser de vários tipos; por exemplo, páginas, ativos, publicações e assim por diante)
* que será, em algum momento, publicado no seu site.

![Visão Geral dos Ambientes](assets/chlimage_1-132.png)

No ambiente de criação, a funcionalidade do AEM é disponibilizada por meio de duas interfaces. No ambiente de publicação, você projeta toda a aparência da interface disponibilizada aos usuários.

### Ambiente de criação {#author-environment}

Autores(as) trabalham no que é conhecido como **ambiente de criação**. Isso fornece uma interface fácil de usar (interface gráfica do usuário (GUI ou UI)) para criar o conteúdo. Ela está localizada atrás do firewall de uma empresa que fornece proteção total e requer que o autor faça logon, usando uma conta que recebeu os direitos de acesso apropriados.

>[!NOTE]
>
>Sua conta precisa ter os direitos de acesso necessários para criar, editar ou publicar conteúdo.

Dependendo de como sua instância e seus direitos de acesso pessoal estão configurados, é possível executar muitas tarefas no conteúdo, incluindo (entre outras):

* gerar novo conteúdo ou editar conteúdo existente em uma página
* usar modelos predefinidos para criar novas páginas de conteúdo
* criar, editar e gerenciar ativos e coleções
* criar, editar e gerenciar suas publicações
* desenvolver suas campanhas e os recursos relacionados
* mover, copiar ou excluir páginas de conteúdo, ativos e assim por diante
* publicar (ou desfazer a publicação) páginas, ativos e assim por diante

Além disso, há tarefas administrativas que ajudam a gerenciar o conteúdo:

* fluxos de trabalho que controlam como as alterações são gerenciadas; por exemplo, impor uma revisão antes da publicação
* projetos que coordenam tarefas individuais

>[!NOTE]
>
>O AEM também é [administrado](/help/sites-administering/home.md) (para a maioria das tarefas) do ambiente de criação.

#### Ambiente de publicação {#publish-environment}

Quando pronto, o conteúdo do site do AEM é publicado no **ambiente de publicação**. Aqui, as páginas do site são disponibilizadas para o público desejado de acordo com a aparência da interface projetada.

Normalmente, o ambiente de publicação está localizado dentro da zona desmilitarizada; em outras palavras, disponível para a Internet, mas não mais sob a proteção total da rede interna.

>[!NOTE]
>
>Infelizmente, às vezes há uma sobreposição na terminologia usada. Isso pode acontecer com:
>
>* **Publicar/Desfazer a publicação**
>  Esses são os termos principais para as ações que tornam o conteúdo publicamente disponível no ambiente de publicação (ou não).
>
>* **Ativar / Desativar**
>  Estes termos são sinônimos de publicar/desfazer a publicação.
>
>* **Replicar / Replicação**
>  Esses são os termos técnicos usados para indicar a movimentação de dados (por exemplo, conteúdo da página, arquivos, código, comentários do usuário) de um ambiente para outro; ou seja, ao publicar ou reverter a replicação de comentários do usuário.
>

#### Dispatcher {#dispatcher}

Para otimizar o desempenho para os visitantes do seu site, o **[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=pt-BR)** implementa o balanceamento de carga e o cache.
