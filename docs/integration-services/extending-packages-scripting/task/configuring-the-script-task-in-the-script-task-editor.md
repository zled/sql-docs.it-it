---
title: "Configurazione dell'attività Script nell'Editor attività Script | Documenti Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 182a7b8f04c2339a8f3d3b986c978a7998c8a9c3
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a>Configurazione dell'attività Script nell'editor attività Script
  Prima di scrivere codice personalizzato nell'attività Script, configurare le proprietà dell'entità nelle tre pagine del **Editor attività Script**. È possibile configurare proprietà di attività aggiuntive che non sono specifiche dell'attività Script utilizzando la finestra Proprietà.  
  
> [!NOTE]  
>  A differenza delle versioni precedenti in cui era possibile indicare se gli script erano precompilati o meno, a partire da [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] tutti gli script sono precompilati.  
  
## <a name="general-page-of-the-script-task-editor"></a>Pagina Generale dell'editor attività Script  
 Nel **generale** pagina del **Editor attività Script**, assegnare un nome univoco e una descrizione per l'attività Script.  
  
## <a name="script-page-of-the-script-task-editor"></a>Pagina Script dell'editor attività Script  
 Il **Script** pagina della finestra di **Editor attività Script** consente di visualizzare le proprietà personalizzate dell'attività Script.  
  
### <a name="scriptlanguage-property"></a>Proprietà ScriptLanguage  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) supporta il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] linguaggi di programmazione Visual c#. Dopo aver creato uno script nell'attività Script, è possibile modificare un valore di **ScriptLanguage** proprietà.  
  
 Per impostare il linguaggio script predefinito per l'attività Script e i componenti di Script, utilizzare il **ScriptLanguage** proprietà il **generale** pagina del **opzioni** la finestra di dialogo. Per ulteriori informazioni, vedere [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
### <a name="entrypoint-property"></a>Proprietà EntryPoint  
 Il **EntryPoint** proprietà specifica il metodo di **la classe ScriptMain** progetto una classe in VSTA che il [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Common Language runtime chiama come punto di ingresso nel codice dell'attività Script. Il **la classe ScriptMain** classe è la classe predefinita generata dai modelli di script.  
  
 Se si modifica il nome del metodo nel progetto VSTA, è necessario modificare il valore della proprietà **EntryPoint** .  
  
### <a name="readonlyvariables-and-readwritevariables-properties"></a>Proprietà ReadOnlyVariables e ReadWriteVariables  
 È possibile immettere elenchi delimitati da virgole di variabili esistenti come valori di queste proprietà per rendere le variabili disponibili per l'accesso di sola lettura o di lettura/scrittura all'interno del codice dell'attività Script. Le variabili di entrambi i tipi sono accessibili nel codice tramite la <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> proprietà del **Dts** oggetto. Per altre informazioni, vedere [Utilizzo di variabili nell'attività Script](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md).  
  
> [!NOTE]  
>  Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.  
  
 Per selezionare le variabili, fare clic sui puntini di sospensione (**...** ) accanto al campo di proprietà. Per ulteriori informazioni, vedere [selezionare le variabili di pagina](../../../integration-services/control-flow/select-variables-page.md).  
  
### <a name="edit-script-button"></a>Pulsante Modifica script  
 Il **modifica Script** pulsante Avvia l'ambiente di sviluppo di VSTA in cui scrivere lo script personalizzato. Per ulteriori informazioni, vedere [la codifica e debug dell'attività Script](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md).  
  
## <a name="expressions-page-of-the-script-task-editor"></a>Pagina Espressioni dell'editor attività Script  
 Nel **espressioni** pagina del **Editor attività Script**, è possibile utilizzare espressioni per fornire valori per le proprietà dell'attività Script elencati in precedenza e per molte altre proprietà di attività. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [La codifica e debug dell'attività Script](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
  
  

