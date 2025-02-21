---
title: Planejando sua atualização
description: Este artigo ajuda a estabelecer metas, fases e resultados claros ao planejar a atualização do AEM.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: f66bb283e5c2a746821839269e112be8c2714ba7
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 0%

---

# Planejando sua atualização {#planning-your-upgrade}

## Visão geral da atualização do AEM {#aem-upgrade-overview}

O AEM é frequentemente usado em implantações de alto impacto que podem atender a milhões de usuários. Normalmente, há aplicativos personalizados implantados nas instâncias, o que aumenta a complexidade. Qualquer esforço para atualizar essa implantação precisa ser tratado metodicamente.

Este guia ajuda a estabelecer metas, fases e resultados claros ao planejar sua atualização. Ele se concentra na execução e nas diretrizes gerais de atualização. Embora forneça uma visão geral das etapas de atualização reais, ele se refere aos recursos técnicos disponíveis, quando apropriado. Deve ser utilizado com os recursos técnicos disponíveis referidos no documento.

O processo de atualização do AEM precisa ser cuidadosamente tratado nas fases de planejamento, análise e execução, com os principais resultados definidos para cada fase.

>[!NOTE]
>
>A atualização para o AEM 6.5 LTS é compatível com os últimos 6 Service packs

É importante garantir que você esteja executando um sistema operacional compatível, Java™ runtime, httpd e a versão do Dispatcher. Para obter mais informações, consulte a seguir: link para o requisito técnico do AEM 6.5 LTS. A atualização desses componentes deve ser contabilizada em seu plano de atualização e deve ocorrer antes da atualização do AEM.

<!-- Alexandru: drafting for now

## Upgrade Scope and Requirements {#upgrade-scope-requirements}

Below you will find a list of areas that are impacted in a typical AEM Upgrade project:

<table>
 <tbody>
  <tr>
   <td><strong>Component</strong></td>
   <td><strong>Impact</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>Operating System</td>
   <td>Uncertain, but subtle effects</td>
   <td>At the time of the AEM upgrade, it may be time to upgrade the operating system as well and this might have some impact.</td>
  </tr>
  <tr>
   <td>Java&trade; Runtime</td>
   <td>Moderate Impact</td>
   <td>AEM 6.3 requires JRE 1.7.x (64 bit) or later. JRE 1.8 is the only version currently supported by Oracle.</td>
  </tr>
  <tr>
   <td>Hardware</td>
   <td>Moderate Impact</td>
   <td>Online Revision Cleanup requires free<br /> disk space equal to 25% of the repository's size and 15% free heap space<br /> to complete successfully. You may need to upgrade your hardware to<br /> ensure sufficient resources for Online Revision Cleanup to fully<br /> run. Also, if upgrading from a version prior to AEM 6, there<br /> may be additional storage requirements.</td>
  </tr>
  <tr>
   <td>Content Repository (CRX or Oak)</td>
   <td>High Impact</td>
   <td>Starting from version 6.1, AEM does not support CRX2, so a migration to<br /> Oak (CRX3) is required if upgrading from an older version. AEM 6.3 has<br /> implemented a new Segment Node Store that also requires a migration. The<br /> crx2oak tool is used for this purpose.</td>
  </tr>
  <tr>
   <td>AEM Components/Content</td>
   <td>Moderate Impact</td>
   <td><code>/libs</code> and <code>/apps</code> are easily handled through the upgrade, but <code>/etc</code> usually requires some manual reapplication of customizations.</td>
  </tr>
  <tr>
   <td>AEM Services</td>
   <td>Low Impact</td>
   <td>Most AEM core services are tested for upgrade. This is an area of low impact.</td>
  </tr>
  <tr>
   <td>Custom Application Services</td>
   <td>Low to High Impact</td>
   <td>Depending on the application and customization, there may be<br /> dependencies on JVM, operating system versions, and some indexing related<br /> changes, as indexes are not generated automatically in Oak.</td>
  </tr>
  <tr>
   <td>Custom Application Content</td>
   <td>Low to High Impact</td>
   <td>Content that will not be handled through the upgrade can be backed up<br /> before the upgrade takes place and then moved back into the repository.<br /> Most content can be handled through the migration tool.</td>
  </tr>
 </tbody>
</table>

It is important to ensure that you are running a supported operating system, Java&trade; runtime, httpd, and Dispatcher version. For more information, see the [AEM 6.5 Technical Requirements page](/help/sites-deploying/technical-requirements.md). Upgrading these components must be accounted for in your project plan and should take place before upgrading AEM. -->

## Fases de atualização {#upgrade-phases}

Muito trabalho é dedicado ao planejamento e à execução de uma atualização do AEM. Para esclarecer os diferentes esforços que entram nesse processo, a Adobe dividiu os exercícios de planejamento e execução em fases separadas. Nas seções abaixo, cada fase resulta em um material de entrega que é usado com frequência em uma fase futura da atualização.

<!-- Alexandru:drafting for now

### Planning for Author Training {#planning-for-author-training}

With any new release, there are potential changes to the UI and user workflows that may be introduced. Also, new releases introduce new features that may be beneficial for the business to use. Adobe recommends reviewing the functional changes that have been introduced and organizing a plan to train your users on using them effectively.

![unu_cropped](assets/unu_cropped.png)

New features in AEM 6.5 can be found in [the AEM section of adobe.com](/help/release-notes/release-notes.md). Make sure to note any changes to UIs or product features that are commonly used in your organization. As you look through the new features, also take note of any that can be of value to your organization. After looking through what has changed in AEM 6.5, develop a training plan for your authors. This could involve using freely available resources like the help feature videos or formal training offered through [Adobe Digital Learning Services](https://learning.adobe.com/). -->

### Criando um Plano de Teste {#creating-a-test-plan}

A implementação do AEM por cada cliente é exclusiva e foi personalizada para atender às suas necessidades de negócios. Como resultado, é importante determinar todas as personalizações feitas no sistema para que possam ser incluídas em um plano de teste. Esse plano de teste alimentará o processo de controle de qualidade que o Adobe executa na instância atualizada.

O ambiente de produção exato precisa ser duplicado e testes devem ser executados nele após a atualização para garantir que todos os aplicativos e códigos personalizados ainda sejam executados conforme desejado. Regressar toda a personalização e executar testes de desempenho, carga e segurança. Ao organizar seu plano de teste, cubra todas as personalizações feitas no sistema, além das interfaces do usuário e dos fluxos de trabalho prontos para uso usados em suas operações diárias. Eles podem incluir serviços e servlets OSGI personalizados, integrações com a Adobe Experience Cloud, integrações com terceiros por meio de conectores do AEM, integrações personalizadas de terceiros, componentes e modelos personalizados, sobreposições de interface do usuário personalizadas no AEM e fluxos de trabalho personalizados. Além disso, as consultas personalizadas ainda devem ser testadas para garantir que seus índices continuem funcionando com eficiência após a atualização.

### Avaliando a complexidade da atualização {#assessing-upgrade-complexity}

Devido à grande variedade na quantidade e na natureza das personalizações que os clientes do Adobe aplicam aos ambientes AEM, é importante reservar algum tempo para determinar o nível geral de esforço que deve ser esperado na atualização. O Analyzer para AEM pode ajudá-lo a avaliar a complexidade da atualização.

O AEM Analyzer para AEM 6.5 LTS deve fornecer uma estimativa bastante precisa do que esperar durante uma atualização para a maioria dos casos. No entanto, para personalizações e implantações mais complexas nas quais você tem alterações incompatíveis, é possível atualizar uma instância de desenvolvimento para o AEM 6.5 LTS de acordo com as instruções em [Executando uma atualização no local](/help/sites-deploying/in-place-upgrade.md). Depois de concluído, execute alguns testes de alto nível de fumaça nesse ambiente. O objetivo deste exercício não é completar exaustivamente o inventário de casos de teste e produzir um inventário formal de defeitos, mas fornecer uma estimativa aproximada da quantidade de trabalho que será necessário para atualizar o código para a compatibilidade com a 6.5 LTS. Quando combinado com o analisador do AEM e as alterações de arquitetura determinadas na seção anterior, uma estimativa aproximada pode ser fornecida à equipe de gerenciamento do projeto para o planejamento da atualização.

### Criação do Runbook de atualização e reversão {#building-the-upgrade-and-rollback-runbook}

Embora a Adobe tenha documentado o processo de upgrade de uma instância do AEM, o layout de rede, a arquitetura de implantação e as personalizações de cada cliente exigem o ajuste e a personalização dessa abordagem. Por esse motivo, a Adobe incentiva que você revise toda a documentação fornecida e a use-a para informar um runbook específico para atualização que descreve os procedimentos específicos de atualização e reversão que você seguirá em seu ambiente.

<!--Alexandru:drafting for now

![runbook-diagram](assets/runbook-diagram.png) -->

A Adobe forneceu procedimentos de atualização e reversão em [Procedimento de Atualização](/help/sites-deploying/upgrade-procedure.md) e instruções passo a passo para aplicar a atualização em Execução de uma [Atualização In-loco](/help/sites-deploying/in-place-upgrade.md). Essas instruções devem ser revisadas e consideradas com a arquitetura do sistema, as personalizações e a tolerância ao tempo de inatividade para determinar os procedimentos de comutação e reversão apropriados que serão executados durante o upgrade. Quaisquer alterações na arquitetura ou nos tamanhos do servidor devem ser incluídas ao elaborar o runbook personalizado.

### Desenvolvendo um plano de atualização {#developing-an-upgrade-plan}

O resultado dos exercícios anteriores pode ser usado para criar um plano de atualização que abranja os cronogramas esperados para seus esforços de teste ou desenvolvimento, treinamento e execução de atualização real.

<!--Alexandru: drafting for now

![develop-project-plan](assets/develop-project-plan.png) -->

Um plano de projeto abrangente deve incluir:

* Finalização dos planos de desenvolvimento e teste
* Atualização de ambientes de desenvolvimento e controle de qualidade
* Atualização da base de código personalizado para AEM 6.5 LTS
* Um ciclo de teste e correção de controle de qualidade
* Atualização do ambiente de preparo
* Integração, desempenho e teste de carga
* Certificação de ambiente
* Ativar

### Execução de desenvolvimento e controle de qualidade {#performing-development-and-qa}

A Adobe forneceu procedimentos para [Atualização de Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md) para serem compatíveis com o AEM 6.5 LTS. À medida que esse processo iterativo é executado, as alterações devem ser feitas no runbook, conforme necessário.

<!--Alexandru: drafting for now

![patru_cropped](assets/patru_cropped.png) -->

O processo de desenvolvimento e teste é geralmente iterativo. À medida que são descobertos problemas que exigem ajustes no processo de atualização, adicione-os ao runbook de atualização personalizado. Após várias iterações de teste e correção, a base de código deve ser totalmente validada e pronta para implantação no ambiente de preparo.

### Teste final {#final-testing}

A Adobe recomenda uma rodada final de testes depois que a base de código tiver sido certificada pela equipe de controle de qualidade da sua organização. Esta rodada de testes envolverá a validação do runbook em um ambiente de preparo, seguida por rodadas de aceitação do usuário, desempenho e testes de segurança.

<!--Alexandru: drafting for now

![cinci_cropped](assets/cinci_cropped.png) -->

Essa etapa é essencial, pois é a única vez que você pode validar as etapas no runbook em relação a um ambiente semelhante à produção. Depois que o ambiente for atualizado, é importante dar aos usuários finais algum tempo para fazer logon e passar pelas atividades que eles realizam ao usar o sistema em suas atividades diárias. Encontrar e corrigir problemas nessas áreas antes da ativação pode ajudar a evitar paralisações dispendiosas da produção.

### Execução da atualização {#performing-the-upgrade}

Depois que a aprovação final for recebida de todas as partes interessadas, é hora de executar os procedimentos de runbook definidos. A Adobe forneceu etapas para atualização e reversão no [Procedimento de Atualização](/help/sites-deploying/upgrade-procedure.md) e etapas de instalação em Execução de uma [Atualização In-loco](/help/sites-deploying/in-place-upgrade.md) como ponto de referência.

![executar-atualização](assets/perform-upgrade.png)

A Adobe forneceu algumas etapas nas instruções de atualização para validação do ambiente. Isso inclui verificações básicas, como verificar os logs de atualização e verificar se todos os pacotes OSGi foram iniciados corretamente, mas a Adobe também recomenda validar com seus próprios casos de teste com base nos processos de negócios. A Adobe também recomenda verificar a programação da Limpeza de revisão on-line do AEM e rotinas relacionadas para garantir que elas ocorram durante um período de silêncio da sua empresa. Essas rotinas são essenciais para o desempenho a longo prazo do AEM.