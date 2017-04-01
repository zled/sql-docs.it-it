---
title: "Definire una base di riferimento delle prestazioni | Microsoft Docs"
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
  - "prestazioni database [SQL Server], dati di riferimento"
  - "monitoraggio delle prestazioni [SQL Server], dati di riferimento"
  - "ottimizzazione del database [SQL Server], dati di riferimento"
  - "prestazioni del server [SQL Server], dati di riferimento"
  - "prestazioni [SQL Server], dati di riferimento"
  - "base di riferimento per le prestazioni [SQL Server]"
  - "misurazioni per statistiche di riferimento [SQL Server]"
  - "monitoraggio delle prestazioni del server [SQL Server], definizione di dati di riferimento"
  - "monitoraggio del database [SQL Server], dati di riferimento"
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Definire una base di riferimento delle prestazioni
  Per stabilire se le prestazioni del sistema [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono ottimali, misurare le prestazioni a intervalli di tempo regolari, anche quando non si è verificato alcun problema, in modo da definire una base di riferimento per le prestazioni del server. Confrontare ogni set di misurazioni con i set precedenti.  
  
 Le aree seguenti influiscono sulle prestazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Risorse di sistema (hardware)  
  
-   Architettura di rete  
  
-   Sistema operativo  
  
-   Applicazioni di database  
  
-   Applicazioni client  
  
 Le misurazioni di riferimento devono essere utilizzate almeno per determinare gli elementi seguenti:  
  
-   Orari di punta e di minore attività.  
  
-   Tempi di risposta di query o batch di comandi.  
  
-   Tempi necessari per il completamento di operazioni di backup e ripristino dei database.  
  
 Dopo aver definito una base di riferimento attendibile, confrontare i dati statistici di riferimento con le prestazioni correnti del server. I valori notevolmente superiori o inferiori a quelli di riferimento sono possibili candidati per analisi più approfondite. Tali scostamenti possono indicare aree per cui sono necessari interventi di ottimizzazione o riconfigurazione. In presenza di un aumento dei tempi di esecuzione di un set di query, ad esempio, esaminare le query per verificare se è possibile riscriverle oppure se è necessario aggiungere statistiche di colonna o nuovi indici.  
  
## Vedere anche  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  