---
title: "Attivit&#224; Lettore di dati WMI | Microsoft Docs"
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
  - "sql13.dts.designer.wmidatareadertask.f1"
helpviewer_keywords: 
  - "WQL [Integration Services]"
  - "Lettore di dati WMI - attività [Integration Services]"
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# Attivit&#224; Lettore di dati WMI
  L'attività Lettore di dati WMI esegue query che utilizzano il linguaggio di query di WMI (Windows Management Instrumentation, Strumentazione gestione Windows) per ottenere da WMI informazioni su un sistema informatico. È possibile utilizzare l'attività Lettore di dati WMI per gli scopi seguenti:  
  
-   Eseguire query sul registro eventi di Windows di un computer locale o remoto e scrivere le informazioni ottenute in un file o in una variabile.  
  
-   Ottenere informazioni sulla presenza, lo stato o le proprietà dei componenti hardware e quindi utilizzare tali informazioni per determinare se altre attività nel flusso di controllo devono essere eseguite o meno.  
  
-   Ottenere un elenco di applicazioni e determinare le versioni installate.  
  
 Per configurare l'attività Lettore di dati WMI, procedere nel modo seguente:  
  
-   Specificare la gestione connessione WMI da utilizzare.  
  
-   Specificare l'origine della query WQL. La query può essere archiviata in una proprietà dell'attività o all'esterno dell'attività, in una variabile o in un file.  
  
-   Definire il formato dei risultati della query WQL. L'attività supporta le tabelle, le coppie nome/valore delle proprietà e i valori di proprietà.  
  
-   Specificare la destinazione della query, che può essere costituita da una variabile o da un file.  
  
-   Indicare se la destinazione della query verrà sovrascritta o mantenuta oppure se i nuovi dati verranno accodati a quelli esistenti.  
  
 Se la destinazione è un file, l'attività Lettore di dati WMI utilizzerà una gestione connessione file per connettersi al file. Per ulteriori informazioni, vedere [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 L'attività Lettore di dati WMI utilizza una gestione connessione WMI per connettersi al server da cui legge le informazioni di WMI. Per altre informazioni, vedere [Gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager.md).  
  
## Query WQL  
 WQL è un sottolinguaggio di SQL che include estensioni per supportare la notifica degli eventi WMI e altre caratteristiche specifiche di WMI. Per altre informazioni su WQL, vedere la documentazione di Strumentazione gestione Windows in [MSDN Library](http://go.microsoft.com/fwlink/?linkid=7022).  
  
> [!NOTE]  
>  Le classi WMI variano a seconda della versione di Windows.  
  
 La query WQL seguente restituisce le voci contenute nel registro eventi applicazioni.  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 La query WQL seguente restituisce informazioni sui dischi logici.  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 La query WQL seguente restituisce un elenco degli aggiornamenti QFE (Quick Fix Engineering) applicati al sistema operativo.  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## Messaggi di registrazione personalizzati disponibili nell'attività Lettore di dati WMI  
 Nella tabella seguente sono elencate le voci di log personalizzate disponibili per l'attività Lettore di dati WMI. Per altre informazioni, vedere [Registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md) e [Messaggi personalizzati per la registrazione](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Voce di log|Description|  
|---------------|-----------------|  
|**WMIDataReaderGettingWMIData**|Indica che l'attività ha iniziato a leggere dati WMI.|  
|**WMIDataReaderOperation**|Specifica la query WQL eseguita dall'attività.|  
  
## Configurazione dell'attività Lettore di dati WMI  
 È possibile impostare le proprietà a livello di programmazione o tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Per informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], fare clic su uno degli argomenti seguenti:  
  
-   [Editor attività Lettore di dati WMI &#40;pagina Opzioni WMI&#41;](../../integration-services/control-flow/wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per informazioni sull'impostazione di queste proprietà a livello di codice, fare clic sull'argomento seguente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## Attività correlate  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Vedere anche  
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  