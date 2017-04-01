---
title: "Specifica di un percorso alternativo per la cartella snapshot (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
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
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Specifica di un percorso alternativo per la cartella snapshot (SQL Server Management Studio)
  Specificare un percorso alternativo snapshot sul **Snapshot** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Per specificare un percorso alternativo per lo snapshot  
  
1.  Nel **Snapshot** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo:  
  
    1.  Selezionare **inserire file nella cartella seguente**, quindi fare clic su **Sfoglia** per passare a una directory o immettere il percorso della directory in cui devono essere archiviati i file di snapshot.  
  
        > [!NOTE]  
        >  L'agente snapshot deve disporre delle autorizzazioni di scrittura per la directory specificata, mentre l'agente di distribuzione o l'agente di merge deve disporre delle autorizzazioni di lettura. Se si utilizzano sottoscrizioni pull, è necessario specificare una directory condivisa come un percorso universal naming convention (UNC), ad esempio \\\computername\snapshot. Per ulteriori informazioni, vedere [sicurezza della cartella Snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
    2.  Deselezionare **inserire file nella cartella predefinita** Se non sono necessari i file di snapshot di essere scritti in entrambe le posizioni.  
  
     Per comprimere i file di snapshot, selezionare **comprimere i file di snapshot in questa posizione**. La compressione viene in genere utilizzata per le connessioni a larghezza di banda ridotta e per i percorsi alternativi per lo snapshot nei supporti rimovibili, ad esempio un CD-ROM.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## Vedere anche  
 [Posizioni alternative della cartella snapshot](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Configurare le proprietà dello Snapshot & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Specificare la posizione predefinita degli Snapshot & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Inizializzazione di una sottoscrizione con uno snapshot](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  