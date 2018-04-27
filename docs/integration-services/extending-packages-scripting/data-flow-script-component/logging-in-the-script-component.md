---
title: Registrazione nel componente script | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: extending-packages-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86427cda2ef58d2dabd1d03e5b927d304b2058a0
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="logging-in-the-script-component"></a>Registrazione del componente script
  La registrazione nei pacchetti di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] consente di salvare informazioni dettagliate su stato di esecuzione, risultati e problemi, tramite la registrazione di eventi predefiniti o di messaggi definiti dall'utente da analizzare in un secondo momento. Il componente script può usare il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> della classe **ScriptMain** per registrare dati definiti dall'utente. Se la registrazione è abilitata e l'evento **ScriptComponentLogEntry** è selezionato per la registrazione nella scheda **Dettagli** della finestra di dialogo **Configura log SSIS**, una singola chiamata al metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> archivia le informazioni dell'evento in tutti i provider di log configurati per l'attività Flusso di dati.  
  
 Di seguito è riportato un semplice esempio di registrazione:  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  Anche se è possibile eseguire direttamente la registrazione dal componente script, è consigliabile implementare eventi anziché registrare. Quando si utilizzano gli eventi, oltre ad abilitare la registrazione dei messaggi di eventi, è anche possibile rispondere all'evento con gestori eventi predefiniti o definiti dall'utente.  
  
 Per altre informazioni sulla registrazione, vedere [Registrazione di Integration Services &#40;SSIS&#41;](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione di Integration Services &#40;SSIS&#41;](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
