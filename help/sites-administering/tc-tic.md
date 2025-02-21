---
title: Configuração da estrutura de integração de tradução
description: Saiba como configurar a estrutura de integração de tradução no Adobe Experience Manager.
contentOwner: Guillaume Carlino
feature: Language Copy
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 17898ee854df1141272b207f96cebe69c325f12c
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 44%

---

# Configuração da estrutura de integração de tradução{#configuring-the-translation-integration-framework}

A estrutura de integração de tradução integra-se aos serviços de tradução de terceiros para orquestrar a tradução de conteúdo do AEM.

* Conectar ao provedor de serviços de tradução.
* Criar uma configuração da estrutura de integração de tradução.
* Associe as configurações de nuvem às suas páginas.

Para obter uma visão geral dos recursos de tradução de conteúdo do AEM, consulte [Tradução de conteúdo para sites multilíngues](/help/sites-administering/translation.md).

## Conexão com um provedor de serviços de tradução {#connecting-to-a-translation-service-provider}

Crie uma configuração de nuvem que conecte o AEM ao seu provedor de serviços de tradução.

O AEM inclui a capacidade de [conectar-se ao Microsoft® Translator](/help/sites-administering/tc-msconf.md) por padrão. Outros fornecedores de tecnologia de tradução com conectores do AEM que são membros do programa de parceria da Adobe Exchange podem ser encontrados [aqui](https://exchange.adobe.com/apps/browse/ec?page=1&amp;partnerLevel=All&amp;product=AEM&amp;q=experience+manager+translation&amp;sort=RELEVANCE).

Depois de instalar um pacote de conectores, é possível criar uma configuração de nuvem para o conector. Normalmente, você precisará fornecer suas credenciais para autenticação com o serviço de tradução. Para obter informações sobre como adicionar uma configuração de nuvem para o conector do Microsoft Translator, consulte [Integração com o Microsoft Translator](/help/sites-administering/tc-msconf.md).

Você pode criar várias configurações de nuvem para o mesmo conector, se necessário. Por exemplo, crie uma configuração para cada conta ou projeto que você tem com o mesmo fornecedor.

Após configurar uma conexão, é possível criar a configuração da estrutura de integração de tradução que a utiliza.

## Criar uma configuração de integração de tradução {#creating-a-translation-integration-configuration}

Crie uma configuração de estrutura de integração de tradução para especificar como traduzir o conteúdo. A configuração inclui as seguintes informações:

* Qual provedor de serviços de tradução usar.
* Se deve ser realizada tradução humana ou automática.
* Se outros conteúdos associados a uma página ou ativo, como tags, deverão ser traduzidos.

Após criar uma configuração de estrutura, associe a configuração de nuvem às páginas que deseja traduzir de acordo com a configuração. Quando o processo de tradução é iniciado, o fluxo de trabalho de tradução continua de acordo com a configuração de estrutura associada.

Quando diferentes seções do seu site tiverem diferentes requisitos de tradução, crie várias configurações de estrutura de acordo. Por exemplo, um site multilíngue inclui cópias em inglês, espanhol e japonês. O proprietário do site usa dois provedores de serviços de tradução diferentes para traduções em espanhol e japonês. Portanto, duas configurações da estrutura são definidas. Cada configuração usa um provedor de serviço de tradução diferente.

Após configurar uma estrutura de integração de tradução, é possível [associá-la às páginas](/help/sites-administering/tc-prep.md) que a utilizam.

**Observação:** para obter uma visão geral dos recursos de tradução de conteúdo do AEM, consulte [Tradução de Conteúdo para Sites Multilíngues](/help/sites-administering/translation.md).

Uma única configuração da estrutura controla como traduzir conteúdo e ativos da página.
![chlimage_1-386](assets/translation-config-65.jpg)

### Propriedades de configuração de sites {#sites-configuration-properties}

As propriedades do Sites controlam como a tradução do conteúdo da página é realizada.

<table>
 <tbody>
  <tr>
   <th>Propriedade</th>
   <th>Descrição</th>
  </tr>
  <tr>
   <td>Fluxo de trabalho da conversão</td>
   <td><p>Selecione o método de tradução executado pela estrutura para o conteúdo do site:</p>
    <ul>
     <li>Tradução automática: o provedor de tradução realiza a tradução usando a tradução automática em tempo real.</li>
     <li>Tradução humana: o conteúdo é enviado ao provedor de tradução para ser traduzido por tradutores. </li>
     <li>Não traduzir: o conteúdo não é enviado para tradução. Isso é para ignorar determinadas ramificações de conteúdo que não seriam traduzidas, mas que poderiam ser atualizadas com o conteúdo mais recente.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Provedor de tradução</td>
   <td>Selecione o provedor de tradução para executar a tradução. Um provedor é exibido na lista quando o conector correspondente é instalado.</td>
  </tr>
  <tr>
   <td>Categoria de conteúdo</td>
   <td>(Somente tradução automática) Uma categoria que descreve o conteúdo que você está traduzindo. A categoria pode afetar a escolha de terminologia e do estilo linguístico na tradução do conteúdo.</td>
  </tr>
  <tr>
   <td>Converter strings do componente</td>
   <td>Selecione para traduzir cadeias de caracteres de componentes associadas à página.</td>
  </tr>
  <tr>
   <td>Traduzir tags</td>
   <td>Selecione para traduzir tags associadas à página.</td>
  </tr>
  <tr>
   <td>Traduzir ativos da página</td>
   <td><p>Selecione como traduzir ativos adicionados a componentes a partir do sistema de arquivos ou referenciados da Assets:</p>
    <ul>
     <li>Não traduzir: os ativos da página não são traduzidos.</li>
     <li>Uso do fluxo de trabalho de tradução do Sites: os Assets são tratados de acordo com as propriedades de configuração na guia Sites.</li>
     <li>Uso do fluxo de trabalho de tradução do Assets: os Assets são tratados de acordo com a configuração das propriedades na guia Assets.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Executar a tradução automaticamente</td>
   <td>Selecione para executar trabalhos de tradução automaticamente após a criação de projetos de tradução. Você não terá a oportunidade de revisar e analisar o trabalho de tradução ao selecionar essa opção.</td>
  </tr>
 </tbody>
</table>

### Propriedades de configuração de ativos {#assets-configuration-properties}

As propriedades de ativos controlam como configurar ativos. Para obter mais informações sobre a tradução de ativos, consulte [Criação de cópias de idioma para ativos](/help/assets/translation-projects.md).

<table>
 <tbody>
  <tr>
   <th>Propriedade</th>
   <th>Descrição</th>
  </tr>
  <tr>
   <td>Fluxo de trabalho da conversão</td>
   <td><p>Selecione o tipo de tradução que a estrutura executa para os ativos:</p>
    <ul>
     <li>Tradução automática: o provedor de tradução executa a tradução imediatamente usando a tradução automática.</li>
     <li>Tradução humana: o conteúdo é enviado automaticamente para o provedor de tradução para ser traduzido manualmente. </li>
     <li>Não traduzir: as Assets não são enviadas para tradução.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Provedor de tradução</td>
   <td>Selecione o provedor de tradução para executar a tradução. Um provedor é exibido na lista quando o conector correspondente é instalado.</td>
  </tr>
  <tr>
   <td>Categoria de conteúdo</td>
   <td>(Somente tradução automática) Uma categoria que descreve o conteúdo que você está traduzindo. A categoria pode afetar a escolha de terminologia e do estilo linguístico na tradução do conteúdo.</td>
  </tr>
  <tr>
   <td>Traduzir ativos</td>
   <td>Selecione para incluir ativos no projeto de tradução. </td>
  </tr>
  <tr>
   <td>Traduzir metadados</td>
   <td>Selecione para traduzir metadados de ativos.</td>
  </tr>
  <tr>
   <td>Traduzir tags</td>
   <td>Selecione para traduzir tags associadas ao ativo.</td>
  </tr>
  <tr>
   <td>Executar a tradução automaticamente</td>
   <td>Selecione para executar trabalhos de tradução automaticamente após a criação de projetos de tradução. Você não terá a oportunidade de revisar ou analisar o trabalho de tradução ao selecionar essa opção.</td>
  </tr>
 </tbody>
</table>

1. Na barra lateral, clique em Ferramentas > Operações > Nuvem > Serviços em nuvem.
1. Na área Integração de tradução, se alguma configuração foi criada, determina qual link aparece:

   * Se nenhuma configuração tiver sido criada, clique em Configurar agora.
   * Se já existirem configurações, clique em Mostrar configurações e, em seguida, clique no link + que aparece ao lado de Configurações disponíveis.

1. Digite um nome para a configuração e clique em Criar.
1. Configure as propriedades nas guias Sites e Assets e clique em OK.

## Configuração de páginas para tradução {#configuring-pages-for-translation}

Para configurar a tradução das páginas de origem para outros idiomas, associe-as com as seguintes configurações de nuvem:

* A configuração de nuvem que conecta o AEM ao seu provedor de tradução.
* A estrutura de integração de tradução que configura os detalhes da tradução.

A configuração da nuvem da estrutura de integração de tradução identifica a configuração da nuvem a ser usada para a conexão com o provedor de serviços. Quando você associa uma página de origem a uma configuração de nuvem da estrutura, a página deve ser associada à configuração de nuvem do provedor de serviços definido na configuração da estrutura.

Quando você associa uma página a uma configuração de nuvem, os descendentes da página herdam a associação. Por exemplo, se você associar a página /content/geometrixx/en/products a uma estrutura de integração de tradução, a página Produtos e todas as páginas abaixo dela serão traduzidas de acordo com a estrutura.

Quando necessário, é possível sobrepor a associação em uma página descendente. Por exemplo, o conteúdo de um site é principalmente sobre roupas. No entanto, uma ramificação de páginas descreve a empresa. A página raiz do site está associada a uma estrutura de integração de tradução que especifica o uso da tradução automática usando a categoria Roupas. A ramificação que descreve a empresa usa uma estrutura que executa a tradução automática usando a categoria Geral.

### Associar uma página a um provedor de tradução {#associating-a-page-with-a-translation-provider}

Associe uma página ao provedor de tradução que você está usando para traduzir a página e suas páginas descendentes.

1. No console do Sites, selecione a página que deseja configurar e clique em Propriedades de exibição.
1. Clique em Editar e na guia Serviços em nuvem.
1. Clique em Adicionar configuração > Integração de tradução.
1. Selecione o provedor de tradução a ser usado e clique em Concluído.

### Associar páginas a uma estrutura de integração de tradução {#associating-pages-with-a-translation-integration-framework}

Associe uma página à estrutura de integração de tradução que define como você deseja executar a tradução da página e de suas páginas descendentes.

1. No console do Sites, selecione a página que deseja configurar e clique em Propriedades de exibição.
1. Clique em Editar e na guia Serviços em nuvem.
1. Clique em Adicionar configuração > Integração de tradução.
1. Selecione a estrutura de integração de tradução a ser usada e clique em Concluído.
