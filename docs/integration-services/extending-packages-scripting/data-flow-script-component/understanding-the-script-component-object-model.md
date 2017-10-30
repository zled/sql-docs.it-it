---
title: Informazioni sul modello di oggetto del componente Script | Documenti Microsoft
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
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 09de00344fe94087b6287b07c4b1ffe933d27b7c
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="understanding-the-script-component-object-model"></a>Informazioni sul modello a oggetti del componente script
  Come descritto in [la codifica e debug del componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md), il progetto di componente Script contiene tre elementi di progetto:  
  
1.  Il **la classe ScriptMain** elemento, che contiene il **la classe ScriptMain** classe in cui scrivere il codice. Il **la classe ScriptMain** classe eredita il **UserComponent** classe.  
  
2.  Il **ComponentWrapper** elemento, che contiene il **UserComponent** un'istanza della classe <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> che contiene i metodi e proprietà che verrà utilizzato per elaborare i dati e di interagire con il pacchetto. Il **ComponentWrapper** elemento contiene inoltre **connessioni** e **variabili** classi di raccolte.  
  
3.  Il **BufferWrapper** item, che contiene le classi che eredita da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> per ogni proprietà di input e output e tipizzate per ogni colonna.  
  
 Quando si scrive codice nel **la classe ScriptMain** elemento, si utilizzerà oggetti, metodi e proprietà trattate in questo argomento. Ogni componente non utilizzerà tutti i metodi elencati, ma se li utilizza la sequenza sarà quella illustrata.  
  
 La classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> non contiene codice di implementazione per i metodi descritti in questo argomento. Pertanto, non è necessario aggiungere una chiamata all'implementazione della classe di base nell'implementazione del metodo, anche se questa operazione non genera errori.  
  
 Per informazioni su come usare i metodi e proprietà di queste classi in un determinato tipo di componente Script, vedere la sezione [ulteriori esempi di componente Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). Negli argomenti di esempio vengono inoltre presentati esempi di codice completi.  
  
## <a name="acquireconnections-method"></a>Metodo AcquireConnections  
 Le origini e le destinazioni devono in genere connettersi a un'origine dati esterna. Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> per recuperare la connessione o le informazioni di connessione dalla gestione connessione appropriata.  
  
 Nell'esempio seguente viene restituito un **SqlConnection** da una gestione connessione ADO.NET.  
  
```vb  
Dim connMgr As IDTSConnectionManager100  
Dim sqlConn As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    connMgr = Me.Connections.MyADONETConnection  
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
End Sub  
```  
  
 Nell'esempio seguente restituisce un percorso completo e nome del file dalla gestione connessione File Flat e quindi apre il file utilizzando un **System.IO**.  
  
```vb  
Private textReader As StreamReader  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    Dim connMgr As IDTSConnectionManager100 = _  
        Me.Connections.MyFlatFileSrcConnectionManager  
    Dim exportedAddressFile As String = _  
        CType(connMgr.AcquireConnection(Nothing), String)  
    textReader = New StreamReader(exportedAddressFile)  
  
End Sub  
```  
  
## <a name="preexecute-method"></a>Metodo PreExecute  
 Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> quando è necessario eseguire un'elaborazione una volta solo prima di avviare l'elaborazione delle righe di dati. In una destinazione, ad esempio, è possibile configurare il comando con parametri che verrà utilizzato dalla destinazione stessa per inserire ogni riga di dati nell'origine dati.  
  
```vb  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
...  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
```  
  
```csharp  
SqlConnection sqlConn;   
SqlCommand sqlCmd;   
SqlParameter sqlParam;   
  
public override void PreExecute()   
{   
  
    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn);   
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int);   
    sqlCmd.Parameters.Add(sqlParam);   
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);   
    sqlCmd.Parameters.Add(sqlParam);   
  
}  
```  
  
## <a name="processing-inputs-and-outputs"></a>Elaborazione di input e output  
  
### <a name="processing-inputs"></a>Elaborazione di input  
 I componenti script configurati come trasformazioni o destinazioni prevedono un unico input.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Contenuto dell'elemento di progetto BufferWrapper  
 Per ogni input che è stato configurato, il **BufferWrapper** elemento di progetto contiene una classe che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> e ha lo stesso nome come input. Ogni classe del buffer di input contiene le proprietà, le funzioni e i metodi seguenti:  
  
-   Proprietà delle funzioni di accesso denominate e tipizzate per ogni colonna di input selezionata. Queste proprietà sono di sola lettura o lettura/scrittura a seconda di **tipo di utilizzo** specificato per la colonna nel **colonne di Input** pagina del **Editor trasformazione Script**.  
  
-   Oggetto  **\<colonna > _IsNull** colonna delle proprietà per ogni selezionato di input. Questa proprietà è di sola lettura o lettura/scrittura a seconda di **tipo di utilizzo** specificato per la colonna.  
  
-   Oggetto **DirectRowTo\<outputbuffer >** metodo per ogni output configurato. Questi metodi vengono utilizzati per filtrare le righe a uno di output diversi nello stesso **ExclusionGroup**.  
  
-   Oggetto **NextRow** funzione per ottenere la riga di input successiva e un **EndOfRowset** funzione per determinare se è stato elaborato l'ultimo buffer di dati. In genere non è necessario queste funzioni quando si utilizzano i metodi implementati nell'elaborazione dell'input di **UserComponent** classe di base. La sezione successiva vengono fornite ulteriori informazioni sul **UserComponent** classe di base.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Contenuto dell'elemento di progetto ComponentWrapper  
 L'elemento di progetto ComponentWrapper contiene una classe denominata **UserComponent** che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. Il **la classe ScriptMain** classe in cui scrivere il codice personalizzato deriva a sua volta da **UserComponent**. Il **UserComponent** classe contiene i metodi seguenti:  
  
-   Un'implementazione dell'override di **ProcessInput** metodo. Si tratta del metodo che i dati chiamato dal motore flusso in fase di esecuzione dopo il **PreExecute** (metodo) e può essere chiamato più volte. **ProcessInput** trasferisce l'elaborazione per il  **\<inputbuffer > _ProcessInput** metodo. Il **ProcessInput** metodo verifica la fine del buffer di input e, se è stata raggiunta la fine del buffer, chiama il sottoponibile a override **FinishOutputs** metodo e privato **MarkOutputsAsFinished** metodo. Il **MarkOutputsAsFinished** chiama quindi **SetEndOfRowset** sull'ultimo buffer di output.  
  
-   Un'implementazione sottoponibile a override del  **\<inputbuffer > _ProcessInput** metodo. Questa implementazione predefinita esegue il ciclo di ogni riga di input e chiama  **\<inputbuffer > _ProcessInputRow**.  
  
-   Un'implementazione sottoponibile a override del  **\<inputbuffer > _ProcessInputRow** metodo. L'implementazione predefinita è vuota. Si tratta del metodo di cui in genere si esegue l'override per scrivere il codice personalizzato di elaborazione dati.  
  
#### <a name="what-your-custom-code-should-do"></a>Funzione del codice personalizzato  
 È possibile utilizzare i metodi seguenti per elaborare l'input nel **la classe ScriptMain** classe:  
  
-   Eseguire l'override  **\<inputbuffer > _ProcessInputRow** per elaborare i dati in ogni riga di input durante il passaggio attraverso.  
  
-   Eseguire l'override  **\<inputbuffer > _ProcessInput** solo se è necessario eseguire operazioni aggiuntive durante lo scorrimento in ciclo tra le righe di input. (Ad esempio, è necessario verificare la presenza di **EndOfRowset** per eseguire altre azioni dopo tutte le righe sono state elaborate.) Chiamare  **\<inputbuffer > _ProcessInputRow** per eseguire l'elaborazione delle righe.  
  
-   Eseguire l'override **FinishOutputs** se è necessario eseguire operazioni sugli output prima che vengano chiusi.  
  
 Il **ProcessInput** metodo assicura che questi metodi vengono chiamati in momenti appropriati.  
  
### <a name="processing-outputs"></a>Elaborazione degli output  
 I componenti script configurati come origini o trasformazioni includono uno o più output.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Contenuto dell'elemento di progetto BufferWrapper  
 Per ogni output configurato, l'elemento di progetto BufferWrapper contiene una classe che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> e ha lo stesso nome dell'output. Ogni classe del buffer di input contiene le proprietà e i metodi seguenti:  
  
-   Proprietà delle funzioni di accesso di sola scrittura, denominate e tipizzate per ogni colonna di output.  
  
-   Sola scrittura  **\<colonna > _IsNull** proprietà per ogni colonna di output selezionato che è possibile utilizzare per impostare il valore della colonna su **null**.  
  
-   Un **AddRow** metodo per aggiungere una nuova riga vuota al buffer di output.  
  
-   Oggetto **SetEndOfRowset** metodo per informare il motore del flusso di dati che non sono previsti più buffer di dati. È inoltre disponibile un **EndOfRowset** funzione per determinare se il buffer corrente è l'ultimo buffer di dati. In genere non è necessario queste funzioni quando si utilizzano i metodi implementati nell'elaborazione dell'input di **UserComponent** classe di base.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Contenuto dell'elemento di progetto ComponentWrapper  
 L'elemento di progetto ComponentWrapper contiene una classe denominata **UserComponent** che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. Il **la classe ScriptMain** classe in cui scrivere il codice personalizzato deriva a sua volta da **UserComponent**. Il **UserComponent** classe contiene i metodi seguenti:  
  
-   Un'implementazione dell'override di **PrimeOutput** metodo. Il motore del flusso di dati chiama questo metodo prima **ProcessInput** in fase di esecuzione e viene chiamato solo una volta. **PrimeOutput** trasferisce l'elaborazione per il **CreateNewOutputRows** metodo. Quindi, se il componente è un'origine (ovvero, il componente non include input), **PrimeOutput** chiama il sottoponibile a override **FinishOutputs** metodo e privato **MarkOutputsAsFinished** metodo. Il **MarkOutputsAsFinished** chiamate al metodo **SetEndOfRowset** sull'ultimo buffer di output.  
  
-   Un'implementazione sottoponibile a override del **CreateNewOutputRows** metodo. L'implementazione predefinita è vuota. Si tratta del metodo di cui in genere si esegue l'override per scrivere il codice personalizzato di elaborazione dati.  
  
#### <a name="what-your-custom-code-should-do"></a>Funzione del codice personalizzato  
 È possibile utilizzare i metodi seguenti per elaborare gli output nel **la classe ScriptMain** classe:  
  
-   Eseguire l'override **CreateNewOutputRows** solo quando è possibile aggiungere e popolare le righe di output prima di elaborare le righe di input. Ad esempio, è possibile utilizzare **CreateNewOutputRows** in un'origine, ma in una trasformazione con output asincroni, è necessario chiamare **AddRow** durante o dopo l'elaborazione di dati di input.  
  
-   Eseguire l'override **FinishOutputs** se è necessario eseguire operazioni sugli output prima che vengano chiusi.  
  
 Il **PrimeOutput** metodo assicura che questi metodi vengono chiamati in momenti appropriati.  
  
## <a name="postexecute-method"></a>Metodo PostExecute  
 Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> quando è necessario eseguire un'elaborazione un'unica volta solo dopo aver elaborato le righe di dati. Ad esempio, un'origine, si consiglia di chiudere il **System.Data.SqlClient.SqlDataReader** utilizzato per caricare i dati nel flusso di dati.  
  
> [!IMPORTANT]  
>  La raccolta di **ReadWriteVariables** è disponibile solo nel **PostExecute** metodo. Pertanto, non è possibile incrementare direttamente il valore di una variabile del pacchetto durante l'elaborazione di ogni riga di dati. Al contrario, incrementare il valore di una variabile locale e impostare il valore della variabile del pacchetto per il valore della variabile locale nel **PostExecute** metodo dopo tutti i dati è stata elaborata.  
  
## <a name="releaseconnections-method"></a>Metodo ReleaseConnections  
 Le origini e le destinazioni devono in genere connettersi a un'origine dati esterna. Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> per chiudere e rilasciare la connessione aperta in precedenza nel metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A>.  
  
```vb  
    Dim connMgr As IDTSConnectionManager100  
...  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
```  
  
```csharp  
IDTSConnectionManager100 connMgr;  
  
public override void ReleaseConnections()  
{  
  
    connMgr.ReleaseConnection(sqlConn);  
  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione del componente Script nell'Editor del componente di Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)   
 [La codifica e debug del componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  

