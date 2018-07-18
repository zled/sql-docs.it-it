---
title: Gli eventi di traccia di Analysis Services | Microsoft Docs
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
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- events [Analysis Services]
- event classes [Analysis Services], about event classes
- Profiler [SQL Server Profiler], Analysis Services
- event classes [Analysis Services]
ms.assetid: 6fb219cc-f37e-437a-a544-01cec0953571
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a4c4631e20227cb1d3aeba34337d7b36c8a84c62
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163442"
---
# <a name="analysis-services-trace-events"></a>Eventi di traccia di Analysis Services
  È possibile seguire l'attività di un'istanza di Microsoft SQL Server Analysis Services (SSAS) acquisendo e analizzando gli eventi di traccia generati dall'istanza.  Gli eventi di traccia vengono raggruppati in modo da trovare più facilmente gli eventi di traccia correlati.  Ogni evento di traccia contiene un set di dati attinente all'evento. Non tutti i dati sono attinenti a tutti gli eventi.  
  
 Gli eventi di traccia possono essere avviati e acquisiti usando **[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]**, vedere [usare SQL Server Profiler per monitorare Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md), o può essere avviata da un comando XMLA come **SQL Server Eventi estesi** e l'analisi in un secondo momento, vedere [utilizzare SQL Server Extended Events &#40;XEvents&#41; per monitorare Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md).  
    
 Nelle tabelle seguenti viene descritta ogni categoria insieme agli eventi in essa contenuti.  
  
 Ogni tabella contiene le colonne seguenti:  
  
 ID evento  
 Valore di tipo integer che identifica un tipo di evento. Questo valore è utile quando si leggono le tracce convertite in tabelle o file XML per filtrare il tipo di evento.  
  
 Nome evento  
 Nome dato all'evento nelle applicazioni client Analysis Services.  
  
 Descrizione evento  
 Breve descrizione dell'evento.  
  
 **[Categoria di eventi eventi di comando](command-events-event-category.md)**  
  
 Raccolta di eventi relativi ai comandi.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|15|Command Begin|Inizio del comando.|  
|16|Command End|Fine del comando.|  
  
 **[Categoria di eventi eventi di individuazione](discover-events-event-category.md)**  
  
 Raccolta di eventi per le richieste di individuazione.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|36|Discover Begin|Inizio della richiesta di individuazione.|  
|38|Discover End|Fine della richiesta di individuazione.|  
  
 **[Individuazione stato del Server-categoria di eventi](discover-server-state-event-category.md)**  
  
 Raccolta di eventi per le richieste di individuazione dello stato del server.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|33|Server State Discover Begin|Inizio dell'individuazione dello stato del server.|  
|34|Server State Discover Data|Contenuto della risposta alla richiesta di individuazione dello stato del server.|  
|35|Server State Discover End|Fine della richiesta di individuazione dello stato del server.|  
  
 **[Categoria errori e avvisi evento](errors-and-warnings-event-category.md)**  
  
 Raccolta di eventi per gli errori del server.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|17|Errore|Errore del server.|  
  
 **[Caricamento e salvataggio dei file categoria di eventi](file-load-and-save-event-category.md)**  
  
 Raccolta di eventi per il caricamento e il salvataggio di file.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|90|Inizio caricamento file|Inizio caricamento file.|  
|91|Fine caricamento file|Fine caricamento file.|  
|92|Inizio salvataggio file|Inizio salvataggio file.|  
|93|Fine salvataggio file|Fine salvataggio file|  
|94|Inizio PageOut|Inizio PageOut.|  
|95|Fine PageOut|Fine PageOut|  
|96|Inizio PageIn|Inizio PageIn.|  
|97|Fine PageIn|Fine PageIn|  
  
 **[Categoria di eventi di blocco](lock-events-category.md)**  
  
 Raccolta di eventi correlati ai blocchi.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|50|Deadlock|Deadlock a livello di metadati.|  
|51|Lock Timeout|Timeout di blocco a livello dei metadati.|  
|52|Lock Acquired|Lock Acquired|  
|53|Lock Released|Lock Released|  
|54|Lock Waiting|Lock Waiting|  
  
 **[Categoria di eventi eventi di notifica](notification-events-event-category.md)**  
  
 Raccolta di eventi di notifica.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|39|Notification|Evento di notifica.|  
|40|User Defined|Evento definito dall'utente.|  
  
 **[Categoria di eventi report di stato](progress-reports-event-category.md)**  
  
 Raccolta di eventi per i report di stato.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|5|Progress Report Begin|Inizio del report di stato.|  
|6|Progress Report End|Fine del report di stato.|  
|7|Progress Report Current|Stato corrente del report di stato.|  
|8|Progress Report Error|Errore nel report di stato.|  
  
 **[Categoria di eventi di query](queries-events-category.md)**  
  
 Raccolta di eventi relativi alle query.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|9|Query Begin|Inizio della query.|  
|10|Query End|Fine della query.|  
  
 **[Categoria di eventi di elaborazione di query](query-processing-events-category.md)**  
  
 Raccolta di eventi chiave durante il processo di esecuzione di una query.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|70|Query Cube Begin|Inizio della query sul cubo.|  
|71|Query Cube End|Fine della query sul cubo.|  
|72|Calculate Non Empty Begin|Inizio del calcolo dei valori non vuoti.|  
|73|Calculate Non Empty Current|Stato corrente del calcolo dei valori non vuoti.|  
|74|Calculate Non Empty End|Fine del calcolo dei valori non vuoti.|  
|75|Serialize Results Begin|Inizio della serializzazione dei risultati.|  
|76|Serialize Results Current|Stato corrente della serializzazione dei risultati.|  
|77|Serialize Results End|Fine della serializzazione dei risultati.|  
|78|Execute MDX Script Begin|Inizio dell'esecuzione di script MDX.|  
|79|Execute MDX Script Current|Stato corrente dell'esecuzione di script MDX. Caratteristica deprecata.|  
|80|Execute MDX Script End|Fine dell'esecuzione di script MDX.|  
|81|Query Dimension|Query su dimensione.|  
|11|Query Subcube|Query sul sottocubo, per Ottimizzazione basata sulle statistiche di utilizzo.|  
|12|Query Subcube Verbose|Query sul sottocubo con informazioni dettagliate. L'abilitazione di questo evento potrebbe causare una riduzione delle prestazioni.|  
|60|Get Data From Aggregation|Risposta alla query tramite il recupero dei dati dall'aggregazione. L'abilitazione di questo evento potrebbe causare una riduzione delle prestazioni.|  
|61|Get Data From Cache|Risposta alla query tramite il recupero dei dati da una delle cache. L'abilitazione di questo evento potrebbe causare una riduzione delle prestazioni.|  
|82|VertiPaq SE Query Begin|Query VertiPaq SE|  
|83|VertiPaq SE Query End|Query VertiPaq SE|  
|84|Resource Usage|Indica letture, scritture, utilizzo della CPU dopo la fine di comandi e query.|  
|85|VertiPaq SE Query Cache Match|Utilizzo cache di query VertiPaq SE|  
|98|Direct Query Begin|Inizio di DirectQuery.|  
|99|Direct Query End|Fine di DirectQuery.|  
  
 **[Categoria di eventi Security Audit](security-audit-event-category.md)**  
  
 Raccolta di classi di evento di controllo del database.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|1|Audit Login|Raccoglie tutti i nuovi eventi di connessione generati dopo l'avvio della traccia, ad esempio quando un client richiede una connessione a un server che esegue un'istanza di SQL Server.|  
|2|Audit Logout|Raccoglie tutti i nuovi eventi di disconnessione generati dopo l'avvio della traccia, ad esempio quando un client esegue un comando di disconnessione.|  
|4|Audit Server Starts And Stops|Registra le attività di chiusura, avvio e sospensione.|  
|18|Audit Object Permission Event|Registra le modifiche alle autorizzazioni per gli oggetti.|  
|19|Audit Admin Operations Event|Registra operazioni del server per eseguire il backup, il ripristino, la sincronizzazione, il collegamento, lo scollegamento, il caricamento o il salvataggio di immagini.|  
  
 **[Categoria di eventi eventi di sessione](session-events-event-category.md)**  
  
 Raccolta di eventi di sessione.  
  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|------------------|--------------------|---------------------------|  
|41|Existing Connection|Connessione utente esistente.|  
|42|Existing Session|Sessione esistente.|  
|43|Session Initialize|Inizializzazione della sessione.|  
  
## <a name="see-also"></a>Vedere anche  
[Usare SQL Server Profiler per monitorare Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)
