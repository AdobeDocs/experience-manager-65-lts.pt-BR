---
title: Expiração de objetos estáticos
description: Saiba como configurar o Adobe Experience Manager para que objetos estáticos não expirem (por um período razoável).
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: a279ebed-a116-4719-989e-1b2f79f6caa4
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Expiração de objetos estáticos{#expiration-of-static-objects}

Os objetos estáticos (por exemplo, ícones) não são alterados. Portanto, o sistema deve ser configurado de modo que não expire (por um período de tempo razoável) e, assim, reduza o tráfego desnecessário.

Isso tem o seguinte impacto:

* Descarrega solicitações da infraestrutura do servidor.
* Aumenta o desempenho do carregamento da página, à medida que o navegador armazena objetos em cache no cache do navegador.

As expirações são especificadas pelo padrão HTTP em relação à &quot;expiração&quot; de arquivos (por exemplo, consulte o capítulo 14.21 de [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt) &quot; Hypertext Transfer Protocol — HTTP 1.1&quot;). Esse padrão usa o cabeçalho para permitir que os clientes armazenem objetos em cache até que sejam considerados obsoletos; esses objetos são armazenados em cache pelo período especificado sem que nenhuma verificação de status seja feita no servidor de origem.

>[!NOTE]
>
>Essa configuração é separada da Dispatcher (e não funcionará para ela).
>
>A finalidade do Dispatcher é armazenar dados em cache na frente do Adobe Experience Manager (AEM).

Todos os arquivos, que não são dinâmicos e que não mudam com o tempo, podem e devem ser armazenados em cache. A configuração do servidor HTTPD do Apache pode ser semelhante a um dos seguintes - dependendo do ambiente:

>[!CAUTION]
>
>Tenha cuidado ao definir o período durante o qual um objeto é considerado atualizado. Como não há *nenhuma verificação até que o período de tempo especificado expire*, o cliente pode acabar apresentando conteúdo antigo do cache.

1. **Para uma instância de Autor:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /libs>
     ExpiresByType text/css "access plus 1 month"
     ExpiresByType text/javascript "access plus 1 month"
     ExpiresByType image/png "access plus 1 month"
     ExpiresByType image/gif "access plus 1 month"
   </Location>
   ```

   Isso permite que o cache intermediário (por exemplo, o cache do navegador) armazene arquivos CSS, JavaScript, PNG e GIF por até um mês, até que expirem. Isso significa que eles não precisam ser solicitados do AEM ou do servidor Web, mas podem permanecer no cache do navegador.

   Outras seções do site não devem ser armazenadas em cache em uma instância de autor, pois estão sujeitas a alterações a qualquer momento.

1. **Para uma instância de publicação:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /content>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   <Location /etc/designs>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   ```

   Isso permite que o cache intermediário (por exemplo, o cache do navegador) armazene arquivos CSS, JavaScript, PNG e GIF por até um dia nos caches do cliente. Embora este exemplo ilustre as configurações globais para tudo abaixo de `/content` e `/etc/designs`, você deve torná-lo mais granular.

   Dependendo da frequência com que seu site é atualizado, você também pode considerar o armazenamento em cache de páginas do HTML. Um período de tempo razoável seria de uma hora:

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Após configurar os objetos estáticos, examine `request.log`, ao selecionar páginas que contêm esses objetos, para confirmar se nenhuma solicitação (desnecessária) está sendo feita para objetos estáticos.
