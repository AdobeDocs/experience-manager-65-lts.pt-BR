---
title: Segurança
description: A segurança de aplicativos começa durante a fase de desenvolvimento
solution: Experience Manager, Experience Manager Sites
feature: Developing,Security
role: Developer
exl-id: abc2747f-cfd8-4ee1-bbc0-5ad89beb383a
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Segurança{#security}

A Segurança de aplicativos é iniciada durante a fase de desenvolvimento. A Adobe recomenda aplicar as seguintes práticas recomendadas de segurança.

## Usar sessão de solicitação {#use-request-session}

Seguindo o princípio de privilégio mínimo, a Adobe recomenda que todo acesso ao repositório seja feito usando a sessão vinculada à solicitação do usuário e o controle de acesso adequado.

## Proteger contra Criação de script entre sites (XSS) {#protect-against-cross-site-scripting-xss}

A criação de script entre sites (XSS) permite que invasores injetem código em páginas da Web visualizadas por outros usuários. Essa vulnerabilidade de segurança pode ser explorada por usuários mal-intencionados da Web para ignorar controles de acesso.

O AEM aplica o princípio de filtrar todo o conteúdo fornecido pelo usuário na saída. É dada a maior prioridade à prevenção de XSS durante o desenvolvimento e o teste.

O mecanismo de proteção XSS fornecido pelo AEM é baseado na [Biblioteca Java™ AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) fornecida pelo [OWASP (O Projeto de Segurança de Aplicativos Web Abertos)](https://owasp.org/). A configuração padrão do AntiSamy pode ser encontrada em

`/libs/cq/xssprotection/config.xml`

É importante adaptar essa configuração às suas necessidades de segurança, sobrepondo o arquivo de configuração. A [documentação oficial do AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) fornece todas as informações necessárias para implementar seus requisitos de segurança.

>[!NOTE]
>
>A Adobe recomenda que você sempre acesse a API de proteção XSS usando o [XSSAPI fornecido pelo AEM](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/xss/XSSAPI.html).

Além disso, um firewall de aplicativo da Web, como o [mod_security para Apache](https://www.modsecurity.org), pode fornecer controle central e confiável sobre a segurança do ambiente de implantação e proteger contra ataques de script entre sites não detectados anteriormente.

## Acesso às informações do Cloud Service {#access-to-cloud-service-information}

>[!NOTE]
>
>As ACLs para as Informações do Cloud Service e as configurações de OSGi necessárias para proteger sua instância são automatizadas como parte do [Modo Pronto para Produção](/help/sites-administering/production-ready.md). Embora isso signifique que não é necessário alterar a configuração manualmente, ainda é recomendável revisá-los antes de entrar em funcionamento com a implantação.

Ao [integrar sua instância do AEM com o Adobe Experience Cloud](/help/sites-administering/marketing-cloud.md), você usa [configurações do Cloud Service](/help/sites-developing/extending-cloud-config.md). As informações sobre essas configurações, juntamente com quaisquer estatísticas coletadas, são armazenadas no repositório. A Adobe recomenda que, se estiver usando essa funcionalidade, você verifique se a segurança padrão nessas informações corresponde aos seus requisitos.

O módulo webservicesupport grava estatísticas e informações de configuração em:

`/etc/cloudservices`

Com as permissões padrão:

* Ambiente de autor: `read` para `contributors`

* Ambiente de publicação: `read` para `everyone`

## Proteger contra ataques de falsificação de solicitação entre sites {#protect-against-cross-site-request-forgery-attacks}

Para obter mais informações sobre os mecanismos de segurança que a AEM emprega para mitigar ataques CSRF, consulte a seção [Filtro de referenciador Sling](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) da Lista de verificação de segurança e a [documentação da Estrutura de proteção CSRF](/help/sites-developing/csrf-protection.md).
