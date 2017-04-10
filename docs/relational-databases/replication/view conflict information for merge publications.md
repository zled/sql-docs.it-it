---
title: "Visualizzazione delle informazioni sui conflitti per le pubblicazioni di tipo merge (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "risoluzione di conflitti di replica di tipo merge [replica di SQL Server], visualizzazione di conflitti"
  - "sp_helpmergeconflictrows"
  - "visualizzazioni di informazioni sui conflitti"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
  - "sp_helpmergearticleconflicts"
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Visualizzazione delle informazioni sui conflitti per le pubblicazioni di tipo merge (programmazione Transact-SQL della replica)
  Quando si risolve un conflitto in una replica di tipo merge, i dati della riga non confermata vengono scritti in una tabella di conflitti. I dati relativi al conflitto possono essere visualizzati a livello di programmazione tramite le stored procedure di replica. Per altre informazioni, vedere [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### Per visualizzare informazioni sul conflitto e i dati delle righe non confermate per tutti i tipi di conflitti  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Notare i valori delle colonne seguenti nel set di risultati:  
  
    -   **centralized_conflicts** -1 indica che le righe con conflitti vengono archiviate nel server di pubblicazione, mentre 0 indica che le righe con conflitti non vengono archiviate nel server di pubblicazione.  
  
    -   **decentralized_conflicts** -1 indica che le righe con conflitti vengono archiviate nel sottoscrittore e 0 indica che le righe con conflitti non vengono archiviate nel Sottoscrittore.  
  
        > [!NOTE]  
        >  Il comportamento di registrazione dei conflitti di una pubblicazione di tipo merge viene impostato tramite la **@conflict_logging** parametro [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Utilizzare il **@centralized_conflicts** parametro è stato deprecato.  
  
     Nella tabella seguente vengono descritti i valori di queste colonne in base al valore specificato per **@conflict_logging**.  
  
    |Valore di @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher**|1|0|  
    |**sottoscrittore**|0|1|  
    |**both**|1|1|  
  
2.  Entrambi i server di pubblicazione nel database di pubblicazione o nel database di sottoscrizione del sottoscrittore eseguire [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Specificare un valore per **@publication** per restituire solo le informazioni sui conflitti per articoli che appartengono a una pubblicazione specifica. In tal modo per gli articoli con conflitti verranno restituite le informazioni della tabella dei conflitti. Prendere nota del valore di **conflict_table** per qualsiasi articolo di interesse. Se il valore di **conflict_table** per un articolo è NULL, eliminare i conflitti si sono verificati in questo articolo.  
  
3.  (Facoltativo) Rivedere le righe con conflitti presenti negli articoli di interesse. A seconda dei valori di **centralized_conflicts** e **decentralized_conflicts** dal passaggio 1, effettuare una delle operazioni seguenti:  
  
    -   Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Specificare una tabella dei conflitti dell'articolo (ottenuto nel passaggio 1) per **@conflict_table**. (Facoltativo) Specificare un valore di **@publication** per limitare le informazioni sui conflitti restituite per una pubblicazione specifica. In tal modo verranno restituiti i dati della riga e altre informazioni sulla riga non confermata.  
  
    -   Nel database di sottoscrizione del sottoscrittore, eseguire [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Specificare una tabella dei conflitti dell'articolo (ottenuto nel passaggio 1) per **@conflict_table**. In tal modo verranno restituiti i dati della riga e altre informazioni sulla riga non confermata.  
  
### Per visualizzare informazioni solo sui conflitti in cui non è stata eseguita l'eliminazione  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Notare i valori delle colonne seguenti nel set di risultati:  
  
    -   **centralized_conflicts** -1 indica che le righe con conflitti vengono archiviate nel server di pubblicazione, mentre 0 indica che le righe con conflitti non vengono archiviate nel server di pubblicazione.  
  
    -   **decentralized_conflicts** -1 indica che le righe con conflitti vengono archiviate nel sottoscrittore e 0 indica che le righe con conflitti non vengono archiviate nel Sottoscrittore.  
  
        > [!NOTE]  
        >  Il comportamento di registrazione dei conflitti di una pubblicazione di tipo merge viene impostato utilizzando il **@conflict_logging** parametro [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Utilizzare il **@centralized_conflicts** parametro è stato deprecato.  
  
2.  Entrambi i server di pubblicazione nel database di pubblicazione o nel database di sottoscrizione del sottoscrittore eseguire [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Specificare un valore per **@publication** per restituire solo informazioni della tabella dei conflitti per articoli che appartengono a una pubblicazione specifica. In tal modo per gli articoli con conflitti verranno restituite le informazioni della tabella dei conflitti. Prendere nota del valore di **source_object** per qualsiasi articolo di interesse. Se il valore di **conflict_table** per un articolo è NULL, eliminare i conflitti si sono verificati in questo articolo.  
  
3.  (Facoltativo) Rivedere le informazioni sui conflitti per i conflitti di eliminazione. A seconda dei valori di **centralized_conflicts** e **decentralized_conflicts** dal passaggio 1, effettuare una delle operazioni seguenti:  
  
    -   Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Specificare il nome della tabella di origine (dal passaggio 1) in cui si è verificato il conflitto per **@source_object**. (Facoltativo) Specificare un valore di **@publication** per limitare le informazioni sui conflitti restituite per una pubblicazione specifica. In tal modo verranno restituite solo le informazioni sui conflitti di eliminazione archiviate nel server di pubblicazione.  
  
    -   Nel database di sottoscrizione del sottoscrittore, eseguire [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Specificare il nome della tabella di origine (dal passaggio 1) in cui si è verificato il conflitto per **@source_object**. (Facoltativo) Specificare un valore di **@publication** per limitare le informazioni sui conflitti restituite per una pubblicazione specifica. In tal modo verranno restituite solo le informazioni sui conflitti di eliminazione archiviate nel Sottoscrittore.  
  
## Vedere anche  
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  