---
title: Desenvolver o AEM Commerce
description: Saiba como gerar um projeto do AEM habilitado para comércio usando o arquétipo de projeto do AEM. Saiba como criar e implantar o projeto em um ambiente de desenvolvimento local.
topics: Commerce, Development
feature: Commerce Integration Framework
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 25%

---

# Desenvolvimento do AEM Commerce {#develop}

O desenvolvimento de projetos do AEM Commerce com base no Commerce integration framework (CIF) para AEM segue as mesmas regras e práticas recomendadas de outros projetos do AEM. Revise estes primeiro:

- [Guia do usuário para desenvolvimento no AEM 6.5](/help/sites-developing/getting-started.md)
- [Conceitos principais do AEM](/help/sites-developing/the-basics.md)
- [Desenvolvimento do AEM – Diretrizes e práticas recomendadas](/help/sites-developing/dev-guidelines-bestpractices.md)
- [Como criar projetos do AEM usando o Apache Maven](/help/sites-developing/ht-projects-maven.md)

## Desenvolvimento local para o AEM Commerce {#local}

Um ambiente de desenvolvimento local é recomendado para trabalhar com projetos do CIF.

>[!NOTE]
>
>As instruções a seguir ajudam a configurar um ambiente de desenvolvimento do AEM local para o AEM Commerce usando o CIF com foco no AEM 6.5). Se você estiver usando o AEM as a Cloud Service, consulte a documentação do [AEM Commerce as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/home.html?lang=pt-BR).

O complemento AEM Commerce para AEM 6.5 também conhecido como. O complemento CIF também está disponível para desenvolvimento local e é fornecido como um pacote do AEM. Ele pode ser baixado do [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) como um pacote de recursos.

### Software necessário

Devem ser instalados:

- AEM local 6.5
- [AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) 7 ou posterior
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 ou mais recente)
- [Nó LTS](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Acesso ao complemento do CIF

O complemento CIF pode ser baixado no [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) e procure por &#39;complemento AEM Commerce&#39;.

>[!TIP]
>
>Use sempre a versão mais recente do complemento CIF.

### Configuração local

Para o desenvolvimento de projetos locais do CIF usando o AEM e o complemento CIF, siga estas etapas:

1. Obtenha a versão AEM 6.5 e instale o AEM 6.5 Service Pack. O AEM 6.5 Service Pack 7 é necessário, no entanto, a Adobe recomenda instalar o último service pack disponível.

1. Descompacte o AEM .jar para criar a pasta `crx-quickstart` e execute:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Crie uma pasta `crx-quickstart/install`

1. Copie o pacote completo do complemento CIF, baixado do Portal de Distribuição de Software, na pasta `crx-quickstart/install`.

>[!TIP]
>
>Como alternativa, o pacote complementar do CIF também pode ser instalado por meio do Gerenciador de pacotes.

1. Iniciar o início rápido do AEM

Verifique a configuração por meio do console OSGI: `http://localhost:4502/system/console/osgi-installer`. A lista deve incluir os pacotes relacionados ao complemento do CIF, o pacote de conteúdo e as configurações de OSGI. Verifique se todos os pacotes foram iniciados.

## Configuração do projeto {#project}

Há duas maneiras de iniciar seu projeto do AEM Commerce usando o CIF.

### Usar o Arquétipo de projeto do AEM

O [Arquétipo de projeto do AEM](https://github.com/adobe/aem-project-archetype) é a principal ferramenta para inicializar um projeto pré-configurado e começar a usar a CIF. Os Componentes principais do CIF e todas as configurações necessárias podem ser incluídos em um projeto gerado com uma opção extra.

>[!TIP]
>
>Use o [Arquétipo de projeto do AEM 25 ou posterior](https://github.com/adobe/aem-project-archetype/releases) para gerar o projeto.

Consulte as [instruções de uso](https://github.com/adobe/aem-project-archetype#usage) do Arquétipo de projeto do AEM sobre como gerar um projeto do AEM. Para incluir a CIF no projeto, use a opção `includeCommerce`.

Por exemplo:

```bash
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.granite.archetypes \
 -D archetypeArtifactId=aem-project-archetype \
 -D aemVersion=6.5.5 \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n \
 -D includeCommerce=y
```

Os Componentes principais do CIF podem ser usados em qualquer projeto incluindo o pacote `all` fornecido ou um indivíduo usando o pacote de conteúdo do CIF e os pacotes OSGI relacionados. Para adicionar os Componentes principais da CIF manualmente a um projeto, use as seguintes dependências:

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-config</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-core</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>graphql-client</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>magento-graphql</artifactId>
    <version>x.y.z</version>
</dependency>
```

### Usar a loja de referência AEM Venia

Uma segunda opção para iniciar um projeto da CIF é clonar e usar a [loja de referência AEM Venia](https://github.com/adobe/aem-cif-guides-venia). A loja de referência AEM Venia é um exemplo de aplicativo de vitrine de referência que demonstra o uso dos Componentes principais da CIF para o AEM. Ela serve como um conjunto de exemplos de práticas recomendadas e um possível ponto de partida para desenvolver sua própria funcionalidade.

Para começar a usar a loja de referência Venia, basta clonar o [repositório Git](https://github.com/adobe/aem-cif-guides-venia) e personalizar o projeto de acordo com suas necessidades.

>[!NOTE]
>
>O projeto da loja de referência Venia contém dois perfis de construção para o AEM as a Cloud Service e o AEM 6.5. Verifique o [arquivo readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) do projeto para ver como eles são usados. Para o AEM 6.5, use o perfil `classic`.

### Conectar o AEM ao sistema Commerce

Para conectar seu projeto ao sistema de comércio, o AEM deve ser configurado com o terminal GraphQL do sistema de comércio.

Um projeto gerado pelo [Arquétipo de Projeto do AEM](https://github.com/adobe/aem-project-archetype) ou pela [Loja de Referência AEM Venia](https://github.com/adobe/aem-cif-guides-venia) já inclui uma [configuração padrão](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) que deve ser ajustada.

Substitua o valor de `url` em `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` pelo ponto de extremidade GraphQL do sistema de comércio usado pelo projeto.

O complemento AEM Commerce e os componentes principais do CIF se conectam ao endpoint de comércio do GraphQL por meio do servidor do AEM e diretamente pelo navegador. Os Componentes principais do CIF do lado do cliente e as ferramentas de criação do complemento do CIF por padrão se conectam ao `/api/graphql`. Se necessário, isso pode ser ajustado por meio da configuração do CIF Cloud Service (veja abaixo).

O complemento CIF fornece um servlet de proxy do GraphQL em `/api/graphql`. Se você não planeja usar um AEM Dispatcher local, é recomendável configurar também o servlet proxy do GraphQL.

Navegue até http://localhost:4502/system/console/configMgr e crie uma configuração OSGI para o serviço `Adobe CIF GraphQL Proxy Configuration`. Use o mesmo endpoint do GraphQL do sistema de comércio usado para o cliente GraphQL acima.

## Recursos adicionais

- [Arquétipo de projeto do AEM](https://github.com/adobe/aem-project-archetype)
- [Loja de referência Venia](https://github.com/adobe/aem-cif-guides-venia)
