---
title: La codifica e debug del componente Script | Documenti Microsoft
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
- SSIS Script task, development environment
- Script component [Integration Services], debugging
- Script component [Integration Services], coding
- SSIS Script component, debugging
- Script component [Integration Services], development environment
- debugging [Integration Services], scripts
- SSIS Script component, coding
- VSTA
ms.assetid: c3913c15-66aa-4b61-89b5-68488fa5f0a4
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ff6c9814547a83439717f8a88d3bd52be80c4ca5
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="coding-and-debugging-the-script-component"></a>Codifica e debug del componente script
  In Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] sono disponibili due modalità per il componente script: progettazione metadati e progettazione codice. Quando si apre il **Editor trasformazione Script**, il componente passa alla modalità di progettazione metadati, in cui configurare i metadati e impostare le proprietà del componente. Dopo l'impostazione delle proprietà del componente script e la configurazione di input e output nella modalità di progettazione metadati, è possibile passare alla modalità di progettazione codice per scrivere lo script personalizzato. Per ulteriori informazioni sulle modalità di progettazione metadati e modalità di progettazione codice, vedere [configurazione del componente Script nell'Editor del componente di Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
## <a name="writing-the-script-in-code-design-mode"></a>Scrittura dello script in modalità di progettazione codice  
  
### <a name="script-component-development-environment"></a>Ambiente di sviluppo del componente script  
 Per scrivere lo script, fare clic su **modifica Script** sul **Script** pagina del **Editor trasformazione Script** per aprire la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE. L'IDE di VSTA include tutte le funzionalità standard dell'ambiente [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET, come l'editor di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] con codifica a colori, la tecnologia IntelliSense e il Visualizzatore oggetti.  
  
 Il codice di script viene scritto in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. Per specificare il linguaggio di scripting, impostare il **ScriptLanguage** proprietà il **Editor trasformazione Script**. Per utilizzare un altro linguaggio di programmazione, è possibile sviluppare un assembly personalizzato nel linguaggio desiderato e chiamarne la funzionalità dal codice nel componente script.  
  
 Lo script creato nel componente script viene archiviato nella definizione del pacchetto. Non viene creato un file script separato. Pertanto, l'utilizzo del componente script non ha effetto sulla distribuzione del pacchetto.  
  
> [!NOTE]  
>  Durante la progettazione del pacchetto, il codice di script viene scritto temporaneamente in un file di progetto. Poiché l'archiviazione di informazioni riservate in un file costituisce un potenziale rischio per la sicurezza, è consigliabile non inserire nel codice di script informazioni riservate, ad esempio le password.  
  
 Per impostazione predefinita, **Option Strict** è disabilitato nell'IDE.  
  
### <a name="script-component-project-structure"></a>Struttura di progetto del componente script  
 L'efficacia del componente script consiste nella possibilità di generare codice di infrastruttura in grado di ridurre la quantità di codice da scrivere. Questa funzionalità si basa sul fatto che input e output, con le relative colonne e proprietà, sono fissi e noti in anticipo. Pertanto, qualsiasi modifica successiva apportata ai metadati del componente può invalidare il codice scritto. Questa condizione è causa di errori di compilazione durante l'esecuzione del pacchetto.  
  
#### <a name="project-items-and-classes-in-the-script-component-project"></a>Elementi e classi del progetto del componente script  
 Quando si passa alla modalità progettazione codice, l'IDE di VSTA viene aperto e visualizza il **la classe ScriptMain** elemento del progetto. Il **la classe ScriptMain** elemento di progetto contiene il modificabile **la classe ScriptMain** (classe), punto che viene utilizzata la voce per lo script e che viene scritto il codice. Gli elementi di codice nella classe variano a seconda del linguaggio di programmazione selezionato per l'attività Script.  
  
 Il progetto di script contiene due elementi del progetto aggiuntivi di sola lettura generati automaticamente:  
  
-   Il **ComponentWrapper** elemento di progetto contiene tre classi:  
  
    -   Il **UserComponent** (classe), che eredita da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> e contiene i metodi e proprietà che verrà utilizzato per elaborare i dati e di interagire con il pacchetto. Il **la classe ScriptMain** classe eredita il **UserComponent** classe.  
  
    -   Oggetto **connessioni** classe di raccolta che contiene i riferimenti alle connessioni selezionate nella pagina Gestione connessione dell'Editor trasformazione Script.  
  
    -   A **variabili** classe di raccolta che contiene riferimenti alle variabili immesse nel **ReadOnlyVariable** e **ReadWriteVariables** proprietà il **Script** pagina del **Editor trasformazione Script**.  
  
-   Il **BufferWrapper** elemento di progetto contiene una classe che eredita da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> per ogni input e output configurato nella **input e output** pagina del **Editor trasformazione Script**. Ognuna di queste classi contiene proprietà della funzione di accesso tipizzate corrispondenti alle colonne di input e output configurate e i buffer del flusso di dati contenenti le colonne.  
  
 Per informazioni sull'utilizzo di questi oggetti, metodi e proprietà, vedere [comprendere Script Component Object Model](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md). Per informazioni su come usare i metodi e proprietà di queste classi in un determinato tipo di componente Script, vedere la sezione [ulteriori esempi di componente Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). Negli argomenti di esempio vengono inoltre presentati esempi di codice completi.  
  
 Quando si configura il componente Script come trasformazione, il **la classe ScriptMain** elemento di progetto contiene il seguente codice generato automaticamente. Nel modello del codice sono inoltre disponibili una panoramica del componente di script, nonché informazioni aggiuntive su come recuperare e modificare oggetti SSIS, quali variabili, eventi e connessioni.  
  
```vb  
' Microsoft SQL Server Integration Services Script Component  
' Write scripts using Microsoft Visual Basic 2008.  
' ScriptMain is the entry point class of the script.  
  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
  
<Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute> _  
<CLSCompliant(False)> _  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub PreExecute()  
        MyBase.PreExecute()  
        '  
        ' Add your code here for preprocessing or remove if not needed  
        '  
    End Sub  
  
    Public Overrides Sub PostExecute()  
        MyBase.PostExecute()  
        '  
        ' Add your code here for postprocessing or remove if not needed  
        ' You can set read/write variables here, for example:  
        ' Me.Variables.MyIntVar = 100  
        '  
    End Sub  
  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
        '  
        ' Add your code here  
        '  
    End Sub  
  
End Class  
```  
  
```csharp  
/* Microsoft SQL Server Integration Services user script component  
*  Write scripts using Microsoft Visual C# 2008.  
*  ScriptMain is the entry point class of the script.*/  
  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
[Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute]  
public class ScriptMain : UserComponent  
{  
  
    public override void PreExecute()  
    {  
        base.PreExecute();  
        /*  
          Add your code here for preprocessing or remove if not needed  
        */  
    }  
  
    public override void PostExecute()  
    {  
        base.PostExecute();  
        /*  
          Add your code here for postprocessing or remove if not needed  
          You can set read/write variables here, for example:  
          Variables.MyIntVar = 100  
        */  
    }  
  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
        /*  
          Add your code here  
        */  
    }  
  
}  
```  
  
#### <a name="additional-project-items-in-the-script-component-project"></a>Altri elementi del progetto del componente script  
 Il progetto di componente Script può includere elementi diverso da quello predefinito **la classe ScriptMain** elemento. È possibile aggiungere al progetto classi, moduli, file di codice e cartelle ed è possibile utilizzare le cartelle per organizzare gruppi di elementi.  
  
 Tutti gli elementi aggiunti vengono salvati in modo permanente nel pacchetto.  
  
#### <a name="references-in-the-script-component-project"></a>Riferimenti nel progetto del componente script  
 È possibile aggiungere riferimenti agli assembly gestiti facendo clic con il progetto dell'attività Script in **Esplora progetti**e quindi fare clic su **Aggiungi riferimento**. Per ulteriori informazioni, vedere [riferimento altri assembly nelle soluzioni di Scripting](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md).  
  
> [!NOTE]  
>  È possibile visualizzare i riferimenti al progetto nell'IDE di VSTA in **Visualizzazione classi** o in **Esplora progetti**. Si apre una di queste finestre di **vista** menu. È possibile aggiungere un nuovo riferimento dal **progetto** menu da **Esplora progetti**, o da **Visualizzazione classi**.  
  
## <a name="interacting-with-the-package-in-the-script-component"></a>Interazione con il pacchetto nel componente script  
 Tramite lo script personalizzato scritto nel componente script è possibile accedere e utilizzare variabili e gestioni connessioni del pacchetto contenitore attraverso funzioni di accesso fortemente tipizzate nelle classi di base generate automaticamente. Tuttavia, è necessario configurare sia le variabili sia le gestioni connessioni prima di passare alla modalità di progettazione codice per renderle disponibili allo script. È inoltre possibile generare eventi ed eseguire registrazioni dal codice del componente script.  
  
 Gli elementi del progetto generati automaticamente nel progetto del componente script forniscono i seguenti oggetti, metodi e proprietà per l'interazione con il pacchetto.  
  
|Funzionalità del pacchetto|Metodo di accesso|  
|---------------------|-------------------|  
|Variabili|Utilizzare le proprietà della funzione di accesso denominate e tipizzate il **variabili** classe di raccolte nel **ComponentWrapper** elemento del progetto, esposto tramite la **variabili** proprietà del **la classe ScriptMain** classe.<br /><br /> Il **PreExecute** metodo può accedere solo alle variabili di sola lettura. Il **PostExecute** metodo può accedere sia di sola lettura e le variabili di lettura/scrittura.|  
|Connessioni|Utilizzare le proprietà della funzione di accesso denominate e tipizzate il **connessioni** classe di raccolte nel **ComponentWrapper** elemento del progetto, esposto tramite la **connessioni** proprietà del **la classe ScriptMain** classe.|  
|Eventi|Generare eventi utilizzando il <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> proprietà del **la classe ScriptMain** classe e **incendio\<X >** metodi del <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interfaccia.|  
|Registrazione|Eseguire la registrazione tramite il <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> metodo il **la classe ScriptMain** classe.|  
  
## <a name="debugging-the-script-component"></a>Debug del componente script  
 Per eseguire il debug del codice nel componente di script, impostare almeno un punto di interruzione nel codice, quindi chiudere l'IDE di VSTA per eseguire il pacchetto in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Quando l'esecuzione del pacchetto entra nel componente di script, l'IDE di VSTA viene riaperto e visualizza il codice in modalità di sola lettura. Quando l'esecuzione raggiunge il punto di interruzione, è possibile esaminare i valori delle variabili e scorrere il codice rimanente.  
  
> [!NOTE]  
>  Non è possibile eseguire il debug di un componente di script se l'attività viene eseguita nell'ambito di un pacchetto figlio eseguito da un'attività Esegui pacchetto. In tali circostanze, i punti di interruzione impostati all'interno del componente di script del pacchetto figlio verranno ignorati. È possibile eseguire il debug del pacchetto figlio normalmente eseguendolo separatamente.  
  
> [!NOTE]  
>  Quando si esegue il debug di un pacchetto che contiene più componenti di script, il debugger è in grado di elaborarne solo uno. Il sistema può eseguire il debug di un altro componente di script se il debugger termina l'elaborazione, come nel caso di un contenitore Ciclo ForEach o Ciclo For.  
  
 È anche possibile monitorare l'esecuzione del componente di script utilizzando i metodi seguenti:  
  
-   Interrompere l'esecuzione e visualizzare un messaggio modale tramite il **MessageBox.Show** metodo il **System.Windows.Forms** dello spazio dei nomi. Rimuovere il codice al termine del processo di debug.  
  
-   Generare eventi per messaggi informativi, avvisi ed errori. I metodi FireInformation FireWarning e FireError visualizzano la descrizione dell'evento in Visual Studio **Output** finestra. Tuttavia, il FireProgress (metodo), il metodo Write e metodo Console. WriteLine non visualizzare alcuna informazione nella **Output** finestra. Vengono visualizzati messaggi di evento FireProgress nel **lo stato di avanzamento** scheda [!INCLUDE[ssIS](../../../includes/ssis-md.md)] finestra di progettazione. Per ulteriori informazioni, vedere [generazione di eventi nel componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md).  
  
-   Registrare eventi o messaggi definiti dall'utente nei provider di log abilitati. Per ulteriori informazioni, vedere [registrazione nel componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md).  
  
 Se si desidera soltanto esaminare l'output di un componente Script configurato come origine o trasformazione, senza salvare i dati a una destinazione, è possibile arrestare il flusso di dati con un [trasformazione Conteggio righe](../../../integration-services/data-flow/transformations/row-count-transformation.md) e collegare un visualizzatore dati all'output del componente Script. Per informazioni sui visualizzatori dati, vedere [il debug del flusso di dati](../../../integration-services/troubleshooting/debugging-data-flow.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Per ulteriori informazioni sulla codifica del componente script, vedere gli argomenti seguenti in questa sezione.  
  
 [Informazioni sul modello di oggetto del componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 Viene illustrato come utilizzare gli oggetti, i metodi e le proprietà disponibili nel componente script.  
  
 [Riferimento ad altri assembly nelle soluzioni di Scripting](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)  
 Viene illustrato come fare riferimento agli oggetti della libreria di classi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nel componente script.  
  
 [Simulazione di un Output degli errori per il componente Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 Viene illustrato come simulare un output degli errori per le righe che generano errori durante l'elaborazione tramite il componente script.  
  
## <a name="external-resources"></a>Risorse esterne  
  
-   Post di blog, [VSTA il programma di installazione e configurazione di VSTA per le installazioni di SSIS 2008 e R2](http://go.microsoft.com/fwlink/?LinkId=215661), su blogs.msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione del componente Script nell'Editor del componente di Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
  
  
