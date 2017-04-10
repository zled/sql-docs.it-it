---
title: "Creare un avviso del database di SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "prestazioni database [SQL Server], avvisi"
  - "avvisi [SQL Server], creazione"
  - "soglie [SQL Server]"
  - "avvisi di database [SQL Server]"
  - "ottimizzazione database [SQL Server], avvisi"
  - "monitoraggio prestazioni [SQL Server], avvisi"
  - "monitoraggio prestazioni server [SQL Server], avvisi"
  - "monitoraggio database [SQL Server], avvisi"
  - "prestazioni server [SQL Server], avvisi"
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Creare un avviso del database di SQL Server
  È possibile utilizzare Monitoraggio di sistema per creare un avviso da generare quando viene raggiunto un valore soglia specificato per un contatore di Monitoraggio di sistema. In risposta all'avviso, Monitoraggio di sistema avvia un'applicazione, ad esempio un'applicazione personalizzata programmata per gestire la condizione dell'avviso. Ad esempio, è possibile creare un avviso che viene generato quando il numero di deadlock supera un determinato valore.  
  
 È inoltre possibile definire avvisi utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Per altre informazioni, vedere [Avvisi](../../ssms/agent/alerts.md).  
  
 Per altre informazioni sull'uso di Monitoraggio di sistema per impostare un avviso del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Impostazione di un avviso del database di SQL Server &#40;Windows&#41;](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md).  
  
## Vedere anche  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  