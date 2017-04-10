---
title: "Editor attivit&#224; Servizio Web (pagina Output) | Microsoft Docs"
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
  - "sql13.dts.designer.webservicestask.output.f1"
helpviewer_keywords: 
  - "Editor attività Servizio Web"
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Editor attivit&#224; Servizio Web (pagina Output)
  Usare la pagina **Output** della finestra di dialogo **Editor attività Servizio Web** per specificare la posizione in cui archiviare il risultato restituito dal metodo Web.  
  
 Per altre informazioni su questa attività, vedere [Attività Servizio Web](../../integration-services/control-flow/web-service-task.md).  
  
## Opzioni statiche  
 **OutputType**  
 Consente di selezionare il tipo di archiviazione da utilizzare per l'archiviazione dei risultati. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Value|Description|  
|-----------|-----------------|  
|**File Connection**|Consente di archiviare i risultati in un file. La selezione di questo valore determina la visualizzazione dell'opzione dinamica **File**.|  
|**Variabile**|Consente di archiviare i risultati in una variabile. La selezione di questo valore determina la visualizzazione dell'opzione dinamica **Variabile**.|  
  
## Opzioni dinamiche di OutputType  
  
### OutputType = Connessione file  
 **File**  
 Selezionare una gestione connessione file nell'elenco oppure fare clic su \<**Nuova connessione**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### OutputType = Variabile  
 **Variabile**  
 Selezionare una variabile nell'elenco oppure fare clic su \<**Nuova variabile**> per crearne una nuova.  
  
 **Argomenti correlati:**  [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Aggiungi variabile](../Topic/Add%20Variable.md)  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Servizio Web &#40;pagina Generale&#41;](../../integration-services/control-flow/web-service-task-editor-general-page.md)   
 [Editor attività Servizio Web &#40;pagina Input&#41;](../../integration-services/control-flow/web-service-task-editor-input-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
  