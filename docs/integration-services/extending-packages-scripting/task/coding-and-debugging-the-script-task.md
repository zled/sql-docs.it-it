---
title: "La codifica e debug dell'attività Script | Documenti Microsoft"
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
- Script task [Integration Services], debugging
- SSIS Script task, development environment
- SSIS Script task, debugging
- Script task [Integration Services], development environment
- Script task [Integration Services], coding
- debugging [Integration Services], scripts
- VSTA
- SSIS Script task, coding
ms.assetid: 687c262f-fcab-42e8-92ae-e956f3d92d69
caps.latest.revision: 81
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8c706fc1db3e31130a7754b9e4c3d16f9a13eaf4
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="coding-and-debugging-the-script-task"></a>Scrittura di codice e debug dell'attività Script
  Dopo aver configurato lo Script delle attività nella **Editor attività Script**, si scrive codice personalizzato nell'ambiente di sviluppo di attività Script.  
  
## <a name="script-task-development-environment"></a>Ambiente di sviluppo dell'attività Script  
 L'attività Script utilizza [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) come ambiente di sviluppo per lo script stesso.  
  
 Il codice di script viene scritto in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. Per specificare il linguaggio di scripting, impostare il **ScriptLanguage** proprietà il **Editor attività Script**. Se si preferisce utilizzare un altro linguaggio di programmazione, è possibile sviluppare un assembly personalizzato nel linguaggio desiderato e chiamarne la funzionalità dal codice nell'attività Script.  
  
 Lo script creato nell'attività Script viene archiviato nella definizione del pacchetto. Non viene creato un file script separato. Pertanto, l'utilizzo dell'attività Script non ha effetto sulla distribuzione del pacchetto.  
  
> [!NOTE]  
>  Quando si progetta il pacchetto e si esegue il debug dello script, il codice di script viene scritto temporaneamente in un file di progetto. Poiché l'archiviazione di informazioni riservate in un file costituisce un potenziale rischio per la sicurezza, è consigliabile non inserire nel codice di script informazioni di questo tipo, ad esempio le password.  
  
 Per impostazione predefinita, **Option Strict** è disabilitato nell'IDE.  
  
## <a name="script-task-project-structure"></a>Struttura di progetto dell'attività Script  
 Quando si crea o si modifica lo script contenuto in un'attività Script, VSTA apre un nuovo progetto vuoto o riapre il progetto esistente. La creazione di questo progetto VSTA non influisce sulla distribuzione del pacchetto, perché il progetto viene salvato nel file del pacchetto; l'attività Script non crea file aggiuntivi.  
  
### <a name="project-items-and-classes-in-the-script-task-project"></a>Elementi e classi del progetto dell'attività Script  
 Per impostazione predefinita, il progetto dell'attività Script visualizzato nella finestra Esplora progetti VSTA contiene un singolo elemento, **la classe ScriptMain**. Il **la classe ScriptMain** elemento, a sua volta, contiene un'unica classe, denominata anche **la classe ScriptMain**. Gli elementi di codice nella classe variano a seconda del linguaggio di programmazione selezionato per l'attività Script:  
  
-   Quando l'attività Script è configurato per il [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] linguaggio di programmazione il **la classe ScriptMain** classe dispone di una subroutine pubblica, **Main**. Il **ScriptMain.Main** subroutine è il metodo chiamato dal runtime quando si esegue l'attività Script.  
  
     Per impostazione predefinita, l'unico codice nel **Main** subroutine di un nuovo script è la riga `Dts.TaskResult = ScriptResults.Success`. Questa riga indica al runtime che l'operazione dell'attività è riuscita. Il **Dts.TaskResult** verrà discusso proprietà [restituzione di risultati dall'attività Script](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md).  
  
-   Quando l'attività Script è configurato per Visual c#, linguaggio di programmazione il **la classe ScriptMain** classe dispone di un metodo pubblico, **Main**. Il metodo viene chiamato durante l'esecuzione dell'attività Script.  
  
     Per impostazione predefinita, il **Main** metodo include la riga `Dts.TaskResult = (int)ScriptResults.Success`. Questa riga indica al runtime che l'operazione dell'attività è riuscita.  
  
 Il **la classe ScriptMain** elemento può contenere classi diverse di **la classe ScriptMain** classe. Le classi sono disponibili solo per l'attività Script in cui risiedono.  
  
 Per impostazione predefinita, il **la classe ScriptMain** elemento di progetto contiene il seguente codice generato automaticamente. Nel modello del codice sono inoltre disponibili una panoramica dell'attività Script, nonché informazioni aggiuntive su come recuperare e modificare oggetti SSIS, quali variabili, eventi e connessioni.  
  
```vb  
' Microsoft SQL Server Integration Services Script Task  
' Write scripts using Microsoft Visual Basic 2008.  
' The ScriptMain is the entry point class of the script.  
  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime.VSTAProxy  
  
<System.AddIn.AddIn("ScriptMain", Version:="1.0", Publisher:="", Description:="")> _  
Partial Class ScriptMain  
  
Private Sub ScriptMain_Startup(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Startup  
  
End Sub  
  
Private Sub ScriptMain_Shutdown(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Shutdown  
Try  
' Unlock variables from the read-only and read-write variable collection properties  
If (Dts.Variables.Count <> 0) Then  
Dts.Variables.Unlock()  
End If  
Catch ex As Exception  
        End Try  
End Sub  
  
Enum ScriptResults  
Success = DTSExecResult.Success  
Failure = DTSExecResult.Failure  
End Enum  
  
' The execution engine calls this method when the task executes.  
' To access the object model, use the Dts property. Connections, variables, events,  
' and logging features are available as members of the Dts property as shown in the following examples.  
'  
' To reference a variable, call Dts.Variables("MyCaseSensitiveVariableName").Value  
' To post a log entry, call Dts.Log("This is my log text", 999, Nothing)  
' To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, True)  
'  
' To use the connections collection use something like the following:  
' ConnectionManager cm = Dts.Connections.Add("OLEDB")  
' cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;"  
'  
' Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.  
'   
' To open Help, press F1.  
  
Public Sub Main()  
'  
' Add your code here  
'  
Dts.TaskResult = ScriptResults.Success  
End Sub  
  
End Class  
```  
  
```csharp  
/*  
   Microsoft SQL Server Integration Services Script Task  
   Write scripts using Microsoft Visual C# 2008.  
   The ScriptMain is the entry point class of the script.  
*/  
  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime.VSTAProxy;  
using System.Windows.Forms;  
  
namespace ST_1bcfdbad36d94f8ba9f23a10375abe53.csproj  
{  
    [System.AddIn.AddIn("ScriptMain", Version = "1.0", Publisher = "", Description = "")]  
    public partial class ScriptMain  
    {  
        private void ScriptMain_Startup(object sender, EventArgs e)  
        {  
  
        }  
  
        private void ScriptMain_Shutdown(object sender, EventArgs e)  
        {  
            try  
            {  
                // Unlock variables from the read-only and read-write variable collection properties  
                if (Dts.Variables.Count != 0)  
                {  
                    Dts.Variables.Unlock();  
                }  
            }  
            catch  
            {  
            }  
        }  
  
        #region VSTA generated code  
        private void InternalStartup()  
        {  
            this.Startup += new System.EventHandler(ScriptMain_Startup);  
            this.Shutdown += new System.EventHandler(ScriptMain_Shutdown);  
        }  
        enum ScriptResults  
        {  
            Success = DTSExecResult.Success,  
            Failure = DTSExecResult.Failure  
        };  
  
        #endregion  
  
        /*  
The execution engine calls this method when the task executes.  
To access the object model, use the Dts property. Connections, variables, events,  
and logging features are available as members of the Dts property as shown in the following examples.  
  
To reference a variable, call Dts.Variables["MyCaseSensitiveVariableName"].Value;  
To post a log entry, call Dts.Log("This is my log text", 999, null);  
To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, true);  
  
To use the connections collection use something like the following:  
ConnectionManager cm = Dts.Connections.Add("OLEDB");  
cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;";  
  
Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.  
  
To open Help, press F1.  
*/  
  
        public void Main()  
        {  
            // TODO: Add your code here  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
    }  
```  
  
### <a name="additional-project-items-in-the-script-task-project"></a>Altri elementi di progetto dell'attività Script  
 Il progetto dell'attività Script può includere elementi diverso da quello predefinito **la classe ScriptMain** elemento. È possibile aggiungere classi, moduli e file di codice al progetto. È anche possibile utilizzare cartelle per organizzare gruppi di elementi. Tutti gli elementi aggiunti vengono salvati in modo permanente nel pacchetto.  
  
### <a name="references-in-the-script-task-project"></a>Riferimenti nel progetto dell'attività Script  
 È possibile aggiungere riferimenti agli assembly gestiti facendo clic con il progetto dell'attività Script in **Esplora progetti**e quindi fare clic su **Aggiungi riferimento**. Per ulteriori informazioni, vedere [riferimento altri assembly nelle soluzioni di Scripting](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md).  
  
> [!NOTE]  
>  È possibile visualizzare i riferimenti al progetto nell'IDE di VSTA in **Visualizzazione classi** o in **Esplora progetti**. Si apre una di queste finestre di **vista** menu. È possibile aggiungere un nuovo riferimento dal **progetto** menu da **Esplora progetti**, o da **Visualizzazione classi**.  
  
## <a name="interacting-with-the-package-in-the-script-task"></a>Interazione con il pacchetto nell'attività Script  
 L'attività Script utilizza globale **Dts** oggetto, ovvero un'istanza del <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> , classe e i relativi membri per interagire con il pacchetto contenitore e con il [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.  
  
 Nella tabella seguente sono elencati i principali membri pubblici del <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> (classe), che viene esposta al codice dell'attività Script tramite globale **Dts** oggetto. Negli argomenti di questa sezione verrà descritto in maggior dettaglio l'utilizzo di questi membri.  
  
|Membro|Scopo|  
|------------|-------------|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>|Fornisce accesso alle gestioni connessioni definite nel pacchetto.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>|Fornisce un'interfaccia degli eventi per consentire all'attività Script di generare errori, avvisi e messaggi informativi.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>|Fornisce un modo semplice per restituire un oggetto per il runtime (oltre al **TaskResult**) che può essere utilizzato anche per la diramazione del flusso di lavoro.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>|Registra informazioni quali lo stato e i risultati dell'attività nei provider di log abilitati.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>|Indica l'esito positivo o negativo dell'attività.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Transaction%2A>|Fornisce la transazione, se presente, in cui è in esecuzione il contenitore dell'attività.|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>|Fornisce l'accesso alle variabili elencate nel **ReadOnlyVariables** e **ReadWriteVariables** attività proprietà per l'utilizzo all'interno dello script.|  
  
 La classe <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> contiene anche alcuni membri pubblici che probabilmente non verranno utilizzati.  
  
|Membro|Description|  
|------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>|La proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> fornisce un accesso più semplice alle variabili. Anche se è possibile utilizzare <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, è necessario chiamare in modo esplicito i metodi per bloccare e sbloccare le variabili per la lettura e la scrittura. L'attività Script gestisce automaticamente la semantica di blocco quando si utilizza la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.|  
  
## <a name="debugging-the-script-task"></a>Debug dell'attività Script  
 Per eseguire il debug del codice nell'attività Script, impostare almeno un punto di interruzione nel codice, quindi chiudere l'IDE di VSTA per eseguire il pacchetto in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Quando l'esecuzione del pacchetto entra nell'attività Script, l'IDE di VSTA viene riaperto e visualizza il codice in modalità di sola lettura. Quando l'esecuzione raggiunge il punto di interruzione, è possibile esaminare i valori delle variabili e scorrere il codice rimanente.  
  
> [!WARNING]  
>  È possibile eseguire il debug dell'attività Script quando si esegue il pacchetto in modalità a 64 bit.  
  
> [!NOTE]  
>  È necessario eseguire il pacchetto da sottoporre a debug nell'attività Script. Se si esegue solo la singola attività, i punti di interruzione nel codice dell'attività Script vengono ignorati.  
  
> [!NOTE]  
>  Non è possibile eseguire il debug di un'attività Script se l'attività viene eseguita nell'ambito di un pacchetto figlio eseguito da un'attività Esegui pacchetto. In tali circostanze, i punti di interruzione impostati all'interno dell'attività Script del pacchetto figlio verranno ignorati. È possibile eseguire il debug del pacchetto figlio normalmente eseguendolo separatamente.  
  
> [!NOTE]  
>  Quando si esegue il debug di un pacchetto che contiene più attività Script, il debugger è in grado di elaborarne solo una. Il sistema può eseguire il debug di un'altra attività Script se il debugger termina l'elaborazione, come nel caso di un contenitore Ciclo ForEach o Ciclo For.  
  
## <a name="external-resources"></a>Risorse esterne  
  
-   Post di blog, [VSTA il programma di installazione e configurazione di VSTA per le installazioni di SSIS 2008 e R2](http://go.microsoft.com/fwlink/?LinkId=215661), su blogs.msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ad altri assembly nelle soluzioni di Scripting](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)   
 [Configurazione dell'attività Script nell'Editor attività Script](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
  
  

