---
title: Configuração do SSL no Windows Vista
description: Saiba como configurar o SSL no Windows Vista. Use e execute a Java Keytool para gerar o certificado SSL com chaves RSA para autenticação.
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: ee73f6a1-712c-461f-95e8-85f8c5694293
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%
---
# Configuração do SSL no Windows Vista {#configuring-ssl-on-windows-vista}

Para configurar o SSL no Windows Vista™, você precisa de um certificado SSL com chaves RSA para autenticação. Você pode usar a ferramenta Chave Java para criar o certificado.

>[!NOTE]
>
>O Windows Vista não funcionará com chaves DSA.

Você pode executar a ferramenta de chaves usando um único comando que inclui todas as informações necessárias para criar o certificado e o keystore.

**Criar um certificado SSL**

1. Em um prompt de comando, navegue até *`[JAVA HOME]`*/bin e digite o seguinte comando para criar o certificado e o keystore:

   `keytool -genkey -keyalg RSA -dname "CN=`*Nome do Host* `, OU=`*Nome do Grupo* `, O=`*Nome da Empresa* `,L=`*Nome da Cidade* `, S=`*Estado* `, C=`*Código do País* `" -alias`*&quot;Certificado LC&quot;* `-keypass` `key`*_* *senha* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Substitua *`[JAVA_HOME]`pelo diretório onde o JDK está instalado e o texto em itálico por valores que correspondam ao seu ambiente.*

1. Digite `changeit` como senha. Essa senha é o padrão para uma instalação do Java e o administrador do sistema pode tê-la alterado.
