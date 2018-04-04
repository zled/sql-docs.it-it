---
title: sqlsrv_get_field | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- sqlsrv_get_field
apitype: NA
helpviewer_keywords:
- sqlsrv_get_field
- API Reference, sqlsrv_get_field
- retrieving data, as a single field
ms.assetid: fa17cc56-fb38-433b-a40d-65642f04dc23
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ff8f669772a8bd2ef0920992e9375c8795a7467b
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="sqlsrvgetfield"></a>sqlsrv_get_field
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera i dati dal campo specificato della riga corrente. L'accesso ai dati dei campi deve avvenire in successione. Ad esempio, non è possibile accedere ai dati del primo campo dopo aver eseguito l'accesso ai dati del secondo campo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_get_field( resource $stmt, int $fieldIndex [, int $getAsType])  
```  
  
#### <a name="parameters"></a>Parametri  
*$stmt*: risorsa di istruzione corrispondente a un'istruzione eseguita.  
  
*$fieldIndex*: indice del campo da recuperare. Gli indici iniziano da zero.  
  
*$getAsType* [facoltativo]: una **SQLSRV** costante (**SQLSRV_PHPTYPE _\***) che determina il tipo di dati PHP per i dati restituiti. Per informazioni sui tipi di dati supportati, vedere [costanti &#40;Microsoft Drivers for PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). Se non viene specificato alcun tipo restituito, verrà restituito un tipo PHP predefinito. Per informazioni sui tipi PHP predefiniti, vedere [Default PHP Data Types](../../connect/php/default-php-data-types.md). Per informazioni sulla specifica dei tipi di dati PHP, vedere [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="return-value"></a>Valore restituito  
I dati del campo. È possibile specificare il tipo di dati PHP dei dati restituiti usando il parametro *$getAsType* . Se non viene specificato alcun tipo di dati restituito, verrà restituito il tipo di dati PHP predefinito. Per informazioni sui tipi PHP predefiniti, vedere [Default PHP Data Types](../../connect/php/default-php-data-types.md). Per informazioni sulla specifica dei tipi di dati PHP, vedere [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="remarks"></a>Osservazioni  
La combinazione di **sqlsrv_fetch** e **sqlsrv_get_field** fornisce accesso forward-only ai dati.  
  
La combinazione di **sqlsrv_fetch**/**sqlsrv_get_field** carica un solo campo del risultato di una riga del set nella memoria script e PHP consente di specificare il tipo restituito. (Per informazioni su come specificare il tipo restituito PHP, vedere [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).) Questa combinazione di funzioni consente inoltre di recuperare i dati come flusso. (Per informazioni sul recupero dei dati come flusso, vedere [recupero dei dati come flusso usando il Driver SQLSRV](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md).)  
  
## <a name="example"></a>Esempio  
L'esempio seguente recupera una riga di dati contenente una revisione di prodotto e il nome del revisore. Per recuperare i dati dal set di risultati, è possibile usare **sqlsrv_get_field** . Nell'esempio si presuppone che SQL Server e il [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) database vengono installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up and execute the query. Note that both ReviewerName and  
Comments are of the SQL Server nvarchar type. */  
$tsql = "SELECT ReviewerName, Comments   
         FROM Production.ProductReview  
         WHERE ProductReviewID=1";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Make the first row of the result set available for reading. */  
if( sqlsrv_fetch( $stmt ) === false )  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Note: Fields must be accessed in order.  
Get the first field of the row. Note that no return type is  
specified. Data will be returned as a string, the default for  
a field of type nvarchar.*/  
$name = sqlsrv_get_field( $stmt, 0);  
echo "$name: ";  
  
/*Get the second field of the row as a stream.  
Because the default return type for a nvarchar field is a  
string, the return type must be specified as a stream. */  
$stream = sqlsrv_get_field( $stmt, 1,   
                            SQLSRV_PHPTYPE_STREAM( SQLSRV_ENC_CHAR));  
while( !feof( $stream))  
{   
    $str = fread( $stream, 10000);  
    echo $str;  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Recupero di dati](../../connect/php/retrieving-data.md)  

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
  
