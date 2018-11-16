---
title: 'Pdostatement:: SetAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07831f8af80804caff64f74102333a56b5f7d4c6
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601031"
---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Imposta un valore di attributo, ovvero un attributo PDO predefinito o un attributo personalizzato del driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>Parametri  
$*attribute*: numero intero, una delle costanti PDO::ATTR_* o PDO::SQLSRV_ATTR_\*. Per l'elenco degli attributi disponibili, vedere la sezione Osservazioni.  
  
$*value*: valore (misto) da impostare per $*attribute*.  
  
## <a name="return-value"></a>Valore restituito  
TRUE in caso di esito positivo; in caso contrario, FALSE.  
  
## <a name="remarks"></a>Remarks  
Nella tabella seguente sono elencati gli attributi disponibili:  
  
|attribute|Valori|Descrizione|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|1 per il limite di memoria PHP.|Consente di configurare le dimensioni del buffer che contiene il set di risultati per un cursore sul lato client.<br /><br />Il valore predefinito è 10.240 KB (10 MB).<br /><br />Per altre informazioni sui cursori sul lato client, vedere [Tipi di cursore &#40;PDO_SQLSRV Driver&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|Valore intero<br /><br />PDO::SQLSRV_ENCODING_UTF8 (impostazione predefinita)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Consente di impostare la codifica del set di caratteri usata dal driver per comunicare con il server.|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true o false|Gestisce operazioni di recupero numerici dalle colonne con tipi numerici SQL (bit, integer, smallint, tinyint, float o real).<br /><br />Quando il flag di opzione di connessione ATTR_STRINGIFY_FETCHES è attivata, il valore restituito è una stringa, anche quando SQLSRV_ATTR_FETCHES_NUMERIC_TYPE si trova in.<br /><br />Quando il tipo PDO restituito nella colonna di binding è PDO_PARAM_INT, il valore restituito da una colonna integer è un valore int anche se SQLSRV_ATTR_FETCHES_NUMERIC_TYPE è disattivata.|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Valore intero|Consente di impostare il timeout in secondi della query.<br /><br />Per impostazione predefinita, il driver attende i risultati per un periodo illimitato. I numeri negativi non sono consentiti.<br /><br />0 indica nessun timeout.|  
  
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

[PDO](https://php.net/manual/book.pdo.php)  
  
