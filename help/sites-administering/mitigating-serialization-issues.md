---
title: Redução de problemas de serialização no AEM
description: Saiba como atenuar problemas de serialização no AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---

# Redução de problemas de serialização no AEM{#mitigating-serialization-issues-in-aem}

## Visão geral {#overview}

A equipe do AEM na Adobe trabalhou em conjunto com o projeto de código aberto [NotSoSerial](https://github.com/kantega/notsoserial) para ajudar a mitigar as vulnerabilidades descritas em **CVE-2015-7501**. NotSoSerial é licenciado sob a [licença do Apache 2](https://www.apache.org/licenses/LICENSE-2.0) e inclui o código ASM licenciado sob sua própria [licença semelhante à BSD](https://asm.ow2.io/).

O jar do agente incluído neste pacote é a distribuição modificada do NotSoSerial pela Adobe.

NotSoSerial é uma solução em nível Java™ para um problema em nível Java™ e não é específica da AEM. Ele adiciona uma verificação de comprovação a uma tentativa de desserializar um objeto. Essa verificação testa um nome de classe em relação a uma inclui na lista de permissões de estilo de firewall, ou inclui na lista de bloqueios, ou ambos. Devido ao número limitado de classes no incluo na lista de bloqueios padrão, é improvável que esse teste afete seus sistemas ou códigos.

Por padrão, o agente executa uma verificação de inclui na lista de bloqueios em relação às classes vulneráveis conhecidas no momento. Essa inclui na lista de bloqueios destina-se a protegê-lo da lista atual de explorações que usam esse tipo de vulnerabilidade.

A inclui na lista de bloqueios e a inclui na lista de permissões podem ser configuradas seguindo as instruções na seção [Configuração do Agente](/help/sites-administering/mitigating-serialization-issues.md#configuring-the-agent) deste artigo.

O agente deve ajudar a reduzir as classes vulneráveis conhecidas mais recentes. Se o seu projeto estiver desserializando dados não confiáveis, ele ainda poderá estar vulnerável a ataques de negação de serviço, ataques de memória insuficiente e explorações desconhecidas de desserialização futuras.

A Adobe oferece suporte oficial ao Java™ 6, 7 e 8. No entanto, a Adobe sabe que o NotSoSerial também é compatível com o Java™ 5.

## Instalar o agente {#installing-the-agent}

>[!NOTE]
>
>Se você tiver instalado anteriormente a correção de serialização para o AEM 6.1, remova os comandos de início do agente da linha de execução do Java™.

1. Instale o pacote **com.adobe.cq.cq-serialization-tester**.

1. Ir para o Console da Web do Pacote em `https://server:port/system/console/bundles`
1. Procure o pacote de serialização e inicie-o. Isso faz com que o carregue automaticamente o agente NotSoSerial.

## Instalando o Agente nos Servidores de Aplicações {#installing-the-agent-on-application-servers}

O agente NotSoSerial não está incluído na distribuição padrão do AEM para servidores de aplicativos. No entanto, você pode extraí-lo da distribuição jar do AEM e usá-lo com a configuração do servidor de aplicativos:

1. Primeiro, baixe o arquivo de início rápido do AEM e extraia-o:

   ```shell
   java -jar aem-quickstart-6.2.0.jar -unpack
   ```

1. Vá para o local da inicialização rápida do AEM recém-descompactada e copie a pasta `crx-quickstart/opt/notsoserial/` para a pasta `crx-quickstart` da instalação do servidor de aplicativos do AEM.

1. Alterar a propriedade de `/opt` para o usuário que está executando o servidor:

   ```shell
   chown -R opt <user running the server>
   ```

1. Configure e verifique se o agente foi ativado corretamente, conforme mostrado nas seções a seguir deste artigo.

## Configurar o agente {#configuring-the-agent}

A configuração padrão é adequada para a maioria das instalações. Essa configuração inclui uma incluir na lista de bloqueios inclui na lista de permissões de classes vulneráveis de execução remota conhecida e um grupo de pacotes de em que a desserialização de dados confiáveis é segura.

A configuração do firewall é dinâmica e pode ser alterada a qualquer momento por:

1. Acessando o Console da Web em `https://server:port/system/console/configMgr`
1. Procurando e clicando em **Configuração do Firewall de Desserialização.**

   >[!NOTE]
   >
   >Você também pode acessar a página de configuração diretamente acessando o URL em:
   >
   >* `https://server:port/system/console/configMgr/com.adobe.cq.deserfw.impl.DeserializationFirewallImpl`

Essa configuração contém os registros incluir na lista de permissões, incluir na lista de bloqueios e desserializar.

**Permitir Listagem**

Na seção lista de permissões, essas listagens são classes ou prefixos de pacote permitidos para desserialização. Se você estiver desserializando suas próprias classes, adicione as classes ou pacotes a este incluo na lista de permissões.

**Listagem de Bloqueios**

Na seção de listagem de blocos, há classes que nunca têm permissão para desserialização. O conjunto inicial dessas classes é limitado às classes que foram consideradas vulneráveis a ataques de execução remota. A inclui na lista de bloqueios ➡ é aplicada antes de qualquer entrada na lista de permissões.

**Log de Diagnóstico**

Na seção para logs de diagnóstico, você pode escolher várias opções para registrar quando a desserialização estiver ocorrendo. Essas opções só são registradas no primeiro uso e não são registradas novamente em usos subsequentes.

O padrão **class-name-only** informa as classes que estão sendo desserializadas.

Você também pode definir a opção **pilha completa**, que registra uma pilha do Java™ da primeira tentativa de desserialização para informar onde a desserialização está ocorrendo. Essa opção é útil para encontrar e remover a desserialização do seu uso.

## Verificando a ativação do agente {#verifying-the-agent-s-activation}

Você pode verificar a configuração do agente de desserialização navegando até o URL em:

* `https://server:port/system/console/healthcheck?tags=deserialization`

Após acessar o URL, uma lista de verificações de integridade relacionadas ao agente é exibida. Você pode determinar se o agente está ativado corretamente, verificando se as verificações de integridade estão sendo bem-sucedidas. Se eles estiverem falhando, você deve carregar o agente manualmente.

Para obter mais informações sobre como solucionar problemas com o agente, consulte [Manipulando erros com o carregamento do agente dinâmico](#handling-errors-with-dynamic-agent-loading) abaixo.

>[!NOTE]
>
>Se você adicionar `org.apache.commons.collections.functors` ao arquivo de inclui na lista de permissões, a verificação de integridade sempre falhará.

## Manipular erros com o carregamento dinâmico do agente {#handling-errors-with-dynamic-agent-loading}

Se erros forem expostos no registro ou se as etapas de verificação detectarem um problema ao carregar o agente, carregue o agente manualmente. Esse fluxo de trabalho também é recomendado se você usar um JRE (Java™ Runtime Environment) em vez de um JDK (Java™ Development Toolkit), porque as ferramentas para carregamento dinâmico não estão disponíveis.

Para carregar o agente manualmente, faça o seguinte:

1. Edite os parâmetros de inicialização da JVM do jar do CQ, adicionando a seguinte opção:

   ```shell
   -javaagent:<aem-installation-folder>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   >[!NOTE]
   >
   >Exige que você use a opção -nofork CQ/AEM também, juntamente com as configurações de memória JVM apropriadas, pois o agente não está ativado em uma JVM bifurcada.

   >[!NOTE]
   >
   >A distribuição Adobe do jar do agente NotSoSerial pode ser encontrada na pasta `crx-quickstart/opt/notsoserial/` da sua instalação do AEM.

1. Interrompa e reinicie a JVM;

1. Verifique a ativação do agente novamente seguindo as etapas descritas acima em [Verificando a Ativação do Agente](/help/sites-administering/mitigating-serialization-issues.md#verifying-the-agent-s-activation).

## Outras considerações {#other-considerations}

Se você estiver executando em uma IBM® JVM, reveja a documentação de suporte da API Java™ Attach em [este local](https://www.ibm.com/docs/en/sdk-java-technology/8?topic=documentation-java-attach-api).
