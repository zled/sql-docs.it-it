---
title: Colonne di dati degli eventi di sessione | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6e3a0287edc3081273f2a3c3075f355e9b2b2493
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34044345"
---
# <a name="session-events-data-columns"></a>Colonne di dati degli eventi di sessione
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoria di eventi Eventi di sessione include la classe di evento seguente:  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|41|Existing Connection|Connessione utente esistente.|  
|42|Existing Session|Sessione esistente.|  
|43|Session Initialize|Inizializzazione della sessione.|  
  
 Nella tabella seguente sono incluse le colonne di dati per la classe di evento.  
  
## <a name="existing-connection"></a>Existing Connection  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|ID connessione univoco.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="existing-session"></a>Existing Session  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Durata dell'evento in millisecondi.|  
|CPUTime|6|2|Tempo della CPU in millisecondi utilizzato dall'evento.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
|RequestProperties|45|9|Proprietà della richiesta XMLA.|  
  
## <a name="session-initialize"></a>Session Initialize  
  
|||||  
|-|-|-|-|  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
|RequestProperties|45|9|Proprietà della richiesta XMLA.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi Controllo di sicurezza](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
