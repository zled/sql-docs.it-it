---
title: Gli errori e avvisi Events Data Columns | Microsoft Docs
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
- Errors and Warnings event category [SQL Server]
ms.assetid: f375d303-7aab-4c51-a955-05a2762cc4d1
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 712bb661c95b659b741374312370b352a3a1e2f6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298991"
---
# <a name="errors-and-warnings-events-data-columns"></a>Colonne di dati degli eventi di errore e di avviso
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
 [Categoria di eventi Controllo di sicurezza](security-audit-event-category.md)  
  
  
