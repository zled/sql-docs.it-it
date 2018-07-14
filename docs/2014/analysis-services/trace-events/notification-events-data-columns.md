---
title: Colonne di dati degli eventi di notifica | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Notification Events event category
ms.assetid: 0ecf06da-1586-415a-9da8-60d4c634f030
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a436f613b39f5beb18a7dea40349ce24ded1bf5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204071"
---
# <a name="notification-events-data-columns"></a>Colonne di dati degli eventi di notifica
  Gli eventi di notifica sono eventi non causati direttamente dagli utenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Le notifiche, ad esempio, vengono generate in seguito all'aggiornamento da parte degli utenti di tabelle sottostanti per la memorizzazione nella cache attiva.  
  
 La categoria degli eventi di notifica include la classe di evento seguente:  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|39|Notification|Evento di notifica.|  
|40|User Defined|Evento definito dall'utente.|  
  
 Nella tabella seguente sono incluse le colonne di dati per la classe di evento.  
  
## <a name="notification"></a>Notification  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento. Di seguito sono le coppie nome / Id sottoclasse/sottoclasse valido:<br /><br /> 0: Proactive Caching Begin<br />1: Proactive Caching End<br />2: Flight Recorder Started<br />3: Flight Recorder Stopped<br />4: Configuration Properties Updated<br />5: SQL Trace<br />6: Object Created<br />7: Object Deleted<br />8: Object Altered<br />9: Proactive Caching Polling Begin<br />10: Proactive Caching Polling End<br />11: Flight Recorder Snapshot Begin<br />12: Flight Recorder Snapshot End<br />13: Proactive Caching: notifiable object updated<br />14: Lazy Processing: start processing<br />15: Lazy Processing: processing complete<br />16: SessionOpened Event Begin<br />17: SessionOpened Event End<br />18: SessionClosing Event Begin<br />19: SessionClosing Event End<br />20: CubeOpened Event Begin<br />21: CubeOpened Event End<br />22: CubeClosing Event Begin<br />23: CubeClosing Event End<br />24: Transaction abort requested|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento di notifica, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene l'ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Duration|5|2|Contiene la durata dell'evento in millisecondi.|  
|IntegerData|10|1|Contiene i dati integer associati all'evento di notifica. Quando la colonna EventSubclass è 8, i valori sono i seguenti:<br /><br /> 1 = Creato<br /><br /> 2 = Eliminato<br /><br /> 3 = Proprietà dell'oggetto modificate<br /><br /> 4 = Proprietà degli elementi figlio dell'oggetto modificate<br /><br /> 6 = Elementi figlio aggiunti<br /><br /> 7 = Elementi figlio eliminati<br /><br /> 8 = Oggetto elaborato completamente<br /><br /> 9 = Oggetto elaborato parzialmente<br /><br /> 10 = Oggetto non elaborato<br /><br /> 11 = Oggetto ottimizzato completamente<br /><br /> 12 = Oggetto ottimizzato parzialmente<br /><br /> 13 = Oggetto non ottimizzato|  
|ObjectID|11|8|Contiene l'ID dell'oggetto per il quale questa notifica è pubblicata; si tratta di un valore stringa.|  
|ObjectType|12|1|Contiene il tipo di oggetto associato all'evento di notifica.|  
|ObjectName|13|8|Contiene il nome dell'oggetto associato all'evento di notifica.|  
|ObjectPath|14|8|Contiene il percorso dell'oggetto associato all'evento di notifica. Il percorso viene restituito come elenco delimitato da virgole di elementi padre, iniziando con l'elemento padre dell'oggetto.|  
|ObjectReference|15|8|Contiene il riferimento all'oggetto per il report di stato e l'evento. Il riferimento all'oggetto è codificato come XML da tutti gli elementi padre utilizzando tag per descrivere l'oggetto.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di notifica.|  
|DatabaseName|28|8|Contiene il nome del database in cui è stato generato l'evento di notifica.|  
|NTUserName|32|8|Contiene il nome utente di Windows associato all'evento di notifica.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento di notifica.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento di notifica. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di notifica. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di testo associati all'evento di notifica.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di notifica.|  
|RequestProperties|45|9|Contiene le proprietà della richiesta XMLA.|  
  
## <a name="user-defined"></a>User Defined  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|Una sottoclasse di evento utente specifica che fornisce informazioni aggiuntive su ogni classe di evento.|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento di notifica, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|IntegerData|10|1|Informazioni sull'evento definito dall'utente specifico.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di notifica.|  
|DatabaseName|28|8|Contiene il nome del database in cui è stato generato l'evento di notifica.|  
|NTUserName|32|8|Contiene il nome utente di Windows associato all'evento di notifica.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|SessionID|39|8|Contiene l'ID di sessione associato all'evento di notifica.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento di notifica. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di notifica. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di testo associati all'evento di notifica.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di notifica.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi di notifica](notification-events-event-category.md)  
  
  
