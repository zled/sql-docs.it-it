---
title: "Esecuzione di script durante la sincronizzazione (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sincronizzazione [replica di SQL Server], script"
  - "script [replica di SQL Server], sincronizzazione e"
  - "sp_addscriptexec"
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Esecuzione di script durante la sincronizzazione (programmazione Transact-SQL della replica)
  La replica supporta l'esecuzione di script su richiesta per i Sottoscrittori di pubblicazioni transazionali e di tipo merge. Questa funzionalità lo script viene copiato nella directory di lavoro di replica e quindi utilizza **sqlcmd** applicare lo script nel Sottoscrittore. Per impostazione predefinita, se si verifica un errore durante l'applicazione dello script per una sottoscrizione di una pubblicazione transazionale, l'agente di distribuzione verrà arrestato. È possibile specificare uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] da eseguire a livello di programmazione tramite le stored procedure di replica.  
  
### Per specificare uno script da eseguire per tutti i Sottoscrittori di una pubblicazione snapshot, transazionale o di tipo merge  
  
1.  Comporre e testare lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] che verrà eseguito su richiesta.  
  
2.  Salvare il file script in un percorso in cui sia accessibile all'agente snapshot per la pubblicazione.  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addscriptexec & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md). Specificare **@publication**, il nome del file di script con il percorso UNC completo creato nel passaggio 2 per **@scriptfile**, e uno dei seguenti valori per **@skiperror**:  
  
    -   **0** -l'agente verrà arrestato l'esecuzione dello script se si verifica un errore.  
  
    -   **1** -l'agente registrerà gli errori e continuare l'esecuzione dello script quando si verificano errori.  
  
4.  Lo script specificato verrà eseguito in ogni Sottoscrittore la volta successiva che l'agente verrà eseguito per sincronizzare la sottoscrizione.  
  
## Vedere anche  
 [Sincronizzare i dati](../../relational-databases/replication/synchronize-data.md)  
  
  