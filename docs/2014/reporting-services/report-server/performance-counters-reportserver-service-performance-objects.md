---
title: 'Contatori delle prestazioni per gli oggetti prestazioni ReportServer: Service e reportserversharepoint: Service | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Server service, performance counters
ms.assetid: 2bcacab2-3a4f-4aae-b123-19d756b9b9ed
caps.latest.revision: 23
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c0573346427258d9b79188852c8d6e13af1cb8d1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238391"
---
# <a name="performance-counters-for-the-reportserverservice--and-reportserversharepointservice-performance-objects"></a>Contatori delle prestazioni per gli oggetti prestazioni di ReportServer:Service e ReportServerSharePoint:Service
  In questo argomento sono descritti i contatori delle prestazioni per gli oggetti prestazioni di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] seguenti:  
  
-   `ReportServer:Service`  
  
-   `ReportServerSharePoint:Service`  
  
> [!NOTE]  
>  Gli oggetti prestazioni vengono utilizzati per monitorare gli eventi nel server di report locale. Se si esegue un server di report in una distribuzione con scalabilità orizzontale, i conteggi si applicano al server corrente e non all'intera distribuzione con scalabilità orizzontale.  
  
 Gli oggetti prestazioni sono disponibili in Windows Performance Monitor (**Perfmon.exe**). Per ulteriori informazioni, vedere la documentazione di Windows. [Profilatura di runtime](http://msdn.microsoft.com/library/w4bz2147.aspx) (http://msdn.microsoft.com/library/w4bz2147.aspx).  
  
 Contenuto dell'argomento:  
  
-   [Contatori delle prestazioni di ReportServer:Service (server di report in modalità nativa)](#bkmk_ReportServer)  
  
-   [ReportServerSharePoint:Service (server di report in modalità SharePoint)](#bkmk_ReportServerSharePoint)  
  
-   [Utilizzare i cmdlet di PowerShell per restituire gli elenchi](#bkmk_powershell)  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Modalità SharePoint | Modalità nativa.  
  
##  <a name="bkmk_ReportServer"></a> Contatori delle prestazioni di ReportServer:Service (server di report in modalità nativa)  
 Nell'oggetto prestazioni `ReportServer:Service` è inclusa una raccolta di contatori per tenere traccia degli eventi correlati a HTTP e degli eventi correlati alla memoria per un'istanza del server di report. Questo oggetto prestazione viene visualizzato una volta per ogni [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] istanza nel computer e si possa aggiungere o rimuovere contatori nell'oggetto prestazione per ogni istanza. I contatori per l'istanza predefinita vengono visualizzati nel formato `ReportServer:Service`. I contatori per le istanze denominate sono visualizzati nel formato `ReportServer$<` *nome_istanza*`>:Service`.  
  
 Il `ReportServer:Service` oggetto delle prestazioni sono state introdotta nella [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], e fornisce un subset di contatori inclusi in Internet Information Services (IIS) e [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] nelle versioni precedenti di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Questi nuovi contatori sono specifici di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e consentono di tenere traccia di eventi correlati a HTTP per il server di report, quali richieste, connessioni e tentativi di accesso. Questo oggetto prestazione, inoltre, include contatori per tenere traccia di eventi di gestione della memoria.  
  
 Nella tabella seguente sono elencati i contatori inclusi nel `ReportServer:Service` oggetto delle prestazioni.  
  
 ![Contenuto correlato di PowerShell](../media/rs-powershellicon.jpg "Contenuto correlato di PowerShell") Il seguente script di Windows PowerShell restituisce l'elenco di contatori delle prestazioni per CounterSetName  
  
```  
(get-counter -listset "ReportServer:Service").paths  
```  
  
|Contatore|Description|  
|-------------|-----------------|  
|`Active connections`|Numero di connessioni attualmente attive nel server.|  
|`Bytes Received Total`|Numero di byte ricevuti dal server. Questo contatore conta i byte non elaborati ricevuti complessivamente sia da Gestione report sia dal server di report.|  
|`Bytes Received/sec`|Numero di byte ricevuti al secondo dal server. Questo contatore è aggiornato solo al termine di un trasferimento, ovvero continua a indicare 0 e aumenta solo al termine di un trasferimento.|  
|`Bytes Sent Total`|Numero di byte inviati dal server. Questo contatore conta i byte non elaborati inviati complessivamente sia da Gestione report sia dal server di report.|  
|`Bytes Sent/sec`|Numero di byte inviati al secondo dal server. Questo contatore è aggiornato solo al termine di un trasferimento, ovvero continua a indicare 0 e aumenta solo al termine di un trasferimento.|  
|`Errors Total`|Numero totale di errori verificatisi durante l'elaborazione di richieste HTTP. Tali errori includono i codici di stato HTTP delle serie 400 e 500.|  
|`Errors/sec`|Numero totale di errori al secondo verificatisi durante l'elaborazione di richieste HTTP. Tali errori includono i codici di stato HTTP delle serie 400 e 500.|  
|`Logon Attempts Total`|Numero di tentativi di accesso eseguiti dai tipi di autenticazione RSWindows. I tipi di autenticazione RSWindows includono RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos e RSWindowsBasic. Il valore zero (0) rappresenta l'autenticazione personalizzata.|  
|`Logon Attempts/sec`|Frequenza di tentativi di accesso.|  
|`Logon Successes Total`|Numero di tentativi di accesso riusciti per i tipi di autenticazione RSWindows. I tipi di autenticazione RSWindows includono RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos e RSWindowsBasic. Il valore zero (0) rappresenta l'autenticazione personalizzata.|  
|`Logon Successes/sec`|Frequenza di accessi riusciti.|  
|`Memory Pressure State`|Uno dei numeri seguenti, da 1 a 5, indicante lo stato corrente della memoria del server:<br /><br /> 1: nessun utilizzo<br /><br /> 2: scarso utilizzo<br /><br /> 3: utilizzo medio<br /><br /> 4: utilizzo elevato<br /><br /> 5: utilizzo eccessivo|  
|`Memory Shrink Amount`|Numero di byte richiesti dal server per compattare la memoria in uso.|  
|`Memory Shrink Notifications/sec`|Numero di notifiche generate dal server nell'ultimo secondo per la compattazione della memoria in uso. Questo valore indica la frequenza con cui il server rileva un utilizzo eccessivo della memoria.|  
|`Requests Disconnected`|Numero di richieste disconnesse a causa di un errore di comunicazione.|  
|`Requests Executing`|Numero di richieste attualmente in elaborazione.|  
|`Requests Not Authorized`|Numero di richieste non riuscite con codice di stato HTTP 401.|  
|`Requests Rejected`|Numero totale di richieste non elaborate a causa di risorse server insufficienti. Questo contatore rappresenta il numero delle richieste che restituiscono un codice di stato HTTP 503, che indica che il server è troppo occupato.|  
|`Requests Total`|Numero totale di richieste ricevute dal servizio del server di report dall'avvio. Questo contatore conta le richieste inviate a Gestione report e quelle inviate da Gestione report al server di report.|  
|`Requests/sec`|Numero di richieste elaborate al secondo. Questo valore rappresenta la velocità di trasferimento corrente dell'applicazione.|  
|`Tasks Queued`|Numero di attività in attesa che un thread diventi disponibile per l'elaborazione. Ogni richiesta inviata al server di report corrisponde a una o più attività. Questo contatore rappresenta solo il numero di attività pronte per l'elaborazione e non include il numero di attività attualmente in esecuzione.|  
  
##  <a name="bkmk_ReportServerSharePoint"></a> ReportServerSharePoint:Service (server di report in modalità SharePoint)  
 Il `ReportServerSharePoint:Service` oggetto delle prestazioni è stato aggiunto [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 ![Contenuto correlato di PowerShell](../media/rs-powershellicon.jpg "Contenuto correlato di PowerShell") Il seguente script di Windows PowerShell restituisce l'elenco di contatori delle prestazioni per CounterSetName  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
|Contatore|  
|-------------|  
|`Memory Pressure State`|  
|`Memory Shrink Amount`|  
|`Memory Shrink Notifications/Sec`|  
  
##  <a name="bkmk_powershell"></a> Utilizzare i cmdlet di PowerShell per restituire gli elenchi  
 ![Contenuto correlato di PowerShell](../media/rs-powershellicon.jpg "Contenuto correlato di PowerShell") Il seguente script di Windows PowerShell restituisce l'elenco di contatori delle prestazioni per CounterSetName "ReportServerSharePoint:Service":  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio delle prestazioni del Server di Report](monitoring-report-server-performance.md)   
 [Contatori delle prestazioni per il MSRS 2014 Web Service e MSRS 2014 Windows Service prestazioni oggetti &#40;modalità nativa&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)   
 [I contatori delle prestazioni per il MSRS 2014 Web Service SharePoint Mode e oggetti prestazioni MSRS 2014 Windows Service SharePoint in modalità &#40;modalità SharePoint&#41;]... / performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)  
  
  