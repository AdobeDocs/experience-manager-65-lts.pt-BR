---
title: Configuração do Armazenamento de Credenciais do Banco de Dados (com base no Elytron)
description: O JBoss EAP 8 oferece suporte a armazenamentos de credenciais Elytron para gerenciamento seguro de senhas de banco de dados na AEM Forms para configuração do modo de domínio.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: f093f39fb535209297940cff13a99c7631812152
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 2%

---


# Configuração do Armazenamento de Credenciais do Banco de Dados (com base no Elytron)

## Configurar Repositório de Credenciais do Banco de Dados Usando Elytron

O JBoss EAP 8 usa **armazenamentos de credenciais Elytron** para gerenciar com segurança senhas de bancos de dados para implantações do AEM Forms. A Adobe fornece **scripts automatizados** para simplificar a criação e a configuração do armazenamento de credenciais baseado em Elytron no modo de domínio.


Esta instalação deve ser concluída **antes de iniciar o Controlador de Domínio JBoss**.

### Pré-requisitos

* O **servidor JBoss deve ser completamente interrompido** antes de executar o script de criação de repositório de credenciais.
* A criação do repositório de credenciais deve ser executada somente no **modo offline**.

Para interromper o JBoss se ele estiver em execução:

* **Windows**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux/UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

### Baixar Scripts

Baixe o script apropriado com base no seu sistema operacional:

| Nome do script | Sistema Operacional |
| -------------------------------- | ---------------- |
| `create-elytron-cred-domain.bat` | Windows |
| `create-elytron-cred-domain.sh` | Linux/UNIX |

Para Linux, torne o script executável:

```
chmod +x create-elytron-cred-domain.sh
```

### Etapas de configuração

#### Etapa 1: baixar e colocar o script

Baixe o script apropriado e coloque-o no seguinte diretório:

```
<JBOSS_HOME>/bin
```

#### Etapa 2: executar o script

* **Windows**

  ```
  cd <JBOSS_HOME>\bin
  create-elytron-cred-domain.bat
  ```

* **Linux/UNIX**

  ```
  cd <JBOSS_HOME>/bin
  ./create-elytron-cred-domain.sh
  ```

#### Etapa 3: Fornecer As Informações Necessárias

Durante a execução, o script solicita as seguintes entradas:

1. **Caminho do JBOSS_HOME**
Insira o caminho completo para o diretório de instalação do JBoss.

2. **Nome do Arquivo de Configuração do Banco de Dados**
Insira uma das seguintes opções com base no seu banco de dados:

   * `domain_oracle.xml`
   * `domain_mysql.xml`
   * `domain_mssql.xml`

3. **Senha do Repositório de Credenciais**
Insira uma senha forte para proteger o armazenamento de credenciais.

   > Esta senha fica oculta durante a entrada e deve ser lembrada para etapas posteriores.

4. **Senha do Banco de Dados**
Digite a senha da conexão real com o banco de dados.

#### Etapa 4: Execução e validação de script

O script executa as seguintes ações automaticamente:

* Cria `cred-store.p12` em:

  ```
  <JBOSS_HOME>/domain/configuration/
  ```

* Cria os seguintes aliases de credencial:

   * `EncryptDBPassword`
   * `EncryptDBPassword_IDP_DS`
   * `EncryptDBPassword_EDC_DS`
   * `EncryptDBPassword_AEM_DS`
* Verifica se todos os aliases foram adicionados com êxito

A execução bem-sucedida confirma a criação do armazenamento de credenciais e a verificação de alias.

#### Etapa 5: Configurar Opções de JVM

Atualize a configuração de inicialização do domínio JBoss para fornecer a senha do armazenamento de credenciais.

* **Linux**
Editar:

  ```
  <JBOSS_HOME>/bin/domain.conf
  ```

  Adicionar:

  ```
  JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourCredStorePassword"
  ```

* **Janelas**
Editar:

  ```
  <JBOSS_HOME>/bin/domain.conf.bat
  ```

  Adicionar:

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourCredStorePassword"
  ```

Substitua `YourCredStorePassword` pela senha inserida durante a criação do repositório de credenciais.

Os arquivos de configuração de domínio fazem referência a esse valor usando a variável `${CS_PASS}`.


#### Etapa 6: verificar configuração de domínio

Abra o arquivo de configuração de domínio do banco de dados:

```
<JBOSS_HOME>/domain/configuration/<domain_*.xml>
```

Verifique se as fontes de dados fazem referência ao armazenamento de credenciais Elytron:

```xml
<security>
    <user-name>your_database_username</user-name>
    <credential-reference store="db-creds" alias="EncryptDBPassword_IDP_DS"/>
</security>
```

Cada fonte de dados usa um alias específico:

* **IDP_DS:** `EncryptDBPassword_IDP_DS`
* **EDC_DS:** `EncryptDBPassword_EDC_DS`
* **AEM_DS:** `EncryptDBPassword_AEM_DS`
* **DefaultDS / ExampleDS:** `EncryptDBPassword`

Todos os aliases fazem referência à mesma senha do banco de dados armazenada no armazenamento de credenciais.

>[!NOTE]
>
>* Configure o armazenamento de credenciais somente no nó principal.
>* Os nós secundários usam automaticamente a configuração de domínio sincronizada a partir do nó primário.
