---
title: Abilitare l&quot;inizializzazione con un backup per le pubblicazioni transazionali | Microsoft Docs
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
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 954362e3ef6728df6f497bcb337aa234718cdee8
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="enable-initialization-with-backup-for-transactional-publications"></a>Abilitare l'inizializzazione con un backup per le pubblicazioni transazionali
  Per inizializzare una sottoscrizione di una pubblicazione transazionale da un backup, attivare la pubblicazione in modo da consentire l'inizializzazione da un backup e quindi specificare le informazioni di backup durante la creazione della sottoscrizione:  
  
-   Abilitare la pubblicazione nella pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Specificare le informazioni di backup con la stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Per altre informazioni sui parametri necessari per **sp_addsubscription**, vedere [Inizializzare una sottoscrizione transazionale da un backup &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md).  
  
### <a name="to-enable-initialization-with-a-backup"></a>Per attivare l'inizializzazione con un backup  
  
1.  Nella pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** selezionare il valore **Vero** per l'opzione **Consenti inizializzazione dai file di backup**.  
  
## <a name="see-also"></a>Vedere anche  
 [Inizializzare una sottoscrizione transazionale senza uno snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
