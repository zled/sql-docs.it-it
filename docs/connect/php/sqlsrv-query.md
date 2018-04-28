---
title: sqlsrv_query | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- sqlsrv_query
apitype: NA
helpviewer_keywords:
- sqlsrv_query
- executing queries
- API Reference, sqlsrv_query
ms.assetid: 9fa7c4c8-4da8-4299-9893-f61815055aa3
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2186e670acc07f694212fbc008b545446870bf81
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsrvquery"></a>sqlsrv_query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Prepara ed esegue un'istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_query(resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Parametri  
*$conn*: risorsa di connessione associata all'istruzione preparata.  
  
*$tsql*: espressione Transact-SQL che corrisponde all'istruzione preparata.  
  
*$params* [facoltativo]: una **matrice** dei valori corrispondenti ai parametri in una query con parametri. Ogni elemento della matrice può corrispondere a uno dei seguenti:
  
-   Valore letterale.  
  
-   Variabile PHP.  
  
-   **Matrice** con la struttura seguente:  
  
    ```  
    array($value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    La descrizione di ogni elemento della matrice è nella tabella seguente:  
  
    |Elemento|Description|  
    |-----------|---------------|  
    |*$value*|Un valore letterale, una variabile PHP o una variabile PHP per riferimento.|  
    |*$direction*[facoltativo]|Uno dei seguenti **SQLSRV_PARAM _\***  costanti usate per indicare la direzione del parametro: **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. Il valore predefinito è **SQLSRV_PARAM_IN**.<br /><br />Per ulteriori informazioni sulle costanti PHP, vedere [costanti &#40;Microsoft Drivers for PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[facoltativo]|Oggetto **SQLSRV_PHPTYPE _\***  costante che specifica il tipo di dati PHP del valore restituito.<br /><br />Per ulteriori informazioni sulle costanti PHP, vedere [costanti &#40;Microsoft Drivers for PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$sqlType*[facoltativo]|Oggetto **SQLSRV_SQLTYPE\***  costante che specifica il tipo di dati di SQL Server del valore di input.<br /><br />Per ulteriori informazioni sulle costanti PHP, vedere [costanti &#40;Microsoft Drivers for PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
  
*$options* [facoltativo]: matrice associativa che imposta le proprietà della query. Le chiavi supportate sono le seguenti:  
  
|Key|Valori supportati|Description|  
|-------|--------------------|---------------|  
|QueryTimeout|Valore integer positivo.|Imposta il timeout in secondi della query. Per impostazione predefinita, il driver attende indefinitamente per ottenere i risultati.|  
|SendStreamParamsAtExec|**true** o **false**<br /><br />Il valore predefinito è **true**.|Configura il driver per l'invio di tutti i flussi di dati al momento dell'esecuzione (**true**), o per inviare il flusso di dati in blocchi (**false**). Per impostazione predefinita, il valore è impostato su **true**. Per altre informazioni, vedere [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
|Scorrimento|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Per altre informazioni su questi valori, vedere [Specifica di un tipo di cursore e selezione di righe](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
  
## <a name="return-value"></a>Valore restituito  
Risorsa di istruzione. Se l'istruzione non può essere creato e/o eseguita, **false** viene restituito.  
  
## <a name="remarks"></a>Osservazioni  
Il **sqlsrv_query** funzione è ideale per le query singole e deve essere la scelta predefinita per eseguire query a meno che non si verifichino circostanze speciali. Questa funzione fornisce un metodo semplificato per eseguire una query con una quantità minima di codice. La funzione **sqlsrv_query** esegue sia la preparazione che l'esecuzione dell'istruzione e può essere usata per eseguire query con parametri.  
  
Per altre informazioni, vedere [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente viene inserita un'unica riga nella tabella *Sales.SalesOrderDetail* del database AdventureWorks. Nell'esempio si presuppone che SQL Server e il [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) database vengono installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
> [!NOTE]  
> Sebbene l'esempio seguente usa un'istruzione INSERT per illustrare l'uso di **sqlsrv_query** per un'esecuzione di un'istruzione singola, il concetto si applica a qualsiasi istruzione Transact-SQL.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "INSERT INTO Sales.SalesOrderDetail   
        (SalesOrderID,   
         OrderQty,   
         ProductID,   
         SpecialOfferID,   
         UnitPrice,   
         UnitPriceDiscount)  
        VALUES   
        (?, ?, ?, ?, ?, ?)";  
  
/* Set parameter values. */  
$params = array(75123, 5, 741, 1, 818.70, 0.00);  
  
/* Prepare and execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if ($stmt) {  
    echo "Row successfully inserted.\n";  
} else {  
    echo "Row insertion failed.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="example"></a>Esempio  
L'esempio seguente aggiorna un campo di *Sales. SalesOrderDetail* tabella del database AdventureWorks. Nell'esempio si presuppone che SQL Server e il [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) database vengono installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = (?)   
         WHERE SalesOrderDetailID = (?)";  
  
/* Assign literal parameter values. */  
$params = array(5, 10);  
  
/* Execute the query. */  
if (sqlsrv_query($conn, $tsql, $params)) {  
    echo "Statement executed.\n";  
} else {  
    echo "Error in statement execution.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close($conn);  
?>  
```  
  
> [!NOTE]
> È consigliabile utilizzare le stringhe come input durante l'associazione di valori da un [colonna decimal o numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) per garantire la precisione e l'accuratezza PHP limitate precisione per [numeri a virgola mobile](http://php.net/manual/en/language.types.float.php).

## <a name="example"></a>Esempio  
In questo esempio di codice viene illustrato come associare un valore decimale come parametro di input.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
     echo "Could not connect.\n";  
     die(print_r(sqlsrv_errors(), true));  
}  

// Assume TestTable exists with a decimal field 
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_query($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```


## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Procedura: Eseguire query con parametri](../../connect/php/how-to-perform-parameterized-queries.md)  

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  

[Procedura: Inviare dati come flusso](../../connect/php/how-to-send-data-as-a-stream.md)  

[Uso dei parametri direzionali](../../connect/php/using-directional-parameters.md)  

  
