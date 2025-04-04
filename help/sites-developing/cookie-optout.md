---
title: Configuração do uso de cookies
description: O AEM fornece um serviço que permite configurar e controlar como os cookies são usados com suas páginas da Web.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---

# Configuração do uso de cookies{#configuring-cookie-usage}

O AEM fornece um serviço que permite configurar e controlar como os cookies são usados com suas páginas da Web:

* Um serviço configurável do lado do servidor mantém uma lista de cookies que podem ser usados.
* Uma API do JavaScript permite que o código JavaScript verifique se um cookie pode ser usado.

Use este recurso para garantir que suas páginas estejam em conformidade com o consentimento dos usuários em relação ao uso de cookies.

## Configuração de cookies permitidos {#configuring-allowed-cookies}

Configure o serviço de cancelamento do Adobe Granite para especificar como os cookies são usados em suas páginas da Web. A tabela a seguir descreve as propriedades que podem ser configuradas.

Para configurar o serviço, você pode usar o [Console da Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ou [adicionar uma configuração OSGi ao repositório](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository). A tabela a seguir descreve as propriedades necessárias para qualquer método. Para uma configuração OSGi, o PID do serviço é `com.adobe.granite.optout`.

| Nome da propriedade (console da Web) | Nome da propriedade OSGi | Descrição |
|---|---|---|
| Cookies de recusa | optout.cookies | Os nomes dos cookies que indicam, quando presentes no dispositivo do usuário, que ele não consentiu em usar cookies. |
| Cabeçalhos HTTP de recusa | optout.headers | Os nomes dos cabeçalhos HTTP que indicam, quando presentes, que o usuário não consentiu em usar cookies. |
| Cookies da lista de permissões | optout.whitelist.cookies | Uma lista de cookies essenciais para o funcionamento do site, e que podem ser usados sem o consentimento do usuário. |

## Validação do uso de cookies {#validating-cookie-usage}

Use o JavaScript do lado do cliente para chamar o Serviço de não participação do Adobe Granite e verificar se você pode usar um cookie. Use o objeto de JavaScript Granite.OptOutUtil para executar qualquer uma das seguintes tarefas:

* Obtenha uma lista de nomes de cookies que indicam que esse usuário não consente em usar cookies para fins de rastreamento.
* Obtenha uma lista de cookies que podem ser usados.
* Determine se o navegador da Web contém um cookie que indica que o usuário não consente com o uso de cookies para rastreamento.
* Determine se um cookie específico pode ser usado.

A [pasta da biblioteca do cliente](/help/sites-developing/clientlibs.md#referencing-client-side-libraries) do granite.utils fornece o objeto Granite.OptOutUtil. Adicione o seguinte código à JSP do cabeçalho da página para incluir um link à biblioteca do JavaScript:

`<ui:includeClientLib categories="granite.utils" />`

Por exemplo, a seguinte função do JavaScript determina se o cookie COOKIE_NAME é permitido para uso antes de gravar nele:

```
function writeCookie(value){
   if (!Granite.OptOutUtil.maySetCookie("COOKIE_NAME"))
      return;
   if (value) {
      value = encodeURIComponent(value);
      document.cookie = "COOKIE_NAME=" + value;
   }
}
```

## O objeto Granite.OptOutUtil do JavaScript {#the-granite-optoututil-javascript-object}

Granite.OptOutUtil permite determinar se o uso de cookies é permitido.

### função getCookieNames() {#getcookienames-function}

Os nomes dos cookies que, quando presentes, indicam que o usuário não consentiu com o uso de cookies.

**Parâmetros**

Nenhum.

**Devoluções**

Uma matriz de nomes de cookies.

#### função getWhitelistCookieNames() {#getwhitelistcookienames-function}

Os nomes dos cookies que podem ser usados independentemente do consentimento do usuário.

**Parâmetros**

Nenhum.

**Devoluções**

Uma matriz de nomes de cookies.

#### função isOptedOut() {#isoptedout-function}

Determina se o navegador do usuário contém cookies que indicam que não foi dado consentimento para o uso de cookies.

**Parâmetros**

Nenhum.

**Devoluções**

Um valor booliano de `true` se for encontrado um cookie que indica ausência de consentimento, e um valor de `false` se nenhum cookie indicar não consentimento.

### função maySetCookie(cookieName) {#maysetcookie-cookiename-function}

Determina se um cookie específico pode ser usado no navegador do usuário. Esta função é equivalente a usar a função `isOptedOut` para determinar se o cookie fornecido está incluído na lista retornada pela função `getWhitelistCookieNames`.

**Parâmetros**

* cookieName: cadeia de caracteres. O nome do cookie.

**Devoluções**

Um valor booliano de `true` se `cookieName` puder ser usado, ou um valor de `false` se `cookieName` não puder ser usado.
