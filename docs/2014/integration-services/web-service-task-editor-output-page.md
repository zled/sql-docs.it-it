---
title: Editor attività servizio Web (pagina Output) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 26
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00d7676916ac06cb82f384202cd2c6f024ffdb65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281547"
---
# <a name="web-service-task-editor-output-page"></a>Editor attività Servizio Web (pagina Output)
  Usare la pagina **Output** della finestra di dialogo **Editor attività Servizio Web** per specificare la posizione in cui archiviare il risultato restituito dal metodo Web.  
  
 Per altre informazioni su questa attività, vedere [Attività Servizio Web](control-flow/web-service-task.md).  
  
## <a name="static-options"></a>Opzioni statiche  
 **OutputType**  
 Consente di selezionare il tipo di archiviazione da utilizzare per l'archiviazione dei risultati. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|**File Connection**|Consente di archiviare i risultati in un file. La selezione di questo valore determina la visualizzazione dell'opzione dinamica **File**.|  
|**Variabile**|Consente di archiviare i risultati in una variabile. La selezione di questo valore determina la visualizzazione dell'opzione dinamica **Variabile**.|  
  
## <a name="outputtype-dynamic-options"></a>Opzioni dinamiche di OutputType  
  
### <a name="outputtype--file-connection"></a>OutputType = Connessione file  
 **File**  
 Selezionare una gestione connessione file nell'elenco o fare clic su \<**Nuova connessione**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>OutputType = Variabile  
 **Variabile**  
 Selezionare una variabile nell'elenco oppure fare clic su \<**Nuova variabile**> per crearne una nuova.  
  
 **Argomenti correlati**  [Variabili di Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Aggiungere una variabile](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività servizio Web &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor attività servizio Web &#40;pagina di Input&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Pagina Espressioni](expressions/expressions-page.md)  
  
  
