---
title: Creazione di una trasformazione sincrona con il componente Script | Documenti Microsoft
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
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: aa1bee1a-ab06-44d8-9944-4bff03d73016
caps.latest.revision: 64
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3d4a507c31f77449aba7eb884c39bf68c7c78581
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-synchronous-transformation-with-the-script-component"></a>Creazione di una trasformazione sincrona con il componente script
  Utilizzare un componente di trasformazione nel flusso di dati di un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per modificare e analizzare i dati quando vengono passati dall'origine alla destinazione. Una trasformazione con output sincroni elabora ogni riga di input non appena viene passata attraverso il componente. Una trasformazione con output asincroni attende di aver ricevuto tutte le righe di input per completare la relativa elaborazione. In questo argomento viene descritta una trasformazione sincrona. Per informazioni sulle trasformazioni asincrone, vedere [la creazione di una trasformazione asincrona con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md). Per ulteriori informazioni sulla differenza tra componenti sincroni e asincroni, vedere [comprensione sincrona e asincrona trasformazioni](../../integration-services/understanding-synchronous-and-asynchronous-transformations.md).  
  
 Per una panoramica del componente Script, vedere [estendendo il flusso di dati con il componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Il componente script e il codice dell'infrastruttura che genera semplificano in modo significativo il processo di sviluppo di un componente del flusso di dati personalizzato. Tuttavia, per comprendere il funzionamento del componente Script, può risultare utile leggere informazioni sui passaggi che è necessario eseguire durante lo sviluppo di un componente del flusso di dati personalizzato nella sezione [lo sviluppo di un componente flusso di dati personalizzato](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)e in particolare [Lo sviluppo di un componente di trasformazione personalizzato con output sincroni](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).  
  
## <a name="getting-started-with-a-synchronous-transformation-component"></a>Introduzione ai componenti di trasformazione sincroni  
 Quando si aggiunge un componente di Script nel riquadro flusso di dati di [!INCLUDE[ssIS](../../includes/ssis-md.md)] finestra di progettazione, il **Seleziona tipo componente Script** viene visualizzata la finestra di dialogo che viene richiesto di selezionare un tipo di componente di origine, destinazione o trasformazione. In questa finestra di dialogo selezionare **trasformazione**.  
  
## <a name="configuring-a-synchronous-transformation-component-in-metadata-design-mode"></a>Configurazione di un componente di trasformazione sincrono in modalità di progettazione metadati  
 Dopo aver selezionato l'opzione per creare un componente di trasformazione, configurare il componente utilizzando il **Editor trasformazione Script**. Per ulteriori informazioni, vedere [configurazione del componente Script nell'Editor del componente di Script](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Per impostare il linguaggio di scripting per il componente Script, impostare il **ScriptLanguage** proprietà il **Script** pagina del **Editor trasformazione Script**.  
  
> [!NOTE]  
>  Per impostare il linguaggio per il componente di Script predefinito, utilizzare il **linguaggio di Scripting** opzione il **generale** pagina del **opzioni** la finestra di dialogo. Per ulteriori informazioni, vedere [General cmdlets pagina](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Un componente di trasformazione del flusso di dati include un input e supporta uno o più output. Configurazione di input e output per il componente è uno dei passaggi che è necessario completare in modalità di progettazione metadati, tramite il **Editor trasformazione Script**, prima di scrivere lo script personalizzato.  
  
### <a name="configuring-input-columns"></a>Configurazione delle colonne di input  
 Un componente di trasformazione include un unico input.  
  
 Nel **colonne di Input** pagina del **Editor trasformazione Script** l'elenco delle colonne vengono visualizzate le colonne disponibili dell'output del componente a monte nel flusso di dati. Selezionare le colonne che si desidera trasformare o passare. Contrassegnare le colonne che si desidera trasformare sul posto come di lettura/scrittura.  
  
 Per ulteriori informazioni sul **colonne di Input** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; pagina colonne di Input &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
### <a name="configuring-inputs-outputs-and-output-columns"></a>Configurazione di input, output e colonne di output  
 Un componente di trasformazione supporta uno o più output.  
  
 Nel **input e output** pagina del **Editor trasformazione Script**, si può notare che è stato creato un singolo output, ma l'output non contiene colonne. In questa pagina dell'editor può essere necessario o consigliabile configurare gli elementi seguenti.  
  
-   Creare uno o più output aggiuntivi, ad esempio un output degli errori simulati per le righe che contengono valori imprevisti. Utilizzare il **Aggiungi Output** e **Rimuovi Output** pulsanti per gestire gli output del componente di trasformazione sincrono. Tutte le righe di input vengono indirizzate a tutti gli output disponibili, a meno che non si indichi che si intende reindirizzare ogni riga a uno o all'altro output. Indicare che si intende reindirizzare le righe specificando un valore intero diverso da zero per il **ExclusionGroup** proprietà sugli output. Il valore integer specifico immesso in **ExclusionGroup** per identificare gli output non è significativo, ma è necessario utilizzare lo stesso valore in modo coerente per il gruppo di output specificato.  
  
    > [!NOTE]  
    >  È inoltre possibile utilizzare un diverso da zero **ExclusionGroup** valore della proprietà con un singolo output quando non si desidera tutte le righe di output. Tuttavia, in questo caso, è necessario chiamare esplicitamente il **DirectRowTo\<outputbuffer >** metodo per ogni riga che si desidera inviare all'output.  
  
-   Assegnare un nome più descrittivo all'input e agli output. Il componente script utilizza questi nomi per generare le proprietà delle funzioni di accesso tipizzate che verranno utilizzate per fare riferimento all'input e agli output nello script.  
  
-   Lasciare le colonne nello stato in cui si trovano per le trasformazioni sincrone. In genere una trasformazione sincrona non aggiunge colonne al flusso di dati. I dati vengono modificati sul posto nel buffer, che viene quindi passato al componente successivo nel flusso di dati. In questo caso, non è necessario aggiungere e configurare in modo esplicito colonne di output negli output della trasformazione. Gli output vengono visualizzati nell'editor senza colonne definite in modo esplicito.  
  
-   Aggiungere le nuove colonne agli output degli errori simulati per gli errori a livello di riga. Normalmente, più output nello stesso **ExclusionGroup** hanno lo stesso set di colonne di output. Tuttavia, se si crea un output degli errori simulati, è possibile aggiungere più colonne per contenere le informazioni sugli errori. Per informazioni su come motore del flusso di dati elabora le righe di errore, vedere [tramite output degli errori in un componente del flusso di dati](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md). Si noti che nel componente script è necessario scrivere codice personalizzato per inserire le informazioni appropriate sugli errori nelle colonne aggiuntive. Per ulteriori informazioni, vedere [simulando un Output degli errori per il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Per ulteriori informazioni sul **input e output** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; input e output pagina &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Aggiunta di variabili  
 Se si desidera utilizzare variabili esistenti nello script, è possibile aggiungerli nel **ReadOnlyVariables** e **ReadWriteVariables** campi proprietà il **Script** pagina del **Editor trasformazione script**.  
  
 Quando si aggiungono più variabili nei campi delle proprietà, separare i relativi nomi con virgole. È inoltre possibile selezionare più variabili facendo clic sui puntini di sospensione (**...** ) accanto al pulsante il **ReadOnlyVariables** e **ReadWriteVariables** campi delle proprietà e quindi selezionando le variabili nel **Seleziona variabili** la finestra di dialogo.  
  
 Per informazioni generali su come usare le variabili con il componente Script, vedere [utilizzo di variabili nel componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Per ulteriori informazioni sul **Script** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; Pagina di script &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-synchronous-transformation-component-in-code-design-mode"></a>Scripting di un componente di trasformazione sincrono in modalità di progettazione codice  
 Dopo aver configurato i metadati per il componente, è possibile scrivere lo script personalizzato. Nel **Editor trasformazione Script**via di **Script** pagina, fare clic su **modifica Script** per aprire la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE in cui è possibile aggiungere lo script personalizzato. Il linguaggio di scripting che si utilizza varia a seconda che sia stato selezionato [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c# come linguaggio di scripting per il **ScriptLanguage** proprietà il **Script** pagina.  
  
 Per informazioni importanti che si applica a tutti i tipi di componenti creati tramite il componente Script, vedere [la codifica e debug del componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Informazioni sul codice generato automaticamente  
 Quando si apre l'IDE di VSTA dopo la creazione e configurazione di un componente di trasformazione, modificabile **la classe ScriptMain** classe viene visualizzata nell'editor di codice con uno stub per il **ProcessInputRow** metodo. Il **la classe ScriptMain** è di classe in cui si scriverà il codice personalizzato, e **ProcessInputRow** è il metodo più importante in un componente di trasformazione.  
  
 Se si apre il **Esplora progetti** in VSTA, è possibile visualizzare che il componente Script ha generato anche sola lettura **BufferWrapper** e **ComponentWrapper** progetto elementi. Il **la classe ScriptMain** classe eredita dal **UserComponent** classe il **ComponentWrapper** elemento del progetto.  
  
 In fase di esecuzione, il motore del flusso di dati richiama il **ProcessInput** metodo nel **UserComponent** classe, che esegue l'override di <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> metodo del <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe padre. Il **ProcessInput** metodo a sua volta consente di scorrere le righe nel buffer di input e chiama il **ProcessInputRow** metodo una volta per ogni riga.  
  
### <a name="writing-your-custom-code"></a>Scrittura di codice personalizzato  
 Un componente di trasformazione con output sincroni è il più semplice da scrivere tra tutti i componenti del flusso di dati. L'esempio a singolo output illustrato più avanti in questo argomento è costituito, ad esempio, dal codice personalizzato seguente:  
  
```vb  
Row.City = UCase(Row.City)  
```  
  
```csharp  
Row.City = (Row.City).ToUpper();  
  
```  
  
 Per completare la creazione di un componente di trasformazione sincrona, utilizzare sottoposto a override **ProcessInputRow** metodo per trasformare i dati in ogni riga del buffer di input. Il motore flusso di dati passa questo buffer, quando è pieno, al componente successivo nel flusso di dati.  
  
 A seconda dei requisiti, è anche possibile scrivere script **PreExecute** e **PostExecute** metodi, disponibile nel **la classe ScriptMain** (classe), per eseguire elaborazione preliminare o finale.  
  
### <a name="working-with-multiple-outputs"></a>Utilizzo di più output  
 L'indirizzamento delle righe di input a uno dei due o più output possibili non richiede una quantità maggiore di codice personalizzato rispetto allo scenario a singolo output descritto in precedenza. L'esempio a due output illustrato più avanti in questo argomento è costituito, ad esempio, dal codice personalizzato seguente:  
  
```vb  
Row.City = UCase(Row.City)  
If Row.City = "REDMOND" Then  
    Row.DirectRowToMyRedmondAddresses()  
Else  
    Row.DirectRowToMyOtherAddresses()  
End If  
```  
  
```csharp  
Row.City = (Row.City).ToUpper();  
  
if (Row.City=="REDMOND")  
{  
    Row.DirectRowToMyRedmondAddresses();  
}  
else  
{  
    Row.DirectRowToMyOtherAddresses();  
}  
```  
  
 In questo esempio, il componente Script genera il **DirectRowTo\<OutputBufferX >** metodi, in base ai nomi degli output che è stato configurato. È possibile utilizzare codice simile per indirizzare le righe di errore a un output degli errori simulati.  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti illustrano il codice personalizzato che è necessario il **la classe ScriptMain** classe per creare un componente di trasformazione sincrono.  
  
> [!NOTE]  
>  Negli esempi viene utilizzata la **Person. Address** tabella il **AdventureWorks** database di esempio e passate la prima e la quarta colonna, il **intAddressID** e  **nvarchar (30) Città** colonne, tramite il flusso di dati. Gli stessi dati vengono utilizzati negli esempi relativi a origine, trasformazione e destinazione in questa sezione. Per ogni esempio, sono documentati ulteriori prerequisiti e presupposti.  
  
### <a name="single-output-synchronous-transformation-example"></a>Esempio di trasformazione sincrona a singolo output  
 In questo esempio viene illustrato un componente di trasformazione sincrono con un singolo output. Questa trasformazione passa attraverso il **AddressID** colonna e converte il **Città** colonna in caratteri maiuscoli.  
  
 Se si desidera eseguire questo codice di esempio, è necessario configurare il pacchetto e il componente come segue:  
  
1.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come trasformazione.  
  
2.  Connettere l'output di un'origine o di un'altra trasformazione al nuovo componente di trasformazione in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Questo output deve fornire i dati di **Person. Address** tabella del **AdventureWorks** database di esempio che contiene il **AddressID** e **città**  colonne.  
  
3.  Aprire il **Editor trasformazione Script**. Nel **colonne di Input** pagina, selezionare il **AddressID** e **Città** colonne. Contrassegna il **Città** colonna in lettura/scrittura.  
  
4.  Nel **input e output** pagina, rinominare l'input e output con nomi più descrittivi, ad esempio **MyAddressInput** e **MyAddressOutput**. Si noti che il **SynchronousInputID** dell'output corrisponde al **ID** dell'input. Pertanto, non è necessario aggiungere e configurare colonne di output.  
  
5.  Nel **Script** pagina, fare clic su **modifica Script** e immettere lo script seguente. Chiudere l'ambiente di sviluppo dello script e **Editor trasformazione Script**.  
  
6.  Creare e configurare un componente di destinazione che prevede il **AddressID** e **Città** colonne, ad esempio un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione o il componente di destinazione di esempio illustrato in [Creazione di una destinazione con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Connettere quindi l'output della trasformazione al componente di destinazione. È possibile creare una tabella di destinazione eseguendo il seguente comando [!INCLUDE[tsql](../../includes/tsql-md.md)] comando il **AdventureWorks** database:  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
7.  Eseguire l'esempio.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        Row.City = UCase(Row.City)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
{  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        Row.City = (Row.City).ToUpper();  
  
    }  
  
}  
```  
  
### <a name="two-output-synchronous-transformation-example"></a>Esempio di trasformazione sincrona a due output  
 In questo esempio viene illustrato un componente di trasformazione sincrona con due output. Questa trasformazione passa attraverso il **AddressID** colonna e converte il **Città** colonna in caratteri maiuscoli. Se il nome della città è Redmond, indirizza la riga a un unico output e tutte le altre righe a un altro output.  
  
 Se si desidera eseguire questo codice di esempio, è necessario configurare il pacchetto e il componente come segue:  
  
1.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come trasformazione.  
  
2.  Connettere l'output di un'origine o di un'altra trasformazione al nuovo componente di trasformazione in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Questo output deve fornire i dati di **Person. Address** tabella del **AdventureWorks** database di esempio che contiene almeno il **AddressID** e  **Città** colonne.  
  
3.  Aprire il **Editor trasformazione Script**. Nel **colonne di Input** pagina, selezionare il **AddressID** e **Città** colonne. Contrassegna il **Città** colonna in lettura/scrittura.  
  
4.  Nel **input e output** pagina, creare un secondo output. Dopo aver aggiunto il nuovo output, assicurarsi di impostare il relativo **SynchronousInputID** per il **ID** dell'input. Questa proprietà è già impostata sul primo output, creato per impostazione predefinita. Per ogni output, impostare il **ExclusionGroup** proprietà sullo stesso valore diverso da zero per indicare che verrà suddiviso le righe di input tra due output si escludono a vicenda. Non è necessario aggiungere colonne di output agli output.  
  
5.  Rinominare l'input e output con nomi più descrittivi, ad esempio **MyAddressInput**, **MyRedmondAddresses**, e **MyOtherAddresses**.  
  
6.  Nel **Script** pagina, fare clic su **modifica Script** e immettere lo script seguente. Chiudere l'ambiente di sviluppo dello script e **Editor trasformazione Script**.  
  
7.  Creare e configurare due componenti di destinazione che prevede il **AddressID** e **Città** colonne, ad esempio un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione, una destinazione File Flat o il componente di destinazione di esempio illustrate in [creazione di una destinazione con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Connettere quindi ogni output della trasformazione a uno dei componenti di destinazione. È possibile creare tabelle di destinazione eseguendo un [!INCLUDE[tsql](../../includes/tsql-md.md)] comando simile al seguente (con nomi di tabella univoci) di **AdventureWorks** database:  
  
    ```sql
    CREATE TABLE [Person].[Address2](  
        [AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL  
    ```  
  
8.  Eseguire l'esempio.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        Row.City = UCase(Row.City)  
  
        If Row.City = "REDMOND" Then  
            Row.DirectRowToMyRedmondAddresses()  
        Else  
            Row.DirectRowToMyOtherAddresses()  
        End If  
  
    End Sub  
  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
  
public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        Row.City = (Row.City).ToUpper();  
  
        if (Row.City == "REDMOND")  
        {  
            Row.DirectRowToMyRedmondAddresses();  
        }  
        else  
        {  
            Row.DirectRowToMyOtherAddresses();  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulle trasformazioni sincrone e asincrone] (~/integration-services/understanding-synchronous-and-asynchronous-transformations.md   
 [La creazione di una trasformazione asincrona con il componente Script] (~/integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md   
 [Sviluppo di un componente di trasformazione personalizzato con output sincroni] (~/integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md  
  
  



