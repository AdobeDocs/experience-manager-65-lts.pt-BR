---
title: Notas de versão atuais do Adobe Experience Manager 6.5 LTS, SP3
description: Encontre informações sobre a versão atual do Adobe Experience Manager 6.5 LTS, Service Pack 3.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 0ce890503d43af340b6ee3c85b1b563613627c78
workflow-type: tm+mt
source-wordcount: '6749'
ht-degree: 26%

---


# Notas de versão atuais do Adobe Experience Manager 6.5 LTS, SP3 {#release-notes}

## Informações da versão {#release-information}

| Produto | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Versão | Service Pack 3 (SP3) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Tipo | Versão do pacote de serviços |
| Data | 20 de agosto de 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL de download | [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.3.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

<!-- **Mandatory Hotfix** – To avoid SNFE (SegmentNotFoundException) issues with offline compaction when installing SP2, install the hotfix described in [Known issues – Repository corruption during online compaction](#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146). -->

## O que está incluído no [!DNL Adobe Experience Manager] 6.5 LTS, SP3 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

O [!DNL Experience Manager] 6.5 LTS, SP3 inclui novos recursos, importantes melhorias solicitadas por clientes e correções de erros. Ele melhora o desempenho, a segurança e a localização na plataforma desde a disponibilidade inicial do 6.5 LTS em março de 2025. [Instale este pacote de serviços](#install-update) no 6.5 LTS.

### Visão geral de problemas corrigidos {#fixed-issues-overview}

O [!DNL Adobe Experience Manager] 6.5 LTS, SP3 resolve problemas entre [!DNL Sites] e [!DNL Experience Manager Foundation]. As correções melhoram a acessibilidade, a confiabilidade da criação, a entrega de conteúdo headless, o gerenciamento de vários sites e a estabilidade da plataforma. As seções a seguir listam cada correção com seu número de referência.

A maioria das alterações se aplica a [!DNL Sites]:

* As melhorias de acessibilidade formam o maior grupo. As atualizações fortalecem a navegação pelo teclado, o feedback do leitor de tela, o gerenciamento de foco, a marcação semântica, o contraste do texto e o dimensionamento do destino de toque no Editor de páginas, no painel lateral do Assets, nos filtros e nas interfaces de criação relacionadas.
* As correções em [!DNL Content Fragments] abrangem o Editor de Fragmentos, o Editor de Modelos, a API REST e a API GraphQL. As atualizações estão corretas: localização, validação de campo, comportamento de edição e tratamento de resposta.
* As correções de Live Copies do MSM permitem que os autores implantem alterações de forma confiável a partir de páginas de blueprint e preservem as configurações de implantação existentes.
* O suporte ao Crosswalk está disponível no Adobe Managed Services, incluindo os pacotes necessários, usuários do sistema e configuração.
* Outras correções abordam as interfaces admin e clássica, os Componentes principais, o console do Componente, a integração do Campaign, os Fragmentos de experiência e os Lançamentos.

As alterações restantes se aplicam a [!DNL Experience Manager Foundation]:

* As atualizações de localização traduzem textos anteriormente somente em inglês entre os Relatórios de integridade, o console Operações e várias interfaces de criação.
* As correções de estabilidade restauram o endpoint de monitoramento de integridade, mantêm o serviço de email em execução após erros intermitentes de configuração e corrigem a edição da variável de fluxo de trabalho e do pacote de fluxo de trabalho.
* A versão também adiciona suporte ao AEM Context Service e resolve problemas de segurança, tradução e interface do usuário.

Para obter a lista completa, consulte [Problemas corrigidos em 6.5 LTS, Service Pack 3](#fixed-issues).


<!-- ## Key features and enhancements -->



<!-- UPDATE THE EACH RELEASE -->

## Correção de problemas no 6.5 LTS, Service Pack 3 {#fixed-issues}

### [!DNL Sites]{#sites-65-LTS-SP3}

* O AEM 6.5 LTS, Service Pack 3 inclui os pacotes Crosswalk, pacote de conteúdo, usuários do sistema, mapeamentos de usuário de serviço, opções de recurso e a configuração OSGi necessária. Novas instalações fornecem os pré-requisitos do Crosswalk automaticamente e exigem apenas configuração de tempo de execução específica do cliente. (SITES-41596)
* O AEM 6.5 LTS, Service Pack 3 atualiza o `cq-wcm-core` para oferecer suporte ao Crosswalk no Adobe Managed Services. A atualização adiciona a criação de modelo e o acesso ao Editor universal, além de remover códigos personalizados obsoletos e alternâncias de recursos. (SITES-37657)


#### Acessibilidade {#sites-accessibility-65-lts-sp3}

* A tela Editor de páginas agora é compatível com o gerenciamento de componentes somente de teclado. Os autores podem usar Inserir componente, Recortar, Colar e Excluir para adicionar, reordenar e remover componentes. (SITES-25359) CRÍTICO
* Os usuários de teclado agora podem reordenar linhas da tabela na Exibição de lista do Sites sem usar gestos de arrastar e soltar. Os controles de teclado permitem que os usuários selecionem uma linha, movam-na para outra posição e concluam o posicionamento. (SITES-24946) CRÍTICO

* O editor de Propriedades personalizadas agora oferece suporte à interação do teclado com seus controles de formatação. Os autores podem mover o foco entre as opções da barra de ferramentas, selecionar um estilo de texto e formatar valores de propriedade usando apenas um teclado. (SITES-40333) PRINCIPAL

* O foco do teclado agora ignora a lista Componentes do painel lateral quando a interação disponível requer arrastar e soltar. Essa alteração impede que os usuários de teclado insiram um fluxo de trabalho de seleção de componentes inutilizável. (SITES-40752)
* Fechar uma sobreposição agora restaura o foco para o controle de acionamento. Os usuários de teclado e leitor de tela não retornam mais à sobreposição ou perdem sua posição na interface. (SITES-40819)
* A navegação pelo teclado não move mais o foco para o conteúdo de página oculto. Essa alteração mantém uma sequência de foco previsível e impede interrupções na navegação. (SITES-41430)
* O botão Bloquear agora fornece feedback preciso do leitor de tela com base em seu título. Os usuários ouvem um rótulo de ação claro em vez de uma descrição longa. (SITES-41431)
* Um indicador visual agora identifica a opção selecionada na caixa de listagem Alterar arquivo ou pasta. O indicador ajuda os usuários a entender o caminho de navegação estrutural e reconhecer a pasta atual. (SITES-25532)
* Agora, os leitores de tela anunciam a direção de classificação crescente ou decrescente uma vez. Um rótulo descritivo identifica claramente a ação do botão e remove o feedback duplicado. (SITES-25534)
* O AEM Sites agora oferece suporte mais amplo à acessibilidade em fluxos de trabalho de criação comuns. As atualizações melhoram a interação do teclado, os rótulos da interface, o gerenciamento de foco e o feedback da tecnologia assistiva. (SITES-38239)
* Os itens da barra de ferramentas agora exibem rótulos visíveis quando recebem foco do teclado. Os usuários de teclado podem identificar cada controle antes de ativá-lo. (SITES-40751)
* Os usuários de teclado e leitor de tela agora podem deixar o menu Caixa de entrada sem deixá-lo aberto. O menu é fechado automaticamente e preserva um caminho de navegação claro. (SITES-25518)
* As amostras de cores agora exibem um ícone de estado selecionado com contraste suficiente. O indicador mais claro ajuda os usuários a reconhecer a amostra ativa em diferentes cores de plano de fundo. (SITES-25523)
* A barra de ferramentas Editar layout agora relata o dispositivo atual com precisão para a tecnologia assistiva. Os botões de dispositivo não sugerem mais que os usuários podem ativar e desativar cada botão. (SITES-25524)
* O modal Pesquisar agora exibe o rótulo **Classificar por** com contraste de texto suficiente. O estilo atualizado melhora a legibilidade para usuários com pouca visão. (SITES-25531)
* Os botões de classificação de Exibição de lista do Sites agora atendem aos requisitos mínimos de contraste. Os usuários podem identificar cada controle de classificação e seu estado mais facilmente no plano de fundo da tabela. (SITES-25372)
* A lista Assets do painel lateral não é mais recarregada quando o campo Filtro recebe foco do teclado. Os usuários podem entrar no campo sem movimentação inesperada de conteúdo ou anúncios repetidos de carregamento do leitor de tela. (SITES-25377)
* As guias da barra lateral do Fragmento de conteúdo agora fornecem rótulos acessíveis consistentes. O NVDA anuncia o nome da guia em vez de anunciar o item de subnavegação selecionado. (SITES-25509)
* O menu Ajuda agora é fechado quando o foco do teclado ou do leitor de tela se move para fora dele. Os usuários podem continuar navegando nos controles de cabeçalho ou no conteúdo da página sem deixar o menu aberto. (SITES-25517)
* O texto inserido nos campos da barra de ferramentas Demografia agora atende aos requisitos mínimos de contraste. Os usuários podem ler os valores do perfil com mais clareza no plano de fundo do campo de texto. (SITES-25318)
* O menu Informações da página agora exibe opções focalizadas com contraste de texto suficiente. O estilo mais claro ajuda os usuários a rastrear o foco do teclado no menu. (SITES-25321)
* As caixas de seleção nas caixas de diálogo Teaser, Imagem e Carrossel agora expõem suas instruções relacionadas aos leitores de tela. Os usuários ouvem a descrição de suporte quando o foco do teclado atinge cada caixa de seleção. (SITES-25364)
* Os controles do editor de texto agora comunicam seu estado atual à tecnologia assistiva. Os leitores de tela identificam o formato de parágrafo ativo e a opção de destino de hiperlink selecionada. (SITES-25367)
* Os leitores de tela agora anunciam claramente o botão **Girar Dispositivo** e a orientação atual do dispositivo. Ativar o controle informa a nova orientação sem usar um rótulo que descreve a ação oposta. (SITES-25292)
* A navegação pelo teclado agora ignora os controles ocultos na barra de ferramentas Demográficos recolhida. Os usuários podem passar pela Visualização de layout sem encontrar opções indisponíveis na barra de ferramentas. (SITES-25304)
* Os rótulos de texto na barra de ferramentas Demografia agora atendem aos requisitos mínimos de contraste durante a Visualização de layout. Os usuários podem ler rótulos como Recomendado com mais clareza no plano de fundo da barra de ferramentas. (SITES-25307)
* A barra de ferramentas Demografia agora exibe indicadores de foco de botão com contraste suficiente. Os usuários podem identificar o controle ativo do Commerce, Persona ou Device durante a navegação pelo teclado. (SITES-25308)
* A barra de ferramentas Editar layout usa um indicador de foco agrupado para o seletor de dispositivos. A estrutura inclui os controles relacionados do **Selecionar Dispositivo** e do **Girar Dispositivo** como parte do comportamento da barra de ferramentas pretendido. (SITES-25283)
* A barra de ferramentas Editar Layout não trunca mais o rótulo do **iPhone 8 Plus** quando os usuários selecionam outro dispositivo. O nome completo do dispositivo permanece visível em todos os estados do botão. (SITES-25284)
* A régua Editar layout agora fornece contexto de medição aos leitores de tela. Os usuários ouvem um rótulo descritivo e o formato de medição em vez de uma série inexplicável de números. (SITES-25287)
* A barra de ferramentas Editar Layout agora destaca o botão **Área de Trabalho** quando o modo de exibição de área de trabalho está ativo. O indicador visual deixa a seleção do dispositivo atual clara. (SITES-25290)
* O foco do teclado agora permanece visível no botão de amostra em todas as cores disponíveis. O espaçamento adicionado impede que o indicador de foco se misture na amostra selecionada. (SITES-25253)
* Agora, os leitores de tela identificam o campo Data do Timewarp corretamente. O campo não fornece mais comentários enganosos que sugerem que ele abre uma caixa de diálogo. (SITES-25263)
* O rótulo do botão Anotação agora atende aos requisitos mínimos de contraste em seus estados padrão e de focalização. Os usuários podem ler o rótulo claramente contra o fundo do botão. (SITES-25267)
* Os leitores de tela agora anunciam rótulos significativos para controles na caixa de diálogo Anotação. Cada botão comunica sua ação sem um prefixo de Anotação desnecessário. (SITES-25277)
* O botão Editar do painel lateral do Assets agora fornece um destino de toque maior. Os usuários podem ativar o controle de forma mais confiável sem selecionar um elemento próximo. (SITES-25221)
* O Editor de páginas agora usa uma hierarquia de cabeçalho lógica. Os leitores de tela identificam o título da página como o título principal e os títulos do painel lateral como títulos subordinados. (SITES-25222)
* A caixa de diálogo Anotação agora expõe seu título como um cabeçalho semântico. Os usuários de leitores de tela podem identificar o título e navegar pela estrutura da caixa de diálogo por meio de comandos de cabeçalho. (SITES-25248)
* Os usuários de leitores de tela agora recebem feedback ao filtrar a lista Inserir novo componente. O campo de pesquisa descreve seu comportamento de filtragem e uma mensagem de status informa a contagem de resultados. (SITES-25251)
* O painel Componentes do painel lateral agora usa a marcação de lista semântica. Os leitores de tela podem anunciar a contagem de itens e oferecer suporte à navegação eficiente na lista. (SITES-25214)
* Os botões Informações agora usam ícones maiores no painel Componentes. Os usuários podem localizar e reconhecer cada controle com mais facilidade. (SITES-25217)
* Agora os títulos de componentes permanecem visíveis quando os usuários aumentam o espaçamento do texto. Títulos longos quebram automaticamente em vez de truncar ou sobrepor conteúdo próximo. (SITES-25219)
* O botão **Editar** do painel lateral do Assets agora indica que ele abre uma nova guia do navegador. Indicações visuais e de leitores de tela preparam os usuários antes da navegação. (SITES-25220)
* O Modo de anotação agora coloca o foco do teclado na barra de ferramentas de anotação quando ela é aberta. Usuários de teclado e leitor de tela podem se mover pelos controles em uma sequência lógica sem voltar do botão **Fechar**. (SITES-24996)
* Os botões Selecionar para os campos Caminho e Tags não usam mais um ícone de caixa de seleção. O ícone atualizado mostra que o controle abre uma caixa de diálogo de seleção em vez de alterar um estado marcado. (SITES-25210)
* O campo Filtro, no painel Componentes do painel lateral, agora tem um rótulo acessível válido. Os leitores de tela anunciam a finalidade do campo em vez de depender de um ícone ou texto de espaço reservado. (SITES-25212)
* O painel lateral do Assets agora oculta miniaturas decorativas de leitores de tela. Os usuários não ouvem mais o nome do ativo duas vezes ao navegar na grade de ativos. (SITES-25213)
* Os botões de opção no painel Filtros agora exibem indicadores de foco com contraste suficiente. Os usuários do teclado podem rastrear o foco enquanto navegam pelas categorias de filtro. (SITES-24986)
* O painel Filtros agora exibe um foco claro do teclado em torno dos botões de opção. O aumento do contraste ajuda os usuários a rastrear sua posição nas opções de filtro. (SITES-24987)
* O carregamento de mensagens de status na página Filtros agora atende aos requisitos mínimos de contraste de texto. Os usuários podem ler o feedback de progresso ao alternar entre a Exibição de cartão e a Exibição de lista. (SITES-24991)
* O título da página na Tela do editor agora usa a marcação de cabeçalho semântico. A tecnologia assistiva pode anunciar o título e incluí-lo na navegação do cabeçalho. (SITES-24993)
* Expandir o menu Emulador agora move o foco do teclado para o primeiro item de menu. Recolher o menu mantém o foco na sequência lógica da barra de ferramentas secundária. (SITES-24954)
* O texto na tabela de Exibição em tempo real agora atende aos requisitos mínimos de contraste. Os usuários podem ler os detalhes da Live Copy com clareza durante os estados normal e ao passar o mouse. (SITES-24956)
* O painel Referências agora usa a marcação de cabeçalho semântico para seu título. Os leitores de tela anunciam o cabeçalho durante o carregamento inicial e enquanto os usuários navegam pelas pastas. (SITES-24967)
* Os links de cartão agora descrevem claramente seus destinos. Os usuários de leitores de tela podem identificar cada link sem ouvir os metadados completos do cartão. (SITES-24975)
* Os botões do menu de cabeçalho não informam mais aos leitores de tela que eles abrem caixas de diálogo. Em vez disso, os leitores de tela anunciam o estado expandido ou recolhido de cada botão, o que descreve com precisão o comportamento do menu. (SITES-24742)
* O texto do botão Excluir agora oferece contraste suficiente com o plano de fundo vermelho. Os usuários podem identificar a ação mais facilmente antes de confirmar a exclusão. (SITES-24772)
* Os cartões de tela de desenho não expõem mais links de imagem e cabeçalho separados que levam ao mesmo destino. Um único link reduz interrupções duplicadas do teclado e anúncios repetidos do leitor de tela. (SITES-24947)
* A Exibição de lista agora exibe o botão arrastar e soltar com maior destaque visual. O tamanho, o peso e o contraste atualizados dos ícones facilitam a localização e o uso do controle. (SITES-24951)
* Os botões de cabeçalho agora fornecem nomes acessíveis concisos: Pesquisa, Aplicativos, Ajuda, Caixa de entrada e Usuário. Os leitores de tela não anunciam mais termos redundantes, como &quot;clicável&quot; ou &quot;gráfico&quot; durante a navegação pelo teclado. (SITES-24715)
* Os links na Navegação do aplicativo agora exibem maior ênfase visual. O aumento do tamanho e do peso do texto melhora a legibilidade para usuários com pouca visão ou diferenças de visão por cores. (SITES-24723)
* Agora os links da caixa de entrada usam a marcação de lista semântica. Os leitores de tela podem identificar os links como um grupo relacionado, anunciar a contagem de itens e oferecer suporte à navegação mais eficiente. (SITES-24730)
* Os controles de dica de ferramenta na caixa de diálogo Preferências do usuário agora expõem nomes descritivos acessíveis. Os leitores de tela anunciam a finalidade de cada controle em vez de dizer &quot;em branco&quot; antes de ler o conteúdo da dica de ferramenta. (SITES-24732)
* Cada ponto de referência do Trilho de filtro agora inclui um rótulo acessível exclusivo. Os leitores de tela podem distinguir o Painel de filtros de outras regiões da página e identificá-lo durante a navegação. (SITES-24686)
* As caixas de diálogo do editor agora separam os botões Ajuda e Alternar tela cheia do elemento de cabeçalho. Os leitores de tela identificam esses controles interativos com precisão e não os anunciam mais como cabeçalhos. (SITES-24696)
* O botão Relatório de CSV agora avisa os usuários antes de abrir uma nova guia do navegador. Seu rótulo acessível comunica o comportamento aos usuários de leitor de tela e teclado antes da ativação. (SITES-24704)
* O painel Filtro agora carrega os rótulos para Pesquisas salvas e Selecionar diretório de pesquisa de forma consistente. O botão Filters não insere mais elementos de rótulo durante as interações de foco, teclado ou mouse. (SITES-24706)
* Os botões Fechar e Remover localização agora fornecem destinos de toque maiores. Os usuários podem ativar qualquer um dos controles de forma mais confiável sem selecionar elementos adjacentes. (SITES-24530)
* O botão Remover localização e seu indicador de foco agora atendem aos requisitos mínimos de contraste. Um contraste mais forte ajuda os usuários a identificar o controle e rastrear o foco do teclado. (SITES-24531)
* Os iframes do editor agora incluem títulos descritivos na tela, nos painéis laterais, nas caixas de diálogo do componente e na pré-visualização de layout. Os leitores de tela podem identificar cada quadro quando o foco entra nele. (SITES-24650)
* O contraste de texto aprimorado facilita a leitura das mensagens do Painel de referências. A alteração esclarece os prompts que solicitam uma seleção ou relatam referências indisponíveis. (SITES-24666)
* O painel Componentes fornece a cada ícone de informações um rótulo acessível significativo. Os leitores de tela identificam de forma consistente o controle que mostra uma descrição do componente. (SITES-24500)
* O foco do teclado agora envolve todo o botão Mostrar descrição para Subtítulo. O contorno visível ajuda os usuários a rastrear sua posição e evitar a ativação de outro controle. (SITES-24503)
* A caixa de diálogo Componente de teaser não expõe mais os botões Ajuda e Alternar tela cheia como cabeçalhos. Os leitores de tela anunciam ambos os controles como botões e preservam a estrutura de cabeçalho correta. (SITES-24525)
* O controle de cabeçalho do Adobe Experience Manager relata corretamente seu estado expandido ou recolhido. O controle abre e fecha o conteúdo de navegação, de modo que os leitores de tela recebem informações de estado válidas. (SITES-24528)
* Os resultados do filtro marcam ícones de globo como decorativos e removem os nomes acessíveis. Os leitores de tela ignoram os ícones em vez de anunciar descrições enganosas. (SITES-3057)
* A caixa de diálogo Distorção de tempo agora associa erros de entrada de tempo ao campo Horas ou Minutos correspondente. Os leitores de tela anunciam o campo afetado junto com a mensagem de validação. (SITES-10980)
* O item de árvore de conteúdo selecionado não se torna mais parte do rótulo de controle Alterar arquivo ou pasta. Os leitores de tela ouvem um nome de controle claro sem texto de estado extra. (SITES-24496)
* Os pontos de referência de região no painel lateral do Assets agora expõem nomes acessíveis distintos. Os usuários de leitores de tela podem identificar e navegar por cada região sem ambiguidade. (SITES-24497)
* Os leitores de tela agora ignoram os ícones decorativos Ajuda e Tela cheia da caixa de diálogo Carrossel. A navegação pelo teclado não aciona mais anúncios desnecessários de ícones. (SITES-2912)
* Os leitores de tela agora pulam ícones decorativos da barra de ferramentas na caixa de diálogo Teaser. Os controles de Ajuda, Tela cheia, formatação e link não produzem mais anúncios redundantes. (SITES-2934)


#### Interface do usuário administrador{#sites-adminui-65-lts-sp3}

* O AEM agora permite que membros do grupo Admin desbloqueiem páginas e representem usuários. Os membros do grupo podem concluir ambas as tarefas administrativas por meio de seu acesso existente. (SITES-14732)
* A Exibição de administrador do Assets atualiza um cartão de ativos depois que os autores selecionam **Reverter para esta versão** na Linha do tempo. A miniatura exibe a versão restaurada imediatamente e não mostra mais o conteúdo de visualização obsoleto. (SITES-46590)


#### Interface do usuário clássica{#sites-classicui-65-lts-sp3}

As propriedades da Cópia de idioma indonésio exibem o código de idioma de ID correto. O painel Referências não substitui mais EM quando os autores criam ou revisam uma Cópia de idioma indonésia. (SITES-44918)


#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp3}

O console Assets agora responde quando os usuários aplicam filtros de pesquisa. Alterar um filtro do modelo de fragmento de conteúdo atualiza os resultados em vez de deixar a lista de ativos atual inalterada. (SITES-38686) PRINCIPAL


#### [!DNL Content Fragments] — Admin{#sites-admin-65-lts-sp3}

* A página Assets agora localiza a dica de ferramenta de um fragmento de conteúdo bloqueado. Os usuários veem o rótulo **Retirado por** traduzido quando passam o mouse sobre o indicador de bloqueio. (SITES-42531) PRINCIPAL

* O AEM localiza o nome inválido fornecido pela mensagem de validação durante a criação do fragmento de conteúdo. Caracteres de título não suportados não acionam mais texto em inglês em interfaces que não estejam em inglês. (SITES-19796)
* O AEM traduz a cadeia de caracteres de Modelos de fragmento de conteúdo durante a criação do Fragmento de conteúdo. A interface do Assets não mostra mais texto em inglês para esse rótulo em ambientes localizados. (SITES-22336)
* Os serviços de fragmento de conteúdo não dependem mais da lógica obsoleta de alternância de recursos. A implementação simplificada remove ramificações dependentes de alternância e mantém o comportamento do service pack consistente. (SITES-38688)
* O AEM traduz a opção Mais tarde durante a publicação agendada do Fragmento de conteúdo. O fluxo de trabalho de publicação corresponde ao idioma da interface ativa. (SITES-42532)
* O AEM traduz a cadeia de caracteres Principal na caixa de diálogo de download do Fragmento de conteúdo. A seção Elementos corresponde ao idioma da interface ativa. (SITES-42534)


#### [!DNL Content Fragments] - Editor de fragmento{#sites-fragments-editor-65-lts-sp3}

* O Editor de fragmento de conteúdo agora posiciona os menus suspensos do Editor de Rich Text corretamente. Cada menu permanece alinhado com seu controle da barra de ferramentas e mantém visíveis os controles de formatação próximos. (SITES-44005) CRÍTICO

* O botão Editar fragmento de conteúdo agora é exibido e funciona imediatamente para entradas de Vários campos de referência. Os autores não precisam mais salvar, fechar e reabrir o fragmento de conteúdo principal antes de editar um fragmento incorporado. (SITES-43733) PRINCIPAL

* O Editor de fragmento de conteúdo mostra um contorno de foco quando os autores selecionam um campo de texto de várias linhas. O outline não duplica mais ou sobrepõe controles próximos. (SITES-39253)
* A criação de Fragmento do conteúdo exibe o texto do espaço reservado CJK sem estilo em itálico. Caracteres japoneses, coreanos, chineses simplificados e chineses tradicionais mantêm a aparência desejada. (SITES-43548)
* O Editor de fragmento de conteúdo atualiza o banner de status depois que os autores salvam ou publicam um fragmento. Os autores podem confirmar os estados Modificado, Salvo ou Publicado sem recarregar a guia do navegador. (SITES-45897)
* O Editor de fragmento de conteúdo valida campos de forma consistente após as alterações na interface do usuário do Granite. As bibliotecas de clientes atualizadas restauram o comportamento de validação esperado. (SITES-46650)


#### [!DNL Content Fragments] — API GraphQL {#sites-graphql-api-65-lts-sp3}

* As respostas JSON do GraphQL agora incluem referências de imagem incorporada quando nomes de arquivo DAM contêm espaços ou caracteres não ASCII. Os aplicativos clientes podem recuperar e renderizar essas imagens sem renomear os ativos. (SITES-42191) PRINCIPAL
* A API do GraphQL do fragmento de conteúdo agora inclui várias atualizações de processamento de consultas e tratamento de respostas. As alterações evitam cabeçalhos e valores de cache duplicados, melhoram a codificação, preservam informações de status de consultas persistentes, lidam com cabeçalhos vazios e retornam erros de ponto de extremidade apropriados. (SITES-40159) PRINCIPAL
* O PersistedQueryServlet agora processa variáveis codificadas em consultas persistentes válidas do GraphQL sem registrar erros falsos ou avisos. As consultas continuam a retornar respostas bem-sucedidas, enquanto os logs refletem seu status de execução real. (SITES-39354) PRINCIPAL

* Recarregar a página Endpoints do GraphQL preserva a mensagem de estado vazio localizada. A página não reverte mais para inglês quando não existem pontos de extremidade. (SITES-43586)


<!--#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp3}-->


#### [!DNL Content Fragments] — Editor de modelos{#sites-model-editor-65-lts-sp3}

* O console de Modelos de fragmento de conteúdo agora exibe miniaturas carregadas para configurações cujos nomes contêm caracteres localizados. Os autores não perdem mais as visualizações em miniatura quando os nomes de configuração usam texto em outros idiomas. (SITES-39242) PRINCIPAL

* O Editor de Modelos de Fragmentos de Conteúdo exibe o texto **Rótulo de Campo** localizado assim que os autores adicionam um componente à tela. Os autores não precisam mais salvar e reabrir o modelo para ver a tradução. (SITES-45383)
* O Editor de modelos de fragmentos de conteúdo localiza a mensagem de validação mostrada quando os autores selecionam um tipo de modelo inválido para um componente Composto. A mensagem agora corresponde ao local ativo em vez de aparecer somente em inglês. (SITES-41117)
* O Editor de modelos de fragmentos de conteúdo localiza todo o texto na caixa de diálogo O modelo está bloqueado. A caixa de diálogo não mescla mais rótulos e instruções de botão em inglês com texto de interface traduzido. (SITES-28592)



#### [!DNL Content Fragments] — API REST{#sites-restapi-65-lts-sp3}

O pacote de API REST de fragmento de conteúdo headless remove opções de recursos obsoletos e o código condicional relacionado. O comportamento da API compatível permanece inalterado, enquanto o pacote retém apenas os alternadores necessários para os recursos ativos. (SITES-39113)



#### Console de componentes{#sites-component-console-65-lts-sp3}

O Localizador de conteúdo agora lista ativos cujos nomes contêm caracteres não codificáveis sem falha ou sem gerar exceções. A página Uso de componentes em tempo real também carrega grandes conjuntos de resultados continuamente, sem exibir linhas vazias durante a rolagem. (SITES-44672) PRINCIPAL

<!--
#### Content API{#sites-content-api-65-lts-sp3}

#### Core backend{#sites-core-backend-65-lts-sp3}
-->

#### Componentes principais{#sites-core-components-65-lts-sp3}

* Os componentes de vários campos agora armazenam uma seleção de ativo remota separada para cada entrada. Os autores podem selecionar, alterar e salvar imagens remotas sem duplicar uma imagem em cada item de vários campos. (SITES-42376) PRINCIPAL
* ThumbnailServlet agora para de processar depois de redirecionar uma solicitação para um recurso ausente. Essa alteração evita exceções repetidas de ponteiro nulo e registro excessivo de erros durante a navegação no DAM e no console. (SITES-41238) PRINCIPAL


#### Integração do Campaign{#sites-campaign-integration-65-lts-sp3}

O ContentServlet do Campaign agora preserva o tipo de conteúdo de resposta JSON durante solicitações de conteúdo. Essa alteração interrompe as entradas de log `WARN` e `ERROR` repetidas que ocorreram após uma atualização do AEM 6.5.24. (SITES-46902) MAJOR


#### Fragmentos de experiência{#sites-experiencefragments-65-lts-sp3}

Os autores agora podem navegar por mais de 40 modelos ao criar uma variação de Fragmento de experiência. Cada página adicional preserva o filtro de pasta original e exibe os próximos modelos correspondentes. (SITES-41531) PRINCIPAL


<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp3} -->


#### Lançamentos{#sites-launches-65-lts-sp3}

O histórico de promoções de lançamentos agora exibe o texto localizado na Linha do tempo do Sites. A Linha do tempo traduz as mensagens &quot;Versão criada de&quot; e &quot;antes de promover a inicialização&quot; nas localidades compatíveis. (SITES-13389)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp3} -->



#### MSM: Live Copies{#sites-msm-live-copies-65-lts-sp3}

* As pastas de Live Copy do fragmento de conteúdo agora retêm o cq:rolloutConfigs quando os autores salvam propriedades inalteradas. Os autores podem atualizar as configurações de implantação posteriormente sem perder a configuração existente. (SITES-43729) CRÍTICO

* Os autores agora podem implantar alterações de componentes na barra de ferramentas editável em uma página de blueprint. A implantação é concluída sem um erro do JavaScript e propaga as alterações para a Live Copy. (SITES-46052) PRINCIPAL
* Os autores agora podem concluir implantações do MSM a partir de páginas do blueprint após uma atualização. A caixa de diálogo de implantação carrega as Live Copies disponíveis e ativa seus controles de implantação em vez de permanecer em um estado de carregamento permanente. (SITES-43116) PRINCIPAL

* A Visão geral da Live Copy agora aplica formatos de data localizados no Status do relacionamento. Os campos **Última modificação do Source da Live Copy**, **Última modificação da Live Copy** e **Última implantação** correspondem à localidade do usuário. (SITES-40756)
* Desativar um pai de blueprint e suas páginas secundárias em uma solicitação agora produz um evento de implantação por caminho. O gerenciador de implantação não executa mais ações duplicadas para a mesma página secundária. (SITES-44987)


#### Editor de página{#sites-pageeditor-65-lts-sp3}

* Agora, os autores podem criar e aplicar tags com letras maiúsculas ou espaços durante um salvamento de Propriedades da página. O AEM armazena imediatamente o valor da tag normalizada e preserva a atribuição da página. (SITES-42550) CRÍTICO

* A rolagem pelo menu de estilo não remove mais o realce do estilo selecionado. Os autores podem confirmar a seleção atual enquanto revisam outras opções disponíveis. (SITES-30874) PRINCIPAL

* O botão Link do editor de rich text agora é aberto quando os autores acessam o AEM por meio de HTTP. A criação de links não dispara mais um erro `crypto.randomUUID`. (SITES-39467)
* Os autores agora podem copiar e colar componentes configurados do Fragmento de conteúdo em contêineres de layout vazios. O componente colado retém a referência do Fragmento do conteúdo original e não exibe mais o erro *Escolher uma variação de experiência*. (SITES-41586)
* O Editor de imagens agora respeita as taxas de corte personalizadas durante a edição híbrida em linha. Cada destino de soltar imagem usa sua própria configuração, de modo que as seleções de corte se aplicam corretamente fora do modo de tela cheia. (SITES-45771)

<!--
#### Replication{#sites-replication-65-lts-sp3}

#### Rich Text Editor{#sites-rte-65-lts-sp3}

#### Template Editor{#sites-template-editor-65-lts-sp3}

#### Universal editor {#sites-universal-editor-65-lts-sp3}

### [!DNL Assets]{#assets-65-lts-sp3}

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp3}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp3}
-->



<!--
### [!DNL Forms]{#forms-65-lts-sp3}
-->



### Foundation {#foundation-65-lts-sp3}

#### Serviço de contexto do AEM {#foundation-aem-context-service-65-lts-sp3}

O AEM 6.5 LTS apresenta o suporte ao AEM Context Service. A implantação adiciona APIs de serviço, integração de agente, provisionamento do AMS, integração da Experience Cloud, monitoramento de produção, runbooks operacionais e relatórios de uso. (GRANITE-65148)

#### Apache Felix {#foundation-apachefelix-65-lts-sp3}

O serviço de email do AEM agora continua enviando emails quando ocorrem erros intermitentes de configuração. Os administradores não precisam mais reiniciar o pacote Day Communicator 5 Mailer para restaurar a entrega de emails. (GRANITE-66817) PRINCIPAL

<!--
#### Campaign{#foundation-campaign-65-lts-sp3}

#### Cloud Services{#foundation-cloudservices-65-lts-sp3}

#### Communities {#foundation-communities-65-lts-sp3}

#### Content distribution{#foundation-content-distribution-65-lts-sp3}

#### CRX {#foundation-crx-65-lts-sp3}

#### Granite{#foundation-granite-65-lts-sp3}

#### HTL{#foundation-htl-5-lts-sp3}

#### Integrations{#foundation-integrations-65-lts-sp3}

#### Jetty{#foundation-jetty-65-lts-sp3}
-->

#### Localização{#foundation-localization-65-lts-sp3}

* O console Operações agora localiza o texto não traduzido anteriormente nos Relatórios de Integridade. Os usuários veem mensagens de status traduzidas, avisos, resultados de manutenção e informações de desempenho. (NPR-44280) PRINCIPAL

* A tarefa de Manutenção do log de auditoria agora exibe um aviso localizado. Os administradores visualizam a conformidade e as orientações legais no idioma selecionado antes de configurar a limpeza automática do log de auditoria. (NPR-44188)
* A página Editar usuário agora exibe um erro localizado quando os usuários reorganizam os perfis modificados. A mensagem explica claramente que os perfis alterados não podem ser movidos até que os usuários salvem suas alterações. (NPR-44282)
* O AEM agora localiza dicas de ferramentas em todas as propriedades da Lista de fragmentos de conteúdo. As orientações traduzidas explicam a seleção de modelo, a filtragem de tags, os caminhos de conteúdo, os limites de item e as configurações de classificação. (SITES-14969)
* Os links de Ajuda dos componentes no Editor de modelos agora abrem a documentação localizada. Os autores acessam orientações que correspondem ao idioma selecionado em vez de páginas de componentes somente em inglês. (SITES-15058)
* O editor de Política de componentes agora localiza erros que relatam um recurso não modificável ou uma falha na criação de um nó. Os autores de modelo recebem essas mensagens no idioma selecionado. (SITES-17475)

<!-- #### Omnisearch{#foundation-omnisearch-65-lts-sp3} -->

#### Painel de operações{#foundation-operations-dashboard-65-lts-sp3}

O endpoint `/system/health/systemalive.json` agora permanece disponível depois que os clientes atualizam o AEM LTS. Uma configuração de contexto de servlet corrigida impede respostas HTTP 404 e suporta sistemas de monitoramento de integridade que dependem do endpoint. (GRANITE-69457) CRÍTICO

#### Platform{#foundation-platform-65-lts-sp3}

A lista de permissões de opção de expressão HTL padrão agora reconhece `decorationTagName` e `cssClassName`. A renderização da grade responsiva padrão não preenche mais `error.log` com avisos de opção desconhecida repetidos. (GRANITE-67152)

<!--
#### Projects{#foundation-projects-65-lts-sp3}

#### Oak {#foundation-oak-65-lts-sp3}

#### Quickstart{#foundation-quickstart-65-lts-sp3} 
-->


#### Segurança{#foundation-security-65-lts-sp3}

A ação **Copiar Grupo** agora abre o formulário esperado em vez de exibir uma página em branco. Os administradores podem inserir uma nova ID e descrição do grupo e, em seguida, duplicar um grupo de segurança existente. (NPR-44302) PRINCIPAL


<!-- #### Sling{#foundation-sling-65-lts-sp3} -->


#### Tradução{#foundation-translation-65-lts-sp3}

Os projetos de tradução agora mantêm contagens de status precisas à medida que os fluxos de trabalho avançam. A criação de lançamentos e a propagação de status seguem o comportamento do fluxo de trabalho esperado, eliminando metadados inconsistentes do projeto. (NPR-43420)


#### Interface do usuário{#foundation-ui-65-lts-sp3}

* O rótulo País/Região agora aparece no idioma de interface selecionado. As interfaces localizadas não exibem mais o rótulo em inglês. (NPR-43883)
* A seleção de uma página irmã agora ativa **Selecionar** em seletores de caminho de vários campos compostos. Os autores podem confirmar o novo caminho sem aumentar a janela do navegador ou repetir a seleção. (GRANITE-69323)


<!-- #### WCM{#foundation-wcm-65-lts-sp3} -->


#### Fluxo de trabalho{#foundation-workflow-65-lts-sp3}

* As páginas Pacote de fluxo de trabalho agora oferecem suporte aos componentes Árvore de conteúdo e Definição de recurso editável no Editor de páginas da interface para toque. Os autores podem navegar pelo conteúdo do pacote e inspecionar ou atualizar seus componentes sem usar a interface clássica. (GRANITE-67348) MAJOR
* O Editor de página da interface para toque agora renderiza a Árvore de conteúdo para páginas do pacote de fluxo de trabalho. Os autores podem inspecionar a estrutura do pacote e editar os componentes de Definição de recursos por meio do mesmo editor. (GRANITE-67186) MAJOR

* A caixa de diálogo da variável de fluxo de trabalho agora exibe os controles corretos para as variáveis Modelo de dados de formulário, JSON, XML e Documento. Os autores não veem mais a marcação de HTML bruta quando criam essas variáveis não primitivas. (GRANITE-67915)



## Sobre [!DNL Experience Manager Foundation] {#experience-manager-foundation}

A plataforma do [!DNL Adobe Experience Manager] 6.5 LTS baseia-se nas versões atualizadas da estrutura baseada em OSGi (Apache Sling e Apache Felix) e do repositório de conteúdo Java™: Apache Jackrabbit Oak 1.68.x.

O Eclipse Jetty 11.0.x é usado como um mecanismo de servlet para o início rápido.

### Compatibilidade com Java™  {#java-support}

* Compatibilidade com Java™ 17 e Java™ 21.
* Para atingir o desempenho ideal, substitua os valores de GC padrão por outros valores. Para obter mais informações, consulte a seção [instalar e atualizar](/help/sites-deploying/custom-standalone-install.md).
* A Adobe distribui atualizações de manutenção do Java™ 17 e do Java™ 21 para uso dos clientes em projetos relacionados ao AEM, quando não estão disponíveis publicamente na Oracle.

### Empacotamento de Uberjar {#uber-jar-packaging}

O UberJar para AEM 6.5 LTS SP3 usa o AEM 6.5 LTS UberJar versão 6.6.3. Você pode recuperar os artefatos UberJar correspondentes do Repositório central Maven. Ao contrário do AEM 6.5, o AEM 6.5 LTS separa APIs públicas e APIs obsoletas em dois artefatos diferentes.

Para compilar nas APIs públicas, use o seguinte:

    &quot;xml
    &lt;dependency>
    &lt;groupId>com.adobe.aem&lt;/groupId>
    &lt;artifactId>uber-jar&lt;/artifactId>
    &lt;version>6.6.3&lt;/version>
    &lt;classifier>apis&lt;/classifier>
    &lt;scope>fornecido&lt;/scope>
    &lt;/dependency>
    &quot;

Se o código também depender de APIs obsoletas, adicione o seguinte:

    &quot;xml
    &lt;dependência>
    &lt;groupId>com.adobe.aem&lt;/groupId>
    &lt;artifactId>uber-jar&lt;/artifactId>
    &lt;versão>6.6.3&lt;/versão>
    &lt;classifier>apis obsoletas&lt;/classifier>
    &lt;escopo>fornecido&lt;/scope>
    &lt;/dependency>
    &quot;

Veja também [Atualizar a versão do AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Atualizar {#upgrade}

* Para mais detalhes sobre o procedimento de upgrade, consulte a [documentação de upgrade](/help/sites-deploying/upgrade.md).
* Para obter instruções detalhadas de atualização, consulte o [Guia de atualização do AEM Forms 6.5 LTS SP1 no JEE](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

## Práticas recomendadas para as atualizações do Pacote de serviços do AEM 6.5 LTS

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

Aplicável a: clientes do AEM 6.5 LTS (no local) que instalam o Service Pack 3 (SP3). O SP3 é fornecido como um JAR de início rápido.

**Por que essa prática de atualização é importante**
O SP2 para o AEM 6.5 LTS é fornecido como um arquivo JAR do Quickstart, em vez de um ZIP para instalação pelo gerenciador de Pacotes. Os clientes locais atualizam substituindo o Quickstart JAR, desempacotando-o e reiniciando. Este método é consistente com o procedimento de atualização padrão do Adobe.


**Fluxo de atualização recomendado (Autor ou Publicação)**

1. Verifique se a instância AEM 6.5 LTS está íntegra e acessível.
1. Baixe o arquivo JAR do Quickstart (por exemplo, `cq-quickstart-6.6.x.jar`) na seção de distribuição de software.
1. Interrompa a instância de execução.
1. No diretório de instalação do AEM (fora de `crx-quickstart/`), substitua o JAR de início rápido anterior pelo JAR do SP3.
1. Extraia o arquivo JAR:

       &quot;java
     java -jar cq-quickstart-6.6.x.jar -unpack
     &quot;
   
   (Ajuste sinalizadores de heap conforme necessário.)

1. Renomeie o arquivo JAR extraído para corresponder à função e à porta como, por exemplo, `cq-author-4502.jar` ou `cq-publish-4503.jar`.
1. Inicie o AEM e confirme a atualização na interface (Ajuda > Sobre) e nos logs.

**Práticas recomendadas**

* Execute a atualização em ambientes de teste ou inferiores antes de colocá-la em produção.
* Faça um backup completo e restaurável (repositório mais qualquer armazenamento de dados externo) antes de começar.
* Revise a orientação para atualização da Adobe no local e os requisitos técnicos (Java 17/21 recomendado para LTS).

>[!NOTE]
>
>Os nomes de arquivo mostrados acima (por exemplo, `cq-quickstart-6.6.x.jar`) refletem a nomenclatura de artefatos do Quickstart adotada nesta versão LTS; utilize sempre o nome exato do arquivo baixado na distribuição de software.

## Instalar e atualizar{#install-update}

Para conferir os requisitos de instalação, consulte as [instruções de instalação](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Se você estiver atualizando diretamente de SPs antigos do 6.5 para o LTS SP1, siga as instruções fornecidas para a [atualização](/help/sites-deploying/upgrade.md) do 6.5 para o 6.5 LTS GA.


Para obter instruções detalhadas, consulte a [documentação de atualização](/help/sites-deploying/upgrade.md), pois a mesma documentação se aplica às atualizações do LTS Service Pack.

>[!NOTE]
>
> Para novas instalações do AEM 6.5 LTS, as definições de índice precisam ser instaladas separadamente. Para mais informações, consulte [este artigo](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Instalar e atualizar o complemento AEM Forms {#install-update-aem-forms-add-on}

Para instruções detalhadas, consulte [Realizar um upgrade no local](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).


## Plataformas compatíveis {#supported-platforms}

Encontre o conjunto completo de plataformas compatíveis, incluindo em relação ao suporte, nos [requisitos técnicos do AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 são as versões recomendadas para usar com o AEM 6.5 LTS.


## Recursos obsoletos e removidos {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

A Adobe analisa e aprimora continuamente os recursos de seus produtos para oferecer mais valor aos clientes, modernizando ou substituindo recursos legados. Essas alterações são implementadas considerando cuidadosamente a compatibilidade com versões anteriores.

Para garantir a transparência e permitir o planejamento adequado, a Adobe segue esse processo de descontinuação do Adobe Experience Manager (AEM):

* A descontinuação é anunciada primeiro. Os recursos descontinuados continuam disponíveis, mas não são mais aprimorados.
* A remoção não ocorre antes da próxima versão principal. A linha do tempo de remoção planejada é comunicada separadamente.
* É disponibilizado pelo menos um ciclo de lançamento de versão para que os clientes façam a transição para alternativas compatíveis antes da remoção de um recurso.

### Recursos descontinuados {#deprecated-features}

Esta seção lista os recursos e funcionalidades que a Adobe descontinuou no AEM 6.5 LTS. Normalmente, a Adobe descontinua recursos antes de os remover em uma versão futura e fornece uma alternativa.

Os clientes são aconselhados a analisar se usam o recurso/funcionalidade em sua implantação atual. Faça planos para alterar sua implementação para usar a alternativa fornecida.

| Área | Destaque | Substituição | Versão (SP) |
| --- | --- | --- | --- |
| Sites | Resumo do texto do fragmento de conteúdo | Não há nenhuma substituição disponível. | |
| Início rápido | APIs do Mongo | As APIs do Mongo agora estão obsoletas e devem ser removidas em versões futuras. | 6.5 TS SP2 |
| Sites | Suporte a Fragmento de conteúdo na API REST do AEM Assets | O AEM 6.5 LTS SP2 fornece OpenAPIs modernas para gerenciamento de fragmentos de conteúdo e modelos. Portanto, os pontos de acesso mais antigos de suporte a fragmentos de conteúdo na API REST do AEM Assets agora estão obsoletos.<br>A Adobe pretende manter esses pontos de acesso mais antigos disponíveis até que seja feito um anúncio de fim de vida útil. A Adobe não planeja melhorias adicionais para os pontos de acesso obsoletos. | 6.5 LTS SP2 |
| Sites | [Editor SPA](/help/sites-developing/spa-overview.md) | Os editores recomendados para gerenciar conteúdo headless no AEM são:<br>- [O Editor Universal](/help/sites-developing/universal-editor/introduction.md) para edição visual.<br>- [O Editor de Fragmentos de Conteúdo](/help/assets/content-fragments/content-fragments-managing.md) para edição baseada em formulários. | 6.5 LTS GA |
| [!DNL Foundation] | Suporte para com.adobe.granite.oauth.server | Integração do Adobe IMS | |

### Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades que foram removidas do AEM 6.5 LTS. Nas versões anteriores, esses recursos estavam marcados como descontinuados.

* O suporte para RDBMK para persistência de repositório do Adobe CRX foi removido.
* Em ambientes agrupados, o MongoMK agora é a única opção compatível de persistência do repositório.

| Área | Destaque | Substituição | Versão (SP) |
| --- | --- | --- | --- |
| Commerce | O AEM CIF Classic não é compatível. | Migre para o [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Soluções | Social/Communities não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Screens | Telas não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Ativos | `dam-pim` e `dam-rating` não são compatíveis, pois esses pacotes dependem de redes sociais. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Ativos | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` foi removido. | Use a API alternativa `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` que foi adicionada. | 6.5 LTS GA |
| Portal | O AEM Portal Diretor não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | O pacote `com.adobe.granite.socketio` foi removido. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | `crx2oak` não é compatível. | Escolha a versão apropriada de [Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Guava | Todas as dependências do Guava foram removidas do AEM; portanto, o pacote `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` não faz parte do AEM. | Os clientes podem adicionar o Guava por conta própria se dependerem dele ou substituir o código do Guava por coleções de Java ou outras alternativas, se possível. | 6.5 LTS GA |
| `We.Retail` | O site de exemplo `We-retail` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | O pacote `oak-solr-osgi` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` e `org.apache.sling.atom.taglib` não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `org.apache.commons.io` foram exportados de `org.apache.commons.commons-io`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `javax.mail` estão sendo exportados do pacote `com.sun.javax.mail`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `org.apache.jackrabbit.api` agora são exportados do pacote `org.apache.jackrabbit.oak-jackrabbit-api`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | `com.github.jknack.handlebars` não é compatível. | Escolha a [versão](https://mvnrepository.com/artifact/com.github.jknack/handlebars) adequada | 6.5 LTS GA |

## Problemas conhecidos {#known-issues}

### AEM Forms

* No Configuration Manager, a inicialização do banco de dados falha durante o bootstrap no AEM Forms 6.5 LTS JEE Turnkey no modo personalizado quando nenhum módulo ou apenas componentes limitados são selecionados. A falha se deve a uma dependência ausente (xalan-2.7.2.jar), resultando em um erro. Adicionar o arquivo JAR ao Adobe-livecycle-jboss.ear\lib resolve o problema. (FORMS-24690)
* Em implantações do Forms JEE LTS Service Pack 2 em execução no WebSphere® Liberty Profile, a funcionalidade de email falha. Ao tentar usar recursos de email, o servidor registra um erro: `Could not convert socket to TLS`. (FORMS-24692)
* No Forms JEE LTS em execução no JBoss®, a funcionalidade relacionada ao email falha. Ao tentar usar recursos de email, o servidor registra um erro: `Error IMAPProvider not a subtype`. Para resolver esse problema, instale o hotfix de [Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-core-jboss.ear). (FORMS-24892)

### Corrupção do repositório durante a compactação online após a compactação offline (GRANITE-65146) {#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146}

Os usuários podem enfrentar corrupção do repositório durante a compactação online se a compactação offline tiver sido executada anteriormente no repositório JCR. Um `SegmentNotFoundException` (SNFE) pode ocorrer neste cenário e pode levar à corrupção do repositório.

Para resolver o problema, instale o Hotfix de [Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-65388-1.0.zip). Como o hotfix inclui um pacote de baixo nível `oak-segment-tar`, a instância é reiniciada após a instalação.

Planeje o tempo de inatividade da instância ao aplicá-la. Para compactação offline, use o [`oak-run` jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar) correspondente, também disponível na Distribuição de Software.

>[!NOTE]
>
> * Para qualquer operação `oak-run`, use o [`oak-run` 1.88.1-B006 jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar).
>
> * Inicie o AEM definindo a propriedade do sistema `oak.compaction.legacy=true`.

### Pacote `com.adobe.granite.apicontroller` ausente no AEM 6.5 LTS SP2 (GRANITE-67640) {#missing-apicontroller-bundle-granite-67640}

O pacote `com.adobe.granite.apicontroller` está ausente no AEM 6.5 LTS SP2. Esse pacote controla como os pacotes OSGi são resolvidos e pode impedir que os pacotes sejam resolvidos para outros pacotes, o que é útil para limitar as APIs expostas.

Para usar esta funcionalidade, instale o hotfix de [Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-67640-1.0.zip).

>[!NOTE]
>
> Para garantir que a configuração padrão do `com.adobe.granite.apicontroller` não introduza restrições de resolução não intencionais que afetem implementações personalizadas existentes, verifique o status do pacote de todos os pacotes instalados após a instalação do hotfix.

### Comentários JSON não são mais compatíveis com Sling-Initial-Content (SP2) {#json-comments-no-longer-supported-in-sling-initial-content}

Esse problema afeta os desenvolvedores e administradores de pacotes OSGi que implantam pacotes que usam `Sling-Initial-Content` com arquivos JSON.

A partir do AEM 6.5 LTS SP2, os arquivos JSON usados em pacotes `Sling-Initial-Content` não aceitam mais comentários (`//` ou `/* */`). As versões anteriores do AEM aceitaram comentários porque o provedor `javax.json` foi tolerante com relação a isso. O AEM 6.5 LTS SP2 atualizou o `org.apache.sling.jcr.contentloader` para a versão 2.6.0, que alterou o analisador JSON para `jakarta.json`. Embora a [especificação JSON (RFC 8259)](https://datatracker.ietf.org/doc/html/rfc8259) não defina a sintaxe para comentários, versões anteriores do AEM as aceitaram devido à tolerância do provedor `javax.json`. O provedor `jakarta.json` não oferece essa extensão.

A falha é silenciosa: os nós de conteúdo não são carregados na ativação do pacote sem erros exibidos no instalador. Se o conteúdo estiver ausente inesperadamente após a atualização para o SP2, verifique se há erros de análise JSON nos logs do instalador OSGi. Para identificar os pacotes afetados, pesquise por `//` ou `/* */` dentro dos arquivos JSON listados nos cabeçalhos de manifesto `Sling-Initial-Content`.

>[!CAUTION]
>
> Para evitar falhas de carregamento de conteúdo após a atualização para o AEM 6.5 LTS SP2, remova todos os comentários dos arquivos JSON em seus pacotes `Sling-Initial-Content`.

### A atualização do pacote Jackson afeta o conector GlobalLink {#jackson-upgrade-globallink-connector}

O AEM 6.5 LTS SP3 atualiza o pacote `jackson`. Essa alteração afeta implantações que usam o conector de tradução GlobalLink.

Se você usar o pacote `gs4tr-globallink-adaptors-aem.core` em uma versão anterior à 3.4.0, atualize o pacote para uma versão compatível. A versão 3.4.0 ou posterior funciona com o pacote `jackson` atualizado no SP3.

>[!NOTE]
>
> Atualize o pacote `gs4tr-globallink-adaptors-aem.core` para a versão 3.4.0 ou posterior, antes ou durante a atualização do SP3, para evitar problemas de compatibilidade com o conector GlobalLink.


### Instale os índices Oak necessários para as APIs do Sites Headless{#site-headless-api}

Algumas APIs que foram movidas para o Sites Headless exigem índices Oak adicionais para funcionalidade completa.

Para usar os seguintes recursos, instale o pacote `cq-dam-cfm-indices`:

* Lista de modelos de fragmentos de conteúdo
* Lista de fragmentos de conteúdo
* API de pesquisa
* Fluxos de trabalhos

Baixe o pacote de índice [cq-dam-cfm-indices](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fcq-dam-cfm-indices-1.1.5.zip) do Portal de Distribuição de Software da Adobe.

### Falha de conexão do Dispatcher com o recurso somente SSL (corrigido no AEM 6.5 LTS SP1 e posterior){#ssl-only-feature}

>[!NOTE]
>
> Esse problema está presente apenas na versão GA do AEM 6.5 LTS.

Ao habilitar o recurso de somente SSL em implantações do AEM, há um problema conhecido que afeta a conectividade entre as instâncias do Dispatcher e do AEM. Após ativar esse recurso, as verificações de integridade falham e a comunicação entre as instâncias do Dispatcher e do AEM é interrompida. Este problema ocorre especificamente quando os clientes tentam se conectar a instâncias do AEM por meio do `https + IP` a partir do Dispatcher. Ele está relacionado a problemas de validação da indicação do nome do servidor (SNI, na sigla em inglês).

**Impacto**

* Falhas de verificação da integridade com códigos de resposta HTTP 400.
* Tráfego interrompido entre as instâncias do Dispatcher e do AEM.
* O conteúdo não pode ser distribuído corretamente por meio do Dispatcher.
* Falhas de conexão ao usar HTTPS com endereços IP na configuração do Dispatcher.
* Erros HTTP 400 “SNI inválida” ao conectar-se via HTTPS + IP.

**Ambientes afetados**

* Implantações do AEM com configurações do Dispatcher.
* Sistemas em que o recurso de somente SSL foi habilitado.
* Configurações do Dispatcher, usando-se o método de conexão `https + IP` com instâncias do AEM.

**Solução**

Se você enfrentar esse problema, entre em contato com o Suporte ao cliente da Adobe. Uma hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) está disponível para resolver esse problema. Não tente habilitar recursos de somente SSL até aplicar a hotfix necessária.

## Pacotes da OSGi e pacotes de conteúdo inclusos{#osgi-bundles-and-content-packages-included}

Os seguintes arquivos zip contêm os documentos de texto que listam os pacotes OSGi e os pacotes de conteúdo incluídos nesta versão do Experience Manager 6.5 LTS Service Pack:

* [Pacotes OSGi](/help/release-notes/assets/65lts_sp3_bundles.zip)
* [Pacotes de conteúdo](/help/release-notes/assets/65lts_sp3_packages.zip)

## Sites restritos{#restricted-sites}

Estes sites só estão disponíveis para clientes. Se você for cliente e precisar de acesso, entre em contato com o seu gerente de conta da Adobe.

* [Download do produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Fale com o suporte ao cliente da Adobe](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).

