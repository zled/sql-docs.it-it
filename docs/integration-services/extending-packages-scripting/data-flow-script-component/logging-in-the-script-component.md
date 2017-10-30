---
title: Registrazione nel componente Script | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 410a2472399574753d67a44b93437b1698c8b086
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="logging-in-the-script-component"></a>Registrazione del componente script
  La registrazione nei pacchetti di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] consente di salvare informazioni dettagliate su stato di esecuzione, risultati e problemi, tramite la registrazione di eventi predefiniti o di messaggi definiti dall'utente da analizzare in un secondo momento. Il componente Script può utilizzare il <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> metodo il **la classe ScriptMain** classe per registrare dati definiti dall'utente. Se la registrazione è abilitata e il **ScriptComponentLogEntry** evento è selezionato per l'accesso il **dettagli** scheda della finestra il **Configura log SSIS** la finestra di dialogo, una singola chiamata al <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> metodo archivia le informazioni sugli eventi in tutti i provider di log che sono stati configurati per l'attività flusso di dati.  
  
 Di seguito è riportato un semplice esempio di registrazione:  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Anche se è possibile eseguire direttamente la registrazione dal componente script, è consigliabile implementare eventi anziché registrare. Quando si utilizzano gli eventi, oltre ad abilitare la registrazione dei messaggi di eventi, è anche possibile rispondere all'evento con gestori eventi predefiniti o definiti dall'utente.  
  
 Per ulteriori informazioni sulla registrazione, vedere [Integration Services &#40; SSIS &#41; Registrazione](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Registrazione](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  

