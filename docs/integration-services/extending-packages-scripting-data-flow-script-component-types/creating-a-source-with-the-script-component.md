---
title: Creazione di un'origine con il componente Script | Documenti Microsoft
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
- Script component [Integration Services], source components
- output columns [Integration Services]
- sources [Integration Services], components
ms.assetid: 547c4179-ea82-4265-8c6f-04a2aa77a3c0
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4944c3d5752da21fed90f16a38a33b4fad41515
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-source-with-the-script-component"></a>Creazione di un'origine con il componente script
  Utilizzare un componente di origine nel flusso di dati di un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per caricare dati da un'origine dati da passare a trasformazioni e destinazioni a valle. Normalmente, ci si connette all'origine dati tramite una gestione connessione esistente.  
  
 Per una panoramica del componente Script, vedere [estendendo il flusso di dati con il componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
 Il componente script e il codice dell'infrastruttura che genera semplificano in modo significativo il processo di sviluppo di un componente del flusso di dati personalizzato. Tuttavia, per comprendere il funzionamento del componente script, può risultare utile leggere informazioni sui passaggi necessari per lo sviluppo di un componente del flusso di dati personalizzato. Vedere la sezione [lo sviluppo di un componente del flusso di dati personalizzato](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), in particolare l'argomento [lo sviluppo di un componente di origine personalizzato](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).  
  
## <a name="getting-started-with-a-source-component"></a>Introduzione ai componenti di origine  
 Quando si aggiunge un componente di Script nel riquadro flusso di dati di [!INCLUDE[ssIS](../../includes/ssis-md.md)] finestra di progettazione, il **Seleziona tipo componente Script** viene visualizzata la finestra di dialogo che viene richiesto di selezionare uno script di origine, destinazione o trasformazione. In questa finestra di dialogo selezionare **origine**.  
  
## <a name="configuring-a-source-component-in-metadata-design-mode"></a>Configurazione di un componente di origine in modalità di progettazione metadati  
 Dopo aver selezionato per creare un componente di origine, configurare il componente utilizzando il **Editor trasformazione Script**. Per ulteriori informazioni, vedere [configurazione del componente Script nell'Editor del componente di Script](../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
 Un componente di origine del flusso di dati non include input e supporta uno o più output. La configurazione degli output per il componente è uno dei passaggi che è necessario completare in modalità di progettazione metadati, tramite il **Editor trasformazione Script**, prima di scrivere lo script personalizzato.  
  
 È inoltre possibile specificare il linguaggio di scripting impostando il **ScriptLanguage** proprietà il **Script** pagina del **Editor trasformazione Script**.  
  
> [!NOTE]  
>  Per impostare il linguaggio script predefinito per i componenti di Script e le attività di Script, utilizzare il **linguaggio di Scripting** opzione il **generale** pagina del **opzioni** la finestra di dialogo. Per ulteriori informazioni, vedere [General Page](~/integration-services/control-flow/script-task-editor-general-page.md).  
  
### <a name="adding-connection-managers"></a>Aggiunta di gestioni connessioni  
 Normalmente, un componente di origine utilizza una gestione connessione esistente per connettersi all'origine dati da cui carica dati nel flusso di dati. Nel **gestioni connessioni** pagina del **Editor trasformazione Script**, fare clic su **Aggiungi** per aggiungere la gestione connessione appropriata.  
  
 Tuttavia, una gestione connessione è solo un'unità pratica che incapsula e archivia le informazioni necessarie per la connessione a un'origine dati di un determinato tipo. È necessario scrivere codice personalizzato per caricare o salvare i dati e possibilmente anche per aprire e chiudere la connessione all'origine dati.  
  
 Per informazioni generali sull'utilizzo delle gestioni connessioni con il componente Script, vedere [connessione alle origini dati nel componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
 Per ulteriori informazioni sul **gestioni connessioni** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; Pagina gestioni connessioni &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
### <a name="configuring-outputs-and-output-columns"></a>Configurazione di output e colonne di output  
 Un componente di origine non include input e supporta uno o più output. Nel **input e output** pagina del **Editor trasformazione Script**, è stato creato un singolo output per impostazione predefinita, ma non le colonne di output sono state create. In questa pagina dell'editor può essere necessario o consigliabile configurare gli elementi seguenti.  
  
-   È necessario aggiungere e configurare manualmente le colonne di output per ogni output. Selezionare la cartella colonne di Output per ogni output e quindi utilizzare il **Aggiungi colonna** e **Rimuovi colonna** pulsanti per gestire le colonne di output per ogni output del componente di origine. In seguito, si farà riferimento alle colonne di output nello script in base ai nomi assegnati in questo passaggio, utilizzando le proprietà delle funzioni di accesso tipizzate create nel codice generato automaticamente.  
  
-   È possibile creare uno o più output aggiuntivi, ad esempio un output degli errori simulati per le righe che contengono valori imprevisti. Utilizzare il **Aggiungi Output** e **Rimuovi Output** pulsanti per gestire gli output del componente di origine. Tutte le righe di input vengono indirizzate a tutti gli output disponibili se non si specifica un valore identico diverso da zero per il **ExclusionGroup** proprietà di tali output in cui si intenda indirizzare ogni riga a uno solo di output che condividono lo stesso **ExclusionGroup** valore. Il valore intero specifico selezionato per identificare il **ExclusionGroup** non è significativo.  
  
    > [!NOTE]  
    >  È inoltre possibile utilizzare un diverso da zero **ExclusionGroup** valore della proprietà con un singolo output quando non si desidera tutte le righe di output. In questo caso, tuttavia, è necessario chiamare esplicitamente il **DirectRowTo\<outputbuffer >** metodo per ogni riga che si desidera inviare all'output.  
  
-   È necessario assegnare un nome descrittivo agli output. In seguito, si farà riferimento agli output in base ai nomi presenti nello script, utilizzando le proprietà delle funzioni di accesso tipizzate create nel codice generato automaticamente.  
  
-   Normalmente, più output nello stesso **ExclusionGroup** hanno le stesse colonne di output. Tuttavia, se si crea un output degli errori simulati, è possibile aggiungere più colonne per archiviare le informazioni sugli errori. Per informazioni su come motore del flusso di dati elabora le righe di errore, vedere [tramite output degli errori in un componente del flusso di dati](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md). Nel componente script, tuttavia, è necessario scrivere codice personalizzato per inserire le informazioni appropriate sugli errori nelle colonne aggiuntive. Per ulteriori informazioni, vedere [simulando un Output degli errori per il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
 Per ulteriori informazioni sul **input e output** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; input e output pagina &#41;](../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md).  
  
### <a name="adding-variables"></a>Aggiunta di variabili  
 Se sono presenti tutte le variabili esistenti i cui valori che si desidera utilizzare nello script, è possibile aggiungerli nel **ReadOnlyVariables** e **ReadWriteVariables** campi proprietà il **Script** pagina della finestra di **Editor trasformazione Script**.  
  
 Quando si immettono più variabili nei campi delle proprietà, separare i relativi nomi con virgole. È inoltre possibile immettere più variabili facendo clic sui puntini di sospensione (**...** ) accanto al pulsante il **ReadOnlyVariables** e **ReadWriteVariables** campi delle proprietà e selezionando le variabili nella **Seleziona variabili** la finestra di dialogo .  
  
 Per informazioni generali su come usare le variabili con il componente Script, vedere [utilizzo di variabili nel componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
 Per ulteriori informazioni sul **Script** pagina del **Editor trasformazione Script**, vedere [Editor trasformazione Script &#40; Pagina di script &#41; ](../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
## <a name="scripting-a-source-component-in-code-design-mode"></a>Generazione di script per un componente di origine in modalità di progettazione codice  
 Dopo aver configurato i metadati per il componente, aprire il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE per codificare gli script personalizzati. Per aprire VSTA, fare clic su **modifica Script** sul **Script** pagina del **Editor trasformazione Script**. È possibile scrivere lo script utilizzando [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c#, a seconda del linguaggio di script selezionato per il **ScriptLanguage** proprietà.  
  
 Per informazioni importanti che si applica a tutti i tipi di componenti creati tramite il componente Script, vedere [la codifica e debug del componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="understanding-the-auto-generated-code"></a>Informazioni sul codice generato automaticamente  
 Quando si apre l'IDE di VSTA dopo la creazione e configurazione di un componente di origine, modificabile **la classe ScriptMain** classe viene visualizzata nell'editor di codice. Scrivere il codice personalizzato **la classe ScriptMain** classe.  
  
 Il **la classe ScriptMain** classe include uno stub per il **CreateNewOutputRows** metodo. Il **CreateNewOutputRows** è il metodo più importante in un componente di origine.  
  
 Se si apre il **Esplora progetti** in VSTA, è possibile visualizzare che il componente Script ha generato anche sola lettura **BufferWrapper** e **ComponentWrapper** progetto elementi. Il **la classe ScriptMain** classe eredita da **UserComponent** classe il **ComponentWrapper** elemento del progetto.  
  
 In fase di esecuzione, il motore del flusso di dati richiama il **PrimeOutput** metodo nel **UserComponent** classe, che esegue l'override di <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PrimeOutput%2A> metodo del <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> classe padre. Il **PrimeOutput** metodo a sua volta chiama i metodi seguenti:  
  
1.  Il **CreateNewOutputRows** metodo, che si esegue l'override **la classe ScriptMain** per aggiungere righe dall'origine dati per l'output, i buffer sono inizialmente vuoti.  
  
2.  Il **FinishOutputs** (metodo), che è vuota per impostazione predefinita. Eseguire l'override di questo metodo in **la classe ScriptMain** per eseguire qualsiasi elaborazione che è necessario per completare l'output.  
  
3.  Privato **MarkOutputsAsFinished** metodo che chiama il <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.SetEndOfRowset%2A> metodo il <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> padre classe per indicare al motore del flusso di dati che l'output è stata completata. Non è necessario chiamare **SetEndOfRowset** in modo esplicito nel codice.  
  
### <a name="writing-your-custom-code"></a>Scrittura di codice personalizzato  
 Per completare la creazione di un componente di origine personalizzata, si consiglia di scrivere script nei metodi seguenti disponibili nel **la classe ScriptMain** classe.  
  
1.  Eseguire l'override di **AcquireConnections** metodo per la connessione all'origine dati esterna. Estrarre l'oggetto connessione o le informazioni di connessione necessarie dalla gestione connessione.  
  
2.  Eseguire l'override di **PreExecute** metodo per caricare i dati, se è possibile caricare tutti i dati di origine nello stesso momento. Ad esempio, è possibile eseguire un **SqlCommand** contro un [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database e caricare tutti i dati di origine nello stesso momento in un **SqlDataReader**. Se è necessario caricare la riga di origine dati una alla volta (ad esempio, durante la lettura di un file di testo), è possibile caricare i dati, il ciclo delle righe in **CreateNewOutputRows**.  
  
3.  Utilizzare sottoposto a override **CreateNewOutputRows** metodo per aggiungere nuove righe ai buffer di output vuoto e inserire i valori di ogni colonna nelle nuove righe di output. Utilizzare il **AddRow** metodo di ogni buffer di output per aggiungere una nuova riga vuota e quindi impostare i valori di ogni colonna. In genere si copiano i valori dalle colonne caricate dall'origine esterna.  
  
4.  Eseguire l'override di **PostExecute** metodo per terminare l'elaborazione dei dati. Ad esempio, è possibile chiudere il **SqlDataReader** utilizzata per caricare i dati.  
  
5.  Eseguire l'override di **ReleaseConnections** metodo per disconnettersi dall'origine dati esterna, se necessario.  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti viene illustrano il codice personalizzato che è necessario il **la classe ScriptMain** classe per creare un componente di origine.  
  
> [!NOTE]  
>  Negli esempi viene utilizzata la **Person. Address** tabella il **AdventureWorks** database di esempio e passate la prima e la quarta colonna, il **intAddressID** e  **nvarchar (30) Città** colonne, tramite il flusso di dati. Gli stessi dati vengono utilizzati negli esempi relativi a origine, trasformazione e destinazione in questa sezione. Per ogni esempio, sono documentati ulteriori prerequisiti e presupposti.  
  
### <a name="adonet-source-example"></a>Esempio di origine ADO.NET  
 Questo esempio viene illustrato un componente di origine che utilizza un oggetto esistente [!INCLUDE[vstecado](../../includes/vstecado-md.md)] gestione connessione per caricare dati da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella nel flusso di dati.  
  
 Se si desidera eseguire questo codice di esempio, è necessario configurare il pacchetto e il componente come segue:  
  
1.  Creare un [!INCLUDE[vstecado](../../includes/vstecado-md.md)] gestione connessione che utilizza il **SqlClient** provider a cui connettersi il **AdventureWorks** database.  
  
2.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come origine.  
  
3.  Aprire il **Editor trasformazione Script**. Nel **input e output** pagina, rinominare l'output predefinito con un nome più descrittivo, ad esempio **MyAddressOutput**, quindi aggiungere e configurare le due colonne di output, **AddressID**e **Città**.  
  
    > [!NOTE]  
    >  Assicurarsi di modificare il tipo di dati di **Città** colonna di output nel tipo DT_WSTR.  
  
4.  Nel **gestioni connessioni** pagina, aggiungere o creare la [!INCLUDE[vstecado](../../includes/vstecado-md.md)] gestione connessione e assegnargli un nome, ad esempio **MyADONETConnection**.  
  
5.  Nel **Script** pagina, fare clic su **modifica Script** e immettere lo script seguente. Chiudere l'ambiente di sviluppo dello script e **Editor trasformazione Script**.  
  
6.  Creare e configurare un componente di destinazione, ad esempio un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione o il componente di destinazione di esempio illustrato in [creazione di una destinazione con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), che prevede il  **AddressID** e **Città** colonne. Quindi, connettere il componente di origine alla destinazione. È possibile connettere direttamente un'origine a una destinazione senza alcuna trasformazione. È possibile creare una tabella di destinazione eseguendo il seguente comando [!INCLUDE[tsql](../../includes/tsql-md.md)] comando il **AdventureWorks** database:  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
7.  Eseguire l'esempio.  
  
    ```vb  
    Imports System.Data.SqlClient  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim connMgr As IDTSConnectionManager100  
        Dim sqlConn As SqlConnection  
        Dim sqlReader As SqlDataReader  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            connMgr = Me.Connections.MyADONETConnection  
            sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            Dim cmd As New SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn)  
            sqlReader = cmd.ExecuteReader  
  
        End Sub  
  
        Public Overrides Sub CreateNewOutputRows()  
  
            Do While sqlReader.Read  
                With MyAddressOutputBuffer  
                    .AddRow()  
                    .AddressID = sqlReader.GetInt32(0)  
                    .City = sqlReader.GetString(1)  
                End With  
            Loop  
  
        End Sub  
  
        Public Overrides Sub PostExecute()  
  
            sqlReader.Close()  
  
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
        SqlDataReader sqlReader;  
  
        public override void AcquireConnections(object Transaction)  
        {  
            connMgr = this.Connections.MyADONETConnection;  
            sqlConn = (SqlConnection)connMgr.AcquireConnection(null);  
  
        }  
  
        public override void PreExecute()  
        {  
  
            SqlCommand cmd = new SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn);  
            sqlReader = cmd.ExecuteReader();  
  
        }  
  
        public override void CreateNewOutputRows()  
        {  
  
            while (sqlReader.Read())  
            {  
                {  
                    MyAddressOutputBuffer.AddRow();  
                    MyAddressOutputBuffer.AddressID = sqlReader.GetInt32(0);  
                    MyAddressOutputBuffer.City = sqlReader.GetString(1);  
                }  
            }  
  
        }  
  
        public override void PostExecute()  
        {  
  
            sqlReader.Close();  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            connMgr.ReleaseConnection(sqlConn);  
  
        }  
  
    }  
    ```  
  
### <a name="flat-file-source-example"></a>Esempio di origine file flat  
 In questo esempio è illustrato un componente di origine che utilizza una gestione connessione file flat esistente per caricare dati da un file flat nel flusso di dati. I dati di origine del file flat vengono creati esportandoli da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se si desidera eseguire questo codice di esempio, è necessario configurare il pacchetto e il componente come segue:  
  
1.  Utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importazione / esportazione guidata per esportare il **Person. Address** tabella il **AdventureWorks** database di esempio in un file flat delimitato da virgole. In questo esempio viene utilizzato il nome file ExportedAddresses.txt.  
  
2.  Creare una gestione connessione file flat che si connette al file di dati esportato.  
  
3.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come origine.  
  
4.  Aprire il **Editor trasformazione Script**. Nel **input e output** pagina, rinominare l'output predefinito con un nome più descrittivo, ad esempio **MyAddressOutput**. Aggiungere e configurare le due colonne di output, **AddressID** e **Città**.  
  
5.  Nel **gestioni connessioni** pagina, aggiungere o creare la connessione File Flat gestione utilizzando un nome descrittivo, ad esempio **MyFlatFileSrcConnectionManager**.  
  
6.  Nel **Script** pagina, fare clic su **modifica Script** e immettere lo script seguente. Chiudere l'ambiente di sviluppo dello script e **Editor trasformazione Script**.  
  
7.  Creare e configurare un componente di destinazione, ad esempio un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione o il componente di destinazione di esempio illustrato in [creazione di una destinazione con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Quindi, connettere il componente di origine alla destinazione. È possibile connettere direttamente un'origine a una destinazione senza alcuna trasformazione. È possibile creare una tabella di destinazione eseguendo il seguente comando [!INCLUDE[tsql](../../includes/tsql-md.md)] comando il **AdventureWorks** database:  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
8.  Eseguire l'esempio.  
  
    ```vb  
    Imports System.IO  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Private textReader As StreamReader  
        Private exportedAddressFile As String  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connMgr As IDTSConnectionManager100 = _  
                Me.Connections.MyFlatFileSrcConnectionManager  
            exportedAddressFile = _  
                CType(connMgr.AcquireConnection(Nothing), String)  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
            MyBase.PreExecute()  
            textReader = New StreamReader(exportedAddressFile)  
        End Sub  
  
        Public Overrides Sub CreateNewOutputRows()  
  
            Dim nextLine As String  
            Dim columns As String()  
  
            Dim delimiters As Char()  
            delimiters = ",".ToCharArray  
  
            nextLine = textReader.ReadLine  
            Do While nextLine IsNot Nothing  
                columns = nextLine.Split(delimiters)  
                With MyAddressOutputBuffer  
                    .AddRow()  
                    .AddressID = columns(0)  
                    .City = columns(3)  
                End With  
                nextLine = textReader.ReadLine  
            Loop  
  
        End Sub  
  
        Public Overrides Sub PostExecute()  
            MyBase.PostExecute()  
            textReader.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.IO;  
    public class ScriptMain:  
        UserComponent  
  
    {  
        private StreamReader textReader;  
        private string exportedAddressFile;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileSrcConnectionManager;  
            exportedAddressFile = (string)connMgr.AcquireConnection(null);  
  
        }  
  
        public override void PreExecute()  
        {  
            base.PreExecute();  
            textReader = new StreamReader(exportedAddressFile);  
        }  
  
        public override void CreateNewOutputRows()  
        {  
  
            string nextLine;  
            string[] columns;  
  
            char[] delimiters;  
            delimiters = ",".ToCharArray();  
  
            nextLine = textReader.ReadLine();  
            while (nextLine != null)  
            {  
                columns = nextLine.Split(delimiters);  
                {  
                    MyAddressOutputBuffer.AddRow();  
                    MyAddressOutputBuffer.AddressID = columns[0];  
                    MyAddressOutputBuffer.City = columns[3];  
                }  
                nextLine = textReader.ReadLine();  
            }  
  
        }  
  
        public override void PostExecute()  
        {  
  
            base.PostExecute();  
            textReader.Close();  
  
        }  
  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di una destinazione con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)   
 [Sviluppo di un componente di origine personalizzato](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
  
  

