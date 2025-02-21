---
title: Diretrizes de dimensionamento de hardware
description: Essas diretrizes de dimensionamento oferecem uma aproximação dos recursos de hardware necessários para implantar um projeto AEM.
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader
source-git-commit: ac26c0163309b6cb6c0cfde2098a8cc05955d03f
workflow-type: tm+mt
source-wordcount: '1231'
ht-degree: 0%

---

# Diretrizes de dimensionamento de hardware{#hardware-sizing-guidelines}

Essas diretrizes de dimensionamento oferecem uma aproximação dos recursos de hardware necessários para implantar um projeto AEM. As estimativas de dimensionamento dependem da arquitetura do projeto, da complexidade da solução, do tráfego esperado e dos requisitos do projeto. Este guia ajuda a determinar as necessidades de hardware de uma solução específica ou a encontrar uma estimativa superior e inferior para os requisitos de hardware.

Os fatores básicos a serem considerados são (nesta ordem):

* **Velocidade da rede**

   * Latência de rede
   * Largura de banda disponível

* **Velocidade computacional**

   * Eficiência de armazenamento em cache
   * Tráfego esperado
   * Complexidade de modelos, aplicativos e componentes
   * Autores simultâneos
   * Complexidade da operação de criação (edição simples de conteúdo, implantação do MSM e assim por diante)

* **Desempenho de E/S**

   * Desempenho e eficiência do armazenamento de arquivos ou bancos de dados

* **Disco rígido**

   * pelo menos duas ou três vezes maior que o tamanho do repositório

* **Memória**

   * Tamanho do site (número de objetos de conteúdo, páginas e usuários)
   * Número de usuários/sessões ativos ao mesmo tempo

## Arquitetura {#architecture}

Uma configuração típica do AEM consiste em um ambiente de autor e publicação. Esses ambientes têm requisitos diferentes em relação ao tamanho do hardware subjacente e à configuração do sistema. Considerações detalhadas para ambos os ambientes estão descritas nas seções [ambiente do autor](/help/managing/hardware-sizing-guidelines.md#author-environment-specific-calculations) e [ambiente de publicação](/help/managing/hardware-sizing-guidelines.md#publish-environment-specific-calculations).

Em uma configuração de projeto típica, você tem vários ambientes nos quais preparar fases do projeto:

* **Ambiente de desenvolvimento**
Desenvolver novos recursos ou fazer alterações significativas. A prática recomendada é trabalhar usando um ambiente de desenvolvimento por desenvolvedor (instalações locais em seus sistemas pessoais).

* **Ambiente de teste do autor**
Para verificar as alterações. O número de ambientes de teste pode variar dependendo dos requisitos do projeto (por exemplo, separado para controle de qualidade, teste de integração ou teste de aceitação do usuário).

* **Publicar ambiente de teste**
Principalmente para testar casos de uso de colaboração social e/ou a interação entre o autor e várias instâncias de publicação.

* **Criar ambiente de produção**
Para autores editarem conteúdo.

* **Publicar ambiente de produção**
Para fornecer conteúdo publicado.

Além disso, os ambientes podem variar, desde um sistema de servidor único executando o AEM e um servidor de aplicativos até um conjunto altamente dimensionado de instâncias clusterizadas de vários servidores e várias CPU. A Adobe recomenda que você use um computador separado para cada sistema de produção e que não execute outros aplicativos nesses computadores.

## Considerações de dimensionamento de hardware genérico {#generic-hardware-sizing-considerations}

As seções abaixo fornecem orientação sobre como calcular os requisitos de hardware, levando em conta várias considerações. Para sistemas grandes, a Adobe sugere que você execute um conjunto simples de testes de desempenho internos em uma configuração de referência.

A otimização de desempenho é uma tarefa fundamental que precisa ser executada antes que qualquer benchmark de um projeto específico possa ser feito. Aplique a dica fornecida na [documentação de Otimização de Desempenho](/help/sites-deploying/configuring-performance.md) antes de executar testes de referência de desempenho e usar seus resultados para qualquer cálculo de dimensionamento de hardware.

Os requisitos de dimensionamento de hardware para casos de uso avançados devem se basear em uma avaliação detalhada do desempenho do projeto. As características dos casos de uso avançados que exigem recursos de hardware excepcionais incluem combinações de:

* carga/taxa de transferência de alto conteúdo
* uso abrangente de código personalizado, fluxos de trabalho personalizados ou bibliotecas de software de terceiros
* integração com sistemas externos não compatíveis

## Espaço em disco/disco rígido {#disk-space-hard-drive}

O espaço em disco necessário depende muito do volume e do tipo do aplicativo Web. Os cálculos devem levar em conta o seguinte:

* a quantidade e o tamanho das páginas, dos ativos e de outras entidades armazenadas no repositório, como fluxos de trabalho, perfis etc.
* a frequência estimada de alterações de conteúdo e, portanto, a criação de versões de conteúdo
* o volume de representações de ativos do DAM que será gerado
* o crescimento geral do conteúdo ao longo do tempo

O espaço em disco é monitorado continuamente durante a Limpeza de revisão on-line e off-line. Se o espaço em disco disponível ficar abaixo de um valor crítico, o processo será cancelado. O valor crítico é 25% do espaço em disco atual do repositório e não é configurável. A Adobe recomenda dimensionar o disco pelo menos duas ou três vezes maior que o tamanho do repositório, incluindo o crescimento estimado.

### Virtualização {#virtualization}

O AEM é bem executado em ambientes virtualizados, mas pode haver fatores como CPU ou E/S que não podem ser diretamente comparados ao hardware físico. Uma recomendação é escolher uma velocidade de I/O mais alta (em geral), pois esse é um fator crítico, geralmente. A avaliação comparativa do ambiente é necessária para obter uma compreensão precisa de quais recursos são necessários.

### Paralelização de instâncias do AEM {#parallelization-of-aem-instances}

**Segurança contra falhas**

Um site à prova de falhas é implantado em pelo menos dois sistemas separados. Se um sistema falhar, outro sistema poderá assumir o controle e, assim, compensar a falha do sistema.

**Escalabilidade dos recursos do sistema**

Enquanto todos os sistemas estão em execução, um maior desempenho computacional está disponível. Esse desempenho adicional não é necessariamente linear com o número de nós de cluster, pois o relacionamento é altamente dependente do ambiente técnico. Consulte a [Documentação do cluster](/help/sites-deploying/recommended-deploys.md) para obter mais informações.

A estimativa de quantos nós de cluster são necessários baseia-se nos requisitos básicos e nos casos de uso específicos do projeto da Web:

* Do ponto de vista da segurança contra falhas, é necessário determinar, para todos os ambientes, o nível crítico de falha e o tempo de compensação com base no tempo necessário para a recuperação de um nó de cluster.
* Para o aspecto da escalabilidade, o número de operações de gravação é basicamente o fator mais importante. O balanceamento de carga pode ser estabelecido para operações que acessam o sistema apenas para processar operações de leitura; consulte [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=pt-BR) para obter detalhes.

### Recomendações de hardware {#hardware-recommendations}

Normalmente, você pode usar o mesmo hardware para o ambiente de criação que é recomendado para o ambiente de publicação. Normalmente, o tráfego do site é menor nos sistemas de criação, mas a eficiência do cache também é menor. No entanto, o fator fundamental aqui é o número de autores trabalhando em paralelo, juntamente com o tipo de ações que estão sendo feitas no sistema. Em geral, a organização por clusters do AEM (do ambiente do autor) é mais eficaz no dimensionamento de operações de leitura; em outras palavras, um cluster do AEM é bem dimensionado com autores que estão executando operações básicas de edição.

## Cálculos adicionais específicos de caso de uso {#additional-use-case-specific-calculations}

Além do cálculo de um aplicativo web padrão, considere fatores específicos para os seguintes casos de uso. Os valores calculados devem ser adicionados ao cálculo padrão.

### Considerações específicas do Assets {#assets-specific-considerations}

O processamento extensivo de ativos digitais requer recursos de hardware otimizados. Os fatores mais relevantes são o tamanho da imagem e a taxa de transferência máxima das imagens processadas.

Aloque pelo menos 16 GB de heap e configure o fluxo de trabalho do [!UICONTROL Ativo de atualização do DAM] para usar o [pacote do Camera Raw](/help/assets/camera-raw.md) para a assimilação de imagens brutas.

>[!NOTE]
>
>Um throughput mais alto de imagens significa que os recursos de computação devem ser capazes de acompanhar o I/O do sistema e vice-versa. Por exemplo, se os workflows forem iniciados pela importação de imagens, o upload de muitas imagens via WebDAV poderá causar um backlog de workflows.
>
>O uso de discos separados para TarPM, armazenamento de dados e índice de pesquisa pode ajudar a otimizar o comportamento de I/O do sistema (no entanto, geralmente faz sentido manter o índice de pesquisa localmente).

>[!NOTE]
>
>Consulte também o [Guia de Desempenho do Assets](/help/sites-deploying/assets-performance-sizing.md).

### Gerenciador de vários sites {#multi-site-manager}

O consumo de recursos ao usar o AEM MSM em um ambiente de criação depende muito dos casos de uso específicos. Os fatores básicos são:

* Número de Live Copies
* Periodicidade das implantações
* Tamanho da árvore de conteúdo a ser implantada
* Funcionalidade conectada das ações de implantação

Testar o caso de uso planejado com um trecho de conteúdo representativo pode ajudar você a entender melhor o consumo de recursos. Se você extrapolar os resultados com a taxa de transferência planejada, poderá avaliar os recursos adicionais necessários para o MSM do AEM.

Além disso, leve em conta os autores que trabalham em paralelo. Eles perceberão os efeitos colaterais do desempenho se os casos de uso do AEM MSM consumirem mais recursos do que o planejado.
