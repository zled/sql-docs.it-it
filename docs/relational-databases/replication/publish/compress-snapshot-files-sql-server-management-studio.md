---
title: "Compressione dei file di snapshot (SQL Server Management Studio) | Microsoft Docs"
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
  - "snapshot [replica di SQL Server], compressi"
  - "replica snapshot [SQL Server], snapshot compressi"
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Compressione dei file di snapshot (SQL Server Management Studio)
  Specificare che i file devono essere compressi nel **Snapshot** pagina la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Per comprimere i file di snapshot  
  
1.  Nel **Snapshot** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo:  
  
    1.  Selezionare **inserire file nella cartella seguente**, quindi fare clic su **Sfoglia** per passare a una directory o immettere il percorso della directory in cui devono essere archiviati i file di snapshot.  
  
        > [!NOTE]  
        >  L'agente snapshot deve disporre delle autorizzazioni di scrittura per la directory specificata, mentre l'agente di distribuzione o l'agente di merge deve disporre delle autorizzazioni di lettura. Se si utilizzano sottoscrizioni pull, è necessario specificare una directory condivisa come un percorso universal naming convention (UNC), ad esempio \\\computername\snapshot. Per ulteriori informazioni, vedere [sicurezza della cartella Snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
    2.  Deselezionare **inserire file nella cartella predefinita** Se non sono necessari i file di snapshot di essere scritti in entrambe le posizioni.  
  
        > [!NOTE]  
        >  Se questa casella di controllo è selezionata, i file archiviati nella cartella predefinita non vengono compressi. I file compressi possono essere archiviati solo nel percorso alternativo specificato nel passaggio precedente.  
  
2.  Selezionare **comprimere i file di snapshot nella cartella**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## Vedere anche  
 [Configurare le proprietà dello Snapshot & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Snapshot compressi](../../../relational-databases/replication/compressed-snapshots.md)   
 [Inizializzazione di una sottoscrizione con uno snapshot](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  