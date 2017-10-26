---
title: 'Procedura: recuperare i parametri di Output mediante il Driver SQLSRV | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedure support
ms.assetid: 1157bab7-6ad1-4bdb-a81c-662eea3e7fcd
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 91401b79d504a140147572c5f2c1f7abc439d221
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-retrieve-output-parameters-using-the-sqlsrv-driver"></a>Procedura: Recuperare i parametri di output mediante il driver SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene illustrato come chiamare una stored procedure in cui un parametro è definito come parametro di output. Si noti che durante il recupero di un parametro di output o di input/output, tutti i risultati restituiti dalla stored procedure devono essere usati prima che il valore del parametro restituito sia accessibile.  
  
> [!NOTE]  
> Le variabili inizializzate o aggiornate su **null**, **DateTime**o tipi di flusso non possono essere usate come parametri di output.  
  
Il troncamento dei dati può verificarsi quando vengono usati tipi di flusso, ad esempio SQLSRV_SQLTYPE_VARCHAR('max'), come parametri di output. I tipi di flusso non sono supportati come parametri di output. Per i tipi non di flusso, il troncamento dei dati può verificarsi se la lunghezza del parametro di output non viene specificata o se la lunghezza specificata non è sufficientemente grande per il parametro di output.  
  
## <a name="example"></a>Esempio  
L'esempio seguente effettua una chiamata a una stored procedure che restituisce le vendite da inizio anno di un dipendente specificato. La variabile PHP *$lastName* è un parametro di input e *$salesYTD* è un parametro di output.  
  
> [!NOTE]  
> L'inizializzazione di *$salesYTD* su 0.0 imposta il valore PHPTYPE restituito su **float**. Per garantire l'integrità del tipo di dati, i parametri di output devono essere inizializzati prima di chiamare la stored procedure. In alternativa, è necessario specificare il valore di PHPTYPE desiderato. Per informazioni sull'impostazione di PHPTYPE, vedere [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Poiché la stored procedure restituisce un solo risultato, *$salesYTD* contiene il valore del parametro di output restituito immediatamente dopo l'esecuzione della stored procedure.  
  
> [!NOTE]  
> È consigliabile pertanto chiamare le stored procedure usando la sintassi canonica. Per altre informazioni sulla sintassi canonica, vedere [Chiamata di una stored procedure](http://go.microsoft.com/fwlink/?linkid=119517).  
  
Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) siano installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nella console.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Drop the stored procedure if it already exists. */  
$tsql_dropSP = "IF OBJECT_ID('GetEmployeeSalesYTD', 'P') IS NOT NULL  
                DROP PROCEDURE GetEmployeeSalesYTD";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = " CREATE PROCEDURE GetEmployeeSalesYTD  
                   @SalesPerson nvarchar(50),  
                   @SalesYTD money OUTPUT  
                   AS  
                   SELECT @SalesYTD = SalesYTD  
                   FROM Sales.SalesPerson AS sp  
                   JOIN HumanResources.vEmployee AS e   
                   ON e.EmployeeID = sp.SalesPersonID  
                   WHERE LastName = @SalesPerson";  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
if( $stmt2 === false )  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*--------- The next few steps call the stored procedure. ---------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of  
 the parameters to be passed to the stored procedure */  
$tsql_callSP = "{call GetEmployeeSalesYTD( ?, ? )}";  
  
/* Define the parameter array. By default, the first parameter is an  
INPUT parameter. The second parameter is specified as an OUTPUT  
parameter. Initializing $salesYTD to 0.0 sets the returned PHPTYPE to  
float. To ensure data type integrity, output parameters should be  
initialized before calling the stored procedure, or the desired  
PHPTYPE should be specified in the $params array.*/  
$lastName = "Blythe";  
$salesYTD = 0.0;  
$params = array(   
                 array($lastName, SQLSRV_PARAM_IN),  
                 array($salesYTD, SQLSRV_PARAM_OUT)  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false )  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Display the value of the output parameter $salesYTD. */  
echo "YTD sales for ".$lastName." are ". $salesYTD. ".";  
  
/*Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_free_stmt( $stmt3);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Procedura: Specificare la direzione del parametro usando il driver SQLSRV](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)  
[How to: Retrieve Input and Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)  
[Recupero di dati](../../connect/php/retrieving-data.md)  
  

