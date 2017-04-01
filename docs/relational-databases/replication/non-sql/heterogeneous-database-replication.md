---
title: "Replica di database eterogenei | Microsoft Docs"
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
  - "replica di database eterogenei,informazioni sulla replica di database eterogenei"
  - "replica [SQL Server], replica di database eterogenei"
  - "replica di database eterogenei"
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Replica di database eterogenei
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta gli scenari eterogenei seguenti per la replica transazionale e snapshot:  
  
-   Pubblicazione di dati da Oracle a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Pubblicazione di dati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 La replica eterogenea a Sottoscrittori non SQL Server è deprecata. La pubblicazione Oracle è deprecata. Per spostare dati, creare soluzioni utilizzando Change Data Capture e [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## Pubblicazione di dati da Oracle  
 È possibile utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per pubblicare dati di Oracle con le stesse funzionalità e la stessa facilità d'uso della replica snapshot e transazionale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La pubblicazione di dati da Oracle è ideale per gli scenari seguenti:  
  
|Scenario|Descrizione|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Sviluppo con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], operando al contempo su dati replicati da un database non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Server di gestione temporanea di data warehousing|Mantenere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database di gestione temporanea sincronizzato con un[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.|  
|Migrazione a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Verifica dell'applicazione in tempo reale a fronte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replicando al contempo le modifiche del sistema di origine. Quando il risultato della migrazione è soddisfacente, passare a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
  
 Per ulteriori informazioni, vedere [Cenni preliminari sulla pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## Pubblicazione di dati in Sottoscrittori non SQL Server  
 I database non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] seguenti sono supportati come Sottoscrittori per le pubblicazioni snapshot e transazionali:  
  
-   Oracle per tutte le piattaforme supportate da Oracle.  
  
-   IBM DB2 per AS400, MVS, Unix, Linux e Windows.  
  
 Per ulteriori informazioni, vedere [sottoscrittori Non SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
  