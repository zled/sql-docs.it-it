---
title: Eseguire gli script prima e dopo l'applicazione dello snapshot | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4352dbbbabdbd2d1aa8aa9b724f4e0aa41720bbd
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="execute-scripts-before-and-after-a-snapshot-is-applied"></a>Eseguire gli script prima e dopo l'applicazione dello snapshot
  Specificare uno script facoltativo da eseguire prima o dopo l'applicazione dello snapshot nella pagina **Snapshot** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Queste opzioni non sono disponibili se l'opzione **Formato snapshot** è impostata su **Carattere**.  
  
### <a name="to-execute-a-script-before-or-after-a-snapshot-is-applied"></a>Per eseguire uno script prima o dopo l'applicazione di uno snapshot  
  
1.  Nella pagina **Snapshot** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**:  
  
    -   Per specificare uno script da eseguire prima dell'applicazione dello snapshot, fare clic su **Sfoglia** per passare allo script oppure immettere un percorso per lo script nella casella di testo **Prima di applicare lo snapshot, esegui lo script seguente** .  
  
        > [!NOTE]  
        >  È necessario che l'agente di distribuzione o l'agente di merge disponga delle autorizzazioni di lettura per la directory specificata. Se si usano sottoscrizioni pull, è necessario specificare una directory condivisa come percorso UNC (Universal Naming Convention), ad esempio \\\nomecomputer\script\scriptpersonali.sql.  
  
    -   Per specificare uno script da eseguire dopo l'applicazione dello snapshot, fare clic su **Sfoglia** per passare allo script oppure immettere un percorso UNC per lo script nella casella di testo **Dopo l'applicazione dello snapshot, esegui lo script seguente** .  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare le proprietà dello snapshot &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Modificare le proprietà di pubblicazioni e articoli](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Eseguire gli script prima e dopo l'applicazione dello snapshot](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Inizializzare una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
