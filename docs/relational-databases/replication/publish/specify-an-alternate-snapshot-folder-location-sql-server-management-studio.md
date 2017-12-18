---
title: Specificare un percorso alternativo per la cartella snapshot (SQL Server Management Studio) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
caps.latest.revision: "42"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9229cda32cf6d4074a969713452c5c084b9d4d63
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="specify-an-alternate-snapshot-folder-location-sql-server-management-studio"></a>Specifica di un percorso alternativo per la cartella snapshot (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Specificare un percorso alternativo per lo snapshot nella pagina **Snapshot** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-specify-an-alternate-snapshot-location"></a>Per specificare un percorso alternativo per lo snapshot  
  
1.  Nella pagina **Snapshot** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**:  
  
    1.  Selezionare **Inserisci i file nella cartella seguente**e quindi fare clic su **Sfoglia** per passare a una directory oppure immettere il percorso della directory in cui devono essere archiviati i file di snapshot.  
  
        > [!NOTE]  
        >  L'agente snapshot deve disporre delle autorizzazioni di scrittura per la directory specificata, mentre l'agente di distribuzione o l'agente di merge deve disporre delle autorizzazioni di lettura. Se si usano sottoscrizioni pull, è necessario specificare una directory condivisa come percorso UNC (Universal Naming Convention), ad esempio \\\nomecomputer\snapshot. Per altre informazioni, vedere [Proteggere la cartella snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
    2.  Deselezionare **Inserisci i file nella cartella predefinita** a meno che non sia necessario scrivere i file di snapshot in entrambe le posizioni.  
  
     Per comprimere i file di snapshot, selezionare **Comprimi i file di snapshot in questa cartella**. La compressione viene in genere utilizzata per le connessioni a larghezza di banda ridotta e per i percorsi alternativi per lo snapshot nei supporti rimovibili, ad esempio un CD-ROM.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Posizioni alternative della cartella snapshot](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Configurare le proprietà dello snapshot &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Specificare la posizione predefinita degli snapshot &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Modificare le proprietà di pubblicazioni e articoli](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Inizializzare una sottoscrizione con uno snapshot](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
