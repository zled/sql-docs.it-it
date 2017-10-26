---
title: sqlsrv_errors | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_errors
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_errors
- sqlsrv_errors
- errors and warnings
ms.assetid: d1fcffec-f34f-46de-9a0e-343f3b5dbae2
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9994273b04f7928826ca5f4c7997d51a548d488e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrverrors"></a>sqlsrv_errors
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce estesi errore e/o avviso informativo sull'ultimo **sqlsrv** operazione eseguita.  
  
Il **sqlsrv_errors** funzione può restituire errori e/o informazioni di avviso quando viene chiamata con uno dei valori di parametro specificati nella sezione relativa ai parametri.  
  
Per impostazione predefinita, gli avvisi generati in una chiamata a qualsiasi funzione **sqlsrv** vengono considerati come errori; se viene generato un avviso in una chiamata a una funzione **sqlsrv** , la funzione restituisce false. Tuttavia, gli avvisi che corrispondono ai valori SQLSTATE 01000, 01001, 01003 e 01S02 non vengono mai considerati come errori.  
  
La riga di codice seguente consente di disattivare il comportamento descritto sopra. Un avviso generato da una chiamata a una funzione **sqlsrv** non fa in modo che la funzione restituisca false:  
  
```  
sqlsrv_configure("WarningsReturnAsErrors", 0);  
```  
  
La riga di codice seguente ripristina il comportamento predefinito; gli avvisi, con le eccezioni descritte sopra, vengono considerati come errori:  
  
```  
sqlsrv_configure("WarningsReturnAsErrors", 1);  
```  
  
Indipendentemente dall'impostazione, gli avvisi possono essere recuperati solo tramite la chiamata **sqlsrv_errors** con il **SQLSRV_ERR_ALL** o **SQLSRV_ERR_WARNINGS** valore del parametro (vedere Sezione parametri che segue per informazioni dettagliate).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_errors( [int $errorsAndOrWarnings] )  
```  
  
#### <a name="parameters"></a>Parametri  
*$errorsAndOrWarnings*[facoltativo]: costante predefinita. Questo parametro può assumere uno dei valori elencati nella tabella seguente:  
  
|Valore|Description|  
|---------|---------------|  
|SQLSRV_ERR_ALL|Vengono restituiti gli errori e gli avvisi generati nell'ultima chiamata di funzione **sqlsrv** .|  
|SQLSRV_ERR_ERRORS|Vengono restituiti gli errori generati nell'ultima chiamata di funzione **sqlsrv** .|  
|SQLSRV_ERR_WARNINGS|Vengono restituiti gli avvisi generati nell'ultima chiamata di funzione **sqlsrv** .|  
  
Se non viene specificato alcun valore di parametro, vengono restituiti gli avvisi e gli errori generati dall'ultima chiamata di funzione **sqlsrv** .  
  
## <a name="return-value"></a>Valore restituito  
Una **matrice** di matrici oppure **null**. Ogni **matrice** nell'oggetto restituito **matrice** contiene tre coppie chiave-valore. Nella tabella seguente sono elencate le chiavi con la relativa descrizione:  
  
|Key|Descrizione|  
|-------|---------------|  
|SQLSTATE|Per errori originati dal driver ODBC, il valore SQLSTATE restituito da ODBC. Per informazioni sui valori SQLSTATE per ODBC, vedere [Codici di errore ODBC](http://go.microsoft.com/fwlink/?linkid=119618).<br /><br />Per gli errori originati dai [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], un valore SQLSTATE di IMSSP.<br /><br />Per gli avvisi originati dai [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], un valore SQLSTATE di 01SSP.|  
|codice|Per errori originati da SQL Server, il codice di errore nativo di SQL Server.<br /><br />Per errori originati dal driver ODBC, il codice di errore restituito da ODBC.<br /><br />Per gli errori originati dai [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], il codice di errore [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] . Per altre informazioni, vedere [Handling Errors and Warnings](../../connect/php/handling-errors-and-warnings.md).|  
|message|Descrizione dell'errore.|  
  
I valori della matrice sono accessibili anche con le chiavi numeriche 0, 1 e 2. Se non si verificano errori o avvisi, viene restituito **null** .  
  
## <a name="example"></a>Esempio  
L'esempio seguente visualizza gli errori che si verificano durante l'esecuzione di un'istruzione non riuscita. (L'istruzione ha esito negativo poiché **InvalidColumName** non è un nome di colonna valido nella tabella specificata.) Nell'esempio si presuppone che SQL Server e [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) database installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nella console.  
  
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
  
/* Set up a query to select an invalid column name. */  
$tsql = "SELECT InvalidColumnName FROM Sales.SalesOrderDetail";  
  
/* Attempt execution. */  
/* Execution will fail because of the invalid column name. */  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
      if( ($errors = sqlsrv_errors() ) != null)  
      {  
         foreach( $errors as $error)  
         {  
            echo "SQLSTATE: ".$error[ 'SQLSTATE']."\n";  
            echo "code: ".$error[ 'code']."\n";  
            echo "message: ".$error[ 'message']."\n";  
         }  
      }  
}  
  
/* Free connection resources */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
  

