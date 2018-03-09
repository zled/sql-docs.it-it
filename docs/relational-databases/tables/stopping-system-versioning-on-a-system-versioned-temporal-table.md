---
title: Arresto del controllo delle versioni di sistema in una tabella temporale con controllo delle versioni di sistema | Microsoft Docs
ms.custom: 
ms.date: 10/11/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dddd707e-bfb1-44ff-937b-a84c5e5d1a94
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2fc598778c154fa0439fc3534243ff4cb2a7f0b1
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="stopping-system-versioning-on-a-system-versioned-temporal-table"></a>Arresto del controllo delle versioni di sistema in una tabella temporale con controllo delle versioni di sistema
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  È possibile arrestare il controllo delle versioni di sistema in una tabella temporale in modo temporaneo o permanente.   
È possibile farlo impostando la clausola **SYSTEM_VERSIONING** su **OFF**.  
  
## <a name="setting-systemversioning--off"></a>Impostazione di SYSTEM_VERSIONING = OFF  
 Arrestare il controllo delle versioni di sistema per eseguire specifiche operazioni di manutenzione sulla tabella temporale o se la tabella con controllo delle versioni non è più necessaria. Questa operazione produce due tabelle indipendenti:  
  
-   Tabella corrente con definizione del periodo  
  
-   Tabella cronologica sotto forma di tabella normale  
  
### <a name="important-remarks"></a>Note importanti  
  
-   Non si verifica alcuna perdita di dati quando si imposta  **SYSTEM_VERSIONING = OFF** o si elimina il periodo **SYSTEM_TIME** .  
  
-   Quando si imposta **SYSTEM_VERSIONING = OFF** e non si rimuove il periodo **SYSTEM_TIME** , il sistema continua ad aggiornare le colonne del periodo per ogni operazione di inserimento e di aggiornamento. L'eliminazione di elementi nella tabella corrente è definitiva.  
  
-   Eliminare il periodo **SYSTEM_TIME** per rimuovere completamente le colonne del periodo.  
  
-   Quando si imposta **SYSTEM_VERSIONING = OFF**, tutti gli utenti con autorizzazioni sufficienti possono modificare lo schema e il contenuto della tabella di cronologia o anche eliminare definitivamente tale tabella.  
  
### <a name="permanently-remove-systemversioning"></a>Rimuovere in modo definitivo SYSTEM_VERSIONING  
 Questo esempio rimuove in modo definitivo SYSTEM_VERSIONING e le colonne del periodo. La rimozione delle colonne del periodo è facoltativa.  
  
```  
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
/*Optionally, DROP PERIOD if you want to revert temporal table to a non-temporal*/   
ALTER TABLE dbo.Department   
DROP PERIOD FOR SYSTEM_TIME;  
  
```  
  
### <a name="temporarily-remove-systemversioning"></a>Rimuovere in modo temporaneo SYSTEM_VERSIONING  
 L'elenco seguente include le operazioni per cui è richiesto che il controllo delle versioni di sistema sia impostato su **OFF**:  
  
-   Rimozione dei dati non necessari dalla cronologia (**DELETE** o **TRUNCATE**)  
  
-   Rimozione dei dati dalla tabella corrente senza il controllo delle versioni (**DELETE**, **TRUNCATE**)  
  
-   **SWITCH OUT** della partizione dalla tabella corrente  
  
-   **SWITCH IN** della partizione nella tabella di cronologia  
  
 Questo esempio arresta temporaneamente SYSTEM_VERSIONING per consentire di eseguire operazioni di manutenzione specifiche. Se si arresta temporaneamente il controllo delle versioni come prerequisito per la manutenzione della tabella, si consiglia di eseguire questa operazione all'interno di una transazione per mantenere la coerenza dei dati.  
  
```  
BEGIN TRAN   
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
TRUNCATE TABLE [History].[DepartmentHistory]   
WITH (PARTITIONS (1,2))   
ALTER TABLE dbo.Department SET    
(   
SYSTEM_VERSIONING = ON (HISTORY_TABLE = History.DepartmentHistory)   
);   
COMMIT ;  
  
```  
  
## <a name="did-this-article-help-you-were-listening"></a>Questo articolo è stato utile? Commenti e suggerimenti  
 Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Stopping%20System-Versioning%20on%20a%20System-Version%20Temporal%20Table%20page)  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle temporali](../../relational-databases/tables/temporal-tables.md)   
 [Introduzione alle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tabelle temporali con controllo delle versioni di sistema con tabelle con ottimizzazione per la memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Creazione di una tabella temporale con controllo delle versioni di sistema](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)   
 [Modifica dei dati in una tabella temporale con controllo delle versioni di sistema](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)   
 [Query sui dati in una tabella temporale con controllo delle versioni di sistema](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)   
 [Modifica dello schema di una tabella temporale con controllo delle versioni di sistema](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)  
  
  
