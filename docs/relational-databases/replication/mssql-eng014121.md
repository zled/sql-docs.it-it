---
title: "MSSQL_ENG014121 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014121 - errore"
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# MSSQL_ENG014121
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14121|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Al server di distribuzione '%s' sono associati database di distribuzione. Impossibile eliminarlo.|  
  
## Spiegazione  
 Un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurata come server di distribuzione non può essere rimossa dal ruolo di server di distribuzione poiché all'istanza sono associati database di distribuzione. Questo errore si verifica se si tenta di eliminare un database di distribuzione associato a uno o più server di pubblicazione.  
  
## Azione dell'utente  
 Per individuare i nomi dei server di pubblicazione e i database di distribuzione associati a questo server di distribuzione, eseguire [sp_helpdistpublisher & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md) da qualsiasi database nel server di distribuzione.  
  
 Eseguire [sp_dropdistributiondb & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md) per i database di distribuzione associati a questo server di distribuzione. Dopo la rimozione di tutte le associazioni di database di distribuzione, è possibile disabilitare la distribuzione.  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Configurazione della distribuzione](../../relational-databases/replication/configure-distribution.md)  
  
  