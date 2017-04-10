---
title: "Monitoraggio della replica con Monitor di sistema | Microsoft Docs"
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
  - "monitoraggio delle prestazioni [replica di SQL Server], Monitor di sistema"
  - "Monitor di sistema [SQL Server], replica"
  - "contatori delle prestazioni [replica di SQL Server]"
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Monitoraggio della replica con Monitor di sistema
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Monitor di sistema Windows consente di utilizzare i grafici, grafici e report per misurare l'efficienza del computer, identificare e risolvere gli eventuali problemi (ad esempio, utilizzo non equilibrato delle risorse hardware insufficienti o di programmi insufficienti) e pianificare hardware aggiuntive. Per ulteriori informazioni, vedere [monitoraggio dell'utilizzo di risorse & #40; Monitor di sistema & #41;](../../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md).  
  
 In Monitor di sistema vengono utilizzati oggetti e contatori delle prestazioni che forniscono informazioni sulle prestazioni dei vari processi. È possibile misurare le prestazioni della replica mediante contatori associati agli agenti di replica:  
  
|Agente|Oggetto prestazione|Contatore|Descrizione|  
|-----------|------------------------|-------------|-----------------|  
|Tutti gli agenti|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Gli agenti di replica|In esecuzione|Numero di agenti di replica correntemente in esecuzione.|  
|agente snapshot|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Snapshot di replica|Snapshot:Comandi recapitati/sec|Numero di comandi al secondo recapitati al database di distribuzione.|  
|agente snapshot|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Snapshot di replica|Snapshot:Transazioni recapitate/sec|Numero di transazioni al secondo recapitate al database di distribuzione.|  
|Agente di lettura log|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lettura log repliche|Lettura log:Comandi recapitati/sec|Numero di comandi al secondo recapitati al database di distribuzione.|  
|Agente di lettura log|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lettura log repliche|Lettura log:Transazioni recapitate/sec|Numero di transazioni al secondo recapitate al database di distribuzione.|  
|Agente di lettura log|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lettura log repliche|Lettura log:Latenza recapito|L'intervallo di tempo in millisecondi che intercorre tra l'applicazione delle transazioni nel server di pubblicazione e il recapito delle transazioni al server di distribuzione.|  
|Agente di distribuzione|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribuzione repliche|Dist:Comandi recapitati/sec|Numero di comandi al secondo recapitati al Sottoscrittore.|  
|Agente di distribuzione|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribuzione repliche|Dist:Transazioni recapitate/sec|Numero di transazioni al secondo recapitate al Sottoscrittore.|  
|Agente di distribuzione|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribuzione repliche|Dist:Latenza recapito|L'intervallo di tempo in millisecondi che intercorre tra il recapito delle transazioni al server di distribuzione e l'applicazione delle transazioni nel Sottoscrittore.|  
|Agente di merge|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Merge repliche|Conflitti/sec|Numero di conflitti al secondo generati durante il processo di replica di tipo merge.|  
|Agente di merge|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Merge repliche|Modifiche scaricate/sec|Il numero di righe al secondo replicate dal server di pubblicazione nel Sottoscrittore.|  
|Agente di merge|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Merge repliche|Modifiche caricate/sec|Il numero di righe al secondo replicate dal Sottoscrittore nel server di pubblicazione.|  
  
## Vedere anche  
 [Monitoraggio & #40; Replica & #41;](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  