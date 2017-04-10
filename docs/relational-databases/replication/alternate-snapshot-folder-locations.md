---
title: "Posizioni alternative della cartella snapshot | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "snapshot [replica di SQL Server], percorsi alternativi delle cartelle"
  - "replica snapshot [replica di SQL Server], percorsi alternativi delle cartelle"
  - "cartelle alternative per snapshot [replica di SQL Server]"
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Posizioni alternative della cartella snapshot
  Le posizioni alternative della cartella snapshot consentono di archiviare i file di snapshot in una posizione aggiuntiva o diversa da quella predefinita, in genere inclusa nel database di distribuzione. Una posizione alternativa può essere un altro server, un'unità di rete oppure un supporto rimovibile, ad esempio un CD-ROM o un disco rimovibile.  
  
 Le posizioni alternative della cartella snapshot vengono archiviate come proprietà della pubblicazione. Dato che la posizione alternativa della cartella snapshot è una proprietà della pubblicazione, l'agente di distribuzione e l'agente di merge sono in grado di individuare la cartella snapshot corretta durante il processo di sincronizzazione.  
  
 Se si desidera specificare una posizione alternativa della cartella snapshot o comprimere i file di snapshot senza creare immediatamente lo snapshot iniziale, è possibile impostare le proprietà della pubblicazione relative alla posizione dello snapshot e quindi eseguire l'agente snapshot per tale pubblicazione. Se tuttavia si modifica la posizione alternativa dopo avere creato lo snapshot iniziale, è possibile che gli snapshot generati per la pubblicazione non vengano ricollocati nella nuova posizione alternativa. In questo caso, a seconda delle impostazioni di pubblicazione, l'agente di merge o l'agente di distribuzione potrebbero non essere in grado di trovare i file di snapshot nella nuova posizione alternativa.  
  
> [!NOTE]  
>  Non si specifica un percorso alternativo (utilizzando la **Proprietà pubblicazione** la finestra di dialogo o [sp_changepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)) che è quello utilizzato per il percorso della cartella snapshot predefinita.  
  
> [!CAUTION]  
>  Non utilizzare contemporaneamente sia WebSync sia percorsi alternativi della cartella snapshot.  
  
 **Per specificare posizioni alternative della cartella snapshot**  
  
-   [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [Specify an Alternate Snapshot Folder Location &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   Replica [!INCLUDE[tsql](../../includes/tsql-md.md)] programming: [configurare le proprietà dello Snapshot & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## Vedere anche  
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Opzioni per gli snapshot](../../relational-databases/replication/snapshot-options.md)  
  
  