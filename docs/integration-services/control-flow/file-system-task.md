---
title: "Attivit&#224; File system | Microsoft Docs"
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
  - "sql13.dts.designer.filesystemtask.f1"
helpviewer_keywords: 
  - "File system - attività [Integration Services]"
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
caps.latest.revision: 58
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# Attivit&#224; File system
  L'attività File system consente di eseguire operazioni su file e directory nel file system. Tramite l'attività File system un pacchetto può ad esempio creare, spostare o eliminare file e directory. È inoltre possibile utilizzare l'attività File system per impostare attributi su file e directory, ad esempio per impostare file come nascosti o in sola lettura.  
  
 Tutte le operazioni dell'attività File system utilizzano un'origine, che può essere costituita da un file o una directory. Il file copiato o la directory eliminata tramite un'attività è un'origine. L'origine può essere specificata tramite una gestione connessione file che punta alla directory o al file oppure specificando il nome di una variabile che contiene il percorso dell'origine. Per altre informazioni, vedere [Gestione connessione File](../../integration-services/connection-manager/file-connection-manager.md) e [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md).  
  
 Le operazioni che prevedono la copia e lo spostamento di file e directory oppure la ridenominazione di file utilizzano un'origine e una destinazione. La destinazione viene specificata utilizzando una gestione connessione file o una variabile. Le operazioni dell'attività File system possono essere configurate in modo da consentire la sovrascrittura dei file e delle directory di destinazione. L'operazione con cui viene creata una nuova directory può essere configurata in modo da utilizzare una directory esistente con il nome specificato anziché avere esito negativo se la directory esiste già.  
  
## Operazioni predefinite dell'attività File system   
 L'attività File system include un set predefinito di operazioni, descritte nella tabella seguente.  
  
|Operazione|Description|  
|---------------|-----------------|  
|Copia directory|Copia una cartella da un percorso a un altro.|  
|Copia file|Copia un file da un percorso a un altro.|  
|Crea directory|Crea una cartella in un percorso specificato.|  
|Elimina directory|Elimina una cartella in un percorso specificato.|  
|Elimina contenuto directory|Elimina tutti i file e le cartelle contenute in una cartella.|  
|Elimina file|Elimina un file in un percorso specificato.|  
|Sposta directory|Sposta una cartella da un percorso a un altro.|  
|Sposta file|Sposta un file da un percorso a un altro.|  
|Rinomina file|Rinomina un file in un percorso specificato.|  
|Imposta attributi|Imposta attributi su file e cartelle. Tali attributi includono Archive, Hidden, Normal, ReadOnly e System. Normal indica la mancanza di attributi e non può essere combinato con altri attributi. Tutti gli altri attributi possono essere utilizzati in combinazione.|  
  
 L'attività File system opera su un singolo file o directory. Pertanto, questa attività non supporta l'utilizzo di caratteri jolly per eseguire la stessa operazione su più file. Affinché l'attività File system ripeta un'operazione su più file o directory, inserire l'attività File system in un contenitore Ciclo Foreach, come descritto nella procedura seguente:  
  
-   **Configurare il contenitore Ciclo Foreach** Nella pagina **Raccolta** dell'Editor ciclo Foreach, impostare l'enumeratore su **Enumeratore Foreach File** e immettere l'espressione con caratteri jolly come configurazione dell'enumeratore per **File**. Nella pagina **Mapping variabili** dell'Editor ciclo Foreach, eseguire il mapping di una variabile che si desidera usare per passare uno alla volta i nomi dei file all'attività File System.  
  
-   **Aggiungere e configurare un'attività File System** Aggiungere un'attività File System al contenitore Ciclo Foreach. Nella pagina **Generale** dell'Editor attività File system, impostare la proprietà **SourceVariable** o **DestinationVariable** sulla variabile definita nel contenitore Ciclo Foreach.  
  
## Voci di log personalizzate disponibili nell'attività File System  
 Nella tabella seguente sono elencate le voci di log personalizzate disponibili per l'attività File system. Per altre informazioni, vedere [Registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md) e [Messaggi personalizzati per la registrazione](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Voce di log|Description|  
|---------------|-----------------|  
|**FileSystemOperation**|Indica l'operazione eseguita dall'attività. Questa voce di log viene scritta all'inizio dell'operazione sul file system e include informazioni sull'origine e sulla destinazione.|  
  
## Configurazione dell'attività File system  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], vedere gli argomenti seguenti:  
  
-   [Editor attività File system &#40;pagina Generale&#41;](../../integration-services/control-flow/file-system-task-editor-general-page.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], vedere l'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
 Per ulteriori informazioni sull'impostazione di queste proprietà a livello di codice, vedere l'argomento seguente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>  
  
## Attività correlate  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include un'attività che consente di eseguire il download e il caricamento di file di dati, nonché di gestire directory sui server. Per altre informazioni, vedere [Attività FTP](../../integration-services/control-flow/ftp-task.md).  
  
## Vedere anche  
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  