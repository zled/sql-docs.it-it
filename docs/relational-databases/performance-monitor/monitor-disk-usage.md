---
title: "Monitoraggio dell&#39;utilizzo del disco | Microsoft Docs"
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
  - "monitoraggio di database [SQL Server], utilizzo del disco"
  - "dischi [SQL Server]"
  - "monitoraggio delle prestazioni [SQL Server], utilizzo del disco"
  - "prestazioni server [SQL Server], utilizzo del disco"
  - "monitoraggio [SQL Server], attività del disco"
  - "paging eccessivo [SQL Server]"
  - "ottimizzazione di database [SQL Server], utilizzo del disco"
  - "I/o [SQL Server], monitoraggio"
  - "dischi [SQL Server], attività di monitoraggio"
  - "isolamento dell'attività del disco [SQL Server]"
  - "prestazioni di database [SQL Server], utilizzo del disco"
  - "monitoraggio delle prestazioni del server [SQL Server], utilizzo del disco"
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Monitoraggio dell&#39;utilizzo del disco
  In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono utilizzate le chiamate di input/output (I/O) del sistema operativo Microsoft Windows per eseguire operazioni di lettura e scrittura sul disco. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestisce i tempi e le modalità di esecuzione delle operazioni di I/O, ma è il sistema operativo Windows a eseguire le operazioni di I/O sottostanti. Il sottosistema di I/O include il bus di sistema, le schede dei controller dei dischi, i dischi, le unità a nastro, l'unità CD-ROM e numerosi altri dispositivi di I/O. L'attività di I/O su disco rappresenta frequentemente la causa di colli di bottiglia in un sistema.  
  
 Il monitoraggio dell'attività del disco si concentra su due aree:  
  
-   Monitoraggio dell'I/O su disco e rilevamento del paging eccessivo  
  
-   Isolamento dell'attività del disco creata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Per ulteriori informazioni, vedere la pagina relativa al [monitoraggio dell'utilizzo del disco](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)  
  
  