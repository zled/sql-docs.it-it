---
title: "MSSQL_ENG014005 | Microsoft Docs"
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
  - "MSSQL_ENG014005 - errore"
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# MSSQL_ENG014005
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14005|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Impossibile eliminare la pubblicazione. Vi è associata una sottoscrizione.|  
  
## Spiegazione  
 Si è tentato di eliminare una pubblicazione alla quale sono associate una o più sottoscrizioni. È possibile eliminare una pubblicazione solo se non vi sono sottoscrizioni associate.  
  
## Azione dell'utente  
 Eliminare le sottoscrizioni prima di eliminare la pubblicazione. Se si utilizza [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per eliminare la pubblicazione, si potrà scegliere di eliminare automaticamente tutte le sottoscrizioni associate prima di eliminare la pubblicazione. Se si utilizzano stored procedure, è necessario prima eliminare esplicitamente le sottoscrizioni. Per ulteriori informazioni, vedere [eliminare una sottoscrizione Push](../../relational-databases/replication/delete-a-push-subscription.md) e [eliminare una sottoscrizione Pull](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 Se apparentemente non vi sono sottoscrizioni associate alla pubblicazione o se viene visualizzato questo errore durante la creazione di una pubblicazione, potrebbe esserci una sottoscrizione precedente che non è stata eliminata completamente dopo la rimozione. Eseguire [sp_removedbreplication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) nel database per rimuovere tutti gli oggetti e impostazioni correlate alla replica.  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  