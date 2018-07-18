---
title: Generazione e definizione di eventi in un componente flusso di dati | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 66a3f97bbc07b94e27f3fc07d23d9c528f386f8c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273337"
---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a>Generazione e definizione di eventi in un componente del flusso di dati
  Gli sviluppatori di componenti possono generare un subset degli eventi definiti nell'interfaccia <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> chiamando i metodi esposti sulla proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. È anche possibile definire eventi personalizzati tramite la raccolta <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> e generarli durante l'esecuzione utilizzando il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>. In questa sezione viene descritto come creare e generare un evento e vengono fornite linee guida su quando è necessario generare eventi in fase di progettazione.  
  
## <a name="raising-events"></a>Generazione di eventi  
 I componenti generano eventi usando i metodi **Fire\<X>** dell'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>. È possibile generare eventi durante la progettazione e l'esecuzione di componenti. In genere, durante la progettazione di componenti, i metodi <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> e <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> vengono chiamati durante la convalida. Questi eventi visualizzano messaggi nel riquadro **Elenco errori** di [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] e forniscono feedback agli utenti di un componente non correttamente configurato.  
  
 I componenti possono inoltre generare eventi in qualsiasi momento durante l'esecuzione. Gli eventi consentono agli sviluppatori di componenti di fornire feedback agli utenti del componente durante la relativa esecuzione. Se viene chiamato il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> durante l'esecuzione, è probabile che il pacchetto non riesca.  
  
## <a name="defining-and-raising-custom-events"></a>Definizione e generazione di eventi personalizzati  
  
### <a name="defining-a-custom-event"></a>Definizione di eventi personalizzati.  
 Gli eventi personalizzati vengono creati chiamando il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> della raccolta <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A>. Questa raccolta viene impostata dall'attività Flusso di dati e viene fornita come proprietà allo sviluppatore di componenti tramite la classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Questa classe contiene eventi personalizzati definiti dall'attività Flusso di dati ed eventi personalizzati definiti dal componente durante il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>.  
  
 Gli eventi personalizzati di un componente non sono persistenti nel codice XML del pacchetto. Pertanto, il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> viene chiamato sia durante la progettazione che durante l'esecuzione per consentire al componente di definire gli eventi che genera.  
  
 Il parametro *allowEventHandlers* del metodo <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> specifica se il componente consente la creazione di oggetti <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> per l'evento. Si noti che <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> sono sincroni. Pertanto, il componente riprende l'esecuzione solo al termine dell'esecuzione di un oggetto <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> connesso all'evento personalizzato. Se il *allowEventHandlers* parametro è `true`, ogni parametro dell'evento viene automaticamente reso disponibile per tutti <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> oggetti tramite le variabili che vengono creati e popolati automaticamente per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.  
  
### <a name="raising-a-custom-event"></a>Generazione di eventi personalizzati  
 I componenti generano eventi personalizzati chiamando il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> e fornendo il nome, il testo e i parametri dell'evento. Se il *allowEventHandlers* parametro è `true`, qualsiasi <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> che vengono creati per l'evento personalizzato vengono eseguiti dal [!INCLUDE[ssIS](../../../includes/ssis-md.md)] motore di run-time.  
  
### <a name="custom-event-sample"></a>Esempio di evento personalizzato  
 Nell'esempio di codice seguente è illustrato un componente che definisce un evento personalizzato durante il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A>, quindi genera l'evento in fase di esecuzione chiamando il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>.  
  
```csharp  
public override void RegisterEvents()  
{  
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};  
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};  
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};  
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref paramterTypes, ref parameterDescriptions);  
}  
public override void ProcessInput(int inputID, PipelineBuffer buffer)  
{  
    while (buffer.NextRow())  
    {  
       // Process buffer rows.  
    }  
  
    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];  
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };  
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);  
}  
```  
  
```vb  
Public  Overrides Sub RegisterEvents()   
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"}   
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)}   
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."}   
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, paramterTypes, parameterDescriptions)   
End Sub   
  
Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
  While buffer.NextRow   
  End While   
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort")   
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now}   
  ComponentMetaData.FireCustomEvent("StartingSort", _  
    "Beginning sort operation.", arguments, _  
    ComponentMetaData.Name, FireSortEventAgain)   
End Sub  
```  
  
![Icona di Integration Services (piccola)](../../media/dts-16.gif "icona di Integration Services (piccola)")**rimangono fino a Date con Integration Services** <br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visita la pagina di Integration Services su MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestori eventi di Integration Services &#40;SSIS&#41;](../../integration-services-ssis-event-handlers.md)   
 [Aggiunta di un gestore eventi a un pacchetto](../../add-an-event-handler-to-a-package.md)  
  
  