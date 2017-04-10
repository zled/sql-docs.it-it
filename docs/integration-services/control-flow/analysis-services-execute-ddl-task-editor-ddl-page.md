---
title: "Editor attivit&#224; Esegui DDL Analysis Services (pagina DDL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asexecuteddltask.ddl.f1"
helpviewer_keywords: 
  - "Editor attività Esegui DDL Analysis Services"
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# Editor attivit&#224; Esegui DDL Analysis Services (pagina DDL)
  La pagina **DDL** della finestra di dialogo **Editor attività Esegui DDL Analysis Services** consente di specificare una connessione a un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per offrire informazioni sull'origine delle istruzioni DDL (Data Definition Language).  
  
 Per altre informazioni su questa attività, vedere [Attività Esegui DDL Analysis Services](../../integration-services/control-flow/analysis-services-execute-ddl-task.md).  
  
## Opzioni statiche  
 **Connessione**  
 Selezionare un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o una gestione connessione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dall'elenco oppure fare clic su \<**Nuova connessione**> e usare la finestra di dialogo **Aggiungi gestione connessione Analysis Services** per creare una nuova connessione.  
  
 **Argomenti correlati:** [Riferimento all'interfaccia utente della finestra di dialogo Aggiungi gestione connessione Analysis Services](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Gestione connessione Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)  
  
 **SourceType**  
 Consente di specificare il tipo di origine delle istruzioni DDL. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|Valore|Description|  
|-----------|-----------------|  
|**Direct Input**|Consente di impostare l'origine sull'istruzione DDL archiviata nella casella di testo **SourceDirect**. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche illustrate nella sezione seguente.|  
|**File Connection**|Consente di impostare l'origine su un file contenente l'istruzione DDL. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche illustrate nella sezione seguente.|  
|**Variabile**|Consente di impostare l'origine su una variabile. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche illustrate nella sezione seguente.|  
  
## Opzioni dinamiche  
  
### SourceType = Direct Input  
 **Origine**  
 Digitare le istruzioni DDL o fare clic sul pulsante con i puntini di sospensione **(…)** e quindi digitare le istruzioni nella finestra di dialogo **Istruzioni DDL**.  
  
### SourceType = File Connection  
 **Origine**  
 Selezionare una connessione file dall'elenco oppure fare clic su \<**Nuova connessione...**> e usare la finestra di dialogo **Gestione connessione file** per creare una nuova connessione.  
  
 **Argomenti correlati:** [Gestione connessione file](../../integration-services/connection-manager/file-connection-manager.md)  
  
### SourceType = Variable  
 **Origine**  
 Selezionare una variabile dall'elenco oppure fare clic su \<**Nuova variabile**> e usare la finestra di dialogo **Aggiungi variabile** per creare una nuova variabile.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Esegui DDL Analysis Services &#40;pagina Generale&#41;](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-general-page.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)   
 [Analysis Services Scripting Language &#40;ASSL per XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Guida di riferimento a XML for Analysis &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  