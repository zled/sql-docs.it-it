---
title: "Editor attività di monitoraggio eventi WMI (pagina Opzioni WMI) | Documenti Microsoft"
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
- sql13.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 410a65bf316b27fac565388d09bf4c9f5cd82b29
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>Editor attività Monitoraggio eventi WMI (pagina Opzioni WMI)
  Usare la pagina **Opzioni WMI** della finestra di dialogo **Editor attività Monitoraggio eventi WM** per specificare l'origine della query WQL e la modalità di risposta dell'attività Monitoraggio eventi WMI agli eventi del servizio Strumentazione Gestione Windows (WMI).  
  
 Per ulteriori informazioni su questa attività, vedere [WMI Event Watcher Task](../../integration-services/control-flow/wmi-event-watcher-task.md). Per altre informazioni su WQL (WMI Query Language), vedere l'argomento relativo a WMI (Windows Management Instrumentation) " [Query con WQL](http://go.microsoft.com/fwlink/?LinkId=79045)" in MSDN Library.  
  
## <a name="static-options"></a>Opzioni statiche  
 **WMIConnectionName**  
 Selezionare una gestione connessione WMI nell'elenco oppure fare clic su \< **nuova connessione WMI...** > per creare una nuova gestione connessione.  
  
 **Argomenti correlati**: [Gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager.md), [Editor gestione connessione WMI](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Consente di selezionare il tipo di origine della query WQL eseguita dall'attività. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Input diretto**|Consente di impostare l'origine su una query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySource**.|  
|**Connessione file**|Consente di selezionare un file contenente la query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySource**.|  
|**Variabile**|Consente di impostare l'origine su una variabile che definisce la query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySource**.|  
  
 **ActionAtEvent**  
 Consente di specificare se l'evento WMI registra l'evento e inizia un'azione [!INCLUDE[ssIS](../../includes/ssis-md.md)] oppure se si limita a registrare l'evento.  
  
 **AfterEvent**  
 Consente di specificare se l'attività ha esito positivo o negativo dopo avere ricevuto l'evento WMI oppure se deve continuare a monitorare l'evento per controllare se viene generato nuovamente.  
  
 **ActionAtTimeout**  
 Consente di specificare se l'attività registra un timeout della query WMI e inizia un evento [!INCLUDE[ssIS](../../includes/ssis-md.md)] in risposta oppure se si limita a registrare il timeout.  
  
 **AfterTimeout**  
 Consente di specificare se l'attività ha esito positivo o negativo in risposta a un timeout oppure se deve continuare il monitoraggio per controllare se viene generato un altro timeout.  
  
 **NumberOfEvents**  
 Consente di specificare il numero di eventi da monitorare.  
  
 **Timeout**  
 Consente di specificare il numero di secondi di attesa per la generazione dell'evento. Un valore pari a 0 significa che non è attivo alcun timeout.  
  
## <a name="wqlquerysource-dynamic-options"></a>Opzioni dinamiche di WQLQuerySource  
  
### <a name="wqlquerysource--direct-input"></a>WQLQuerySource = Input diretto  
 **WQLQuerySource**  
 Consente di specificare una query o di immettere una query nella finestra di dialogo **Query WQL** visualizzata facendo clic sul pulsante (...).  
  
### <a name="wqlquerysource--file-connection"></a>WQLQuerySource = Connessione file  
 **WQLQuerySource**  
 Selezionare una gestione connessione File nell'elenco oppure fare clic su \< **nuova connessione...** > per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### <a name="wqlquerysource--variable"></a>WQLQuerySource = Variabile  
 **WQLQuerySource**  
 Selezionare una variabile nell'elenco oppure fare clic su \< **nuova variabile...** > per creare una nuova variabile.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Aggiungi variabile](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Monitoraggio eventi WMI &#40; Pagina generale &#41;](../../integration-services/control-flow/wmi-event-watcher-task-editor-general-page.md)   
 [Pagina espressioni](../../integration-services/expressions/expressions-page.md)   
 [Attività lettore di dati WMI](../../integration-services/control-flow/wmi-data-reader-task.md)  
  
  
