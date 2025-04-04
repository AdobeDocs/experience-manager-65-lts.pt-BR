---
title: Testes - quando e com quem?
description: Várias funções podem ser envolvidas em testes e em vários estágios de desenvolvimento do projeto.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Testes - quando e com quem?{#testing-when-and-with-whom}

Várias funções podem ser envolvidas em testes e em vários estágios de desenvolvimento do projeto.

<table>
 <tbody>
  <tr>
   <td>Equipe de teste</td>
   <td>Responsável por... </td>
   <td>Quando...</td>
  </tr>
  <tr>
   <td>Equipe de desenvolvimento</td>
   <td>A equipe de desenvolvimento é responsável pelos testes de unidade e por alguns testes de integração.</td>
   <td>Esses testes são os primeiros na cadeia, embora sejam repetidos/estendidos durante o desenvolvimento.</td>
  </tr>
  <tr>
   <td>Equipe do Quality Assurance</td>
   <td><p>Você precisa de uma Equipe do Quality Assurance (de qualquer tamanho, se apropriado) para testes funcionais e de desempenho.</p> <p>São testadores neutros e dedicados - uma regra de ouro do software sempre afirma que um desenvolvedor nunca deve testar seu próprio trabalho.</p> <p>Os membros dessa equipe podem ser retirados da equipe do projeto Day, do parceiro e/ou da equipe do cliente.</p> </td>
   <td><p>A primeira versão da função deve ser disponibilizada aos testadores (quando for possível). Embora uma versão provisória antecipada possa gerar muitos bugs, ela pode fornecer feedback antecipado sobre problemas críticos.</p> </td>
  </tr>
  <tr>
   <td>Equipe de teste do cliente</td>
   <td><p>Dependendo do Modelo de projeto selecionado, pode ser planejado que membros da equipe do cliente estejam envolvidos no teste, especialmente autores do site do cliente.</p> <p>Isso é vantajoso porque:</p>
    <ul>
     <li><p>O cliente recebe experiência do projeto que está sendo desenvolvido.</p> </li>
     <li><p>Fornece feedback antecipado do cliente.</p> </li>
     <li><p>Os usuários muitas vezes expressam seus requisitos em termos de experiência anterior; envolver os clientes em testes o mais cedo possível aumenta sua experiência com o novo projeto em termos de experiência <i>prática</i>.</p> </li>
    </ul> </td>
   <td><p>Novamente, o envolvimento antecipado é bom, embora qualquer versão que os clientes usem deva ser estável, com funcionalidade razoável.</p> <p>As primeiras impressões são sempre importantes.</p> </td>
  </tr>
 </tbody>
</table>
