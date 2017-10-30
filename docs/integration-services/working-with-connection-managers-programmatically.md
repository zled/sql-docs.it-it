---
title: Utilizzo di gestioni connessioni a livello di codice | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connection managers [Integration Services], programming
ms.assetid: 2686fe84-1ecc-48b8-9160-e7122274bd84
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9093b9eadce231aea248cd04c2b57dc5dd5e1a76
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-connection-managers-programmatically"></a>Utilizzo di gestioni connessioni a livello di programmazione
  In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], il metodo AcquireConnection della classe di gestione connessione associata è il metodo viene chiamato più spesso quando si lavora con le gestioni connessioni nel codice gestito. Quando si scrive codice gestito, è necessario chiamare il metodo AcquireConnection per utilizzare la funzionalità di una connessione di gestione. È necessario chiamare questo metodo sia che il codice gestito venga scritto in un'attività Script, in un componente script, in un oggetto personalizzato o in un'applicazione personalizzata.  
  
 Per chiamare il metodo AcquireConnection correttamente, è necessario conoscere le risposte alle domande seguenti:  
  
-   **Quali Gestioni connessione restituiscono un oggetto gestito dal metodo AcquireConnection?**  
  
     Molte gestioni connessioni restituiscono oggetti COM non gestiti ( ComObject) e tali oggetti possono essere facilmente utilizzati da codice gestito. L'elenco di queste gestioni connessioni include la gestione connessione OLE DB utilizzata di frequente.  
  
-   **Per le gestioni connessioni che restituiscono un oggetto gestito, gli oggetti che i relativi metodi AcquireConnection restituiscono?**  
  
     Per eseguire il cast il valore restituito nel tipo appropriato, è necessario conoscere il tipo di oggetto restituisce il metodo AcquireConnection. Ad esempio, il metodo AcquireConnection per il [!INCLUDE[vstecado](../includes/vstecado-md.md)] gestione connessione restituisce un oggetto SqlConnection aperto quando si utilizza il provider SqlClient. Tuttavia, il metodo AcquireConnection per la gestione connessione File restituisce solo una stringa.  
  
 In questo argomento vengono fornite le risposte a queste domande per le gestioni connessioni incluse in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="connection-managers-that-do-not-return-a-managed-object"></a>Gestioni connessione che non restituiscono un oggetto gestito  
 Nella tabella seguente sono elencate le gestioni connessioni che restituiscono un oggetto COM nativo ( ComObject) dal metodo AcquireConnection. Tali oggetti non gestiti non possono essere facilmente utilizzati da codice gestito.  
  
|Tipo di gestione connessione|Nome gestione connessione|  
|-----------------------------|-----------------------------|  
|ADO|Gestione connessione ADO|  
|MSOLAP90|Gestione connessione [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|  
|EXCEL|Gestione connessione Excel|  
|FTP|gestione connessione FTP|  
|HTTP|gestione connessione HTTP|  
|ODBC|gestione connessione ODBC|  
|OLEDB|gestione connessione OLE DB|  
  
 In genere, è possibile utilizzare un [!INCLUDE[vstecado](../includes/vstecado-md.md)] gestione connessione da codice gestito per connettersi a un'origine dati OLE DB, Excel, ODBC o ADO.  
  
## <a name="return-values-from-the-acquireconnection-method"></a>Valori restituiti dal metodo AcquireConnection  
 Nella tabella seguente sono elencate le gestioni connessioni che restituiscono un oggetto gestito dal metodo AcquireConnection. Tali oggetti gestiti possono essere facilmente utilizzati da codice gestito.  
  
|Tipo di gestione connessione|Nome gestione connessione|Tipo di valore restituito|Informazioni aggiuntive|  
|-----------------------------|-----------------------------|--------------------------|----------------------------|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Gestione connessione [!INCLUDE[vstecado](../includes/vstecado-md.md)]|**SqlConnection**||  
|FILE|gestione connessione file|**System. String**|Percorso del file.|  
|FLATFILE|Gestione connessione file flat|**System. String**|Percorso del file.|  
|MSMQ|gestione connessione MSMQ|**System.Messaging.MessageQueue**||  
|MULTIFILE|gestione connessione per più file|**System. String**|Percorso di uno dei file.|  
|MULTIFLATFILE|gestione connessione per più file flat|**System. String**|Percorso di uno dei file.|  
|SMOServer|gestione connessione SMO|**Microsoft.SqlServer.Management.Smo.Server**||  
|SMTP|Gestione connessione SMTP|**System. String**|Ad esempio: `SmtpServer=<server name>;UseWindowsAuthentication=True;EnableSsl=False;`|  
|WMI|Gestione connessione WMI|**System.Management.ManagementScope**||  
|SQLMOBILE|Gestione connessione SQL Server Compact|**System.Data.SqlServerCe.SqlCeConnection**||  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a origini dati nell'attività Script](../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)   
 [Connessione a origini dati nel componente Script](../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)   
 [Connessione alle origini dati in un'attività personalizzata](../integration-services/extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
  
  

