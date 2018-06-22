---
title: Comando Events Data Columns | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Command Events event category
ms.assetid: 7169f1e2-c6be-4d8c-b147-25719b84bc2c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 290c9ca23a71c43d16f29e0bd0e6d1f595b6df14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054607"
---
# <a name="command-events-data-columns"></a>Colonne di dati degli eventi di comando
  Nella tabella seguente vengono descritte le colonne di dati per ogni classe di evento della categoria di eventi **Eventi di comando** .  
  
 La categoria di eventi **Eventi di comando** include le classi di eventi seguenti:  
  
-   [Classe Command Begin](#bkmk_1)  
  
-   [Classe Command End](#bkmk_2)  
  
 Nelle tabelle seguenti vengono elencate le colonne di dati per ognuna di queste classi di eventi.  
  
##  <a name="bkmk_1"></a> Colonne di dati della classe Command Begin  
  
|Colonna di dati|Description|  
|-----------------|-----------------|  
|ConnectionID|Contiene l'ID di connessione univoco associato all'evento di comando.|  
|TextData|Contiene i dati di tipo text associati all'evento di comando.|  
|ServerName|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di comando.|  
|CurrentTime|Contiene l'ora corrente dell'evento di comando.|  
|DatabaseName|Contiene il nome del database in cui è in esecuzione il comando.|  
|EventSubclass|Contiene la classe di evento dell'evento di comando. I valori possibili sono:<br /><br /> 0: Create<br />1: Alter<br />2: Delete<br />3: Process<br />4: DesignAggregations<br />5: WBInsert<br />6: WBUpdate<br />7: WBDelete<br />8: Backup<br />9: Restore<br />10: MergePartitions<br />11: Subscribe<br />12: Batch<br />13: BeginTransaction<br />14: CommitTransaction<br />15: RollbackTransaction<br />16: GetTransactionState<br />17: Cancel<br />18: Synchronize<br />19: Import80MiningModels<br />20: Attach<br />21: Detach<br />22: SetAuthContext<br />23: ImageLoad<br />24: ImageSave<br />10000: Altro|  
|NTUserName|Contiene il nome utente di Windows associato all'evento di comando. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|RequestProperties|Contiene le proprietà della richiesta XMLA (XML for Analysis) associata all'evento di comando.|  
|SPID|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di comando. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|StartTime|Contiene l'ora, se disponibile, in cui è iniziato l'evento di comando.|  
|SessionType|Contiene l'entità che ha provocato l'operazione.|  
|NTDomainName|Contiene l'account di dominio di Windows associato all'evento di autorizzazione per l'oggetto.|  
|ClientProcessID|Contiene l'ID del processo client univoco associato all'evento di comando.|  
  
##  <a name="bkmk_2"></a> Colonne di dati della classe Command End  
  
|Colonna di dati|Description|  
|-----------------|-----------------|  
|ConnectionID|Contiene l'ID di connessione univoco associato all'evento di comando.|  
|TextData|Contiene i dati di tipo text associati all'evento di comando.|  
|ServerName|Contiene il nome dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di comando.|  
|CurrentTime|Contiene l'ora corrente dell'evento di comando. Per il filtro, i formati sono *AAAA*-*MM*-*GG* e *AAAA*-*MM*-*GG HH*:*MM*:*SS*.|  
|DatabaseName|Contiene il nome del database in cui è in esecuzione il comando.|  
|Duration|Contiene un valore approssimativo dell'intervallo di tempo tra l'evento di inizio comando e l'evento di fine comando.|  
|EndTime|Contiene l'ora di fine dell'evento di comando. Per il filtro, i formati sono *AAAA*-*MM*-*GG* e *AAAA*-*MM*-*GG HH*:*MM*:*SS*.|  
|EventSubclass|Contiene la classe di evento dell'evento di comando. I valori possibili sono:<br /><br /> 0: Create<br />1: Alter<br />2: Delete<br />3: Process<br />4: DesignAggregations<br />5: WBInsert<br />6: WBUpdate<br />7: WBDelete<br />8: Backup<br />9: Restore<br />10: MergePartitions<br />11: Subscribe<br />12: Batch<br />13: BeginTransaction<br />14: CommitTransaction<br />15: RollbackTransaction<br />16: GetTransactionState<br />17: Cancel<br />18: Synchronize<br />19: Import80MiningModels<br />20: Attach<br />21: Detach<br />22: SetAuthContext<br />23: ImageLoad<br />24: ImageSave<br />10000: Altro|  
|NTCanonicalUserName|Contiene il nome utente di Windows associato all'evento di comando. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|NTUserName|Contiene l'account utente di Windows associato all'evento di comando.|  
|SPID|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di comando. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|StartTime|Contiene l'ora, se disponibile, in cui è iniziato l'evento di fine comando.|  
|CPUTime|Contiene la quantità di tempo CPU, in millisecondi, utilizzata dal processo tra l'evento di inizio comando e quello di fine comando.|  
|Errore|Contiene il numero di errore di eventuali errori associati all'evento di comando.|  
|Severity|Contiene il livello di gravità di un'eccezione associata all'evento di comando. I valori possibili sono:<br /><br /> 0 = Esito positivo<br /><br /> 1 = Messaggio informativo<br /><br /> 2 = Avviso<br /><br /> 3 = Errore|  
|Esito positivo|Contiene informazioni sull'esito positivo o negativo dell'evento di comando. I valori possibili sono:<br /><br /> 0 = esito negativo<br /><br /> 1 = esito positivo|  
|SessionType|Contiene l'entità che ha provocato l'operazione associata all'evento di fine comando.|  
|NTDomainName|Contiene l'account di dominio di Windows associato all'evento di comando.|  
|ClientProcessID|Contiene l'ID del processo client univoco associato all'evento di comando.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi Eventi di comando](command-events-event-category.md)  
  
  