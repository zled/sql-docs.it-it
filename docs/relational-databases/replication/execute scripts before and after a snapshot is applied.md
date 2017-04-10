---
title: "Esecuzione di script prima e dopo l&#39;applicazione di uno snapshot (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "snapshot [replica di SQL Server], script"
  - "script [replica di SQL Server], snapshot"
  - "replica snapshot [SQL Server], script"
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Esecuzione di script prima e dopo l&#39;applicazione di uno snapshot (SQL Server Management Studio)
  Specificare uno script facoltativo da eseguire prima o dopo lo snapshot viene applicato sul **Snapshot** pagina la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Queste opzioni non sono disponibili se il **formato dello Snapshot** opzione è impostata su **carattere**.  
  
### Per eseguire uno script prima o dopo l'applicazione di uno snapshot  
  
1.  Nel **Snapshot** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo:  
  
    -   Per specificare uno script da eseguire prima lo snapshot viene applicato, fare clic su **Sfoglia** per passare allo script oppure immettere un percorso dello script nel **prima di applicare lo snapshot, Esegui lo script seguente** casella di testo.  
  
        > [!NOTE]  
        >  È necessario che l'agente di distribuzione o l'agente di merge disponga delle autorizzazioni di lettura per la directory specificata. Se si utilizzano sottoscrizioni pull, è necessario specificare una directory condivisa come un percorso universal naming convention (UNC), ad esempio \\\computername\scripts\myscript.sql.  
  
    -   Per specificare uno script da eseguire dopo aver applicato lo snapshot, fare clic su **Sfoglia** per passare allo script oppure immettere un percorso UNC per lo script nel **dopo aver applicato lo snapshot, Esegui lo script seguente** casella di testo.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Vedere anche  
 [Configurare le proprietà dello Snapshot & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Modifica delle proprietà di pubblicazioni e articoli](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Eseguire gli script prima e dopo l'applicazione dello snapshot](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  