---
title: Colonne di dati di eventi individuazione | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: trace-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Discover Events event category
ms.assetid: 10ec598e-5b51-4767-b4f7-42e261d96a40
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1d4275dc8ed85c907a458c5772a57153dc88fa0e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discover-events-data-columns"></a>Colonne di dati degli eventi di individuazione
  La categoria degli eventi di individuazione include le classi di eventi seguenti:  
  
-   Classe Discover Begin  
  
-   Classe Discover End  
  
 Nelle tabelle seguenti vengono elencate le colonne di dati per ognuna di queste classi di eventi.  
  
## <a name="discover-begin-classdata-columns"></a>Colonne di dati della classe Discover Begin  
  
|||||  
|-|-|-|-|  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento.  Di seguito sono indicate coppie di valori **Sub Class Id**/**Sub Class Name** validi:<br /><br /> 0: DBSCHEMA_CATALOGS<br /><br /> 1: DBSCHEMA_TABLES<br /><br /> 2: DBSCHEMA_COLUMNS<br /><br /> 3: DBSCHEMA_PROVIDER_TYPES<br /><br /> 4: MDSCHEMA_CUBES<br /><br /> 5: MDSCHEMA_DIMENSIONS<br /><br /> 6: MDSCHEMA_HIERARCHIES<br /><br /> 7: MDSCHEMA_LEVELS<br /><br /> 8: MDSCHEMA_MEASURES<br /><br /> 9: MDSCHEMA_PROPERTIES<br /><br /> 10: MDSCHEMA_MEMBERS<br /><br /> 11: MDSCHEMA_FUNCTIONS<br /><br /> 12: MDSCHEMA_ACTIONS<br /><br /> 13: MDSCHEMA_SETS<br /><br /> 14: DISCOVER_INSTANCES<br /><br /> 15: MDSCHEMA_KPIS<br /><br /> 16: MDSCHEMA_MEASUREGROUPS<br /><br /> 17: MDSCHEMA_COMMANDS<br /><br /> 18: DMSCHEMA_MINING_SERVICES<br /><br /> 19: DMSCHEMA_MINING_SERVICE_PARAMETERS<br /><br /> 20: DMSCHEMA_MINING_FUNCTIONS<br /><br /> 21: DMSCHEMA_MINING_MODEL_CONTENT<br /><br /> 22: DMSCHEMA_MINING_MODEL_XML<br /><br /> 23: DMSCHEMA_MINING_MODELS<br /><br /> 24: DMSCHEMA_MINING_COLUMNS<br /><br /> 25: DISCOVER_DATASOURCES<br /><br /> 26: DISCOVER_PROPERTIES<br /><br /> 27: DISCOVER_SCHEMA_ROWSETS<br /><br /> 28: DISCOVER_ENUMERATORS<br /><br /> 29: DISCOVER_KEYWORDS<br /><br /> 30: DISCOVER_LITERALS<br /><br /> 31: DISCOVER_XML_METADATA<br /><br /> 32: DISCOVER_TRACES<br /><br /> 33: DISCOVER_TRACE_DEFINITION_PROVIDERINFO<br /><br /> 34: DISCOVER_TRACE_COLUMNS<br /><br /> 35: DISCOVER_TRACE_EVENT_CATEGORIES<br /><br /> 36: DMSCHEMA_MINING_STRUCTURES<br /><br /> 37: DMSCHEMA_MINING_STRUCTURE_COLUMNS<br /><br /> 38: DISCOVER_MASTER_KEY<br /><br /> 39: MDSCHEMA_INPUT_DATASOURCES<br /><br /> 40: DISCOVER_LOCATIONS<br /><br /> 41: DISCOVER_PARTITION_DIMENSION_STAT<br /><br /> 42: DISCOVER_PARTITION_STAT<br /><br /> 43: DISCOVER_DIMENSION_STAT<br /><br /> 44: MDSCHEMA_MEASUREGROUP_DIMENSIONS<br /><br /> 49: DISCOVER_XEVENT_TRACE_DEFINITION|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di individuazione.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|NTUserName|32|8|Contiene il nome utente di Windows associato all'evento di individuazione. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|NTDomainName|33|8|Contiene il dominio di Windows associato all'evento di individuazione.|  
|ClientProcessID|36|1|Contiene l'ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento di individuazione.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento di individuazione. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di individuazione. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di testo associati all'evento.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di individuazione.|  
|RequestProperties|45|9|Contiene le proprietà della richiesta XMLA (XML for Analysis) associata all'evento di individuazione.|  
  
## <a name="discover-end-classdata-columns"></a>Colonne di dati della classe Discover End  
  
|||||  
|-|-|-|-|  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|EventClass|0|1|Contiene la classe di evento utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento. Di seguito sono indicate coppie di valori **Sub Class Id**/**Sub Class Name** validi:<br /><br /> 0: DBSCHEMA_CATALOGS<br /><br /> 1: DBSCHEMA_TABLES<br /><br /> 2: DBSCHEMA_COLUMNS<br /><br /> 3: DBSCHEMA_PROVIDER_TYPES<br /><br /> 4: MDSCHEMA_CUBES<br /><br /> 5: MDSCHEMA_DIMENSIONS<br /><br /> 6: MDSCHEMA_HIERARCHIES<br /><br /> 7: MDSCHEMA_LEVELS<br /><br /> 8: MDSCHEMA_MEASURES<br /><br /> 9: MDSCHEMA_PROPERTIES<br /><br /> 10: MDSCHEMA_MEMBERS<br /><br /> 11: MDSCHEMA_FUNCTIONS<br /><br /> 12: MDSCHEMA_ACTIONS<br /><br /> 13: MDSCHEMA_SETS<br /><br /> 14: DISCOVER_INSTANCES<br /><br /> 15: MDSCHEMA_KPIS<br /><br /> 16: MDSCHEMA_MEASUREGROUPS<br /><br /> 17: MDSCHEMA_COMMANDS<br /><br /> 18: DMSCHEMA_MINING_SERVICES<br /><br /> 19: DMSCHEMA_MINING_SERVICE_PARAMETERS<br /><br /> 20: DMSCHEMA_MINING_FUNCTIONS<br /><br /> 21: DMSCHEMA_MINING_MODEL_CONTENT<br /><br /> 22: DMSCHEMA_MINING_MODEL_XML<br /><br /> 23: DMSCHEMA_MINING_MODELS<br /><br /> 24: DMSCHEMA_MINING_COLUMNS<br /><br /> 25: DISCOVER_DATASOURCES<br /><br /> 26: DISCOVER_PROPERTIES<br /><br /> 27: DISCOVER_SCHEMA_ROWSETS<br /><br /> 28: DISCOVER_ENUMERATORS<br /><br /> 29: DISCOVER_KEYWORDS<br /><br /> 30: DISCOVER_LITERALS<br /><br /> 31: DISCOVER_XML_METADATA<br /><br /> 32: DISCOVER_TRACES<br /><br /> 33: DISCOVER_TRACE_DEFINITION_PROVIDERINFO<br /><br /> 34: DISCOVER_TRACE_COLUMNS<br /><br /> 35: DISCOVER_TRACE_EVENT_CATEGORIES<br /><br /> 36: DMSCHEMA_MINING_STRUCTURES<br /><br /> 37: DMSCHEMA_MINING_STRUCTURE_COLUMNS<br /><br /> 38: DISCOVER_MASTER_KEY<br /><br /> 39: MDSCHEMA_INPUT_DATASOURCES<br /><br /> 40: DISCOVER_LOCATIONS<br /><br /> 41: DISCOVER_PARTITION_DIMENSION_STAT<br /><br /> 42: DISCOVER_PARTITION_STAT<br /><br /> 43: DISCOVER_DIMENSION_STAT<br /><br /> 44: MDSCHEMA_MEASUREGROUP_DIMENSIONS<br /><br /> 49: DISCOVER_XEVENT_TRACE_DEFINITION|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento di individuazione, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora, se disponibile, in cui è iniziato l'evento di fine individuazione. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene l'ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Contiene la durata dell'evento di individuazione in millisecondi.|  
|CPUTime|6|2|Contiene il tempo della CPU in millisecondi utilizzato dall'evento.|  
|Severity|22|1|Contiene il livello di gravità di un'eccezione.|  
|Esito positivo|23|1|Contiene informazioni sull'esito positivo o negativo dell'evento di individuazione. I valori possibili sono:<br /><br /> 0 = esito negativo<br /><br /> 1 = esito positivo|  
|Errore|24|1|Contiene il numero di errore di eventuali errori associati all'evento di individuazione.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di individuazione.|  
|DatabaseName|28|8|Contiene il nome del database in cui è stato generato l'evento di individuazione.|  
|NTUserName|32|8|Contiene il nome utente di Windows associato all'evento di autorizzazione per l'oggetto.|  
|NTDomainName|33|8|Contiene l'account di dominio di Windows associato all'evento di individuazione.|  
|ClientProcessID|36|1|Contiene l'ID di processo client dell'applicazione che ha avviato l'evento.|  
|ApplicationName|37|8|Contiene il nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento di individuazione.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento di autorizzazione per l'oggetto. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di fine individuazione. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di testo associati all'evento.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di individuazione.|  
|RequestProperties|45|9|Contiene le proprietà nella richiesta XMLA.|  
  
## <a name="see-also"></a>Vedere anche  
 [Discover Events Event Category](../../analysis-services/trace-events/discover-events-event-category.md)  
  
  

