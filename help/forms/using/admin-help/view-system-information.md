---
title: Exibir informações do sistema
description: Saiba como visualizar gráficos de monitoramento de recursos e informações sobre o servidor que está executando formulários do AEM.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 6be4ce1d-39fe-4a25-9d4e-f1cbc593d2c7
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Exibir informações do sistema {#view-system-information}

A guia Sistema exibe gráficos de monitoramento de recursos e informações sobre o servidor que está executando formulários do AEM. Para acessar essas informações, no console de administração, clique em Monitor de integridade no canto superior direito da página. Se você estiver executando formulários do AEM em um ambiente clusterizado, as informações exibidas serão para o nó selecionado na lista Servidor.

Para salvar as informações atuais do sistema como um arquivo de propriedades, clique em Salvar.

O painel direito da guia Sistema exibe representações gráficas das seguintes informações:

* Itens de Trabalho e Contagem de Trabalho
* Uso de Heap e Heap Comprometido
* Uso de Não-heap e Não-heap Confirmado

Você pode arrastar seu ponteiro ao longo da linha do tempo para obter valores para um determinado momento.

>[!NOTE]
>
>Os dados do gráfico, os valores das informações do servidor e a hora do relógio são atualizados a cada 10 minutos. As informações não são exibidas em tempo real.

O painel esquerdo da guia Sistema exibe as seguintes informações sobre o servidor ou nó:

**Máquina Virtual:** versão da Java Virtual Machine (JVM) no servidor.

**Fornecedor da Máquina Virtual:** Fabricante da JVM.

**Versão da Máquina Virtual:** número da versão da JVM

**Nome do Computador:** Nome do host do servidor onde o AEM Forms está instalado.

**Horário de funcionamento:** o horário, em horas e minutos, em que o servidor esteve em execução.

**Compilador Just-In-Time:** O nome do compilador que está sendo usado.

**Tempo de Compilação:** a quantidade de tempo gasto na compilação.

**Número de Threads Ativos:** O número total de threads presentes atualmente no sistema de formulários do AEM.

**Número de Pico do Threads:** Maior número de threads ativos já registrados no sistema.

**Número de Classes Carregadas:** Número de classes Carregadas na JVM.

**Número de Classes Descarregadas:** Número de classes Descarregadas da JVM.

**Heap mínimo:** a quantidade mínima de heap que foi usada.

**Heap máximo:** a quantidade máxima de heap que foi usada.

**Nome do Sistema Operacional:** O nome do sistema operacional em execução no AEM Forms Server.

**Versão do Sistema Operacional:** Número da versão do sistema operacional em execução no AEM Forms Server.

**Arco do Sistema Operacional:** A arquitetura do sistema operacional em que o JVM está sendo executado.

**Número de Processadores:** O número de processadores no sistema.

**Argumentos da Máquina Virtual:** o argumento usado pela JVM.

**Caminho da classe:** o caminho da classe usado pela JVM.

**Caminho da biblioteca:** o caminho da biblioteca usado pela JVM.

**Caminho da Classe de Inicialização:** O caminho da classe de inicialização usado pela JVM.

**Tipo de Servidor de Aplicativos:** Tipo de servidor de aplicativos usado para executar formulários do AEM.

**Versão do Servidor de Aplicativos:** Número da versão do servidor de aplicativos usada para executar formulários do AEM.

**Fornecedor do Servidor de Aplicativos:** Fabricante do servidor de aplicativos usado para executar formulários do AEM.

**Data de Instalação:** Data (no formato aaaa-mm-dd) em que o AEM Forms foi instalado.

**Versão do AEM Forms:** Versão do AEM Forms instalada.

**Versão do Patch:** número do patch dos formulários AEM.

**Nome do Banco de Dados:** Tipo de banco de dados usado pelos formulários do AEM.

**Versão do Banco de Dados:** Número da versão do banco de dados usada pelos formulários do AEM.

**Nome da Unidade do Banco de Dados:** O nome do driver usado pelo JVM para conexão com o banco de dados.

**Versão do Driver do Banco de Dados:** A versão do driver usada pelo JVM para se conectar ao banco de dados.

O botão **Salvar** permite salvar essas informações do sistema em um arquivo de propriedade.
