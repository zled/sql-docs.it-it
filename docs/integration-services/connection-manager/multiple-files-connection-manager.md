---
title: "Gestione connessione per pi&#249; file | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cartelle [Integration Services], connessioni"
  - "file [Integration Services], connessioni"
  - "gestione connessione per più file"
  - "gestioni connessioni [Integration Services], più file"
  - "connessioni [Integration Services], file"
  - "connessioni per più file"
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 36
---
# Gestione connessione per pi&#249; file
  Una gestione connessione per più file consente a un pacchetto di fare riferimento a file e cartelle esistenti o di creare file e cartelle in fase di esecuzione.  
  
> [!NOTE]  
>  Le attività predefinite e i componenti del flusso di dati in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] non utilizzano la gestione connessione per più file. È tuttavia possibile utilizzare la gestione connessione nell'attività Script o nel componente di script. Per informazioni sull'uso delle gestioni connessioni nell'attività Script, vedere [Connessione a origini dati nell'attività Script](../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md). Per informazioni sull'uso delle gestioni connessioni nel componente Script, vedere [Connessione a origini dati nel componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
## Tipi di utilizzo per la gestione connessione per più file  
 La proprietà **FileUsageType** della gestione connessione per più file specifica la modalità di uso della connessione. La gestione connessione per più file consente sia di creare file e cartelle, sia di utilizzare file e cartelle esistenti.  
  
 Nella tabella seguente vengono elencati i possibili valori di **FileUsageType**.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**0**|La gestione connessione per più file utilizza un file esistente.|  
|**1**|La gestione connessione per più file crea un file.|  
|**2**|La gestione connessione per più file utilizza una cartella esistente.|  
|**3**|La gestione connessione per più file crea una cartella.|  
  
## Configurazione della gestione connessione per più file  
 Quando si aggiunge una gestione connessione per più file a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione per più file, imposta le proprietà di tale connessione e quindi la aggiunge alla raccolta **Connections** del pacchetto.  
  
 La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **MULTIFILE**.  
  
 Per configurare una gestione connessione per più file, procedere nel modo seguente:  
  
-   Specificare il tipo di utilizzo di file e cartelle.  
  
-   Specificare file e cartelle.  
  
-   Se si utilizzano più file e cartelle, specificare l'ordine con cui accedere a tali elementi.  
  
 Se la gestione connessione per più file fa riferimento a più file e cartelle, i percorsi dei file e delle cartelle sono separati da una barra verticale. La proprietà **ConnectionString** della gestione connessione ha il formato seguente:  
  
 \<*percorso*>|\<*percorso*>  
  
 Per specificare più file o cartelle è inoltre possibile utilizzare caratteri jolly. Per fare riferimento, ad esempio, a tutti i file di testo sull'unità C è possibile impostare il valore della proprietà **ConnectionString** su C:\\*.txt.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], vedere [Riferimento all'interfaccia utente della finestra di dialogo Aggiungi gestione connessione file](../../integration-services/connection-manager/add-file-connection-manager-dialog-box-ui-reference.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  