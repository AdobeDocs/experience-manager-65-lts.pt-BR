---
title: Quais ambientes de teste são necessários?
description: Vários ambientes devem ser considerados como parte do teste
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Quais ambientes de teste são necessários?{#which-test-environments-will-be-needed}

Para definir quais configurações para teste, você deve considerar o seguinte:

**Desenvolvimento** - Para a Unidade e determinados testes de Integração.

**Testando** - Para a maioria dos testes.

**Ao vivo** - Para desempenho final e testes de stress. Também para testes de aceitação com o cliente.

Decida quais instâncias são necessárias e onde (geralmente, pelo menos uma de cada para todos os níveis de teste):

**Autor** - Esta instância permite que os autores insiram e publiquem conteúdo.

**Publicar** - Esta instância apresenta o site em seu formulário publicado para acesso dos visitantes.

Testado com a Dispatcher.

Por fim, o hardware real deve ser considerado - todos os testes de desempenho devem ser feitos em um sistema com a configuração o mais próxima possível do ambiente ativo final. Por esse motivo, também é recomendável que o Lançamento do projeto seja dividido em:

**Soft Launch** - disponibilidade reduzida; o que permite tempo para testes de desempenho, ajuste e otimização em condições realistas no ambiente de produção.

**Inicialização rígida** - Disponibilidade total.
