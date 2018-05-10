---
title: Migrazione da ADO MD ad ADOMD.NET | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc5c88301ac6d777372c66a3e702710ae45b7177
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="migrating-from-ado-md-to-adomdnet"></a>Migrazione da ADO MD ad ADOMD.NET
  La libreria ADOMD.NET è analoga alla libreria ADO MD (ActiveX Data Objects Multidimensional), un'estensione della libreria ADO (ActiveX Data Objects) utilizzata per accedere ai dati multidimensionali nelle applicazioni client basate sul modello COM (Component Object Model). ADO MD consente di accedere in modo semplice ai dati multidimensionali da linguaggi non gestiti, ad esempio C++ e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic, mentre ADOMD.NET consente di accedere facilmente ai dati analitici (sia multidimensionale che di data mining) da linguaggi gestiti, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] C# e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET. In ADOMD.NET è disponibile inoltre un modello a oggetti per metadati notevolmente migliorato.  
  
 La migrazione di applicazioni client esistenti da ADO MD ad ADOMD.NET è semplice da eseguire, ma sono presenti diverse importanti differenze relative alla migrazione:  
  
 **Per fornire l'accesso dati e la connettività alle applicazioni client**  
 |ADO MD|ADOMD.NET|  
|------------|---------------|  
|Necessità di riferimenti sia ad Adodb.dll che ad Adomd.dll.|Necessità di un unico riferimento a Microsoft.AnalysisServices.AdomdClient.dll.|  
  
 La classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> fornisce supporto per la connettività, oltre che l'accesso ai metadati.  
  
 **Per recuperare i metadati per gli oggetti multidimensionali**  
 |ADO MD|ADOMD.NET|  
|------------|---------------|  
|Utilizzare la classe di catalogo.|Utilizzare la proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.|  
  
 **Per eseguire query e restituire oggetti set di celle**  
 |ADO MD|ADOMD.NET|  
|------------|---------------|  
|Utilizzare la classe di set di celle.|Utilizzare la classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.|  
  
 **Per accedere ai metadati che consentono di visualizzare un set di celle**  
 |ADO MD|ADOMD.NET|  
|------------|---------------|  
|Utilizzare la classe di posizione.|Utilizzare gli oggetti <xref:Microsoft.AnalysisServices.AdomdClient.Set> e <xref:Microsoft.AnalysisServices.AdomdClient.Tuple>.|  
  
> [!NOTE]  
>  La classe <xref:Microsoft.AnalysisServices.AdomdClient.Position> è supportata per la compatibilità con le versioni precedenti.  
  
 **Per recuperare i metadati del modello di data mining**  
 In ADO MD non sono disponibili classi. In ADOMD.NET utilizzare una delle raccolte di data mining:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> che contiene un elenco di ogni modello di data mining nell'origine dati.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> che fornisce informazioni sugli algoritmi di data mining disponibili.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> che espone informazioni sulle strutture di data mining nel server.  
  
 Per evidenziare tali differenze, negli esempi di migrazione seguenti viene eseguito il confronto di un'applicazione ADO MD esistente con un'applicazione ADOMD.NET equivalente.  
  
## <a name="looking-at-a-migration-example"></a>Analisi di un esempio di migrazione  
 Sebbene nell'esempio di codice ADO MD esistente e nell'esempio ADOMD.NET equivalente illustrati in questa sezione venga eseguito lo stesso set di azioni, ovvero creazione di una connessione, esecuzione di un'istruzione MDX (Multidimensional Expressions) e recupero di metadati e dati, negli esempi non vengono utilizzati gli stessi oggetti per eseguire tali attività.  
  
### <a name="existing-ado-md-code"></a>Codice ADO MD esistente  
 Esempio di codice seguente, creato nella documentazione di ADO MD 2.8, è scritto in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic® 6.0 e viene utilizzato ADO MD per illustrare come connettersi ed eseguire query su un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati. Questo esempio ADO MD vengono utilizzati i seguenti oggetti:  
  
-   Crea una connessione da un **catalogo** oggetto.  
  
-   Esegue l'istruzione MDX (Multidimensional Expressions) usando il **set di celle** oggetto.  
  
-   Recupera i metadati e dati dal **posizione** oggetto, il recupero dal **set di celle** oggetto.  
  
```  
Private Sub cmdCellSettoDebugWindow_Click()  
Dim cat As New ADOMD.Catalog  
Dim cst As New ADOMD.Cellset  
Dim i As Integer  
Dim j As Integer  
Dim k As Integer  
Dim strServer As String  
Dim strSource As String  
Dim strColumnHeader As String  
Dim strRowText As String  
  
On Error GoTo Error_cmdCellSettoDebugWindow_Click  
Screen.MousePointer = vbHourglass  
'*-----------------------------------------------------------------------  
'* Set server to local host.  
'*-----------------------------------------------------------------------  
    strServer = "LOCALHOST"  
  
'*-----------------------------------------------------------------------  
'* Set MDX query string source.  
'*-----------------------------------------------------------------------  
    strSource = strSource & "SELECT "  
    strSource = strSource & "{[Measures].members} ON COLUMNS,"  
    strSource = strSource & _  
        "NON EMPTY [Store].[Store City].members ON ROWS"  
    strSource = strSource & " FROM Sales"  
  
'*-----------------------------------------------------------------------  
'* Set active connection.  
'*-----------------------------------------------------------------------  
        cat.ActiveConnection = "Data Source=" & strServer & _  
            ";Provider=msolap;"  
  
'*-----------------------------------------------------------------------  
'* Set cellset source to MDX query string.  
'*-----------------------------------------------------------------------  
        cst.Source = strSource  
  
'*-----------------------------------------------------------------------  
'* Set cellset active connection to current connection  
'*-----------------------------------------------------------------------  
    Set cst.ActiveConnection = cat.ActiveConnection  
  
'*-----------------------------------------------------------------------  
'* Open cellset.  
'*-----------------------------------------------------------------------  
    cst.Open  
  
'*-----------------------------------------------------------------------  
'* Allow space for row header text.  
'*-----------------------------------------------------------------------  
strColumnHeader = vbTab & vbTab & vbTab & vbTab & vbTab & vbTab  
  
'*-----------------------------------------------------------------------  
'* Loop through column headers.  
'*-----------------------------------------------------------------------  
       For i = 0 To cst.Axes(0).Positions.Count - 1  
            strColumnHeader = strColumnHeader & _  
                cst.Axes(0).Positions(i).Members(0).Caption & vbTab & _  
                    vbTab & vbTab & vbTab  
       Next  
       Debug.Print vbTab & strColumnHeader & vbCrLf  
  
'*-----------------------------------------------------------------------  
'* Loop through row headers and provide data for each row.  
'*-----------------------------------------------------------------------  
        strRowText = ""  
        For j = 0 To cst.Axes(1).Positions.Count - 1  
            strRowText = strRowText & _  
                cst.Axes(1).Positions(j).Members(0).Caption & vbTab & _  
                    vbTab & vbTab & vbTab  
            For k = 0 To cst.Axes(0).Positions.Count - 1  
                strRowText = strRowText & cst(k, j).FormattedValue & _  
                    vbTab & vbTab & vbTab & vbTab  
            Next  
            Debug.Print strRowText & vbCrLf  
            strRowText = ""  
        Next  
  
    Screen.MousePointer = vbDefault  
Exit Sub  
  
Error_cmdCellSettoDebugWindow_Click:  
   Beep  
   Screen.MousePointer = vbDefault  
   MsgBox "The following error has occurred:" & vbCrLf & _  
      Err.Description, vbCritical, " Error!"  
   Exit Sub  
End Sub  
```  
  
### <a name="equivalent-adomdnet-code"></a>Codice ADOMD.NET equivalente  
 Nell'esempio seguente, scritto in Visual Basic .NET utilizzando ADOMD.NET, viene illustrato come eseguire le stesse azioni dell'esempio scritto in Visual Basic 6.0 precedente. La differenza principale tra l'esempio seguente e l'esempio ADO MD precedente è costituita dagli oggetti utilizzati per eseguire le azioni. Nell'esempio ADOMD.NET vengono utilizzati i seguenti oggetti:  
  
-   Crea una connessione con un **AdomdConnection** oggetto.  
  
-   Esegue l'istruzione MDX tramite un **AdomdCommand** oggetto.  
  
-   Recupera i metadati e dati dal **impostare** oggetto, il recupero dal **set di celle** oggetto.  
  
```  
Private Sub DisplayCellSetInOutputWindow()  
    Dim conn As AdomdConnection  
    Dim cmd As AdomdCommand  
    Dim cst As CellSet  
    Dim i As Integer  
    Dim j As Integer  
    Dim k As Integer  
    Dim strServer As String = "LOCALHOST"  
    Dim strSource As String = "SELECT [Measures].members ON COLUMNS, " & _  
        "NON EMPTY [Store].[Store City].members ON ROWS FROM SALES"  
    Dim strOutput As New System.IO.StringWriter  
  
    '*-----------------------------------------------------------------------  
    '* Open connection.  
    '*-----------------------------------------------------------------------  
    Try  
        ' Create a new AdomdConnection object, providing the connection  
        ' string.  
        conn = New AdomdConnection("Data Source=" & strServer & _  
        ";Provider=msolap;")  
        ' Open the connection.  
        conn.Open()  
    Catch ex As Exception  
        Throw New ApplicationException( _  
            "An error occurred while connecting.")  
    End Try  
  
    Try  
    '*-----------------------------------------------------------------------  
    '* Open cellset.  
    '*-----------------------------------------------------------------------  
        ' Create a new AdomdCommand object, providing the MDX query string.  
        cmd = New AdomdCommand(strSource, conn)  
        ' Run the command and return a CellSet object.  
        cst = cmd.ExecuteCellSet()  
  
    '*-----------------------------------------------------------------------  
    '* Concatenate output.  
    '*-----------------------------------------------------------------------  
  
    ' Include spacing to account for row headers.  
    strOutput.Write(vbTab, 6)  
  
    ' Iterate through the first axis of the CellSet object and  
    ' retrieve column headers.  
    For i = 0 To cst.Axes(0).Set.Tuples.Count - 1  
        strOutput.Write(cst.Axes(0).Set.Tuples(i).Members(0).Caption)  
        strOutput.Write(vbTab, 4)  
    Next  
    strOutput.WriteLine()  
  
    ' Iterate through the second axis of the CellSet object and  
    ' retrieve row headers and cell data.  
    For j = 0 To cst.Axes(1).Set.Tuples.Count - 1  
        ' Append the row header.  
        strOutput.Write(cst.Axes(1).Set.Tuples(j).Members(0).Caption)  
        strOutput.Write(vbTab, 4)  
  
        ' Append the cell data for that row.  
        For k = 0 To cst.Axes(0).Set.Tuples.Count - 1  
            strOutput.Write(cst.Cells(k, j).FormattedValue)  
            strOutput.Write(vbTab, 4)  
        Next  
        strOutput.WriteLine()  
    Next  
  
    ' Display the output.  
    Debug.WriteLine(strOutput.ToString)  
  
    '*-----------------------------------------------------------------------  
    '* Release resources.  
    '*-----------------------------------------------------------------------  
        conn.Close()  
    Catch ex As Exception  
        ' Ignore or handle errors.  
    Finally  
        cst = Nothing  
        cmd = Nothing  
        conn = Nothing  
    End Try  
End Sub  
```  
  
  
