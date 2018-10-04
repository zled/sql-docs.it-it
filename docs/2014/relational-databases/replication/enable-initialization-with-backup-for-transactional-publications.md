---
title: Abilitare l'inizializzazione con un Backup per le pubblicazioni transazionali (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f7aa6ce1627250d217cce8778c099a50e668cbd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056731"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a>Abilitazione dell'inizializzazione con un backup per le pubblicazioni transazionali (SQL Server Management Studio)
  Per inizializzare una sottoscrizione di una pubblicazione transazionale da un backup, attivare la pubblicazione in modo da consentire l'inizializzazione da un backup e quindi specificare le informazioni di backup durante la creazione della sottoscrizione:  
  
-   Abilitare la pubblicazione nella pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
-   Specificare le informazioni di backup con la stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Per altre informazioni sui parametri necessari per **sp_addsubscription**, vedere [Inizializzare una sottoscrizione transazionale da un backup &#40;programmazione Transact-SQL della replica&#41;](initialize-a-transactional-subscription-from-a-backup.md).  
  
### <a name="to-enable-initialization-with-a-backup"></a>Per attivare l'inizializzazione con un backup  
  
1.  Nella pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** selezionare il valore **Vero** per l'opzione **Consenti inizializzazione dai file di backup**.  
  
## <a name="see-also"></a>Vedere anche  
 [Inizializzare una sottoscrizione transazionale senza uno snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
