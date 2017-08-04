---
title: "Editor attività (pagina generale) Profiling dati | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataprofilingtask.general.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: eec15906-d757-4079-b2f6-aca4e52b3b4c
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f5acdf3ae4f27685fce7aab56aab423044491ee1
ms.openlocfilehash: bed1fa78db9ee0beca66efe57f088d1d74d377f2
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="data-profiling-task-editor-general-page"></a>Editor attività Profiling dati (pagina Generale)
  Usare la pagina **Generale** di **Editor attività Profiling dati** per configurare le opzioni seguenti:  
  
-   Specificare la destinazione per l'output del profilo.  
  
-   Utilizzare le impostazioni predefinite per semplificare l'attività di profiling di una singola tabella o vista.  
  
 Per altre informazioni sull'uso dell'attività Profiling dati, vedere [Impostazione dell'attività Profiling dati](../../integration-services/control-flow/setup-of-the-data-profiling-task.md). Per altre informazioni sull'uso del Visualizzatore profilo dati per analizzare l'output dell'attività Profiling dati, vedere [Visualizzatore profilo dati](../../integration-services/control-flow/data-profile-viewer.md).  
  
 **Per aprire la pagina Generale in Editor attività Profiling dati**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenente l'attività Profiling dati.  
  
2.  Nella scheda **Flusso di controllo** fare doppio clic sull'attività Profiling dati.  
  
3.  In **Editor attività Profiling dati**fare clic su **Generale**.  
  
## <a name="data-profiling-options"></a>Opzioni di profiling dei dati  
 **Timeout**  
 Specifica il numero di secondi dopo il quale attivare il timeout dell'attività Profiling dati e arrestarne l'esecuzione. Il valore predefinito è 0, che non specifica alcun timeout.  
  
## <a name="destination-options"></a>Opzioni destinazione  
  
> [!IMPORTANT]  
>  Il file di output potrebbe contenere dati sensibili sul database e i dati inclusi nel database. Per suggerimenti su come rendere più sicuro questo file, vedere [Accesso ai file utilizzati dai pacchetti](../../integration-services/security/security-overview-integration-services.md#files).  
  
 **DestinationType**  
 Consente di specificare se salvare l'output del profilo dei dati in un file o una variabile:  
  
|Value|Description|  
|-----------|-----------------|  
|**FileConnection**|Consente di salvare l'output del profilo in un file nel percorso specificato in una gestione connessione file.<br /><br /> Nota: è possibile specificare la gestione connessione file da usare tramite l'opzione **Destination** .|  
|**Variabile**|Consente di salvare l'output del profilo in una variabile del pacchetto.<br /><br /> Nota: è possibile specificare la variabile del pacchetto da usare tramite l'opzione **Destination** .|  
  
 **Destination**  
 Consente di specificare la gestione connessione file o la variabile del pacchetto contenente l'output del profilo dei dati:  
  
-   Se l'opzione **DestinationType** è impostata su **FileConnection**, l'opzione **Destination** visualizza le gestioni connessione file disponibili. Selezionare una di queste gestioni connessioni, oppure \<nuova connessione File > per creare una nuova connessione di File manager.  
  
-   Se l'opzione **DestinationType** è impostata su **Variable**, l'opzione **Destination** visualizza le variabili del pacchetto disponibili nell'elenco **Destination** . Selezionare una di queste variabili, oppure \<nuova variabile > per creare una nuova variabile.  
  
 **OverwriteDestination**  
 Consente di specificare se sovrascrivere il file di output, se presente. Il valore predefinito è **False**. Il valore di questa proprietà viene utilizzato solo quando l'opzione DestinationType è impostata su FileConnection. Quando l'opzione DestinationType è impostata su Variable, l'attività sovrascrive sempre il valore precedente della variabile.  
  
> [!IMPORTANT]  
>  Se si tenta di eseguire l'attività Profiling dati più di una volta senza modificare il nome del file di output o impostare il valore della proprietà **OverwriteDestination** su **True**, l'attività restituirà un errore e un messaggio indicante che il file di output è già presente.  
  
## <a name="other-options"></a>Altre opzioni  
 **Profilo rapido**  
 Consente di visualizzare l'opzione **Form profilo rapido singola tabella**. Questo form semplifica l'attività di profiling di una singola tabella o vista tramite le impostazioni predefinite. Per altre informazioni, vedere [Form profilo rapido singola tabella &#40;Attività Profiling dati&#41;](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md).  
  
 **Apri Visualizzatore profilo**  
 Consente di aprire il Visualizzatore profilo dati. Il Visualizzatore profilo dati autonomo visualizza l'output del profilo dei dati dall'attività Profiling dati. È possibile visualizzare l'output del profilo dei dati dopo avere eseguito l'attività Profiling dati nel pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e aver calcolato i profili dati.  
  
> [!NOTE]  
>  È anche possibile aprire il Visualizzatore profilo dati eseguendo DataProfileViewer.exe nella cartella  *\<unità >*: il file \Programmi (x86) | C:\Programmi\Microsoft SQL Server\110\DTS\Binn del programma.  
  
## <a name="see-also"></a>Vedere anche  
 [Form profilo rapido singola tabella &#40;Attività Profiling dati&#41;](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md)   
 [Dati di profilatura Editor attività &#40; Pagina richieste profilo &#41;](../../integration-services/control-flow/data-profiling-task-editor-profile-requests-page.md)  
  
  
