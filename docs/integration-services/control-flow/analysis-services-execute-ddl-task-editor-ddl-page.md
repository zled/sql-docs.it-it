---
title: "Analysis Services Editor attività Esegui DDL (pagina DDL) | Documenti Microsoft"
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
- sql13.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4bae07f66d84f8a692ad7b59ef61ee63d4a5fd62
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>Editor attività Esegui DDL Analysis Services (pagina DDL)
  La pagina **DDL** della finestra di dialogo **Editor attività Esegui DDL Analysis Services** consente di specificare una connessione a un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per offrire informazioni sull'origine delle istruzioni DDL (Data Definition Language).  
  
 Per altre informazioni su questa attività, vedere [Attività Esegui DDL Analysis Services](../../integration-services/control-flow/analysis-services-execute-ddl-task.md).  
  
## <a name="static-options"></a>Opzioni statiche  
 **Connessione**  
 Selezionare un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto o un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gestione connessione nell'elenco oppure fare clic su \< **nuova connessione...** > e utilizzare il **Aggiungi gestione connessione Analysis Services** la finestra di dialogo per creare una nuova connessione.  
  
 **Argomenti correlati:** [Riferimento all'interfaccia utente della finestra di dialogo Aggiungi gestione connessione Analysis Services](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Gestione connessione Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)  
  
 **SourceType**  
 Consente di specificare il tipo di origine delle istruzioni DDL. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|Valore|Description|  
|-----------|-----------------|  
|**Direct Input**|Consente di impostare l'origine sull'istruzione DDL archiviata nella casella di testo **SourceDirect** . Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche illustrate nella sezione seguente.|  
|**File Connection**|Consente di impostare l'origine su un file contenente l'istruzione DDL. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche illustrate nella sezione seguente.|  
|**Variabile**|Consente di impostare l'origine su una variabile. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche illustrate nella sezione seguente.|  
  
## <a name="dynamic-options"></a>Opzioni dinamiche  
  
### <a name="sourcetype--direct-input"></a>SourceType = Direct Input  
 **Origine**  
 Digitare le istruzioni DDL o fare clic sul pulsante con i puntini di sospensione **(…)** e quindi digitare le istruzioni nella finestra di dialogo **Istruzioni DDL** .  
  
### <a name="sourcetype--file-connection"></a>SourceType = File Connection  
 **Origine**  
 Selezionare una connessione File nell'elenco oppure fare clic su \< **nuova connessione...** > e utilizzare il **gestione connessione File** la finestra di dialogo per creare una nuova connessione.  
  
 **Argomenti correlati:** [Gestione connessione file](../../integration-services/connection-manager/file-connection-manager.md)  
  
### <a name="sourcetype--variable"></a>SourceType = Variable  
 **Origine**  
 Selezionare una variabile nell'elenco oppure fare clic su \< **nuova variabile...** > e utilizzare il **Aggiungi variabile** la finestra di dialogo per creare una nuova variabile.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività DDL &#40; Esegui di Analysis Services Pagina generale &#41;](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-general-page.md)   
 [Pagina espressioni](../../integration-services/expressions/expressions-page.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)   
 [Analysis Services Scripting Language &#40;ASSL per XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [XML for Analysis &#40; XMLA &#41; Riferimento](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
