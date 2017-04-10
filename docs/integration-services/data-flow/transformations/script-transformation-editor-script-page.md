---
title: "Editor trasformazione Script (pagina Script) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.scriptcomponent.script.f1"
helpviewer_keywords: 
  - "Editor trasformazione Script"
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Editor trasformazione Script (pagina Script)
  Usare la scheda **Script** della finestra di dialogo **Editor trasformazione Script** per specificare uno script e le proprietà correlate.  
  
 Per ulteriori informazioni sul componente Script, vedere [Script Component](../../../integration-services/data-flow/transformations/script-component.md) e [Configuring the Script Component in the Script Component Editor](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Per informazioni sulla programmazione del componente Script, vedere [Extending the Data Flow with the Script Component](../../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## Opzioni  
 **Proprietà**  
 Consente di visualizzare e modificare le proprietà della trasformazione Script. Molte delle proprietà visualizzate sono di sola lettura. È possibile modificare le proprietà seguenti:  
  
|Valore|Description|  
|-----------|-----------------|  
|**Description**|Consente di descrivere gli scopi della trasformazione Script.|  
|**LocaleID**|Consente di stabilire le impostazioni locali per specificare informazioni sul paese/regione relative all'ordinamento e alla conversione di data e ora.|  
|**Nome**|Consente di digitare un nome descrittivo per il componente.|  
|**ValidateExternalMetadata**|Consente di specificare se la trasformazione Script convalida i metadati delle colonne in fase di progettazione utilizzando origini dei dati esterne. Il valore **false** consente di ritardare la convalida fino al momento dell'esecuzione.|  
|**ReadOnlyVariables**|Consente di digitare un elenco delimitato da virgole delle variabili per l'accesso di sola lettura da parte della trasformazione Script.<br /><br /> Nota: per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.|  
|**ReadWriteVariables**|Consente di digitare un elenco delimitato da virgole delle variabili per l'accesso di lettura/scrittura da parte della trasformazione Script.<br /><br /> Nota: per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.|  
|**ScriptLanguage**|Selezionare il linguaggio di scripting che deve essere utilizzato dal componente Script.<br /><br /> Per impostare il linguaggio di scripting predefinito per componenti Script e attività Script, usare l'opzione **Linguaggio di scripting** nella pagina **Generale** della finestra di dialogo **Opzioni**.|  
|**UserComponentTypeName**|Specifica la classe <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> e l'assembly **Microsoft.SqlServer.TxScript** che supportano l'infrastruttura [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
 **Modifica script**  
 Usare [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) per creare o modificare uno script.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Seleziona tipo componente script](../../../integration-services/data-flow/transformations/select-script-component-type.md)   
 [Editor trasformazione Script &#40;pagina Colonne di input&#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md)   
 [Editor trasformazione Script &#40;pagina Input e output&#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md)   
 [Editor trasformazione Script &#40;pagina Gestioni connessioni&#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md)   
 [Ulteriori esempi di componente script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  