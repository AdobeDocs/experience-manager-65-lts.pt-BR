---
title: Configuração da autenticação de nó secundário (com base em Elytron)
description: O JBoss EAP 8 usa o Elytron para habilitar a comunicação segura e o registro de nós secundários com o controlador de domínio primário.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: f093f39fb535209297940cff13a99c7631812152
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 3%

---


# Configuração da autenticação de nó secundário (com base em Elytron)

## Configurar a autenticação de nó secundário usando o Elytron

O JBoss EAP 8 usa o **Elytron** para autenticar a comunicação entre os **nós primário e secundário** em uma implantação clusterizada. Essa configuração garante o registro seguro e a comunicação de nós secundários com o controlador de domínio primário.

Duas opções de configuração estão disponíveis, dependendo do ambiente e dos requisitos de segurança.


## Pré-requisitos

* Um **usuário de gerenciamento chamado`secondary`** deve ser criado no **nó primário**.
* Executar esta configuração **somente no(s) nó(s) secundário(s)**.
* Repita a configuração para **cada nó secundário** no cluster.
* **JBoss deve ser completamente interrompido** nos nós primário e secundário.
* Todas as operações do repositório de credenciais devem ser executadas no **modo offline**.

Para interromper o JBoss se ele estiver em execução:

* **Windows**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux/UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

## Escolha uma opção de configuração

* **Opção 1: Configuração Rápida Usando O Repositório De Credenciais Padrão**
Recomendado para ambientes inferiores e testes.

* **Opção 2: Configuração do Repositório de Credenciais Personalizado**
Recomendado para ambientes de produção e seguros.

## Opção 1: Configuração Rápida Usando o Repositório de Credenciais Padrão

**Mais adequado para:** cenários de desenvolvimento, teste e instalação rápida.

### Visão geral

* Um arquivo de repositório de credenciais padrão (`cs_secondary_hc.p12`) está pré-configurado.
* A senha padrão do repositório de credenciais já está definida em `domain.conf`.
* Somente o alias de senha de autenticação precisa ser adicionado.

### Etapas de configuração

#### Etapa 1: Verificar armazenamento de credenciais padrão

Confirme se o arquivo de repositório de credenciais padrão existe:

* **Windows**

  ```
  <JBOSS_HOME>\domain\configuration\cs_secondary_hc.p12
  ```

* **Linux**

  ```
  <JBOSS_HOME>/domain/configuration/cs_secondary_hc.p12
  ```

Se o arquivo não existir, use a **Opção 2**.

#### Etapa 2: Adicionar alias de senha de autenticação

Execute o seguinte comando de `<JBOSS_HOME>/bin`:

* **Windows**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

> O valor do segredo deve corresponder à senha usada ao criar o usuário `secondary` no nó primário.

#### Etapa 3: verificar a configuração de domain.conf

Verifique se a seguinte entrada já existe (nenhuma alteração é necessária):

* **Windows**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=password"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=password"
  ```

#### Etapa 4: iniciar os nós

1. Inicie o **nó primário** e aguarde até que ele seja totalmente inicializado.
2. Iniciar o **nó secundário**.

### Verificação

Verifique os logs:

* **Nó Primário**

  ```
  <JBOSS_HOME>/domain/log/host-controller.log
  ```

  ```
  Registered remote secondary host "secondary"
  ```

* **Nó Secundário**

  ```
  Connected to primary host controller
  ```

## Opção 2: configuração do armazenamento de credenciais personalizado (produção)

**Mais adequado para:** ambientes de produção que exigem segurança avançada.

### Etapas de configuração

#### Etapa 1: Remover Armazenamento De Credenciais Padrão (Se Presente)

Se o armazenamento de credenciais padrão existir, renomeie-o:

* **Windows**

  ```
  rename cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

* **Linux**

  ```
  mv cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

#### Etapa 2: Criar armazenamento de credenciais personalizado

De `<JBOSS_HOME>/bin`:

* **Windows**

  ```
  elytron-tool.bat credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

#### Etapa 3: Adicionar alias de senha de autenticação

* **Windows**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

#### Etapa 4: atualizar domain.conf

Atualizar a referência da senha do repositório de credenciais:

* **Windows**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=YourCustomPassword"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=YourCustomPassword"
  ```

#### Etapa 5: verificar configuração XML

Verifique se `host-secondary.xml` contém as entradas de cliente de autenticação e de repositório de credenciais configuradas.
Nenhuma alteração será necessária se a configuração padrão estiver presente.


#### Etapa 6: iniciar os nós

1. Inicie o **nó primário** e aguarde até que seja totalmente iniciado.
2. Iniciar o **nó secundário**.

### Verificação

Confirme o registro bem-sucedido usando os logs do controlador do host em ambos os nós.

## Resumo

* **A opção 1** fornece uma configuração rápida usando um repositório de credenciais pré-configurado.
* **A opção 2** habilita a segurança mais forte usando uma senha de repositório de credenciais personalizado.
* A configuração deve ser concluída **somente em nós secundários**.
* A configuração do nó primário é reutilizada automaticamente no domínio.

