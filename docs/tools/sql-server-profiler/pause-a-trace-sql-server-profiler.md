---
title: "Sospendere una traccia (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sospensione di tracce"
  - "arresto temporaneo di tracce"
  - "tracce [SQL Server], sospensione"
  - "arresto di tracce"
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Sospendere una traccia (SQL Server Profiler)
  La sospensione di una traccia consente di impedire l'ulteriore acquisizione dei dati evento fino al riavvio della traccia.  
  
 Quando si sospende una traccia, è possibile impedire l'acquisizione dei dati evento fino al riavvio della traccia. Il riavvio di una traccia consente di riprendere le operazioni di acquisizione. Dopo il riavvio, gli eventuali dati acquisiti in precedenza non andranno perduti. Quando si riavvia la traccia, l'acquisizione dei dati riprende dal momento del riavvio. Durante la sospensione di una traccia è possibile modificarne il nome, gli eventi, le colonne e i filtri. Non è invece possibile modificare le destinazioni di invio dei dati della traccia o la connessione al server.  
  
### Per sospendere una traccia  
  
1.  Selezionare una finestra contenente una traccia in esecuzione.  
  
2.  Nel menu **File** fare clic su **Sospendi traccia**.  
  
## Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  