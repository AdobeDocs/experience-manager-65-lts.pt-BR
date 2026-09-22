---
title: O AEM Forms bloqueia solicitações HTTP válidas
description: As verificações de validação XSS do AEM Forms podem bloquear solicitações HTTP válidas para clientes que usam componentes personalizados. Saiba como identificar o problema e reduzir temporariamente as verificações de validação.
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin,Developer
exl-id: 10a02e57-7ff8-42d8-b31e-f714c0dd8338
source-git-commit: 4df5a9888532afd86562678a76c35841ac5634b8
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 2%
---
# O AEM Forms bloqueia solicitações HTTP válidas {#aem-forms-blocks-valid-http-requests}

## Problema {#issue}

O AEM Forms inclui verificações de segurança para impedir ataques de script entre sites (XSS). Essas verificações podem bloquear algumas solicitações HTTP válidas para clientes que usam componentes personalizados no AEM Forms. Quando uma solicitação é bloqueada, a seguinte mensagem é exibida nos registros do servidor:

```text
Got Exception while Validating XSS: HTTP parameter name: params[browserLocale]: Invalid input. Please conform to regex ^[a-zA-Z0-9_]{1,32}$ with a maximum length of 2000: org.owasp.esapi.errors.ValidationException: HTTP parameter name: params[browserLocale]: Invalid input. Please conform to regex ^[a-zA-Z0-9_]{1,32}$ with a maximum length of 2000.
```

>[!NOTE]
>
>Para uma solicitação POST, o valor padrão do parâmetro é **1048576**. Para uma solicitação GET, o valor padrão do parâmetro é **2000**. Para modificar o valor do parâmetro para uma solicitação POST, passe o argumento `com.adobe.idp.dsc.provider.rest.httpParamMaxSize` durante a inicialização do servidor.

## Causa {#cause}

O regex de validação XSS é mais rigoroso que o formato do valor do parâmetro enviado pelo componente personalizado, portanto, o AEM Forms rejeita a solicitação.

## Resolução {#resolution}

>[!CAUTION]
>
>A remoção das verificações de segurança torna o sistema vulnerável a ataques de criação de script entre sites (XSS). Remova as verificações de segurança somente como uma solução temporária.

Para remover temporariamente as verificações de segurança e permitir todas as solicitações HTTP:

1. Pare o servidor do AEM Forms.

1. Crie um backup do arquivo `[AEM-Forms-Installation-Directory]/configurationManager/export/adobe-livecycle-<application_server_name>.ear`.

1. Extrair o arquivo `esapi-helper-2.x.x.jar` do arquivo `adobe-livecycle-<server_name>.ear`. O local do arquivo `esapi-helper-2.x.x.jar` difere para cada servidor de aplicativos:

   | Servidor de aplicativos | Localização do arquivo esapi-helper-2.x.x.jar |
   | --- | --- |
   | JBoss | `adobe-livecycle-jboss.ear/lib` |
   | Oracle WebLogic | `adobe-livecycle-weblogic.ear/APP-INF/lib` |
   | IBM WebSphere | `adobe-livecycle-websphere.ear/` |

1. Abra os arquivos `[extracted esapi-helper-2.x.x.jar]/esapi/validation.properties` e `[extracted esapi-helper-2.x.x.jar]/esapi/ESAPI.properties` para edição.

1. Defina o valor das seguintes propriedades como `^[\\s\\S]*$`. Por exemplo, `Validator.HTTPParameterName=^[\\s\\S]*$`. Salve e feche os arquivos.

   * `Validator.HTTPQueryString`
   * `Validator.PMCallParameterName`
   * `Validator.PMCallParameterValue`
   * `Validator.HTTPParameterName`
   * `Validator.HTTPParameterValue`
   * `Validator.xssSafeString`

1. Empacotar o `esapi-helper-2.x.x.jar` atualizado em `adobe-livecycle-<application_server_name>.ear`. Implante o `adobe-livecycle-<application_server_name>.ear` atualizado no servidor de aplicativos.

1. Inicie o servidor do AEM Forms.

## Referência {#references}

* [Reduzindo vulnerabilidades de SSRF (Server-Side Request Forgery) para AEM Forms no JEE 6.5 LTS SP2](/help/forms/troubleshooting/mitigating-server-side-request-forgery-vulnerabilities-for-aem-forms-on-jee-65-lts-sp2.md)
