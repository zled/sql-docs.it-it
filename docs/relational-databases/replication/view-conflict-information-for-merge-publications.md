---
title: Visualizzare le informazioni sui conflitti per le pubblicazioni di tipo merge | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- sp_helpmergeconflictrows
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
- sp_helpmergearticleconflicts
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 754a5c4bed2ba321987c4b0b820f4ad821369f42
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351686"
---
# <a name="view-conflict-information-for-merge-publications"></a>Visualizzare le informazioni sui conflitti per le pubblicazioni di tipo merge
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Quando si risolve un conflitto in una replica di tipo merge, i dati della riga non confermata vengono scritti in una tabella di conflitti. I dati relativi al conflitto possono essere visualizzati a livello di programmazione tramite le stored procedure di replica. Per altre informazioni, vedere [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### <a name="to-view-conflict-information-and-losing-row-data-for-all-types-of-conflicts"></a>Per visualizzare informazioni sul conflitto e i dati delle righe non confermate per tutti i tipi di conflitti  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Notare i valori delle colonne seguenti nel set di risultati:  
  
    -   **centralized_conflicts** : 1 indica che le righe con conflitti vengono archiviate nel server di pubblicazione, mentre 0 indica che le righe con conflitti non vengono archiviate nel server di pubblicazione.  
  
    -   **decentralized_conflicts** : 1 indica che le righe con conflitti vengono archiviate nel Sottoscrittore, mentre 0 indica che le righe con conflitti non vengono archiviate nel Sottoscrittore.  
  
        > [!NOTE]  
        >  Per definire il comportamento della registrazione dei conflitti relativi a una pubblicazione di tipo merge, viene utilizzato il parametro **@conflict_logging** di [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Il parametro **@centralized_conflicts** è deprecato.  
  
     Nella tabella seguente sono descritti i valori di queste colonne sulla base del valore specificato per **@conflict_logging**.  
  
    |Valore della proprietà @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher**|1|0|  
    |**subscriber**|0|1|  
    |**both**|1|1|  
  
2.  Nel database di pubblicazione del server di pubblicazione o nel database di sottoscrizione del Sottoscrittore eseguire [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Specificare il valore **@publication** per restituire le informazioni sui conflitti solo per articoli che appartengono a una pubblicazione specifica. In tal modo per gli articoli con conflitti verranno restituite le informazioni della tabella dei conflitti. Notare il valore di **conflict_table** per qualsiasi articolo di interesse. Se il valore di **conflict_table** per un articolo è NULL, eliminare i conflitti che si sono verificati in questo articolo.  
  
3.  (Facoltativo) Rivedere le righe con conflitti presenti negli articoli di interesse. A seconda dei valori di **centralized_conflicts** e **decentralized_conflicts** ottenuti al passaggio 1, eseguire una delle operazioni seguenti:  
  
    -   Nel database di pubblicazione del server di pubblicazione eseguire [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Specificare una tabella dei conflitti per l'articolo (ottenuta al passaggio 1) per **@conflict_table**. (Facoltativo) Specificare il valore **@publication** per limitare le informazioni restituite sui conflitti a una pubblicazione specifica. In tal modo verranno restituiti i dati della riga e altre informazioni sulla riga non confermata.  
  
    -   Nel database di sottoscrizione del Sottoscrittore eseguire [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Specificare una tabella dei conflitti per l'articolo (ottenuta al passaggio 1) per **@conflict_table**. In tal modo verranno restituiti i dati della riga e altre informazioni sulla riga non confermata.  
  
### <a name="to-view-information-only-on-conflicts-where-the-delete-failed"></a>Per visualizzare informazioni solo sui conflitti in cui non è stata eseguita l'eliminazione  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Notare i valori delle colonne seguenti nel set di risultati:  
  
    -   **centralized_conflicts** : 1 indica che le righe con conflitti vengono archiviate nel server di pubblicazione, mentre 0 indica che le righe con conflitti non vengono archiviate nel server di pubblicazione.  
  
    -   **decentralized_conflicts** : 1 indica che le righe con conflitti vengono archiviate nel Sottoscrittore, mentre 0 indica che le righe con conflitti non vengono archiviate nel Sottoscrittore.  
  
        > [!NOTE]  
        >  Per definire il comportamento della registrazione dei conflitti relativi a una pubblicazione di tipo merge, viene utilizzato il parametro **@conflict_logging** di [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Il parametro **@centralized_conflicts** è deprecato.  
  
2.  Nel database di pubblicazione del server di pubblicazione o nel database di sottoscrizione del Sottoscrittore eseguire [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Specificare il valore **@publication** per restituire le informazioni della tabella dei conflitti solo per articoli che appartengono a una pubblicazione specifica. In tal modo per gli articoli con conflitti verranno restituite le informazioni della tabella dei conflitti. Notare il valore di **source_object** per qualsiasi articolo di interesse. Se il valore di **conflict_table** per un articolo è NULL, eliminare i conflitti che si sono verificati in questo articolo.  
  
3.  (Facoltativo) Rivedere le informazioni sui conflitti per i conflitti di eliminazione. A seconda dei valori di **centralized_conflicts** e **decentralized_conflicts** ottenuti al passaggio 1, eseguire una delle operazioni seguenti:  
  
    -   Nel database di pubblicazione del server di pubblicazione eseguire [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Specificare il nome della tabella di origine (ottenuta al passaggio 1) nella quale si verifica il conflitto per **@source_object**. (Facoltativo) Specificare il valore **@publication** per limitare le informazioni restituite sui conflitti a una pubblicazione specifica. In tal modo verranno restituite solo le informazioni sui conflitti di eliminazione archiviate nel server di pubblicazione.  
  
    -   Nel database di sottoscrizione del Sottoscrittore eseguire [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Specificare il nome della tabella di origine (ottenuta al passaggio 1) nella quale si verifica il conflitto per **@source_object**. (Facoltativo) Specificare il valore **@publication** per limitare le informazioni restituite sui conflitti a una pubblicazione specifica. In tal modo verranno restituite solo le informazioni sui conflitti di eliminazione archiviate nel Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
