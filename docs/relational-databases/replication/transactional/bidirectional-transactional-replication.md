---
title: "Replica transazionale bidirezionale | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replica bidirezionale"
  - "replica transazionale, replica bidirezionale"
  - "replica transazionale bidirezionale"
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Replica transazionale bidirezionale
  La replica transazionale bidirezionale è una topologia di replica transazionale specifica che consente lo scambio reciproco di modifiche tra due server: ogni server pubblica i dati e successivamente esegue la sottoscrizione di una pubblicazione con gli stessi dati dell'altro server. Il **@loopback_detection** parametro [sp_addsubscription & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) è impostata su TRUE per assicurarsi che le modifiche vengono inviate solo a server di sottoscrizione e non comportano la modifica viene inviata al server di pubblicazione.  
  
 In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive, questa topologia è supportata inoltre dalla replica transazionale peer-to-peer, ma la replica bidirezionale può fornire prestazioni migliori.  
  
## Vedere anche  
 [Replica transazionale peer-to-peer](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  