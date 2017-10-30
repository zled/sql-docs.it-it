---
title: Creazione di una destinazione con il componente Script | Documenti Microsoft
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
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7680aac73590f92eadd615b9d164967e61877664
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-destination-with-the-script-component"></a>Creazione di una destinazione con il componente script
  Utilizzare un componente di destinazione nel flusso di dati di un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per salvare in un'origine dati i dati ricevuti dalle origini e dalle trasformazioni upstream. Normalmente, il componente di destinazione si connette all'origine dati tramite una gestione connessione esistente.  
  
 Per una panoramica del componente Script, vedere [estendendo il flusso di dati con il componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Il componente script e il codice dell'infrastruttura che genera semplificano in modo significativo il processo di sviluppo di un componente del flusso di dati personalizzato. Tuttavia, per comprendere il funzionamento del componente Script, può risultare utile leggere informazioni sui passaggi necessari per lo sviluppo di un componenti del flusso di dati personalizzati nel [lo sviluppo di un componente flusso di dati personalizzato](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) sezione particolare [Lo sviluppo di un componente di destinazione personalizzato](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).  
  
## <a name="getting-started-with-a-destination-component"></a>Introduzione ai componenti di destinazione  
 Quando si aggiunge un componente di Script alla scheda flusso di dati di [!INCLUDE[ssIS](../../includes/ssis-md.md)] finestra di progettazione, il **Seleziona tipo componente Script** viene visualizzata la finestra di dialogo che chiede di selezionare un **origine**, **destinazione** , o **trasformazione** script. In questa finestra di dialogo selezionare **destinazione**.  
  
 Connettere quindi l'output di una trasformazione al componente di destinazione in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. A scopo di test, è possibile connettere direttamente un'origine a una destinazione senza alcuna trasformazione.  
  
## <a name="configuring-a-destination-component-in-metadata-design-mode"></a>Configurazione di un componente di destinazione in modalità di progettazione metadati  
 Dopo aver selezionato l'opzione per creare un componente di destinazione, configurare il componente utilizzando il **Editor trasformazione Script**. Per ulteriori informazioni, vedere [configurazione del componente Script nell'Editor del componente di Script](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Per selezionare il linguaggio di scripting che verrà utilizzata dalla destinazione dello Script, impostare il **ScriptLanguage** proprietà il **Script** pagina del **Editor trasformazione Script** la finestra di dialogo.  
  
> [!NOTE]  
>  Per impostare il linguaggio per il componente di Script predefinito, utilizzare il **linguaggio di Scripting** opzione il **generale** pagina del **opzioni** la finestra di dialogo. Per ulteriori informazioni, vedere [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
 Un componente di destinazione del flusso di dati include un input e nessun output. La configurazione dell'input per il componente è uno dei passaggi che è necessario completare in modalità di progettazione metadati, tramite il **Editor trasformazione Script**, prima di scrivere lo script personalizzato.  
  
### <a name="adding-connection-managers"></a>Aggiunta di gestioni connessioni  
 Normalmente, un componente di destinazione utilizza una gestione connessione esistente per connettersi all'origine dati in cui salva i dati dal flusso di dati. Nel **gestioni connessioni** pagina del **Editor trasformazione Script**, fare clic su **Aggiungi** per aggiungere la gestione connessione appropriata.  
  
 Tuttavia, una gestione connessione è solo un'unità pratica che incapsula e archivia le informazioni necessarie per la connessione a un'origine dati di un determinato tipo. È necessario scrivere codice personalizzato per caricare o salvare i dati e possibilmente per aprire e chiudere la connessione all'origine dati.  
  
 Per informazioni generali sull'utilizzo delle gestioni connessioni con il componente Script, vedere [connessione alle origini dati nel componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
 Per ulteriori informazioni sul **gestioni connessioni** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; Pagina gestioni connessioni &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
### <a name="configuring-inputs-and-input-columns"></a>Configurazione di input e colonne di input  
 Un componente di destinazione include un input e nessun output.  
  
 Nel **colonne di Input** pagina del **Editor trasformazione Script**, l'elenco delle colonne vengono visualizzate le colonne disponibili dell'output del componente a monte nel flusso di dati. Selezionare le colonne da salvare.  
  
 Per ulteriori informazioni sul **colonne di Input** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; pagina colonne di Input &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md).  
  
 Il **input e output** pagina della finestra di **Editor trasformazione Script** Mostra un singolo input, è possibile rinominare. Si farà riferimento all'input in base al relativo nome nello script utilizzando la proprietà della funzione di accesso creata nel codice generato automaticamente.  
  
 Per ulteriori informazioni sul **input e output** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; input e output pagina &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Aggiunta di variabili  
 Se si desidera utilizzare variabili esistenti nello script, è possibile aggiungerli nel **ReadOnlyVariables** e **ReadWriteVariables** campi proprietà il **Script** pagina del **Editor trasformazione script**.  
  
 Quando si aggiungono più variabili nei campi delle proprietà, separare i relativi nomi con virgole. È inoltre possibile selezionare più variabili facendo clic sui puntini di sospensione (**...** ) accanto al pulsante il **ReadOnlyVariables** e **ReadWriteVariables** campi delle proprietà e quindi selezionando le variabili nel **Seleziona variabili** la finestra di dialogo.  
  
 Per informazioni generali su come usare le variabili con il componente Script, vedere [utilizzo di variabili nel componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Per ulteriori informazioni sul **Script** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; Pagina di script &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-destination-component-in-code-design-mode"></a>Generazione di script per un componente di destinazione in modalità di progettazione codice  
 Dopo aver configurato i metadati per il componente, è possibile scrivere lo script personalizzato. Nel **Editor trasformazione Script**via di **Script** pagina, fare clic su **modifica Script** per aprire la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE in cui è possibile aggiungere lo script personalizzato. Il linguaggio di scripting che si utilizza varia a seconda che sia stato selezionato [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c# come linguaggio di scripting per il **ScriptLanguage** proprietà il **Script** pagina.  
  
 Per informazioni importanti che si applica a tutti i tipi di componenti creati tramite il componente Script, vedere [la codifica e debug del componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Informazioni sul codice generato automaticamente  
 Quando si apre l'IDE di VSTA dopo la creazione e configurazione di un componente di destinazione, modificabile **la classe ScriptMain** classe viene visualizzata nell'editor di codice con uno stub per il **ProcessInputRow** metodo. Il **la classe ScriptMain** è di classe in cui si scriverà il codice personalizzato, e **ProcessInputRow** è il metodo più importante in un componente di destinazione.  
  
 Se si apre il **Esplora progetti** in VSTA, è possibile visualizzare che il componente Script ha generato anche sola lettura **BufferWrapper** e **ComponentWrapper** progetto elementi. Il **la classe ScriptMain** classe eredita da **UserComponent** classe il **ComponentWrapper** elemento del progetto.  
  
 In fase di esecuzione, il motore del flusso di dati richiama il **ProcessInput** metodo nel **UserComponent** classe, che esegue l'override di <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> metodo del <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe padre. Il **ProcessInput** metodo a sua volta consente di scorrere le righe nel buffer di input e chiama il **ProcessInputRow** metodo una volta per ogni riga.  
  
### <a name="writing-your-custom-code"></a>Scrittura di codice personalizzato  
 Per completare la creazione di un componente di destinazione personalizzato, si consiglia di scrivere script nei metodi seguenti disponibili nel **la classe ScriptMain** classe.  
  
1.  Eseguire l'override di **AcquireConnections** metodo per la connessione all'origine dati esterna. Estrarre l'oggetto connessione o le informazioni di connessione necessarie dalla gestione connessione.  
  
2.  Eseguire l'override di **PreExecute** per preparare salvare i dati. Ad esempio, è consigliabile creare e configurare un **SqlCommand** e i relativi parametri in questo metodo.  
  
3.  Utilizzare sottoposto a override **ProcessInputRow** metodo per copiare ogni riga di input per l'origine dati esterna. Ad esempio, per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione, è possibile copiare i valori della colonna nei parametri di un **SqlCommand** ed eseguire il comando una volta per ogni riga. Per una destinazione file flat, è possibile scrivere i valori per ogni colonna da un **StreamWriter**, separandoli con il delimitatore di colonna.  
  
4.  Eseguire l'override di **PostExecute** metodo per disconnettersi dall'origine dati esterna, se necessario e per eseguire le altre operazioni di pulitura necessarie.  
  
## <a name="examples"></a>Esempi  
 Negli esempi che seguono viene illustrato il codice che è necessario il **la classe ScriptMain** classe per creare un componente di destinazione.  
  
> [!NOTE]  
>  Negli esempi viene utilizzata la **Person. Address** tabella il **AdventureWorks** database di esempio e passate la prima e la quarta colonna, il  **int*AddressID* * * e **nvarchar (30) Città** colonne, tramite il flusso di dati. Gli stessi dati vengono utilizzati negli esempi relativi a origine, trasformazione e destinazione in questa sezione. Per ogni esempio, sono documentati ulteriori prerequisiti e presupposti.  
  
### <a name="adonet-destination-example"></a>Esempio di destinazione ADO.NET  
 Questo esempio viene illustrato un componente di destinazione che utilizza un oggetto esistente [!INCLUDE[vstecado](../../includes/vstecado-md.md)] gestione connessione per salvare i dati dal flusso di dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.  
  
 Se si desidera eseguire questo codice di esempio, è necessario configurare il pacchetto e il componente come segue:  
  
1.  Creare un [!INCLUDE[vstecado](../../includes/vstecado-md.md)] gestione connessione che utilizza il **SqlClient** provider a cui connettersi il **AdventureWorks** database.  
  
2.  Creare una tabella di destinazione eseguendo il seguente comando [!INCLUDE[tsql](../../includes/tsql-md.md)] comando il **AdventureWorks** database:  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come destinazione.  
  
4.  Connettere l'output di un'origine o di una trasformazione a monte al componente di destinazione in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. È possibile connettere direttamente un'origine a una destinazione senza alcuna trasformazione. Questo output deve fornire i dati di **Person. Address** tabella del **AdventureWorks** database di esempio che contiene almeno il **AddressID** e  **Città** colonne.  
  
5.  Aprire il **Editor trasformazione Script**. Nel **le colonne di Input** pagina, selezionare il **AddressID** e **Città** colonne di input.  
  
6.  Nel **input e output** pagina, rinominare l'input con un nome più descrittivo, ad esempio **MyAddressInput**.  
  
7.  Nel **gestioni connessioni** pagina, aggiungere o creare la [!INCLUDE[vstecado](../../includes/vstecado-md.md)] gestione connessione con un nome, ad esempio **MyADONETConnectionManager**.  
  
8.  Nel **Script** pagina, fare clic su **modifica Script** e immettere lo script seguente. Quindi, chiudere l'ambiente di sviluppo dello script.  
  
9. Chiudi il **Editor trasformazione Script** ed eseguire l'esempio.  
  
```vb  
Imports System.Data.SqlClient  
...  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Dim connMgr As IDTSConnectionManager100  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
  
    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
        connMgr = Me.Connections.MyADONETConnectionManager  
        sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
    End Sub  
  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
        With sqlCmd  
            .Parameters("@addressid").Value = Row.AddressID  
            .Parameters("@city").Value = Row.City  
            .ExecuteNonQuery()  
        End With  
    End Sub  
  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System.Data.SqlClient;  
public class ScriptMain:  
    UserComponent  
  
{  
    IDTSConnectionManager100 connMgr;  
    SqlConnection sqlConn;  
    SqlCommand sqlCmd;  
    SqlParameter sqlParam;  
  
    public override void AcquireConnections(object Transaction)  
    {  
  
        connMgr = this.Connections.MyADONETConnectionManager;  
        sqlConn = (SqlConnection)connMgr.AcquireConnection(null);  
  
    }  
  
    public override void PreExecute()  
    {  
  
        sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " +  
            "VALUES(@addressid, @city)", sqlConn);  
        sqlParam = new SqlParameter("@addressid", SqlDbType.Int);  
        sqlCmd.Parameters.Add(sqlParam);  
        sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);  
        sqlCmd.Parameters.Add(sqlParam);  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
        {  
            sqlCmd.Parameters["@addressid"].Value = Row.AddressID;  
            sqlCmd.Parameters["@city"].Value = Row.City;  
            sqlCmd.ExecuteNonQuery();  
        }  
    }  
  
    public override void ReleaseConnections()  
    {  
  
        connMgr.ReleaseConnection(sqlConn);  
  
    }  
  
}  
```  
  
### <a name="flat-file-destination-example"></a>Esempio di destinazione file flat  
 In questo esempio è illustrato un componente di destinazione che utilizza una gestione connessione file flat esistente per salvare i dati del flusso di dati in un file flat.  
  
 Se si desidera eseguire questo codice di esempio, è necessario configurare il pacchetto e il componente come segue:  
  
1.  Creare una gestione connessione file flat che si connette a un file di destinazione. Il file non deve necessariamente esistere, in quanto verrà creato dal componente di destinazione. Configurare il file di destinazione come file delimitato da virgole che contiene il **AddressID** e **Città** colonne.  
  
2.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come destinazione.  
  
3.  Connettere l'output di un'origine o di una trasformazione a monte al componente di destinazione in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. È possibile connettere direttamente un'origine a una destinazione senza alcuna trasformazione. Questo output deve fornire i dati di **Person. Address** tabella del **AdventureWorks** database di esempio e deve contenere almeno le **AddressID** e **Città** colonne.  
  
4.  Aprire il **Editor trasformazione Script**. Nel **colonne di Input** pagina, selezionare il **AddressID** e **Città** colonne.  
  
5.  Nel **input e output** pagina, rinominare l'input con un nome più descrittivo, ad esempio **MyAddressInput**.  
  
6.  Nel **gestioni connessioni** pagina, aggiungere o creare la connessione File Flat gestione con un nome descrittivo, ad esempio **MyFlatFileDestConnectionManager**.  
  
7.  Nel **Script** pagina, fare clic su **modifica Script** e immettere lo script seguente. Quindi, chiudere l'ambiente di sviluppo dello script.  
  
8.  Chiudi il **Editor trasformazione Script** ed eseguire l'esempio.  
  
```vb  
Imports System.IO  
...  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Dim copiedAddressFile As String  
    Private textWriter As StreamWriter  
    Private columnDelimiter As String = ","  
  
    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
        Dim connMgr As IDTSConnectionManager100 = _  
            Me.Connections.MyFlatFileDestConnectionManager  
        copiedAddressFile = CType(connMgr.AcquireConnection(Nothing), String)  
  
    End Sub  
  
    Public Overrides Sub PreExecute()  
  
        textWriter = New StreamWriter(copiedAddressFile, False)  
  
    End Sub  
  
    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
        With textWriter  
            If Not Row.AddressID_IsNull Then  
                .Write(Row.AddressID)  
            End If  
            .Write(columnDelimiter)  
            If Not Row.City_IsNull Then  
                .Write(Row.City)  
            End If  
            .WriteLine()  
        End With  
  
    End Sub  
  
    Public Overrides Sub PostExecute()  
  
        textWriter.Close()  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System.IO;  
public class ScriptMain:  
    UserComponent  
  
{  
    string copiedAddressFile;  
    private StreamWriter textWriter;  
    private string columnDelimiter = ",";  
  
    public override void AcquireConnections(object Transaction)  
    {  
  
        IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileDestConnectionManager;  
        copiedAddressFile = (string) connMgr.AcquireConnection(null);  
  
    }  
  
    public override void PreExecute()  
    {  
  
        textWriter = new StreamWriter(copiedAddressFile, false);  
  
    }  
  
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
    {  
  
        {  
            if (!Row.AddressID_IsNull)  
            {  
                textWriter.Write(Row.AddressID);  
            }  
            textWriter.Write(columnDelimiter);  
            if (!Row.City_IsNull)  
            {  
                textWriter.Write(Row.City);  
            }  
            textWriter.WriteLine();  
        }  
  
    }  
  
    public override void PostExecute()  
    {  
  
        textWriter.Close();  
  
    }  
  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'origine con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)   
 [Sviluppo di un componente di destinazione personalizzato](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
  
  

