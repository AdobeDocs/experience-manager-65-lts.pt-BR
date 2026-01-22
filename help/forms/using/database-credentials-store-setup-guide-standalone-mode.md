---
title: Guia de Configuração da Database Credential Store (Modo Independente)
description: Localize a configuração do armazenamento de credenciais do banco de dados para o AEM Forms JEE no JBoss/Red Hat EAP no modo independente.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
hide: true
index: false
hidefromtoc: true
source-git-commit: 5d020671efaa4527a5f6dbb4b779c7a3351888a4
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---


# Guia de Configuração da Database Credential Store (Modo Independente)

## Visão geral

Este guia aborda a **configuração do armazenamento de credenciais do banco de dados** para o AEM Forms JEE no JBoss/Red Hat EAP no **modo autônomo**. Isso é necessário ao executar a instalação manual.

**Este guia abrange:**

- Criando o repositório de credenciais do banco de dados (`cred-store.p12`)
- Adicionando aliases de senha de banco de dados com segurança
- Configuração do JBoss para usar o armazenamento de credenciais

**CRÍTICO:** Estes scripts operam EM **SOMENTE MODO OFFLINE**. O JBoss deve ser interrompido antes de executar esses scripts. Os scripts usam o modo `embed-server`, que requer que o servidor seja interrompido.

**Observação:** este é **não** um guia de instalação autônomo completo. Este documento supõe:

- O JBoss já está instalado
- Os arquivos de configuração autônomos (`lc_oracle.xml`, `lc_mysql.xml` ou `lc_mssql.xml`) já estão configurados
- O banco de dados está configurado e acessível

Se você precisar de instruções completas de instalação independente, consulte o guia de instalação principal.

## Pré-requisitos

Antes de executar esses scripts, verifique se:

1. **JBoss DEVE ser interrompido**
   - Estes scripts funcionam somente no **MODO OFFLINE**
   - Os scripts usam `embed-server`, que requer que o servidor seja parado
   - Se JBoss estiver em execução, os scripts falharão
   - Verifique se o JBoss está em execução:
      - Windows: verifique o processo `java.exe` no Gerenciador de Tarefas
      - Linux: `ps aux | grep jboss` ou `ps aux | grep java`
   - Interromper JBoss se estiver em execução:
      - Pressione `Ctrl+C` no terminal onde o JBoss está em execução
      - Ou elimine o processo manualmente

2. **A senha do banco de dados está pronta**

3. **Você optou por uma senha segura para o repositório de credenciais**

4. **Você sabe qual arquivo de configuração de banco de dados está usando:**
   - `lc_oracle.xml` (para banco de dados Oracle)
   - `lc_mysql.xml` (para banco de dados MySQL)
   - `lc_mssql.xml` (para banco de dados do Microsoft SQL Server)

## Etapas de configuração

### Etapa 1: Criar Armazenamento de Credenciais do Banco de Dados

Use os scripts fornecidos para criar o armazenamento de credenciais do banco de dados e adicionar todos os aliases de senha necessários.

#### No Windows:

**Local do Script:** `create-elytron-cred-standalone.bat`

`batch cd path\to\script\location create-elytron-cred-standalone.bat`

**O script solicitará:**
1. **caminho JBOSS_HOME** (por exemplo, `C:\Adobe\Adobe_Experience_Manager_Forms\jboss`)
2. **Nome do arquivo de configuração** (por exemplo, `lc_oracle.xml`, `lc_mysql.xml` ou `lc_mssql.xml`)
3. **Senha do repositório de credenciais** (isso protege o arquivo de repositório de chaves - lembre-se dessa senha)
4. **Senha do banco de dados** (sua senha real do banco de dados)

**O que o script faz:**

- Cria um repositório de credenciais em: `JBOSS_HOME\standalone\configuration\cred-store.p12`
- Modifica temporariamente o arquivo de configuração para habilitar a criação do repositório de credenciais
- Adiciona os seguintes aliases com a senha do banco de dados:
   - `EncryptDBPassword`
   - `EncryptDBPassword_IDP_DS`
   - `EncryptDBPassword_EDC_DS`
   - `EncryptDBPassword_AEM_DS`
- Restaura o arquivo de configuração ao seu estado original
- Verifica se todos os aliases foram adicionados com êxito

#### No Linux:

**Local do Script:** `create-elytron-cred-standalone.sh`

`bash cd /path/to/script/location chmod +x create-elytron-cred-standalone.sh./create-elytron-cred-standalone.sh`

**O script solicitará:**

1. **caminho JBOSS_HOME** (por exemplo, `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss`)
2. **Nome do arquivo de configuração** (por exemplo, `lc_oracle.xml`, `lc_mysql.xml` ou `lc_mssql.xml`)
3. **Senha do repositório de credenciais** (isso protege o arquivo de repositório de chaves - lembre-se dessa senha)
4. **Senha do banco de dados** (sua senha real do banco de dados)

**O que o script faz:**

- Cria um repositório de credenciais em: `JBOSS_HOME/standalone/configuration/cred-store.p12`
- Modifica temporariamente o arquivo de configuração para habilitar a criação do repositório de credenciais
- Adiciona os seguintes aliases com a senha do banco de dados:
   - `EncryptDBPassword`
   - `EncryptDBPassword_IDP_DS`
   - `EncryptDBPassword_EDC_DS`
   - `EncryptDBPassword_AEM_DS`
- Restaura o arquivo de configuração ao seu estado original
- Verifica se todos os aliases foram adicionados com êxito

**Saída esperada:**

```
=== JBoss Elytron Credential Store Setup ===
Enter JBOSS_HOME path (e.g. /opt/jboss): /opt/Adobe/Adobe_Experience_Manager_Forms/jboss
Enter configuration file name (e.g. lc_oracle.xml): lc_oracle.xml
Enter credential store password: ********
Confirm credential store password: ********
Enter database password: ********
Creating credential store using JBoss CLI...
Adding aliases to credential store...
Verifying credential store aliases...

All 4 aliases verified successfully!
- EncryptDBPassword
- EncryptDBPassword_IDP_DS
- EncryptDBPassword_EDC_DS
- EncryptDBPassword_AEM_DS

Credential store setup completed successfully!
```

### Etapa 2: Atualizar Arquivo de Configuração Independente

Após executar o script, é necessário configurar o JBoss para ler a senha do armazenamento de credenciais na inicialização.

#### No Windows:

**Local do Arquivo:** `<JBOSS_HOME>\bin\standalone.conf.bat`

Exemplo: `C:\Adobe\Adobe_Experience_Manager_Forms\jboss\bin\standalone.conf.bat`

Adicione ou atualize a seguinte linha:

```batch
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourActualPassword123"
```

Substitua `YourActualPassword123` pela **senha do repositório de credenciais** usada na Etapa 1.

#### No Linux:

**Local do Arquivo:** `<JBOSS_HOME>/bin/standalone.conf`

Exemplo: `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss/bin/standalone.conf`

Adicione ou atualize a seguinte linha:

```bash
JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourActualPassword123"
```

Substitua `YourActualPassword123` pela **senha do repositório de credenciais** usada na Etapa 1.

### Etapa 3: iniciar JBoss

Após concluir a configuração do armazenamento de credenciais, inicie o JBoss com o arquivo de configuração apropriado.

**Observação:** para obter os comandos e procedimentos de inicialização exatos para iniciar o JBoss no modo independente, consulte o **guia de instalação principal**. Os comandos de inicialização podem variar dependendo da sua configuração específica e do tipo de banco de dados (`lc_oracle.xml`, `lc_mysql.xml` ou `lc_mssql.xml`).

## Verificação

### Verificar Logs do Servidor

**Local do Log:**

- Windows: `<JBOSS_HOME>\standalone\log\server.log`
- Linux: `<JBOSS_HOME>/standalone/log/server.log`

**Procurar mensagens de inicialização bem-sucedidas:**

```
INFO  [org.jboss.as.server] WFLYSRV0025: JBoss EAP started
INFO  [org.jboss.as.connector.deployers.jdbc] Bound data source [java:/AdobeDataSource]
```

**Nenhum erro relacionado a:**

- Carregamento de armazenamento de credencial
- Conexão com o banco de dados
- Aliases ausentes

## Resolução de problemas

### Problema 1: Armazenamento de credenciais não encontrado

**Mensagem de erro:**

```
ERROR Unable to load credential store
```

**Solução:**

1. Verifique se o arquivo de repositório de credenciais existe:
   - Windows: `dir <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux: `ls -l <JBOSS_HOME>/standalone/configuration/cred-store.p12`
2. Se estiver ausente, execute novamente o script de criação de armazenamento de credenciais (Etapa 1)

### Problema 2: Senha incorreta do armazenamento de credenciais

**Mensagem de erro:**

```
ERROR Unable to load credential store - Invalid password
```

**Solução:**
Verifique se a senha em `standalone.conf.bat` / `standalone.conf` (Etapa 2) corresponde à senha usada ao criar o repositório de credenciais (Etapa 1).

**Para Corrigir:**
Editar `standalone.conf.bat` / `standalone.conf` e atualizar a senha:

```
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=CorrectPassword"
```

### Problema 3: Falha na Conexão do Banco de Dados

**Mensagem de erro:**

```
ERROR Failed to obtain connection
```

**Solução:**

1. Verifique se a senha do banco de dados usada no armazenamento de credenciais está correta
2. Verifique se a configuração da fonte de dados faz referência ao alias correto
3. Verificar a conectividade de rede com o servidor de banco de dados

**Para Recriar Repositório de Credenciais:**

1. Parar JBoss
2. Excluir o repositório de credenciais existente:
   - Windows: `del <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux: `rm <JBOSS_HOME>/standalone/configuration/cred-store.p12`
3. Execute novamente o script de criação de repositório de credenciais com a senha de banco de dados correta

### Problema 4: Falha Do Script Durante A Execução

**Mensagem de erro:**

```
ERROR: jboss-cli.bat is not found
```

**Solução:**
Verifique se o caminho JBOSS_HOME está correto e aponta para o diretório de instalação do JBoss.

**Mensagem de erro:**

```
ERROR: Configuration file not found
```

**Solução:**

1. Verifique se o nome do arquivo de configuração está correto
2. Verifique se o arquivo existe no diretório `JBOSS_HOME\standalone\configuration\`
3. Verifique se você está usando o arquivo de configuração correto específico do banco de dados

## Referência rápida

### Armazenamento de Credenciais do Banco de Dados (Modo Independente)

**Propósito:** Armazenar senhas de banco de dados com segurança

**Script:**

- Windows: `create-elytron-cred-standalone.bat`
- Linux: `create-elytron-cred-standalone.sh`

**Cria:**

- Arquivo: `standalone/configuration/cred-store.p12`
- Aliases: `EncryptDBPassword`, `EncryptDBPassword_IDP_DS`, `EncryptDBPassword_EDC_DS`, `EncryptDBPassword_AEM_DS`

**Configuração:**

- Variável: `-DCS_PASS=password`
- Arquivo: `standalone.conf.bat` (Windows) ou `standalone.conf` (Linux)

