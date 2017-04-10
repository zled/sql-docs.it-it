---
title: "Attivit&#224; Monitoraggio eventi WMI | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.wmieventwatchertask.f1"
helpviewer_keywords: 
  - "WQL [Integration Services]"
  - "Monitoraggio eventi WMI - attività [Integration Services]"
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
caps.latest.revision: 53
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 53
---
# Attivit&#224; Monitoraggio eventi WMI
  L'attività Monitoraggio eventi WMI consente di monitorare gli eventi di WMI (Windows Management Instrumentation, Strumentazione gestione Windows) utilizzando una query WQL (Management Instrumentation Query Language) per specificare gli eventi desiderati. È possibile utilizzare l'attività Monitoraggio eventi WMI per gli scopi seguenti:  
  
-   Attendere la notifica dell'aggiunta di file a una cartella e quindi avviare l'elaborazione dei file.  
  
-   Eseguire un pacchetto che elimina file quando la quantità di memoria disponibile in un server è inferiore a una percentuale specificata.  
  
-   Monitorare l'installazione di un'applicazione e quindi eseguire un pacchetto che la utilizza.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include un'attività che consente di leggere le informazioni di WMI.  
  
 Per ulteriori informazioni su questa attività, fare clic sull'argomento seguente:  
  
-   [Attività Lettore di dati WMI](../../integration-services/control-flow/wmi-data-reader-task.md)  
  
## Query WQL  
 WQL è un sottolinguaggio di SQL che include estensioni per supportare la notifica degli eventi WMI e altre caratteristiche specifiche di WMI. Per altre informazioni su WQL, vedere la documentazione di Strumentazione gestione Windows in [MSDN Library](http://go.microsoft.com/fwlink/?linkid=62553).  
  
> [!NOTE]  
>  Le classi WMI variano a seconda della versione di Windows.  
  
 La query seguente esegue il monitoraggio di una notifica che segnala che l'utilizzo della CPU è superiore al 40%.  
  
```  
SELECT * from __InstanceModificationEvent WITHIN 2 WHERE TargetInstance ISA 'Win32_Processor' and TargetInstance.LoadPercentage > 40  
```  
  
 La query seguente esegue il monitoraggio di una notifica che segnala che un file è stato aggiunto a una cartella.  
  
```  
SELECT * FROM __InstanceCreationEvent WITHIN 10 WHERE TargetInstance ISA "CIM_DirectoryContainsFile" and TargetInstance.GroupComponent= "Win32_Directory.Name=\"c:\\\\WMIFileWatcher\""   
```  
  
## Messaggi di registrazione personalizzati disponibili nell'attività Monitoraggio eventi WMI  
 Nella tabella seguente sono elencate le voci di log personalizzate disponibili per l'attività Monitoraggio eventi WMI. Per altre informazioni, vedere [Registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md) e [Messaggi personalizzati per la registrazione](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Voce di log|Description|  
|---------------|-----------------|  
|**WMIEventWatcherEventOccurred**|Indica che si è verificato un evento monitorato dall'attività.|  
|**WMIEventWatcherTimedout**|Indica che si è verificato il timeout dell'attività.|  
|**WMIEventWatcherWatchingForWMIEvents**|Indica che l'attività ha iniziato a eseguire la query WQL. La voce include la query.|  
  
## Configurazione dell'attività Monitoraggio eventi WMI  
 Per configurare l'attività Lettore di dati WMI, procedere nel modo seguente:  
  
-   Specificare la gestione connessione WMI da utilizzare.  
  
-   Specificare l'origine della query WQL. È possibile utilizzare query con origine esterna all'attività, una variabile o un file, oppure archiviate in una proprietà dell'attività.  
  
-   Specificare l'operazione che deve essere eseguita dall'attività quando si verifica l'evento WMI. È possibile registrare la notifica dell'evento e lo stato dopo l'evento oppure generare eventi di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] personalizzati che forniscono informazioni associate all'evento WMI, la notifica e lo stato dopo l'evento.  
  
-   Definire la risposta dell'attività all'evento. È possibile configurare l'attività in modo da riuscire o non riuscire, a seconda dell'evento, oppure da riprendere semplicemente il monitoraggio dell'evento.  
  
-   Specificare l'operazione che deve essere eseguita dall'attività al timeout della query WQL. È possibile registrare il timeout e lo stato dopo il timeout oppure generare un evento di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] personalizzato che indica che si è verificato il timeout dell'evento WMI e registra il timeout e lo stato dopo il timeout.  
  
-   Definire la risposta dell'attività al timeout. È possibile configurare l'attività in modo da riuscire o non riuscire oppure da riprendere semplicemente il monitoraggio dell'evento.  
  
-   Specificare il numero di volte per cui monitorare l'evento.  
  
-   Specificare il timeout.  
  
 Se l'origine è un file, l'attività Monitoraggio eventi WMI utilizzerà una gestione connessione file per connettersi al file. Per ulteriori informazioni, vedere [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 L'attività Monitoraggio eventi WMI utilizza una gestione connessione WMI per connettersi al server da cui legge le informazioni di WMI. Per altre informazioni, vedere [Gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager.md).  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Editor attività Monitoraggio eventi WMI &#40;pagina Generale&#41;](../../integration-services/control-flow/wmi-event-watcher-task-editor-general-page.md)  
  
-   [Editor attività Monitoraggio eventi WMI &#40;pagina Opzioni WMI&#41;](../../integration-services/control-flow/wmi-event-watcher-task-editor-wmi-options-page.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Configurazione a livello di codice dell'attività Monitoraggio eventi WMI  
 Per ulteriori informazioni sull'impostazione di queste proprietà a livello di codice, fare clic sull'argomento seguente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
  