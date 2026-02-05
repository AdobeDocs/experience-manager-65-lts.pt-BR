---
title: Arquitetura de conteúdo
description: Dicas para projetar seu conteúdo (dica - tudo é conteúdo)
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: eb47f730-ac26-47a0-9bd7-3b7e94c79ecd
source-git-commit: cc96a14ebaf9f895a798b5f4904f5b4769b990bb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# Arquitetura de conteúdo{#content-architecture}

## Siga o modelo de David {#follow-david-s-model}

David Nuescheler escreveu David&#39;s Model anos atrás, mas suas ideias ainda continuam verdadeiras hoje. Os principais princípios do Modelo de David são os seguintes:

* Os dados vêm primeiro, estruturados depois. Talvez.
* Direcione a hierarquia de conteúdo; não deixe que isso aconteça.
* Os espaços de trabalho são para `clone()`, `merge()` e `update()`.
* Cuidado com os irmãos de mesmo nome.
* As referências podem ser consideradas prejudiciais.
* Arquivos são arquivos.
* As identidades são más.

O modelo de David pode ser encontrado no wiki do Jackrabbit em [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Tudo é conteúdo {#everything-is-content}

Tudo deve ser armazenado no repositório, em vez de depender de fontes de dados separadas de terceiros, como bancos de dados. Essa abordagem se aplica ao conteúdo criado, aos dados binários como imagens, código e configurações. Ele permite usar um conjunto de APIs para gerenciar todo o conteúdo e gerenciar a promoção desse conteúdo por meio de replicação. Você também obtém uma única fonte de backup, registro e assim por diante.

### Usar o princípio de design de &quot;modelo de conteúdo primeiro&quot; {#use-the-content-model-first-design-principle}

Ao criar um novo recurso, sempre comece criando a estrutura de conteúdo JCR primeiro e, em seguida, examine a leitura e a gravação de conteúdo usando os servlets Sling padrão. Essa abordagem permite garantir que sua implementação funcione bem com mecanismos de controle de acesso prontos para uso e evitar a geração de servlets estilo CRUD desnecessários.

### Ser RESTful {#be-restful}

Defina servlets com base em resourceTypes em vez de caminhos. Essa abordagem possibilita o uso de controles de acesso JCR, a adesão a princípios REST e o uso do solucionador de recursos e recursos fornecido na solicitação. Essa abordagem permite alterar os scripts que renderizam URLs no lado do servidor sem alterar URLs do lado do cliente. Ele também oculta do cliente os detalhes de implementação do lado do servidor para maior segurança.

### Evitar a definição de novos tipos de nó {#avoid-defining-new-node-types}

Os tipos de nó funcionam em um nível baixo na camada de infraestrutura. A maioria dos requisitos é atendida usando um `sling:resourceType` atribuído a um tipo de nó `nt:unstructured`, `oak:Unstructured`, `sling:Folder` ou `cq:Page`. Os tipos de nó equivalem ao esquema no repositório e alterar os tipos de nó pode custar caro.

### Seguir as convenções de nomenclatura no JCR {#adhere-to-naming-conventions-in-the-jcr}

Seguir convenções de nomenclatura adiciona consistência à base de código, reduzindo a taxa de incidência de defeitos e aumentando a velocidade dos desenvolvedores que trabalham no sistema. As seguintes convenções são usadas pela Adobe no desenvolvimento do AEM:

* Nomes de nós

   * Todas em minúsculas.
   * Separação de palavras usando hifens.

* Nomes de propriedades

   * Caixa alta, começando com uma letra minúscula.

* Componentes (JSP/HTML)

   * Todas em minúsculas.
   * Separação de palavras usando hifens.
