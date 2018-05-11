---
title: Colonne di dati di report di stato | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7d8dd07cbaf7ca4b9942b09f0f538a14a883e694
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="progress-reports-data-columns"></a>Colonne di dati degli eventi di report di stato
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoria di eventi di report di stato include le classi di eventi seguenti:  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|5|Progress Report Begin|Inizio del report di stato.|  
|6|Progress Report End|Fine del report di stato.|  
|7|Progress Report Current|Stato corrente del report di stato.|  
|8|Progress Report Error|Errore nel report di stato.|  
  
 Nelle tabelle seguenti vengono elencate le colonne di dati per ognuna di queste classi di eventi.  
  
## <a name="progress-report-begindata-columns"></a>Colonne di dati dell'evento Progress Report Begin  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento. Di seguito sono indicate coppie di valori **Sub Class Id**: **Sub Class Name** validi:<br /><br /> 1: **Process**<br /><br /> 2: **Merge**<br /><br /> 3: **Delete**<br /><br /> 4: **DeleteOldAggregations**<br /><br /> 5: **Rebuild**<br /><br /> 6: **Commit**<br /><br /> 7: **Rollback**<br /><br /> 8: **CreateIndexes**<br /><br /> 9: **CreateTable**<br /><br /> 10: **InsertInto**<br /><br /> 11: **Transaction**<br /><br /> 12: **Initialize**<br /><br /> 13: **Discretize**<br /><br /> 14: **Query**<br /><br /> 15: **CreateView**<br /><br /> 16: **WriteData**<br /><br /> 17: **ReadData**<br /><br /> 18: **GroupData**<br /><br /> 19: **GroupDataRecord**<br /><br /> 20: **BuildIndex**<br /><br /> 21: **Aggregate**<br /><br /> 22: **BuildDecode**<br /><br /> 23: **WriteDecode**<br /><br /> 24: **BuildDMDecode**<br /><br /> 25: **ExecuteSQL**<br /><br /> 26: **ExecuteModifiedSQL**<br /><br /> 27: **Connecting**<br /><br /> 28: **BuildAggsAndIndexes**<br /><br /> 29: **MergeAggsOnDisk**<br /><br /> 30: **BuildIndexForRigidAggs**<br /><br /> 31: **BuildIndexForFlexibleAggs**<br /><br /> 32: **WriteAggsAndIndexes**<br /><br /> 33: **WriteSegment**<br /><br /> 34: **DataMiningProgress**<br /><br /> 35: **ReadBufferFullReport**<br /><br /> 36: **ProactiveCacheConversion**<br /><br /> 37: **Backup**<br /><br /> 38: **Restore**<br /><br /> 39: **Synchronize**<br /><br /> 40: **Build Processing Schedule**<br /><br /> 41: **Detach**<br /><br /> 42: **Attach**<br /><br /> 43: **Analyze\Encode Data**<br /><br /> 44: **Compress Segment**<br /><br /> 45: **Write Table Column**<br /><br /> 46: **Relationship Build Prepare**<br /><br /> 47: **Build Relationship Segment**<br /><br /> 48: **Load**<br /><br /> 49: **Metadata Load**<br /><br /> 50: **Data Load**<br /><br /> 51: **Post Load**<br /><br /> 52: **Metadata traversal during Backup**<br /><br /> 53: **VertiPaq**<br /><br /> 54: **Hierarchy processing**<br /><br /> 55: **Switching dictionary**|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento restituito, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|JobID|7|1|Contiene l'ID processo associato all'evento restituito.|  
|SessionType|8|8|Contiene il tipo di sessione, ovvero l'entità che provoca l'evento, associato all'evento restituito. Per l'elaborazione degli eventi, i valori validi sono:<br /><br /> 1= Utente<br /><br /> 2= Memorizzazione nella cache attiva<br /><br /> 3= Elaborazione lenta|  
|ObjectID|11|8|Contiene l'ID oggetto (una stringa) associato all'evento restituito.|  
|ObjectType|12|1|Contiene il tipo di oggetto.|  
|ObjectName|13|8|Contiene il nome dell'oggetto associato all'evento restituito.|  
|ObjectPath|14|8|Contiene il percorso dell'oggetto per l'oggetto associato all'evento restituito in forma di elenco delimitato da virgole di elementi padre, iniziando dagli elementi padre dell'oggetto.|  
|ObjectReference|15|8|Contiene il riferimento all'oggetto per l'evento restituito, codificato come XML per tutti gli elementi padre e che utilizza tag per descrivere l'oggetto.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento restituito.|  
|DatabaseName|28|8|Contiene il nome del database in cui è stato generato l'evento restituito.|  
|NTUserName|32|8|Contiene l'account utente di Windows associato all'evento restituito.|  
|NTDomainName|33|8|Contiene l'account di dominio di Windows associato all'evento restituito.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento restituito.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento restituito. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA (XML for Analysis).|  
|TextData|42|9|Contiene i dati di tipo text associati all'evento restituito.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento restituito.|  
  
## <a name="progress-report-enddata-columns"></a>Colonne di dati dell'evento Progress Report End  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento. Di seguito sono indicate coppie di valori **Sub Class Id**: **Sub Class Name** validi:<br /><br /> 1: **Process**<br /><br /> 2: **Merge**<br /><br /> 3: **Delete**<br /><br /> 4: **DeleteOldAggregations**<br /><br /> 5: **Rebuild**<br /><br /> 6: **Commit**<br /><br /> 7: **Rollback**<br /><br /> 8: **CreateIndexes**<br /><br /> 9: **CreateTable**<br /><br /> 10: **InsertInto**<br /><br /> 11: **Transaction**<br /><br /> 12: **Initialize**<br /><br /> 13: **Discretize**<br /><br /> 14: **Query**<br /><br /> 15: **CreateView**<br /><br /> 16: **WriteData**<br /><br /> 17: **ReadData**<br /><br /> 18: **GroupData**<br /><br /> 19: **GroupDataRecord**<br /><br /> 20: **BuildIndex**<br /><br /> 21: **Aggregate**<br /><br /> 22: **BuildDecode**<br /><br /> 23: **WriteDecode**<br /><br /> 24: **BuildDMDecode**<br /><br /> 25: **ExecuteSQL**<br /><br /> 26: **ExecuteModifiedSQL**<br /><br /> 27: **Connecting**<br /><br /> 28: **BuildAggsAndIndexes**<br /><br /> 29: **MergeAggsOnDisk**<br /><br /> 30: **BuildIndexForRigidAggs**<br /><br /> 31: **BuildIndexForFlexibleAggs**<br /><br /> 32: **WriteAggsAndIndexes**<br /><br /> 33: **WriteSegment**<br /><br /> 34: **DataMiningProgress**<br /><br /> 35: **ReadBufferFullReport**<br /><br /> 36: **ProactiveCacheConversion**<br /><br /> 37: **Backup**<br /><br /> 38: **Restore**<br /><br /> 39: **Synchronize**<br /><br /> 40: **Build Processing Schedule**<br /><br /> 41: **Detach**<br /><br /> 42: **Attach**<br /><br /> 43: **Analyze\Encode Data**<br /><br /> 44: **Compress Segment**<br /><br /> 45: **Write Table Column**<br /><br /> 46: **Relationship Build Prepare**<br /><br /> 47: **Build Relationship Segment**<br /><br /> 48: **Load**<br /><br /> 49: **Metadata Load**<br /><br /> 50: **Data Load**<br /><br /> 51: **Post Load**<br /><br /> 52: **Metadata traversal during Backup**<br /><br /> 53: **VertiPaq**<br /><br /> 54: **Hierarchy processing**<br /><br /> 55: **Switching dictionary**|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento restituito, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene l'ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Contiene la quantità di tempo trascorso in millisecondi richiesta dall'evento.|  
|CPUTime|6|2|Contiene il tempo della CPU in millisecondi utilizzato dall'evento.|  
|JobID|7|1|Contiene l'ID processo associato all'evento restituito.|  
|SessionType|8|8|Contiene il tipo di sessione, ovvero l'entità che provoca l'evento, associato all'evento restituito. Per l'elaborazione degli eventi, i valori validi sono:<br /><br /> 1= Utente<br /><br /> 2= Memorizzazione nella cache attiva<br /><br /> 3= Elaborazione lenta|  
|ProgressTotal|9|1|Contiene informazioni sullo stato complessivo dell'evento restituito.|  
|IntegerData|10|1|Contiene i dati di tipo integer associati all'evento restituito, ad esempio il conteggio delle righe elaborate per un evento di elaborazione.|  
|ObjectID|11|8|Contiene l'ID oggetto (una stringa) associato all'evento restituito.|  
|ObjectType|12|1|Contiene il tipo di oggetto.|  
|ObjectName|13|8|Contiene il nome dell'oggetto associato all'evento restituito.|  
|ObjectPath|14|8|Contiene il percorso dell'oggetto per l'oggetto associato all'evento restituito in forma di elenco delimitato da virgole di elementi padre, iniziando dagli elementi padre dell'oggetto.|  
|ObjectReference|15|8|Contiene il riferimento all'oggetto per l'evento restituito, codificato come XML per tutti gli elementi padre e che utilizza tag per descrivere l'oggetto.|  
|Severity|22|1|Contiene il livello di gravità di un'eccezione associata all'evento restituito. I valori possibili sono:<br /><br /> 0 = Esito positivo<br /><br /> 1 = Messaggio informativo<br /><br /> 2 = Avviso<br /><br /> 3 = Errore|  
|Operazione completata|23|1|Contiene informazioni sull'esito positivo o negativo dell'evento del server restituito. I valori possibili sono:<br /><br /> 0 = esito negativo<br /><br /> 1 = esito positivo|  
|Errore|24|1|Contiene il numero di errore di un determinato evento.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento restituito.|  
|DatabaseName|28|8|Contiene il nome del database in cui è stato generato l'evento restituito.|  
|NTUserName|32|8|Contiene l'account utente di Windows associato all'evento restituito.|  
|NTDomainName|33|8|Contiene l'account di dominio di Windows associato all'evento restituito.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento restituito.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento restituito. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento restituito. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA (XML for Analysis).|  
|TextData|42|9|Contiene i dati di tipo text associati all'evento restituito.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento restituito.|  
  
## <a name="progress-report-currentdata-columns"></a>Colonne di dati dell'evento Progress Report Current  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento. Di seguito sono indicate coppie di valori **Sub Class Id**: **Sub Class Name** validi:<br /><br /> 1: **Process**<br /><br /> 2: **Merge**<br /><br /> 3: **Delete**<br /><br /> 4: **DeleteOldAggregations**<br /><br /> 5: **Rebuild**<br /><br /> 6: **Commit**<br /><br /> 7: **Rollback**<br /><br /> 8: **CreateIndexes**<br /><br /> 9: **CreateTable**<br /><br /> 10: **InsertInto**<br /><br /> 11: **Transaction**<br /><br /> 12: **Initialize**<br /><br /> 13: **Discretize**<br /><br /> 14: **Query**<br /><br /> 15: **CreateView**<br /><br /> 16: **WriteData**<br /><br /> 17: **ReadData**<br /><br /> 18: **GroupData**<br /><br /> 19: **GroupDataRecord**<br /><br /> 20: **BuildIndex**<br /><br /> 21: **Aggregate**<br /><br /> 22: **BuildDecode**<br /><br /> 23: **WriteDecode**<br /><br /> 24: **BuildDMDecode**<br /><br /> 25: **ExecuteSQL**<br /><br /> 26: **ExecuteModifiedSQL**<br /><br /> 27: **Connecting**<br /><br /> 28: **BuildAggsAndIndexes**<br /><br /> 29: **MergeAggsOnDisk**<br /><br /> 30: **BuildIndexForRigidAggs**<br /><br /> 31: **BuildIndexForFlexibleAggs**<br /><br /> 32: **WriteAggsAndIndexes**<br /><br /> 33: **WriteSegment**<br /><br /> 34: **DataMiningProgress**<br /><br /> 35: **ReadBufferFullReport**<br /><br /> 36: **ProactiveCacheConversion**<br /><br /> 37: **Backup**<br /><br /> 38: **Restore**<br /><br /> 39: **Synchronize**<br /><br /> 40: **Build Processing Schedule**<br /><br /> 41: **Detach**<br /><br /> 42: **Attach**<br /><br /> 43: **Analyze\Encode Data**<br /><br /> 44: **Compress Segment**<br /><br /> 45: **Write Table Column**<br /><br /> 46: **Relationship Build Prepare**<br /><br /> 47: **Build Relationship Segment**<br /><br /> 48: **Load**<br /><br /> 49: **Metadata Load**<br /><br /> 50: **Data Load**<br /><br /> 51: **Post Load**<br /><br /> 52: **Metadata traversal during Backup**<br /><br /> 53: **VertiPaq**<br /><br /> 54: **Hierarchy processing**<br /><br /> 55: **Switching dictionary**|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento restituito, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|JobID|7|1|Contiene l'ID processo associato all'evento restituito.|  
|SessionType|8|8|Contiene il tipo di sessione, ovvero l'entità che provoca l'evento, associato all'evento restituito. Per l'elaborazione degli eventi, i valori validi sono:<br /><br /> 1= Utente<br /><br /> 2= Memorizzazione nella cache attiva<br /><br /> 3= Elaborazione lenta|  
|ProgressTotal|9|1|Contiene informazioni sullo stato complessivo dell'evento restituito.|  
|IntegerData|10|1|Contiene i dati di tipo integer associati all'evento restituito, ad esempio il conteggio delle righe elaborate per un evento di elaborazione.|  
|ObjectID|11|8|Contiene l'ID oggetto (una stringa) associato all'evento restituito.|  
|ObjectType|12|1|Contiene il tipo di oggetto.|  
|ObjectName|13|8|Contiene il nome dell'oggetto associato all'evento restituito.|  
|ObjectPath|14|8|Contiene il percorso dell'oggetto per l'oggetto associato all'evento restituito in forma di elenco delimitato da virgole di elementi padre, iniziando dagli elementi padre dell'oggetto.|  
|ObjectReference|15|8|Contiene il riferimento all'oggetto per l'evento restituito, codificato come XML per tutti gli elementi padre e che utilizza tag per descrivere l'oggetto.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento restituito.|  
|DatabaseName|28|8|Contiene il nome del database in cui è stato generato l'evento restituito.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento restituito.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento restituito. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA (XML for Analysis).|  
|TextData|42|9|Contiene i dati di tipo text associati all'evento restituito.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento restituito.|  
  
## <a name="progress-report-errordata-columns"></a>Colonne di dati dell'evento Progress Report Error  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento. Di seguito sono indicate coppie di valori **Sub Class Id**: **Sub Class Name** validi:<br /><br /> 1: **Process**<br /><br /> 2: **Merge**<br /><br /> 3: **Delete**<br /><br /> 4: **DeleteOldAggregations**<br /><br /> 5: **Rebuild**<br /><br /> 6: **Commit**<br /><br /> 7: **Rollback**<br /><br /> 8: **CreateIndexes**<br /><br /> 9: **CreateTable**<br /><br /> 10: **InsertInto**<br /><br /> 11: **Transaction**<br /><br /> 12: **Initialize**<br /><br /> 13: **Discretize**<br /><br /> 14: **Query**<br /><br /> 15: **CreateView**<br /><br /> 16: **WriteData**<br /><br /> 17: **ReadData**<br /><br /> 18: **GroupData**<br /><br /> 19: **GroupDataRecord**<br /><br /> 20: **BuildIndex**<br /><br /> 21: **Aggregate**<br /><br /> 22: **BuildDecode**<br /><br /> 23: **WriteDecode**<br /><br /> 24: **BuildDMDecode**<br /><br /> 25: **ExecuteSQL**<br /><br /> 26: **ExecuteModifiedSQL**<br /><br /> 27: **Connecting**<br /><br /> 28: **BuildAggsAndIndexes**<br /><br /> 29: **MergeAggsOnDisk**<br /><br /> 30: **BuildIndexForRigidAggs**<br /><br /> 31: **BuildIndexForFlexibleAggs**<br /><br /> 32: **WriteAggsAndIndexes**<br /><br /> 33: **WriteSegment**<br /><br /> 34: **DataMiningProgress**<br /><br /> 35: **ReadBufferFullReport**<br /><br /> 36: **ProactiveCacheConversion**<br /><br /> 37: **Backup**<br /><br /> 38: **Restore**<br /><br /> 39: **Synchronize**<br /><br /> 40: **Build Processing Schedule**<br /><br /> 41: **Detach**<br /><br /> 42: **Attach**<br /><br /> 43: **Analyze\Encode Data**<br /><br /> 44: **Compress Segment**<br /><br /> 45: **Write Table Column**<br /><br /> 46: **Relationship Build Prepare**<br /><br /> 47: **Build Relationship Segment**<br /><br /> 48: **Load**<br /><br /> 49: **Metadata Load**<br /><br /> 50: **Data Load**<br /><br /> 51: **Post Load**<br /><br /> 52: **Metadata traversal during Backup**<br /><br /> 53: **VertiPaq**<br /><br /> 54: **Hierarchy processing**<br /><br /> 55: **Switching dictionary**|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento restituito, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene l'ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Contiene la quantità di tempo trascorso in millisecondi richiesta dall'evento.|  
|JobID|7|1|Contiene l'ID processo associato all'evento restituito.|  
|SessionType|8|8|Contiene il tipo di sessione, ovvero l'entità che provoca l'evento, associato all'evento restituito. Per l'elaborazione degli eventi, i valori validi sono:<br /><br /> 1= Utente<br /><br /> 2= Memorizzazione nella cache attiva<br /><br /> 3= Elaborazione lenta|  
|ProgressTotal|9|1|Contiene informazioni sullo stato complessivo dell'evento restituito.|  
|IntegerData|10|1|Contiene i dati di tipo integer associati all'evento restituito, ad esempio il conteggio delle righe elaborate per un evento di elaborazione.|  
|ObjectID|11|8|Contiene l'ID oggetto (una stringa) associato all'evento restituito.|  
|ObjectType|12|1|Contiene il tipo di oggetto.|  
|ObjectName|13|8|Contiene il nome dell'oggetto associato all'evento restituito.|  
|ObjectPath|14|8|Contiene il percorso dell'oggetto per l'oggetto associato all'evento restituito in forma di elenco delimitato da virgole di elementi padre, iniziando dagli elementi padre dell'oggetto.|  
|ObjectReference|15|8|Contiene il riferimento all'oggetto per l'evento restituito, codificato come XML per tutti gli elementi padre e che utilizza tag per descrivere l'oggetto.|  
|Severity|22|1|Contiene il livello di gravità di un'eccezione associata all'evento restituito. I valori possibili sono:<br /><br /> 0 = Esito positivo<br /><br /> 1 = Messaggio informativo<br /><br /> 2 = Avviso<br /><br /> 3 = Errore|  
|Errore|24|1|Contiene il numero di errore di un determinato evento.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento restituito.|  
|DatabaseName|28|8|Contiene il nome del database in cui è stato generato l'evento restituito.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento restituito.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento restituito. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA (XML for Analysis).|  
|TextData|42|9|Contiene i dati di tipo text associati all'evento restituito.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento restituito.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi report di stato](../../analysis-services/trace-events/progress-reports-event-category.md)  
  
  
