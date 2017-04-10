---
title: "Impostazione della posizione predefinita degli snapshot (SQL Server Management Studio) | Microsoft Docs"
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
  - "snapshot [replica di SQL Server], posizioni predefinite"
  - "posizioni predefinite per gli snapshot"
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Impostazione della posizione predefinita degli snapshot (SQL Server Management Studio)
  Specificare la posizione predefinita degli snapshot sul **cartella Snapshot** pagina della configurazione guidata distribuzione. Per ulteriori informazioni sull'utilizzo di questa procedura guidata, vedere [Configura pubblicazione e distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md). Se si crea una pubblicazione in un server che non è configurato come server di distribuzione, specificare una posizione predefinita degli snapshot sul **cartella Snapshot** pagina della procedura guidata nuova pubblicazione. Per ulteriori informazioni sull'utilizzo di questa procedura guidata, vedere [creare una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md).  
  
 Modificare la posizione predefinita degli snapshot nel **editori** pagina della **proprietà server di distribuzione - \< distributore>** la finestra di dialogo. Per ulteriori informazioni, vedere [visualizzare e modificare server di distribuzione e le proprietà server di pubblicazione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md). Impostare la cartella snapshot per ogni pubblicazione nel **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per altre informazioni, vedere [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Per modificare la posizione predefinita degli snapshot  
  
1.  Nel **editori** pagina della **proprietà server di distribuzione - \< server di distribuzione>** finestra di dialogo, fare clic sul pulsante delle proprietà (**...**) per il server di pubblicazione per cui si desidera modificare la posizione predefinita degli snapshot.  
  
2.  Nel **proprietà server di pubblicazione - \< Publisher>** finestra di dialogo immettere un valore per il **cartella Snapshot predefinita** proprietà.  
  
    > [!NOTE]  
    >  L'agente snapshot deve disporre delle autorizzazioni di scrittura per la directory specificata, mentre l'agente di distribuzione o l'agente di merge deve disporre delle autorizzazioni di lettura. Se si utilizzano sottoscrizioni pull, è necessario specificare una directory condivisa come un percorso universal naming convention (UNC), ad esempio \\\computername\snapshot. Per ulteriori informazioni, vedere [sicurezza della cartella Snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Vedere anche  
 [Posizioni alternative della cartella snapshot](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  