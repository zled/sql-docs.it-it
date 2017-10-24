---
title: Esempio di Visual Basic di Data Shaping | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic example of data shaping[ADO], about data shaping
ms.assetid: d95dd499-19e2-4ce7-b16e-f56a04a9519c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7b2716ffe745fcbb9359c34c33317e61ac82602
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="visual-basic-example-of-data-shaping"></a>Esempio di Visual Basic di Data Shaping
```  
' This application makes use of Microsoft Hierarchical FlexGrid  
' Control, which is named as MSHFLexGrid.  
Const SHAPER = "MSDataShape"  
Const DP = "SQLOLEDB"  
Const DS = "MySQLServer"  
Const DB = "Northwind"  
  
Private Sub Form_Load()  
    FirstExample  
End Sub  
  
Private Sub Form_Resize()  
    MSHFlexGrid.Top = 0  
    MSHFlexGrid.Left = 0  
    MSHFlexGrid.Width = Me.ScaleWidth  
    MSHFlexGrid.Height = Me.ScaleHeight  
End Sub  
  
Private Sub FirstExample()  
    Dim con As ADODB.Connection  
    Dim rst As ADODB.Recordset  
    Dim sCmd As String  
  
    Set con = New ADODB.Connection  
    Set rst = New ADODB.Recordset  
  
    con.ConnectionString = ConnectionString(SHAPER, DP, DS, DB)  
    con.Open  
  
    sCmd = "SHAPE {SELECT CustomerID, ContactName FROM Customers} " _  
        & "APPEND ({SELECT OrderID, OrderDate, CustomerID FROM Orders} " _  
        & "AS chapOrders " _  
        & "RELATE customerID TO customerID)"  
  
    rst.Open sCmd, con, adOpenStatic, 2  
    Set MSHFlexGrid.Recordset = rst  
  
    rst.Close  
    Set rst = Nothing  
  
    con.Close  
    Set con = Nothing  
  
End Sub  
  
Private Function ConnectionString(pr As String, _  
                                  dpr As String, _  
                                  dsr As String, _  
                                  dbs As String)  
    Dim s As String  
    If pr = "" Then  
        s = "Provider=" & dpr & _  
          ";Data Source=" & dsr & _  
          ";Initial Catalog=" & dbs & _  
          ";Integrated Security=SSPI;"  
    Else  
        s = "Provider=" & pr & _  
          ";Data Provider=" & dpr & _  
          ";Data Source=" & dsr & _  
          ";Initial Catalog=" & dbs & _  
          ";Integrated Security=SSPI;"  
    End If  
    ConnectionString = s  
End Function  
  
```  
  
#### <a name="try-it"></a>Provalo!  
  
1.  Creare un progetto di applicazione Visual Basic Standard EXE  
  
2.  Selezionare **componenti** dal **progetto** menu in Visual Studio  
  
3.  Selezionare "Microsoft gerarchica FlexGrid controllo 6.0 (OLEDB)" di **componenti** finestra popup e quindi fare clic su **salvare**.  
  
4.  Fare doppio clic sul controllo FlexGrid dal riquadro casella degli strumenti nell'area di lavoro di Visual Basic. Modificare il nome di questa istanza in MSHFLEXGRID.  
  
5.  Copiare il codice precedente e incollarlo il **codice** pagina per sostituire il codice esistente.  
  
6.  Selezionare **avviare** dal **eseguire** menu per eseguire l'applicazione.

