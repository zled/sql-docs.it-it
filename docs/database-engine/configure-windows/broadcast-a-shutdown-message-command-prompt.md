---
title: "Trasmissione di un messaggio di chiusura (prompt dei comandi) | Microsoft Docs"
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
  - "SQL Server, arresto"
  - "istanze denominate [SQL Server], trasmissione di messaggi di chiusura"
  - "trasmissione di messaggi di chiusura"
  - "trasmissione di messaggio di chiusura"
  - "prompt dei comandi [SQL Server], trasmissione di messaggi di chiusura"
  - "istanze predefinite [SQL Server], trasmissione di messaggi di chiusura"
  - "arresto di SQL Server"
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Trasmissione di un messaggio di chiusura (prompt dei comandi)
  Questo argomento illustra come trasmettere un messaggio di arresto in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando il comando **net send** . Specificare nel messaggio l'orario di arresto dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , in modo da consentire agli utenti di completare le attività in corso.  
  
##  <a name="SSMSProcedure"></a>  
  
#### Per trasmettere un messaggio di arresto  
  
1.  Dal prompt dei comandi digitare quanto segue:  
  
     **net send /users "messaggio"**  
  
     L'opzione **/users** specifica che il messaggio verrà inviato a tutti gli utenti connessi al server  
  
> [!NOTE]  
>  Per usare il comando **net send** è necessario che sia in esecuzione il servizio Messenger sia sul computer che invia il messaggio sia sui computer che dovranno riceverlo. In Windows Server 2003 il servizio Messenger è disabilitato per impostazione predefinita. Per informazioni sul comando **net send**, vedere la documentazione di Windows.  
  
 In alcune reti potrebbe essere più appropriato contattare gli utenti per posta elettronica o telefonicamente. Utilizzare Monitor attività per determinare quali utenti sono attualmente connessi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per informazioni su Monitoraggio attività, vedere [Monitoraggio attività](../../relational-databases/performance-monitor/activity-monitor.md) e [Aprire Monitoraggio attività &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).  
  
## Vedere anche  
 [Avviare, arrestare, sospendere, riprendere, riavviare il motore di database, SQL Server Agent o SQL Server Browser](../../database-engine/configure-windows/start, stop, pause, resume, restart sql server services.md)  
  
  