---
title: Creazione di una destinazione ODBC con il componente Script | Documenti Microsoft
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
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5eb539f0d18f473b10ed8d49bcee9c298292fb41
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-odbc-destination-with-the-script-component"></a>Creazione di una destinazione ODBC con il componente script
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è in genere salvare dati in una destinazione ODBC, utilizzando un [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destinazione e [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Provider di dati per ODBC. È possibile, tuttavia, creare anche una destinazione ODBC ad hoc da utilizzare in un solo pacchetto. Per creare questa destinazione ODBC ad hoc, si utilizza il componente script come illustrato nell'esempio seguente.  
  
> [!NOTE]  
>  Se si desidera creare un componente da riutilizzare più facilmente con più attività Flusso di dati e più pacchetti, è possibile utilizzare il codice di questo esempio di componente script come punto iniziale per un componente del flusso di dati personalizzato. Per altre informazioni, vedere [Sviluppo di un componente del flusso di dati personalizzato](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come creare un componente di destinazione che utilizza un database ODBC esistente di gestione connessione per salvare i dati dal flusso di dati in un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.  
  
 In questo esempio è una versione modificata personalizzato [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destinazione dimostrata nell'argomento [creazione di una destinazione con il componente Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). In questo esempio, tuttavia, la destinazione [!INCLUDE[vstecado](../../includes/vstecado-md.md)] personalizzata è stata modificata per l'utilizzo di una gestione connessione ODBC e il salvataggio dei dati in una destinazione ODBC. Queste modifiche includono anche le seguenti:  
  
-   Non è possibile chiamare il **AcquireConnection** metodo della gestione connessione ODBC dal codice gestito, perché restituisce un oggetto nativo. In questo esempio viene pertanto utilizzata la stringa di connessione della gestione connessione per connettersi direttamente all'origine dati tramite il provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ODBC gestito.  
  
-   Il **OdbcCommand** prevede che i parametri posizionali. Le posizioni dei parametri sono indicate dai punti interrogativi (?) nel testo del comando. (Al contrario, un **SqlCommand** previsti parametri denominati.)  
  
 Questo esempio viene utilizzato il **Person. Address** tabella il **AdventureWorks** database di esempio. Nell'esempio vengono passate la prima e la quarta colonna, il * *int*AddressID** * e **nvarchar (30) Città** colonne, di questa tabella tramite il flusso di dati. Questi stessi dati viene utilizzati in origine, trasformazione e gli esempi di destinazione nell'argomento [lo sviluppo di specifici tipi di componenti Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Per configurare l'esempio di componente script  
  
1.  Creare una connessione ODBC manager che si connette a di **AdventureWorks** database.  
  
2.  Creare una tabella di destinazione eseguendo il comando Transact-SQL seguente nel **AdventureWorks** database:  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Aggiungere un nuovo componente script all'area di progettazione del flusso di dati e configurarlo come destinazione.  
  
4.  Connettere l'output di un'origine o di una trasformazione a monte al componente di destinazione in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. È possibile connettere direttamente un'origine a una destinazione senza alcuna trasformazione. Per garantire che funziona in questo esempio, l'output del componente a monte deve includere almeno le **AddressID** e **Città** le colonne di **Person. Address** tabella del **AdventureWorks** database di esempio.  
  
5.  Aprire il **Editor trasformazione Script**. Nel **colonne di Input** pagina, selezionare il **AddressID** e **Città** colonne.  
  
6.  Nel **input e output** pagina, rinominare l'input con un nome più descrittivo, ad esempio **MyAddressInput**.  
  
7.  Nel **gestioni connessioni** pagina, aggiungere o creare la gestione connessione ODBC con un nome descrittivo, ad esempio **MyODBCConnectionManager**.  
  
8.  Nel **Script** pagina, fare clic su **modifica Script**, quindi immettere lo script seguente nel **la classe ScriptMain** classe.  
  
9. Chiudere l'ambiente di sviluppo dello script, chiudere il **Editor trasformazione Script**, e quindi eseguire l'esempio.  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di una destinazione con il componente script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
