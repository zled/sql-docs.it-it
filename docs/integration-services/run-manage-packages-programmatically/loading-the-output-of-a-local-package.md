---
title: Caricamento dell'Output di un pacchetto locale | Documenti Microsoft
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
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 41de742c987d9f043f3dd247ee84af6a3eaf365b
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="loading-the-output-of-a-local-package"></a>Caricamento dell'output di un pacchetto locale
  Applicazioni client possono leggere l'output di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pacchetti quando l'output viene salvato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazioni utilizzando [!INCLUDE[vstecado](../../includes/vstecado-md.md)], o quando l'output viene salvato in una destinazione file flat utilizzando le classi di **System.IO** dello spazio dei nomi. Tuttavia, un'applicazione client può anche leggere l'output di un pacchetto direttamente dalla memoria, senza la necessità di un passaggio intermedio per rendere persistenti i dati. La chiave per questa soluzione è il **Microsoft.SqlServer.Dts.DtsClient** spazio dei nomi, che contiene implementazioni speciali del **IDbConnection**, **IDbCommand**, e **IDbDataParameter** interfacce dal **System. Data** dello spazio dei nomi. L'assembly Microsoft.SqlServer.Dts.DtsClient.dll è installato per impostazione predefinita in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.  
  
> [!NOTE]  
>  La procedura descritta in questo argomento richiede che la proprietà DelayValidation dell'attività flusso di dati e di eventuali oggetti padre sia impostata sul valore predefinito di **False**.  
  
## <a name="description"></a>Description  
 In questa procedura viene illustrato lo sviluppo di un'applicazione client in codice gestito che carica l'output di un pacchetto con una destinazione DataReader direttamente dalla memoria. I passaggi riepilogati in questa sezione sono illustrati nel codice di esempio seguente.  
  
#### <a name="to-load-data-package-output-into-a-client-application"></a>Per caricare l'output del pacchetto di dati in un'applicazione client  
  
1.  Nel pacchetto configurare una destinazione DataReader in modo da ricevere l'output che si desidera leggere nell'applicazione client. Assegnare alla destinazione DataReader un nome descrittivo, che verrà utilizzato più avanti nell'applicazione client. Prendere nota di tale nome.  
  
2.  Nel progetto di sviluppo, impostare un riferimento al **Microsoft.SqlServer.Dts.DtsClient** spazio dei nomi per l'individuazione dell'assembly **Microsoft.SqlServer.Dts.DtsClient.dll**. Per impostazione predefinita, questo assembly è installato **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**. Importare lo spazio dei nomi nel codice in c# **Using** o [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] **importazioni** istruzione.  
  
3.  Nel codice, creare un oggetto di tipo **DtsClient.DtsConnection** con una stringa di connessione che contiene i parametri della riga di comando richiesti da **dtexec.exe** per eseguire il pacchetto. Per altre informazioni, vedere [dtexec Utility](../../integration-services/packages/dtexec-utility.md). Aprire la connessione con questa stringa di connessione. È inoltre possibile utilizzare il **dtexecui** utilità per creare visivamente la stringa di connessione necessarie.  
  
    > [!NOTE]  
    >  Nel codice di esempio è illustrato il caricamento del pacchetto dal file system tramite la sintassi `/FILE <path and filename>`. Tuttavia, è anche possibile caricare il pacchetto dal database MSDB utilizzando la sintassi `/SQL <package name>` o dall'archivio pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tramite la sintassi `/DTS \<folder name>\<package name>`.  
  
4.  Creare un oggetto di tipo **DtsClient.DtsCommand** che utilizza creato in precedenza **DtsConnection** e impostare il relativo **CommandText** proprietà sul nome dell'oggetto DataReader destinazione nel pacchetto. Chiamare quindi il **ExecuteReader** metodo dell'oggetto comando per caricare i risultati del pacchetto in un nuovo DataReader.  
  
5.  Facoltativamente, è possibile parametrizzare indirettamente l'output del pacchetto tramite la raccolta di **DtsDataParameter** gli oggetti al **DtsCommand** oggetto per passare valori alle variabili definite nel pacchetto. All'interno del pacchetto è possibile utilizzare queste variabili come parametri di query o in espressioni per influire sui risultati restituiti alla destinazione DataReader. È necessario definire queste variabili nel pacchetto nel **DtsClient** dello spazio dei nomi prima di utilizzarli con il **DtsDataParameter** oggetto da un'applicazione client. (Potrebbe essere necessario fare clic sul **selezione colonne finestra variabili** pulsante della barra degli strumenti di **variabili** finestra per visualizzare il **Namespace** colonna.) Nel codice client, quando si aggiunge un **DtsDataParameter** per il **parametri** insieme il **DtsCommand**, omettere il riferimento dello spazio dei nomi DtsClient dal nome della variabile . Esempio:  
  
    ```  
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));  
    ```  
  
6.  Chiamare il **lettura** metodo del DataReader più volte secondo necessità per scorrere le righe di dati di output. Utilizzare i dati o salvarli per un utilizzo successivo nell'applicazione client.  
  
    > [!IMPORTANT]  
    >  Il **lettura** di questa implementazione del DataReader restituisce **true** ancora una volta dopo l'ultima riga di dati è stato letto. Questo rende difficile da usare il solito codice che esegue il ciclo del DataReader mentre **lettura** restituisce **true**. Se il codice tenta di chiudere il DataReader o la connessione dopo aver letto il numero previsto di righe, senza una chiamata finale aggiuntiva per il **lettura** metodo, il codice genererà un'eccezione non gestita. Tuttavia, se il codice tenta di leggere i dati in questa iterazione finale di un ciclo, quando **lettura** restituisce comunque **true** ma è stata passata l'ultima riga, il codice genererà gestita  **ApplicationException** con il messaggio "l'interfaccia IDataReader SSIS è oltre la fine del set di risultati". Questo comportamento è diverso da quello di altre implementazioni di DataReader. Pertanto, quando si utilizza un ciclo per leggere le righe nel DataReader mentre **lettura** restituisce **true**, è necessario scrivere codice per intercettare, test e, eliminare questo previsto  **ApplicationException** nell'ultima chiamata ha esito positivo per il **lettura** metodo. Oppure, se si conosce in anticipo il numero di righe previsto, è possibile elaborare le righe e quindi chiamare il **lettura** metodo ancora una volta prima di chiudere il DataReader e la connessione.  
  
7.  Chiamare il **Dispose** metodo il **DtsCommand** oggetto. Ciò è particolarmente importante se sono stati utilizzati **DtsDataParameter** oggetti.  
  
8.  Chiudere il DataReader e gli oggetti connessione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene eseguito un pacchetto che calcola un singolo valore di aggregazione e lo salva in una destinazione DataReader, quindi legge questo valore dal DataReader e lo visualizza in una casella di testo in un Windows Form.  
  
 L'utilizzo di parametri non è necessario quando si carica l'output di un pacchetto in un'applicazione client. Se non si desidera utilizzare un parametro, è possibile omettere l'utilizzo della variabile nel **DtsClient** dello spazio dei nomi e omettere il codice che usa il **DtsDataParameter** oggetto.  
  
#### <a name="to-create-the-test-package"></a>Per creare un pacchetto di test  
  
1.  Creare un nuovo pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Nel codice di esempio viene utilizzato "DtsClientWParamPkg.dtsx" come nome del pacchetto.  
  
2.  Aggiungere una variabile di tipo String nello spazio dei nomi DtsClient. Nell'esempio di codice viene utilizzato Country come nome della variabile. (Potrebbe essere necessario fare clic sul **selezione colonne finestra variabili** pulsante della barra degli strumenti di **variabili** finestra per visualizzare il **Namespace** colonna.)  
  
3.  Aggiungere una gestione connessione OLE DB che si connette al database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
4.  Aggiungere un'attività Flusso di dati al pacchetto e passare all'area di progettazione Flusso di dati.  
  
5.  Aggiungere un'origine OLE DB al flusso di dati e configurarla per l'utilizzo della gestione connessione OLE DB creata in precedenza, oltre al comando SQL seguente.  
  
    ```  
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?  
    ```  
  
6.  Fare clic su **parametri** e, nel **imposta parametri Query** finestra di dialogo casella, eseguire il mapping solo parametro di input nella query, Parameter0, alla variabile dtsclient:: Country.  
  
7.  Aggiungere una trasformazione Aggregazione al flusso di dati, quindi connettere l'output dell'origine OLE DB alla trasformazione. Aprire Editor trasformazione Aggregazione e configurarlo per eseguire un'operazione "COUNT ALL" su tutte le colonne di input (*) e per restituire come output il valore aggregato con l'alias CustomerCount.  
  
8.  Aggiungere una destinazione DataReader al flusso di dati e connettere l'output della trasformazione Aggregazione alla destinazione DataReader. Nel codice di esempio viene utilizzato "DataReaderDest" come nome del DataReader. Selezionare l'unica colonna di input disponibile, CustomerCount, per la destinazione.  
  
9. Salvare il pacchetto. L'applicazione di test creata di seguito eseguirà il pacchetto e recupererà il relativo output direttamente dalla memoria.  
  
#### <a name="to-create-the-test-application"></a>Per creare l'applicazione di test  
  
1.  Creare una nuova applicazione Windows Form.  
  
2.  Aggiungere un riferimento di **Microsoft.SqlServer.Dts.DtsClient** dello spazio dei nomi passando all'assembly con lo stesso nome in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.  
  
3.  Copiare e incollare il codice di esempio seguente nel modulo di codice per il form.  
  
4.  Modificare il valore del **dtexecArgs** variabile in base alle esigenze in modo che contenga i parametri della riga di comando richiesti da **dtexec.exe** per eseguire il pacchetto. Il codice di esempio carica il pacchetto dal file system.  
  
5.  Modificare il valore del **dataReaderName** variabile in base alle esigenze in modo che contenga il nome della destinazione DataReader nel pacchetto.  
  
6.  Inserire un pulsante e una casella di testo nel form. Il codice di esempio utilizza **btnRun** come il nome del pulsante e **txtResults** come il nome della casella di testo.  
  
7.  Eseguire l'applicazione e fare clic sul pulsante. Dopo una breve pausa durante l'esecuzione del pacchetto, nella casella di testo del form dovrebbe essere visualizzato il valore di aggregazione calcolato dal pacchetto, ovvero il conteggio di clienti in Canada.  
  
### <a name="sample-code"></a>Codice di esempio  
  
```vb  
Imports System.Data  
Imports Microsoft.SqlServer.Dts.DtsClient  
  
Public Class Form1  
  
  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click  
  
    Dim dtexecArgs As String  
    Dim dataReaderName As String  
    Dim countryName As String  
  
    Dim dtsConnection As DtsConnection  
    Dim dtsCommand As DtsCommand  
    Dim dtsDataReader As IDataReader  
    Dim dtsParameter As DtsDataParameter  
  
    Windows.Forms.Cursor.Current = Cursors.WaitCursor  
  
    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""  
    dataReaderName = "DataReaderDest"  
    countryName = "Canada"  
  
    dtsConnection = New DtsConnection()  
    With dtsConnection  
      .ConnectionString = dtexecArgs  
      .Open()  
    End With  
  
    dtsCommand = New DtsCommand(dtsConnection)  
    dtsCommand.CommandText = dataReaderName  
  
    dtsParameter = New DtsDataParameter("Country", DbType.String)  
    dtsParameter.Direction = ParameterDirection.Input  
    dtsCommand.Parameters.Add(dtsParameter)  
  
    dtsParameter.Value = countryName  
  
    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)  
  
    With dtsDataReader  
      .Read()  
      txtResults.Text = .GetInt32(0).ToString("N0")  
    End With  
  
    'After reaching the end of data rows,  
    ' call the Read method one more time.  
    Try  
      dtsDataReader.Read()  
    Catch ex As Exception  
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception on final call to Read method", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    ' The following method is a best practice, and is  
    '  required when using DtsDataParameter objects.  
    dtsCommand.Dispose()  
  
    Try  
      dtsDataReader.Close()  
    Catch ex As Exception  
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception closing DataReader", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    Try  
      dtsConnection.Close()  
    Catch ex As Exception  
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception closing connection", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    Windows.Forms.Cursor.Current = Cursors.Default  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Data;  
using Microsoft.SqlServer.Dts.DtsClient;  
  
namespace DtsClientWParamCS  
{  
  public partial class Form1 : Form  
  {  
    public Form1()  
    {  
      InitializeComponent();  
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);  
    }  
  
    private void btnRun_Click(object sender, EventArgs e)  
    {  
      string dtexecArgs;  
      string dataReaderName;  
      string countryName;  
  
      DtsConnection dtsConnection;  
      DtsCommand dtsCommand;  
      IDataReader dtsDataReader;  
      DtsDataParameter dtsParameter;  
  
      Cursor.Current = Cursors.WaitCursor;  
  
      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";  
      dataReaderName = "DataReaderDest";  
      countryName = "Canada";  
  
      dtsConnection = new DtsConnection();  
      {  
        dtsConnection.ConnectionString = dtexecArgs;  
        dtsConnection.Open();  
      }  
  
      dtsCommand = new DtsCommand(dtsConnection);  
      dtsCommand.CommandText = dataReaderName;  
  
      dtsParameter = new DtsDataParameter("Country", DbType.String);  
      dtsParameter.Direction = ParameterDirection.Input;  
      dtsCommand.Parameters.Add(dtsParameter);  
  
      dtsParameter.Value = countryName;  
  
      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);  
  
      {  
        dtsDataReader.Read();  
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");  
      }  
  
      //After reaching the end of data rows,  
      // call the Read method one more time.  
      try  
      {  
        dtsDataReader.Read();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      // The following method is a best practice, and is  
      //  required when using DtsDataParameter objects.  
      dtsCommand.Dispose();  
  
      try  
      {  
        dtsDataReader.Close();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      try  
      {  
        dtsConnection.Close();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      Cursor.Current = Cursors.Default;  
  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comprendere le differenze tra l'esecuzione locale e remoto](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [Caricamento ed esecuzione di un pacchetto locale a livello di codice](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Caricamento ed esecuzione di un pacchetto remoto a livello di programmazione](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
  
