---
title: Verificações pós-atualização e solução de problemas
description: Saiba como solucionar problemas que podem ocorrer após uma atualização.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 09b297721b08ef428f1ac8a26fec38d5a8bd34fd
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# Verificações pós-atualização e solução de problemas{#post-upgrade-checks-and-troubleshooting}

## Verificações pós-atualização {#post-upgrade-checks}

Após a [Atualização no Local](/help/sites-deploying/in-place-upgrade.md), as atividades a seguir devem ser executadas para finalizar a atualização. Pressupõe-se que o AEM tenha sido iniciado com o jar LTS do AEM 6.5 e que a base de código atualizada tenha sido implantada.

* [Verificar logs para o sucesso da atualização](#verify-logs-for-upgrade-success)

* [Verificar pacotes OSGi](#verify-osgi-bundles)

* [Verificar versão do Oak](#verify-oak-version)

* [Validação inicial das páginas](#initial-validation-of-pages)

* [Verificar configurações de manutenção programada](#verify-scheduled-maintenance-configurations)

* [Habilitar agentes de replicação](#enable-replication-agents)

* [Habilitar os trabalhos agendados personalizados](#enable-custom-scheduled-jobs)

* [Executar plano de teste](#execute-test-plan)


### Verificar logs para Êxito na Atualização {#verify-logs-for-upgrade-success}

**atualizar.log**

Anteriormente, a inspeção do estado pós-atualização da instância exigia uma inspeção cuidadosa de vários arquivos de log, partes do repositório e a barra inicial. Gerar um relatório pós-atualização pode ajudar a detectar atualizações com defeito antes de entrar em funcionamento.

O principal objetivo desse recurso é reduzir a necessidade de interpretação manual ou lógica de análise complexa entre vários endpoints necessários para qualificar o sucesso de uma atualização. A solução tem como objetivo fornecer informações inequívocas para que os sistemas de automação externos reajam ao sucesso ou à falha identificada de uma atualização.

Mais especificamente, garante que:

* As falhas de atualização detectadas pela estrutura de atualização são centralizadas em um único relatório de atualização.
* O relatório de atualização inclui indicadores sobre a intervenção manual necessária.

Para acomodar isso, foram feitas alterações na maneira como os logs são gerados no arquivo `upgrade.log`.

**log.erro**

O error.log deve ser cuidadosamente revisado durante e após a inicialização do AEM usando o jar da versão de destino. Quaisquer avisos ou erros devem ser revisados. Em geral, é melhor procurar problemas no início do log. Os erros que ocorrem posteriormente no log podem ser, na verdade, efeitos colaterais de uma causa raiz que é chamada no início do arquivo. Se ocorrerem erros e avisos repetidos, consulte abaixo para [Analisar problemas com a Atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade).

### Verificar pacotes OSGi {#verify-osgi-bundles}

Navegue até o console OSGi `/system/console/bundles` e verifique se algum pacote não foi iniciado. Se algum pacote estiver em um estado instalado, consulte `error.log` para determinar o problema raiz.

### Verificar versão do Oak {#verify-oak-version}

Após a atualização, você deverá ver que a versão do Oak foi atualizada para **1.68.1-B002**. Para verificar a versão do Oak, navegue até o console OSGi e verifique a versão associada aos pacotes do Oak: Oak Core, Oak Commons, Oak Segment Tar.

### Validação inicial das páginas {#initial-validation-of-pages}

Executar uma validação inicial em várias páginas do AEM. Se estiver atualizando um ambiente de Autor, abra a página Inicial e a página de Boas-vindas ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). Nos ambientes Autor e Publicação, abra algumas páginas de aplicativo e teste de fumaça que eles renderizam corretamente. Se algum problema ocorrer, consulte `error.log` para solucionar.

### Verificar configurações de manutenção programada {#verify-scheduled-maintenance-configurations}

#### Habilitar coleta de lixo do armazenamento de dados {#enable-data-store-garbage-collection}

Se estiver usando um Armazenamento de dados de arquivo, verifique se a tarefa Coleta de lixo do armazenamento de dados está ativada e adicionada à lista de Manutenção semanal. As instruções estão descritas em [Limpeza de revisão](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Isso não é recomendado para instalações de armazenamento de dados personalizado S3 ou ao usar um armazenamento de dados compartilhado.

#### Ativar limpeza de revisão online {#enable-online-revision-cleanup}

Se estiver usando MongoMK ou o novo formato de segmento TarMK, verifique se a tarefa Revision Clean Up está ativada e adicionada à lista Daily Maintenance (Manutenção diária). As instruções estão descritas em [Limpeza de revisão](/help/sites-deploying/revision-cleanup.md).

### Habilitar agentes de replicação {#enable-replication-agents}

Depois que o ambiente de publicação for totalmente atualizado e validado, ative os agentes de replicação no Ambiente de autor. Verifique se os agentes podem se conectar às respectivas instâncias de Publicação. Consulte [Atualizar Procedimento](/help/sites-deploying/upgrade-procedure.md) para obter mais detalhes sobre a ordem dos eventos.

### Habilitar os trabalhos agendados personalizados {#enable-custom-scheduled-jobs}

Todos os trabalhos agendados como parte da base de código podem ser ativados neste ponto.

### Executar plano de teste {#execute-test-plan}

Execute o plano de teste detalhado conforme definido em [Atualizando Código e Personalizações na **seção Procedimento de Teste**](/help/sites-deploying/upgrading-code-and-customizations.md#testing-procedure-testing-procedure).

## Análise De Problemas Com A Atualização {#analyzing-issues-with-the-upgrade}

Esta seção contém alguns cenários de problemas que podem ocorrer durante o procedimento de atualização para o AEM 6.5 LTS.

### Falha ao atualizar pacotes e pacotes  {#packages-and-bundles-fail-to-update}

Se os pacotes não forem instalados durante a atualização, os pacotes que eles contêm também não serão atualizados. Essa categoria de problemas é causada por uma configuração incorreta do armazenamento de dados. Eles também aparecerão como mensagens de **ERRO** e **AVISO** no error.log. Como na maioria desses casos o logon padrão pode falhar, você pode usar o CRXDE diretamente para inspecionar e encontrar os problemas de configuração.

### A Atualização Não Foi Executada {#the-upgrade-did-not-run}

Antes de iniciar as etapas de preparação, execute primeiro a instância de **origem** com o comando `java -jar aem-quickstart.jar`. Isso é necessário para garantir que o arquivo quickstart.properties seja gerado corretamente. Se estiver ausente, a atualização não funcionará. Como alternativa, você pode verificar se o arquivo está presente procurando em `crx-quickstart/conf` na pasta de instalação da instância de origem. Além disso, ao iniciar o AEM para iniciar a atualização, ele deve ser executado com o comando `java -jar <aem-quickstart-6.5-LTS.jar>`. A inicialização a partir de um script de inicialização não iniciará o AEM no modo de atualização.

### Alguns pacotes do AEM não estão alternando para o estado ativo {#some-aem-bundles-are-not-switching-to-the-active-state}

Se houver pacotes não inicializando, verifique se há dependências não satisfeitas.

Caso esse problema esteja presente, mas se baseie em uma instalação de pacote com falha que resultou na não atualização de pacotes, eles serão considerados incompatíveis para a nova versão. Para obter mais informações sobre como solucionar problemas, consulte **Falha ao atualizar pacotes e pacotes** acima.

Também é recomendável comparar a lista de pacotes de uma nova instância AEM 6.5 LTS com a atualizada para detectar os pacotes que não foram atualizados. Isso fornecerá um escopo mais próximo do que procurar no `error.log`.

### Pacotes personalizados não estão alternando para o estado ativo {#custom-bundles-not-switching-to-the-active-state}

Caso seus pacotes personalizados não estejam alternando para o estado ativo, é provável que haja um código que não esteja importando a API alterada. Isso levará, na maioria das vezes, a dependências insatisfeitas.

Também é melhor verificar se a alteração que causou o problema foi necessária e reverter se não for. Verifique também se o aumento da versão da exportação de pacotes foi aumentado mais do que o necessário, após o controle de versão semântico rigoroso.

### Analisando error.log e upgrade.log {#analyzing-the-error.log-and-upgrade.log}

Na maioria das situações, os registros precisam ser consultados para que os erros localizem a causa de um problema. No entanto, com as atualizações, também é necessário monitorar problemas de dependência, pois os pacotes antigos podem não ser atualizados corretamente.

A melhor maneira de fazer isso é remover o error.log, removendo todas as mensagens que provavelmente não estão relacionadas ao problema que você está enfrentando. Você pode fazer isso por meio de uma ferramenta como o grep, usando:

```shell
grep -v UnrelatedErrorString
```

Algumas mensagens de erro podem não ser explicativas imediatamente. Nesse caso, observar o contexto em que eles ocorrem também pode ajudar a entender onde o erro foi criado. É possível separar o erro usando:

* `grep -B` para adicionar linhas antes do erro;

ou

* `grep -A` para adicionar linhas após.

Em alguns casos, mensagens de AVISO também podem ser encontradas, pois pode haver casos válidos que levam a esse estado e o aplicativo nem sempre pode decidir se esse é um erro real. Consulte também estas mensagens.

### Contato com o suporte da Adobe {#contacting-adobe-support}

Se você tiver seguido as instruções nesta página e ainda estiver vendo problemas, entre em contato com o Suporte da Adobe. Para fornecer o máximo possível de informações ao engenheiro de suporte que trabalha no seu caso, inclua os arquivos `error.log` e `upgrade.log` da sua atualização.
