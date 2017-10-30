---
title: "Sviluppo di componenti del flusso di dati con più input | Documenti Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 3c7b50e8-2aa6-4f6a-8db4-e8293bc21027
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2cafe3a18fbe930088347304ed758afe505771d6
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="developing-data-flow-components-with-multiple-inputs"></a>Sviluppo di componenti flusso di dati con più input
  Un componente flusso di dati con più input può usare una quantità di memoria eccessiva se i relativi input generano dati a frequenze irregolari. Quando si sviluppa un componente del flusso di dati personalizzato che supporta due o più input, è possibile gestire la richiesta di memoria utilizzando i seguenti membri nello spazio dei nomi Microsoft.SqlServer.Dts.Pipeline:  
  
-   Proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> della classe <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Impostare il valore di questa proprietà su **true** se si desidera implementare il codice necessario per il componente del flusso di dati personalizzato gestire i dati generati a frequenze irregolari.  
  
-   Metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> della classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. È necessario fornire un'implementazione di questo metodo se si imposta la <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> proprietà **true**. Se non si fornisce un'implementazione, nel motore del flusso di dati viene generata un'eccezione durante la fase di esecuzione.  
  
-   Metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> della classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. È inoltre necessario fornire un'implementazione di questo metodo se si imposta la <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> proprietà **true** e il componente personalizzato supporta più di due input. Se non si fornisce un'implementazione, nel motore del flusso di dati viene generata un'eccezione durante la fase di esecuzione se l'utente collega più di due input.  
  
 Insieme, questi membri consentono di sviluppare una soluzione per richieste elevate di memoria simili alla soluzione sviluppata da Microsoft per le trasformazioni Merge e Merge join.  
  
## <a name="setting-the-supportsbackpressure-property"></a>Impostazione della proprietà SupportsBackPressure  
 Il primo passaggio nell'implementazione migliore gestione della memoria per un componente del flusso di dati personalizzato che supporta più input consiste nell'impostare il valore della <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> proprietà **true** nel <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Quando il valore di <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> è **true**, chiamato dal motore del flusso di dati di <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> (metodo) e, quando sono presenti più di due input, chiama anche il <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> metodo in fase di esecuzione.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente, l'implementazione del <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> imposta il valore di <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> a **true**.  
  
```csharp  
[DtsPipelineComponent(ComponentType = ComponentType.Transform,  
        DisplayName = "Shuffler",  
        Description = "Shuffle the rows from input.",  
        SupportsBackPressure = true,  
        LocalizationType = typeof(Localized),  
        IconResource = "Microsoft.Samples.SqlServer.Dts.MIBPComponent.ico")  
]  
public class Shuffler : Microsoft.SqlServer.Dts.Pipeline.PipelineComponent  
        {  
          ...  
        }  
```  
  
## <a name="implementing-the-isinputready-method"></a>Implementazione del metodo IsInputReady  
 Quando si imposta il valore della <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> proprietà **true** nel <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> dell'oggetto, è inoltre necessario fornire un'implementazione per il <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> metodo il <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> classe.  
  
> [!NOTE]  
>  L'implementazione del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> non deve chiamare le implementazioni nella classe di base. L'implementazione predefinita di questo metodo nella base classe genera semplicemente un **NotImplementedException**.  
  
 Quando si implementa questo metodo, impostare lo stato di un elemento nel valore booleano *canProcess* matrice per ogni input del componente. (Gli input sono identificati dai relativi valori di ID nel *inputIDs* array.) Quando si imposta il valore di un elemento di *canProcess* matrice **true** per un input, il motore del flusso di dati chiama il componente <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> (metodo) e fornisce ulteriori dati per l'input specificato.  
  
 Mentre sono disponibili più dati upstream, il valore di *canProcess* deve essere sempre l'elemento di matrice per almeno un input **true**, o l'elaborazione viene arrestata.  
  
 Il motore del flusso di dati chiama il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> prima di inviare ogni buffer di dati per determinare quali input sono in attesa di ricevere altri dati. Quando il valore restituito indica che un input è bloccato, il motore del flusso di dati memorizza temporaneamente nella cache buffer aggiuntivi di dati per l'input anziché inviarli al componente.  
  
> [!NOTE]  
>  Il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> o <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> non viene chiamato nel codice personalizzato. Il motore del flusso di dati chiama questi metodi e gli altri metodi del **PipelineComponent** classe che si esegue l'override, quando il motore del flusso di dati viene eseguito il componente.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente l'implementazione del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> indica che un input è in attesa di ricevere altri dati quando sussistono le condizioni seguenti:  
  
-   È disponibile una maggiore quantità di dati upstream per l'input (`!inputEOR`).  
  
-   Per il componente non sono attualmente disponibili dati da elaborare per l'input nei buffer già ricevuti dal componente (`inputBuffers[inputIndex].CurrentRow() == null`).  
  
 Se un input è in attesa di ricevere altri dati, il componente del flusso di dati indica questa situazione impostando a **true** il valore dell'elemento nel *canProcess* matrice che corrisponde a quell'input.  
  
 Viceversa, se per il componente sono ancora disponibili dati da elaborare per l'input, viene sospesa l'elaborazione dell'input. L'esempio esegue questa impostazione per **false** il valore dell'elemento nel *canProcess* matrice che corrisponde a quell'input.  
  
```csharp  
public override void IsInputReady(int[] inputIDs, ref bool[] canProcess)  
{  
    for (int i = 0; i < inputIDs.Length; i++)  
    {  
        int inputIndex = ComponentMetaData.InputCollection.GetObjectIndexByID(inputIDs[i]);  
  
        canProcess[i] = (inputBuffers[inputIndex].CurrentRow() == null)  
            && !inputEOR[inputIndex];  
    }  
}  
```  
  
 Nell'esempio precedente viene usata la matrice `inputEOR` booleana per indicare se sono disponibili più dati upstream per ogni input. `EOR` nel nome della matrice rappresenta "la fine del set di righe" e fa riferimento alla proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> dei buffer del flusso di dati. In una parte dell'esempio non inclusa in questo argomento, il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> controlla il valore della proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> per ogni buffer di dati ricevuto. Quando un valore di **true** indica che non è disponibile per un input non sono più dati upstream, nell'esempio viene impostato il valore di `inputEOR` elemento della matrice per l'input per **true**. In questo esempio del <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> metodo imposta il valore dell'elemento corrispondente nel *canProcess* matrice **false** di input quando il valore della `inputEOR` elemento della matrice indica che non è disponibile per l'input non sono più dati upstream.  
  
## <a name="implementing-the-getdependentinputs-method"></a>Implementazione del metodo GetDependentInputs  
 Se il componente flusso di dati personalizzato supporta più di due input, è necessario fornire un'implementazione per il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> della classe <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>.  
  
> [!NOTE]  
>  L'implementazione del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> non deve chiamare le implementazioni nella classe di base. L'implementazione predefinita di questo metodo nella base classe genera semplicemente un **NotImplementedException**.  
  
 Il motore del flusso di dati chiama solo il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> quando l'utente collega più di due input al componente. Quando un componente dispone solo di due input e <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> metodo indica che un input è bloccato (*canProcess* = **false**), il motore del flusso di dati riconosce che l'altro input è in attesa di ricevere altri dati. Se tuttavia sono presenti più di due input e il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> indica che un input è bloccato, il codice aggiuntivo nel metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> identifica quali input sono in attesa di ricevere altri dati.  
  
> [!NOTE]  
>  Il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> o <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> non viene chiamato nel codice personalizzato. Il motore del flusso di dati chiama questi metodi e gli altri metodi del **PipelineComponent** classe che si esegue l'override, quando il motore del flusso di dati viene eseguito il componente.  
  
### <a name="example"></a>Esempio  
 Per un input specifico bloccato, l'implementazione seguente del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> restituisce una raccolta degli input in attesa di ricevere altri dati che quindi bloccano l'input specificato. Il componente identifica gli input di blocco cercando gli input diversi da quello bloccato per i quali non sono attualmente disponibili dati da elaborare nei buffer già ricevuti dal componente (`inputBuffers[i].CurrentRow() == null`). Il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> restituisce quindi la raccolta di input di blocco come una raccolta di ID di input.  
  
```csharp  
public override Collection<int> GetDependentInputs(int blockedInputID)  
{  
    Collection<int> currentDependencies = new Collection<int>();  
    for (int i = 0; i < ComponentMetaData.InputCollection.Count; i++)  
    {  
        if (ComponentMetaData.InputCollection[i].ID != blockedInputID  
            && inputBuffers[i].CurrentRow() == null)  
        {  
            currentDependencies.Add(ComponentMetaData.InputCollection[i].ID);  
        }  
    }  
  
    return currentDependencies;  
}  
```  
  
  

