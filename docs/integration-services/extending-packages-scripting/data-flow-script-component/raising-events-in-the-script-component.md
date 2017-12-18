---
title: Generazione di eventi nel componente script | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62a4772efb1d5b70277882c460ea20d753a56b86
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="raising-events-in-the-script-component"></a>Generazione di eventi nel componente script
  Gli eventi consentono di segnalare errori, avvisi e altre informazioni, ad esempio l'avanzamento o lo stato delle attività, al pacchetto contenitore. Il pacchetto fornisce gestori eventi per la gestione di notifiche degli eventi. Il componente script può generare eventi chiamando metodi sulla proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> della classe **ScriptMain**. Per altre informazioni sulla gestione degli eventi da parte dei pacchetti di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], vedere [Gestori eventi di Integration Services &#40;SSIS&#41;](../../../integration-services/integration-services-ssis-event-handlers.md).  
  
 Gli eventi possono essere registrati in qualsiasi provider di log abilitato nel pacchetto. I provider di log archiviano informazioni sugli eventi in un archivio dati. Il componente script può anche utilizzare il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> per registrare informazioni in un provider di log senza generare un evento. Per ulteriori informazioni sull'utilizzo del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>, vedere la sezione seguente.  
  
 Per generare un evento, l'attività Script chiama uno dei metodi seguenti dell'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> esposta dalla proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>:  
  
|Evento|Description|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|Genera un evento personalizzato definito dall'utente nel pacchetto.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|Informa il pacchetto di una condizione di errore.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|Fornisce informazioni all'utente.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|Informa il pacchetto dello stato del componente.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|Informa il pacchetto che il componente è in uno stato che garantisce la notifica all'utente, ma non è una condizione di errore.|  
  
 Di seguito è riportato un semplice esempio di generazione di un evento Error:  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
## <a name="see-also"></a>Vedere anche  
 [Gestori eventi di Integration Services &#40;SSIS&#41;](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [Aggiunta di un gestore eventi a un pacchetto](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  
