---
title: Componente del flusso di registrazione e definizione di voci di Log in un tipo di dati | Documenti Microsoft
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
- logs [Integration Services], custom
- custom log entries [Integration Services]
- custom data flow components [Integration Services], logging
- data flow components [Integration Services], logging
ms.assetid: 2190dba9-59b5-480b-b8e9-21d5a54c5917
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a0cbdbb818c7299221172f5ceb9b4ee5c54bddcb
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="logging-and-defining-log-entries-in-a-data-flow-component"></a>Registrazione e definizione di voci di log in un componente del flusso di dati
  I componenti personalizzati del flusso di dati possono inserire messaggi in una voce di log esistente tramite il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.PostLogMessage%2A> dell'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. Possono inoltre presentare informazioni all'utente tramite il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A> o metodi simili dell'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. Tuttavia, questo approccio genera l'overhead della generazione e gestione di eventi aggiuntivi e forza l'utente a esaminare numerosi messaggi informativi dettagliati alla ricerca di quelli che potrebbero interessarlo. È possibile utilizzare una voce di log personalizzata, come descritto di seguito, per fornire informazioni di log personalizzate con etichette distinte agli utenti del componente.  
  
## <a name="registering-and-using-a-custom-log-entry"></a>Registrazione e utilizzo di una voce di log personalizzata  
  
### <a name="registering-a-custom-log-entry"></a>Registrazione di una voce di log personalizzata  
 Per registrare una voce di log personalizzata per il componente, eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterLogEntries%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Nell'esempio seguente viene registrata una voce di log personalizzata e vengono forniti un nome e una descrizione.  
  
```csharp  
using Microsoft.SqlServer.Dts.Runtime;  
...  
private const string MyLogEntryName = "My Custom Component Log Entry";  
private const string MyLogEntryDescription = "Log entry from My Custom Component ";  
...  
    public override void RegisterLogEntries()  
    {  
      this.LogEntryInfos.Add(MyLogEntryName,  
        MyLogEntryDescription,  
        Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT);  
    }  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
...  
Private Const MyLogEntryName As String = "My Custom Component Log Entry"   
Private Const MyLogEntryDescription As String = "Log entry from My Custom Component "  
...  
Public  Overrides Sub RegisterLogEntries()   
  Me.LogEntryInfos.Add(MyLogEntryName, _  
    MyLogEntryDescription, _  
    Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT)   
End Sub  
```  
  
 L'enumerazione <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency> fornisce un hint al runtime sulla frequenza con cui verrà registrato l'evento:  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_OCCASIONAL>: l'evento viene registrato occasionalmente, non durante ogni esecuzione.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>: l'evento viene registrato un numero costante di volte durante ogni esecuzione.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_PROPORTIONAL>: l'evento viene registrato un numero di volte proporzionale alla quantità di lavoro completata.  
  
 Negli esempi precedenti viene utilizzato <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT> perché il componente si aspetta di registrare una voce una volta ogni esecuzione.  
  
 Dopo la registrazione della voce di log personalizzate e aggiungere un'istanza del componente personalizzato all'area della finestra di progettazione del flusso di dati, il **registrazione** la finestra di dialogo nella finestra di progettazione visualizza una nuova voce di log con il nome "My personalizzate Component Log Entry" nell'elenco di voci di log disponibili.  
  
### <a name="logging-to-a-custom-log-entry"></a>Registrazione in una voce di log personalizzata  
 Dopo la registrazione della voce di log personalizzata, il componente può registrare messaggi personalizzati. Nell'esempio seguente viene scritta una voce di log personalizzata durante il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> che contiene il testo di un'istruzione SQL utilizzata dal componente.  
  
```csharp  
public override void PreExecute()  
{  
  DateTime now = DateTime.Now;  
  byte[] additionalData = null;  
  this.ComponentMetaData.PostLogMessage(MyLogEntryName,  
    this.ComponentMetaData.Name,  
    "Command Sent was: " + myCommand.CommandText,  
    now, now, 0, ref additionalData);  
}  
```  
  
```vb  
Public  Overrides Sub PreExecute()   
  Dim now As DateTime = DateTime.Now   
  Dim additionalData As Byte() = Nothing   
  Me.ComponentMetaData.PostLogMessage(MyLogEntryName, _  
    Me.ComponentMetaData.Name, _  
    "Command Sent was: " + myCommand.CommandText, _  
    now, now, 0, additionalData)   
End Sub  
```  
  
 A questo punto quando l'utente esegue il pacchetto, dopo aver selezionato il "My Custom Component Log Entry" nella **registrazione** la finestra di dialogo, il log conterrà una voce chiaramente identificata come "User:: My Custom Component Log Entry". Questa nuova voce di log contiene il testo dell'istruzione SQL, il timestamp ed eventuali altri dati registrati dallo sviluppatore.  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Registrazione](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  