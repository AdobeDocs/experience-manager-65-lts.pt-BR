---
title: O Editor universal
description: Saiba mais sobre a flexibilidade do Universal Editor e como ele pode ajudar a potencializar suas experiências headless usando o AEM 6.5 LTS.
feature: Developing
role: Developer
exl-id: 495df631-5bdd-456b-b115-ec8561f33488
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 1%

---

# Sobre o Editor universal {#universal-editor}

Saiba mais sobre a flexibilidade do Universal Editor e como ele pode ajudar a potencializar suas experiências headless usando o AEM 6.5 LTS.

## Visão geral {#overview}

O Universal Editor é um editor visual versátil que faz parte do Adobe Experience Manager Sites. Ele permite que os autores façam a edição &quot;o que você vê é o que você obtém&quot; (WYSIWYG) de qualquer experiência headless.

* Os autores se beneficiam da flexibilidade do Universal Editor. Ele oferece suporte à mesma edição visual consistente para todas as formas de conteúdo headless do AEM.
* Os desenvolvedores se beneficiam da versatilidade do Universal Editor, pois ele também suporta a verdadeira dissociação da implementação. Ele permite que os desenvolvedores usem praticamente qualquer estrutura ou arquitetura de sua escolha, sem impor restrições de SDK ou tecnologia.

Consulte a [documentação do AEM as a Cloud Service sobre o Universal Editor](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) para obter mais detalhes.

## Arquitetura {#architecture}

O Editor universal é um serviço que trabalha em conjunto com o AEM para criar conteúdo em headless.

* O Editor Universal está hospedado em `https://experience.adobe.com/#/aem/editor/canvas` e pode editar páginas renderizadas pelo AEM 6.5 LTS.
* O Editor universal lê a página do AEM por meio da Dispatcher da instância do autor do AEM.
* O Universal Editor Service, que é executado no mesmo host que a Dispatcher, grava as alterações de volta na instância de autor do AEM.

![Fluxo de autor usando o Editor Universal](assets/author-flow.png)

## Requisitos {#requirements}

Os itens a seguir são compatíveis com o Editor Universal:

* AEM 6.5 LTS GA
   * A hospedagem no local e a hospedagem do Adobe Managed Services (AMS) são compatíveis.
* [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)
   * Há suporte para hospedagem no local e AMS.
* [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) (versão `2023.8.13099` ou superior)

Este documento se concentra no suporte ao AEM 6.5 LTS do Editor universal. Para usar o Editor universal com o AEM 6.5 LTS, é necessário o seguinte:

* AEM 6.5 LTS GA
* Dispatcher configurado corretamente

## Configurar {#setup}

Para usar o Editor universal, faça o seguinte:

1. [Configure serviços na sua instância de criação do AEM.](#configure-aem)
1. [Configurar um Serviço do Editor Universal local.](#set-up-ue)
1. [Ajuste seu Dispatcher para permitir o Universal Editor Service.](#update-dispatcher)

Após concluir a instalação, você pode [instrumentar seus aplicativos para usar o Editor Universal.](#instrumentation)

### Configurar serviços {#configure-aem}

O Editor Universal depende de vários serviços que devem ser configurados.

#### Defina o Atributo SameSite para o cookie `login-token`. {#samesite-attribute}

1. Abra o Gerenciador de configurações.
   * `http://<host>:<port>/system/console/configMgr`
1. Localize o **Manipulador de autenticação de token do Adobe Granite** na lista e clique em **Alterar os valores de configuração**.
1. Na caixa de diálogo, altere o atributo **SameSite do cookie de token de logon** (`token.samesite.cookie.attr`) para `Partitioned`.
1. Clique em **Salvar**.

#### Remova a opção X-Frame de cabeçalhos `SAMEORIGIN`. {#sameorigin}

1. Abra o Gerenciador de configurações.
   * `http://<host>:<port>/system/console/configMgr`
1. Localize o **Apache Sling Main Servlet** na lista e clique em **Editar os valores de configuração**.
1. Exclua o valor `X-Frame-Options=SAMEORIGIN` do atributo (**)** Cabeçalhos de resposta adicionais`sling.additional.response.headers` se ele existir.
1. Clique em **Salvar**.

#### Configurar o manipulador de autenticação do parâmetro de consulta do Adobe Granite {#query-parameter}

1. Abra o Gerenciador de configurações.
   * `http://<host>:<port>/system/console/configMgr`
1. Localize o **Manipulador de Autenticação de Parâmetro de Consulta do Adobe Granite** na lista e clique em **Editar os valores de configuração**.
1. No campo **Caminho** (`path`), adicione `/` para habilitar.
   * Um valor vazio desativa o manipulador de autenticação.
1. Clique em **Salvar**.

#### Definir quais caminhos de conteúdo ou `sling:resourceTypes` são abertos no Editor Universal {#paths}

1. Abra o Gerenciador de configurações.
   * `http://<host>:<port>/system/console/configMgr`
1. Localize o **Serviço de URL do Editor Universal** na lista e clique em **Editar os valores de configuração**.
1. Defina para quais caminhos de conteúdo ou `sling:resourceTypes` o Editor Universal deve ser aberto.
   * No campo **Mapeamento de Abertura do Editor Universal**, forneça os caminhos para os quais o Editor Universal está aberto.
   * No **Sling:resourceTypes que deve ser aberto pelo Editor Universal**, insira uma lista de recursos que o Editor Universal abre diretamente.
1. Clique em **Salvar**.
1. Verifique sua [configuração do Externalizador](/help/sites-developing/externalizer.md) e certifique-se de que, no mínimo, você tenha os ambientes local, de autor e de publicação definidos como no exemplo a seguir:

   ```text
   "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
   "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
   "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]"
   ```

Quando essas etapas de configuração forem concluídas, o AEM abrirá o Editor universal para páginas na seguinte ordem:

1. O AEM verifica os mapeamentos em `Universal Editor Opening Mapping` e se o conteúdo estiver em qualquer caminho definido nele, o Editor Universal será aberto para ele.

1. Para conteúdo fora dos caminhos definidos em `Universal Editor Opening Mapping`, o AEM verifica se o conteúdo `resourceType` corresponde a uma entrada em **Sling:resourceTypes que deve ser aberta pelo Editor Universal**. Se ele corresponder, o AEM abrirá o conteúdo no Editor Universal em `${author}${path}.html`.
1. Caso contrário, o AEM abrirá o Editor de páginas.

As variáveis a seguir estão disponíveis para definir seus mapeamentos em `Universal Editor Opening Mapping`.

* `path`: Caminho de conteúdo do recurso a ser aberto
* `localhost`: Entrada do externalizador para `localhost` sem esquema, por exemplo, `localhost:4502`
* `author`: Entrada externalizadora para autor sem esquema, por exemplo, `localhost:4502`
* `publish`: Entrada do externalizador para publicação sem esquema, por exemplo, `localhost:4503`
* `preview`: Entrada do externalizador para visualização sem esquema, por exemplo, `localhost:4504`
* `env`: `prod`, `stage`, `dev` com base nos modos de execução do Sling definidos
* `token`: Token de consulta necessário para `QueryTokenAuthenticationHandler`

Exemplo de mapeamentos:

* Abrir todas as páginas em `/content/foo` no Autor do AEM:
   * `/content/foo:${author}${path}.html?login-token=${token}`
   * Resultados ao abrir `https://localhost:4502/content/foo/x.html?login-token=<token>`
* Abrir todas as páginas em `/content/bar` em um servidor NextJS remoto, fornecendo todas as variáveis como informações
   * `/content/bar:nextjs.server${path}?env=${env}&author=https://${author}&publish=https://${publish}&login-token=${token}`
   * Resultados ao abrir `https://nextjs.server/content/bar/x?env=prod&author=https://localhost:4502&publish=https://localhost:4503&login-token=<token>`

### Configurar o Serviço de Editor Universal {#set-up-ue}

Com o AEM atualizado e configurado, você pode configurar um Serviço local do Universal Editor para desenvolvimento e teste locais.

1. Instale o Node.js versão >=20.
1. Baixe e descompacte o Serviço Universal Editor mais recente da [Distribuição de Software](https://experienceleague.adobe.com/pt-br/docs/experience-cloud/software-distribution/home)
1. Configure o Universal Editor Service por meio de variáveis de ambiente ou arquivo `.env`.
   * [Consulte a documentação do AEM as a Cloud Service Universal Editor para obter detalhes.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/local-dev#setting-up-service)
   * Observe que talvez seja necessário usar a opção `UES_MAPPING` se for necessária a regravação interna do IP.
1. Executar `universal-editor-service.cjs`

### Atualizar o Dispatcher {#update-dispatcher}

Com o AEM configurado e um Serviço do Editor Universal local em execução, é necessário permitir um proxy reverso para o novo serviço [no Dispatcher.](https://experienceleague.adobe.com/pt-br/docs/experience-manager-dispatcher/using/dispatcher)

1. Ajuste o arquivo vhost da instância do autor para incluir um proxy reverso.

   ```html
   <IfModule mod_proxy.c>
    ProxyPass "/universal-editor" "http://localhost:8080"
    ProxyPassReverse "/universal-editor" "http://localhost:8080"
   </IfModule>
   ```

   >[!NOTE]
   >
   >8080 é a porta padrão. Se você alterou isto usando o parâmetro `UES_PORT` em [seu arquivo `.env`,](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/local-dev#setting-up-service) ajuste o valor da porta aqui de acordo.

1. Reinicie o Apache.

## Instrumentar seu aplicativo {#instrumentation}

Com o AEM atualizado e um Serviço do editor universal local em execução, você pode começar a editar conteúdo headless usando o editor universal.

No entanto, seu aplicativo deve ser instrumentado para aproveitar o Editor universal. Envolve a inclusão de metatags para instruir o editor sobre como e onde o conteúdo deve ser mantido. Os detalhes desta instrumentação estão disponíveis na [documentação do Universal Editor para AEM as a Cloud Service.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/getting-started#instrument-page)

Observe que, ao seguir a documentação do Universal Editor com AEM as a Cloud Service, as seguintes alterações se aplicam ao usá-lo com o AEM 6.5 LTS.

* O protocolo na meta tag deve ser `aem65` em vez de `aem`.

  ```html
  <meta name="urn:adobe:aue:system:aemconnection" content={`aem65:${getAuthorHost()}`}/>
  ```

* O ponto de extremidade do Serviço do Editor Universal deve ser anunciado por meio de uma meta tag.

  ```html
  <meta name="urn:adobe:aue:config:service" content={`${getAuthorHost()}/universal-editor`}/>
  ```

* Na seção `plugins` da definição de componentes, deve ser usado `aem65` em vez de `aem`.

>[!TIP]
>
>Para obter um guia abrangente do desenvolvedor para o Universal Editor, consulte [Visão geral do Universal Editor para desenvolvedores do AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/developer-overview) na documentação do AEM as a Cloud Service. Observe as alterações no AEM 6.5 LTS descritas nesta seção.

## Diferenças entre o AEM 6.5 LTS e o AEM as a Cloud Service {#differences}

O Editor universal no AEM 6.5 LTS funciona amplamente da mesma forma que no AEM as a Cloud Service, incluindo a interface do usuário e grande parte da configuração. Há, no entanto, diferenças que você deve observar.

* O Universal Editor no 6.5 LTS é compatível apenas com o caso de uso headless.
* A configuração do Editor Universal varia ligeiramente para 6.5 LTS ([conforme descrito](#setup) no documento atual).
* O Editor universal no 6.5 LTS usa um seletor de ativos diferente e um seletor de Fragmento de conteúdo diferente do AEM as a Cloud Service.
