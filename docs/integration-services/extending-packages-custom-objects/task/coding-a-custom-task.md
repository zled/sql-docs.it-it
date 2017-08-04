---
title: "La codifica di un'attività personalizzata | Documenti Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- CSharp
helpviewer_keywords:
- Validate method
- custom tasks [Integration Services], validating
- validation [Integration Services], design-time tasks
- SSIS custom tasks, validating
ms.assetid: dc224f4f-b339-4eb6-a008-1b4fe0ea4fd2
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c4fd06d10d2ecd2796d0b12707c5e34168941c7c
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="coding-a-custom-task"></a>Scrittura del codice di un'attività personalizzata
  Dopo avere creato una classe che eredita dalla classe di base <xref:Microsoft.SqlServer.Dts.Runtime.Task> e avere applicato l'attributo <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> alla classe, è necessario eseguire l'override dell'implementazione delle proprietà e dei metodi della classe di base per fornire la funzionalità personalizzata.  
  
## <a name="configuring-the-task"></a>Configurazione dell'attività  
  
### <a name="validating-the-task"></a>Convalida dell'attività  
 Quando si progetta un pacchetto di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], è possibile utilizzare la convalida per verificare le impostazioni per ogni attività, in modo da rilevare impostazioni non corrette o non appropriate non appena vengono specificate, anziché trovare tutti gli errori solo in fase di esecuzione. Scopo della convalida è determinare se l'attività contiene impostazioni o connessioni non valide che ne impediranno la corretta esecuzione. In questo modo è possibile assicurarsi che il pacchetto contenga attività che con buone probabilità verranno eseguite al primo tentativo.  
  
 È possibile implementare la convalida utilizzando il **convalida** metodo nel codice personalizzato. Il motore di runtime convalida un'attività chiamando il **convalida** metodo sull'attività. È responsabilità dello sviluppatore dell'attività definire i criteri che determinano l'esito positivo o negativo della convalida dell'attività e notificare al motore di runtime il risultato di questa valutazione.  
  
#### <a name="task-abstract-base-class"></a>Classe di base astratta Task  
 Il <xref:Microsoft.SqlServer.Dts.Runtime.Task> fornisce la classe base astratta di **convalida** metodo che ogni attività esegue l'override per definire i criteri della convalida. Il [!INCLUDE[ssIS](../../../includes/ssis-md.md)] finestra di progettazione chiama automaticamente il **convalida** metodo più volte durante la progettazione del pacchetto e fornisce indicazioni visive per l'utente quando si verificano avvisi o errori per identificare i problemi con la configurazione dell'attività. Le attività forniscono i risultati della convalida restituendo un valore dall'enumerazione <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> e generando eventi di avviso e di errore. Questi eventi contengono informazioni visualizzate all'utente in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
 Di seguito sono riportati alcuni esempi di convalida:  
  
-   Una gestione connessione convalida il nome di file specifico.  
  
-   Una gestione connessione convalida che l'input è del tipo previsto, ad esempio un file XML.  
  
-   Un'attività che prevede input di database verifica che non è in grado di ricevere dati da una connessione non di database.  
  
-   Un'attività garantisce che nessuna delle proprie proprietà sia in conflitto con altre proprietà impostate per la stessa attività.  
  
-   Un'attività garantisce che tutte le risorse richieste utilizzate dall'attività in fase di esecuzione siano disponibili.  
  
 Le prestazioni sono un aspetto da considerare quando si determinano gli elementi da convalidare. Ad esempio, l'input di un'attività potrebbe essere una connessione su una rete caratterizzata da una larghezza di banda insufficiente o da un traffico elevato. L'elaborazione della convalida può richiedere diversi secondi se si decide di verificare che la risorsa sia disponibile. Un'altra convalida può generare un round trip a un server con un carico elevato, quindi la routine di convalida può essere lenta. Anche se è possibile convalidare molte proprietà e impostazioni, questa operazione non è sempre necessaria.  
  
-   Il codice di **convalida** metodo viene chiamato anche dal <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> prima dell'esecuzione dell'attività e il <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> Annulla l'esecuzione se la convalida non riesce.  
  
#### <a name="user-interface-considerations-during-validation"></a>Considerazioni sull'interfaccia utente durante la convalida  
 Il <xref:Microsoft.SqlServer.Dts.Runtime.Task> include un <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interfaccia come parametro per il **convalida** metodo. L'interfaccia <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> contiene i metodi chiamati dall'attività per generare eventi nel motore di runtime. I metodi <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> vengono chiamati quando si verifica una condizione di avviso o di errore durante la convalida. Entrambi i metodi di avviso richiedono gli stessi parametri, che includono un codice di errore, un componente di origine, una descrizione, un file della Guida e informazioni di contesto della Guida. Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] utilizza queste informazioni per visualizzare indicatori visivi nell'area di progettazione. Gli indicatori visivi forniti dalla finestra di progettazione includono l'icona di un punto esclamativo visualizzata accanto all'attività nell'area di progettazione. Tale icona indica all'utente che l'attività richiede procedure aggiuntive di configurazione prima che l'esecuzione possa continuare.  
  
 L'icona del punto esclamativo visualizza inoltre una descrizione comando contenente un messaggio di errore. Il messaggio di errore viene fornito dall'attività nel parametro di descrizione dell'evento. I messaggi di errore vengono visualizzati anche nella **elenco attività** riquadro di [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], garantendo all'utente una posizione centrale per la visualizzazione di tutti gli errori di convalida.  
  
#### <a name="validation-example"></a>Esempio di convalida  
 Esempio di codice seguente viene illustrata un'attività con un **UserName** proprietà. Questa proprietà è stata specificata come richiesto per l'esito positivo della convalida. Se la proprietà non viene impostata, l'attività genera un errore e restituisce <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> dall'enumerazione <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>. Il **convalida** metodo viene eseguito il wrapping in un blocco try/catch e convalida non riesce se si verifica un'eccezione.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class SampleTask : Task  
{  
  private string userName = "";  
  
  public override DTSExecResult Validate(Connections connections,  
     VariableDispenser variableDispenser, IDTSComponentEvents events,  
     IDTSLogging log)  
  {  
    try  
    {  
      if (this.userName == "")  
      {  
        //   Raise an OnError event.  
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0);  
        //   Fail validation.  
        return DTSExecResult.Failure;  
      }  
      //   Return success.  
      return DTSExecResult.Success;  
    }  
    catch (System.Exception exception)  
    {  
      //   Capture exceptions, post an error, and fail validation.  
      events.FireError(0, "Sampletask", exception.Message, "", 0);  
      return DTSExecResult.Failure;  
    }  
  }  
  public string UserName  
  {  
    get  
    {  
      return this.userName;  
    }  
    set  
    {  
      this.userName = value;  
    }  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Public Class SampleTask  
  Inherits Task  
  
  Private _userName As String = ""  
  
  Public Overrides Function Validate(ByVal connections As Connections, _  
     ByVal variableDispenser As VariableDispenser, _  
     ByVal events As IDTSComponentEvents, _  
     ByVal log As IDTSLogging) As DTSExecResult  
  
    Try  
      If Me._userName = "" Then  
        '   Raise an OnError event.  
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0)  
        '   Fail validation.  
        Return DTSExecResult.Failure  
      End If  
      '   Return success.  
      Return DTSExecResult.Success  
    Catch exception As System.Exception  
      '   Capture exceptions, post an error, and fail validation.  
      events.FireError(0, "Sampletask", exception.Message, "", 0)  
      Return DTSExecResult.Failure  
    End Try  
  
  End Function  
  
  Public Property UserName() As String  
    Get  
      Return Me._userName  
    End Get  
    Set(ByVal Value As String)  
      Me._userName = Value  
    End Set  
  End Property  
  
End Class  
```  
  
### <a name="persisting-the-task"></a>Persistenza dell'attività  
 In genere non è necessario implementare la persistenza personalizzata per un'attività. La persistenza personalizzata è richiesta solo quando le proprietà di un oggetto utilizzano tipi di dati complessi. Per ulteriori informazioni, vedere [lo sviluppo di oggetti personalizzati per Integration Services](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md).  
  
## <a name="executing-the-task"></a>Esecuzione dell'attività  
 In questa sezione viene descritto come utilizzare il **Execute** metodo ereditato e sottoposto a override dalle attività. Vengono inoltre illustrate varie modalità con cui fornire informazioni sui risultati dell'esecuzione dell'attività.  
  
### <a name="execute-method"></a>Metodo Execute  
 Quando l'esecuzione di attività che sono contenute in un pacchetto di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Common Language runtime chiama i relativi **Execute** metodo. Attività implementano la logica di business e le funzionalità in questo metodo e fornire i risultati dell'esecuzione inviando messaggi, restituendo un valore di <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumerazione e l'override della proprietà **ottenere** del **ExecutionValue** proprietà.  
  
 La classe di base <xref:Microsoft.SqlServer.Dts.Runtime.Task> fornisce un'implementazione predefinita del metodo <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>. Le attività personalizzate eseguono l'override di questo metodo per definire le funzionalità di runtime. L'oggetto <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> esegue il wrapping dell'attività, isolandola dal motore di runtime e dagli altri oggetti nel pacchetto. A causa di questo isolamento, l'ordine di esecuzione dell'attività è indipendente dalla relativa posizione nel pacchetto e l'attività viene eseguita solo quando viene chiamata dal runtime. Questa architettura consente di evitare i problemi che possono verificarsi quando le attività modificano il pacchetto durante l'esecuzione. L'attività dispone di accesso agli altri oggetti del pacchetto solo tramite gli oggetti forniti come parametri nel metodo <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>. Questi parametri consentono alle attività di generare eventi, scrivere voci nel log eventi, accedere alla raccolta di variabili e integrare le connessioni a origini dati nelle transazioni, mantenendo allo stesso tempo l'isolamento necessario per garantire la stabilità e l'affidabilità del pacchetto.  
  
 Nella tabella seguente sono riportati i parametri forniti all'attività nel metodo <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
|Parametro|Description|  
|---------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Connections>|Contiene una raccolta di oggetti <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> disponibili per l'attività.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.VariableDispenser>|Contiene le variabili disponibili per l'attività. Le attività utilizzano le variabili tramite VariableDispenser, non direttamente. VariableDispenser blocca e sblocca le variabili e impedisce il verificarsi di deadlock o sovrascritture.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>|Contiene i metodi chiamati dall'attività per generare eventi nel motore di runtime.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSLogging>|Contiene i metodi e le proprietà utilizzati dall'attività per scrivere voci nel registro eventi.|  
|Oggetto|Contiene l'oggetto transazione di cui fa parte il contenitore, se presente. Questo valore viene passato come parametro al metodo <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> di un oggetto <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.|  
  
### <a name="providing-execution-feedback"></a>Feedback dell'esecuzione  
 Attività includono il codice in **try/catch** blocchi per evitare eccezioni vengano generati per il motore di run-time. In questo modo l'esecuzione del pacchetto viene completata senza arresti imprevisti. Tuttavia, il motore di runtime prevede altri meccanismi per la gestione delle condizioni di errore che possono verificarsi durante l'esecuzione di un'attività, tra cui l'invio di messaggi di errore e di avviso, la restituzione di un valore dalla struttura <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>, l'invio di messaggi, la restituzione del valore <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> e la diffusione di informazioni sui risultati dell'esecuzione dell'attività tramite la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A>.  
  
 L'interfaccia <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> contiene i metodi <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>, che possono essere chiamati dall'attività per inviare messaggi di errore e di avviso al motore di runtime. Entrambi i metodi richiedono parametri quali il codice di errore, il componente di origine, il file della Guida e informazioni di contesto della Guida. A seconda della configurazione dell'attività, il runtime risponde a questi messaggi generando eventi e punti di interruzione oppure scrivendo informazioni nel registro eventi.  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> fornisce anche la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A>, che può essere utilizzata per fornire informazioni aggiuntive sui risultati dell'esecuzione. Ad esempio, se un'attività Elimina le righe da una tabella come parte del relativo **Execute** (metodo), potrebbe restituire il numero di righe eliminate come valore della <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> proprietà. Inoltre, <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> fornisce la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A>. Questa proprietà consente all'utente di eseguire il mapping dell'oggetto<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> restituito dall'attività con qualsiasi variabile visibile all'attività. La variabile specificata può quindi essere utilizzata per stabilire vincoli di precedenza tra attività.  
  
### <a name="execution-example"></a>Esempio di esecuzione  
 Esempio di codice seguente viene illustrata un'implementazione del **Execute** (metodo) e viene illustrato un override **ExecutionValue** proprietà. L'attività Elimina il file specificato da di **fileName** proprietà dell'attività. L'attività Invia un avviso se il file non esiste o se il **fileName** proprietà è una stringa vuota. L'attività restituisce un **booleano** valore il <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> proprietà per indicare se il file è stato eliminato.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class SampleTask : Task  
{  
  private string fileName = "";  
  private bool fileDeleted = false;  
  
  public override DTSExecResult Execute(Connections cons,  
     VariableDispenser vars, IDTSComponentEvents events,  
     IDTSLogging log, Object txn)  
  {  
    try  
    {  
      if (this.fileName == "")  
      {  
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0);  
        this.fileDeleted = false;  
      }  
      else  
      {  
        if (System.IO.File.Exists(this.fileName))  
        {  
          System.IO.File.Delete(this.fileName);  
          this.fileDeleted = true;  
        }  
        else  
          this.fileDeleted = false;  
      }  
      return DTSExecResult.Success;  
    }  
    catch (System.Exception exception)  
    {  
      //   Capture the exception and post an error.  
      events.FireError(0, "Sampletask", exception.Message, "", 0);  
      return DTSExecResult.Failure;  
    }  
  }  
  public string FileName  
  {  
    get { return this.fileName; }  
    set { this.fileName = value; }  
  }  
  public override object ExecutionValue  
  {  
    get { return this.fileDeleted; }  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Public Class SampleTask  
  Inherits Task  
  
  Private _fileName As String = ""  
  Private _fileDeleted As Boolean = False  
  
  Public Overrides Function Execute(ByVal cons As Connections, _  
     ByVal vars As VariableDispenser, ByVal events As IDTSComponentEvents, _  
     ByVal log As IDTSLogging, ByVal txn As Object) As DTSExecResult  
  
    Try  
      If Me._fileName = "" Then  
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0)  
        Me._fileDeleted = False  
      Else  
        If System.IO.File.Exists(Me._fileName) Then  
          System.IO.File.Delete(Me._fileName)  
          Me._fileDeleted = True  
        Else  
          Me._fileDeleted = False  
        End If  
      End If  
      Return DTSExecResult.Success  
    Catch exception As System.Exception  
      '   Capture the exception and post an error.  
      events.FireError(0, "Sampletask", exception.Message, "", 0)  
      Return DTSExecResult.Failure  
    End Try  
  
  End Function  
  
  Public Property FileName() As String  
    Get  
      Return Me._fileName  
    End Get  
    Set(ByVal Value As String)  
      Me._fileName = Value  
    End Set  
  End Property  
  
  Public Overrides ReadOnly Property ExecutionValue() As Object  
    Get  
      Return Me._fileDeleted  
    End Get  
  End Property  
  
End Class  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'attività personalizzata](../../../integration-services/extending-packages-custom-objects/task/creating-a-custom-task.md)   
 [La codifica di un'attività personalizzata](../../../integration-services/extending-packages-custom-objects/task/coding-a-custom-task.md)   
 [Sviluppo di un'interfaccia utente per un'attività personalizzata](../../../integration-services/extending-packages-custom-objects/task/developing-a-user-interface-for-a-custom-task.md)  
  
  