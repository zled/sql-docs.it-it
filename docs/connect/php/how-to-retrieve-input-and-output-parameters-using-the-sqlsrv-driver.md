---
title: 'Procedura: recuperare i parametri dei / o mediante il Driver SQLSRV | Documenti Microsoft'
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
ms.assetid: 9a7c5f60-67f9-4968-a3a8-c256ee481da2
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9278465398b033d198ec5b3304f9c601f5cb677b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver"></a>How to: Retrieve Input and Output Parameters Using the SQLSRV Driver
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene illustrato come usare il driver SQLSRV per chiamare una stored procedure in cui un parametro è definito come parametro di input/output e come recuperare i risultati. Si noti che durante il recupero di un parametro di output o di input/output, tutti i risultati restituiti dalla stored procedure devono essere usati prima che il valore del parametro restituito sia accessibile.  
  
> [!NOTE]  
> Le variabili inizializzate o aggiornate su **null**, **DateTime**o tipi di flusso non possono essere usate come parametri di output.  
  
## <a name="example"></a>Esempio  
L'esempio seguente chiama una stored procedure che sottrae le ore di ferie usufruite dalle ore di ferie disponibili di un dipendente specifico. La variabile che rappresenta le ore di ferie usufruite, *$vacationHrs*, viene passata alla stored procedure come parametro di input. Dopo aver aggiornato le ore di ferie disponibili, la stored procedure usa lo stesso parametro per restituire il numero di ore di ferie rimanenti.  
  
> [!NOTE]  
> L'inizializzazione di *$vacationHrs* su 4 imposta il valore restituito di PHPTYPE su Integer. Per garantire l'integrità del tipo di dati, i parametri di input/output devono essere inizializzati prima di chiamare la stored procedure. In alternativa, è necessario specificare il valore di PHPTYPE voluto. Per informazioni sull'impostazione di PHPTYPE, vedere [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Poiché la stored procedure restituisce due risultati, [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md) deve essere chiamato dopo che è stata eseguita la stored procedure per rendere disponibile il valore del parametro di output. Dopo la chiamata **sqlsrv_next_result**, *$vacationHrs* contiene il valore del parametro di output restituito dalla stored procedure.  
  
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
$tsql_dropSP = "IF OBJECT_ID('SubtractVacationHours', 'P') IS NOT NULL  
                DROP PROCEDURE SubtractVacationHours";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = "CREATE PROCEDURE SubtractVacationHours  
                        @EmployeeID int,  
                        @VacationHrs smallint OUTPUT  
                  AS  
                  UPDATE HumanResources.Employee  
                  SET VacationHours = VacationHours - @VacationHrs  
                  WHERE EmployeeID = @EmployeeID;  
                  SET @VacationHrs = (SELECT VacationHours  
                                      FROM HumanResources.Employee  
                                      WHERE EmployeeID = @EmployeeID)";  
  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
if( $stmt2 === false )  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*--------- The next few steps call the stored procedure. ---------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of  
the parameters to be passed to the stored procedure */  
$tsql_callSP = "{call SubtractVacationHours( ?, ?)}";  
  
/* Define the parameter array. By default, the first parameter is an  
INPUT parameter. The second parameter is specified as an INOUT  
parameter. Initializing $vacationHrs to 8 sets the returned PHPTYPE to  
integer. To ensure data type integrity, output parameters should be  
initialized before calling the stored procedure, or the desired  
PHPTYPE should be specified in the $params array.*/  
  
$employeeId = 4;  
$vacationHrs = 8;  
$params = array(   
                 array($employeeId, SQLSRV_PARAM_IN),  
                 array($vacationHrs, SQLSRV_PARAM_INOUT)  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false )  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Display the value of the output parameter $vacationHrs. */  
sqlsrv_next_result($stmt3);  
echo "Remaining vacation hours: ".$vacationHrs;  
  
/*Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_free_stmt( $stmt3);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Procedura: Specificare la direzione del parametro usando il driver SQLSRV](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)  
[Procedura: Recuperare i parametri di output mediante il driver SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)  
[Recupero di dati](../../connect/php/retrieving-data.md)  
  

