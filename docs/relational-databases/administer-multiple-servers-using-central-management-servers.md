---
title: "Amministrare pi&#249; server tramite server di gestione centrale | Microsoft Docs"
ms.custom: ""
ms.date: "08/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "query multiserver"
  - "server di gestione centrale"
  - "amministrazione multiserver [SQL Server]"
  - "server master [SQL Server], server di gestione centrale"
  - "configurazione di destinazione [SQL Server]"
  - "configurazione server [SQL Server]"
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# Amministrare pi&#249; server tramite server di gestione centrale
  È possibile amministrare più server designando server di gestione centrale e creando gruppi di server.  
  
## Che cos’è un server di gestione centrale e cosa sono i gruppi di server?  
 Un'istanza di SQL Server definita come server di gestione centrale gestisce i gruppi di server che contengono le informazioni sulla connessione per una o più istanze. Le istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] e i criteri della gestione basata su criteri possono essere eseguiti contemporaneamente in più gruppi di server. È inoltre possibile visualizzare i file di log in istanze gestite tramite un server di gestione centrale. 
 
 Un server di gestione centrale è essenzialmente un repository centrale contenente un elenco di server gestiti. Le versioni precedenti a [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] non possono essere designate come server di gestione centrale.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] le istruzioni possono inoltre essere eseguite su gruppi di server locali nella finestra Server registrati.  
  
## Creare un server di gestione centrale e gruppi di server 
 Per creare un server di gestione centrale e gruppi di server, usare la finestra **Server registrati** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Notare che il server di gestione centrale non può essere un membro di uno dei gruppi che gestisce. 
 
 Per altre informazioni su come creare server di gestione centrale e gruppi di server, vedere [Creazione di un server di gestione centrale e di un gruppo di server &#40;SQL Server Management Studio&#41;](../tools/sql-server-management-studio/create-a-central-management-server-and-server-group.md).  
  
## Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  