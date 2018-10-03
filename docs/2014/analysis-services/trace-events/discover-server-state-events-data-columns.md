---
title: Individuare lo stato del Server Events Data Columns | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Discover Server State event category
ms.assetid: fbacb187-a4d1-4aa4-be3b-3ddd175f9e19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7076a131acf9c3237c653e32ad238df20bca896
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104601"
---
# <a name="discover-server-state-events-data-columns"></a>Colonne di dati degli eventi di individuazione dello stato del server
  La categoria degli eventi di individuazione stato del server include le classi di eventi seguenti:  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|33|Server State Discover Begin|Inizio dell'individuazione dello stato del server.|  
|34|Server State Discover Data|Contenuto della risposta alla richiesta di individuazione dello stato del server.|  
|35|Server State Discover End|Fine della richiesta di individuazione dello stato del server.|  
  
 Nelle tabelle seguenti vengono elencate le colonne di dati per ognuna di queste classi di eventi.  
  
## <a name="server-state-discover-begin-classdata-columns"></a>Colonne di dati dell'evento Server State Discover Begin  
  
|||||  
|-|-|-|-|  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento di individuazione dello stato del server, quando disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di individuazione dello stato del server.|  
|NTUserName|32|8|Contiene l'account utente di Windows associato all'evento di individuazione dello stato del server.|  
|NTDomainName|33|8|Contiene l'account di dominio di Windows associato all'evento di individuazione dello stato del server.|  
|ClientProcessID|36|1|Contiene l'ID processo dell'applicazione client in cui è stata creata la connessione al server.|  
|ApplicationName|37|8|Contiene il nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento di individuazione dello stato del server.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento di individuazione dello stato del server. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di individuazione dello stato del server. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di testo associati all'evento.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di individuazione dello stato del server.|  
|RequestProperties|45|9|Contiene le proprietà della richiesta XMLA corrente.|  
  
## <a name="server-state-discover-data-classdata-columns"></a>Colonne di dati dell'evento Server State Discover Data  
  
|||||  
|-|-|-|-|  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento di individuazione dello stato del server, quando disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di individuazione dello stato del server.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento di individuazione dello stato del server.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di individuazione dello stato del server. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di tipo text associati alla risposta del server alla richiesta di individuazione.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di individuazione dello stato del server.|  
  
## <a name="server-state-discover-end-classdata-columns"></a>Colonne di dati dell'evento Server State Discover End  
  
|||||  
|-|-|-|-|  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento di individuazione dello stato del server, quando disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene l'ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Duration|5|2|Contiene la durata dell'evento in millisecondi.|  
|CPUTime|6|2|Contiene la quantità di tempo CPU in millisecondi utilizzata dall'evento di individuazione dello stato del server.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di individuazione dello stato del server.|  
|NTUserName|32|8|Contiene l'account utente di Windows associato all'evento di individuazione dello stato del server.|  
|NTDomainName|33|8|Contiene l'account di dominio di Windows associato all'evento di individuazione dello stato del server.|  
|ClientProcessID|36|1|Contiene l'ID processo dell'applicazione client che ha avviato la richiesta XMLA.|  
|ApplicationName|37|8|Contiene il nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|Contiene l'account di dominio di Windows associato all'evento di individuazione dello stato del server.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento di individuazione dello stato del server. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di individuazione dello stato del server. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di tipo text associati alla risposta del server alla richiesta di individuazione.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di individuazione dello stato del server.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi di individuazione stato del server](discover-server-state-event-category.md)  
  
  
