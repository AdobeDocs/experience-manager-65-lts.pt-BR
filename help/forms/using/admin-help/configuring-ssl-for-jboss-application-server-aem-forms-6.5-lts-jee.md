---
title: Configurando o SSL para o JBoss Application Server (AEM 6.5 LTS JEE)
description: Saiba como configurar o SSL para o JBoss Application Server.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 86d6d0f7b6fe1c36349f29e45a3eee31b04e5e80
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---


# Configurando o SSL para o JBoss Application Server (AEM 6.5 LTS JEE)

## Visão geral

Para configurar o SSL no JBoss Application Server for Adobe Experience Manager (AEM) 6.5 LTS em execução no Java EE, você deve habilitar a comunicação HTTPS segura. A habilitação do SSL criptografa os dados trocados entre os clientes e o servidor, tornando-o um requisito de segurança essencial para qualquer implantação de produção do AEM Forms.

O processo envolve duas etapas principais:

- **Obtendo uma credencial SSL** — gerando um certificado autoassinado ou solicitando um de uma Autoridade de Certificação (CA).
- **Habilitando SSL em JBoss** — usando o subsistema Elytron por meio de comandos CLI JBoss.

Neste guia, os seguintes valores de espaço reservado são usados:

- `[appserver root]` — o diretório inicial do servidor de aplicativos JBoss que está executando o AEM Forms.
- `[type]` — um nome de pasta que varia dependendo do tipo de instalação executada.
- `[JAVA_HOME]` — o diretório onde o JDK está instalado.

## Parte 1: Criar uma credencial SSL (autoassinado)

Se você não tiver um certificado de uma CA, poderá gerar uma credencial SSL autoassinada usando o utilitário Java `keytool`. Isso é adequado para ambientes de desenvolvimento ou teste.

### Etapa 1 — Gerar o armazenamento de chaves

Navegue até `[JAVA_HOME]/bin` em um prompt de comando e execute o comando a seguir, substituindo os valores pelos valores apropriados para o seu ambiente. O Nome do Host deve ser o FQDN (nome de domínio totalmente qualificado) do servidor de aplicativos:

```bash
keytool -genkey -dname "CN=Host Name, OU=Group Name, O=Company Name, L=City Name, S=State, C=Country Code" \
  -alias "AEMForms Cert" -keyalg RSA \
  -keypass key_password -keystore keystorename.keystore
```

Quando solicitado, insira o `keystore_password`. Observe que a senha do keystore e a chave devem ser idênticas.

### Etapa 2 — Copiar o armazenamento de chaves para o diretório de configuração

Copie o keystore gerado na pasta de configuração apropriada para seu tipo de instalação:

```bash
# Windows Single Server
copy keystorename.keystore [appserver root]\standalone\configuration

# Windows Server Cluster
copy keystorename.keystore [appserver root]\domain\configuration

# Linux Single Server
cp keystorename.keystore [appserver root]/standalone/configuration

# Linux Server Cluster
cp keystorename.keystore [appserver root]/domain/configuration
```

### Etapa 3 — Exportar o arquivo de certificado

Exporte o certificado do keystore usando um dos seguintes comandos:

```bash
# Single Server
keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [appserver root]/standalone/configuration/keystorename.keystore

# Server Cluster
keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [appserver root]/domain/configuration/keystorename.keystore
```

Digite o `keystore_password` quando solicitado.

### Etapa 4 — copiar e verificar o certificado

Copie `AEMForms_cert.cer` para o diretório de configuração e verifique seu conteúdo:

```bash
# Copy (Linux Single Server example)
cp AEMForms_cert.cer [appserver root]/standalone/configuration

# Verify certificate contents (Single Server)
keytool -printcert -v -file [appserver root]/standalone/configuration/AEMForms_cert.cer

# Verify certificate contents (Server Cluster)
keytool -printcert -v -file [appserver root]/domain/configuration/AEMForms_cert.cer
```

### Etapa 5 — Importar o certificado para o Java Truststore

Antes de importar, verifique se o arquivo `cacerts` é gravável:

```bash
# Windows: Right-click cacerts → Properties → deselect Read-only

# Linux:
chmod 777 [JAVA_HOME]/jre/lib/security/cacerts
```

Em seguida, importe o certificado:

```bash
keytool -import -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [JAVA_HOME]/jre/lib/security/cacerts
```

Quando a senha for solicitada, digite `changeit` (a senha padrão do Java truststore — verifique com o administrador se isso foi alterado). Quando solicitado **Confiar neste certificado? [não]**, tipo `yes`. Você deve ver uma mensagem de confirmação: *&quot;O certificado foi adicionado ao keystore.&quot;*

>[!NOTE]
>
> Se você estiver se conectando ao AEM Forms por SSL a partir do Workbench, também deve instalar o certificado no computador do Workbench.

## Parte 2: Ativar SSL em JBoss usando o subsistema Elytron

Com a credencial SSL em vigor, agora é possível ativar HTTPS no JBoss usando seu subsistema de segurança Elytron pela CLI do JBoss. Verifique se o arquivo de armazenamento de chaves está localizado no diretório de configuração apropriado antes de continuar.

>[!NOTE]
>
> No Windows, cada comando da CLI deve ser inserido como uma única linha sem quebras de linha. Substitua `keystorename.keystore` com seu nome de arquivo real e `changeit` com seu armazenamento de chaves/senha de chave.

### Etapa 6a — Criar uma loja de chaves Elytron

```bash
/subsystem=elytron/key-store=aemKeyStore:add(
  path="keystorename.keystore",
  relative-to=jboss.server.config.dir,
  type="JKS",
  credential-reference={clear-text="changeit"})
```

Substitua `JKS` por `PKCS12` se o keystore usar esse formato.

### Etapa 6b — Criar o gerenciador de chaves Elytron

```bash
/subsystem=elytron/key-manager=aemKeyManager:add(
  key-store=aemKeyStore,
  credential-reference={clear-text="changeit"})
```

Se o armazenamento de chaves contiver várias entradas de certificado, especifique explicitamente o alias:

```bash
/subsystem=elytron/key-manager=aemKeyManager:add(
  key-store=aemKeyStore,
  alias="AEMForms Cert",
  credential-reference={clear-text="changeit"})
```

### Etapa 6c — Atualizar o contexto SSL do servidor

```bash
/subsystem=elytron/server-ssl-context=applicationSSC:write-attribute(
  name=key-manager,
  value=aemKeyManager)
```

### Etapa 6d — Configurar o ouvinte HTTPS Undertow

Conecte o contexto SSL ao Undertow (o servidor Web JBoss) para ativar o ouvinte HTTPS:

```bash
/subsystem=undertow/server=default-server/https-listener=https:add(
  socket-binding=https,
  ssl-context=applicationSSC)
```

## Parte 3: Reiniciar o servidor de aplicativos

Após concluir a configuração do Elytron, reinicie o JBoss para aplicar as alterações.

### Instalações Turnkey (Serviços do Windows)

- Abra **Painel de Controle > Ferramentas Administrativas > Serviços**.
- Selecione **JBoss para Adobe Experience Manager forms**.
- Selecione **Ação > Parar** e aguarde a interrupção do serviço.
- Selecione **Ação > Iniciar**.

### Instalações pré-configuradas ou manuais do JBoss

Em um prompt de comando, navegue até `[appserver root]/bin`:

```bash
# Stop the server
Windows: shutdown.bat -S
Linux:   ./shutdown.sh -S

# Wait until JBoss fully shuts down, then start the server
Windows: run.bat -c <profile>
Linux:   ./run.sh -c <profile>
```

## Parte 4: Solicitar uma credencial de uma autoridade de certificação

Para ambientes de produção, você deve usar um certificado emitido por uma CA confiável. O processo envolve a geração de um par de chaves, a criação de uma Solicitação de assinatura de certificado (CSR) e a importação do certificado assinado pela CA.

### Gerar o armazenamento de chaves e criar uma CSR

Navegue até `[JAVA_HOME]/bin` e gere o keystore:

```bash
keytool -genkey -dname "CN=Host Name, OU=Group Name, O=Company Name, L=City Name, S=State, C=Country Code" \
  -alias "AEMForms Cert" -keyalg RSA \
  -keypass key_password -keystore keystorename.keystore
```

Em seguida, gere a CSR para enviar à CA:

```bash
keytool -certreq -alias "AEMForms Cert" \
  -keystore keystorename.keystore \
  -file AEMFormscertRequest.csr
```

Envie o arquivo `.csr` à sua autoridade de certificação. Depois de receber o certificado assinado de volta, siga as etapas abaixo.

### Importar o certificado assinado pela CA

Importe primeiro o certificado raiz de CA:

```bash
keytool -import -trustcacerts -file rootcert.pem \
  -keystore keystorename.keystore -alias root
```

Se o certificado raiz ainda não for confiável para o navegador, importe-o para lá também. Em seguida, importe o certificado assinado pela CA:

```bash
keytool -import -trustcacerts -file CACertificateName.crt \
  -keystore keystorename.keystore
```

>[!NOTE]
>
> O certificado assinado pela CA importado substituirá qualquer certificado público autoassinado existente, se houver um presente no armazenamento de chaves.

Depois que o certificado de autoridade de certificação for importado, continue com as **Etapas 6a-6d** da Parte 2 (configuração Elytron), reinicie o servidor (Parte 3) e verifique o acesso SSL.

## Verificar acesso SSL

Depois de reiniciar o servidor, verifique se o SSL está funcionando corretamente acessando o console de administração do AEM Forms por HTTPS. A porta SSL padrão para JBoss é `8443`:

```
https://[host name]:8443/adminui
```

Se o console de administração carregar com êxito em HTTPS, o SSL foi configurado corretamente. Use a porta `8443` para todas as conexões SSL subsequentes com o AEM Forms.
