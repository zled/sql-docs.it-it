---
title: 'PDO:: Prepare | Documenti Microsoft'
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4bb96c535fb3962e5c92723bb67d6cd0827de03
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
*key_pair*: matrice che contiene il nome dell'attributo e un valore. Per ulteriori informazioni, vedere le sezione Note.  
  
## <a name="return-value"></a>Valore restituito  
In caso di esito positivo restituisce un oggetto PDOStatement. In caso di esito negativo, restituisce un oggetto PDOException o false, a seconda del valore di PDO::ATTR_ERRMODE.  
  
## <a name="remarks"></a>Osservazioni  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] non valuta le istruzioni preparate fino all'esecuzione.  
  
Nella tabella seguente sono elencati i possibili *key_pair* valori.  
  
|Key|Description|  
|-------|---------------|  
|PDO::ATTR_CURSOR|Specifica il comportamento del cursore. Il valore predefinito è PDO::CURSOR_FWDONLY. PDO::CURSOR_SCROLL è un cursore statico.<br /><br />Ad esempio, `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`.<br /><br />Se si usa PDO::CURSOR_SCROLL, è possibile usare PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE, descritto di seguito.<br /><br />Vedere [tipi di cursore &#40;Driver PDO_SQLSRV&#41; ](../../connect/php/cursor-types-pdo-sqlsrv-driver.md) per ulteriori informazioni sui set di risultati e i cursori nel driver PDO_SQLSRV.|  
|PDO::ATTR_EMULATE_PREPARES|Se PDO:: attr_emulate_prepares è attivata, i segnaposto in un'istruzione preparata viene sostituito dalla parametri associati. Un'istruzione SQL completa con alcun segnaposto viene quindi inviata al database in esecuzione. <br /><br />PDO:: attr_emulate_prepares consente di ignorare alcune restrizioni in SQL Server. Ad esempio, SQL Server non supporta parametri denominati o posizionali in alcune clausole Transact-SQL. Inoltre, SQL Server ha un limite di 2100 parametri di associazione.<br /><br />È possibile impostare l'attributo PDO:: attr_emulate_prepares su true. Esempio:<br /><br />`PDO::ATTR_EMULATE_PREPARES => true`<br /><br />Per impostazione predefinita, questo attributo è impostato su false.<br /><br />**Nota:** la sicurezza delle query con parametri non è attiva quando si usa `PDO::ATTR_EMULATE_PREPARES => true`. L'applicazione deve verificare che i dati associati ai parametri non contengano codice dannoso di Transact-SQL.<br /><br />**Limitazioni:**: perché i parametri non sono associati con funzionalità di query con parametri del database, non sono supportati parametri input_output e di output.|  
|PDO::SQLSRV_ATTR_ENCODING|PDO::SQLSRV_ENCODING_UTF8 (impostazione predefinita)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|Se true, consente di specificare l'esecuzione di una query diretta. False indica l'esecuzione di un'istruzione preparata. Per ulteriori informazioni su PDO:: sqlsrv_attr_direct_query, vedere [esecuzione di istruzioni diretta e preparata nel Driver PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Per altre informazioni, vedere [PDO::setAttribute](../../connect/php/pdo-setattribute.md).|  
  
Se si usa PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, è possibile usare PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE. Ad esempio,  
  
```  
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));  
```  
  
nella tabella seguente vengono illustrati i valori possibili per PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE.  
  
|Value|Description|  
|---------|---------------|  
|PDO::SQLSRV_CURSOR_BUFFERED|Crea un cursore statico (memorizzato nel buffer) sul lato client. Per ulteriori informazioni sui cursori sul lato client, vedere [tipi di cursore &#40;Driver PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
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
Questo esempio illustra come usare il metodo PDO::prepare con un cursore sul lato client. Per un esempio che illustri un cursore sul lato server, vedere [tipi di cursore &#40;Driver PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).  
  
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
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
