---
title: 'Pdostatement:: SetAttribute | Documenti Microsoft'
ms.custom: ''
ms.date: 07/13/2017
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
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fba09d6c9e9e3b9806943802466628f820bece8f
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Imposta un valore di attributo, ovvero un attributo PDO predefinito o un attributo personalizzato del driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>Parametri  
$*attributo*: un numero intero, una delle PDO::ATTR_ * PDO::SQLSRV_ATTR_\* costanti. Per l'elenco degli attributi disponibili, vedere la sezione Osservazioni.  
  
$*valore*: valore (misto) da impostare per $ specificato*attributo*.  
  
## <a name="return-value"></a>Valore restituito  
TRUE in caso di esito positivo; in caso contrario, FALSE.  
  
## <a name="remarks"></a>Osservazioni  
Nella tabella seguente sono elencati gli attributi disponibili:  
  
|attribute|Valori|Description|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|1 per il limite di memoria PHP.|Consente di configurare le dimensioni del buffer che contiene il set di risultati per un cursore sul lato client.<br /><br />Il valore predefinito è 10.240 KB (10 MB).<br /><br />Per ulteriori informazioni sui cursori sul lato client, vedere [tipi di cursore &#40;Driver PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|Integer<br /><br />PDO::SQLSRV_ENCODING_UTF8 (impostazione predefinita)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Consente di impostare la codifica del set di caratteri usata dal driver per comunicare con il server.|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true o false|Gestisce i recuperi numerici dalle colonne con i tipi numerici SQL (bit, integer, smallint, tinyint, float o real).<br /><br />Quando il flag di opzione di connessione ATTR_STRINGIFY_FETCHES è attiva, il valore restituito è una stringa, anche quando si trova in SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.<br /><br />Quando il tipo PDO restituito nella colonna di associazione è PDO_PARAM_INT, il valore restituito da una colonna integer è un valore int, anche se SQLSRV_ATTR_FETCHES_NUMERIC_TYPE è disattivata.|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Integer|Consente di impostare il timeout in secondi della query.<br /><br />Per impostazione predefinita, il driver attende i risultati per un periodo illimitato. I numeri negativi non sono consentiti.<br /><br />0 indica nessun timeout.|  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets'=>false )  );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
echo $stmt->getAttribute( constant( "PDO::ATTR_CURSOR" ) );  
  
echo "\n";  
  
$stmt->setAttribute(PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 2);  
echo $stmt->getAttribute( constant( "PDO::SQLSRV_ATTR_QUERY_TIMEOUT" ) );  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
