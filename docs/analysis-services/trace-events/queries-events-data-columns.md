---
title: Esegue una query di colonne di dati degli eventi | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 56a945a1130753fc2feb08a89bd4f6e2676f1bd0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34045635"
---
# <a name="queries-events-data-columns"></a>Colonne di dati degli eventi di query
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoria di eventi Eventi di query include le classi di eventi seguenti:  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|9|Query Begin|Inizio della query.|  
|10|Query End|Fine della query.|  
  
 Nelle tabelle seguenti vengono elencate le colonne di dati per ognuna di queste classi di eventi.  
  
## <a name="query-begin-classdata-columns"></a>Colonne di dati della classe Query Begin  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento.<br /><br /> 0: MDXQuery<br /><br /> 1: DMXQuery<br /><br /> 2: SQLQuery<br /><br /> 3: DAXQuery|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di query.|  
|DatabaseName|28|8|Contiene il nome del database in cui è in esecuzione la query.|  
|NTUserName|32|8|Contiene il nome utente di Windows associato all'evento di query.|  
|NTDomainName|33|8|Contiene l'account di dominio di Windows associato all'evento di query.|  
|ClientProcessID|36|1|Contiene l'ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Contiene il nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|Contiene l'ID univoco di sessione della richiesta XMLA.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento di query. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di query. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di tipo text associati all'evento di query.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di query.|  
|RequestParameters|44|9|Contiene i parametri per i comandi e le query con parametri associati all'evento di query.|  
|RequestProperties|45|9|Contiene le proprietà della richiesta XMLA.|  
  
## <a name="query-end-classdata-columns"></a>Colonne di dati della classe Query End  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento.<br /><br /> 0: MDXQuery<br /><br /> 1: DMXQuery<br /><br /> 2: SQLQuery<br /><br /> 3: DAXQuery|  
|CurrentTime|2|5|Contiene l'ora corrente dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene l'ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Contiene la quantità di tempo trascorso in millisecondi richiesta dall'evento.|  
|CPUTime|6|2|Contiene il tempo della CPU in millisecondi utilizzato dall'evento.|  
|Severity|22|1|Contiene il livello di gravità di un'eccezione associata all'evento di query. I valori possibili sono:<br /><br /> 0 = Esito positivo<br /><br /> 1 = Messaggio informativo<br /><br /> 2 = Avviso<br /><br /> 3 = Errore|  
|Operazione completata|23|1|Contiene informazioni sull'esito positivo o negativo dell'evento di query. I valori possibili sono:<br /><br /> 0 = esito negativo<br /><br /> 1 = esito positivo|  
|Errore|24|1|Contiene il numero di errore di eventuali errori associati all'evento di query.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di query.|  
|DatabaseName|28|8|Contiene il nome del database in cui è in esecuzione la query.|  
|NTUserName|32|8|Contiene il nome utente di Windows associato all'evento di query.|  
|NTDomainName|33|8|Contiene l'account di dominio di Windows associato all'evento di query.|  
|ClientProcessID|36|1|Contiene l'ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Contiene il nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|Contiene l'ID univoco di sessione della richiesta XMLA.|  
|NTCanonicalUserName|40|8|Contiene il nome utente di Windows associato all'evento di query. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di query. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|TextData|42|9|Contiene i dati di tipo text associati all'evento di query.|  
|ServerName|43|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di query.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi di query](../../analysis-services/trace-events/queries-events-category.md)  
  
  
