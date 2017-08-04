---
title: Estensione del flusso di dati con il componente Script | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- data flow task [Integration Services], components
- data flow [Integration Services], extending
- debugging [Integration Services], components
- code design mode [Integration Services]
- metadata [Integration Services]
- scripts [Integration Services], extending data flow
- data flow components [Integration Services], Script component
- components [Integration Services], data flow
- Script component [Integration Services], about Script component
- Script component [Integration Services]
- data flow [Integration Services], components
ms.assetid: 072bc4b8-363a-4131-87c3-240338e2fa5c
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c58a854082fcbd12333be63995e4fcdf2d55aac7
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-data-flow-with-the-script-component"></a>Estensione del flusso di dati con il componente script
  Il componente Script estende le funzionalità del flusso di dati di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] pacchetti con codice personalizzato scritto in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual c# che viene compilato ed eseguito in fase di esecuzione del pacchetto. Il componente script semplifica lo sviluppo di un'origine, di una trasformazione o di una destinazione personalizzata del flusso di dati quando le origini, le trasformazioni e le destinazioni incluse in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] non soddisfano pienamente specifici requisiti. Dopo aver configurato il componente con gli input e gli output previsti, scrive automaticamente tutto il codice dell'infrastruttura richiesto, consentendo agli sviluppatori di concentrarsi esclusivamente sul codice necessario per l'elaborazione personalizzata.  
  
 Un componente Script interagisce con il pacchetto contenitore e il flusso di dati tramite le classi generate automaticamente il **ComponentWrapper** e **BufferWrapper** gli elementi, che sono istanze del progetto del <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> e <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> classi rispettivamente. Queste classi rendono disponibili connessioni, variabili e altri elementi del pacchetto come oggetti tipizzati e gestiscono input e output. Il componente script può inoltre utilizzare lo spazio dei nomi [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] e la libreria di classi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], nonché assembly personalizzati, per implementare la funzionalità personalizzata.  
  
 Il componente script e il codice dell'infrastruttura che genera semplificano in modo significativo il processo di sviluppo di un componente del flusso di dati personalizzato. Tuttavia, per comprendere il funzionamento del componente Script, può risultare utile leggere la sezione [lo sviluppo di un componente flusso di dati personalizzato](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) per comprendere i passaggi necessari per lo sviluppo di un componente del flusso di dati personalizzati.  
  
 Se si crea un'origine, una trasformazione o una destinazione che si prevede di riutilizzare in più pacchetti, è consigliabile sviluppare un componente personalizzato anziché utilizzare il componente script. Per altre informazioni, vedere [Sviluppo di un componente del flusso di dati personalizzato](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Negli argomenti seguenti vengono fornite ulteriori informazioni sul componente script.  
  
 [Configurazione del componente Script nell'Editor del componente di Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
 Le proprietà configurate nel **Editor trasformazione Script** sulle funzionalità e le prestazioni del codice del componente Script.  
  
 [La codifica e debug del componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
 Utilizzare il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] strumenti per l'ambiente di sviluppo Applications (VSTA) per sviluppare gli script inclusi nel componente Script.  
  
 [Informazioni sul modello di oggetto del componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 Un nuovo progetto di componente script contiene tre elementi di progetto con diverse classi, nonché proprietà e metodi generati automaticamente.  
  
 [Utilizzo di variabili nel componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)  
 Il **ComponentWrapper** elemento di progetto contiene le proprietà della funzione di accesso fortemente tipizzate per le variabili del pacchetto.  
  
 [Connessione a origini dati nel componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)  
 Il **ComponentWrapper** elemento di progetto contiene anche le proprietà della funzione di accesso fortemente tipizzate per le connessioni definite nel pacchetto.  
  
 [Generazione di eventi nel componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md)  
 È possibile generare eventi per fornire la notifica di problemi ed errori.  
  
 [Registrazione nel componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md)  
 È possibile registrare informazioni nei provider di log abilitati nel pacchetto.  
  
 [Sviluppo di tipi specifici di componenti di Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 In questi semplici esempi viene illustrato come utilizzare il componente script per sviluppare origini, trasformazioni e destinazioni del flusso di dati.  
  
 [Esempi di componente di Script aggiuntivi](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 In questi semplici esempi vengono illustrati alcuni possibili utilizzi del componente script.  
  
## <a name="see-also"></a>Vedere anche  
 [Componente script](../../../integration-services/data-flow/transformations/script-component.md)   
 [Confronto tra l'attività Script e il componente Script](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
