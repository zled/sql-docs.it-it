---
title: sqlsrv_fetch_object | Documenti Microsoft
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
- sqlsrv_fetch_object
apitype: NA
helpviewer_keywords:
- sqlsrv_fetch_object
- API Reference, sqlsrv_fetch_object
- retrieving data, as an object
ms.assetid: 4ce2df2c-083a-4a4d-a1e2-e866e63707d5
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0c2caedf7b6bb6e0e4a996c885144b219798ab1d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvfetchobject"></a>sqlsrv_fetch_object
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera la riga successiva di dati in forma di oggetto PHP.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_fetch_object( resource $stmt [, string $className [, array $ctorParams[, row[, ]offset]]])  
```  
  
#### <a name="parameters"></a>Parametri  
*$stmt*: risorsa di istruzione corrispondente a un'istruzione eseguita.  
  
*$className* [facoltativo]: una stringa che specifica il nome della classe per creare un'istanza. Se non viene specificato alcun valore per il parametro *$className* , viene creata un'istanza della classe **stdClass** PHP.  
  
*$ctorParams* [facoltativo]: matrice che contiene i valori passati al costruttore della classe specificata con il *$className* parametro. Se il costruttore della classe specificata accetta valori di parametro, per la chiamata a *$ctorParams* object **sqlsrv_fetch_object**.  
  
*riga* [facoltativo]: uno dei valori seguenti, che specifica la riga per accedere a un set di risultati che usa un cursore scorrevole. (Se *riga* è specificato, *$className* e *$ctorParams* deve essere specificato in modo esplicito, anche se è necessario specificare null per *$className*e *$ctorParams*.)  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
Per altre informazioni su questi valori, vedere [Specifica di un tipo di cursore e selezione di righe](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).  
  
*offset* [facoltativo]: usato con SQLSRV_SCROLL_ABSOLUTE e SQLSRV_SCROLL_RELATIVE per specificare la riga da recuperare. Il primo record nel set di risultati è 0.  
  
## <a name="return-value"></a>Valore restituito  
Un oggetto PHP con proprietà corrispondenti ai nomi dei campi del set di risultati. I valori delle proprietà vengono popolati con i valori dei campi del set di risultati corrispondenti. Se la classe specificata con il parametro facoltativo *$className* non esiste o se all'istruzione specificata non è associato alcun set di risultati attivo, viene restituito **false** . Se non sono presenti altre righe da recuperare, viene restituito **null** .  
  
Il tipo di dati di un valore nell'oggetto restituito corrisponderà al tipo di dati PHP predefinito. Per informazioni sui tipi di dati PHP predefiniti, vedere [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
## <a name="remarks"></a>Osservazioni  
Se viene specificato un nome di classe con il parametro facoltativo *$className* , viene creata un'istanza di un oggetto di questo tipo di classe. Se la classe presenta proprietà con nomi corrispondenti ai nomi dei campi del set di risultati, alle proprietà vengono applicati i valori del set di risultati corrispondenti. Se un nome di campo del set di risultati non corrisponde ad alcuna proprietà della classe, all'oggetto viene aggiunta una proprietà con il nome del campo del set di risultati e alla proprietà viene applicato il valore del set di risultati.  
  
Quando si specifica una classe con il parametro *$className* , si applicano le regole seguenti:  
  
-   La corrispondenza tiene conto della distinzione tra maiuscole e minuscole. Ad esempio, il nome della proprietà CustomerId non corrisponde al nome del campo CustomerID. In questo caso, la proprietà CustomerID verrebbe aggiunta all'oggetto e il valore del campo CustomerID verrebbe assegnato alla proprietà CustomerID.  
  
-   La corrispondenza si verifica indipendentemente dai modificatori di accesso. Ad esempio, se la classe specificata ha una proprietà privata il cui nome corrisponde al nome di un campo del set di risultati, alla proprietà viene applicato il valore del campo del set di risultati.  
  
-   I tipi di dati delle proprietà della classe vengono ignorati. Se il campo "CustomerID" nel set di risultati è una stringa ma la proprietà "CustomerID" della classe è Integer, nella proprietà "CustomerID" viene scritto il valore della stringa del set di risultati.  
  
-   Se la classe specificata non esiste, la funzione restituisce **false** e aggiunge un errore alla raccolta degli errori. Per informazioni sul recupero delle informazioni relative agli errori, vedere [sqlsrv_errors](../../connect/php/sqlsrv-errors.md).  
  
Se viene restituito un campo senza nome, **sqlsrv_fetch_object** rimuove il valore del campo ed emette un avviso. Ad esempio, si consideri l'istruzione Transact-SQL seguente che inserisce un valore in una tabella di database e recupera la chiave primaria generata dal server:  
  
<pre>INSERT INTO Production.ProductPhoto (LargePhoto) VALUES (?);  
SELECT SCOPE_IDENTITY()</pre>  
  
Se i risultati restituiti dalla query vengono recuperati con **sqlsrv_fetch_object**, il valore restituito da `SELECT SCOPE_IDENTITY()` viene rimosso e viene emesso un avviso. Per evitare questo problema, è possibile specificare un nome per il campo restituito nell'istruzione Transact-SQL. Di seguito è illustrato un modo per specificare un nome di colonna in Transact-SQL:  
  
`SELECT SCOPE_IDENTITY() AS PictureID`  
  
## <a name="example"></a>Esempio  
L'esempio seguente recuperata ciascuna riga di un set di risultati in forma di oggetto PHP. Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) siano installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nella console.  
  
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
  
/* Set up and execute the query. */  
$tsql = "SELECT FirstName, LastName  
         FROM Person.Contact  
         WHERE LastName='Alan'";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in query preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve each row as a PHP object and display the results.*/  
while( $obj = sqlsrv_fetch_object( $stmt))  
{  
      echo $obj->LastName.", ".$obj->FirstName."\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Esempio  
L'esempio seguente recupera ciascuna riga di un set di risultati in forma di istanza della classe *Product* definita nello script. L'esempio recupera informazioni sui prodotti dal *Purchasing. PurchaseOrderDetail* e *Production. Product* tabelle del database AdventureWorks per prodotti con una determinata data di scadenza (* DueDate*) e scorte (*StockQty*) inferiore a un valore specificato. L'esempio evidenzia alcune delle regole applicate quando si specifica una classe in una chiamata a **sqlsrv_fetch_object**:  
  
-   La variabile *$product* è un'istanza della classe *Product* , perché con il parametro *$className* è specificato "Product" e la classe *Product* esiste.  
  
-   La proprietà *Name* viene aggiunta all'istanza *$product* perché la proprietà *name* non corrisponde.  
  
-   La proprietà *Color* viene aggiunta all'istanza *$product* perché non esiste una proprietà corrispondente.  
  
-   La proprietà privata *UnitPrice* viene popolata con il valore del campo *UnitPrice* .  
  
Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) siano installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nella console.  
  
```  
<?php  
/* Define the Product class. */  
class Product  
{  
     /* Constructor */  
     public function Product($ID)  
     {  
          $this->objID = $ID;  
     }  
     public $objID;  
     public $name;  
     public $StockedQty;  
     public $SafetyStockLevel;  
     private $UnitPrice;  
     function getPrice()  
     {  
          return $this->UnitPrice;  
     }  
}  
  
/* Connect to the local server using Windows Authentication, and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Define the query. */  
$tsql = "SELECT Name,  
                SafetyStockLevel,  
                StockedQty,  
                UnitPrice,  
                Color  
         FROM Purchasing.PurchaseOrderDetail AS pdo  
         JOIN Production.Product AS p  
         ON pdo.ProductID = p.ProductID  
         WHERE pdo.StockedQty < ?  
         AND pdo.DueDate= ?";  
  
/* Set the parameter values. */  
$params = array(3, '2002-01-29');  
  
/* Execute the query. */  
$stmt = sqlsrv_query( $conn, $tsql, $params);  
if ( $stmt )  
{  
     echo "Statement executed.\n";  
}   
else   
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Iterate through the result set, printing a row of data upon each  
 iteration. Note the following:  
     1) $product is an instance of the Product class.  
     2) The $ctorParams parameter is required in the call to  
        sqlsrv_fetch_object, because the Product class constructor is  
        explicity defined and requires parameter values.  
     3) The "Name" property is added to the $product instance because  
        the existing "name" property does not match.  
     4) The "Color" property is added to the $product instance  
        because there is no matching property.  
     5) The private property "UnitPrice" is populated with the value  
        of the "UnitPrice" field.*/  
$i=0; //Used as the $objID in the Product class constructor.  
while( $product = sqlsrv_fetch_object( $stmt, "Product", array($i)))  
{  
     echo "Object ID: ".$product->objID."\n";  
     echo "Product Name: ".$product->Name."\n";  
     echo "Stocked Qty: ".$product->StockedQty."\n";  
     echo "Safety Stock Level: ".$product->SafetyStockLevel."\n";  
     echo "Product Color: ".$product->Color."\n";  
     echo "Unit Price: ".$product->getPrice()."\n";  
     echo "-----------------\n";  
     $i++;  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
La variabile **sqlsrv_fetch_object** restituisce sempre i dati in base ai [Default PHP Data Types](../../connect/php/default-php-data-types.md). Per informazioni su come specificare il tipo di dati PHP, vedere [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Se viene restituito un campo senza nome, **sqlsrv_fetch_object** rimuove il valore del campo ed emette un avviso. Ad esempio, si consideri l'istruzione Transact-SQL seguente che inserisce un valore in una tabella di database e recupera la chiave primaria generata dal server:  
  
<pre>INSERT INTO Production.ProductPhoto (LargePhoto) VALUES (?);  
SELECT SCOPE_IDENTITY()</pre>  
  
Se i risultati restituiti dalla query vengono recuperati con **sqlsrv_fetch_object**, il valore restituito da `SELECT SCOPE_IDENTITY()` viene rimosso e viene emesso un avviso. Per evitare questo problema, è possibile specificare un nome per il campo restituito nell'istruzione Transact-SQL. Di seguito è illustrato un modo per specificare un nome di colonna in Transact-SQL:  
  
`SELECT SCOPE_IDENTITY() AS PictureID`  
  
## <a name="see-also"></a>Vedere anche  
[Recupero di dati](../../connect/php/retrieving-data.md)  
[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  

