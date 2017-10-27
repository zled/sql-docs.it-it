---
title: Creazione di una trasformazione asincrona con il componente Script | Documenti Microsoft
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
- asynchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: 0d814404-21e4-4a68-894c-96fa47ab25ae
caps.latest.revision: 63
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4da61e00337430a3eaef84e40f9f732a572cc45b
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a>Creazione di una trasformazione asincrona con il componente script
  Utilizzare un componente di trasformazione nel flusso di dati di un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per modificare e analizzare i dati quando vengono passati dall'origine alla destinazione. Una trasformazione con output sincroni elabora ogni riga di input non appena viene passata attraverso il componente. Una trasformazione con output asincroni potrebbe invece attendere fino al completamento dell'elaborazione, la trasformazione ha ricevuto tutte le righe di input o la trasformazione può restituire come output determinate righe prima di aver ricevuto tutte le righe di input. In questo argomento viene descritta una trasformazione asincrona. Se l'elaborazione richiede una trasformazione sincrona, vedere [la creazione di una trasformazione sincrona con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md). Per ulteriori informazioni sulle differenze tra componenti sincroni e asincroni, vedere [comprensione sincrona e asincrona trasformazioni](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md).  
  
 Per una panoramica del componente Script, vedere [estendendo il flusso di dati con il componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Il componente script e il codice dell'infrastruttura che genera semplificano il processo di sviluppo di un componente del flusso di dati personalizzato. Tuttavia, per comprendere il funzionamento del componente Script, può risultare utile leggere informazioni sui passaggi che è necessario seguire lo sviluppo di un componente del flusso di dati personalizzati nel [lo sviluppo di un componente flusso di dati personalizzato](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) sezione, e in particolare [lo sviluppo di un componente di trasformazione personalizzato con output sincroni](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).  
  
## <a name="getting-started-with-an-asynchronous-transformation-component"></a>Introduzione ai componenti di trasformazione asincroni  
 Quando si aggiunge un componente di Script alla scheda flusso di dati di [!INCLUDE[ssIS](../../includes/ssis-md.md)] finestra di progettazione, il **Seleziona tipo componente Script** viene visualizzata la finestra di dialogo che richiede di preconfigurare il componente come origine, trasformazione o destinazione. In questa finestra di dialogo selezionare **trasformazione**.  
  
## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a>Configurazione di un componente di trasformazione asincrono in modalità di progettazione metadati  
 Dopo aver selezionato l'opzione per creare un componente di trasformazione, configurare il componente utilizzando il **Editor trasformazione Script**. Per ulteriori informazioni, vedere [configurazione del componente Script nell'Editor del componente di Script](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Per selezionare il linguaggio di scripting che verrà utilizzato il componente Script, impostare il **ScriptLanguage** proprietà il **Script** pagina del **Editor trasformazione Script** finestra di dialogo casella.  
  
> [!NOTE]  
>  Per impostare il linguaggio per il componente di Script predefinito, utilizzare il **linguaggio di Scripting** opzione il **generale** pagina del **opzioni** la finestra di dialogo. Per ulteriori informazioni, vedere [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Un componente di trasformazione del flusso di dati include un input e supporta uno o più output. La configurazione di input e output del componente è uno dei passaggi che è necessario completare in modalità di progettazione metadati, tramite il **Editor trasformazione Script**, prima di scrivere lo script personalizzato.  
  
### <a name="configuring-input-columns"></a>Configurazione delle colonne di input  
 Un componente di trasformazione creato tramite il componente script include un unico input.  
  
 Nel **colonne di Input** pagina il **Editor trasformazione Script**, l'elenco di colonne vengono visualizzate le colonne disponibili dell'output del componente a monte nel flusso di dati. Selezionare le colonne che si desidera trasformare o passare. Contrassegnare le colonne che si desidera trasformare sul posto come di lettura/scrittura.  
  
 Per ulteriori informazioni sul **colonne di Input** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; pagina colonne di Input &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
### <a name="configuring-inputs-outputs-and-output-columns"></a>Configurazione di input, output e colonne di output  
 Un componente di trasformazione supporta uno o più output.  
  
 In genere una trasformazione con output asincroni include due output. Ad esempio, per il conteggio del numero di indirizzi di una specifica città, è possibile passare i dati degli indirizzi a un output, inviando il risultato dell'aggregazione a un altro output. L'output di aggregazione richiede anche una nuova colonna di output.  
  
 Nel **input e output** pagina del **Editor trasformazione Script**, vedrai che è stato creato un singolo output per impostazione predefinita, ma non le colonne di output sono state create. In questa pagina dell'editor è possibile configurare gli elementi seguenti:  
  
-   È possibile creare uno o più output aggiuntivi, ad esempio un output per il risultato di un'aggregazione. Utilizzare il **Aggiungi Output** e **Rimuovi Output** pulsanti per gestire gli output del componente di trasformazione asincrono. Impostare il **SynchronousInputID** proprietà di ogni output su zero per indicare che l'output non è sufficiente passare i dati da un componente a monte o trasformarli sul posto nelle colonne e righe esistenti. Questa impostazione rende gli output asincroni rispetto all'input.  
  
-   È possibile assegnare un nome descrittivo all'input e agli output. Il componente script utilizza questi nomi per generare le proprietà delle funzioni di accesso tipizzate che verranno utilizzate per fare riferimento all'input e agli output nello script.  
  
-   In genere una trasformazione asincrona aggiunge colonne al flusso di dati. Quando il **SynchronousInputID** è di proprietà di un output pari a zero, che indica che l'output non è sufficiente passare i dati da un componente a monte o trasformarli sul posto nelle righe esistenti e le colonne, è necessario aggiungere e configurare colonne di output in modo esplicito nell'output. Tali colonne non devono necessariamente avere gli stessi nomi delle colonne di input a cui sono mappate.  
  
-   È possibile aggiungere più colonne per includere ulteriori informazioni. È necessario scrivere codice personalizzato per inserire dati nelle colonne aggiuntive. Per informazioni sulla riproduzione del comportamento di un output degli errori standard, vedere [simulando un Output degli errori per il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Per ulteriori informazioni sul **input e output** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; input e output pagina &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Aggiunta di variabili  
 Se sono presenti tutte le variabili esistenti i cui valori che si desidera utilizzare nello script, è possibile aggiungerle nei campi delle proprietà ReadOnlyVariables e ReadWriteVariables sul **Script** pagina della finestra di **Editor trasformazione Script** .  
  
 Quando si aggiungono più variabili nei campi delle proprietà, separare i relativi nomi con virgole. È inoltre possibile selezionare più variabili facendo clic sui puntini di sospensione (**...** ) accanto al pulsante il **ReadOnlyVariables** e **ReadWriteVariables** campi delle proprietà e quindi selezionando le variabili nel **Seleziona variabili** la finestra di dialogo.  
  
 Per informazioni generali su come usare le variabili con il componente Script, vedere [utilizzo di variabili nel componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Per ulteriori informazioni sul **Script** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; Pagina di script &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a>Scripting di un componente di trasformazione asincrono in modalità di progettazione codice  
 Dopo aver configurato tutti i metadati per il componente, è possibile scrivere lo script personalizzato. Nel **Editor trasformazione Script**via di **Script** pagina, fare clic su **modifica Script** per aprire la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE in cui è possibile aggiungere lo script personalizzato. Il linguaggio di scripting che si utilizza varia a seconda che sia stato selezionato [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c# come linguaggio di scripting per il **ScriptLanguage** proprietà il **Script** pagina.  
  
 Per informazioni importanti che si applica a tutti i tipi di componenti creati tramite il componente Script, vedere [la codifica e debug del componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Informazioni sul codice generato automaticamente  
 Quando si apre l'IDE di VSTA dopo la creazione e configurazione di un componente di trasformazione, modificabile **la classe ScriptMain** classe viene visualizzata nell'editor di codice con stub per il ProcessInputRow e i metodi CreateNewOutputRows. La classe classe ScriptMain è dove si scriverà il codice personalizzato e ProcessInputRow è il metodo più importante in un componente di trasformazione. Il **CreateNewOutputRows** metodo viene in genere utilizzato in un componente di origine, che è simile a una trasformazione asincrona in quanto entrambi i componenti devono creare le proprie righe di output.  
  
 Se si apre VSTA **Esplora progetti** , è possibile visualizzare che il componente Script ha generato anche sola lettura **BufferWrapper** e **ComponentWrapper** gli elementi del progetto . La classe classe ScriptMain eredita dalla classe UserComponent il **ComponentWrapper** elemento del progetto.  
  
 In fase di esecuzione, il motore del flusso di dati chiama il metodo PrimeOutput **UserComponent** classe, che esegue l'override di <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A> metodo la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe padre. Il metodo PrimeOutput a sua volta chiama il metodo CreateNewOutputRows.  
  
 Successivamente, il motore del flusso di dati richiama il metodo ProcessInput nella classe UserComponent, che esegue l'override di <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> metodo la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe padre. Il metodo ProcessInput, a sua volta, consente di scorrere le righe nel buffer di input e chiama il metodo ProcessInputRow una volta per ogni riga.  
  
### <a name="writing-your-custom-code"></a>Scrittura di codice personalizzato  
 Per completare la creazione di un componente di trasformazione asincrono, è necessario utilizzare il metodo ProcessInputRow sottoposto a override per elaborare i dati in ogni riga del buffer di input. Poiché gli output non sono sincroni rispetto all'input, è necessario scrivere in modo esplicito le righe di dati negli output.  
  
 In una trasformazione asincrona, è possibile utilizzare il metodo AddRow per aggiungere righe all'output in modo appropriato tra all'interno dei metodi ProcessInputRow o ProcessInput. Non è necessario utilizzare il metodo CreateNewOutputRows. Se si scrive una singola riga di risultati, ad esempio quelli di aggregazione, in un determinato output, è possibile creare in anticipo la riga di output utilizzando il metodo CreateNewOutputRows e compilare i relativi valori in un secondo momento dopo l'elaborazione di tutte le righe di input. Tuttavia non è utile creare più righe nel metodo CreateNewOutputRows, perché il componente Script consente di utilizzare solo la riga corrente in un input o output. Il metodo CreateNewOutputRows è più importante in un componente di origine in cui non sono presenti righe di input da elaborare.  
  
 È anche possibile eseguire l'override del metodo ProcessInput stesso, in modo da poter eseguire preliminare o finale un'elaborazione aggiuntiva prima o dopo aver scorrere il buffer di input e chiamare ProcessInputRow per ogni riga. Ad esempio, uno degli esempi di codice in questo argomento esegue l'override di ProcessInput per contare il numero di indirizzi in una specifica città come ProcessInputRow scorre le righe**.** L'esempio scrive il valore di riepilogo per il secondo output dopo l'elaborazione di tutte le righe. Nell'esempio viene completato l'output ProcessInput perché il buffer di output non sono più disponibili quando viene chiamato PostExecute.  
  
 A seconda dei requisiti, è possibile scrivere script nei metodi PreExecute e PostExecute disponibili nella classe la classe ScriptMain per eseguire qualsiasi elaborazione preliminare o finale.  
  
> [!NOTE]  
>  Se si sviluppa un componente del flusso di dati personalizzato da zero, sarebbe importante per l'override del metodo PrimeOutput i riferimenti ai buffer di output in modo che è possibile aggiungere righe di dati per i buffer in un secondo momento. Nel componente Script, questo non è necessario perché si dispone di una classe generata automaticamente che rappresenta ogni buffer di output nel **BufferWrapper** elemento del progetto.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato il codice personalizzato necessario nella classe ScriptMain classe per creare un componente di trasformazione asincrono.  
  
> [!NOTE]  
>  Negli esempi viene utilizzata la **Person. Address** tabella il **AdventureWorks** database di esempio e passate la prima e la quarta colonna, il **intAddressID** e  **nvarchar (30) Città** colonne, tramite il flusso di dati. Gli stessi dati vengono utilizzati negli esempi relativi a origine, trasformazione e destinazione in questa sezione. Per ogni esempio, sono documentati ulteriori prerequisiti e presupposti.  
  
 In questo esempio viene illustrato un componente di trasformazione asincrono con due output. Questa trasformazione passa attraverso il **AddressID** e **Città** colonne da un output, mentre conta il numero di indirizzi di una specifica città (Redmond, Washington, U.S.A.) e quindi l'output di valore risultante a un secondo output.  
  
 Se si desidera eseguire questo codice di esempio, è necessario configurare il pacchetto e il componente come segue:  
  
1.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come trasformazione.  
  
2.  Connettere l'output di un'origine o di un'altra trasformazione al nuovo componente di trasformazione nella finestra di progettazione. Questo output deve fornire i dati di **Person. Address** tabella del **AdventureWorks** database di esempio che contiene almeno il **AddressID** e  **Città** colonne.  
  
3.  Aprire il **Editor trasformazione Script**. Nel **colonne di Input** pagina, selezionare il **AddressID** e **Città** colonne.  
  
4.  Nel **input e output** pagina, aggiungere e configurare il **AddressID** e **Città** le colonne nel primo output. Aggiungere un secondo output, quindi aggiungere una colonna di output per il valore di riepilogo nel secondo output. Impostare la proprietà SynchronousInputID del primo output su 0, perché in questo esempio ogni riga di input viene copiata in modo esplicito nel primo output. La proprietà SynchronousInputID dell'output appena creato è già impostata su 0.  
  
5.  Rinominare l'input, gli output e la nuova colonna di output specificando nomi più descrittivi. L'esempio Usa **MyAddressInput** come il nome dell'input, **MyAddressOutput** e **MySummaryOutput** per gli output e **MyRedmondCount** per la colonna di output nel secondo output.  
  
6.  Nel **Script** pagina, fare clic su **modifica Script** e immettere lo script seguente. Chiudere l'ambiente di sviluppo dello script e **Editor trasformazione Script**.  
  
7.  Creare e configurare un componente di destinazione per il primo output che prevede il **AddressID** e **Città** colonne, ad esempio un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione o il componente di destinazione di esempio illustrate in [creazione di una destinazione con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md),. Connettere quindi il primo output della trasformazione, **MyAddressOutput**, al componente di destinazione. È possibile creare una tabella di destinazione eseguendo il seguente comando [!INCLUDE[tsql](../../includes/tsql-md.md)] comando il **AdventureWorks** database:  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
8.  Creare e configurare un altro componente di destinazione per il secondo output. Connettere quindi il secondo output della trasformazione, **MySummaryOutput**, al componente di destinazione. Poiché il secondo output scrive una singola riga con un singolo valore, è possibile configurare facilmente una destinazione con una gestione connessione file flat che si connette a un nuovo file con una singola colonna. Nell'esempio, questa colonna di destinazione è denominata **MyRedmondCount**.  
  
9. Eseguire l'esempio.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Private myRedmondAddressCount As Integer  
  
    Public Overrides Sub CreateNewOutputRows()  
  
        MySummaryOutputBuffer.AddRow()  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInput(ByVal Buffer As MyAddressInputBuffer)  
  
        While Buffer.NextRow()  
            MyAddressInput_ProcessInputRow(Buffer)  
        End While  
  
        If Buffer.EndOfRowset Then  
            MyAddressOutputBuffer.SetEndOfRowset()  
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount  
            MySummaryOutputBuffer.SetEndOfRowset()  
        End If  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        With MyAddressOutputBuffer  
            .AddRow()  
            .AddressID = Row.AddressID  
            .City = Row.City  
        End With  
  
        If Row.City.ToUpper = "REDMOND" Then  
            myRedmondAddressCount += 1  
        End If  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
{  
    private int myRedmondAddressCount;  
  
    public override void CreateNewOutputRows()  
    {  
  
        MySummaryOutputBuffer.AddRow();  
  
    }  
  
    public override void MyAddressInput_ProcessInput(MyAddressInputBuffer Buffer)  
    {  
  
        while (Buffer.NextRow())  
        {  
            MyAddressInput_ProcessInputRow(Buffer);  
        }  
  
        if (Buffer.EndOfRowset())  
        {  
            MyAddressOutputBuffer.SetEndOfRowset();  
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount;  
            MySummaryOutputBuffer.SetEndOfRowset();  
        }  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        {  
            MyAddressOutputBuffer.AddRow();  
            MyAddressOutputBuffer.AddressID = Row.AddressID;  
            MyAddressOutputBuffer.City = Row.City;  
        }  
  
        if (Row.City.ToUpper() == "REDMOND")  
        {  
            myRedmondAddressCount += 1;  
        }  
  
    }  
  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulle trasformazioni sincrone e asincrone](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md)   
 [Creazione di una trasformazione sincrona con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
 [Sviluppo di un componente di trasformazione personalizzato con output asincroni](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
  
  
