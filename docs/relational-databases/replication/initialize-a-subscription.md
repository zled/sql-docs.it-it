---
title: "Inizializzazione di una sottoscrizione | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replica snapshot [SQL Server], inizializzazione di sottoscrizioni"
  - "replica transazionale, inizializzazione di sottoscrizioni"
  - "inizializzazione di sottoscrizioni [replica di SQL Server]"
  - "sottoscrizioni [replica di SQL Server], inizializzazione"
  - "inizializzazione di sottoscrizioni [replica di SQL Server], informazioni sull'inizializzazione di sottoscrizioni"
  - "replica di tipo merge [replica di SQL Server], inizializzazione di sottoscrizioni"
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Inizializzazione di una sottoscrizione
  I Sottoscrittori in una topologia di replica devono essere inizializzati in modo da disporre di una copia dello schema di ogni articolo della pubblicazione per cui è stata effettuata la sottoscrizione e di tutti gli oggetti di replica necessari, quali stored procedure, trigger e tabelle di metadati. Il Sottoscrittore, inoltre, riceve in genere un set di dati iniziale. Con il metodo di inizializzazione predefinito è possibile utilizzare uno snapshot completo in cui sono inclusi lo schema, gli oggetti di replica e i dati. È tuttavia possibile inizializzare le pubblicazioni senza uno snapshot completo.  
  
 Per ulteriori informazioni, vedere [inizializzare una sottoscrizione con uno Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) e [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  