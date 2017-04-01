---
title: "Gestori eventi di Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di Integration Services, eventi"
  - "run-time [Integration Services]"
  - "pacchetti di SQL Server Integration Services, eventi"
  - "gestori eventi [Integration Services], informazioni sui gestori eventi"
  - "eventi [Integration Services]"
  - "pacchetti [Integration Services], eventi"
  - "gestori eventi [Integration Services]"
  - "pacchetti SSIS, eventi"
  - "contenitori [Integration Services], eventi"
  - "eventi [Integration Services], informazioni sugli eventi"
ms.assetid: 6f60cf93-35dc-431c-908d-2049c4ab66ba
caps.latest.revision: 52
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 51
---
# Gestori eventi di Integration Services (SSIS)
  Durante la fase di esecuzione gli eseguibili, costituiti da pacchetti e contenitori Ciclo Foreach, Ciclo For, Sequenza e Host attività, generano eventi. Quando si verifica un errore, ad esempio, viene generato l'evento OnError. È possibile creare gestori di eventi personalizzati per tali eventi, per estendere le funzionalità dei pacchetti e semplificarne la gestione in fase di esecuzione. I gestori di eventi possono eseguire varie attività, ad esempio:  
  
-   Cancellare l'archivio dati temporaneo al termine dell'esecuzione di un pacchetto o attività.  
  
-   Recuperare informazioni di sistema per verificare la disponibilità delle risorse prima dell'esecuzione di un pacchetto.  
  
-   Aggiornare dati in una tabella quando una ricerca in una tabella di riferimento non riesce.  
  
-   Inviare un messaggio di posta elettronica quando viene generato un errore o un avviso oppure quando un'attività non riesce.  
  
 Se per un evento non esiste alcun gestore, tale evento verrà passato al contenitore di livello immediatamente superiore nella gerarchia dei contenitori del pacchetto. Se il contenitore dispone di un gestore di evento, quest'ultimo verrà eseguito in risposta all'evento, in caso contrario l'evento verrà passato al contenitore di livello immediatamente superiore nella gerarchia dei contenitori.  
  
 Nella figura seguente viene illustrato un semplice pacchetto che include un contenitore Ciclo For contenente un'attività Esegui SQL.  
  
 ![Pacchetto, Ciclo For, host di attività e attività Esegui SQL](../integration-services/media/mw-dts-eventhandlerpkg.gif "Pacchetto, Ciclo For, host di attività e attività Esegui SQL")  
  
 Solo il pacchetto dispone di un gestore di evento per il proprio evento **OnError** . Se si verifica un errore mentre viene eseguita l'attività Esegui SQL, verrà eseguito il gestore dell'evento **OnError** del pacchetto. Nella figura seguente viene illustrata la sequenza di chiamate che provoca l'esecuzione del gestore dell'evento **OnError** per il pacchetto.  
  
 ![Flusso del gestore dell'evento](../integration-services/media/mw-dts-eventhandlers.gif "Flusso del gestore dell'evento")  
  
 I gestori di eventi sono membri di un insieme di gestori di eventi, disponibile in tutti i contenitori. Se si crea un pacchetto utilizzando Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] , sarà possibile visualizzare i membri dell'insieme dei gestori di eventi nelle cartelle **Gestori eventi** della scheda **Esplora pacchetti** di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 Per configurare il contenitore di un gestore di evento, procedere nel modo seguente:  
  
-   Specificare un nome e una descrizione per il gestore di evento.  
  
-   Indicare se il gestore di evento viene eseguito, se il pacchetto deve generare un errore in caso di errore del gestore di evento e il numero di errori che possono verificarsi prima che il gestore di evento generi a sua volta un errore.  
  
-   Specificare il risultato di esecuzione da restituire al posto di quello effettivamente restituito dal gestore di evento in fase di esecuzione.  
  
-   Specificare l'opzione relativa alle transazioni per il gestore di evento.  
  
-   Specificare la modalità di registrazione utilizzata dal gestore di evento.  
  
## Contenuto di un gestore di evento  
 La creazione di un gestore di evento è simile alla compilazione di un pacchetto. Un gestore di evento include attività e contenitori, ordinati in sequenza in modo da formare un flusso di controllo, e può includere anche flussi di dati. In Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] è disponibile la scheda **Gestori eventi** , che consente di creare gestori di eventi personalizzati.  
  
 È possibile creare gestori di eventi anche a livello di codice. Per altre informazioni, vedere [Gestione degli eventi a livello di programmazione](../integration-services/building-packages-programmatically/handling-events-programmatically.md).  
  
## Eventi di run-time  
 Nella tabella seguente vengono elencati i gestori di eventi disponibili in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e vengono descritti gli eventi di run-time che ne provocano l'esecuzione.  
  
|Gestore di evento|Evento|  
|-------------------|-----------|  
|**OnError**|Gestore di evento per l'evento **OnError** . Questo evento viene generato da un eseguibile quando si verifica un errore.|  
|**OnExecStatusChanged**|Gestore di evento per l'evento **OnExecStatusChanged** . Questo evento viene generato da un eseguibile quando cambia il suo stato di esecuzione.|  
|**OnInformation**|Gestore di evento per l'evento **OnInformation** . Questo evento viene generato durante la convalida e l'esecuzione di un eseguibile, allo scopo di fornire informazioni. Questo evento fornisce solo informazioni, non errori o avvisi.|  
|**OnPostExecute**|Gestore di evento per l'evento **OnPostExecute** . Questo evento viene generato da un eseguibile immediatamente dopo la fine dell'esecuzione.|  
|**OnPostValidate**|Gestore di evento per l'evento **OnPostValidate** . Questo evento viene generato da un eseguibile al termine della convalida.|  
|**OnPreExecute**|Gestore di evento per l'evento **OnPreExecute** . Questo evento viene generato da un eseguibile immediatamente prima della sua esecuzione.|  
|**OnPreValidate**|Gestore di evento per l'evento **OnPreValidate** . Questo evento viene generato da un eseguibile all'inizio della sua convalida.|  
|**OnProgress**|Gestore di evento per l'evento **OnProgress** . Questo evento viene generato da un eseguibile quando compie un avanzamento misurabile.|  
|**OnQueryCancel**|Gestore di evento per l'evento **OnQueryCancel** . Questo evento viene generato da un eseguibile per determinare se l'esecuzione deve essere arrestata.|  
|**OnTaskFailed**|Gestore di evento per l'evento **OnTaskFailed** . Questo evento viene generato da un'attività quando non riesce.|  
|**OnVariableValueChanged**|Gestore di evento per l'evento **OnVariableValueChanged** . Questo evento viene generato da un eseguibile quando il valore di una variabile viene modificato. L'evento viene generato dall'eseguibile in cui è definita la variabile. Se la proprietà **RaiseChangeEvent** della variabile è impostata su **False**, questo evento non verrà generato. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../integration-services/integration-services-ssis-variables.md).|  
|**OnWarning**|Gestore di evento per l'evento **OnWarning** . Questo evento viene generato da un eseguibile quando viene generato un avviso.|  
  
## Configurazione di un gestore dell'evento  
 È possibile impostare le proprietà a livello di codice o nella finestra **Proprietà** di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] .  
  
 Per informazioni su come impostare queste proprietà nella finestra di Progettazione [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vedere [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
 Per informazioni sull'impostazione di queste proprietà a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.  
  
## Attività correlate  
 Per informazioni su come aggiungere un gestore eventi a un pacchetto, vedere [Aggiunta di un gestore eventi a un pacchetto](../Topic/Add%20an%20Event%20Handler%20to%20a%20Package.md).  
  
  