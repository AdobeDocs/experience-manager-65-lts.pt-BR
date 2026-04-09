---
title: Atualização do AEM 6.5 LTS no JBoss EAP 8 (Windows)
description: Este guia fornece instruções passo a passo para atualizar uma instalação existente do Adobe Experience Manager (AEM) 6.5 LTS do JBoss EAP 7.4 para o JBoss EAP 8 no Windows, usando o JDK 21.
source-git-commit: 835530039678bc16a6de87b8d580be91a2026f94
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 2%

---

# Atualização do AEM 6.5 LTS no JBoss EAP 8 (Windows)

## Visão geral

Este guia fornece instruções passo a passo para atualizar uma instalação existente do Adobe Experience Manager (AEM) 6.5 LTS do JBoss EAP 7.4 para o JBoss EAP 8 no Windows, usando o JDK 21.

**Caminho de atualização:** JBoss EAP 7.4 (JDK 11) → JBoss EAP 8 (JDK 21)

## Avisos importantes

>[!NOTE]
>
>Este é um procedimento de atualização crítico. Sempre faça primeiro esse upgrade em um ambiente que não seja de produção e mantenha os backups completos.
>
> **&#x200B; PRÉ-REQUISITOS:** É obrigatório fazer backup completo do sistema e um plano de reversão documentado antes de continuar.

## Requisitos de pré-atualização

### Requisitos do sistema

| Componente | Requisito |
|-----------|-------------|
| Sistema Operacional | Windows Server 2016 ou posterior (64 bits) |
| Ambiente do Source | JBoss EAP 7.4 com AEM 6.5 LTS |
| Ambiente de público alvo | JBoss EAP 8.x |
| Java Development Kit | JDK 21 (Oracle ou OpenJDK) |
| Versão do AEM | AEM 6.5 Service Pack (recomendado mais recente) |
| Espaço de disco | Mínimo de 50 GB de espaço livre para o processo de atualização |

### Downloads necessários

Antes de iniciar a atualização, obtenha o seguinte:

1. **Distribuição do JBoss EAP 8.0**\
   Baixar de: [https://developers.redhat.com/products/eap/download](https://developers.redhat.com/products/eap/download)

2. **Instalador do JDK 21**\
   Baixar o Oracle JDK 21 ou OpenJDK 21 para Windows (64 bits)

3. **Arquivo WAR do AEM 6.5 LTS**\
   Obter o AEM 6.5 Service Pack WAR mais recente da Distribuição de software da Adobe

## Etapa 1: Criar Backup Completo

>[!IMPORTANT]
>
> Faça backups abrangentes antes de continuar.

### Lista de verificação de backup

- [ ] Backup completo do diretório de instalação existente do JBoss EAP 7.4
- [ ] Backup da pasta `crx-repository`
- [ ] Backup da pasta `crx-quickstart`
- [ ] Exportação de todas as configurações personalizadas
- [ Backup do banco de dados ] (se estiver usando um banco de dados externo)
- [ ] Documentar as configurações e o estado atual do sistema

### Criar backup

```cmd
# Example backup location
C:\AEM-Backups\Pre-Upgrade-<date>

# Copy entire JBoss 7.4 directory
xcopy "C:\jboss-eap-7.4" "C:\AEM-Backups\Pre-Upgrade-<date>\jboss-eap-7.4" /E /I /H
```

**Recomendado:** Armazene backups em uma unidade separada ou em um local de rede.

## Etapa 2: instalar o JBoss EAP 8

### Extrair JBoss EAP 8

1. Extraia a distribuição ZIP do JBoss EAP 8 para o diretório de instalação de destino:

   ```
   C:\jboss-eap-8.0
   ```

2. Anote este caminho de diretório como `<JBOSS_HOME>` para uso neste guia.

### Replicar estrutura de diretório

Certifique-se de que a nova instalação do JBoss EAP 8 tenha a mesma estrutura de diretório personalizada da configuração anterior do JBoss EAP 7.4, especialmente:

- Diretórios de implantação personalizados
- Pastas de configuração externas
- Locais do arquivo de log
- Qualquer módulo ou biblioteca personalizada

## Etapa 3: Migrar dados do repositório

### Copiar repositório do CRX

1. Navegue até a instalação existente do JBoss EAP 7.4:

   ```
   <OLD_JBOSS_HOME>\bin\crx-repository
   ```

2. Copie toda a pasta `crx-repository` para a nova instalação do JBoss EAP 8:

   ```cmd
   xcopy "C:\jboss-eap-7.4\bin\crx-repository" "C:\jboss-eap-8.0\bin\crx-repository" /E /I /H
   ```

**Importante:** esta pasta contém seu repositório de conteúdo e deve ser transferida completamente.

### Verificar cópia do repositório

Depois de copiar, verifique se o tamanho e a estrutura do repositório correspondem à origem:

```cmd
dir "C:\jboss-eap-8.0\bin\crx-repository" /s
```

## Etapa 4: Interromper instância do AEM

Antes de fazer qualquer alteração, verifique se o AEM foi completamente interrompido.

### Parar pelos Serviços do Windows

1. Abrir **Serviços** (Executar: `services.msc`)
2. Localizar o serviço AEM/JBoss
3. Clique com o botão direito e selecione **Parar**
4. Aguardar até que o serviço pare completamente

### Parar através da linha de comando

Se o AEM foi iniciado manualmente:

1. Vá para a janela do console JBoss
2. Pressione `Ctrl+C`
3. Aguarde o desligamento da energia - normal ser concluído

### Verificar desligamento

Certifique-se de que o processo Java não esteja mais em execução:

```cmd
tasklist | findstr java
```

## Etapa 5: Limpar arquivos herdados do AEM

Remova arquivos desatualizados do diretório `crx-quickstart` para garantir uma atualização limpa.

>[!CAUTION]
>
> Exclua apenas os arquivos e pastas específicos listados abaixo. Não remova nenhum outro arquivo de configuração, código personalizado ou dados do repositório.

### 5.1 Remover a pasta de inicialização do Launchpad

**Local:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\startup
```

**Ação:**

```cmd
rd /s /q "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\startup"
```

**Propósito:** esta pasta contém pacotes OSGi antigos que serão gerados novamente durante a atualização.

### 5.2 Remover arquivo JAR base

**Local:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\org.apache.sling.launchpad.base.jar
```

**Ação:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\org.apache.sling.launchpad.base.jar"
```

**Propósito:** este JAR será substituído pela versão do novo arquivo WAR.

### 5.3 Remover arquivo de comando do Bootstrap

**Local:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\felix\bundle0\BootstrapCommandFile_*.txt
```

**Ação:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\felix\bundle0\BootstrapCommandFile_*.txt"
```

**Finalidade:** comandos do Bootstrap serão regenerados para o novo ambiente.

### 5.4 Remova o arquivo sling.options

**Local:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\felix\sling.options.file
```

**Ação:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\felix\sling.options.file"
```

### 5.5 Remover o arquivo sling_bootstrap.txt

**Local:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\launchpad\sling_bootstrap.txt
```

**Ação:**

```cmd
del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\launchpad\sling_bootstrap.txt"
```

### 5.6 Fazer backup e remover o arquivo sling.properties

Esse arquivo contém configurações específicas do ambiente que podem precisar ser mescladas posteriormente.

**Local:**

```
<JBOSS_HOME>\bin\crx-repository\crx-quickstart\conf\sling.properties
```

**Ação:**

1. **Criar backup:**

   ```cmd
   copy "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\conf\sling.properties" "C:\AEM-Backups\sling.properties.backup"
   ```

2. **Excluir original:**

   ```cmd
   del "C:\jboss-eap-8.0\bin\crx-repository\crx-quickstart\conf\sling.properties"
   ```

**Finalidade:** uma nova `sling.properties` será gerada. Revise seu backup para restaurar qualquer configuração personalizada após a atualização.

## Etapa 6: instalar e configurar o JDK 21

### Instalar JDK 21

1. Executar o instalador do JDK 21 para Windows
2. Instalar em um local padrão (por exemplo, `C:\Program Files\Java\jdk-21`)
3. Concluir o assistente de instalação

### Configurar variáveis de ambiente

#### Definir JAVA_HOME

1. Abrir **Propriedades do Sistema** → **Avançado** → **Variáveis de Ambiente**
2. Em **Variáveis do Sistema**, clique em **Novo**
3. Defina:
   - Nome da variável: `JAVA_HOME`
   - Valor da variável: `C:\Program Files\Java\jdk-21`
4. Clique em **OK**

#### Atualizar variável PATH

1. Em **Variáveis do Sistema**, selecione `Path` e clique em **Editar**
2. Adicionar nova entrada:

   ```
   %JAVA_HOME%\bin
   ```

3. Mova esta entrada para o início da lista para garantir que o JDK 21 tenha precedência
4. Clique em **OK** em todas as caixas de diálogo

### Verificar instalação do Java

1. Abra um Prompt de Comando **novo** (para carregar variáveis de ambiente atualizadas)
2. Verificar versão do Java:

   ```cmd
   java -version
   ```

   Saída esperada:

   ```
   java version "21.0.x"
   Java(TM) SE Runtime Environment (build 21.0.x+...)
   Java HotSpot(TM) 64-Bit Server VM (build 21.0.x+..., mixed mode, sharing)
   ```

3. Verificar JAVA_HOME:

   ```cmd
   echo %JAVA_HOME%
   ```

## Etapa 7: definir configurações da JVM

Antes de implantar o AEM, defina as configurações apropriadas de memória JVM para uso de produção.

### Editar standalone.conf.bat

1. Vá até:

   ```
   <JBOSS_HOME>\bin
   ```

2. Abrir `standalone.conf.bat` em um editor de texto (como Administrador)

3. Localize ou adicione a configuração `JAVA_OPTS`:

   ```batch
   rem # AEM Production JVM Settings
   set "JAVA_OPTS=-Xms4096m -Xmx4096m -XX:MaxMetaspaceSize=768m"
   set "JAVA_OPTS=%JAVA_OPTS% -Djava.net.preferIPv4Stack=true"
   set "JAVA_OPTS=%JAVA_OPTS% -Dfile.encoding=UTF-8"
   set "JAVA_OPTS=%JAVA_OPTS% -server"
   ```

4. Salvar e fechar o arquivo

**Configurações Recomendadas:**

| Parâmetro | Valor recomendado | Descrição |
|-----------|-------------------|-------------|
| `-Xms` | 4096m - 8192m | Tamanho inicial do heap |
| `-Xmx` | 4096m - 8192m | Tamanho máximo do heap |
| `-XX:MaxMetaspaceSize` | 768m - 1024m | Limite de metaspace |

**Observação:** ajuste valores com base na memória disponível do servidor e nos requisitos de carga de trabalho.

## Etapa 8: implantar o AEM 6.5 LTS WAR

### Preparar arquivo WAR

Verifique se o arquivo WAR do AEM está configurado corretamente de acordo com o guia de implantação:

- `jboss-deployment-structure.xml` está presente
- `web.xml` inclui configurações de várias partes
- O WAR será reembalado se qualquer modificação tiver sido feita

### Implantar no JBoss

1. Copie o arquivo WAR do AEM 6.5 LTS para o diretório de implantações:

   ```cmd
   copy "C:\AEM-Downloads\cq-quickstart-6.5.xx.war" "C:\jboss-eap-8.0\standalone\deployments\cq-quickstart.war"
   ```

**Importante:** verifique se o nome de arquivo WAR corresponde ao caminho de contexto de URL desejado.

## Etapa 9: iniciar o JBoss EAP 8 com o AEM

### Iniciar o servidor

1. Abrir **Prompt de Comando** como **Administrador**

2. Navegue até o diretório bin do JBoss:

   ```cmd
   cd C:\jboss-eap-8.0\bin
   ```

3. Iniciar JBoss EAP 8:

   ```cmd
   standalone.bat -b 0.0.0.0 -bmanagement 0.0.0.0
   ```

### Monitorar inicialização inicial

Observe a saída do console para:

1. **Implantação WAR:**

   ```
   Deployed "cq-quickstart.war" (runtime-name : "cq-quickstart.war")
   ```

2. **Mensagens de Inicialização do AEM:**

   ```
   Apache Sling Application Launcher
   Sling Home: crx-repository/crx-quickstart
   ```

3. **Atualização do Repositório (se aplicável):**

   ```
   Performing repository migration...
   ```

**Tempo de Inicialização Esperado:** 5-15 minutos dependendo do tamanho do repositório e dos recursos do sistema.

## Etapa 10: Verificar o êxito da atualização

### Verificar inicialização do AEM

Monitore o console JBoss para obter a mensagem de inicialização final:

```
**** AEM started successfully ****
```

### Acessar a interface da AEM

1. Abrir um navegador da Web
2. Vá até:

   ```
   http://localhost:8080/cq-quickstart
   ```

3. Fazer logon com credenciais de administrador:
   - Nome de Usuário: `admin`
   - Senha: `admin` (ou sua senha personalizada)

### Verificar informações do sistema

1. Navegue até **Ferramentas** → **Operações** → **Console da Web**

   ```
   http://localhost:8080/cq-quickstart/system/console
   ```

2. Clique em **Informações do sistema**

3. Verificar:

   - **Versão do JVM:** deve mostrar o Java 21
   - **Versão do JBoss:** deve mostrar o EAP 8.x
   - **Versão do AEM:** deve mostrar 6.5.xx

### Verificar Integridade do Sistema

Navegue até **Ferramentas** → **Operações** → **Diagnóstico** para executar verificações de integridade:

- Status do pacote: todos os pacotes devem estar &quot;ativos&quot;
- Resolução do recurso: deve mostrar o status íntegro
- Desempenho da consulta: verificar se há degradação

## Tarefas Pós-Atualização

### Restaurar configurações personalizadas

1. Examinar o arquivo `sling.properties` do backup
2. Restaure os modos de execução ou configurações personalizados para o novo arquivo:

   ```
   <JBOSS_HOME>\bin\crx-repository\crx-quickstart\conf\sling.properties
   ```

3. Reinicie o AEM se as configurações forem alteradas

### Atualizar agentes de replicação

1. Navegue até **Ferramentas** → **Implantação** → **Replicação** → **Agentes no Autor**
2. Revisar e testar todos os agentes de replicação
3. Atualizar todas as referências codificadas para caminhos de servidor antigos

### Testar funcionalidade crítica

- [ ] Criação e publicação de conteúdo
- [ ] Carregamento e processamento de ativos
- [ Execução do fluxo de trabalho ]
- [ ] Autenticação de usuário
- [ ] Pontos de extremidade de integração
- [ ] Componentes e modelos personalizados

### Otimização do desempenho

1. Revisar e limpar caches temporários
2. Monitorar o desempenho do sistema durante o uso inicial
3. Ajuste as configurações da JVM, se necessário, com base nos padrões de uso reais

## Resolução de problemas

### Problemas comuns

| Problema | Causa possível | Solução |
|-------|---------------|----------|
| Falha ao iniciar o AEM | Versão incorreta do Java | Verificar `JAVA_HOME` pontos para JDK 21 |
| Erros de corrupção do repositório | Cópia de repositório incompleta | Restaurar a partir do backup e copiar novamente o repositório |
| OutOfMemoryError | Memória de heap insuficiente | Aumento de `-Xmx` em `standalone.conf.bat` |
| Pacotes no estado &quot;Instalado&quot; | Dependências ausentes | Verificar dependências de pacote no Console da Web |
| A porta 8080 já está em uso | Outro serviço usando a porta | Interromper serviço conflitante ou alterar porta JBoss |

### Locais do arquivo de log

- **Log do JBoss Server:**\
  `<JBOSS_HOME>\standalone\log\server.log`

- **Log de Erros do AEM:**\
  `<JBOSS_HOME>\bin\crx-repository\crx-quickstart\logs\error.log`

- **Log de acesso do AEM:**\
  `<JBOSS_HOME>\bin\crx-repository\crx-quickstart\logs\access.log`

### Procedimento de reversão

Se a atualização falhar e não puder ser resolvida:

1. Interromper JBoss EAP 8
2. Restaure o backup completo do JBoss EAP 7.4
3. Restaurar a pasta `crx-repository`
4. Verificar `JAVA_HOME` pontos para JDK 11 (se estiver revertendo)
5. Iniciar o ambiente anterior

## Práticas recomendadas

### Antes da implantação em produção

- [ ] Testar o processo completo de atualização em um ambiente de desenvolvimento
- [ ] Testar em um ambiente de preparo com dados semelhantes aos de produção
- [ ] Documente todas as configurações e integrações personalizadas
- [ ] Criar um plano de reversão detalhado
- [ ] Agendar atualização durante a janela de manutenção
- [ ] Notificar todas as partes interessadas sobre o tempo de inatividade planejado

### Após a atualização bem-sucedida

- [ ] Monitorar logs do sistema por 48 a 72 horas
- [ ] Realizar teste de carga para identificar problemas de desempenho
- [ ] Atualize a documentação do sistema
- [ ] Treine a equipe em qualquer diferença do JBoss EAP 8
- [ ] Arquivar toda a documentação de atualização e os backups

## Documentação relacionada

- [Guia de Migração do JBoss EAP 8](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/8.0/html/migration_guide/)
- [Guia de Atualização do Adobe Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=pt-BR)
- [Instalando Service Packs do AEM](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=pt-BR)

## Informações do documento

| Texto | Valor |
|-------|-------|
| Versão do documento | 1.0 |
| Última atualização | Fevereiro de 2026 |
| Versão do AEM | 6.5 LTS |
| Plataforma Source | JBoss EAP 7.4 / JDK 11 |
| Plataforma de destino | JBoss EAP 8.x / JDK 21 |
| Sistema Operacional | Windows Server |

**Aviso legal:** Adobe, Adobe Experience Manager e AEM são marcas registradas da Adobe Inc. JBoss e Red Hat são marcas registradas da Red Hat, Inc.
