---
title: "Editor attivit&#224; Lettore di dati WMI (pagina Opzioni WMI) | Microsoft Docs"
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
  - "sql13.dts.designer.wmidatareadertask.wmiquery.f1"
helpviewer_keywords: 
  - "Editor attività Lettore di dati WMI"
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Editor attivit&#224; Lettore di dati WMI (pagina Opzioni WMI)
  Usare la pagina **Opzioni WMI** della finestra di dialogo **Editor attività Lettore di dati WMI** per specificare l'origine della query WQL (Windows Management Instrumentation Query Language) e la destinazione del risultato della query.  
  
 Per ulteriori informazioni su questa attività, vedere [WMI Data Reader Task](../../integration-services/control-flow/wmi-data-reader-task.md). Per altre informazioni su WQL (WMI Query Language), vedere l'argomento relativo a WMI (Windows Management Instrumentation) [Querying with WQL](http://go.microsoft.com/fwlink/?LinkId=79045) (Query con WQL) in MSDN Library.  
  
## Opzioni statiche  
 **WMIConnectionName**  
 Consente di selezionare una gestione connessione WMI nell'elenco o di creare una nuova gestione connessione facendo clic su \<**Nuova connessione WMI**>.  
  
 **Argomenti correlati**: [Gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager.md), [Editor gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Consente di selezionare il tipo di origine della query WQL eseguita dall'attività. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Input diretto**|Consente di impostare l'origine su una query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySourceType**.|  
|**Connessione file**|Consente di selezionare un file contenente la query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySourceType**.|  
|**Variabile**|Consente di impostare l'origine su una variabile che definisce la query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySourceType**.|  
  
 **OutputType**  
 Consente di specificare se l'output deve essere una tabella di dati, un valore di proprietà o un nome e valore di proprietà.  
  
 **OverwriteDestination**  
 Consente di specificare se mantenere, sovrascrivere o accodare ai dati originali nel file o nella variabile di destinazione.  
  
 **DestinationType**  
 Consente di selezionare il tipo di destinazione della query WQL eseguita dall'attività. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Connessione file**|Selezionare un file in cui salvare i risultati della query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **DestinationType**.|  
|**Variabile**|Impostare la variabile in cui archiviare i risultati della query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **DestinationType**.|  
  
## Opzioni dinamiche di WQLQuerySourceType  
  
### WQLQuerySourceType = Input diretto  
 **WQLQuerySource**  
 Consente di specificare una query o di immettere una query nella finestra di dialogo **Query WQL** visualizzata facendo clic sul pulsante (...).  
  
### WQLQuerySourceType = Connessione file  
 **WQLQuerySource**  
 Selezionare una gestione connessione file nell'elenco oppure fare clic su \<**Nuova connessione**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### WQLQuerySourceType = Variabile  
 **WQLQuerySource**  
 Selezionare una variabile nell'elenco oppure fare clic su **Nuova variabile** per crearne una nuova.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Aggiungi variabile](../Topic/Add%20Variable.md)  
  
## Opzioni dinamiche di DestinationType  
  
### DestinationType = Connessione file  
 **Destinazione**  
 Selezionare una gestione connessione file nell'elenco oppure fare clic su \<**Nuova connessione**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### DestinationType = Variabile  
 **Destinazione**  
 Selezionare una variabile nell'elenco oppure fare clic su **Nuova variabile** per crearne una nuova.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Aggiungi variabile](../Topic/Add%20Variable.md)  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Lettore di dati WMI &#40;pagina Generale&#41;](../../integration-services/control-flow/wmi-data-reader-task-editor-general-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)   
 [Attività Monitoraggio eventi WMI](../../integration-services/control-flow/wmi-event-watcher-task.md)  
  
  