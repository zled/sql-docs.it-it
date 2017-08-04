---
title: Bulk Insert Task Editor (pagina connessione) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c837ff29b8f5158620629811352c398a39d30c2c
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="bulk-insert-task-editor-connection-page"></a>Editor attività Inserimento bulk (pagina Connessione)
  Usare la pagina **Connessione** della finestra di dialogo **Editor attività Inserimento bulk** per specificare l'origine e la destinazione dell'operazione di inserimento bulk e il formato da usare.  
  
 Per altre informazioni sulle operazioni di inserimento bulk, vedere [Attività Inserimento bulk](../../integration-services/control-flow/bulk-insert-task.md) e [File di formato per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="options"></a>Opzioni  
 **Connessione**  
 Selezionare una gestione connessione OLE DB nell'elenco oppure fare clic su \< **nuova connessione...** > per creare una nuova connessione.  
  
 **Argomenti correlati:** [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md), [Configura gestione connessione OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 **DestinationTable**  
 Consente di digitare il nome della tabella o della vista di destinazione o di selezionare una tabella o una vista nell'elenco.  
  
 **Formato**  
 Consente di selezionare l'origine del formato per l'inserimento bulk. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Usa file**|Consente di selezionare un file contenente la specifica di formato. Selezionando questa opzione viene visualizzata l'opzione dinamica **FormatFile**.|  
|**Specifica**|Consente di specificare il formato. Selezionando questa opzione vengono visualizzate le opzioni dinamiche **RowDelimiter** e **ColumnDelimiter**.|  
  
 **File**  
 Selezionare una gestione connessione File o File Flat nell'elenco oppure fare clic su \< **nuova connessione...** > per creare una nuova connessione.  
  
 Il percorso del file è relativo al Motore di database di SQL Server specificato nella gestione connessione per questa attività. Il file di testo deve essere accessibile dal Motore di database di SQL Server in un disco rigido locale sul server oppure tramite un'unità condivisa o di cui è stato eseguito il mapping a SQL Server. Non è possibile accedere al file tramite SSIS Runtime.  
  
 Se si accede al file di origine utilizzando una gestione connessione file flat, l'attività Inserimento bulk non utilizzerà il formato specificato nella gestione connessione file flat, ma userà il formato specificato in un file di formato o i valori delle proprietà RowDelimiter e ColumnDelimiter dell'attività.  
  
 **Argomenti correlati:** [Gestione connessione file](../../integration-services/connection-manager/file-connection-manager.md), [Editor gestione connessione file](../../integration-services/connection-manager/file-connection-manager-editor.md), [Gestione connessione file flat](../../integration-services/connection-manager/flat-file-connection-manager.md), [Editor gestione connessione file flat &#40;pagina generale&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md), [Editor gestione connessione file flat &#40;pagina Colonne&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md), [Editor gestione connessione file flat &#40;pagina Avanzate&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)  
  
 **Aggiorna tabelle**  
 Consente di aggiornare l'elenco di tabelle e di viste.  
  
## <a name="format-dynamic-options"></a>Opzioni dinamiche di Format  
  
### <a name="format--use-file"></a>Format = Usa file  
 **FormatFile**  
 Digitare il percorso del file di formato oppure fare clic sui puntini di sospensione **(…)** per trovare il file di formato.  
  
### <a name="format--specify"></a>Format = Specifica  
 **RowDelimiter**  
 Consente di specificare il delimitatore di riga nel file di origine. Il valore predefinito è **{CR}{LF}**.  
  
 **ColumnDelimiter**  
 Consente di specificare il delimitatore di colonna nel file di origine. Il valore predefinito è **Tabulazione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività inserimento bulk &#40; Pagina generale &#41;](../../integration-services/control-flow/bulk-insert-task-editor-general-page.md)   
 [Editor attività inserimento bulk &#40; pagina Opzioni &#41;](../../integration-services/control-flow/bulk-insert-task-editor-options-page.md)   
 [Pagina espressioni](../../integration-services/expressions/expressions-page.md)   
 [INSERIMENTO di MASSA &#40; Transact-SQL &#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  
