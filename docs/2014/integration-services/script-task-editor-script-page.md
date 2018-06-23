---
title: Editor attività script (pagina Script) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0b5641a837761e113368eea47777c3c3bf82ee20
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171246"
---
# <a name="script-task-editor-script-page"></a>Editor attività Script (pagina Script)
  Utilizzare la pagina **Script** della finestra di dialogo **Editor attività Script** per impostare le proprietà dello script e specificare le variabili accessibili per lo script.  
  
> [!NOTE]  
>  In [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] e versioni successive, tutti gli script sono precompilati. Nelle versioni precedenti, si imposta una proprietà **PrecompileScriptIntoBinaryCode** per specificare che lo script è stato precompilato.  
  
 Per ulteriori informazioni sull'attività Script, vedere [Script Task](control-flow/script-task.md) e [Configuring the Script Task in the Script Task Editor](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md). Per informazioni sulla programmazione dell'attività Script, vedere [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).  
  
## <a name="options"></a>Opzioni  
 **ScriptLanguage**  
 Selezionare il linguaggio di scripting per l'attività, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
 Dopo avere creato uno script per l'attività, non è possibile modificare il valore della proprietà **ScriptLanguage** .  
  
 Per impostare il linguaggio di scripting predefinito per l'attività Script, utilizzare l'opzione **Linguaggio di scripting** nella pagina **Generale** della finestra di dialogo **Opzioni** . Per ulteriori informazioni, vedere [General Page](general-page-of-integration-services-designers-options.md).  
  
 **EntryPoint**  
 Specificare il metodo chiamato dal runtime [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] come punto di ingresso nel codice dell'attività Script. Il metodo specificato deve essere nella classe ScriptMain del progetto [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA). ScriptMain è la classe predefinita generata dai modelli di script.  
  
 Se si modifica il nome del metodo nel progetto VSTA, è necessario modificare il valore della proprietà **EntryPoint** .  
  
 **ReadOnlyVariables**  
 Digitare un elenco delimitato da virgole di variabili di sola lettura disponibili per lo script oppure fare clic sul pulsante con i puntini di sospensione (**…**) e selezionare le variabili nella finestra di dialogo **Seleziona variabili** .  
  
> [!NOTE]  
>  Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.  
  
 **ReadWriteVariables**  
 Digitare un elenco delimitato da virgole di variabili di lettura/scrittura disponibili per lo script oppure fare clic sul pulsante con i puntini di sospensione (**…**) e selezionare le variabili nella finestra di dialogo **Seleziona variabili** .  
  
> [!NOTE]  
>  Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.  
  
 **Modifica script**  
 Apre VSTA IDE, dove è possibile creare o modificare lo script.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Pagina Generale](general-page-of-integration-services-designers-options.md)   
 [Editor attività script &#40;pagina Generale&#41;](../../2014/integration-services/script-task-editor-general-page.md)   
 [Pagina espressioni](expressions/expressions-page.md)   
 [Esempi di attività script](extending-packages-scripting-task-examples/script-task-examples.md)   
 [Servizi di integrazione &#40;SSIS&#41; variabili](integration-services-ssis-variables.md)   
 [Aggiungere, eliminare o modificare l'ambito della variabile definita dall'utente in un pacchetto](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  