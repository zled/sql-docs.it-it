---
title: "Opzioni per gli snapshot | Microsoft Docs"
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
  - "replica snapshot [SQL Server], opzioni"
  - "snapshot [replica di SQL Server], opzioni"
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Opzioni per gli snapshot
  Quando si inizializza una sottoscrizione con uno snapshot è possibile:  
  
-   Specificare una posizione alternativa per la cartella snapshot in aggiunta a quella predefinita o al posto di questa. Per ulteriori informazioni, vedere [percorsi della cartella Snapshot alternativa](../../relational-databases/replication/alternate-snapshot-folder-locations.md).  
  
-   Comprimere gli snapshot per l'archiviazione sui supporti rimovibili o il trasferimento su una rete lenta. Per ulteriori informazioni, vedere [gli snapshot compressi](../../relational-databases/replication/compressed-snapshots.md).  
  
-   Eseguire gli script [!INCLUDE[tsql](../../includes/tsql-md.md)] prima o dopo aver applicato lo snapshot. Per ulteriori informazioni, vedere [eseguire script prima e dopo l'applicazione dello Snapshot](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Trasferire i file di snapshot mediante il protocollo FTP (File Transfer Protocol). Per ulteriori informazioni, vedere [trasferire gli snapshot tramite FTP](../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
## Vedere anche  
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  