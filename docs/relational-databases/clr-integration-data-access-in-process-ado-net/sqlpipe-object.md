---
title: Oggetto SqlPipe | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
caps.latest.revision: 54
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 48f672ff313848809cc92dde6f9f1127d5c2bdfc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlpipe-object"></a>Oggetto SqlPipe
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è molto comune scrivere una stored procedure (o una stored procedure estesa) per l'invio di risultati o parametri di output al client chiamante.  
  
 In un [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, di qualsiasi **selezionare** istruzione che restituisce zero o più righe invia i risultati del chiamante connesso "pipe."  
  
 Per common language runtime (CLR) di database in esecuzione in oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile inviare i risultati alla pipe connessa utilizzando il **inviare** metodi il **SqlPipe** oggetto. Accesso di **Pipe** proprietà del **SqlContext** per ottenere il **SqlPipe** oggetto. Il **SqlPipe** è concettualmente simile alla classe il **risposta** trovare la classe in ASP.NET. Per ulteriori informazioni, vedere documentazione di riferimento per la classe SqlPipe in .NET Framework SDK (Software Development Kit).  
  
## <a name="returning-tabular-results-and-messages"></a>Restituzione di risultati tabulari e messaggi  
 Il **SqlPipe** ha un **inviare** metodo che presenta tre overload. ovvero:  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 Il **inviare** metodo invia dati direttamente al client o al chiamante. In genere è il client che utilizza l'output di **SqlPipe**, ma nel caso di stored procedure CLR nidificate il consumer dell'output può anche essere una stored procedure. Procedure1 chiama ad esempio SqlCommand.ExecuteReader() con il testo del comando "EXEC Procedure2". Procedure2 è anche una stored procedure gestita. Se Procedure2 chiama il metodo SqlPipe.Send(SqlDataRecord), la riga verrà inviata al lettore di Procedure1, non al client.  
  
 Il **inviare** metodo invia un messaggio stringa che viene visualizzato sul client come messaggio informativo, equivalente a PRINT in [!INCLUDE[tsql](../../includes/tsql-md.md)]. Può inoltre inviare una set di risultati utilizzando a riga singola **SqlDataRecord**, o una riga a più set di risultati utilizzando un **SqlDataReader**.  
  
 Il **SqlPipe** oggetto dispone anche di un **ExecuteAndSend** metodo. Questo metodo può essere utilizzato per eseguire un comando (passato come un **SqlCommand** oggetto) e inviare i risultati direttamente al chiamante. Se sono presenti errori nel comando inviato, le eccezioni vengono inviate alla pipe, ma una copia viene inviata anche al codice gestito chiamante. Se il codice chiamante non rileva l'eccezione, lo stack verrà propagato al codice [!INCLUDE[tsql](../../includes/tsql-md.md)] e verrà visualizzato due volte nell'output. Se il codice chiamante rileva l'eccezione, il consumer della pipe visualizzerà l'errore, ma questo non verrà duplicato.  
  
 Può accettare solo un **SqlCommand** che è associato alla connessione di contesto; non può accettare un comando che viene associato alla connessione senza contesto.  
  
## <a name="returning-custom-result-sets"></a>Restituzione di set di risultati personalizzati  
 Stored procedure gestite possono inviare set di risultati che non provengono da un **SqlDataReader**. Il **SendResultsStart** metodo, insieme a **SendResultsRow** e **SendResultsEnd**, consente alle stored procedure di inviare set di risultati personalizzati al client.  
  
 **SendResultsStart** accetta un **SqlDataRecord** come input. Indica l'inizio di un set di risultati e utilizza i metadati del record per costruire i metadati che descrivono il set in questione. Non invia il valore del record con **SendResultsStart**. Tutte le righe successive, inviate mediante **SendResultsRow**, deve corrispondere una definizione dei metadati.  
  
> [!NOTE]  
>  Dopo la chiamata di **SendResultsStart** solo metodo **SendResultsRow** e **SendResultsEnd** può essere chiamato. La chiamata a qualsiasi altro metodo nella stessa istanza di **SqlPipe** provoca un **InvalidOperationException**. **SendResultsEnd** imposta **SqlPipe** allo stato iniziale in cui è possibile chiamare altri metodi.  
  
### <a name="example"></a>Esempio  
 Il **uspGetProductLine** stored procedure restituisce il nome, numero di prodotto, colore e di listino di tutti i prodotti all'interno di una linea di prodotti specificata. Questa stored procedure accetta corrispondenze esatte per *prodLine*.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 Nell'esempio [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione esegue il **uspGetProduct** routine che restituisce un elenco di biciclette da passeggio.  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto SqlDataRecord](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)   
 [Stored procedure CLR](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [Estensioni specifiche In-Process di SQL Server ad ADO.NET](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
