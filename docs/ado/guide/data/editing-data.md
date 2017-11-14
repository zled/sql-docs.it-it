---
title: La modifica dei dati | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, editing data
- AdUseClient [ADO]
- editing data [ADO]
ms.assetid: ef514f85-c446-4f05-824e-c9313b2ffae1
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 76a5921185f6643f328559e3bc73dfac46bfee0c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="editing-data"></a>La modifica dei dati
Abbiamo illustrato come utilizzare ADO per connettersi a un'origine dati, eseguire un comando, ottenere i risultati in un **Recordset** dell'oggetto e spostarsi all'interno di **Recordset**. In questa sezione è incentrata sull'operazione di ADO fondamentale: modifica dei dati.  
  
 In questa sezione continua a utilizzare l'esempio **Recordset** introdotta in [analisi dei dati](../../../ado/guide/data/examining-data.md), con una modifica importante. Il codice seguente viene utilizzato per aprire la **Recordset**:  
  
```  
'BeginEditIntro  
    Dim strSQL As String  
    Dim objRs1 As ADODB.Recordset  
  
    strSQL = "SELECT * FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
  
    objRs1.Open strSQL, GetNewConnection, adOpenStatic, _  
                adLockBatchOptimistic, adCmdText  
  
    ' Disconnect the Recordset from the Connection object.  
    Set objRs1.ActiveConnection = Nothing  
'EndEditIntro  
```  
  
 La modifica significativa al codice comporta l'impostazione di **CursorLocation** proprietà del **connessione** uguale all'oggetto **adUseClient** nel  *GetNewConnection* funzione (illustrata nell'esempio successivo), che indica l'utilizzo di un cursore client. Per ulteriori informazioni sulle differenze tra i cursori sul lato client e lato server, vedere [informazioni sui cursori e blocchi](../../../ado/guide/data/understanding-cursors-and-locks.md).  
  
 Il **CursorLocation** della proprietà **adUseClient** impostazione consente di spostare la posizione del cursore dall'origine dati (in questo caso il Server SQL) per il percorso del codice client (workstation desktop). Questa impostazione forza ADO per richiamare il motore del cursore Client OLE DB nel client per creare e gestire il cursore.  
  
 Si può notare inoltre che il **LockType** parametro il **aprire** metodo modificato in **adLockBatchOptimistic**. Si apre il cursore in modalità batch. (Il provider memorizza nella cache più modifiche e li scrive all'origine dati sottostante solo quando si chiama il **UpdateBatch** metodo.) Le modifiche apportate al **Recordset** non verrà aggiornato nel database fino a quando il **UpdateBatch** metodo viene chiamato.  
  
 Infine, il codice in questa sezione Usa una versione modificata della funzione GetNewConnection. Questa versione della funzione ora restituisce un cursore sul lato client. La funzione è simile al seguente:  
  
```  
'BeginNewConnection  
Public Function GetNewConnection() As ADODB.Connection  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim strConnStr As String  
  
    strConnStr = "Provider='SQLOLEDB';Initial Catalog='Northwind';" & _  
                 "Data Source='MySqlServer';Integrated Security='SSPI';"  
  
    objConn.ConnectionString = strConnStr  
    objConn.CursorLocation = adUseClient  
    objConn.Open  
  
    Set GetNewConnection = objConn  
  
    Exit Function  
  
ErrHandler:  
    Set objConn = Nothing  
    Set GetNewConnection = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Function  
'EndNewConnection  
```  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Modifica di record esistenti](../../../ado/guide/data/editing-existing-records.md)  
  
-   [Aggiunta di record](../../../ado/guide/data/adding-records.md)  
  
-   [Determinazione delle funzionalità supportate](../../../ado/guide/data/determining-what-is-supported.md)  
  
-   [Eliminazione di record mediante il metodo Delete](../../../ado/guide/data/deleting-records-using-the-delete-method.md)  
  
-   [Alternative: Utilizzo di istruzioni SQL](../../../ado/guide/data/alternatives-using-sql-statements.md)

