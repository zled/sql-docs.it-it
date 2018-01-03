---
title: Chiamare una Stored Procedure con un comando | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calling stored procedures [ADO]
- stored procedures [ADO]
- commands [ADO]
ms.assetid: 685f7652-2271-4ede-b552-2eeb8c756b4c
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e6c22f098efcb2352e450c07aece8f88c8f32b4d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="calling-a-stored-procedure-with-a-command"></a>Chiamare una Stored Procedure con un comando
È possibile utilizzare un comando per chiamare una stored procedure. L'esempio di codice alla fine di questo argomento si riferisce a una stored procedure nel database di esempio Northwind, chiamato CustOrdersOrders, che viene definito come segue.  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 Vedere la documentazione di SQL Server per ulteriori informazioni su come definire e chiamare stored procedure.  
  
 Questa stored procedure è simile al comando utilizzato [parametri dell'oggetto Command](../../../ado/guide/data/command-object-parameters.md). Accetta il parametro ID di un cliente e restituisce informazioni sugli ordini del cliente. Esempio di codice seguente usa questa stored procedure come origine per un oggetto ADO **Recordset**.  
  
 Utilizzando la stored procedure consente di accedere a un'altra funzionalità di ADO: il **parametri** raccolta **aggiornamento** metodo. Tramite questo metodo, verranno automaticamente inserite in tutte le informazioni sui parametri necessari per il comando in fase di esecuzione. Si verifica una riduzione delle prestazioni utilizzando questa tecnica, poiché ADO deve eseguire una query origine dati per le informazioni sui parametri.  
  
 Esistono altre differenze sostanziali tra l'esempio di codice seguente e il codice in [parametri dell'oggetto Command](../../../ado/guide/data/command-object-parameters.md), dove i parametri sono stati immessi manualmente. In questo codice viene innanzitutto impostata la **Prepared** proprietà **True** perché è una stored procedure SQL Server e per definizione è precompilata. In secondo luogo, il **CommandType** proprietà del **comando** oggetto modificato in **adCmdStoredProc** nel secondo esempio per informare ADO che il comando è una stored procedure.  
  
 Infine, nel secondo esempio il parametro deve fare riferimento a indice quando si imposta il valore, perché si potrebbe non conosce il nome del parametro in fase di progettazione. Se si conosce il nome del parametro, è possibile impostare il nuovo [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) proprietà del **comando** dell'oggetto su True e si riferiscono al nome della proprietà. Ci si potrebbe chiedere perché la posizione del primo parametro indicato nella stored procedure (@CustomerID) 1 anziché 0 (`objCmd(1) = "ALFKI"`). Questo avviene perché il parametro 0 contiene un valore restituito dalla stored procedure SQL Server.  
  
```  
'BeginAutoParamCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objParm1 As New ADODB.Parameter  
    Dim objRs As New ADODB.Recordset  
  
    ' Set CommandText equal to the stored procedure name.  
    objCmd.CommandText = "CustOrdersOrders"  
    objCmd.CommandType = adCmdStoredProc  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
    objCmd.ActiveConnection = objConn  
  
    ' Automatically fill in parameter info from stored procedure.  
    objCmd.Parameters.Refresh  
  
    ' Set the param value.  
    objCmd(1) = "ALFKI"  
  
    ' Execute once and display...  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    ' ...then set new param value, re-execute command, and display.  
    objCmd(1) = "CACTU"  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
    Exit Sub  
  
ErrHandler:  
    'clean up  
    If objRs.State = adStateOpen Then  
        objRs.Close  
    End If  
  
    If objConn.State = adStateOpen Then  
        objConn.Close  
    End If  
  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndAutoParamCmd  
  
'BeginNewConnection  
Private Function GetNewConnection() As ADODB.Connection  
    Dim oCn As New ADODB.Connection  
    Dim sCnStr As String  
  
    sCnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Integrated Security='SSPI';Initial Catalog='Northwind';"  
    oCn.Open sCnStr  
  
    If oCn.State = adStateOpen Then  
        Set GetNewConnection = oCn  
    End If  
  
End Function  
'EndNewConnection  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Articolo della Knowledge Base 117500](http://go.microsoft.com/fwlink/?LinkId=117500)
