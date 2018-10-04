---
title: Colonne di dati di report di stato | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Progress Reports event category
ms.assetid: d34a6322-e26b-4454-b98f-32307d6956b5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8569f18f3838116ea5a1ed045f418602f85032c6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171171"
---
# <a name="progress-reports-data-columns"></a>Colonne di dati degli eventi di report di stato
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
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: processo<br /><br /> 2: merge<br /><br /> 3: eliminare<br /><br /> 4: DeleteOldAggregations<br /><br /> 5: ricompilare<br /><br /> 6: eseguire il commit<br /><br /> 7: eseguire il rollback<br /><br /> 8: CreateIndexes<br /><br /> 9: CreateTable<br /><br /> 10: InsertInto<br /><br /> 11: transazioni<br /><br /> 12: inizializzare<br /><br /> 13: discretizzare<br /><br /> 14: query<br /><br /> 15: CreateView<br /><br /> 16: WriteData<br /><br /> 17: ReadData<br /><br /> 18: GroupData<br /><br /> 19: GroupDataRecord<br /><br /> 20: BuildIndex<br /><br /> 21: aggregazione<br /><br /> 22: BuildDecode<br /><br /> 23: WriteDecode<br /><br /> 24: BuildDMDecode<br /><br /> 25: ExecuteSQL<br /><br /> 26: ExecuteModifiedSQL<br /><br /> 27: la connessione<br /><br /> 28: BuildAggsAndIndexes<br /><br /> 29: MergeAggsOnDisk<br /><br /> 30: BuildIndexForRigidAggs<br /><br /> 31: BuildIndexForFlexibleAggs<br /><br /> 32: WriteAggsAndIndexes<br /><br /> 33: WriteSegment<br /><br /> 34: DataMiningProgress<br /><br /> 35: ReadBufferFullReport<br /><br /> 36: ProactiveCacheConversion<br /><br /> 37: backup<br /><br /> 38: restore<br /><br /> 39: sincronizzare<br /><br /> 40: pianificazione dell'elaborazione di compilazione<br /><br /> 41: scollegamento<br /><br /> 42: collegare<br /><br /> 43: Analyze\Encode dati<br /><br /> 44: comprimere segmento<br /><br /> 45: scrivere una colonna di tabella<br /><br /> 46: compilazione di relazione preparare<br /><br /> 47: compila il segmento di relazione<br /><br /> 48: load<br /><br /> 49: caricamento metadati<br /><br /> 50: caricamento dei dati<br /><br /> 51: postcaricamento<br /><br /> 52: attraversamento dei metadati durante il Backup<br /><br /> 53: VertiPaq<br /><br /> 54: elaborazione gerarchia<br /><br /> 55: dizionario commutazione|  
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
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: processo<br /><br /> 2: merge<br /><br /> 3: eliminare<br /><br /> 4: DeleteOldAggregations<br /><br /> 5: ricompilare<br /><br /> 6: eseguire il commit<br /><br /> 7: eseguire il rollback<br /><br /> 8: CreateIndexes<br /><br /> 9: CreateTable<br /><br /> 10: InsertInto<br /><br /> 11: transazioni<br /><br /> 12: inizializzare<br /><br /> 13: discretizzare<br /><br /> 14: query<br /><br /> 15: CreateView<br /><br /> 16: WriteData<br /><br /> 17: ReadData<br /><br /> 18: GroupData<br /><br /> 19: GroupDataRecord<br /><br /> 20: BuildIndex<br /><br /> 21: aggregazione<br /><br /> 22: BuildDecode<br /><br /> 23: WriteDecode<br /><br /> 24: BuildDMDecode<br /><br /> 25: ExecuteSQL<br /><br /> 26: ExecuteModifiedSQL<br /><br /> 27: la connessione<br /><br /> 28: BuildAggsAndIndexes<br /><br /> 29: MergeAggsOnDisk<br /><br /> 30: BuildIndexForRigidAggs<br /><br /> 31: BuildIndexForFlexibleAggs<br /><br /> 32: WriteAggsAndIndexes<br /><br /> 33: WriteSegment<br /><br /> 34: DataMiningProgress<br /><br /> 35: ReadBufferFullReport<br /><br /> 36: ProactiveCacheConversion<br /><br /> 37: backup<br /><br /> 38: restore<br /><br /> 39: sincronizzare<br /><br /> 40: pianificazione dell'elaborazione di compilazione<br /><br /> 41: scollegamento<br /><br /> 42: collegare<br /><br /> 43: Analyze\Encode dati<br /><br /> 44: comprimere segmento<br /><br /> 45: scrivere una colonna di tabella<br /><br /> 46: compilazione di relazione preparare<br /><br /> 47: compila il segmento di relazione<br /><br /> 48: load<br /><br /> 49: caricamento metadati<br /><br /> 50: caricamento dei dati<br /><br /> 51: postcaricamento<br /><br /> 52: attraversamento dei metadati durante il Backup<br /><br /> 53: VertiPaq<br /><br /> 54: elaborazione gerarchia<br /><br /> 55: dizionario commutazione|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento restituito, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene l'ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Duration|5|2|Contiene la quantità di tempo trascorso in millisecondi richiesta dall'evento.|  
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
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: processo<br /><br /> 2: merge<br /><br /> 3: eliminare<br /><br /> 4: DeleteOldAggregations<br /><br /> 5: ricompilare<br /><br /> 6: eseguire il commit<br /><br /> 7: eseguire il rollback<br /><br /> 8: CreateIndexes<br /><br /> 9: CreateTable<br /><br /> 10: InsertInto<br /><br /> 11: transazioni<br /><br /> 12: inizializzare<br /><br /> 13: discretizzare<br /><br /> 14: query<br /><br /> 15: CreateView<br /><br /> 16: WriteData<br /><br /> 17: ReadData<br /><br /> 18: GroupData<br /><br /> 19: GroupDataRecord<br /><br /> 20: BuildIndex<br /><br /> 21: aggregazione<br /><br /> 22: BuildDecode<br /><br /> 23: WriteDecode<br /><br /> 24: BuildDMDecode<br /><br /> 25: ExecuteSQL<br /><br /> 26: ExecuteModifiedSQL<br /><br /> 27: la connessione<br /><br /> 28: BuildAggsAndIndexes<br /><br /> 29: MergeAggsOnDisk<br /><br /> 30: BuildIndexForRigidAggs<br /><br /> 31: BuildIndexForFlexibleAggs<br /><br /> 32: WriteAggsAndIndexes<br /><br /> 33: WriteSegment<br /><br /> 34: DataMiningProgress<br /><br /> 35: ReadBufferFullReport<br /><br /> 36: ProactiveCacheConversion<br /><br /> 37: backup<br /><br /> 38: restore<br /><br /> 39: sincronizzare<br /><br /> 40: pianificazione dell'elaborazione di compilazione<br /><br /> 41: scollegamento<br /><br /> 42: collegare<br /><br /> 43: Analyze\Encode dati<br /><br /> 44: comprimere segmento<br /><br /> 45: scrivere una colonna di tabella<br /><br /> 46: compilazione di relazione preparare<br /><br /> 47: compila il segmento di relazione<br /><br /> 48: load<br /><br /> 49: caricamento metadati<br /><br /> 50: caricamento dei dati<br /><br /> 51: postcaricamento<br /><br /> 52: attraversamento dei metadati durante il Backup<br /><br /> 53: VertiPaq<br /><br /> 54: elaborazione gerarchia<br /><br /> 55: dizionario commutazione|  
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
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: processo<br /><br /> 2: merge<br /><br /> 3: eliminare<br /><br /> 4: DeleteOldAggregations<br /><br /> 5: ricompilare<br /><br /> 6: eseguire il commit<br /><br /> 7: eseguire il rollback<br /><br /> 8: CreateIndexes<br /><br /> 9: CreateTable<br /><br /> 10: InsertInto<br /><br /> 11: transazioni<br /><br /> 12: inizializzare<br /><br /> 13: discretizzare<br /><br /> 14: query<br /><br /> 15: CreateView<br /><br /> 16: WriteData<br /><br /> 17: ReadData<br /><br /> 18: GroupData<br /><br /> 19: GroupDataRecord<br /><br /> 20: BuildIndex<br /><br /> 21: aggregazione<br /><br /> 22: BuildDecode<br /><br /> 23: WriteDecode<br /><br /> 24: BuildDMDecode<br /><br /> 25: ExecuteSQL<br /><br /> 26: ExecuteModifiedSQL<br /><br /> 27: la connessione<br /><br /> 28: BuildAggsAndIndexes<br /><br /> 29: MergeAggsOnDisk<br /><br /> 30: BuildIndexForRigidAggs<br /><br /> 31: BuildIndexForFlexibleAggs<br /><br /> 32: WriteAggsAndIndexes<br /><br /> 33: WriteSegment<br /><br /> 34: DataMiningProgress<br /><br /> 35: ReadBufferFullReport<br /><br /> 36: ProactiveCacheConversion<br /><br /> 37: backup<br /><br /> 38: restore<br /><br /> 39: sincronizzare<br /><br /> 40: pianificazione dell'elaborazione di compilazione<br /><br /> 41: scollegamento<br /><br /> 42: collegare<br /><br /> 43: Analyze\Encode dati<br /><br /> 44: comprimere segmento<br /><br /> 45: scrivere una colonna di tabella<br /><br /> 46: compilazione di relazione preparare<br /><br /> 47: compila il segmento di relazione<br /><br /> 48: load<br /><br /> 49: caricamento metadati<br /><br /> 50: caricamento dei dati<br /><br /> 51: postcaricamento<br /><br /> 52: attraversamento dei metadati durante il Backup<br /><br /> 53: VertiPaq<br /><br /> 54: elaborazione gerarchia<br /><br /> 55: dizionario commutazione|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento restituito, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene l'ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Duration|5|2|Contiene la quantità di tempo trascorso in millisecondi richiesta dall'evento.|  
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
 [Categoria di eventi di report di stato](progress-reports-event-category.md)  
  
  
