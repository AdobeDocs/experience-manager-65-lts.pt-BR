---
title: Criando e Consumindo Jobs para Descarregamento
description: O recurso Apache Sling Discovery fornece uma API Java que permite criar trabalhos JobManager e serviços JobConsumer que os consomem
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Criando e Consumindo Jobs para Descarregamento{#creating-and-consuming-jobs-for-offloading}

O recurso Apache Sling Discovery fornece uma API Java que permite criar trabalhos JobManager e serviços JobConsumer que os consomem.

Para obter informações sobre como criar topologias de descarregamento e configurar o consumo de tópico, consulte [Trabalhos de Descarregamento](/help/sites-deploying/offloading.md).

## Lidar com cargas de trabalho {#handling-job-payloads}

A estrutura de descarregamento define duas propriedades de trabalho que você usa para identificar a carga útil do trabalho. Os agentes de replicação de descarga usam essas propriedades para identificar os recursos a serem replicados nas instâncias na topologia:

* `offloading.job.input.payload`: uma lista separada por vírgulas de caminhos de conteúdo. O conteúdo é replicado para a instância que executa o trabalho.
* `offloading.job.output.payload`: uma lista separada por vírgulas de caminhos de conteúdo. Quando a execução do trabalho é concluída, a carga do trabalho é replicada para esses caminhos na instância que criou o trabalho.

Use a enumeração `OffloadingJobProperties` para fazer referência aos nomes de propriedade:

* `OffloadingJobProperties.INPUT_PAYLOAD.propertyName()`
* `OffloadingJobProperties.OUTPUT_PAYLOAD.propetyName()`

As tarefas não exigem cargas. No entanto, a carga é necessária se o trabalho exigir a manipulação de um recurso e o trabalho for descarregado em um computador que não criou o trabalho.

## Criação de trabalhos de descarregamento {#creating-jobs-for-offloading}

Crie um cliente que chame o método JobManager.addJob para criar um trabalho que um JobConsumer selecionado automaticamente executa. Forneça as seguintes informações para criar o job:

* Tópico: O tópico do trabalho.
* Nome: (opcional)
* Mapa de Propriedades: um objeto `Map<String, Object>` que contém qualquer número de propriedades, como os caminhos de carga útil de entrada e os caminhos de carga útil de saída. Esse objeto Map está disponível para o objeto JobConsumer que executa o job.

O serviço de exemplo a seguir cria um trabalho para um determinado tópico e um caminho de carga de entrada.

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;

import java.util.HashMap;

import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;

import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.ResourceResolver;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class JobGeneratorImpl implements JobGenerator  {

 @Reference
 private JobManager jobManager;
 @Reference ResourceResolverFactory resolverFactory;

 public String createJob(String topic, String payload) throws Exception {
  Job offloadingJob;

  ResourceResolver resolver = resolverFactory.getResourceResolver(null);
  if(resolver.getResource(payload)!=null){

   HashMap<String, Object> jobprops = new HashMap<String, Object>();
   jobprops.put(OffloadingJobProperties.INPUT_PAYLOAD.propertyName(), payload);

   offloadingJob = jobManager.addJob(topic, null, jobprops);
  } else {
   throw new Exception("Payload for job cannot be found");
  }
  if (offloadingJob == null){
   throw new Exception ("Offloading job could not be created");
  }
  return offloadingJob.getId();
 }
}
```

O log contém a seguinte mensagem quando JobGeneratorImpl.createJob é chamado para o tópico `com/adobe/example/offloading` e a carga `/content/geometrixx/de/services`:

```shell
10.06.2013 15:43:33.868 *INFO* [JobHandler: /etc/workflow/instances/2013-06-10/model_1554418768647484:/content/geometrixx/en/company] com.adobe.example.offloading.JobGeneratorImpl Received request to make job for topic com/adobe/example/offloading and payload /content/geometrixx/de/services
```

## Desenvolver um consumidor de trabalho {#developing-a-job-consumer}

Para consumir trabalhos, desenvolva um serviço OSGi que implemente a interface `org.apache.sling.event.jobs.consumer.JobConsumer`. Identifique com o tópico a ser consumido usando a propriedade `JobConsumer.PROPERTY_TOPICS`.

O exemplo de implementação JobConsumer a seguir é registrado com o tópico `com/adobe/example/offloading`. O consumidor simplesmente define a propriedade Consumed do nó de conteúdo da carga útil como true.

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;
import org.apache.sling.event.jobs.consumer.JobConsumer;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import javax.jcr.Session;
import javax.jcr.Node;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class MyJobConsumer implements JobConsumer {

 public static final String TOPIC = "com/adobe/example/offloading";

 @Property(value = TOPIC)
 static final String myTopic = JobConsumer.PROPERTY_TOPICS;

 @Reference
 private ResourceResolverFactory resolverFactory;

 @Reference
 private JobManager jobManager;

 private final Logger log = LoggerFactory.getLogger(getClass());

 public JobResult process(Job job) {
  JobResult result = JobResult.FAILED;
  String topic = job.getTopic();
  log.info("Consuming job of topic: {}", topic);
  String payloadIn =  (String) job.getProperty(OffloadingJobProperties.INPUT_PAYLOAD.propertyName());
  String payloadOut =  (String) job.getProperty(OffloadingJobProperties.OUTPUT_PAYLOAD.propertyName());

  log.info("Job has Input Payload {} and Output Payload {}",payloadIn, payloadOut);

  ResourceResolver resolver = null;
  try {
   resolver = resolverFactory.getAdministrativeResourceResolver(null);
   Session session = resolver.adaptTo(Session.class);
   Node inNode = session.getNode(payloadIn);
   inNode.getNode(Node.JCR_CONTENT).setProperty("consumed",true);
   result = JobResult.OK;
  }catch (Exception e){
   log.info("ERROR -- JOB RESULT IS FAILURE " + e.getMessage());
   result = JobResult.FAILED;
  }
  log.info("Job OK for payload {}",payloadIn);
  return result;
 }
}
```

A classe MyJobConsumer gera as seguintes mensagens de log para uma carga de entrada de /content/geometrixx/de/services:

```shell
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Consuming job of topic: com/adobe/example/offloading
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job has Input Payload /content/geometrixx/de/services and Output Payload /content/geometrixx/de/services
10.06.2013 16:02:40.884 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job OK for payload /content/geometrixx/de/services
```

A propriedade Consumed pode ser observada usando o CRXDE Lite:

![chlimage_1-25](assets/chlimage_1-25a.png)

## Dependências do Maven {#maven-dependencies}

Adicione as seguintes definições de dependência ao arquivo pom.xml para que o Maven possa resolver as classes relacionadas a descarga.

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.event</artifactId>
   <version>3.1.5-R1485539</version>
   <scope>provided</scope>
</dependency>
<dependency>
   <groupId>com.adobe.granite</groupId>
   <artifactId>com.adobe.granite.offloading.core</artifactId>
   <version>1.0.4</version>
   <scope>provided</scope>
</dependency>
```

Os exemplos anteriores também exigiam as seguintes definições de dependência:

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.api</artifactId>
   <version>2.4.3-R1488084</version>
   <scope>provided</scope>
</dependency>

<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
   <version>2.0.0</version>
   <scope>provided</scope>
</dependency>
```
