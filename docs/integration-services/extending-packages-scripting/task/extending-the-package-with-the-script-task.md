---
title: "Estensione del pacchetto con l'attività Script | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b2e0b0a933568f8313cefd2f1d6dbdd02f5d3cbc
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-package-with-the-script-task"></a>Estensione del pacchetto con l'attività Script
  L'attività Script estende le funzionalità in fase di esecuzione di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] pacchetti con codice personalizzato scritto in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual c# che viene compilato ed eseguito in fase di esecuzione del pacchetto. L'attività Script semplifica lo sviluppo di un'attività di runtime personalizzata quando le attività incluse in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] non soddisfano pienamente tutti i requisiti. L'attività Script scrive automaticamente tutto il codice dell'infrastruttura richiesto, consentendo agli sviluppatori di concentrarsi esclusivamente sul codice necessario per l'elaborazione personalizzata.  
  
 Un'attività Script interagisce con il pacchetto contenitore attraverso globale **Dts** di un'istanza di oggetto, la <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> classe esposta nell'ambiente di scripting. È possibile scrivere codice in un'attività Script che modifica i valori archiviati nelle variabili [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]; in seguito, il pacchetto può utilizzare questi valori aggiornati per determinare il percorso del proprio flusso di lavoro. L'attività Script può inoltre utilizzare lo spazio dei nomi [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] e la libreria di classi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], nonché assembly personalizzati, per implementare la funzionalità personalizzata.  
  
 L'attività Script e il codice dell'infrastruttura che genera semplificano in modo significativo il processo di sviluppo di un'attività personalizzata. Tuttavia, per comprendere il funzionamento dell'attività Script, può risultare utile leggere la sezione [lo sviluppo di un'attività personalizzata](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md) per comprendere i passaggi necessari per lo sviluppo di un'attività personalizzata.  
  
 Se si crea un'attività che si prevede di riutilizzare in più pacchetti, è preferibile sviluppare un'attività personalizzata anziché utilizzare l'attività Script. Per ulteriori informazioni, vedere [confronto tra soluzioni di Scripting e oggetti personalizzati](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Negli argomenti seguenti vengono fornite ulteriori informazioni sull'attività Script.  
  
 [Configurazione dell'attività Script nell'Editor attività Script](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
 Viene illustrato come le proprietà configurate nel **Editor attività Script** sulle funzionalità e le prestazioni del codice nell'attività Script.  
  
 [La codifica e debug dell'attività Script](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
 Viene illustrato come utilizzare [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) per sviluppare gli script contenuti nell'attività Script.  
  
 [Utilizzo di variabili nell'attività Script](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Viene descritto come utilizzare le variabili tramite la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 [Connessione a origini dati nell'attività Script](../../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Viene descritto come utilizzare le connessioni tramite la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>.  
  
 [Generazione di eventi nell'attività Script](../../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Viene descritto come generare eventi tramite la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
 [Registrazione nell'attività Script](../../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 Viene descritto come registrare informazioni tramite il metodo <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>.  
  
 [Restituzione di risultati dall'attività Script](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md)  
 Viene descritto come restituire risultati tramite le proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> e <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>.  
  
 [Esempi di attività script](../../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
 Vengono forniti esempi che dimostrano diversi utilizzi possibili di un'attività Script.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività script](../../../integration-services/control-flow/script-task.md)   
 [Confronto tra l'attività Script e il componente Script](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  

