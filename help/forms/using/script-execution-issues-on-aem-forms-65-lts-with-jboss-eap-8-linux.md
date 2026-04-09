---
title: Falha na execução do script no AEM Forms 6.5 LTS com JBoss EAP 8 (Linux)
description: Configurando o JBoss EAP 8.0 em um ambiente Linux, você pode encontrar determinados erros ao executar scripts de shell ou arquivos de inicialização
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: 4dfaa625-47fa-4681-9e2f-a3bbdca95276
source-git-commit: 96fe29ceae4c38238ccc40d456f2ad8e276788c7
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Falha na execução do script no AEM Forms 6.5 LTS com JBoss EAP 8 (Linux)

## Problema

Ao configurar o **JBoss EAP 8.0 (AEM Forms 6.5.1 LTS)** em um ambiente **Linux**, você pode encontrar um dos seguintes erros ao executar scripts de shell ou arquivos de inicialização:

```text
/bin/sh^M: bad interpreter
$'\r': command not found
```

Estes erros ocorrem quando scripts de shell ou arquivos de configuração são criados ou editados em um sistema **Windows** e contêm terminações de linha **CRLF (Retorno de Carro + Alimentação de Linha)**.
Os sistemas Linux suportam apenas **LF (Line Feed)** terminações de linha, e terminações de linha no estilo do Windows causam falhas de execução de script.

## Aplica-se a

* **JBoss EAP 8.0**
* **Sistemas operacionais baseados em Linux/UNIX**

## Etapas de solução de problemas

1. **Identificar o arquivo afetado**

   * Revise a saída do erro para identificar o script `.sh` ou o arquivo de configuração que está causando a falha.

2. **Converter o arquivo para o formato Unix**

   * Use o utilitário `dos2unix` para converter terminações de linha de estilo Windows para o formato Unix:

     ```bash
     dos2unix <file_name>
     ```

   * Substitua `<file_name>` pelo script ou arquivo de configuração real que está gerando o erro.

3. **Repetir se necessário**

   * Se vários scripts forem afetados, repita a conversão para todos os arquivos `.sh` relevantes (por exemplo, scripts de inicialização do instalador, LCM ou JBoss).

4. **Executar o script novamente**

   * Após a conversão, execute o script novamente para confirmar se o problema foi resolvido.

Depois de converter os arquivos em terminações de linha Unix (LF), os erros `/bin/sh^M` e `$'\r': command not found` são resolvidos e os scripts JBoss são executados com êxito no Linux.
