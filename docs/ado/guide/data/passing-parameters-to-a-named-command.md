---
title: Passaggio di parametri a un comando denominato | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- named commands [ADO]
- commands [ADO], passing parameters to a named command
ms.assetid: 36e0cdbe-7f50-40f5-af0d-700f5d8dc75a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f98080e73f2a0eb32450c0bc8e5779471adc74c6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="passing-parameters-to-a-named-command"></a>Passaggio di parametri a un comando denominato
Analogamente a come il risultato del comando viene passato come un *out* variabili del comando denominato, parametri per un comando con parametri è stato passato come *in* variabili per il comando specificato.  
  
 Nell'esempio di codice riportato di seguito viene eseguito un tentativo di recuperare tutti gli ordini effettuati dal cliente il cui **CustomerID** è "Base al ALKFI" dal database Northwind. Il valore di **CustomerID** viene fornito al momento quando viene chiamato il comando specificato.  
  
```  
Const DS = "MySqlServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim objConn As New ADODB.Connection  
Dim objRs As New ADODB.Recordset  
Dim objComm As New ADODB.Command  
  
CommandText = "SELECT OrderID, OrderDate, " & _  
                     "RequiredDate, ShippedDate " & _  
                     "FROM Orders " & _  
                     "WHERE CustomerID = ? " & _  
                     "ORDER BY OrderID"  
  
ConnectionString = "Provider=" & DP & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;"  
  
' Connect to the data source.  
objConn.Open ConnectionString  
  
' Set a named command.  
objComm.CommandText = CommandText  
objComm.CommandType = adCmdText  
objComm.Name = "GetOrdersOf"  
Set objComm.ActiveConnection = objConn  
  
' Call the named command, passing a CustomerID value  
' as the input parameter.   
'    "ALFKI" is the required input parameter,  
'    objRs is the resultant output variable.  
objConn.GetOrdersOf "ALKFI", objRs  
  
' Display the result.  
Debug.Print "All orders by ALFKI:"  
Do While Not objRs.EOF  
    Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                objRs(2) & vbTab & objRs(3)  
    objRs.MoveNext  
Loop  
  
' Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
Set objComm = Nothing  
```  
  
 Si noti che tutti i parametri di input devono precedere qualsiasi variabile di output e i tipi di dati dei parametri devono corrispondere o possono essere convertiti a quelle dei campi corrispondenti. L'istruzione seguente:  
  
```  
objConn.GetOrdersOf 12345, objRs  
```  
  
 -verrà generato un errore di tipi di dati non corrispondenti, perché il parametro di input obbligatorio è di un **stringa** tipo, non di un **intero** tipo.  
  
 La chiamata seguente:  
  
```  
objConn.GetOrdersOf "12345", objRs  
```  
  
 -è valido, ma verrà restituito un risultato vuoto impostato perché tale record non esiste nel database.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
