---
title: Bloccare le colonne di dati degli eventi | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c223157f-41a0-405c-bc1a-41c999506936
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9a211ed540b3bddb11c5d84cf0db65ef3dade1ad
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lock-events-data-columns"></a>Colonne di dati degli eventi di blocco
  La categoria di eventi di blocco include la classe di evento seguente:  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|50|Deadlock|Informazioni sui blocchi correnti nello stato deadlock.|  
|51|Lock Timeout|Informazioni sui blocchi per cui si è recentemente verificato un timeout|  
|52|Lock Acquired|Informazioni sui blocchi recentemente acquisiti|  
|53|Lock Released|Informazioni sui blocchi recentemente rilasciati|  
|54|Lock Waiting|Informazioni sui blocchi in attesa su altri blocchi|  
  
 Nella tabella seguente sono incluse le colonne di dati per la classe di evento.  
  
## <a name="deadlock"></a>Deadlock  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="lock-timeout"></a>Lock Timeout  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Durata dell'evento in millisecondi.|  
|IntegerData|10|1|Dati di tipo integer.|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|SessionID|39|8|GUID della sessione.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="lock-acquired"></a>Lock Acquired  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|ID connessione univoco.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|GUID della sessione.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="lock-released"></a>Lock Released  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|ID connessione univoco.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|GUID della sessione.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="lock-waiting"></a>Lock Waiting  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|ID connessione univoco.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|GUID della sessione.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi relativa ai blocchi](../../analysis-services/trace-events/lock-events-category.md)  
  
  
