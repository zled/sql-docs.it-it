---
title: Utilizzo di un oggetto di connessione | Documenti Microsoft
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
helpviewer_keywords: connections [ADO]
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f6053e0134a3b9ae866f88aa4ee0742d311c2821
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="using-a-connection-object"></a>Utilizzo di un oggetto di connessione
Prima di aprire un **connessione** dell'oggetto, è necessario definire alcune informazioni sull'origine dati e il tipo di connessione. È assegnata la maggior parte delle informazioni di *ConnectionString* parametro del [Open (metodo)](../../../ado/reference/ado-api/open-method-ado-connection.md) sul **connessione** oggetto, o dal [ConnectionString proprietà](../../../ado/reference/ado-api/connectionstring-property-ado.md) sul **connessione** oggetto. Una stringa di connessione è costituita da un elenco di coppie valore/argomento separati da punti e virgola, con i valori racchiusi tra virgolette singole. Ad esempio  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  È inoltre possibile specificare un nome di origine dati ODBC (DSN) o un file di Data Link (UDL) in una stringa di connessione. Per ulteriori informazioni sui nomi, vedere [gestione delle origini dati](../../../odbc/admin/managing-data-sources.md) in riferimento per programmatori ODBC. Per ulteriori informazioni su file UDL, vedere [Introduzione all'API di collegamento dati](http://msdn.microsoft.com/en-us/95c180ea-bd4f-4dca-b95a-576afd135bbc) in riferimento OLE DB Programmer.  
  
 In genere, si stabilisce una connessione tramite la chiamata di **Connection** metodo con un appropriato un *stringa di connessione* come parametro. Nel frammento di codice Visual Basic seguente è illustrato un esempio:  
  
```  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
' Open a connection.  
Set oConn = New ADODB.Connection  
.Open   
  
' Make a query over the connection.  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
' Close the connection.  
oConn.Close  
Set oConn = Nothing  
  
```  
  
 Qui **oRs.Open** accetta un **connessione** oggetto (*oConn*) variabile come valore del relativo *ActiveConnection* parametro. Inoltre, il **Connection.CursorLocation** proprietà assume il valore predefinito di **adUseServer**. Per ovviare a questo per il [HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md) riportato nella sezione precedente. La seguente istruzione comporta errori di run-time.  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```
