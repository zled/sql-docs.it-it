---
title: 'PDO:: Prepare | Microsoft Docs'
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ac27dbcc186eff263803da714032d532c95d3b4
ms.sourcegitcommit: f9d4f9c1815cff1689a68debdccff5e7ff97ccaf
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39367703"
---
# <a name="pdoprepare"></a>PDO::prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Prepara un'istruzione per l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PDOStatement PDO::prepare ( $statement [, array(key_pair)] )  
```  
  
#### <a name="parameters"></a>Parametri  
$*statement*: stringa contenente l'istruzione SQL da eseguire.  
  
*key_pair*: matrice contenente il nome e il valore di un attributo. Per ulteriori informazioni, vedere le sezione Note.  
  
## <a name="return-value"></a>Valore restituito  
In caso di esito positivo restituisce un oggetto PDOStatement. In caso di esito negativo, restituisce un oggetto PDOException o false, a seconda del valore di PDO::ATTR_ERRMODE.  
  
## <a name="remarks"></a>Remarks  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] non valuta le istruzioni preparate fino all'esecuzione.  
  
Nella tabella seguente sono elencati i valori *key_pair* possibili.  
  
|Key|Descrizione|  
|-------|---------------|  
|PDO::ATTR_CURSOR|Specifica il comportamento del cursore. Il valore predefinito è PDO::CURSOR_FWDONLY. PDO::CURSOR_SCROLL è un cursore statico.<br /><br />Ad esempio, `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`.<br /><br />Se si usa PDO::CURSOR_SCROLL, è possibile usare PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE, descritto di seguito.<br /><br />Per altre informazioni sui set di risultati e sui cursori nel driver PDO_SQLSRV, vedere [Tipi di cursore &#40;driver PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::ATTR_EMULATE_PREPARES|Per impostazione predefinita, questo attributo è false, che può essere modificato da questo `PDO::ATTR_EMULATE_PREPARES => true`. Visualizzare [emulare preparare](#emulate-prepare) per i dettagli e di esempio.|
|PDO::SQLSRV_ATTR_ENCODING|PDO::SQLSRV_ENCODING_UTF8 (impostazione predefinita)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|Se true, consente di specificare l'esecuzione di una query diretta. False indica l'esecuzione di un'istruzione preparata. Per altre informazioni su PDO::SQLSRV_ATTR_DIRECT_QUERY, vedere [Esecuzione di istruzioni diretta e preparata nel driver PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Per altre informazioni, vedere [PDO::setAttribute](../../connect/php/pdo-setattribute.md).|  
  
Se si usa PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, è possibile usare PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE. Ad esempio,  
  
```  
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));  
```  
  
nella tabella seguente vengono illustrati i valori possibili per PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE.  
  
|valore|Descrizione|  
|---------|---------------|  
|PDO::SQLSRV_CURSOR_BUFFERED|Crea un cursore statico (memorizzato nel buffer) sul lato client. Per altre informazioni sui cursori sul lato client, vedere [Tipi di cursore &#40;PDO_SQLSRV Driver&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_CURSOR_DYNAMIC|Crea un cursore dinamico (non memorizzato nel buffer) sul lato server che consente di accedere alle righe in qualsiasi ordine e riflette le modifiche nel database.|  
|PDO::SQLSRV_CURSOR_KEYSET_DRIVEN|Crea un cursore keyset sul lato server. Un cursore keyset non aggiorna il conteggio delle righe se dalla tabella viene eliminata una riga (una riga eliminata viene restituita senza alcun valore).|  
|PDO::SQLSRV_CURSOR_STATIC|Crea un cursore statico sul lato server che consente di accedere alle righe in qualsiasi ordine ma non riflette le modifiche nel database.<br /><br />PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL implica PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_STATIC.|  
  
È possibile chiudere un oggetto PDOStatement impostandolo su null.  
  
## <a name="example"></a>Esempio  
Questo esempio illustra come usare il metodo PDO::prepare con marcatori di parametro e un cursore forward-only.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table1(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
echo "\n";  
  
$query = "insert into Table1(col1, col2) values(:col1, :col2)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( ':col1' => $col1, ':col2' => $col2 ) );  
print $stmt->rowCount();  
  
$stmt = null  
?>  
```  

## <a name="example"></a>Esempio  
Questo esempio illustra come usare il metodo PDO::prepare con un cursore sul lato client. Per un esempio di cursore sul lato server, vedere [Tipi di cursore &#40;driver PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  

<a name="emulate-prepare" />

## <a name="example"></a>Esempio 

Questo esempio illustra come usare il metodo PDO:: Prepare con `PDO::ATTR_EMULATE_PREPARES` impostato su true. 

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$database = "tempdb";
$conn = new PDO("sqlsrv:server = $serverName; Database = $database", $username, $password);

$pdo_options = array();
$pdo_options[PDO::ATTR_EMULATE_PREPARES] = true;
$pdo_options[PDO::SQLSRV_ATTR_ENCODING] = PDO::SQLSRV_ENCODING_UTF8;

$stmt = $conn->prepare("CREATE TABLE TEST([id] [int] IDENTITY(1,1) NOT NULL, 
                                          [name] nvarchar(max))", 
                                          $pdo_options);
$stmt->execute();

$prefix = '가각';
$name = '가각ácasa';
$name2 = '가각sample2';

$stmt = $conn->prepare("INSERT INTO TEST(name) VALUES(:p0)", $pdo_options);
$stmt->execute(['p0' => $name]);
unset($stmt);

$stmt = $conn->prepare("SELECT * FROM TEST WHERE NAME LIKE :p0", $pdo_options);
$stmt->execute(['p0' => "$prefix%"]);
foreach ($stmt as $row) {
    echo "\n" . 'FOUND: ' . $row['name'];
}

unset($stmt);
unset($conn);
?>
```

Il driver PDO_SQLSRV internamente sostituisce tutti i segnaposto con i parametri vincolate dal [PDOStatement::bindParam()](../../connect/php/pdostatement-bindparam.md). Pertanto, una stringa di query SQL con segnaposto non viene inviata al server. Si consideri questo esempio,

```
$statement = $PDO->prepare("INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)");
$statement->bindParam(:cus_name, "Cardinal");
$statement->bindParam(:con_name, "Tom B. Erichsen");
$statement->execute();
```

Con `PDO::ATTR_EMULATE_PREPARES` impostato su false (il caso predefinito), i dati inviati al database sono:

```
"INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)"
Information on :cus_name parameter
Information on :con_name parameter
```

Il server eseguirà la query utilizzando la funzionalità di query con parametri per l'associazione di parametri. D'altra parte, con `PDO::ATTR_EMULATE_PREPARES` impostato su true, la query inviata al server è essenzialmente:

```
"INSERT into Customers (CustomerName, ContactName) VALUES ('Cardinal', 'Tom B. Erichsen')"
```

Impostazione `PDO::ATTR_EMULATE_PREPARES` a true può ignorare alcune restrizioni in SQL Server. Ad esempio, SQL Server non supporta i parametri denominati o posizionali in alcune clausole Transact-SQL. Inoltre, SQL Server ha un limite di 2100 parametri di associazione.

> [!NOTE]
> Prepara l'emulate impostato su true, la sicurezza delle query con parametri non è attiva. Pertanto l'applicazione deve verificare che i dati associati ai parametri non contengano codice Transact-SQL dannoso.

### <a name="encoding"></a>Codifica

Se l'utente desidera eseguire l'associazione di parametri con codifiche diverse (ad esempio, UTF-8 o binario), utente deve specificare chiaramente la codifica dello script PHP.

Il driver PDO_SQLSRV controlla innanzitutto la codifica specificata nella `PDO::bindParam()` (ad esempio, `$statement->bindParam(:cus_name, "Cardinal", PDO::PARAM_STR, 10, PDO::SQLSRV_ENCODING_UTF8)`). 

Se non viene trovato, il driver verificherà se qualsiasi codifica è impostato nelle `PDO::prepare()` o `PDOStatement::setAttribute()`. In caso contrario, il driver utilizza la codifica specificata nella `PDO::__construct()` o `PDO::setAttribute()`.

### <a name="limitations"></a>Limitazioni

Come può notare, l'associazione viene eseguita internamente dal driver. Una query valida viene inviata al server per l'esecuzione senza alcun parametro. Alcune limitazioni rispetto al caso normale, risultato quando la funzionalità di query con parametri non è in uso.

- Non funziona per i parametri che vengono associati come `PDO::PARAM_INPUT_OUTPUT`.
    - Quando l'utente specifica `PDO::PARAM_INPUT_OUTPUT` in `PDO::bindParam()`, viene generata un'eccezione PDO.
- Non funziona per i parametri che vengono associati come parametri di output.
    - Quando l'utente crea un'istruzione preparata con segnaposto che sono pensati per i parametri di output (vale a dire, con un segno di uguale immediatamente dopo un segnaposto, ad esempio `SELECT ? = COUNT(*) FROM Table1`), viene generata un'eccezione PDO.
    - Quando un'istruzione preparata richiama una stored procedure con un segnaposto come argomento per un parametro di output, viene generata alcuna eccezione poiché il driver non è in grado di rilevare il parametro di output. Tuttavia, la variabile fornita dall'utente per il parametro di output rimarrà invariata.
- Segnaposto duplicati per un parametro con codificato binario non funzionerà

## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
