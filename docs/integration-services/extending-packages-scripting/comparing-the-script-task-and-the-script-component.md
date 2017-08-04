---
title: "Confronto tra l'attività Script e il componente Script | Documenti Microsoft"
ms.custom: 
ms.date: 03/17/2017
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
- Script task [Integration Services], comparing to Script component
- Script component [Integration Services], comparing to Script task
ms.assetid: 4b73753a-4239-491b-b7a6-abc63ba83d2d
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0413b4b88a1f0326dad1ba261aea647cefd43302
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="comparing-the-script-task-and-the-script-component"></a>Confronto tra l'attività Script e il componente script
  L'attività Script, disponibile nella finestra del flusso di controllo del [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] finestra di progettazione e il componente Script, disponibile nella finestra del flusso di dati, hanno scopi molto diversi in un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pacchetto. L'attività è uno strumento generico del flusso di controllo, mentre il componente funge da origine, trasformazione o destinazione nel flusso di dati. Nonostante gli scopi diversi, tuttavia, l'attività Script e il componente script presentano analogie negli strumenti di creazione di codice che utilizzano e negli oggetti del pacchetto che rendono disponibili per lo sviluppatore. Identificando le analogie e le differenze, sarà possibile utilizzare l'attività e il componente in modo più efficace.  
  
## <a name="similarities-between-the-script-task-and-the-script-component"></a>Analogie tra l'attività Script e il componente script  
 L'attività Script e il componente Script condividono le caratteristiche comuni seguenti.  
  
|Funzionalità|Description|  
|-------------|-----------------|  
|Due modalità della fase di progettazione|Nell'attività e nel componente si inizia specificando proprietà nell'editor e quindi si passa all'ambiente di sviluppo per scrivere codice.|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA)|L'attività e il componente utilizzano entrambi lo stesso IDE di VSTA e supportano codice scritto in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.|  
|Script precompilati|A partire da [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] tutti gli script sono precompilati. Nelle versioni precedenti è possibile specificare se gli script sono precompilati.<br /><br /> Lo script è precompilato in codice binario, permettendo un'esecuzione più veloce, ma a discapito dell'aumento delle dimensioni dei pacchetti.|  
|debug|L'attività e il componente supportano entrambi i punti di interruzione e l'esecuzione di codice istruzione per istruzione durante il debug in un ambiente di progettazione. Per ulteriori informazioni, vedere [la codifica e debug dell'attività Script](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) e [la codifica e debug del componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).|  
  
## <a name="differences-between-the-script-task-and-the-script-component"></a>Differenze tra l'attività Script e il componente script  
 L'attività Script e il componente script presentano le seguenti differenze di rilievo.  
  
|Funzionalità|Attività Script|Componente script|  
|-------------|-----------------|----------------------|  
|Flusso di controllo/flusso di dati|L'attività Script viene configurata nella scheda Flusso di controllo della finestra di progettazione e viene eseguita all'esterno del flusso di dati del pacchetto.|Il componente script viene configurato nella pagina Flusso di dati della finestra di progettazione e rappresenta un'origine, una trasformazione o una destinazione nell'attività Flusso di dati.|  
|Scopo|Un'attività Script è in grado di completare qualsiasi attività generica.|È necessario specificare se si desidera creare un'origine, una trasformazione o una destinazione con il componente script.|  
|Esecuzione|Un'attività Script esegue codice personalizzato in un punto del flusso di lavoro del pacchetto. Se non viene inserita in un contenitore Ciclo o in un gestore eventi, viene eseguita una sola volta.|Anche un componente script viene eseguito una sola volta, ma in genere esegue la propria routine di elaborazione principale una volta per ogni riga di dati del flusso di dati.|  
|Editor|Il **Editor attività Script** ha tre pagine: **generale**, **Script**, e **espressioni**. Solo il **ReadOnlyVariables** e **ReadWriteVariables**, e **ScriptLanguage** proprietà influiscono direttamente sul codice che è possibile scrivere.|Il **Editor trasformazione Script** contiene fino a quattro pagine: **colonne di Input**, **input e output**, **Script**, e **gestioni connessioni**. I metadati e le proprietà che si configurano in ognuna di queste pagine determinano i membri delle classi di base generate automaticamente che è possibile utilizzare nel codice.|  
|Interazione con il pacchetto|Nel codice scritto per un'attività Script, utilizzare il **Dts** proprietà per accedere ad altre funzionalità del pacchetto. Il **Dts** proprietà è un membro del **la classe ScriptMain** classe.|Nel codice del componente script si utilizzano le proprietà delle funzioni di accesso tipizzate per accedere a determinate caratteristiche del pacchetto, ad esempio variabili e gestioni connessioni.<br /><br /> Il **PreExecute** metodo può accedere solo alle variabili di sola lettura. Il **PostExecute** metodo può accedere sia di sola lettura e le variabili di lettura/scrittura.<br /><br /> Per ulteriori informazioni su questi metodi, vedere [la codifica e debug del componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).|  
|Utilizzo di variabili|L'attività Script utilizza il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> proprietà del **Dts** oggetto per accedere a variabili che sono disponibili tramite l'attività <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> e <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> proprietà. Esempio:<br /><br /> [Visual Basic]<br /><br /> `Dim myVar as String` <br /> `myVar = Dts.Variables(“MyStringVariable”).Value.ToString`<br /><br /> [C#]<br /><br /> `string myVar;` <br /> `myVar = Dts.Variables["MyStringVariable"].Value.ToString();`|Il componente script utilizza le proprietà delle funzioni di accesso tipizzate della classe di base generata automaticamente, create dalle proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadOnlyVariables%2A> e <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadWriteVariables%2A> del componente. Esempio:<br /><br /> [Visual Basic]<br /><br /> `Dim myVar as String` <br /> `myVar = Me.Variables.MyStringVariable`<br /><br /> [C#]<br /><br /> `string myVar;` <br /> `myVar = this.Variables.MyStringVariable;`|  
|Utilizzo delle connessioni|L'attività Script utilizza il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> proprietà del **Dts** oggetto per accedere alle gestioni connessioni definite nel pacchetto. Esempio:<br /><br /> [Visual Basic]<br /><br /> `Dim myFlatFileConnection As String` <br /> `myFlatFileConnection = _     DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _     String)`<br /><br /> [C#]<br /><br /> `string myFlatFileConnection;` <br /> `myFlatFileConnection = (Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);`|Il componente script utilizza le proprietà delle funzioni di accesso tipizzate della classe di base generata automaticamente, create dall'elenco di gestioni connessioni immesso dall'utente nella pagina corrispondente dell'editor. Esempio:<br /><br /> [Visual Basic]<br /><br /> `Dim connMgr As IDTSConnectionManager100` <br /> `connMgr = Me.Connections.MyADONETConnection`<br /><br /> [C#]<br /><br /> `IDTSConnectionManager100 connMgr;` <br /> `connMgr = this.Connections.MyADONETConnection;`|  
|Generazione di eventi|L'attività Script utilizza il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> proprietà del **Dts** oggetto per la generazione di eventi. Esempio:<br /><br /> [Visual Basic]<br /><br /> `Dts.Events.FireError(0, "Event Snippet", _     ex.Message & ControlChars.CrLf & ex.StackTrace, _     "", 0)`<br /><br /> [C#]<br /><br /> `Dts.Events.FireError(0, "Event Snippet", ex.Message + "\r" + ex.StackTrace, "", 0);`|Il componente script genera errori, avvisi e messaggi informativi utilizzando i metodi dell'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> restituita dalla proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>. Esempio:<br /><br /> [Visual Basic]<br /><br /> `Dim myMetadata as IDTSComponentMetaData100 myMetaData = Me.ComponentMetaData myMetaData.FireError(...)`|  
|Registrazione|L'attività Script utilizza il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> metodo il **Dts** oggetto per registrare informazioni nei provider di log abilitati. Esempio:<br /><br /> [Visual Basic]<br /><br /> `Dim bt(0) As Byte Dts.Log("Test Log Event", _     0, _     bt)`<br /><br /> [C#]<br /><br /> `byte[] bt = new byte[0];` <br /> `Dts.Log("Test Log Event", 0, bt);`|Il componente script utilizza il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> della classe di base generata automaticamente per registrare informazioni nei provider di log abilitati. Esempio:<br /><br /> [Visual Basic]<br /><br /> `Dim bt(0) As Byte`<br /><br /> `Me.Log("Test Log Event", _`<br /><br /> `0, _`<br /><br /> `bt)`<br /><br /> [C#]<br /><br /> `byte[] bt = new byte[0]; this.Log("Test Log Event", 0, bt);`|  
|Restituzione di risultati|L'attività Script utilizza sia il <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> proprietà e il parametro facoltativo <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> proprietà del **Dts** oggetto notificare al runtime di risultati.|Il componente script viene eseguito come parte dell'attività Flusso di dati e non restituisce risultati utilizzando queste proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione del pacchetto con l'attività Script](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)   
 [Estensione del flusso di dati con il componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)   
  
  
