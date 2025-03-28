---
title: 'Reutilizar conteúdo: gerenciador de vários sites e Live Copy'
description: Saiba mais sobre como reutilizar conteúdo com as Live Copies e o Gerenciador de vários sites.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Multi Site Manager
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '2665'
ht-degree: 19%

---

# Reutilizar conteúdo: gerenciador de vários sites e Live Copy{#reusing-content-multi-site-manager-and-live-copy}

O Gerenciador de vários sites (MSM) permite que você use o mesmo conteúdo de site em vários locais. O MSM usa a funcionalidade de Live Copy para fazer isso:

* Com o MSM é possível:

   * Criar um conteúdo uma vez e
   * Copiar este conteúdo e reutilizá-lo em outras áreas ([live copies](#live-copies)) do mesmo site ou de outros sites.

* O MSM mantém os relacionamentos (dinâmicos) entre o conteúdo original e as live copies, de modo que:

   * Quando você altera o conteúdo original, o original e as live copies são sincronizadas (para aplicar essas alterações às live copies também).
   * Você pode ajustar o conteúdo das live copies desconectando o relacionamento dinâmico de subpáginas individuais, componentes ou ambos. Ao fazer isso, as alterações na origem não são mais aplicadas à live copy.

Esta e as seguintes páginas abordam os problemas relacionados:

* [Criação e sincronização de Live Copies](/help/sites-administering/msm-livecopy.md)
* [Visão geral do console da Live Copy](/help/sites-administering/msm-livecopy-overview.md)
* [Configurar a sincronização da Live Copy](/help/sites-administering/msm-sync.md)
* [Conflitos de implantação do MSM](/help/sites-administering/msm-rollout-conflicts.md)
* [Práticas recomendadas do MSM](/help/sites-administering/msm-best-practices.md)

## Cenários possíveis {#possible-scenarios}

Há muitos casos de uso para o MSM e as live copies, alguns cenários incluem:

* **Multinacionais - da empresa global para a local**

  Um caso de uso típico que o MSM permite é a reutilização de conteúdo em vários sites multinacionais de mesmo idioma. Isso permite que o conteúdo principal seja reutilizado, ao mesmo tempo que permite variações nacionais.

  Por exemplo, a seção em inglês da amostra do site de referência We.Retail é criada para clientes nos EUA. A maior parte do conteúdo deste site também pode ser usada para outros sites We.Retail que atendem clientes que falam inglês de diferentes países e culturas. O conteúdo principal permanece o mesmo em todos os sites, enquanto ajustes regionais podem ser feitos.

  A seguinte estrutura pode ser usada para sites dos Estados Unidos, Reino Unido, Canadá e Austrália:

  ```xml
  /content
      |- we.retail
          |- language-masters
              |- en
      |- we.retail
          |- us
              |- en
      |- we.retail
          |- gb
              |- en
      |- we.retail
          |- ca
              |- en
      |- we.retail
          |- au
              |- en
  ```

  >[!NOTE]
  >
  >O MSM não traduz o conteúdo. Ele é usado para criar a estrutura necessária e implantar o conteúdo.
  >
  >
  >Consulte [Tradução de conteúdo para sites multilíngues](/help/sites-administering/translation.md) se desejar estender esse exemplo.

* **Nacional - da sede para as divisões regionais**

  Alternativamente, uma empresa com uma rede de revendedores pode querer sites separados para suas concessionárias individuais - cada um sendo uma variação do site principal fornecido pela sede. Pode ser uma única empresa com vários escritórios regionais ou um sistema nacional de franquias composto por um franqueador central e por vários franqueados locais.

  A sede pode fornecer as informações principais, enquanto as entidades regionais podem adicionar informações locais, como detalhes de contato, horários de abertura e eventos.

  ```xml
  /content
      |- head-office-Berlin
      |- branch-Hamburg
      |- branch-Stuttgart
      |- branch-Munich
      |- branch-Frankfurt
  ```

* **Várias versões**

  Ou você pode usar o MSM para criar versões de uma sub-ramificação específica. Por exemplo, um subsite de suporte que contém detalhes das diferentes versões de um produto específico, em que as informações básicas permanecem constantes e apenas os recursos atualizados devem ser alterados:

  ```xml
  /content
      |- support
          |- product X
              |- v5.0
              |- v4.0
              |- v3.0
              |- v2.0
              |- v1.0
  ```

  >[!NOTE]
  >
  >Nesse cenário, você deve decidir se faz uma cópia simples ou usa Live Copies.
  >
  >Há um equilíbrio de:
  >
  >  * Quanto do conteúdo principal precisa ser atualizado nas várias versões.
  >
  >Contra:
  >
  >  * Quantas cópias individuais devem ser ajustadas.

## MSM a partir da interface {#msm-from-the-ui}

O MSM é diretamente acessível por meio da interface usando várias opções do console apropriado. Para fornecer uma introdução, o seguinte lista os locais principais:

* **Criar Site** (**Sites**)

   * O MSM ajuda você a gerenciar vários sites que compartilham conteúdo em comum. Por exemplo, sites geralmente são fornecidos para públicos internacionais, de modo que a maior parte do conteúdo é comum em todos os países, com um subconjunto de conteúdo específico para cada país individual. O MSM permite [criar live copies que atualizam automaticamente um ou mais sites com base no seu site de origem](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Isso também ajuda a impor uma estrutura básica comum, usar o conteúdo em comum nos vários sites, manter uma aparência comum e concentrar os esforços no gerenciamento do conteúdo que realmente difere entre os sites.
   * Ela requer uma configuração de blueprint predefinida para especificar a origem.
   * Cria uma live copy da origem (predefinida).
   * Ele fornece ao usuário o botão **Implantação**.

* **Criar Live Copy** (**Sites**)

   * O MSM permite [criar uma live copy ad-hoc (única) de uma página individual ou subramificação de um site](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page); por exemplo, duplicar uma subramificação para fornecer informações sobre uma versão nova/atualizada de um produto.
   * Cria uma Live Copy ad-hoc (nenhuma configuração do blueprint é necessária).
   * Ele pode ser usado para criar (imediatamente) uma live copy de qualquer página/ramificação.
   * Requer **sincronização** (não fornece o botão **Implantação**).

* **Visualizar propriedades** (**Sites**)

   * Quando apropriado, esta opção ajuda você a [monitorar sua live copy](/help/sites-administering/msm-livecopy.md#monitoring-your-live-copy), fornecendo informações sobre o **Live Copy** y ou o **Blueprint** relacionados.

* **Referências** (**Sites**)

   * O painel [Referências](/help/sites-authoring/basic-handling.md#references) fornece informações sobre **Live Copies**, juntamente com o acesso às ações adequadas.

* **Visão geral da Live Copy** (**Sites**)

   * Este console permite que você [exiba e gerencie seu blueprint e suas live copies](/help/sites-administering/msm-livecopy-overview.md).

* **Blueprints** (**Ferramentas** - **Sites**)

   * Este console permite [criar e gerenciar as configurações do blueprint](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration).

>[!NOTE]
>
>O MSM pode ser usado com páginas e [Fragmentos de experiência](/help/sites-authoring/experience-fragments.md), pois esses fragmentos fazem parte de uma experiência (página).

>[!NOTE]
>
>Alguns aspectos da funcionalidade do MSM são usados em vários outros recursos do Adobe Experience Manager (AEM) (por exemplo, Inicializações, Catálogo); nesses casos, a live copy é gerenciada por esse recurso.

### Termos usados {#terms-used}

Como introdução, a tabela a seguir fornece uma visão geral dos principais termos usados com o MSM; eles são abordados com mais detalhes nas seções e páginas subsequentes:

<table>
 <tbody>
  <tr>
   <td><strong>Termo</strong></td>
   <td><strong>Definição</strong></td>
   <td><strong>Mais detalhes</strong></td>
  </tr>
  <tr>
   <td><strong>Origem</strong></td>
   <td>As páginas originais.</td>
   <td>Sinônimo de Blueprints e/ou páginas do Blueprint.</td>
  </tr>
  <tr>
   <td><strong>Live Copy</strong></td>
   <td>A cópia (da origem) mantida pelas ações de sincronização, conforme definido pelas configurações de implantação. </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Configuração da Live Copy</strong></td>
   <td>Definição dos detalhes de configuração de uma live copy.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Relacionamento online</strong><br /> </td>
   <td>Definição efetiva da herança para um determinado recurso; as conexões entre a origem e as live copies.<br /> </td>
   <td>Garante que as alterações na origem possam ser sincronizadas com a live copy.</td>
  </tr>
  <tr>
   <td><strong>Blueprint</strong></td>
   <td>Sinônimo de Source.</td>
   <td>Ela pode ser definida por uma configuração de blueprint.</td>
  </tr>
  <tr>
   <td><strong>Configuração do blueprint</strong></td>
   <td>Configuração predefinida especificando um caminho de origem.</td>
   <td>Quando uma página do blueprint é referenciada em uma configuração do blueprint, o comando Implantação fica disponível.</td>
  </tr>
  <tr>
   <td><strong>Sincronização</strong></td>
   <td>O termo genérico para a sincronização de conteúdo entre a origem e as live copies (pela <strong>Implantação</strong> e <strong>Sincronização</strong>).</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Implantação</strong><br /> </td>
   <td>Sincroniza desde o original até a live copy.<br /> Pode ser acionado por um autor (em uma página de blueprint) ou por um evento do sistema (conforme definido pela configuração de implantação).</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Configuração de implantação</strong></td>
   <td>Regras que determinam quais propriedades são sincronizadas, como e quando.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Sincronizar</strong></td>
   <td>Uma solicitação manual de sincronização, feita a partir das páginas de live copy.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Herança</strong></td>
   <td>Uma página/componente de live copy herda o conteúdo de sua página/componente original quando a sincronização ocorre.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Suspender</strong></td>
   <td>Remove temporariamente o relacionamento dinâmico entre uma live copy e sua página de blueprint.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Desconectar</strong></td>
   <td>Remove permanentemente o relacionamento dinâmico entre uma live copy e sua página de blueprint.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Redefinir</strong></td>
   <td><p>Redefinir uma página de live copy para:</p>
    <ul>
     <li>Remover todos os cancelamentos de herança e <br /> </li>
     <li>Retornar a página ao mesmo estado da página de origem.</li>
    </ul> <p>A redefinição afeta todas as alterações feitas nas propriedades da página, no sistema de parágrafos e nos componentes.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Superficial</strong></td>
   <td>Uma Live Copy de uma única página.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Profundo</strong></td>
   <td>Uma Live Copy de uma página, junto com suas páginas secundárias.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Consulte [Visão geral da API do Java™](/help/sites-developing/extending-msm.md#overview-of-the-java-api) para obter os nomes dos objetos.

## Live Copies {#live-copies}

Uma live copy do MSM é uma cópia do conteúdo específico do site para o qual é mantido um relacionamento dinâmico com a origem original:

* A live copy herda o conteúdo de sua origem.
* A sincronização executa a transferência real do conteúdo quando alterações são feitas no conteúdo original.
* Uma live copy pode ser considerada como:

   * Superficial: uma página única
   * Profunda: a página, junto com suas páginas secundárias

* Regras de sincronização - chamadas de configurações de implantação - determinam quais propriedades são sincronizadas e quando a sincronização ocorre.

No exemplo anterior, `/content/we-retail/language-masters/en` é o site principal global em inglês. Para reutilizar o conteúdo deste site, são criadas live copies do MSM:

* O conteúdo abaixo de `/content/we-retail/language-masters/en` é a origem.

* O conteúdo abaixo de `/content/we-retail/language-masters/en` é copiado abaixo dos nós `/content/we-retail/us/en/`, `/content/we-retail/gb/en`, `/content/we-retail/ca/en` e `/content/we-retail/au/en`. Estas são as live copies.

* Os autores podem alterar as páginas abaixo de `/content/we-retail/language-masters/en`.
* Quando acionado, o MSM sincroniza essas alterações nas live copies.

### Live Copies - Composição {#live-copies-composition}

>[!NOTE]
>
>Os diagramas e descrições nesta seção representam instantâneos de possíveis live copies. Eles não são abrangentes, mas fornecem uma visão geral e destacam características específicas.

Inicialmente, ao criar uma live copy, as páginas de origem selecionadas são refletidas em uma base de um por um na live copy. Depois disso, novos recursos (páginas e/ou parágrafos) também podem ser criados diretamente na live copy. Portanto, é útil estar ciente dessas variações e de como elas afetam a sincronização. As possíveis composições incluem:

* [Live Copy com páginas que não são da Live Copy](#live-copy-with-non-live-copy-pages)
* [Live Copies aninhadas](#nested-live-copies)

A forma básica da live copy tem:

* Páginas de Live Copy que refletem as páginas originais selecionadas em uma base de um por um.
* Uma definição de configuração.
* Um relacionamento dinâmico definido para cada recurso:

   * Vincular o recurso de live copy ao seu blueprint/origem.
   * Usado ao realizar a herança e a implantação.

* As alterações podem ser [sincronizadas](/help/sites-administering/msm-livecopy.md#synchronizing-your-live-copy) de acordo com os requisitos.

![Sincronizar](assets/chlimage_1-367.png)

#### Live Copy com páginas que não são da Live Copy {#live-copy-with-non-live-copy-pages}

Ao criar uma live copy no AEM, você pode visualizar e navegar pela ramificação da live copy - e usar a funcionalidade normal do AEM na ramificação da live copy. Isso significa que você (ou um processo) pode criar recursos (páginas, parágrafos ou ambos) dentro da ramificação da live copy. Por exemplo, `myCanadaOnlyProduct`.

* Esses recursos não têm um relacionamento dinâmico com as páginas de origem/blueprints e não são sincronizados.
* Podem ocorrer cenários que o MSM trata como casos especiais. Por exemplo, quando você (ou um processo) cria uma página com a mesma posição e nome nas ramificações da origem/blueprint e da live copy. Para essas situações, consulte [Conflitos de implantação do MSM](/help/sites-administering/msm-rollout-conflicts.md) para obter mais informações.

![Conflitos de implantação](assets/chlimage_1-368.png)

#### Live Copies aninhadas {#nested-live-copies}

Quando você (ou um processo) cria uma [página em uma live copy existente](#live-copy-with-non-live-copy-pages), esta nova página também pode ser configurada como uma live copy de um blueprint diferente. Isso é conhecido como uma Live Copy aninhada, em que o comportamento da segunda live copy (interna) é afetado pela primeira live copy (externa) da seguinte maneira:

* Uma implantação profunda, acionada para a live copy de nível superior, pode continuar na live copy aninhada (por exemplo, se o acionador corresponder).
* Quaisquer links entre as origens são regravados nas live copies.

  Por exemplo, os links do segundo ao primeiro blueprint são regravados como links da segunda live copy aninhada para a primeira live copy.

![Links entre fontes](assets/chlimage_1-369.png)

>[!NOTE]
>
>Se você mover/renomear uma página na ramificação da live copy, ela será tratada (internamente) como uma live copy aninhada para permitir que o AEM rastreie os relacionamentos.

#### Live Copies empilhadas {#stacked-live-copies}

Uma live copy é conhecida como Live Copy empilhada quando é criada como secundária de uma live copy superficial. Ela se comporta da mesma forma que uma [Live Copy aninhada](#nested-live-copies).

### Source, blueprints e configurações de blueprint {#source-blueprints-and-blueprint-configurations}

Qualquer página ou ramificação de páginas pode ser usada como origem de uma live copy.

No entanto, o MSM também permite definir uma configuração de blueprint que especifique um caminho de origem. Os benefícios de usar uma configuração do blueprint são:

* Permitir que o autor use a opção **Implantação** em um blueprint - para enviar modificações (explicitamente) para live copies que herdam deste blueprint.
* Permitir que o autor use **Criar Site**; isso permite que o usuário selecione idiomas facilmente e configure a estrutura da live copy.
* Defina uma configuração de implantação padrão para live copies que tenham uma relação com o blueprint.

A origem de uma live copy pode ser páginas normais ou páginas alteradas por uma configuração de blueprint - ambas são casos de uso válidos.

A origem forma o blueprint para a live copy. O blueprint é definido quando você:

* [Criar uma configuração de blueprint](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration)

  A configuração define (antecipadamente) as páginas que serão usadas para criar a live copy.

* [Criar uma Live Copy de uma página](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

  As páginas usadas para criar a live copy (as páginas de origem) são as páginas do blueprint.

  A página de origem pode ser referenciada por uma configuração de blueprint, ou não.

### Implantação e sincronização {#rollout-and-synchronize}

Uma implantação é a ação central do MSM que sincroniza as Live Copies com a origem. É possível executar implantações manualmente ou elas podem ocorrer automaticamente:

* A [configuração de implantação](#rollout-configurations) pode ser definida para que [eventos](/help/sites-administering/msm-sync.md#rollout-triggers) específicos ocasionem uma implantação automaticamente.
* Ao criar uma página de blueprint, você pode usar o comando [Implantação](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) para enviar alterações para a live copy.

  **O comando Implantação** está disponível em uma página de blueprint referenciada em uma configuração de blueprint.

  ![Implantação](assets/chlimage_1-370.png)

* Ao criar uma página de live copy, você pode usar o comando [Sincronizar](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) para trazer as alterações da origem para a live copy.

  O comando **Sincronizar** está sempre disponível na página da live copy (independentemente da página de origem/blueprint ser alterada por uma configuração de blueprint).

  ![Sincronizar](assets/chlimage_1-371.png)

### Configurações de implantação {#rollout-configurations}

Uma configuração de implantação define quando e como uma live copy é sincronizada com o conteúdo original. Uma configuração de implantação consiste em um acionador e uma ou mais ações de sincronização:

* **Acionador**

  Um acionador é um evento que ocasiona a sincronização da ação dinâmica, como a ativação de uma página de origem. O MSM define os acionadores que você pode usar.

* **Ações de sincronização**

  Executado na Live Copy para sincronizá-la com a origem. Exemplos de ações são: copiar o conteúdo, ordenar nós secundários e ativar a página de live copy. O MSM fornece várias ações de sincronização.

  >[!NOTE]
  >
  >É possível criar ações personalizadas para sua instância usando a API do Java™.

As configurações de implantação podem ser reutilizadas, de modo que mais de uma live copy pode usar a mesma configuração. Várias [configurações de implantação](/help/sites-administering/msm-sync.md#installed-rollout-configurations) estão inclusas em uma instalação padrão.

### Conflitos de implantação {#rollout-conflicts}

As implantações podem se tornar complicadas, especialmente quando os autores estão editando tanto o conteúdo original quanto a live copy. Portanto, é útil estar ciente de como o AEM trata quaisquer [conflitos que possam ocorrer durante a implantação](/help/sites-administering/msm-rollout-conflicts.md).

### Suspensão e cancelamento de herança e sincronização {#suspending-and-cancelling-inheritance-and-synchronization}

Cada página e componente em uma live copy é associado à página e ao componente de origem por meio de um relacionamento dinâmico. O relacionamento dinâmico configura a sincronização do conteúdo da live copy da origem.

Você pode **Suspender** a herança da live copy de uma página de live copy para poder alterar as propriedades e os componentes da página. Ao suspender a herança, as propriedades e os componentes da página não são mais sincronizados com a origem.

Ao editar uma página individual, os autores podem **cancelar a herança** de um componente. Quando a herança é cancelada, o relacionamento dinâmico é suspenso e a sincronização não ocorre para esse componente. Cancelar a herança e a sincronização são opções úteis quando subseções do conteúdo devem ser personalizadas.

### Desconectar uma Live Copy {#detaching-a-live-copy}

Você também pode [desanexar uma live copy](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy) do blueprint para remover todas as conexões.

>[!CAUTION]
>
>A ação Desconectar é permanente e irreversível.

Desanexar remove permanentemente o relacionamento dinâmico entre uma live copy e sua página de blueprint. Todas as propriedades relevantes ao MSM são removidas da live copy e as páginas da live copy se tornam uma cópia independente.

>[!NOTE]
>
>Consulte [Desanexando uma Live Copy](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy) para obter detalhes completos, incluindo o impacto relacionado em páginas secundárias e principais.

## Etapas padrão para usar o MSM {#standard-steps-for-using-msm}

As etapas a seguir descrevem o procedimento padrão de uso do MSM para reutilizar conteúdo e sincronizar alterações em Live Copies.

1. Desenvolva o conteúdo do site de origem.
1. Determine a configuração de implantação a ser usada.

   1. O MSM [instala várias configurações de implantação](/help/sites-administering/msm-sync.md#installed-rollout-configurations) que podem atender a vários casos de uso.
   1. Opcionalmente, você pode [criar uma configuração de implantação](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration), se necessário.

1. Determine onde você deve [especificar as configurações de implantação a serem usadas](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use) e configurar conforme necessário.
1. Se necessário, [crie uma configuração de blueprint](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration) que identifique o conteúdo original da live copy.
1. [Criar uma live copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy).
1. Altere o conteúdo original, conforme necessário. Empregue o processo normal de revisão e aprovação de conteúdo estabelecido por sua organização.
1. [Implante](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) o blueprint ou [sincronize a live copy](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) com as alterações.

## Personalização do MSM {#customizing-msm}

O MSM fornece ferramentas para que sua implementação possa se adaptar às complexidades excepcionais que podem existir ao compartilhar conteúdo:

* **Configurações de implantação personalizadas**
  [Crie uma configuração de implantação](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) quando as configurações instaladas não atenderem aos seus requisitos. Você pode usar qualquer acionador de implantação e ação de sincronização disponível.

* **Ações de Sincronização Personalizadas**
  [Crie uma ação de sincronização personalizada](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) quando as ações instaladas não atenderem aos requisitos específicos do aplicativo. O MSM fornece uma API Java™ para criar ações de sincronização personalizadas.

## Práticas recomendadas {#best-practices}

A página de [Práticas recomendadas do MSM](/help/sites-administering/msm-best-practices.md) contém informações importantes sobre a implementação.
