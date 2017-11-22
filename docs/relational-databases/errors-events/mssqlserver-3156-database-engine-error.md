---
title: MSSQLSERVER_3156 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fae24a904f64ca47afba7874148e62bb4ebc2067
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3156"></a>MSSQLSERVER_3156
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|3156|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LDDB_CANT_WRITE|  
|Testo del messaggio|Impossibile ripristinare il file '%ls' in '%ls'. Utilizzare WITH MOVE per identificare un percorso valido per il file.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio generico identifica i nomi file logici o fisici dei file di cui è non stato possibile eseguire il ripristino a causa di un problema relativo al percorso specificato.  
  
### <a name="possible-causes"></a>Possibili cause  
Tra le cause possibili sono incluse le seguenti:  
  
-   Potrebbe essere necessario l'accesso alla directory di Windows specificata.  
  
-   Il percorso potrebbe essere stato digitato in modo non corretto oppure è possibile che il percorso specificato non esista.  
  
-   Il nome file potrebbe essere utilizzato da un file che non può essere sovrascritto.  
  
## <a name="user-action"></a>Azione dell'utente  
Esaminare i log degli errori alla ricerca di altri messaggi contenenti ulteriori dettagli.  
  
Correggere il problema relativo al percorso specificato, ad esempio concedendo l'accesso, oppure utilizzare l'opzione WITH MOVE nell'istruzione RESTORE per rilocare il file.  
  
## <a name="see-also"></a>Vedere anche  
[Ripristinare un database in una nuova posizione &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Ripristinare i file in una nuova posizione &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
