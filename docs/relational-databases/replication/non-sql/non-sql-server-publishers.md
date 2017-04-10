---
title: "Server di pubblicazione non SQL Server | Microsoft Docs"
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
  - "replica di database eterogenei, server di pubblicazione non SQL Server"
  - "server di pubblicazione non SQL Server"
  - "origini di dati eterogenei, server di pubblicazione non SQL Server"
  - "server di pubblicazione [replica di SQL Server], Oracle"
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Server di pubblicazione non SQL Server
  Pubblicazione di dati da non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] origini consente di consolidare i dati in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente la sottoscrizione di dati snapshot o transazionali pubblicati da un database Oracle. Per ulteriori informazioni sulla pubblicazione da Oracle, vedere [Cenni preliminari sulla pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
 La replica eterogenea a Sottoscrittori non SQL Server è deprecata. La pubblicazione Oracle è deprecata. Per spostare dati, creare soluzioni utilizzando Change Data Capture e [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 La pubblicazione da database non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è ideale nei seguenti scenari:  
  
|Scenario|Descrizione|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Sviluppo con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], operando al contempo su dati replicati da un database non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Server di gestione temporanea di data warehousing|Mantenere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database di gestione temporanea sincronizzato con un[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.|  
|Migrazione a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Verifica dell'applicazione in tempo reale a fronte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replicando al contempo le modifiche del sistema di origine. Quando il risultato della migrazione è soddisfacente, passare a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
  
## Vedere anche  
 [Replica di database eterogenei](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  