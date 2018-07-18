---
title: Errori e avvisi Events Data Columns | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84a1f21e5556efcf64e1ff1b7c6d5ab2208d1038
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34043095"
---
# <a name="errors-and-warnings-events-data-columns"></a>Colonne di dati degli eventi di errore e di avviso
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoria di eventi Errori e avvisi include la classe di evento seguente:  
  
-   Classe Error  
  
 Nella tabella seguente sono incluse le colonne di dati per la classe di evento.  
  
## <a name="error-event-classdata-columns"></a>Colonne di dati della classe di evento Error  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|StartTime|3|5|Contiene l'ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|SessionType|8|8|Contiene il tipo dell'entità che ha causato l'errore.|  
|Severity|22|1|Contiene il livello di gravità di un'eccezione associata all'evento di errore. I valori possibili sono:<br /><br /> 0 = Esito positivo<br /><br /> 1 = Messaggio informativo<br /><br /> 2 = Avviso<br /><br /> 3 = Errore|  
|Operazione completata|23|1|Contiene informazioni sull'esito positivo o negativo dell'evento di errore. I valori possibili sono:<br /><br /> 0 = esito negativo<br /><br /> 1 = esito positivo|  
|Errore|24|1|Contiene il numero di eventuali errori associati all'evento di errore.|  
|ConnectionID|25|1|Contiene l'ID di connessione univoco associato all'evento di errore.|  
|DatabaseName|28|8|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di errore.|  
|NTUserName|32|8|Contiene il nome utente di Windows associato all'evento di errore.|  
|NTDomainName|33|8|Contiene l'account di dominio di Windows associato all'evento di accesso.|  
|ClientHostName|35|8|Contiene il nome del computer in cui è in esecuzione il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|Contiene l'ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Contiene il nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di errore. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA (XML for Analysis).|  
|SPID|41|1|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di errore. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA (XML for Analysis).|  
|TextData|42|9|Contiene i dati di tipo text associati all'evento di errore.|  
|ServerName|43|8|Contiene il nome del server in esecuzione sull'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di errore del server.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi Controllo di sicurezza](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
