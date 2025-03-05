---
title: Atualização de código e personalizações
description: Saiba mais sobre como atualizar código e personalizações no AEM.
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: da061097fd57135bde149b41a12ab78cad5761d6
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 0%

---

# Atualização de código e personalizações{#upgrading-code-and-customizations}

Ao planejar uma atualização, as seguintes áreas de uma implementação devem ser investigadas e abordadas.

* [Atualizar a base de código](#upgrade-code-base)
* [Procedimento de teste](#testing-procedure)

## Visão geral {#overview}

1. **AEM Analyzer** - Execute o AEM Analyzer conforme descrito no planejamento de atualização e detalhado na página [Avaliação da Complexidade de Atualização com o AEM Analyzer](/help/sites-deploying/aem-analyzer.md). Você obtém um relatório do AEM Analyzer que contém mais detalhes sobre as áreas que devem ser abordadas, além das APIs/pacotes indisponíveis na versão Target do AEM. O relatório do AEM Analyzer fornece uma indicação de quaisquer incompatibilidades no código. Se não houver nenhum, sua implantação já será compatível com o LTS 6.5. Você ainda pode optar por fazer novo desenvolvimento para usar a funcionalidade LTS 6.5, mas não é necessário apenas para manter a compatibilidade.
1. **Desenvolver Base de Código para 6.5 LTS**- Crie uma ramificação ou repositório dedicado para a base de código para a versão de Destino. Use as informações da Compatibilidade de pré-atualização para planejar as áreas do código a serem atualizadas.
1. **Compilar com 6.5 LTS Uber jar**- Atualize os POMs de base de código para apontar para 6.5.2025 uber jar e compile o código em relação a ele.
1. **Implantar no Ambiente 6.5 LTS** - Uma instância limpa do AEM 6.5 LTS (Autor + Publicação) deve ser colocada em um ambiente Dev/QA. A base de código atualizada e uma amostra representativa de conteúdo (da produção atual) devem ser implantadas.
1. **Validação de controle de qualidade e correção de erros** - o controle de qualidade deve validar o aplicativo nas instâncias do Autor e de Publicação de 6.5.2025. Quaisquer bugs encontrados devem ser corrigidos e confirmados na base de código 6.5 LTS. Repita o Dev-Cycle conforme necessário até que todos os bugs sejam corrigidos.

Antes de continuar com uma atualização, você deve ter uma base de código de aplicativo estável que foi totalmente testada contra o AEM 6.5 LTS.

## Atualizar a base de código {#upgrade-code-base}

### Criar uma Ramificação Dedicada para o Código LTS 6.5 no Controle de Versão {#create-a-dedicated-branch-for-6.5-lts-code-in-version-control}

Todos os códigos e configurações necessários para a implementação do AEM devem ser gerenciados usando alguma forma de controle de versão. Uma ramificação dedicada no controle de versão deve ser criada para gerenciar todas as alterações necessárias à base de código na versão de destino do AEM. O teste iterativo da base de código em relação à versão de destino do AEM e correções de erros subsequentes é gerenciado nessa ramificação.

### Atualizar a versão do AEM Uber Jar {#update-the-aem-uber-jar-version}

O jar do AEM Uber inclui todas as APIs do AEM como uma única dependência no `pom.xml` do seu projeto Maven. É sempre uma prática recomendada incluir o Uber Jar como uma única dependência, em vez de incluir dependências individuais da API do AEM. Ao atualizar a base de código, altere a versão do Uber Jar para apontar para a versão 6.5 LTS do AEM. Atualize quaisquer APIs ou métodos obsoletos para que sejam compatíveis com a versão de destino do AEM. Recompile a base de código em relação à nova versão do Uber Jar.

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Há uma pequena diferença na forma como o AEM 6.5 e o AEM 6.5 LTS Uber Jars são empacotados. Consulte a seção abaixo:

**Uber Jars para AEM 6.5**

1. `uber-jar-6.5.x.jar` - Contém todas as APIs públicas do AEM 6.5.
1. `uber-jar-6.5.x-apis-with-deprecations.jar` - Inclui APIs públicas e APIs obsoletas do AEM 6.5.

**Uber Jars para AEM 6.5 LTS**

Para o AEM 6.5 LTS, há novamente dois tipos de Uber Jars:

1. `uber-jar-6.6.x-apis.jar` - Contém todas as APIs públicas do AEM 6.5 LTS.
1. `uber-jar-6.6.x-deprecated-apis.jar` - Inclui somente APIs obsoletas do AEM 6.5 LTS.

**Diferença principal: AEM 6.5 vs. AEM 6.5 LTS Uber Jars**

* No AEM 6.5, se forem necessárias APIs públicas e obsoletas, você poderá usar incluir jar único, `uber-jar-6.5.x-apis-with-deprecations.jar` no arquivo `pom.xml`.
* No AEM 6.5 LTS, se você precisar de APIs públicas e obsoletas, será necessário incluir dois jars separados, `uber-jar-6.6.x-apis.jar` para APIs públicas e `uber-jar-6.6.x-deprecated-apis.jar` para APIs obsoletas.

**Coordenadas Maven para Jar de APIs obsoletos**

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

### Notas do desenvolvedor {#developer-notes}

* O AEM 6.5 LTS não inclui a biblioteca guava da Google pronta para uso. A versão necessária pode ser instalada de acordo com o requisito.
* O pacote XSS do Sling agora usa a biblioteca Java HTML Sanitizer, e o uso do método `XSSAPI#filterHTML()` deve ser usado para renderizar o conteúdo do HTML com segurança e não para transmitir dados para outras APIs.

## Procedimento de teste {#testing-procedure}

Um plano de teste abrangente deve ser preparado para testar as atualizações. O teste da base de código e do aplicativo atualizados deve ser feito primeiro em ambientes inferiores. Quaisquer bugs encontrados devem ser corrigidos de forma iterativa até que a base de código seja estável, somente então os ambientes de nível superior devem ser atualizados.

### Testando o procedimento de atualização {#testing-upgrade-procedure}

O procedimento de atualização descrito aqui deve ser testado em ambientes de Desenvolvimento e Controle de Qualidade, conforme documentado no seu manual de execução personalizado (consulte [Planejando sua atualização](/help/sites-deploying/upgrade-planning.md)). O procedimento de atualização deve ser repetido até que todas as etapas sejam documentadas no livro de execução de atualização e o processo de atualização seja tranquilo.

### Áreas de teste de implementação  {#implementation-test-areas-}

Abaixo estão áreas críticas de qualquer implementação do AEM que devem ser cobertas pelo seu plano de teste depois que o ambiente for atualizado e a base de código atualizada for implantada.

<table>
 <tbody>
  <tr>
   <td><strong>Área de teste funcional</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td>Sites publicados</td>
   <td>Testando a implementação do AEM e o código associado no nível de publicação<br /> por meio da Dispatcher. Deve incluir critérios para atualizações de página e invalidação de cache <br />.</td>
  </tr>
  <tr>
   <td>Criação  </td>
   <td>Testar a implementação do AEM e o código associado no nível do Autor. Deve incluir página, criação de componentes e caixas de diálogo.</td>
  </tr>
  <tr>
   <td>Integrações com as soluções da Experience Cloud</td>
   <td>Validar integrações com produtos como o Analytics.</td>
  </tr>
  <tr>
   <td>Integrações com sistemas de terceiros</td>
   <td>Valide todas as integrações de terceiros nos níveis do Autor e de Publicação.</td>
  </tr>
  <tr>
   <td>Autenticação, segurança e permissões</td>
   <td>Todos os mecanismos de autenticação, como LDAP/SAML, devem ser validados.<br /> Permissões e grupos devem ser testados nos níveis Autor e Publicação<br />.</td>
  </tr>
  <tr>
   <td>Consultas</td>
   <td>Índices e consultas personalizados devem ser testados junto com o desempenho da consulta.</td>
  </tr>
  <tr>
   <td>Personalizações da interface do usuário</td>
   <td>Quaisquer extensões ou personalizações da interface do usuário do AEM no ambiente de criação.</td>
  </tr>
  <tr>
   <td>Fluxos de trabalhos</td>
   <td>Fluxos de trabalho e funcionalidade personalizados e/ou prontos para uso.</td>
  </tr>
  <tr>
   <td>Teste de desempenho</td>
   <td>O teste de carga deve ser executado nos níveis de Autor e Publicação que simulam cenários do mundo real.</td>
  </tr>
 </tbody>
</table>

### Documentar o plano de teste e os resultados {#document-test-plan-and-results}

Deve ser criado um plano de teste que abranja as áreas de teste de implementação acima. Geralmente, faz sentido separar o plano de teste por Listas de tarefas Autor e Publicar. Esse plano de teste deve ser executado em ambientes de Desenvolvimento, Controle de qualidade e Preparo antes da atualização dos ambientes de Produção. Os resultados dos testes e as métricas de desempenho devem ser capturados em ambientes inferiores para fornecer comparação ao atualizar ambientes de Preparo e Produção.
